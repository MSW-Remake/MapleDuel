# Adding New Card Packs

## Overview

This guide explains the step-by-step process of adding new card packs to Maple Duel. New card packs are collections of cards with specific themes or concepts that allow players to expand their collections through purchase.

## Step 1: Card Pack Data Definition

### Adding New Card Pack Information to CardPack.csv
```csv
name,displayName,description,price,cardCount,rarity1Rate,rarity2Rate,rarity3Rate,rarity4Rate,rarity5Rate,iconRUID,packRUID
DragonPack,Dragon Card Pack,Cards imbued with ancient dragon power,2500,5,40,30,20,8,2,dragon_pack_icon,dragon_pack_model
```

**Card Pack Attribute Descriptions:**
- `name`: Internal identifier
- `displayName`: Name shown to players
- `description`: Card pack description
- `price`: Purchase price (Meso)
- `cardCount`: Number of cards per pack
- `rarity1Rate~rarity5Rate`: Probability for each rarity level (%)
- `iconRUID`: Card pack icon resource
- `packRUID`: Card pack 3D model resource

### Defining Card Pool per Card Pack
```lua
-- Extending CardPackManager.mlua
local DRAGON_PACK_CARDS = {
    -- Common cards (rarity 1)
    Common = {
        "BabyDragon", "DragonScale", "DragonEgg", "WyvernRider",
        "DragonBreath", "ScaledArmor", "DragonFruit", "Dragonling"
    },
    -- Rare cards (rarity 2) 
    Rare = {
        "YoungDragon", "DragonMage", "DragonKnight", "WyvernMaster",
        "FireBreath", "IceBreath", "DragonShield"
    },
    -- Epic cards (rarity 3)
    Epic = {
        "AdultDragon", "ElderWyvern", "DragonLord", "DragonSorceress"
    },
    -- Unique cards (rarity 4)
    Unique = {
        "AncientDragon", "CrystalDragon", "ShadowDragon"
    },
    -- Legendary cards (rarity 5)
    Legendary = {
        "ArchDragon", "DragonGod"
    }
}
```

## Step 2: CardPackManager Extension

### Registering New Card Pack
```lua
-- Adding dragon pack to CardPackManager.mlua
@ExecSpace("ServerOnly")
method void OnBeginPlay()
    __base:OnBeginPlay()
    
    -- Existing card packs...
    self.cardPools["DragonPack"] = DRAGON_PACK_CARDS
    self.specialEffects["DragonPack"] = "DragonPackOpenEffect"
end
```

### Implementing Card Pack Opening Logic
```lua
method table OpenCardPack(string packName)
    local packData = self:GetPackData(packName)
    if not packData then
        return nil
    end
    
    local cards = {}
    local cardPool = self.cardPools[packName]
    
    for i = 1, packData.cardCount do
        local rarity = self:RollRarity(packData)
        local card = self:SelectRandomCard(cardPool, rarity)
        table.insert(cards, {name = card, rarity = rarity})
    end
    
    -- Bonus card (under special conditions)
    if self:ShouldGetBonusCard(packName) then
        local bonusCard = self:SelectBonusCard(packName)
        table.insert(cards, bonusCard)
    end
    
    return cards
end

method string RollRarity(table packData)
    local roll = math.random(1, 100)
    local cumulative = 0
    
    for i = 5, 1, -1 do -- Check from highest rarity
        cumulative += packData["rarity" .. i .. "Rate"]
        if roll <= cumulative then
            return i
        end
    end
    
    return 1 -- Default: Common
end

method string SelectRandomCard(table cardPool, integer rarity)
    local rarityName = self:GetRarityName(rarity)
    local availableCards = cardPool[rarityName]
    
    if not availableCards or #availableCards == 0 then
        -- If no cards of this rarity, select from one rarity lower
        return self:SelectRandomCard(cardPool, math.max(1, rarity - 1))
    end
    
    return availableCards[math.random(1, #availableCards)]
end
```

### Special Effects and Events
```lua
method boolean ShouldGetBonusCard(string packName)
    if packName == "DragonPack" then
        -- 10% chance for bonus dragon card
        return math.random(1, 100) <= 10
    end
    return false
end

method table SelectBonusCard(string packName)
    if packName == "DragonPack" then
        return {
            name = "MythicalDragon", 
            rarity = 6, -- Special rarity
            isBonus = true
        }
    end
    return nil
end
```

## Step 3: Shop UI Update

### Adding New Card Pack to ShopModule
```lua
-- Extending ShopModule.mlua
@ExecSpace("ClientOnly")
method void RefreshCardPackList()
    local cardPackManager = self.Entity.CurrentMap.cardPackManager
    local availablePacks = cardPackManager:GetAvailablePacks()
    
    for _, packData in ipairs(availablePacks) do
        local packButton = self:CreateCardPackButton(packData)
        self.cardPackContainer:AddChild(packButton)
    end
end

method Entity CreateCardPackButton(table packData)
    local buttonEntity = _SpawnService:SpawnByModelId(
        _EntryService:GetModelIdByName("CardPackButton"), 
        "CardPackButton"
    )
    
    -- Set card pack icon
    local iconComponent = buttonEntity:GetComponentByType(SpriteRendererComponent)
    iconComponent.SpriteRUID = packData.iconRUID
    
    -- Display price
    local priceText = buttonEntity:GetChild("PriceText").TextComponent
    priceText.String = tostring(packData.price) .. " Meso"
    
    -- Click event
    buttonEntity:ConnectEvent(ButtonClickEvent, function()
        self:PurchaseCardPack(packData.name)
    end)
    
    return buttonEntity
end
```

### Card Pack Purchase Handling
```lua
method void PurchaseCardPack(string packName)
    local character = _UserService.LocalPlayer.Character
    if not character.isLoaded or _Server:IsRequesting() then 
        return 
    end
    
    local packData = self.cardPackManager:GetPackData(packName)
    
    -- Check price
    if character.meso < packData.price then
        self.uiManager.PopupModule:ShowMessage("Insufficient Meso!")
        return
    end
    
    -- Confirmation popup
    self.uiManager.PopupModule:Open("ConfirmPurchase", true, function()
        _Server:Request(character, "BuyCardPack", {packName})
    end)
end
```

## Step 4: Card Pack Opening Animation

### Extending CardPackModule
```lua
-- Adding new card pack opening animation to CardPackModule.mlua
@ExecSpace("ClientOnly")
method void PlayOpenAnimation(string packName, table cards)
    if packName == "DragonPack" then
        self:PlayDragonPackAnimation(cards)
    else
        self:PlayDefaultOpenAnimation(cards)
    end
end

@ExecSpace("ClientOnly")  
method void PlayDragonPackAnimation(table cards)
    -- Dragon pack exclusive effects
    _Effect:PlayEffect("DragonFireBurst", Vector3.zero, self.Entity)
    
    -- Card appearance animation
    _TimerService:SetTimerOnce(function()
        for i, card in ipairs(cards) do
            _TimerService:SetTimerOnce(function()
                self:RevealCard(card, i)
                if card.rarity >= 4 then -- Unique or higher
                    _Effect:PlayEffect("DragonRoar", Vector3.zero, self.Entity)
                end
            end, i * 0.5)
        end
    end, 1.0)
end
```

## Step 5: Card Pack Theme Events

### Seasonal Card Pack Activation
```lua
-- EventManager.mlua (hypothetical event manager)
method void ActivateSeasonalPack(string season)
    if season == "DragonSeason" then
        -- Dragon pack discount event
        self.cardPackManager:SetPackDiscount("DragonPack", 0.2) -- 20% discount
        
        -- Increase bonus probability
        self.cardPackManager:SetBonusRate("DragonPack", 0.15) -- Increase to 15%
        
        -- Set event duration
        self:SetEventDuration(7) -- For 7 days
    end
end
```

### Daily Free Pack
```lua
method void CheckDailyFreePack(Character character)
    local lastFreePackDate = character:GetData("lastFreePackDate")
    local today = _DateTime:GetDate()
    
    if lastFreePackDate ~= today then
        -- Give free pack on first visit today
        character:SetData("lastFreePackDate", today)
        self:GiveFreeCardPack(character, "BasicPack")
    end
end
```

## Step 6: Collection System Integration

### Card Collection Update
```lua
-- Adding new card pack cards to collection in CardModule.mlua
method void UpdateCollection(Character character, table newCards)
    for _, card in ipairs(newCards) do
        if not character:HasCard(card.name) then
            character:AddToCollection(card.name)
            
            -- Special effect on first acquisition
            if self:IsRareCard(card) then
                self:ShowFirstTimeCollection(card)
            end
        end
    end
end

method void ShowFirstTimeCollection(table card)
    _Effect:PlayEffect("NewCardCollection", Vector3.zero, self.Entity)
    
    self.uiManager.PopupModule:ShowMessage(
        string.format("You acquired a new %s card!", card.name)
    )
end
```

## Step 7: Balance and Probability Adjustment

### Card Pack Probability Monitoring
```lua
method table GetPackOpeningStats(string packName)
    local stats = {
        totalOpened = 0,
        rarityDistribution = {0, 0, 0, 0, 0},
        averageValue = 0
    }
    
    -- Collect card pack opening data from players
    for _, character in ipairs(self:GetAllCharacters()) do
        local characterStats = character:GetPackStats(packName)
        stats.totalOpened += characterStats.opened
        
        for i = 1, 5 do
            stats.rarityDistribution[i] += characterStats.rarityCount[i]
        end
    end
    
    return stats
end

method void AdjustPackRates(string packName)
    local stats = self:GetPackOpeningStats(packName)
    local expectedRates = self:GetExpectedRates(packName)
    
    -- Compare actual vs expected rates and adjust
    for i = 1, 5 do
        local actualRate = stats.rarityDistribution[i] / stats.totalOpened * 100
        local expectedRate = expectedRates[i]
        
        if math.abs(actualRate - expectedRate) > 2 then -- If difference > 2%
            self:AdjustRarityRate(packName, i, expectedRate)
        end
    end
end
```

## Step 8: Resources and Localization

### Multi-language Support
```lua
-- Card pack name and description localization
local PACK_LOCALIZATION = {
    ko = {
        DragonPack = {
            name = "드래곤 카드팩",
            description = "고대 드래곤의 힘이 깃든 전설의 카드들을 획득할 수 있습니다."
        }
    },
    en = {
        DragonPack = {
            name = "Dragon Card Pack", 
            description = "Obtain legendary cards imbued with ancient dragon power."
        }
    }
}
```

### Resource Optimization
```lua
method void PreloadPackResources(string packName)
    local packData = self:GetPackData(packName)
    
    -- Preload card pack related resources
    _ResourceService:PreloadAsync({
        packData.iconRUID,
        packData.packRUID,
        self.specialEffects[packName]
    })
end
```

## Completion Checklist

- [ ] Add new card pack data to CardPack.csv
- [ ] Implement card pool and opening logic in CardPackManager
- [ ] Add new card pack to ShopModule UI
- [ ] Implement card pack opening animation
- [ ] Integrate with collection system
- [ ] Test probability and balance
- [ ] Resource optimization and localization
- [ ] Integrate with event system (optional)

## References

- `1. Core Architecture/Economy System/Card Pack System.md` - Detailed card pack system explanation
- `1. Core Architecture/Economy System/Shop System.md` - Shop system integration
- `3. Developer Guide/Game Content Addition/Adding New Cards.md` - How to add cards

Adding new card packs is important content that directly impacts game profitability and player engagement. Use this guide to create attractive and balanced card packs.

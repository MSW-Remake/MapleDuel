# Adding New Jobs

## Overview

This guide explains the step-by-step process of adding a new job class to Maple Duel. When adding a new job, the dedicated job cards and basic deck are automatically configured, and AI bots are also added along with it.

## Step 1: Data Definition

### Adding New Job Cards to Card.csv
```csv
name,category,job,rarity,cost,hp,atk,description,frontRUID,backRUID,soundRUID,triggerNameArray,auraNameArray
SamuraiSlash,Skill,Samurai,Common,3,0,0,Cut enemies with samurai sword energy,samurai_slash_front,common_back,slash_sound,"SamuraiSlash",""
```

**Key Settings:**
- `job`: New job name (e.g., `Samurai`)
- `category`: Card type (`Minion`, `Skill`)
- `rarity`: Rarity setting
- `triggerNameArray`: Card effect trigger name

### Defining Job-Specific Basic Card Set
```lua
-- Basic card composition for new job
local SAMURAI_BASE_CARDS = {
    {name = "SamuraiSlash", count = 2},
    {name = "BushidoSpirit", count = 1}, 
    {name = "KatanaStrike", count = 2},
    {name = "SamuraiGuard", count = 1}
}
```

## Step 2: DeckManager Extension

### Registering New Job in Deck System
```lua
-- Extending DeckManager.mlua
@ExecSpace("ServerOnly")
method void OnBeginPlay()
    __base:OnBeginPlay()
    
    -- Existing jobs
    self.validJobs = {"Warrior", "Magician", "Bowman", "Thief", "Pirate", "Samurai"}
    
    -- Basic deck composition for new job
    self.defaultDecks["Samurai"] = {
        -- Common cards 12 pieces
        {name = "MiniMushroom", count = 2},
        {name = "Snail", count = 2},
        -- ... other common cards
        
        -- Samurai exclusive cards 8 pieces  
        {name = "SamuraiSlash", count = 2},
        {name = "KatanaStrike", count = 2},
        {name = "BushidoSpirit", count = 1},
        {name = "SamuraiGuard", count = 1},
        {name = "DragonSlayer", count = 1},
        {name = "Meditate", count = 1}
    }
end
```

### Extending Deck Validation
```lua
method boolean IsValidJobForDeck(string job, table cards)
    if job == "Samurai" then
        -- Samurai-specific validation logic
        return self:ValidateSamuraiDeck(cards)
    end
    
    -- Existing job validation...
end

method boolean ValidateSamuraiDeck(table cards)
    local samuraiCardCount = 0
    
    for _, card in ipairs(cards) do
        local cardData = self.cardManager:GetCardData(card.name)
        if cardData and cardData.job == "Samurai" then
            samuraiCardCount += card.count or 1
        end
    end
    
    -- Samurai cards must be minimum 6, maximum 10
    return samuraiCardCount >= 6 and samuraiCardCount <= 10
end
```

## Step 3: Adding New Job Bot to BotManager

### Extending Bot Data
```lua
-- Adding new job bot to BotManager.mlua
@ExecSpace("ServerOnly") 
method void OnBeginPlay()
    __base:OnBeginPlay()
    
    -- Existing bots...
    self:AddBot("SamuraiBotEasy", {
        name = "Samurai Trainee",
        job = "Samurai", 
        level = 1,
        difficulty = "Easy",
        deck = self:CreateSamuraiDeck("Easy")
    })
    
    self:AddBot("SamuraiBotHard", {
        name = "Samurai Master",
        job = "Samurai",
        level = 10, 
        difficulty = "Hard",
        deck = self:CreateSamuraiDeck("Hard")
    })
end

method table CreateSamuraiDeck(string difficulty)
    local baseDeck = self.deckManager.defaultDecks["Samurai"]
    
    if difficulty == "Hard" then
        -- Hard bots use more powerful cards
        baseDeck = self:UpgradeDeckToLegendary(baseDeck)
    end
    
    return baseDeck
end
```

### Defining AI Strategy Patterns
```lua
-- Adding samurai AI pattern to ScoreManager.mlua
method number CalculateSamuraiPlayScore(Card card, Player bot, Player enemy)
    local score = 0
    
    -- Samurai job trait: Prefers consecutive attacks
    if card.name == "SamuraiSlash" then
        -- High score when enemy HP is low
        if enemy.hp <= 15 then
            score += 30
        end
        
        -- Increase score if consecutive skill combo is possible
        if self:CanComboWith(bot, "KatanaStrike") then
            score += 20
        end
    end
    
    return score
end
```

## Step 4: Card Effect Implementation

### Adding New Job Triggers to TriggerManager
```lua
-- Extending TriggerManager.mlua
method boolean SamuraiSlashCondition(string triggerKey, Card invoker, Card receiver)
    -- Samurai Slash: Targets enemy minions
    return triggerKey == "PlaySkill" and receiver.job ~= invoker.job
end

method void SamuraiSlashAction(string triggerKey, Card invoker, Card receiver, table args)
    local damage = 4 + (invoker:GetBonusAttack() or 0)
    
    -- Consecutive attack effect: Additional damage if samurai skill was used last turn
    if self:WasSamuraiSkillUsedLastTurn(invoker:GetPlayer()) then
        damage += 2
        _Effect:PlaySkillEffect("SamuraiCombo", receiver.minionActor.Entity)
    end
    
    receiver:TakeDamage(damage, invoker)
end

method boolean WasSamuraiSkillUsedLastTurn(Player player)
    -- Check previous turn records
    local lastActions = player:GetLastTurnActions()
    for _, action in ipairs(lastActions) do
        if action.type == "PlaySkill" and action.card.job == "Samurai" then
            return true
        end
    end
    return false
end
```

## Step 5: UI Updates

### Adding New Job to Character Selection UI
```lua
-- Extending Character.mlua
method table GetAvailableJobs()
    return {
        {name = "Warrior", job = "Warrior", icon = "warrior_icon"},
        {name = "Magician", job = "Magician", icon = "magician_icon"}, 
        {name = "Bowman", job = "Bowman", icon = "bowman_icon"},
        {name = "Thief", job = "Thief", icon = "thief_icon"},
        {name = "Pirate", job = "Pirate", icon = "pirate_icon"},
        {name = "Samurai", job = "Samurai", icon = "samurai_icon"} -- New addition
    }
end
```

### Filtering New Job Cards in Deck Editor UI
```lua
-- Extending DeckEditPanel.mlua  
method table FilterCardsByJob(string selectedJob)
    local availableCards = {}
    
    for _, cardData in ipairs(self.cardManager.dataSet:GetAllRows()) do
        -- Common cards are available for all jobs
        if cardData.job == "Common" or cardData.job == selectedJob then
            table.insert(availableCards, cardData)
        end
    end
    
    return availableCards
end
```

## Step 6: Adding Resources

### Visual Resources
- **Card Artwork**: Front images for new job cards
- **Job Icon**: Job symbol icon to display in UI  
- **Skill Effects**: Visual effects for new job skills
- **Sounds**: Sound effects dedicated to new job skills

### Resource Registration
```lua
-- Registering new resources in ResourceManager.mlua
local SAMURAI_RESOURCES = {
    icons = {
        samurai_icon = "SamuraiIcon.png"
    },
    effects = {
        samurai_slash = "SamuraiSlash.effect",
        bushido_spirit = "BushidoSpirit.effect"
    },
    sounds = {
        katana_strike = "KatanaStrike.wav",
        meditate = "Meditate.wav"
    }
}
```

## Step 7: Balance Adjustment

### Game Balance Review for New Job
```lua
-- Defining samurai job characteristics
local SAMURAI_TRAITS = {
    strengths = {
        "Consecutive attack combos",
        "Burst damage", 
        "Mobility"
    },
    weaknesses = {
        "Low defense",
        "High mana consumption",
        "Vulnerable to ranged attacks"
    },
    playstyle = "Aggressive tempo deck"
}
```

### Card Power Level Adjustment
```lua
method void BalanceSamuraiCards()
    -- Adjust so win rate against existing jobs stays around 50%
    local samuraiWinRate = self:CalculateJobWinRate("Samurai")
    
    if samuraiWinRate > 55 then
        self:NerfSamuraiCards() -- Nerf
    elseif samuraiWinRate < 45 then  
        self:BuffSamuraiCards() -- Buff
    end
end
```

## Step 8: Testing

### New Job Feature Testing
```lua
function TestSamuraiJob()
    -- Deck creation test
    local deck = CreateSamuraiDeck()
    assert(IsValidDeck(deck, "Samurai"))
    
    -- Bot battle test  
    local samuraiBot = CreateBot("Samurai", "Easy")
    local testResult = SimulateDuel(samuraiBot, CreateBot("Warrior", "Easy"))
    
    -- Card effect test
    TestSamuraiSkillEffects()
    
    log("Samurai job test complete")
end
```

## Completion Checklist

- [ ] Add new job card data to Card.csv
- [ ] Register new job in DeckManager and define basic deck
- [ ] Add new job bot to BotManager
- [ ] Implement new job card effects in TriggerManager  
- [ ] Modify UI to allow new job selection
- [ ] Add new job related resources (art, sound, effects)
- [ ] Test and adjust game balance
- [ ] Complete integration testing for all features

## References

- `1. Core Architecture/Deck System/Deck Management System.md` - Detailed deck system explanation
- `1. Core Architecture/AI/Bot System/Bot Data Management.md` - Bot system management
- `3. Developer Guide/Game Content Addition/Adding New Cards.md` - How to add cards

Adding a new job is a complex task, but following this guide allows you to systematically and stably integrate new jobs into the game.

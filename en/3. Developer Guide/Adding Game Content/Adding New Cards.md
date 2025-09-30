# Adding New Cards

## Overview

Adding new cards to Maple Duel requires multiple steps including data entry, visual resource preparation, game logic implementation, and testing. This guide explains the complete process of successfully adding new cards to the game step by step.

## Step 1: Card Planning and Design

### Defining Card Specifications

Before adding a new card, you must first define the card's basic specifications.

**Required Information:**
```
Card Name: e.g., "FireBolt"
Category: Skill or Minion
Job: Warrior, Magician, Bowman, Thief, Pirate, Common
Theme: Classic, Nautilus, etc.
Rarity: Normal, Rare, Epic, Unique, Legendary
Cost: 0~10 MP
Effect: Specific game effect description
```

**Additional Information for Minion Cards:**
```
Max HP: 1~10
Attack: 0~10
Special Status: Barrier, Venom, Chill status
```

**Additional Information for Skill Cards:**
```
Target Required: Whether it's a target-specified skill
```

## Step 2: Card.csv Data Entry

### Understanding Data Structure

Add new card information to the `RootDesk/MyDesk/DataSets/Card.csv` file.

**Key Field Descriptions:**
```csv
name,category,class,theme,rarity,isToken,tagArray,variantArray,linkArray,cost,maxHp,atk,hasBarrier,hasVenom,hasChill,isDirectAttackable,isImmuneToStrong,cardTriggerNameArray,cardAuraNameArray,minionTriggerNameArray,minionAuraNameArray,damageSound,dieSound,skillAnimation_1,skillAnimation_2,skillAnimation_3,ballAnimation_1,ballAnimation_2,ballAnimation_3,hitAnimation_1,hitAnimation_2,hitAnimation_3,extraAnimation_1,extraAnimation_2,extraAnimation_3,skillSound_1,skillSound_2,skillSound_3,hitSound_1,hitSound_2,hitSound_3,extraSound_1,extraSound_2,extraSound_3
```

### Actual Data Entry Examples

**Skill Card Example (FireBolt):**
```csv
FireBolt,Skill,Magician,Classic,Common,,,,,3,,,,,,,,,"[""FireBolt""]",,,,,,fire_skill_animation_1,,,fire_ball_1,,,fire_hit_1,,,,,fire_skill_sound_1,,,fire_hit_sound_1,,,,,
```

**Minion Card Example (GoblinWarrior):**
```csv
GoblinWarrior,Minion,Warrior,Classic,Normal,,,,,2,3,2,,,,,,,"[""GoblinWarrior""]",,"[""GoblinWarrior""]",,goblin_damage,goblin_die,,,,,,,goblin_hit,,,,,,,goblin_hurt,,,,,
```

### Field-by-Field Detailed Guide

**Basic Information Fields:**
- `name`: Unique card name (English, no spaces)
- `category`: "Skill" or "Minion"
- `class`: "Warrior", "Magician", "Bowman", "Thief", "Pirate", "Common"
- `theme`: Card set theme
- `rarity`: "Normal", "Rare", "Epic", "Unique", "Legendary"

**Gameplay Fields:**
- `cost`: MP cost (0~10)
- `maxHp`: Minion max HP (Minions only)
- `atk`: Minion attack power (Minions only)

**Trigger and Aura:**
- `cardTriggerNameArray`: Card effect trigger array `["TriggerName"]`
- `minionTriggerNameArray`: Minion effect trigger array `["TriggerName"]`

**Resource ID Fields:**
- `skillAnimation_1~3`: Skill animation resource IDs
- `skillSound_1~3`: Skill sound resource IDs
- Other animation and sound resource IDs

## Step 3: Trigger Effect Implementation

### Adding Effects to TriggerManager

If new cards have special effects, you need to add trigger methods to `TriggerManager.mlua`.

**Skill Card Trigger Implementation**:
- `TriggerManager.mlua :: FireBolt()` — Execute skill effect
- `TriggerManager.mlua :: FireBoltCondition()` — Check activation condition

**Minion Trigger Example:**
```lua
method void GoblinWarrior(Minion invoker, Minion receiver)
    self.taskManager:RunProcess(function()
        -- Deal 1 damage to all enemy minions when dying
        if receiver == invoker then
            local enemies = invoker.player.opponent.field:GetMinions(nil)
            self.taskManager:Damage(enemies, invoker, 1, nil, "GoblinWarrior", nil)
        end
    end, "GoblinWarrior")
end

method boolean GoblinWarriorCondition(string triggerKey, Minion invoker, Minion receiver)
    return triggerKey == "Death" and invoker == receiver
end
```

### Key Trigger Keys

- **"Cast"**: When card is cast
- **"Summon"**: When minion is summoned  
- **"Death"**: When unit dies
- **"BeginTurn"**: At turn start
- **"EndTurn"**: At turn end
- **"Attack"**: When attacking
- **"BeforeAttack"**: Before attack
- **"AfterAttack"**: After attack

## Step 4: Visual Resource Preparation

### Card Model Creation

**Required Models:**
```
CardFront Models: [CardName]DefaultSilverCardFront
                  [CardName]DefaultGoldCardFront
CardBack Models:  [CardName]DefaultSilverCardBack  
                  [CardName]DefaultGoldCardBack
Thumbnail:        [CardName]Default (for thumbnails)
```

**Variant Support:**
```
Default: [CardName]Default[Quality]CardFront
Variant: [CardName][VariantName][Quality]CardFront
Example: FireBoltHanbokSilverCardFront
```

### Animation and Effects

**Skill Card Animations:**
- `skillAnimation_1~3`: Skill casting animations
- `ballAnimation_1~3`: Projectile animations
- `hitAnimation_1~3`: Hit effects

**Minion Animations:**
- `damageSound`: Damage sound
- `dieSound`: Death sound
- `hitAnimation_1~3`: Hit effects

### Resource Registration

**ResourceManager Update:**
New card resources must be registered in `ResourceManager.mlua`.

## Step 5: UI and Localization

### Card Name Localization

**Multi-language Support:**
```
Korean: "FireBolt" -> "파이어 볼트"
English: "FireBolt" -> "Fire Bolt"
Japanese: "FireBolt" -> "ファイアボルト"
```

### Adding Card Descriptions

Card effect descriptions must be added for each language.

## Step 6: AI Bot Integration

### Adding Scores to ScoreManager

Add scoring logic to `ScoreManager.mlua` so bots can evaluate new cards.

```lua
method number GetCardScore(Card card, Player player)
    local cardName = card.name
    
    if cardName == "FireBolt" then
        return 4.0  -- Base score + situational adjustments
    elseif cardName == "GoblinWarrior" then
        return 5.5  -- Minion base score
    end
    
    -- Default scoring logic...
end
```

### BotManager Deck Composition

To include new cards in bot default decks, update `BotManager.mlua`.

## Step 7: Testing

### Feature Testing

**Checklist:**
- [ ] Does the card load properly?
- [ ] Is the card's visual representation correct?
- [ ] Does the card effect work as intended?
- [ ] Do animations and sounds play?
- [ ] Does the bot use the card appropriately?

### Balance Testing

**Check Items:**
- [ ] Is the effect appropriate for the cost?
- [ ] Does it balance well with existing cards?
- [ ] Does it have excessive impact on the game meta?

### Bug Testing

**Common Bugs:**
- Trigger condition errors
- Animation timing issues
- Resource loading failures
- Multi-language display errors

## Practical Example: Adding "Healing Potion" Card

### Step 1: Planning
```
Card Name: HealingPotion
Category: Skill
Job: Common
Theme: Classic
Rarity: Normal
Cost: 2 MP
Effect: Restore 3 HP to one friendly unit
```

### Step 2: CSV Data
```csv
HealingPotion,Skill,Common,Classic,Normal,,,,,2,,,,,,,,,,"[""HealingPotion""]",,,,,,healing_animation,,,healing_ball,,,healing_effect,,,,,healing_sound,,,healing_hit,,,,,
```

### Step 3: Trigger Implementation
```lua
method void HealingPotion(Card invoker, Card receiver, table result, Unit target)
    self.taskManager:RunProcess(function()
        if isvalid(target) and target.player == receiver.player then
            self.taskManager:Heal({target}, receiver, 3, nil, "HealingPotion", nil)
        end
    end, "HealingPotion")
end

method boolean HealingPotionCondition(string triggerKey, Card invoker, Card receiver)
    return triggerKey == "Cast" and invoker == receiver
end
```

### Step 4: Resource Preparation
- `HealingPotionDefaultSilverCardFront.model`
- `HealingPotionDefaultGoldCardFront.model`
- Healing animation and sound files

## Advanced Features

### Conditional Effects

```lua
method void AdvancedCard(Card invoker, Card receiver)
    self.taskManager:RunProcess(function()
        local player = receiver.player
        local handCount = player.hand:GetCardCount()
        
        if handCount >= 5 then
            -- Enhanced effect when hand has 5 or more cards
            self.taskManager:Damage(enemies, receiver, 8, nil, "AdvancedCard", nil)
        else
            -- Basic effect
            self.taskManager:Damage(enemies, receiver, 4, nil, "AdvancedCard", nil)
        end
    end, "AdvancedCard")
end
```

### Chain Effects

```lua
method void ChainCard(Card invoker, Card receiver)
    self.taskManager:RunProcess(function()
        -- First effect
        self.taskManager:Damage(targets, receiver, 2, nil, "ChainCard", nil)
        
        -- Trigger additional effect
        self:InvokeTriggers({receiver}, {receiver.player}, "ChainEffect", {}, nil, nil)
    end, "ChainCard")
end
```

## Considerations

### Performance Considerations
- Complex triggers can affect game performance
- Prevent infinite loops or excessive chain effects
- Optimize resource sizes

### Balance Considerations
- Appropriateness of effect for cost
- Interaction with existing cards
- Impact on metagame

### Compatibility Considerations
- Compatibility with existing save files
- Multi-language support
- Operation across various platforms

## References

- `1. Core Architecture/Card System/` - Detailed card system documentation
- `1. Core Architecture/Manager System/` - Manager system documentation
- `2. Implementation Details/Event System/Trigger System.md` - Trigger system documentation

Following this guide to add new cards will create high-quality cards that integrate consistently with Maple Duel's entire system.

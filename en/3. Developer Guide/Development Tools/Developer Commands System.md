# Developer Commands System

## Overview

The developer commands system in Maple Duel provides useful debugging commands for development and testing processes through `Developer.mlua`. These developer-exclusive tools are executed via chat and enable game state manipulation and data verification.

## Core Commands System

### Developer.mlua
Logic component responsible for processing developer commands.

**Key Functions:**
- Chat command parsing
- Game state manipulation
- Log output
- Data initialization

## Main Developer Commands

### Data Management Commands

**`/reset`** - Reset Character Data
```lua
// Usage: /reset
// Function: Reset all character data to initial state
```

**`/clear`** - Delete Specific Data
```lua
// Usage: /clear [data type]
// Function: Delete information of specified data type
```

**`/meso [amount]`** - Give Meso
```lua
// Usage: /meso 10000
// Function: Give specified amount of meso to character
```

### Card and Deck Management

**`/card [card name]`** - Add Card
```lua
// Usage: /card FireBolt
// Function: Add specified card to collection
```

**`/pack [pack name]`** - Give Card Pack
```lua  
// Usage: /pack ClassicPack
// Function: Add specified card pack to inventory
```

### Game State Manipulation

**`/god`** - God Mode
```lua
// Usage: /god
// Function: Toggle player invincibility state
```

**`/win`** - Force Victory
```lua
// Usage: /win  
// Function: Instantly win current duel
```

**`/draw [amount]`** - Force Card Draw
```lua
// Usage: /draw 5
// Function: Add specified number of cards to hand
```

### Logging and Debugging

**`/log [message]`** - Log Output
`Developer.mlua :: Log()` — Client log output

**`/info`** - Display Current State Information
```lua
// Usage: /info
// Function: Output current character/game state information to console
```

## Command Implementation Examples

### Meso Give Command
- `Developer.mlua :: GiveMeso()` — Meso giving and data saving

### Card Pack Give Command
```lua
method void GiveCardPack(Character character, string packName)
    local cardPackManager = character.Entity.CurrentMap.cardPackManager
    local cards = cardPackManager:OpenCardPack(packName)
    character:GainCards(cards, packName)
    self:Log(string.format("Card pack %s given successfully", packName))
end
```

## Safety Considerations

### Authority Verification
```lua
method boolean IsAuthorized(Character character)
    -- Check developer permissions
    return character.isDeveloper or character.isAdmin
end
```

### Production Build Deactivation
```lua
method void ProcessCommand(string command)
    if not DEBUG_MODE then
        return -- Disabled in release build
    end
    
    -- Process command...
end
```

## Usage Examples

### Test Environment Setup
```
1. /reset - Reset existing data
2. /meso 50000 - Give test meso
3. /card FireBolt - Add test card
4. /pack ClassicPack - Give card pack to build deck
5. /info - Check current state
```

### Balance Testing
```
1. /god - God mode to observe combat
2. /draw 10 - Fill hand with cards
3. /win - Instant victory to check results
```

## References

- `RootDesk/MyDesk/Logics/Developer.mlua` - Developer commands implementation
- `1. 핵심 아키텍처/소셜 시스템/채팅 시스템.md` - Chat system integration

This developer commands system is a core tool that greatly simplifies the development and testing process of Maple Duel, supporting efficient game development.

# Trigger System

## Overview

The trigger system of Maple Duel is a core mechanism that executes automatic card effects when game events occur. Through `TriggerManager.mlua`, conditional effects for each card are automatically activated at appropriate timing during game progression, providing complex interactions and strategic depth.

## Trigger System Architecture

### Core Components

**TriggerManager.mlua** centrally manages all card triggers.

**Main Properties:**
```lua
property CardManager cardManager = nil
property Duel duel = nil
property ActionManager actionManager = nil
property CommandManager commandManager = nil
property TaskManager taskManager = nil
property History history = nil

property any invoker = nil      -- Object that triggered the trigger
property any receiver = nil     -- Object receiving the trigger  
property table args = nil       -- Trigger arguments
```

## Trigger Execution Mechanism

### InvokeTriggers Method

The starting point for all trigger execution.

```lua
method void InvokeTriggers(table invokerArray, table receiverArray, string triggerKey, table args, table eachArgs, table resultTable)
    -- 1. Handle card reveal
    local cardArray = self:ShareOpenCards(invokerArray, receiverArray, triggerKey, args, eachArgs, resultTable)
    for _, card in ipairs(cardArray) do
        card:Open()
        card:SetFace(false)
    end
    
    -- 2. Execute triggers
    for _, invoker in ipairs(invokerArray) do
        self:RunTriggers(triggerKey, invoker, invoker, eachArgs and eachArgs[invoker] or args, resultTable and resultTable[invoker] or nil)
        for _, receiver in ipairs(receiverArray) do
            if receiver ~= invoker then
                self:RunTriggers(triggerKey, invoker, receiver, eachArgs and eachArgs[invoker] or args, resultTable and resultTable[invoker] or nil)
            end
        end
    end
end
```

### RunTriggers Method

Executes triggers for individual objects.

```lua
method void RunTriggers(string triggerKey, Object invoker, Object receiver, table args, table result)
    if not receiver.triggerNameArray then return end
    
    -- Backup context
    local backupInvoker = self.invoker
    local backupReceiver = self.receiver
    local backupArgs = self.args
    
    -- Set current execution context
    self.invoker = invoker
    self.receiver = receiver
    self.args = args
    
    -- Execute triggers
    local triggerNameArray = _Table:ShallowCopy(receiver.triggerNameArray)
    for _, triggerName in ipairs(triggerNameArray) do
        if self:IsTriggerCondition(triggerKey, triggerName, invoker, receiver, args, result) then
            self:RunTrigger(triggerName, invoker, receiver, args, result)
        end
    end
    
    -- Restore context
    self.invoker = backupInvoker
    self.receiver = backupReceiver
    self.args = backupArgs
end
```

## Trigger Condition System

### Condition Check Mechanism

```lua
method boolean IsTriggerCondition(string triggerKey, string triggerName, Object invoker, Object receiver, table args, table result)
    return _Util:Call(self, triggerName .. "Condition", {triggerKey, invoker, receiver, result, _Table:Unpack(args)})
end
```

### Major Trigger Keys

Trigger keys defined for each game event:

- **"Cast"** - When casting cards
- **"Summon"** - When summoning minions
- **"Death"** - When units die
- **"Damage"** - When receiving damage
- **"Attack"** - When attacking
- **"EndTurn"** - When turn ends
- **"BeginTurn"** - When turn begins

## Card-Specific Trigger Implementation

### AirStrike Card Example

**Trigger Condition:**
```lua
method boolean AirStrikeCondition(string triggerKey, Card invoker, Card receiver)
    return triggerKey == "Cast" and invoker == receiver
end
```

**Trigger Effect:**
```lua
method void AirStrike(Card invoker, Card receiver)
    self.taskManager:RunProcess(function()
        local unitArray = receiver.player.opponent:GetUnits()
        local damage = 3
        
        -- Apply skill damage bonus
        if receiver.player.skillDamage > 0 then
            damage += 4
        end
        
        -- Damage all opponent units
        self.taskManager:Damage(unitArray, receiver, damage, nil, "AirStrike", 0.075)
    end, "AirStrike")
end
```

### ArmorCrash Card Example

**Trigger Condition:**
```lua
method boolean ArmorCrashCondition(string triggerKey, Card invoker, Card receiver)
    return triggerKey == "Cast" and invoker == receiver
end
```

**Trigger Effect:**
```lua
method void ArmorCrash(Card invoker, Card receiver)
    self.taskManager:RunProcess(function()
        -- Set max HP of 2 random opponent minions to 1
        local targets = receiver.player.opponent.field:ShareRandomMinions(2, nil)
        self.taskManager:InsertSetMaxHpEnchantment(targets, 1, nil, nil, "ArmorCrash", nil)
    end, "ArmorCrash")
end
```

### Conditional Trigger Example (ArrowBlow)

**Trigger Condition:**
```lua
method boolean ArrowBlowCondition(string triggerKey, Card invoker, Card receiver)
    return triggerKey == "Cast" and invoker == receiver
end
```

**Trigger Effect:**
```lua
method void ArrowBlow(Card invoker, Card receiver, table result, Minion target)
    self.taskManager:RunProcess(function()
        -- Deal 5 damage to target
        local resultTable = self.taskManager:Damage({target}, receiver.player, 5, nil, "ArrowBlow", nil)
        
        -- Draw 2 cards if target didn't die
        if not resultTable[target].isDead then
            self.taskManager:Draw({[receiver.player] = 2}, nil, false)
        end
    end, "ArrowBlow")
end
```

## Trigger Chain and Complex Effects

### ShareOpenCards Method

Reveals related cards before trigger execution.

```lua
method table ShareOpenCards(table invokerArray, table receiverArray, string triggerKey, table args, table eachArgs, table resultTable)
    local cardArray = {}
    
    for _, invoker in ipairs(invokerArray) do
        for _, receiver in ipairs(receiverArray) do
            if receiver:IsCard() and receiver.triggerNameArray then
                for _, triggerName in ipairs(receiver.triggerNameArray) do
                    if self:IsTriggerCondition(triggerKey, triggerName, invoker, receiver, 
                                               eachArgs and eachArgs[invoker] or args, 
                                               resultTable and resultTable[invoker] or nil) and
                       not _Table:Contains(cardArray, receiver) then
                        table.insert(cardArray, receiver)
                    end
                end
            end
        end
    end
    
    return cardArray
end
```

### Trigger Chain Execution

```lua
-- When triggers cause other triggers
method void ChainTriggerExample(Card invoker, Card receiver)
    self.taskManager:RunProcess(function()
        -- Execute first effect
        self.taskManager:Damage(targetArray, receiver, damage, nil, "ChainEffect1", nil)
        
        -- Trigger chain trigger
        self:InvokeTriggers({receiver}, {receiver.player}, "ChainEffect", {}, nil, nil)
    end, "ChainTriggerExample")
end
```

## Trigger Execution Flow

### Card Cast Trigger Flow

```mermaid
graph TD
    A[Player Casts Card] --> B[TaskManager:PlayCard]
    B --> C[TriggerManager:InvokeTriggers]
    C --> D[triggerKey = "Cast"]
    D --> E[ShareOpenCards]
    E --> F[Card Reveal Animation]
    F --> G[Call RunTriggers]
    G --> H[Check Each Card's triggerNameArray]
    H --> I{Check Condition}
    I -->|Condition Met| J[Execute Trigger Effect]
    I -->|Condition Not Met| K[Next Trigger]
    J --> L[TaskManager:RunProcess]
    L --> M[Execute Actual Game Logic]
    M --> K
    K --> N[All Triggers Complete]
```

### Minion Summon Trigger Flow

```mermaid
graph TD
    A[Cast Minion Card] --> B[Place Minion on Field]
    B --> C[triggerKey = "Summon"]
    C --> D[Check Other Cards' Summon Triggers]
    D --> E["Phantom Summon" and Other Chain Effects]
    E --> F[Execute Trigger Chain]
    F --> G[Finalize Board State]
```

## Advanced Trigger Patterns

### Multi-Target Trigger

```lua
method void MultiTargetExample(Card invoker, Card receiver, table result, table targets)
    self.taskManager:RunProcess(function()
        for _, target in ipairs(targets) do
            -- Individual processing for each target
            local damage = self:CalculateTargetDamage(target)
            self.taskManager:Damage({target}, receiver, damage, nil, "MultiTarget", nil)
        end
    end, "MultiTargetExample")
end
```

### Conditional Chain Trigger

```lua
method void ConditionalChainExample(Card invoker, Card receiver)
    self.taskManager:RunProcess(function()
        local result = self.taskManager:SomeAction()
        
        if result.success then
            -- Trigger additional trigger on success
            self:InvokeTriggers({receiver}, allCards, "Success", {result = result}, nil, nil)
        else
            -- Trigger different trigger on failure
            self:InvokeTriggers({receiver}, allCards, "Failure", {result = result}, nil, nil)
        end
    end, "ConditionalChainExample")
end
```

## Performance Optimization

### Trigger Filtering

```lua
-- Prevent unnecessary trigger execution
method boolean OptimizedTriggerCondition(string triggerKey, Card invoker, Card receiver)
    -- Quick condition check first
    if triggerKey ~= "Cast" then return false end
    if invoker ~= receiver then return false end
    
    -- Complex condition check later
    return self:ComplexConditionCheck(invoker, receiver)
end
```

### Context Management

Safely handles nested trigger execution by backing up and restoring context during trigger execution.

## Debugging and Logging

### Trigger Execution Tracking

```lua
method void RunTrigger(string triggerName, any invoker, any receiver, table args, table result)
    -- Debug logging
    if DEBUG_TRIGGERS then
        log(string.format("Trigger: %s, Invoker: %s, Receiver: %s", 
                         triggerName, tostring(invoker), tostring(receiver)))
    end
    
    _Util:Call(self, triggerName, {invoker, receiver, result, _Table:Unpack(args)})
end
```

## Code Reference

### Core Files
- `RootDesk/MyDesk/Components/Managers/TriggerManager.mlua` — Trigger system main logic
- `RootDesk/MyDesk/Components/Managers/TaskManager.mlua` — Task management for trigger effect execution
- `RootDesk/MyDesk/Components/Managers/ActionManager.mlua` — Trigger action animation handling

### Major Methods
- `TriggerManager:InvokeTriggers()` — Trigger execution starting point
- `TriggerManager:RunTriggers()` — Individual object trigger execution  
- `TriggerManager:IsTriggerCondition()` — Trigger condition check
- `TriggerManager:ShareOpenCards()` — Reveal cards that will trigger

## Trigger System Features

### Advantages
1. **Automation**: Automatic effect execution when conditions are met
2. **Extensibility**: Only need to implement triggers when adding new cards
3. **Chain Support**: Triggers can cause other triggers
4. **Timing Accuracy**: Precisely synchronized with game events

### Design Principles
1. **Naming Convention**: `[CardName]` and `[CardName]Condition` pairs
2. **State Integrity**: Context preservation during trigger execution
3. **Performance**: Minimize unnecessary trigger execution
4. **Readability**: Independent trigger logic for each card

This trigger system is the core engine that implements the complexity and strategic depth of Maple Duel as a card game, enabling hundreds of card effects to interact organically.

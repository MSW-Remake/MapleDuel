# Debugging and Testing Guide

## Overview

Efficient debugging and testing during Maple Duel development is key to ensuring game quality. This guide presents debugging techniques in MapleStory Worlds environment, log checking methods, performance monitoring, and systematic testing approaches.

## Logging System

### Basic Logging
**Log Output Functions:**
- `log()` — Basic debug message output
- Debug mode distinction through conditional logging

### Developer Log Functions
- `_Developer:Log()` — Developer-exclusive detailed log output

## Error Handling

### Safe Method Calls
**Using pcall:**
- `pcall()` — Safe function execution
- Returns execution success status and result/error message

### Server Communication Error Handling
- `Server.mlua :: Send()` — Safe server method execution
- Error handling through combination of `_Util.Call` and `pcall`

## Performance Monitoring

### Execution Time Measurement
**Performance Measurement:**
- Execution time measurement using `_DateTime:GetTime()`
- Performance analysis through start/end time difference calculation

### Memory Usage Check
**Resource Cleanup:**
- `tweener:Destroy()` — Tweener cleanup
- `_TimerService:ClearTimer()` — Timer cleanup

## Client-Server Synchronization Debugging

### State Inconsistency Verification
**Synchronization Validation:**
- Log output for client/server states separately
- Distinguish execution environment with `@ExecSpace` annotation

### Command Synchronization Tracking
- `CommandManager.mlua :: RunCommand()` — Command execution log
- Resolve synchronization issues by tracking command names and IDs

## Gameplay Testing

### Automated Test Bot Usage
```lua
-- Automated testing using Bot.mlua
bot:SetTestMode(true)
bot:PlayRandomCards(10) -- 10 turns of auto-play
bot:CheckGameState() -- Verify game state
```

### Scenario Testing
```lua
-- Reproduce specific situation
function TestCardCombo()
    player:AddCardToHand("FireBolt")
    player:AddCardToHand("IceSpear") 
    player:SetMP(10)
    
    -- Execute combo
    player:PlayCard("FireBolt")
    player:PlayCard("IceSpear")
    
    -- Verify results
    assert(enemy.hp == expectedHp, "Damage calculation error")
end
```

## UI Testing

### Module State Verification
```lua
-- Debug UIManager state
method void DebugUIState()
    log(string.format("Currently open modules: %d", self:GetOpenModuleCount()))
    
    for moduleName, module in pairs(self.modules) do
        if module.isOpen then
            log(string.format("Open module: %s", moduleName))
        end
    end
end
```

### Animation Testing
```lua
-- Verify tweening animation
local tweener = _Tween:MoveTo(entity, targetPos, 1.0, EaseType.Linear)
_TimerService:SetTimerOnce(function()
    local currentPos = entity.TransformComponent.WorldPosition
    assert(math.abs(currentPos.x - targetPos.x) < 0.1, "Animation position error")
end, 1.1)
```

## Data Integrity Testing

### Save/Load Verification
```lua
-- Character data save/load test
function TestDataPersistence()
    local originalMeso = character.meso
    character:SaveData()
    
    -- Change data
    character.meso = 0
    
    -- Load data
    character:LoadData()
    
    assert(character.meso == originalMeso, "Data save/load failed")
end
```

### CSV Data Validation
```lua
-- Card.csv data validity check
function ValidateCardData()
    local cardManager = _CardManager
    local dataSet = cardManager.dataSet
    
    for i = 1, dataSet:GetRowCount() do
        local name = dataSet:GetValue(i, "name")
        local cost = dataSet:GetValue(i, "cost")
        
        assert(cost >= 0 and cost <= 10, 
               string.format("Card %s cost out of range: %d", name, cost))
    end
end
```

## Network Testing

### Connection State Monitoring
```lua
-- Check server request status
if _Server:IsRequesting() then
    log("Server request in progress...")
else
    log("Server request completed")
end
```

### Packet Loss Simulation
```lua
-- Test intentional request failure
method void TestNetworkFailure()
    -- Assume network request failure scenario
    if math.random() < 0.1 then -- 10% failure chance
        log("Network request failure simulation")
        return
    end
    
    -- Normal processing
    _Server:Request(component, methodName, args)
end
```

## Regression Testing

### Existing Function Verification
```lua
-- Core gameplay function test suite
function RegressionTestSuite()
    TestCardPlay()
    TestMinionSummon()
    TestCombatSystem()
    TestTurnManagement()
    TestDeckManagement()
    
    log("Regression testing complete")
end
```

## Performance Testing

### Large Data Processing
```lua
-- Performance test with many cards
function TestPerformanceWithManyCards()
    local startTime = _DateTime:GetTime()
    
    for i = 1, 1000 do
        local card = CreateTestCard(i)
        player:AddCard(card)
    end
    
    local endTime = _DateTime:GetTime()
    log(string.format("1000 cards processing time: %f seconds", endTime - startTime))
end
```

### Memory Leak Detection
```lua
-- Track object creation/destruction
local objectCount = 0

function CreateTrackedObject()
    objectCount = objectCount + 1
    local obj = CreateObject()
    obj.destroy = function()
        objectCount = objectCount - 1
        DestroyObject(obj)
    end
    return obj
end

function CheckMemoryLeak()
    log(string.format("Current active objects: %d", objectCount))
end
```

## Test Automation

### Unit Test Framework
```lua
local TestFramework = {}

function TestFramework:Assert(condition, message)
    if not condition then
        error("Test failed: " .. (message or "condition not met"))
    end
end

function TestFramework:RunTest(testFunction, testName)
    log("Test started: " .. testName)
    
    local success, result = pcall(testFunction)
    
    if success then
        log("Test passed: " .. testName)
    else
        log("Test failed: " .. testName .. " - " .. tostring(result))
    end
end
```

### Integration Test Execution
```lua
-- Execute all tests
function RunAllTests()
    TestFramework:RunTest(TestCardSystem, "Card System")
    TestFramework:RunTest(TestDuelSystem, "Duel System")
    TestFramework:RunTest(TestUISystem, "UI System")
    TestFramework:RunTest(TestNetworking, "Network System")
end
```

## Debugging Tool Usage

### Extending Developer Commands
```lua
-- Add debugging commands
Developer.commands["/debug"] = function(args)
    local debugInfo = {
        playerCount = _UserService:GetPlayerCount(),
        gameTime = _DateTime:GetTime(),
        memoryUsage = GetMemoryUsage()
    }
    
    for key, value in pairs(debugInfo) do
        log(string.format("%s: %s", key, tostring(value)))
    end
end
```

## Best Practices

### Log Level Management
```lua
local LogLevel = {
    DEBUG = 1,
    INFO = 2, 
    WARNING = 3,
    ERROR = 4
}

function LogWithLevel(level, message)
    if CURRENT_LOG_LEVEL <= level then
        log(string.format("[%s] %s", GetLogLevelName(level), message))
    end
end
```

### Test Data Management
```lua
-- Create test-specific data
function CreateTestCharacter()
    local testChar = Character:new()
    testChar.name = "TestPlayer"
    testChar.meso = 10000
    testChar.level = 1
    return testChar
end
```

Using this debugging and testing guide, you can effectively identify and resolve various issues that arise during Maple Duel development, significantly improving game stability and quality.

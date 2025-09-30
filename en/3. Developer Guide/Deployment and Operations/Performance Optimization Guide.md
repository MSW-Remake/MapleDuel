# Performance Optimization Guide

## Overview

Performance optimization in Maple Duel is a core element that ensures smooth gameplay in mobile environments. This guide presents various optimization techniques including object pooling, resource management, network optimization, and memory management.

## Object Pooling Optimization

### Card Object Pooling
```lua
-- Card pooling system in Duel.mlua
@Component  
script Duel extends Component
    property table cardPool = {}
    property table minionPool = {}
    property integer maxPoolSize = 50
    
    method Card GetPooledCard()
        if #self.cardPool > 0 then
            local card = table.remove(self.cardPool)
            card:Reset() -- Reset card state
            return card
        else
            -- Create new card if pool is empty
            return self:CreateNewCard()
        end
    end
    
    method void ReturnCardToPool(Card card)
        if #self.cardPool < self.maxPoolSize then
            card:Hide()
            card.isActive = false
            table.insert(self.cardPool, card)
        else
            -- Destroy card if pool is full
            card:Destroy()
        end
    end
    
    method Card CreateNewCard()
        local cardEntity = _SpawnService:SpawnByModelId(
            _EntryService:GetModelIdByName("Card"), 
            "Card"
        )
        local card = cardEntity:GetComponentByType(Card)
        return card
    end
end
```

### Minion Object Pooling
```lua
-- Minion pooling optimization
method Minion GetPooledMinion(string minionName)
    local pool = self.minionPools[minionName]
    if not pool then
        pool = {}
        self.minionPools[minionName] = pool
    end
    
    if #pool > 0 then
        local minion = table.remove(pool)
        minion:Reset()
        minion:Show()
        return minion
    else
        return self:CreateNewMinion(minionName)
    end
end

method void ReturnMinionToPool(Minion minion)
    local minionName = minion.name
    local pool = self.minionPools[minionName]
    
    if #pool < MAX_MINION_POOL_SIZE then
        minion:Hide()
        minion:ResetToDefaults()
        table.insert(pool, minion)
    else
        minion:Destroy()
    end
end
```

### Effect Object Pooling
```lua
-- Effect.mlua pooling optimization
@Logic
script Effect extends Logic
    property table effectPool = {}
    
    @ExecSpace("ClientOnly")
    method Entity GetPooledEffect(string effectName)
        local pool = self.effectPool[effectName]
        if not pool then
            pool = {}
            self.effectPool[effectName] = pool
        end
        
        if #pool > 0 then
            local effect = table.remove(pool)
            effect.IsActive = true
            return effect
        else
            return self:CreateEffect(effectName)
        end
    end
    
    @ExecSpace("ClientOnly")
    method void ReturnEffectToPool(Entity effect, string effectName)
        effect.IsActive = false
        effect.TransformComponent.WorldPosition = Vector3(0, -1000, 0) -- Move off-screen
        
        local pool = self.effectPool[effectName]
        if #pool < MAX_EFFECT_POOL_SIZE then
            table.insert(pool, effect)
        else
            _SpawnService:Destroy(effect)
        end
    end
end
```

## Memory Management Optimization

### Garbage Collection Optimization
```lua
-- Memory usage monitoring and optimization
@Logic
script MemoryManager extends Logic
    property number lastGCTime = 0
    property number gcThreshold = 50 * 1024 * 1024 -- 50MB
    
    method void OnUpdate()
        local currentMemory = self:GetMemoryUsage()
        local currentTime = _DateTime:GetTime()
        
        -- Perform GC if memory usage exceeds threshold or every 30 seconds
        if currentMemory > self.gcThreshold or 
           currentTime - self.lastGCTime > 30 then
            self:OptimizeMemory()
            self.lastGCTime = currentTime
        end
    end
    
    method void OptimizeMemory()
        -- Clean up unused tweeners
        self:CleanupTweeners()
        
        -- Clean up timers
        self:CleanupTimers()
        
        -- Clean up event listeners
        self:CleanupEventListeners()
        
        -- Clean up texture cache
        self:CleanupTextureCache()
        
        -- Force garbage collection
        collectgarbage("collect")
    end
    
    method void CleanupTweeners()
        for entity, tweeners in pairs(_GlobalTweeners) do
            if not isvalid(entity) then
                for _, tweener in ipairs(tweeners) do
                    tweener:Destroy()
                end
                _GlobalTweeners[entity] = nil
            end
        end
    end
end
```

### Texture Memory Optimization
```lua
-- Texture loading and unloading optimization
method void OptimizeTextureMemory()
    -- Unload textures of cards not visible on screen
    for _, card in ipairs(self:GetAllCards()) do
        if not card:IsVisible() and card.texture then
            _ResourceService:UnloadTexture(card.texture)
            card.texture = nil
        end
    end
    
    -- Unload unused UI textures
    for moduleName, module in pairs(self.uiManager.modules) do
        if not module.isOpen then
            module:UnloadTextures()
        end
    end
end
```

## Rendering Optimization

### Batching Optimization
```lua
-- Optimizing draw calls for UI elements
method void OptimizeUIRendering()
    -- Render UI elements using the same atlas together
    local sortingGroups = {}
    
    for _, uiElement in ipairs(self:GetActiveUIElements()) do
        local atlas = uiElement:GetAtlasName()
        if not sortingGroups[atlas] then
            sortingGroups[atlas] = {}
        end
        table.insert(sortingGroups[atlas], uiElement)
    end
    
    -- Set sorting layers by group
    local layerIndex = 0
    for atlas, elements in pairs(sortingGroups) do
        for _, element in ipairs(elements) do
            element:SetSortingLayer("UI", layerIndex)
        end
        layerIndex += 1
    end
end
```

### LOD (Level of Detail) System
```lua
-- Detail adjustment based on distance
method void ApplyLOD(Entity entity, number distanceFromCamera)
    local lodLevel = self:CalculateLODLevel(distanceFromCamera)
    
    if lodLevel == 0 then
        -- High quality (close distance)
        entity:SetTextureQuality("High")
        entity:SetAnimationQuality("High")
    elseif lodLevel == 1 then
        -- Medium quality
        entity:SetTextureQuality("Medium")
        entity:SetAnimationQuality("Medium")
    else
        -- Low quality (far distance)
        entity:SetTextureQuality("Low")
        entity:SetAnimationQuality("Low")
    end
end

method integer CalculateLODLevel(number distance)
    if distance < 5 then return 0
    elseif distance < 15 then return 1
    else return 2 end
end
```

## Network Optimization

### Data Packet Optimization
```lua
-- CommandManager network optimization
method void OptimizeNetworking()
    -- Command batching - send multiple commands at once
    if #self.pendingCommands > 1 then
        local batchedCommand = {
            type = "BATCH",
            commands = self.pendingCommands,
            timestamp = _DateTime:GetTime()
        }
        
        _Server:SendCommand(batchedCommand)
        self.pendingCommands = {}
    end
end

-- Data compression
method table CompressGameData(table data)
    -- Remove duplicate data
    local compressed = {}
    local references = {}
    
    for key, value in pairs(data) do
        if references[value] then
            compressed[key] = {type = "ref", id = references[value]}
        else
            local refId = #references + 1
            references[value] = refId
            compressed[key] = {type = "data", value = value, id = refId}
        end
    end
    
    return compressed
end
```

### Predictive Loading
```lua
-- Preloading through player behavior prediction
method void PredictiveLoading(Player player)
    -- Predict likely card plays by analyzing player's hand
    local likelyCards = self:AnalyzeHandForLikelyPlays(player.hand)
    
    for _, cardName in ipairs(likelyCards) do
        -- Preload card effects
        local cardData = self.cardManager:GetCardData(cardName)
        if cardData.effectName then
            _ResourceService:PreloadEffect(cardData.effectName)
        end
        
        -- Preload card sounds
        if cardData.soundRUID then
            _ResourceService:PreloadSound(cardData.soundRUID)
        end
    end
end

method table AnalyzeHandForLikelyPlays(Hand hand)
    local likelyCards = {}
    local player = hand:GetPlayer()
    
    for _, card in ipairs(hand:GetCards()) do
        -- Cards with MP cost equal to or less than current MP
        if card.cost <= player.mp then
            table.insert(likelyCards, card.name)
        end
    end
    
    return likelyCards
end
```

## Animation Optimization

### Animation Culling
```lua
-- Disable animations not visible on screen
method void OptimizeAnimations()
    for _, entity in ipairs(self:GetAllAnimatedEntities()) do
        if not self:IsEntityVisible(entity) then
            -- Stop animations for off-screen entities
            local animator = entity:GetComponentByType(StateAnimationComponent)
            if animator then
                animator.IsEnabled = false
            end
        else
            -- Resume animations for on-screen entities
            local animator = entity:GetComponentByType(StateAnimationComponent)
            if animator then
                animator.IsEnabled = true
            end
        end
    end
end

method boolean IsEntityVisible(Entity entity)
    local bounds = entity:GetBounds()
    local camera = _CameraService.MainCamera
    local frustum = camera:GetFrustum()
    
    return frustum:ContainsBounds(bounds)
end
```

### Dynamic Animation Quality Adjustment
```lua
-- Auto-adjust animation quality based on performance
method void AdjustAnimationQuality()
    local frameRate = self:GetCurrentFrameRate()
    local targetFrameRate = 60
    
    if frameRate < targetFrameRate * 0.8 then -- Below 48fps
        -- Lower animation quality
        for _, entity in ipairs(self:GetAllAnimatedEntities()) do
            local animator = entity:GetComponentByType(StateAnimationComponent)
            if animator then
                animator.PlaybackSpeed = 0.5 -- Reduce animation speed
                animator.UpdateMode = "FrameSkip" -- Frame skip mode
            end
        end
        
        self.currentQuality = "Low"
    elseif frameRate > targetFrameRate * 0.95 then -- Above 57fps
        -- Restore animation quality
        for _, entity in ipairs(self:GetAllAnimatedEntities()) do
            local animator = entity:GetComponentByType(StateAnimationComponent)
            if animator then
                animator.PlaybackSpeed = 1.0
                animator.UpdateMode = "Normal"
            end
        end
        
        self.currentQuality = "High"
    end
end
```

## UI Optimization

### UI Update Optimization
```lua
-- Update UI only when necessary
method void OptimizeUIUpdates()
    -- Use dirty flag system
    for _, module in pairs(self.uiManager.modules) do
        if module.isDirty and module.isVisible then
            module:UpdateUI()
            module.isDirty = false
        end
    end
end

-- Scroll view optimization (virtualization)
method void VirtualizeScrollView(ScrollView scrollView)
    local viewportHeight = scrollView:GetViewportHeight()
    local itemHeight = scrollView:GetItemHeight()
    local visibleCount = math.ceil(viewportHeight / itemHeight) + 2 -- 2 extra items
    
    local scrollPosition = scrollView:GetScrollPosition()
    local firstVisibleIndex = math.floor(scrollPosition / itemHeight)
    
    -- Activate only items in visible range
    for i = 1, scrollView:GetTotalItemCount() do
        local item = scrollView:GetItem(i)
        
        if i >= firstVisibleIndex and i < firstVisibleIndex + visibleCount then
            item:SetActive(true)
            item:UpdateContent()
        else
            item:SetActive(false)
        end
    end
end
```

## Database Optimization

### Query Optimization
```lua
-- Efficient data retrieval
method table GetOptimizedCardData(table cardNames)
    -- Retrieve multiple card data with single query
    local cardDataMap = {}
    local dataSet = _DataService:GetTable("Card")
    
    -- Fast search using index
    for _, cardName in ipairs(cardNames) do
        local index = self.cardNameIndex[cardName]
        if index then
            cardDataMap[cardName] = dataSet:GetRow(index)
        end
    end
    
    return cardDataMap
end

-- Data caching
method void CacheFrequentData()
    -- Cache frequently used data in memory
    self.cachedData = {
        commonCards = self:GetCommonCards(),
        basicDecks = self:GetBasicDecks(),
        uiTexts = self:GetUITexts()
    }
end
```

## Performance Monitoring

### Real-time Performance Tracking
```lua
-- Performance metrics collection
@Component
script PerformanceMonitor extends Component
    property table metrics = {}
    
    method void TrackPerformance(string metricName, function func, ...)
        local startTime = _DateTime:GetHighResolutionTime()
        local result = func(...)
        local endTime = _DateTime:GetHighResolutionTime()
        
        local duration = endTime - startTime
        
        if not self.metrics[metricName] then
            self.metrics[metricName] = {
                totalTime = 0,
                callCount = 0,
                maxTime = 0,
                minTime = math.huge
            }
        end
        
        local metric = self.metrics[metricName]
        metric.totalTime += duration
        metric.callCount += 1
        metric.maxTime = math.max(metric.maxTime, duration)
        metric.minTime = math.min(metric.minTime, duration)
        
        return result
    end
    
    method table GetPerformanceReport()
        local report = {}
        
        for metricName, metric in pairs(self.metrics) do
            report[metricName] = {
                averageTime = metric.totalTime / metric.callCount,
                maxTime = metric.maxTime,
                minTime = metric.minTime,
                callCount = metric.callCount,
                totalTime = metric.totalTime
            }
        end
        
        return report
    end
end
```

### Automatic Performance Adjustment
```lua
-- Auto quality adjustment based on performance
method void AutoAdjustQuality()
    local performanceScore = self:CalculatePerformanceScore()
    
    if performanceScore < 0.5 then
        -- Low performance: optimization mode
        self:EnablePerformanceMode()
    elseif performanceScore > 0.8 then
        -- High performance: quality mode
        self:EnableQualityMode()
    end
end

method void EnablePerformanceMode()
    -- Reduce effect quality
    _Effect:SetQuality("Low")
    
    -- Reduce texture resolution
    _ResourceService:SetTextureQuality(0.5)
    
    -- Limit animation frame rate
    _AnimationService:SetMaxFrameRate(30)
    
    -- Increase UI update interval
    self.uiUpdateInterval = 0.1
end

method void EnableQualityMode()
    -- Restore effect quality
    _Effect:SetQuality("High")
    
    -- Restore texture resolution
    _ResourceService:SetTextureQuality(1.0)
    
    -- Restore animation frame rate
    _AnimationService:SetMaxFrameRate(60)
    
    -- Decrease UI update interval
    self.uiUpdateInterval = 0.033
end
```

## Platform-Specific Optimization

### Mobile Optimization
```lua
-- Mobile device detection and optimization
method void OptimizeForMobile()
    if _DeviceService:IsMobile() then
        -- Battery saver mode
        self:EnableBatterySaver()
        
        -- Touch optimization
        self:OptimizeTouchInput()
        
        -- Memory optimization
        self:AggressiveMemoryCleanup()
    end
end

method void EnableBatterySaver()
    -- Limit background animations
    for _, bgAnimation in ipairs(self:GetBackgroundAnimations()) do
        bgAnimation:SetFrameRate(15) -- Limit to 15fps
    end
    
    -- Optimize particle systems
    for _, particle in ipairs(self:GetParticleSystems()) do
        particle:SetMaxParticles(particle:GetMaxParticles() * 0.5)
    end
end
```

These comprehensive performance optimization techniques enable Maple Duel to provide stable and smooth gameplay experience across various device environments.

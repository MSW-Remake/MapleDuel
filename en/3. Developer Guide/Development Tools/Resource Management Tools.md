# Resource Management Tools

## Overview

Resource management in Maple Duel directly impacts game performance and development efficiency as a core element. This guide presents effective resource management methods using `ResourceManager.mlua` and asset organization best practices.

## ResourceManager.mlua Usage

### Basic Resource Structure
```lua
-- ResourceManager.mlua basic structure
@Component
script ResourceManager extends Component
    property table cardResource = {}
    property table uiResource = {}  
    property table effectResource = {}
    property table soundResource = {}
    
    @ExecSpace("ClientOnly")
    method void OnBeginPlay()
        self:LoadAllResources()
    end
end
```

### Resource Group Management
```lua
-- Card-related resources
method void LoadCardResources()
    self.cardResource = {
        -- Card frames
        frames = {
            common = "CommonCardFrame",
            rare = "RareCardFrame", 
            epic = "EpicCardFrame",
            unique = "UniqueCardFrame",
            legendary = "LegendaryCardFrame"
        },
        -- Job-specific backgrounds
        jobBackgrounds = {
            warrior = "WarriorCardBg",
            magician = "MagicianCardBg",
            bowman = "BowmanCardBg",
            thief = "ThiefCardBg", 
            pirate = "PirateCardBg"
        }
    }
end

-- UI-related resources
method void LoadUIResources()
    self.uiResource = {
        -- Common UI elements
        common = {
            buttonNormal = "ButtonNormal",
            buttonHover = "ButtonHover", 
            buttonPressed = "ButtonPressed",
            panelBg = "PanelBackground",
            scrollBar = "ScrollBar"
        },
        -- Module-specific UI
        modules = {
            lobby = "LobbyPanelBg",
            shop = "ShopPanelBg", 
            card = "CardPanelBg",
            duel = "DuelPanelBg"
        }
    }
end

-- Effect-related resources
method void LoadEffectResources()
    self.effectResource = {
        -- Combat effects
        combat = {
            hit = "HitEffect",
            death = "DeathEffect",
            heal = "HealEffect",
            damage = "DamageEffect"
        },
        -- UI effects  
        ui = {
            cardDraw = "CardDrawEffect",
            buttonClick = "ButtonClickEffect",
            pageTransition = "PageTransitionEffect"
        }
    }
end
```

## Resource Loading Optimization

### Preloading System
```lua
-- Pre-load essential resources
@ExecSpace("ClientOnly")
method void PreloadCriticalResources()
    local criticalResources = {
        -- Resources absolutely needed at game start
        "LobbyBackground",
        "MainMenuMusic", 
        "CommonCardFrame",
        "BasicUIElements"
    }
    
    _ResourceService:PreloadAsync(criticalResources, function(progress)
        self:UpdateLoadingProgress(progress)
    end)
end

-- Contextual resource loading
method void PreloadForDuel()
    local duelResources = {
        -- Resources needed for duels
        "DuelField",
        "TurnTimer",
        "MinionModels", 
        "SkillEffects",
        "CombatSounds"
    }
    
    _ResourceService:PreloadAsync(duelResources)
end

method void PreloadForShop() 
    local shopResources = {
        "CardPackModels",
        "ShopBackground",
        "CoinEffects",
        "PurchaseSounds"
    }
    
    _ResourceService:PreloadAsync(shopResources)
end
```

### Lazy Loading
```lua
-- Resources loaded only when needed
method string GetResource(string category, string resourceName)
    if not self.loadedResources[category] then
        self.loadedResources[category] = {}
    end
    
    if not self.loadedResources[category][resourceName] then
        -- Load only on first request
        self.loadedResources[category][resourceName] = self:LoadResourceFromDisk(category, resourceName)
    end
    
    return self.loadedResources[category][resourceName]
end
```

## Asset Organization Guide

### Folder Structure Optimization
```
RootDesk/MyDesk/
├── Images/
│   ├── Cards/           # Card images
│   │   ├── Fronts/      # Card fronts
│   │   ├── Backs/       # Card backs  
│   │   └── Frames/      # Card frames
│   ├── UI/              # UI elements
│   │   ├── Buttons/     # Button images
│   │   ├── Panels/      # Panel backgrounds
│   │   └── Icons/       # Icons
│   └── Effects/         # Effect sprites
├── Models/              # 3D models
│   ├── Cards/           # Card 3D models
│   ├── Minions/         # Minion models
│   └── Environment/     # Environment objects
├── Sounds/              # Sound files
│   ├── BGM/            # Background music
│   ├── SFX/            # Sound effects
│   └── Voice/          # Voice
└── Materials/          # Materials
    ├── Cards/          # Card materials
    └── UI/             # UI materials
```

### Naming Convention Standardization
```lua
-- Apply consistent naming conventions
local NAMING_CONVENTIONS = {
    cards = {
        front = "{cardName}_Front",
        back = "{cardName}_Back", 
        model = "{cardName}_Model"
    },
    ui = {
        button = "{moduleName}_{buttonName}_Btn",
        panel = "{moduleName}_Panel_Bg",
        icon = "{category}_{iconName}_Icon"
    },
    sounds = {
        effect = "{effectName}_SFX",
        bgm = "{sceneName}_BGM",
        voice = "{characterName}_{actionName}_Voice"
    }
}

method string GetStandardResourceName(string category, string type, table params)
    local template = NAMING_CONVENTIONS[category][type]
    return string.format(template, table.unpack(params))
end
```

### Resolution-based Resource Management
```lua
-- Select optimized resources by device
method string GetOptimizedResource(string baseName)
    local screenInfo = _ScreenService:GetScreenInfo()
    local dpi = screenInfo.dpi
    
    if dpi >= 300 then
        -- High-resolution devices
        return baseName .. "_HD"
    elseif dpi >= 200 then
        -- Medium resolution
        return baseName .. "_MD"  
    else
        -- Low resolution
        return baseName .. "_SD"
    end
end
```

## Memory Management

### Resource Caching Strategy
```lua
-- LRU cache implementation
local ResourceCache = {}
ResourceCache.__index = ResourceCache

function ResourceCache:new(maxSize)
    return setmetatable({
        cache = {},
        usage = {},
        maxSize = maxSize or 100,
        currentSize = 0
    }, self)
end

function ResourceCache:get(key)
    local value = self.cache[key]
    if value then
        -- Update usage time
        self.usage[key] = _DateTime:GetTime()
        return value
    end
    return nil
end

function ResourceCache:put(key, value)
    if self.currentSize >= self.maxSize then
        self:evictLeastUsed()
    end
    
    self.cache[key] = value
    self.usage[key] = _DateTime:GetTime()
    self.currentSize += 1
end

function ResourceCache:evictLeastUsed()
    local oldestKey = nil
    local oldestTime = math.huge
    
    for key, time in pairs(self.usage) do
        if time < oldestTime then
            oldestTime = time
            oldestKey = key
        end
    end
    
    if oldestKey then
        self.cache[oldestKey] = nil
        self.usage[oldestKey] = nil
        self.currentSize -= 1
    end
end
```

### Automatic Resource Release
```lua
-- Release unnecessary resources on scene change
method void CleanupSceneResources(string leavingScene)
    local resourcesToCleanup = self.sceneResources[leavingScene]
    
    if resourcesToCleanup then
        for _, resource in ipairs(resourcesToCleanup) do
            if not self:IsSharedResource(resource) then
                _ResourceService:UnloadResource(resource)
            end
        end
        
        self.sceneResources[leavingScene] = nil
    end
end

-- Check if resource is shared
method boolean IsSharedResource(string resourceName)
    local sharedResources = {
        "CommonCardFrame",
        "ButtonNormal", 
        "LoadingIcon",
        "ErrorSound"
    }
    
    return table.contains(sharedResources, resourceName)
end
```

## Resource Validation Tools

### Missing Resource Detection
```lua
-- Resource integrity check at game start
method table ValidateAllResources()
    local missingResources = {}
    
    -- Required resource list
    local requiredResources = self:GetRequiredResourceList()
    
    for category, resources in pairs(requiredResources) do
        for _, resourceName in ipairs(resources) do
            if not self:ResourceExists(resourceName) then
                table.insert(missingResources, {
                    category = category,
                    name = resourceName
                })
            end
        end
    end
    
    if #missingResources > 0 then
        self:LogMissingResources(missingResources)
    end
    
    return missingResources
end

method boolean ResourceExists(string resourceName)
    local success, resource = pcall(function()
        return _ResourceService:GetResource(resourceName)
    end)
    
    return success and resource ~= nil
end
```

### Duplicate Resource Detection
```lua
method table FindDuplicateResources()
    local resourceHashes = {}
    local duplicates = {}
    
    local allResources = _ResourceService:GetAllResources()
    
    for _, resource in ipairs(allResources) do
        local hash = self:CalculateResourceHash(resource)
        
        if resourceHashes[hash] then
            table.insert(duplicates, {
                original = resourceHashes[hash],
                duplicate = resource.name
            })
        else
            resourceHashes[hash] = resource.name
        end
    end
    
    return duplicates
end
```

## Performance Monitoring

### Resource Usage Tracking
```lua
-- Monitor resource memory usage
method table GetResourceUsageStats()
    local stats = {
        totalMemory = 0,
        categoryBreakdown = {},
        topConsumers = {}
    }
    
    for category, resources in pairs(self.loadedResources) do
        local categoryMemory = 0
        
        for resourceName, resource in pairs(resources) do
            local size = self:GetResourceSize(resource)
            categoryMemory += size
            
            table.insert(stats.topConsumers, {
                name = resourceName,
                size = size,
                category = category
            })
        end
        
        stats.categoryBreakdown[category] = categoryMemory
        stats.totalMemory += categoryMemory
    end
    
    -- Sort by memory usage
    table.sort(stats.topConsumers, function(a, b) 
        return a.size > b.size 
    end)
    
    return stats
end

-- Measure resource loading time
method void TrackLoadingPerformance()
    local startTime = _DateTime:GetTime()
    
    -- Resource loading...
    
    local endTime = _DateTime:GetTime()
    local loadTime = endTime - startTime
    
    self.performanceStats.avgLoadTime = 
        (self.performanceStats.avgLoadTime + loadTime) / 2
        
    if loadTime > self.performanceStats.maxLoadTime then
        self.performanceStats.maxLoadTime = loadTime
    end
end
```

## Automation Tools

### Automatic Resource Compression
```lua
-- Optimize resources for build
method void OptimizeResourcesForBuild()
    local imagesToOptimize = self:GetImageResources()
    
    for _, image in ipairs(imagesToOptimize) do
        -- Image compression and optimization
        self:CompressImage(image.path, {
            quality = 85,
            format = "webp",
            maxWidth = 1024,
            maxHeight = 1024
        })
    end
    
    local soundsToOptimize = self:GetSoundResources()
    
    for _, sound in ipairs(soundsToOptimize) do
        -- Audio compression
        self:CompressAudio(sound.path, {
            bitrate = 128,
            format = "ogg"
        })
    end
end
```

### Unused Resource Detection
```lua
method table FindUnusedResources()
    local allResources = _ResourceService:GetAllResources()
    local usedResources = self:ScanCodeForResourceReferences()
    local unusedResources = {}
    
    for _, resource in ipairs(allResources) do
        if not usedResources[resource.name] then
            table.insert(unusedResources, resource.name)
        end
    end
    
    return unusedResources
end
```

## Best Practices

### Resource Loading Priority
```lua
-- Define loading priorities
local LOADING_PRIORITIES = {
    critical = 1,    -- Game start essential
    high = 2,        -- Main gameplay
    medium = 3,      -- General features
    low = 4          -- Additional features
}

method void LoadResourcesByPriority()
    for priority = 1, 4 do
        local resources = self:GetResourcesByPriority(priority)
        self:LoadResourceBatch(resources)
        
        if priority <= 2 then
            -- Wait for complete loading of important resources before next step
            while not self:IsResourceBatchLoaded(resources) do
                _CoroutineService:Wait(0.1)
            end
        end
    end
end
```

### Resource Profiling
```lua
-- Resource usage profiling in development mode
method void StartResourceProfiling()
    if not DEBUG_MODE then return end
    
    self.profilingEnabled = true
    self.resourceAccessLog = {}
    
    _TimerService:SetTimerLoop(function()
        self:LogResourceUsage()
    end, 5.0) -- Log every 5 seconds
end

method void LogResourceUsage()
    local stats = self:GetResourceUsageStats()
    
    log(string.format("Total Memory: %d KB", stats.totalMemory / 1024))
    
    for category, memory in pairs(stats.categoryBreakdown) do
        log(string.format("%s: %d KB", category, memory / 1024))
    end
end
```

Following this resource management guide can significantly optimize Maple Duel's performance and improve development efficiency. Strategic resource management considering memory limitations and loading times in mobile environments plays a crucial role in game success.

# Data Backup and Recovery

## Overview

Safe backup and recovery of player data in Maple Duel is core to service operations. This guide provides detailed explanations of understanding data structures, backup strategies, integrity verification, and data recovery procedures on the MapleStory Worlds platform.

## Understanding Data Structure

### Player Data Hierarchy Structure
```lua
-- Main data fields in Character.mlua
local CHARACTER_DATA_STRUCTURE = {
    -- Basic information
    basic = {
        "name",           -- Character name
        "level",          -- Level
        "exp",            -- Experience
        "meso",           -- Game currency
        "rank",           -- Rank
        "job",            -- Job
        "createdAt",      -- Creation time
        "lastLoginAt"     -- Last login
    },
    
    -- Card collection
    collection = {
        "cardCollection", -- Owned card list
        "cardCount",      -- Card count by type
        "newCards"        -- Newly acquired cards
    },
    
    -- Deck information
    decks = {
        "deckArray",      -- Deck list
        "deckIndex",      -- Currently selected deck index
        "deckJob"         -- Deck job
    },
    
    -- Statistics and records
    stats = {
        "winCount",       -- Win count
        "loseCount",      -- Lose count
        "totalGameCount", -- Total game count
        "maxWinStreak",   -- Maximum win streak
        "achievements"    -- Achievements
    },
    
    -- Settings
    preferences = {
        "soundVolume",    -- Sound volume
        "musicVolume",    -- Music volume
        "autoEndTurn",    -- Auto end turn
        "tutorialComplete" -- Tutorial completion status
    }
}
```

### Data Storage Method
```lua
-- Data saving method in Character.mlua
@ExecSpace("ServerOnly")
method void SaveData()
    local saveData = {
        version = DATA_VERSION,
        timestamp = _DateTime:GetTime(),
        
        -- Basic information
        name = self.name,
        level = self.level,
        exp = self.exp,
        meso = self.meso,
        rank = self.rank,
        job = self.job,
        
        -- Collection data
        cardCollection = self:SerializeCollection(),
        deckArray = self:SerializeDecks(),
        
        -- Statistics data
        stats = self:SerializeStats(),
        
        -- Settings data
        preferences = self:SerializePreferences(),
        
        -- Checksum
        checksum = self:CalculateChecksum()
    }
    
    -- Save to MapleStory Worlds data service
    _DataService:SaveUserData(self.Entity.PlayerEntity.UserId, saveData)
end

-- Collection serialization
method table SerializeCollection()
    local serialized = {}
    
    for cardName, count in pairs(self.cardCollection) do
        serialized[cardName] = {
            count = count,
            firstObtained = self.cardFirstObtained[cardName],
            variants = self.cardVariants[cardName] or {}
        }
    end
    
    return serialized
end

-- Deck serialization
method table SerializeDecks()
    local serialized = {}
    
    for i, deck in ipairs(self.deckArray) do
        if deck then
            serialized[i] = {
                cards = deck.cards,
                job = deck.job,
                name = deck.name,
                createdAt = deck.createdAt,
                lastModified = deck.lastModified
            }
        end
    end
    
    return serialized
end
```

## Backup Strategy

### Auto Backup System
```lua
-- Auto backup scheduler
@Component
script BackupManager extends Component
    property integer backupInterval = 300 -- Every 5 minutes
    property integer maxBackupFiles = 24  -- Keep maximum 24 files (2 hours worth)
    
    @ExecSpace("ServerOnly")
    method void OnBeginPlay()
        self:StartAutoBackup()
    end
    
    method void StartAutoBackup()
        _TimerService:SetTimerLoop(function()
            self:PerformAutoBackup()
        end, self.backupInterval)
    end
    
    method void PerformAutoBackup()
        local allCharacters = _UserService:GetAllCharacters()
        
        for _, character in ipairs(allCharacters) do
            if character:IsDataModified() then
                self:BackupCharacterData(character)
                character:MarkDataClean()
            end
        end
    end
end
```

### Backup Data Compression
```lua
-- Backup data compression and storage
method void BackupCharacterData(Character character)
    local backupData = {
        userId = character.Entity.PlayerEntity.UserId,
        timestamp = _DateTime:GetTime(),
        dataVersion = DATA_VERSION,
        
        -- Player data
        characterData = character:SerializeForBackup(),
        
        -- Metadata
        metadata = {
            backupReason = "auto", -- auto, manual, critical
            gameVersion = GAME_VERSION,
            serverInfo = self:GetServerInfo()
        }
    }
    
    -- Data compression
    local compressedData = self:CompressData(backupData)
    
    -- Generate backup filename
    local backupFileName = string.format("backup_%s_%d.dat", 
        character.Entity.PlayerEntity.UserId, 
        _DateTime:GetTime())
    
    -- Save to cloud storage
    _CloudStorage:SaveBackup(backupFileName, compressedData)
    
    -- Update local backup log
    self:UpdateBackupLog(character.Entity.PlayerEntity.UserId, backupFileName)
end

method string CompressData(table data)
    local jsonString = _MSON:Encode(data)
    return _CompressionService:Compress(jsonString, "gzip")
end
```

### Differential Backup
```lua
-- Differential backup that backs up only changed data
method table CreateDifferentialBackup(Character character)
    local currentData = character:SerializeForBackup()
    local lastBackup = self:GetLastBackupData(character.Entity.PlayerEntity.UserId)
    
    if not lastBackup then
        -- First backup is full backup
        return currentData
    end
    
    local differences = {}
    
    -- Compare data and extract changes
    for key, value in pairs(currentData) do
        if not self:DataEquals(lastBackup[key], value) then
            differences[key] = {
                old = lastBackup[key],
                new = value,
                timestamp = _DateTime:GetTime()
            }
        end
    end
    
    return {
        type = "differential",
        baseBackupId = lastBackup.backupId,
        changes = differences,
        timestamp = _DateTime:GetTime()
    }
end

method boolean DataEquals(any data1, any data2)
    if type(data1) ~= type(data2) then
        return false
    end
    
    if type(data1) == "table" then
        for k, v in pairs(data1) do
            if not self:DataEquals(v, data2[k]) then
                return false
            end
        end
        for k, v in pairs(data2) do
            if data1[k] == nil then
                return false
            end
        end
        return true
    else
        return data1 == data2
    end
end
```

## Data Integrity Verification

### Checksum Verification
```lua
-- Checksum calculation for data integrity
method string CalculateChecksum(table data)
    local dataString = _MSON:Encode(data)
    return _CryptographyService:ComputeHash(dataString, "SHA256")
end

-- Backup data verification
method boolean VerifyBackupIntegrity(table backupData)
    local storedChecksum = backupData.checksum
    backupData.checksum = nil -- Calculate excluding checksum
    
    local calculatedChecksum = self:CalculateChecksum(backupData)
    
    return storedChecksum == calculatedChecksum
end

-- Data consistency check
method table ValidateDataConsistency(table characterData)
    local issues = {}
    
    -- Basic data validation
    if not characterData.name or characterData.name == "" then
        table.insert(issues, "Invalid character name")
    end
    
    if characterData.meso < 0 then
        table.insert(issues, "Negative meso value")
    end
    
    if characterData.level < 1 or characterData.level > MAX_LEVEL then
        table.insert(issues, "Invalid character level")
    end
    
    -- Collection data verification
    local validCardNames = self.cardManager:GetAllValidCardNames()
    for cardName, data in pairs(characterData.cardCollection) do
        if not table.contains(validCardNames, cardName) then
            table.insert(issues, string.format("Invalid card: %s", cardName))
        end
        
        if data.count < 0 or data.count > MAX_CARD_COUNT then
            table.insert(issues, string.format("Invalid card count for %s: %d", cardName, data.count))
        end
    end
    
    -- Deck data verification
    for i, deck in ipairs(characterData.deckArray) do
        if deck then
            local deckIssues = self:ValidateDeck(deck)
            for _, issue in ipairs(deckIssues) do
                table.insert(issues, string.format("Deck %d: %s", i, issue))
            end
        end
    end
    
    return issues
end
```

### Data Recovery Feasibility Check
```lua
method table CheckDataRecovery(string userId)
    local backupHistory = self:GetBackupHistory(userId)
    local recoveryOptions = {}
    
    for _, backup in ipairs(backupHistory) do
        local isValid = self:TestBackupRestoration(backup, true) -- Test mode
        
        table.insert(recoveryOptions, {
            backupId = backup.id,
            timestamp = backup.timestamp,
            dataVersion = backup.dataVersion,
            isRestorable = isValid.success,
            issues = isValid.issues or {},
            dataSize = backup.size
        })
    end
    
    -- Sort by recovery priority
    table.sort(recoveryOptions, function(a, b)
        if a.isRestorable ~= b.isRestorable then
            return a.isRestorable -- Restorable first
        end
        return a.timestamp > b.timestamp -- Latest first
    end)
    
    return recoveryOptions
end
```

## Data Recovery Procedure

### Basic Recovery Process
```lua
-- Main data recovery method
method table RestoreCharacterData(string userId, string backupId)
    local restoreResult = {
        success = false,
        errors = {},
        warnings = {},
        restoredData = nil
    }
    
    -- Step 1: Backup file verification
    local backupData = self:LoadBackupData(backupId)
    if not backupData then
        table.insert(restoreResult.errors, "Backup file not found")
        return restoreResult
    end
    
    -- Step 2: Integrity verification
    if not self:VerifyBackupIntegrity(backupData) then
        table.insert(restoreResult.errors, "Backup integrity check failed")
        return restoreResult
    end
    
    -- Step 3: Data consistency check
    local consistencyIssues = self:ValidateDataConsistency(backupData.characterData)
    if #consistencyIssues > 0 then
        -- Check for critical issues
        local criticalIssues = self:FilterCriticalIssues(consistencyIssues)
        if #criticalIssues > 0 then
            restoreResult.errors = criticalIssues
            return restoreResult
        else
            restoreResult.warnings = consistencyIssues
        end
    end
    
    -- Step 4: Backup current data (for restore failure)
    local character = _UserService:GetCharacterByUserId(userId)
    if character then
        self:CreateEmergencyBackup(character, "pre_restore")
    end
    
    -- Step 5: Execute data restoration
    local success, error = pcall(function()
        self:ApplyRestoredData(userId, backupData.characterData)
    end)
    
    if success then
        restoreResult.success = true
        restoreResult.restoredData = backupData.characterData
        
        -- Log restoration
        self:LogDataRestore(userId, backupId, "SUCCESS")
    else
        table.insert(restoreResult.errors, "Restore execution failed: " .. tostring(error))
        
        -- Rollback on failure
        self:RollbackRestore(userId)
        self:LogDataRestore(userId, backupId, "FAILED", error)
    end
    
    return restoreResult
end
```

### Selective Recovery
```lua
-- Selectively restore specific data only
method table PartialRestore(string userId, string backupId, table restoreOptions)
    local backupData = self:LoadBackupData(backupId)
    local character = _UserService:GetCharacterByUserId(userId)
    
    if not character then
        return {success = false, error = "Character not found"}
    end
    
    local restoredFields = {}
    
    -- Collection restoration
    if restoreOptions.restoreCollection then
        character.cardCollection = backupData.characterData.cardCollection
        character.cardCount = backupData.characterData.cardCount
        table.insert(restoredFields, "collection")
    end
    
    -- Deck restoration
    if restoreOptions.restoreDecks then
        character.deckArray = self:DeserializeDecks(backupData.characterData.deckArray)
        character.deckIndex = backupData.characterData.deckIndex
        table.insert(restoredFields, "decks")
    end
    
    -- Statistics restoration
    if restoreOptions.restoreStats then
        character.winCount = backupData.characterData.winCount
        character.loseCount = backupData.characterData.loseCount
        character.totalGameCount = backupData.characterData.totalGameCount
        table.insert(restoredFields, "stats")
    end
    
    -- Meso/level restoration
    if restoreOptions.restoreProgress then
        character.meso = backupData.characterData.meso
        character.level = backupData.characterData.level
        character.exp = backupData.characterData.exp
        table.insert(restoredFields, "progress")
    end
    
    -- Save changes
    character:SaveData()
    
    return {
        success = true,
        restoredFields = restoredFields,
        timestamp = _DateTime:GetTime()
    }
end
```

### Auto Recovery System
```lua
-- Auto recovery when data corruption is detected
method void AutoRecovery(Character character)
    local issues = self:ValidateDataConsistency(character:SerializeForBackup())
    
    if #issues > 0 then
        -- Attempt recovery
        local recoveryOptions = self:CheckDataRecovery(character.Entity.PlayerEntity.UserId)
        
        for _, option in ipairs(recoveryOptions) do
            if option.isRestorable then
                local restoreResult = self:RestoreCharacterData(
                    character.Entity.PlayerEntity.UserId, 
                    option.backupId
                )
                
                if restoreResult.success then
                    self:NotifyAutoRecovery(character, option.backupId)
                    break
                end
            end
        end
    end
end

method void NotifyAutoRecovery(Character character, string backupId)
    -- Notify player of auto recovery
    local message = string.format(
        "Data integrity issue detected and automatically recovered from %s backup.",
        _DateTime:FormatTime(self:GetBackupTimestamp(backupId))
    )
    
    character:SendSystemMessage(message)
    
    -- Also notify administrator
    self:NotifyAdminAutoRecovery(character.Entity.PlayerEntity.UserId, backupId)
end
```

## Backup Data Management

### Backup File Cleanup
```lua
-- Clean up old backup files
method void CleanupOldBackups()
    local retentionDays = 30 -- Keep for 30 days
    local cutoffTime = _DateTime:GetTime() - (retentionDays * 24 * 3600)
    
    local allBackups = _CloudStorage:ListBackups()
    
    for _, backup in ipairs(allBackups) do
        if backup.timestamp < cutoffTime then
            -- Check if it's an important backup
            if not self:IsImportantBackup(backup) then
                _CloudStorage:DeleteBackup(backup.id)
                self:LogBackupDeletion(backup.id, "expired")
            end
        end
    end
end

method boolean IsImportantBackup(table backup)
    -- Important milestone backups (level up, rank up, etc.)
    if backup.metadata.milestone then
        return true
    end
    
    -- Manual backups
    if backup.metadata.backupReason == "manual" then
        return true
    end
    
    -- Backups used for restoration
    if backup.metadata.usedForRestore then
        return true
    end
    
    return false
end
```

### Backup Monitoring
```lua
-- Backup system status monitoring
method table GetBackupSystemStatus()
    local status = {
        lastBackupTime = self:GetLastBackupTime(),
        totalBackups = self:GetTotalBackupCount(),
        failedBackups = self:GetFailedBackupCount(),
        storageUsed = self:GetBackupStorageUsage(),
        healthScore = 0
    }
    
    -- Calculate health score
    local timeSinceLastBackup = _DateTime:GetTime() - status.lastBackupTime
    
    if timeSinceLastBackup < 600 then -- Within 10 minutes
        status.healthScore += 30
    elseif timeSinceLastBackup < 1800 then -- Within 30 minutes  
        status.healthScore += 20
    else
        status.healthScore += 10
    end
    
    local failureRate = status.failedBackups / math.max(status.totalBackups, 1)
    if failureRate < 0.01 then -- Less than 1%
        status.healthScore += 40
    elseif failureRate < 0.05 then -- Less than 5%
        status.healthScore += 30
    else
        status.healthScore += 10
    end
    
    if status.storageUsed < 0.8 then -- Less than 80%
        status.healthScore += 30
    elseif status.storageUsed < 0.95 then -- Less than 95%
        status.healthScore += 20
    else
        status.healthScore += 5
    end
    
    return status
end
```

## Management Tools

### Administrator Recovery Tool
```lua
-- Administrator data recovery interface
@AdminOnly
method table AdminRestoreData(string userId, table options)
    -- Check administrator permissions
    if not self:IsAdmin(_UserService.LocalPlayer) then
        return {success = false, error = "Insufficient permissions"}
    end
    
    -- Validate restore options
    local validOptions = self:ValidateRestoreOptions(options)
    if not validOptions.isValid then
        return {success = false, errors = validOptions.errors}
    end
    
    -- Execute restoration
    local result = self:RestoreCharacterData(userId, options.backupId)
    
    -- Log administrator action
    self:LogAdminAction(_UserService.LocalPlayer, "DATA_RESTORE", {
        targetUserId = userId,
        backupId = options.backupId,
        result = result.success
    })
    
    return result
end
```

### Data Migration
```lua
-- Data migration when data structure changes
method void MigrateUserData(string userId, string fromVersion, string toVersion)
    local character = _UserService:GetCharacterByUserId(userId)
    if not character then return end
    
    local migrator = self.migrators[fromVersion .. "_to_" .. toVersion]
    if not migrator then
        error("No migrator found for " .. fromVersion .. " to " .. toVersion)
    end
    
    -- Backup before migration
    self:CreateEmergencyBackup(character, "pre_migration")
    
    -- Execute migration
    local success, result = pcall(migrator.migrate, character)
    
    if success then
        character.dataVersion = toVersion
        character:SaveData()
        self:LogDataMigration(userId, fromVersion, toVersion, "SUCCESS")
    else
        self:LogDataMigration(userId, fromVersion, toVersion, "FAILED", result)
        error("Migration failed: " .. tostring(result))
    end
end
```

This backup and recovery system comprehensively protects Maple Duel players' valuable game data and enables rapid recovery when issues occur.

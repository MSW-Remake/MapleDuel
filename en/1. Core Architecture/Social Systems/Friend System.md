# Friend System

## Overview

Maple Duel's friend system is a core social feature that enables social interaction between players. It provides functions such as adding/removing friends, managing friend requests, checking online status, and friend follow (visit) functionality.

## Core Components

### SocialModule.mlua
The main interface for social UI, responsible for displaying friend lists and handling friend requests.

**Key Features:**
- Friend list pagination display (7 friends per page)
- Friend request popup handling
- Real-time friend status updates (refreshed every 5 seconds)
- Rank and profile information display

```lua
-- Core logic for displaying friend list by pages
method void ShowFriendSlots(integer pageIndex)
    self.pageIndex = pageIndex
    
    local character = _UserService.LocalPlayer.Character
    local start = 1 + 7 * (pageIndex - 1)
    local finish = math.min(7 * pageIndex, #self.userIdArray)
    local userIdArray = {}
    for i = start, finish do
        table.insert(userIdArray, self.userIdArray[i])
    end
    _Server:Request(character.Entity.CurrentMap.Map, "GetFriends", {character, userIdArray})
end
```

### InteractionModule.mlua
Component that handles direct interactions with other players.

**Key Features:**
- Send friend requests to other players
- Remove friendship with existing friends
- UI positioning based on target player location

```lua
-- Friend request/remove button state management
method void SetFriendButton(boolean isFriendWithOther)
    self.isFriendWithOther = isFriendWithOther
    
    local resource = self.resourceManager:GetResource("InteractionModule")
    if self.isFriendWithOther then
        self.friendButton.Entity.SpriteGUIRendererComponent.ImageRUID = resource.unfriend
        self.friendButtonText.Text = _LocalizationService:GetText("Unfriend")
    else
        self.friendButton.Entity.SpriteGUIRendererComponent.ImageRUID = resource.friendRequest
        self.friendButtonText.Text = _LocalizationService:GetText("FriendRequest")
    end
end
```

### FriendSlot.mlua
Slot component that displays and manages individual friend information.

**Key Features:**
- Separate display for online/offline friend status
- Display friend's current location info (channel, room, game mode)
- Friend removal and follow functionality

```lua
-- Set online friend information
method void SetFriendOnline(string userId, table friend)
    self.userId = userId
    self.friend = friend
    
    self.rankImage.ImageRUID = self.resourceManager:GetResource("Rank")[friend.majorRank]
    self.nicknameText.Text = friend.nickname
    self.profileCodeText.Text = "#" .. friend.profileCode
    
    local location = friend.location
    local mode = location.mode
    if mode == "Lobby" then
        self.locationText.Text = string.format("%s %d", _LocalizationService:GetText("Channel"), location.channel.id) 
    elseif mode == "RankedMatch" then
        self.locationText.Text = _LocalizationService:GetText("RankedMatch")
    -- ... Other mode-specific location display
    end
end
```

## Server-side Friend Management (Character.mlua)

### Friend Relationship Verification

```lua
method boolean IsFriendWith(Character character)
    return self:IsUser() and self.friendTable[character.Entity.Name] ~= nil
end

method integer GetFriendCount()
    return _Table:GetSize(self.friendTable)
end
```

### Friend Request System

**Sending Friend Request:**
```lua
@ExecSpace("ServerOnly")
method void SendFriendRequest(Character other)
    if not self.isLoaded then return end
    
    local result
    if not isvalid(other) or not other.isLoaded then
        result = "UserNotFound"
    elseif _Table:Contains(other.friendRequestArray, self) then
        result = "Pending"
    elseif self:IsFriendWith(other) then
        result = "FriendAlready"
    else
        result = "Success"
    end
    
    if result == "Success" then
        table.insert(other.friendRequestArray, self)
        self:SendFriendRequestInOther(other.Entity.Name)
    end
    
    self:SendFriendRequestInOwner(result, self.Entity.Name)
end
```

**Accepting Friend Request:**
```lua
@ExecSpace("ServerOnly")
method void AcceptFriendRequest(Character sender)
    if result == "Success" then
        self.friendTable[sender.Entity.Name] = {
            profileCode = sender.profileCode, 
            nickname = sender.nickname
        }
        sender.friendTable[self.Entity.Name] = {
            profileCode = self.profileCode, 
            nickname = self.nickname
        }
        self:AcceptFriendRequestInSender(sender.Entity.Name)
    end
    self:AcceptFriendRequestInOwner(sender, result, self.Entity.Name)
end
```

**Removing Friend:**
```lua
@ExecSpace("ServerOnly")
method void Unfriend(string userId)
    if not self.isLoaded then return end
    
    if not self.friendTable[userId] then
        self:UnfriendInOwner(userId, self.Entity.Name)
        return
    end
    
    -- Bilateral removal if the other party is online
    local other = _UserService:GetUserEntityByUserId(userId)
    if isvalid(other) and isvalid(other.Character) then
        other.Character.friendTable[self.Entity.Name] = nil
        self:UnfriendInOther(userId)
    end
    
    self.friendTable[userId] = nil
    self:UnfriendInOwner(userId, self.Entity.Name)
end
```

## Server-side Friend Information Query (Map.mlua)

### Friend List Query

```lua
@ExecSpace("ServerOnly")
method void GetFriends(Character character, table userIdArray)
    if not isvalid(character) then return end
    
    local friendTable = {}
    for _, userId in ipairs(userIdArray) do
        local userEntity = _UserService:GetUserEntityByUserId(userId)
        if isvalid(userEntity) and isvalid(userEntity.Character) then
            local friend = userEntity.Character
            if friend.isLoaded then
                friendTable[userId] = {
                    nickname = friend.nickname,
                    profileCode = friend.profileCode,
                    majorRank = friend:GetMajorRank(),
                    location = friend:GetLocation()
                }
            end
        end
    end
    
    local friendArray = {}
    for i, userId in ipairs(userIdArray) do
        friendArray[i] = friendTable[userId]
    end
    
    self:GetFriendsInSender(userIdArray, friendArray, character.Entity.Name)
end
```

### Friend Follow System

```lua
@ExecSpace("ServerOnly")
method void Follow(Character character, string userId, table friend)
    if not isvalid(character) then return end
    if character.friendTable[userId] == nil then return end
    if character.isMatching then return end
    
    -- Logic to move to friend's location
    -- Handle movement based on channel, room, game mode
end
```

## Data Structures

### friendTable Structure
```lua
friendTable = {
    [userId] = {
        profileCode = "1234",
        nickname = "FriendNickname"
    }
}
```

### friendRequestArray Structure
```lua
friendRequestArray = {
    character1, -- Character object reference
    character2,
    -- ...
}
```

### friend Location Info Structure
```lua
location = {
    mode = "Lobby" | "RankedMatch" | "FriendlyMatch" | "Practice" | "Tutorial",
    channel = { id = 1 },
    room = { channel = { id = 1 }, id = 1 }
}
```

## Event System

### Client Events

**GetFriends Event:**
- Triggered when friend list information is received
- Used for updating friend slot UI

**Unfriend Event:**
- Triggered when friendship is removed
- Used for removing corresponding friend slot from UI

```lua
character.Entity:SendEvent(_Event:Unfriend(userId))
```

## Special Features

### Duel Spectating System Integration
When players become friends, the ability to spectate each other's duels is automatically activated.

```lua
-- Set spectating permission when accepting friend request
if isvalid(self.player) and not isvalid(sender.player) and self.player.duel.isDueling then
    self.player.commandManager:SetWatching(sender, self.player)
end
```

### Real-time Status Updates
- Friend list is automatically refreshed every 5 seconds
- Online status, location, and rank information are updated in real-time

### UI/UX Features

**Pagination:**
- Display 7 friends per page
- Navigate pages with left/right arrows

**Visual Feedback:**
- Online friends show rank icons
- Offline friends hide rank icons
- Location-specific status messages displayed

**Sound Feedback:**
- Appropriate sounds played on button clicks
- UI sounds provided for friend request/removal

This friend system is a core element that enriches the social experience of Maple Duel, facilitating ongoing relationship building and interaction between players.

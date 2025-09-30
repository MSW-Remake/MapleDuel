# Social Features UI

## 📋 Overview

MapleDuel's Social Features UI is a core system that supports player interaction and community engagement. Through friend management, real-time chat, ranking systems, and player interactions, it transforms a simple card game into a living social platform. It provides a healthy and enjoyable community environment through intuitive UI and safe interaction systems.

**Related Files**: 
- `RootDesk/MyDesk/Components/UIs/SocialModule.mlua` (Friend System)
- `RootDesk/MyDesk/Components/UIs/ChatModule.mlua` (Chat System)
- `RootDesk/MyDesk/Components/UIs/RankingModule.mlua` (Ranking System)
- `RootDesk/MyDesk/Components/UIs/FriendSlot.mlua` (Friend Slot)
- `RootDesk/MyDesk/Components/UIs/InteractionModule.mlua` (Player Interaction)

## 🏗️ Social UI System Architecture

### Integrated Social Feature Structure

```mermaid
graph TB
    A[Social Features UI System] --> B[Friend Management]
    A --> C[Real-time Chat]
    A --> D[Ranking System]
    A --> E[Player Interaction]
    
    B --> B1[SocialModule<br/>Friend System Hub]
    B1 --> B2[Friend List Management]
    B1 --> B3[Friend Request Processing]
    B1 --> B4[Online Status Check]
    B1 --> B5[Follow System]
    
    C --> C1[ChatModule<br/>Chat Control]
    C1 --> C2[Chat Enable/Disable]
    C1 --> C3[Chat Balloon Management]
    C1 --> C4[Developer Commands]
    
    D --> D1[RankingModule<br/>Ranking System]
    D1 --> D2[Overall Ranking Display]
    D1 --> D3[Page Navigation]
    D1 --> D4[Real-time Rank Updates]
    
    E --> E1[InteractionModule<br/>Player Interaction]
    E1 --> E2[Friend Request Button]
    E1 --> E3[Profile Check]
    E1 --> E4[Game Invitation]
```

## 👥 1. Friend System (SocialModule)

### Friend Management Hub

#### Friend List System
```mermaid
graph TB
    A[SocialModule] --> B[Friend List Display]
    A --> C[Friend Request Processing]
    A --> D[Profile Information]
    
    B --> B1[Pagination]
    B --> B2[FriendSlot Array]
    B --> B3[Real-time Refresh]
    B --> B4[Online Status Display]
    
    C --> C1[Accept/Decline Popup]
    C --> C2[Friend Request Notification]
    C --> C3[Automatic UI Update]
    
    D --> D1[Nickname Display]
    D --> D2[Rank Information]
    D --> D3[Profile Code]
    D --> D4[Current Location Info]
```

#### Friend Request Processing System
```mermaid
sequenceDiagram
    participant P1 as Player1
    participant SM as SocialModule
    participant S as Server
    participant P2 as Player2
    
    P2->>SM: Receive friend request
    SM->>SM: ShowFriendRequestPopup() display
    SM->>P1: Activate popup UI
    
    P1->>SM: Click Accept button
    SM->>S: AcceptFriendRequest request
    S->>S: Create friend relationship
    S-->>SM: Update friend list
    SM->>SM: Close popup & refresh list
    
    alt If declining
        P1->>SM: Click Refuse button
        SM->>S: RefuseFriendRequest request
        S->>S: Process request decline
        SM->>SM: Close popup
    end
```

#### Automatic Refresh System
```lua
-- Periodic friend list update
if self.refreshTimer then
    _TimerService:ClearTimer(self.refreshTimer)
end
self.refreshTimer = _TimerService:SetTimer(function()
    if self.isOpen then
        _Server:Request(character, "GetFriends", {})
    end
end, 10, true)  -- Refresh every 10 seconds
```

### Friend Slot Interaction (FriendSlot)

#### Individual Friend Management
```mermaid
graph LR
    A[FriendSlot] --> B[Friend Info Display]
    A --> C[Action Buttons]
    
    B --> B1[Rank Icon]
    B --> B2[Nickname]
    B --> B3[Profile Code]
    B --> B4[Current Location]
    
    C --> C1[Delete Button<br/>Unfriend]
    C --> C2[Follow Button<br/>Follow Friend]
```

#### Follow System
```lua
self.followButton.Entity:ConnectEvent(ButtonClickEvent, function()
    -- State verification
    if character.isMatching then
        self.uiManager.PopupModule:Open("NotPossibleWhileMatching", true, nil, nil)
        return
    end
    
    -- Check same location
    if isvalid(_UserService:GetUserEntityByUserId(self.userId)) then
        self.uiManager.PopupModule:Open("SameLocation", true, nil, nil)
        return
    end
    
    -- Confirmation popup when in game
    if isvalid(character.player) and character.player.duel.isDueling then
        self.uiManager.PopupModule:Open("DoubleCheckFollow", false, function()
            _Server:Request(map, "Follow", {character, self.userId, self.friend})
        end, nil)
    else
        _Server:Request(map, "Follow", {character, self.userId, self.friend})
    end
end)
```

**Follow Feature Characteristics**:
- **Location Movement**: Instantly move to the room where friend is located
- **Status Check**: Restricted during matching or in-game
- **Confirmation System**: Confirmation popup when interrupting game
- **Same Location**: Notification when already in same place

## 💬 2. Chat System (ChatModule)

### Chat Control System

#### Integrated Chat Management
```mermaid
graph TB
    A[ChatModule] --> B[Chat Toggle Button]
    B --> C[Chat Enable]
    B --> D[Chat Disable]
    
    C --> C1[Enable all player chat balloons]
    C --> C2[Display chat messages]
    C --> C3[Allow chat input]
    
    D --> D1[Disable all player chat balloons]
    D --> D2[Clear existing chat messages]
    D --> D3[Block chat input]
    D --> D4[Show disabled icon]
```

#### Global Chat State Management
```lua
method void OnBeginPlay()
    self.chatButton.Entity:ConnectEvent(ButtonClickEvent, function()
        -- Toggle chat state
        self.isChatEnable = not self.isChatEnable
        self.disableIcon.Entity.Enable = not self.isChatEnable
        self.uiManager:UpdateChat()
        
        -- Apply to all users in current map
        local currentMap = _UserService.LocalPlayer.CurrentMap
        for _, userEntity in ipairs(_UserService:GetUsersByMapComponent(currentMap.MapComponent)) do
            local character = userEntity.Character
            if isvalid(character.player) then
                -- Player in game
                character.player.chatBalloon.Enable = self.isChatEnable
                if not self.isChatEnable then
                    character.player:ClearChat()
                end
            else
                -- Player in lobby
                userEntity.ChatBalloonComponent.Enable = self.isChatEnable
            end
        end
    end)
end
```

### Chat Balloon System

#### Situation-specific Chat Display
- **Lobby Chat**: Use general ChatBalloonComponent
- **In-Game Chat**: Use Player's dedicated chat balloon
- **Developer Commands**: Support `/` prefix commands
- **Automatic Cleanup**: Remove existing messages when chat disabled

## 🏆 3. Ranking System (RankingModule)

### Hierarchical Ranking Display

#### Paginated Ranking System
```mermaid
graph TB
    A[RankingModule] --> B[Ranking Data Request]
    A --> C[Page Navigation]
    A --> D[Ranking Slot Display]
    
    B --> B1[RankManager.GetRankingInfos]
    B1 --> B2[Receive ranking info from server]
    B2 --> B3[Update rankingInfoArray]
    
    C --> C1[Left Arrow - Previous Page]
    C --> C2[Right Arrow - Next Page]
    C --> C3[Page Range Validation]
    
    D --> D1[Display 10 RankingSlots]
    D1 --> D2[Rank, Nickname, Rank Score]
    D1 --> D3[Rank Icon Display]
```

#### Dynamic Page Calculation
```lua
-- Calculate number of pages
local totalPages = math.ceil(#self.rankingInfoArray / #self.rankingSlotArray)

-- Page navigation control
self.leftArrowButton.Entity:ConnectEvent(ButtonClickEvent, function()
    if self.pageIndex > 1 then
        self:ShowRanking(self.pageIndex - 1)
    end
end)

self.rightArrowButton.Entity:ConnectEvent(ButtonClickEvent, function()
    if self.pageIndex < totalPages then
        self:ShowRanking(self.pageIndex + 1)
    end
end)
```

### Ranking Slot System

#### Hierarchical Information Display
- **RankingSlot_1~10**: 10 players' ranking info per page
- **Ranking Info**: Overall rank and rank within page
- **Player Info**: Nickname, rank icon, score
- **Real-time Updates**: Request latest info every time module opens

## 🤝 4. Player Interaction (InteractionModule)

### Social Interaction During Game

#### Friend Request System
Provides instant friend request feature with opponent during game.

```mermaid
sequenceDiagram
    participant P1 as Player1
    participant IM as InteractionModule
    participant SM as SocialModule
    participant P2 as Player2
    
    P1->>IM: Click friend request button
    IM->>P2: Send friend request
    P2->>SM: Receive friend request notification
    SM->>P2: Show accept/decline popup
    
    alt Accept
        P2->>SM: Click Accept
        SM->>IM: Friend relationship established
        IM->>P1: Friend addition complete notification
    else Decline
        P2->>SM: Click Refuse
        SM->>IM: Request declined notification
    end
```

### Profile Information Display

#### Real-time Player Information
- **Rank Information**: Current tier and rank points
- **Game Statistics**: Win rate, number of games, etc.
- **Online Status**: Current activity status
- **Friend Relationship**: Whether already friends

## 🛡️ 5. Safety & Security System

### State-based Restrictions

#### Smart Interaction Restrictions
```lua
-- Common safety verification pattern
if not character.isLoaded or _Server:IsRequesting() then
    return  -- Character not loaded or server processing
end

if character.isMatching then
    self.uiManager.PopupModule:Open("NotPossibleWhileMatching", true, nil, nil)
    return  -- Restricted during matching
end

if isvalid(character.player) and character.player.duel.isDueling then
    -- Special handling during game (confirmation popup, etc.)
end
```

### Anti-abuse System

#### Spam Prevention and Restrictions
- **Request Limiting**: Prevent duplicate requests during server processing
- **Time Restrictions**: Limit intervals between friend requests
- **Status Check**: Restrict features based on game situation
- **Automatic Cleanup**: Automatic recovery from abnormal states

## 🎨 6. UI/UX Optimization

### Responsiveness Enhancement

#### Immediate Feedback System
```mermaid
graph LR
    A[User Action] --> B[Immediate UI Response]
    B --> C[Server Request]
    C --> D[Receive Result]
    D --> E[Final UI Update]
    
    B --> F[Show Loading State]
    F --> G[Improve User Waiting Experience]
```

#### Smart Refresh
- **Conditional Updates**: Server requests only when necessary
- **Caching**: Local storage of recent data
- **Incremental Updates**: Update only changed parts

### Visual Consistency

#### Unified Design Patterns
- **Common Button Styles**: Accept/Refuse, Delete/Follow, etc.
- **Consistent Animation**: Scale, fade, slide effects
- **Standard Colors**: Unified color codes by state
- **Responsive Layout**: Support for various screen sizes

## 🔄 7. Real-time Update System

### Event-based Synchronization

#### Character Event Integration
```lua
-- Automatic processing of friend-related events
character.Entity:ConnectEvent(Unfriend, function(event)
    local userId = event.userId
    -- Automatic cleanup of corresponding friend slot
    for _, slot in ipairs(self.friendSlotArray) do
        if slot.userId == userId then
            slot:Clear()
            break
        end
    end
end)

character.Entity:ConnectEvent(FriendStatusChanged, function(event)
    -- Immediate UI update when friend status changes
    self:RefreshFriendList()
end)
```

### Network Optimization

#### Efficient Data Transfer
- **Change Detection**: Transfer only when actual changes occur
- **Batch Requests**: Combine multiple operations into single request
- **Compressed Responses**: Transfer only selected necessary information

## 💡 Code Reference

Core social UI logic:
- `SocialModule.mlua :: ShowFriendRequestPopup()` — Friend request popup
- `SocialModule.mlua :: RefreshFriendList()` — Friend list refresh
- `FriendSlot.mlua :: Follow()` — Follow friend feature
- `ChatModule.mlua :: UpdateChat()` — Chat state switching
- `RankingModule.mlua :: ShowRanking()` — Ranking page display

The Social Features UI system is a core system that makes MapleDuel more than just a simple card game into a living community, supporting safe and enjoyable interactions between players.

UIMyInfo:OnBeginPlay -- Initialize UI and set player information
UIMyInfo:OnUpdate -- Update player HP bar and text in real-time
UIPopup:Open -- Open popup window and set message and callback functions
UIPopup:OnClickOk -- Execute callback and close popup when OK button is clicked
UIPopup:OnClickCancel -- Execute callback and close popup when Cancel button is clicked
UIPopup:Close -- Disconnect events and start popup closing animation
UIPopup:StartTween -- Execute popup open/close animation
UIToast:ShowMessage -- Display toast message on screen
UIToast:HideMessage -- Immediately hide toast message
UIToast:StartTween -- Execute toast message show/hide animation
AvatarRenderer:OnBeginPlay -- Initialize avatar renderer and set emotions/actions
AvatarRenderer:HandleScreenTouchEditorEvent -- Reset avatar state when handling editor screen touch events
Bot:OnBeginPlay -- Initialize bot AI at game start and set up connections to various managers in the duel system
Bot:SelectBehavior -- Bot AI analyzes all possible actions in the current situation, scores them, and selects the optimal action
Bot:SetDifficulty -- Set bot game difficulty to adjust AI behavior patterns and rank points
Bot:Play -- Execute the actual playing of the card selected by the bot to the appropriate target or location
Bot:DeclareEndRound -- Declare round end when the bot has no more cards to play
Bot:ChatOnce -- Display message in bot's chat bubble for a specified duration only once
Bot:ChatRepeat -- Repeatedly display and hide messages in bot's chat bubble at specified intervals
Bot:StopChat -- Completely stop bot's chat bubble display and clear messages
Bot:Run -- Execute bot AI main loop - analyze current situation every 3 seconds to select and execute optimal actions
Character:OnMapEnter -- Initialize matching system and set user state when character enters map
Character:OnBeginPlay -- Initialize character components at game start and handle data loading for server/client
Character:GetProperties -- Return character core properties as table for network synchronization
Character:SetProperties -- Batch set character property values using property table received from network
Character:SetPropertiesInClient -- Character property setting method executed only on client side
Character:SyncProperties -- Send character property information synchronization to specified user on server
Character:OnSyncProperties -- Update UI elements like nametag on client after property synchronization completion
Character:Sync -- Complete synchronization of all character properties and states from server to client
Character:Clear -- Completely reset all character game data to initial state
Character:LoadServerAttribute -- Attribute method to check if server has permission to perform data loading operations
Character:Load -- Load all character game information from database and initialize game state
Character:SetLoadedInOwner -- Set character data loading completion state on client to allow UI updates
Character:RankedMatchReady -- Handle duel start processing when user is ready in ranked match
Character:SpawnClassTag -- Create class tag entity to be displayed above character on client
Character:SetTemp -- Set temporary data and handle limited-time event card pack count and attendance
Character:SetTempInOwner -- Set temporary data on client and update event UI
Character:GetOpenEventCardPackCount -- Return number of times event card packs can be opened for free based on current date
Character:DecreaseOpenEventCardPackCount -- Deduct 1 from remaining free opens when opening event card pack
Character:DecreaseOpenEventCardPackCountInOwner -- Update event card pack open count on client and reflect in UI
Character:SetMeso -- Set character's meso amount to specified value on server
Character:SetMesoInOwner -- Set meso amount on client and reflect in UI
Character:AddMeso -- Process meso amount increase/decrease on server and synchronize to client
Character:AddMesoInServer -- Perform meso amount increase/decrease calculation only on server and update value
Character:AddMesoInOwner -- Immediately reflect meso amount increase/decrease in UI on client
Character:GetDailyRankedWinMeso -- Query meso reward that can be received for ranked match wins based on today's date
Character:SetDailyRankedWinMeso -- Set ranked match win meso reward amount based on today's date
Character:AddDailyRankedWinMeso -- Increase meso reward amount received for ranked match wins based on today's date
Character:GetDailyPlayMeso -- Query meso reward that can be received for gameplay based on today's date
Character:SetDailyPlayMeso -- Set gameplay meso reward amount based on today's date
Character:AddDailyPlayMeso -- Increase gameplay meso reward amount based on today's date
Character:GetDailyRankedPlayCount -- Query daily ranked play count
Character:SetDailyRankedPlayCount -- Set daily ranked play count
Character:IncreaseDailyRankedPlayCount -- Increase daily ranked play count
Character:GetCardCount -- Query owned quantity of specific card
Character:SetCards -- Set card collection data
Character:SetCardsInOwner -- Set card collection data on client
Character:GainCards -- Acquire cards and add to collection
Character:LoseCards -- Lose cards and remove from collection
Character:BuySingleCardPackServerAttribute -- Server attribute method - check permission to purchase card pack
Character:BuySingleCardPack -- Process single card pack purchase
Character:BuySingleCardPackInOwner -- Process single card pack purchase result on client
Character:BuySingleCardPackByOpenEventServerAttribute -- Server attribute method - check permission to purchase event card pack
Character:BuySingleCardPackByOpenEvent -- Process free card pack purchase during event period
Character:BuySingleCardPackByOpenEventInOwner -- Process event card pack purchase result on client
Character:BuyMultipleCardPacksServerAttribute -- Server attribute method - check permission to purchase multiple card packs
Character:BuyMultipleCardPacks -- Process multiple card pack purchase (5-pack set)
Character:HasCardBack -- Check if specific card back is owned
Character:SetCardBack -- Set card back to use
Character:SetDecks -- Set deck array and validate owned card quantities
Character:CreateDeck -- Create new deck
Character:FinishDeck -- Complete deck editing and save
Character:SaveDeck -- Temporarily save deck
Character:DeleteDeck -- Delete currently selected deck
Character:SetDeckIndex -- Set deck index to use
Character:SetRank -- Set rank points and ranking
Character:BuyCard -- Process individual card purchase
Character:SellCard -- Process card selling
Character:IsUser -- Check if actual user or bot
Character:IsOwner -- Check if local player themselves
Character:IsAlly -- Check if ally (including friend relationship)
Character:IsAbleToMatch -- Check if in matchable state
Character:GetDeck -- Return currently used deck information (considering tutorial mode)
Character:SetNameTag -- Set nametag according to rank
Character:OpenCardPack -- Process card pack opening
Character:SendFriendRequest -- Send friend request
Character:PlayEmote -- Play emotion expression
Character:PlayEmoteInClient -- Play emotion expression animation on client
Character:SpawnEmoteEffect -- Create emotion expression effect entity
Character:IncreaseSpecialEventAttendanceCount -- Process increasing special event attendance count once per day on server
Character:IncreaseSpecialEventAttendanceCountInOwner -- Update special event attendance count information on client
Character:OnUpdate -- Every frame update - daily attendance check
Character:ReceiveCardPacksBySpecialEventServerAttribute -- Server attribute method to check permission to receive special event card pack rewards
Character:ReceiveCardPacksBySpecialEvent -- Process distributing daily card pack rewards for special events on server
Character:ReceiveCardPacksBySpecialEventInOwner -- Process special event card pack reward receipt results and UI display on client
Character:ShowEvent -- Open special event UI window on client to display reward information
Character:HandleTouchEvent -- Event handling to open emotion expression UI if touching self, or interaction UI if touching others when character is touched
Character:HandleUserLeaveEvent -- Event handling to save all game data to database and clean up game state when user leaves game
Home:OnBeginPlay -- Initialize home map and set camera
Home:GetProperties -- Return home map's properties to synchronize as table
Home:OnSyncProperties -- Create UI modules when synchronizing properties on client
Home:UpdateChannels -- Update and manage server channel information
Home:EnterChannelServerAttribute -- Server attribute method - check channel entry permission
Home:EnterChannel -- Move player to specific channel
Home:GetChannelsServerAttribute -- Server attribute method - check channel list query permission
Home:GetChannels -- Query current active channel list and send to client
Home:GetChannelsInOwner -- Send channel list event on client
Home:GetRooms -- Query and return room list for specified mode
Home:GetNewRoomId -- Generate new available room ID for specified mode
Home:CreateFriendlyMatchRoomServerAttribute -- Server attribute method - check friendly match room creation permission
Home:CreateFriendlyMatchRoom -- Create friendly match room and move player
Home:EnterFriendlyMatchRoomServerAttribute -- Server attribute method - check friendly match room entry permission
Home:EnterFriendlyMatchRoom -- Make player enter existing friendly match room
Home:BeginPracticeServerAttribute -- Server attribute method - check practice mode start permission
Home:BeginPractice -- Start practice mode with difficulty based on player's rank
Home:BeginTutorialServerAttribute -- Server attribute method - check tutorial start permission
Home:BeginTutorial -- Create and move to tutorial room for player
Home:GetFriendlyMatchRoomsServerAttribute -- Server attribute method - check friendly match room list query permission
Home:GetFriendlyMatchRooms -- Query current active friendly match room list and send to client
Home:GetFriendlyMatchRoomsInSender -- Send friendly match room list event on client
Home:BeginMatchingServerAttribute -- Server attribute method - check ranked matching start permission
Home:BeginMatching -- Start ranked matching
Home:BeginMatchingInSender -- Change matching start UI state on client
Home:CancelMatchingServerAttribute -- Server attribute method - check matching cancel permission
Home:CancelMatching -- Cancel ongoing ranked matching
Home:CancelMatchingInSender -- Change matching cancel UI state on client
Home:Initialize -- Initialize home map by mode (lobby or ranked match)
Home:UpdateMatchResult -- Update match result and calculate rank points
Home:ReturnToLobbyServerAttribute -- Server attribute method - check lobby return permission
Home:ReturnToLobby -- Return player to lobby
Input:OnBeginPlay -- Initialize input system and connect trigger events
Input:SetState -- Switch input state and handle UI/game logic
Input:HideScope -- Hide targeting scope
Input:PlaceScope -- Set targeting scope and line position
Input:SetTarget -- Set targeting target and update scope visual
Input:HandleScreenTouchHoldEvent -- Handle screen touch hold events - card dragging etc.
Input:HandleScreenTouchReleaseEvent -- Handle screen touch release events - card playing etc.
Integer:SetInteger -- Set integer value and display as number sprites
Integer:SetPositiveInteger -- Set positive value and display with + sign
Integer:Clear -- Remove all number sprites and initialize
Integer:SetColor -- Change color of all number sprites
Integer:SetAlpha -- Change transparency of all number sprites
Integer:GetDigits -- Separate integer into individual digits and return as array
Integer:PlaceDigits -- Place and display number sprites on screen
Layout:OnBeginPlay -- Store Transform components of child entities in table
Layout:GetTransform -- Search and return Transform component by name
MainCamera:OnBeginPlay -- Set main camera and apply zoom appropriate for screen ratio
Map:GetProperties -- Return map properties as table
Map:SetProperties -- Set map properties using received property table
Map:SetPropertiesInClient -- Set properties on client
Map:SyncProperties -- Synchronize properties to specific user on server
Map:OnSyncProperties -- Apply map decoration after property synchronization completion
Map:Sync -- Synchronize map information from server to client
Map:Decorate -- Set map decoration and background music according to theme
Map:GetFriendsServerAttribute -- Server attribute method for friend list query
Map:GetFriends -- Query and return friend list information
Map:GetFriendsInSender -- Update friend information and send event on client
Map:FollowServerAttribute -- Server attribute method for friend follow functionality
Map:Follow -- Process friend follow functionality
Notice:ShowText -- Display announcement text on screen and play sound effect
Npc:OnBeginPlay -- Initialize NPC and repeatedly display random conversation messages
Room:GetProperties -- Return room properties as table
Room:OnSyncProperties -- Create UI modules when synchronizing properties on client
Room:ReturnToLobbyServerAttribute -- Server attribute method - check lobby return permission
Room:ReturnToLobby -- Move player to lobby or move to static room
Room:Initialize -- Initialize room - create and set bots according to mode
Room:HandleSetRoom -- Handle room setting event
SpriteRenderer:HandleAnimationClipEvent -- Update sprite when animation clip changes
TurnSign:OnBeginPlay -- Initialize turn sign and connect touch events
TurnSign:SetState -- Change turn sign state and visual update
TurnSign:SetStateByTurnPlayer -- Automatically set turn sign state according to turn player
TurnSign:RotateSign -- Animate turn sign rotation to specified angle
TurnSign:SetText -- Set turn sign text and apply animation effects
TurnSign:SetColor -- Change turn sign color
TurnSign:BeginCountdown -- Start turn time limit countdown
TurnSign:EndCountdown -- End countdown and handle timeout
TurnSign:PlaceRope -- Update countdown rope position and size
Tutorial:GetProperties -- Return tutorial core properties as table for network synchronization
Tutorial:SetProperties -- Batch set tutorial state using property table received from network
Tutorial:SetPropertiesInClient -- Tutorial property setting method executed only on client side
Tutorial:SyncProperties -- Synchronize properties to specific user on server
Tutorial:OnSyncProperties -- Request tutorial progress after property synchronization completion
Tutorial:Sync -- Synchronize tutorial information from server to client
Tutorial:SetArrow -- Set tutorial arrow position
Tutorial:ClearArrow -- Hide tutorial arrow
Tutorial:SetClick -- Set tutorial click indicator position
Tutorial:ClearClick -- Hide tutorial click indicator
Tutorial:SetDrag -- Set tutorial drag animation
Tutorial:ClearDrag -- Clean up and hide tutorial drag animation
Tutorial:ProgressServerAttribute -- Server attribute method for tutorial progress
Tutorial:Progress -- Update tutorial progress state
Tutorial:ProgressInClient -- Handle tutorial step-by-step UI processing on client
CardFront:OnBeginPlay -- Hide display symbol when initializing card front
MinionBody:OnBeginPlay -- Initialize minion body and create status effect entities
Thumbnail:OnBeginPlay -- Initialize thumbnail and connect touch events
Thumbnail:SetInfo -- Set card information on thumbnail and update visual
Thumbnail:ClearInfo -- Initialize all thumbnail information
Thumbnail:DestroyTweener -- Destroy tweener animation object
Thumbnail:DestroyAnchorTweener -- Destroy anchor tweener animation object
Thumbnail:SetAnchorTransform -- Immediately set anchor position
Thumbnail:TransformAnchorTo -- Animate anchor movement to specified position
Thumbnail:TransformToAnchor -- Animate thumbnail movement to anchor position
Thumbnail:AttachToAnchor -- Attach thumbnail to anchor entity
Thumbnail:IsInTouchArea -- Check if specified point is within touch area
Thumbnail:GetBlueprint -- Return current thumbnail's blueprint information
Thumbnail:GetBlueprintByName -- Create blueprint with specified name
Thumbnail:SetDisplayTimer -- Timer to set undisplayable state after specified time
Thumbnail:ClearDisplayTimer -- Release display timer
Thumbnail:PlaceFront -- Place thumbnail in front layer
Thumbnail:PlaceBack -- Place thumbnail in back layer
UnitBody:OnBeginPlay -- Hide display symbol when initializing unit body
ActionManager:OnBeginPlay -- Set processing delay time and core delay time tables for each action when initializing action manager
ActionManager:GetProcessDelay -- Return processing delay time according to action name
ActionManager:GetCoreDelay -- Return core delay time according to action name
ActionManager:PlayPreProcessAction -- Execute action pre-processing stage
ActionManager:PlayPostProcessAction -- Execute action post-processing stage
ActionManager:PlayPreCoreAction -- Execute action core pre-processing stage
ActionManager:PlayPostCoreAction -- Execute action core post-processing stage
ActionManager:GetSummonActionName -- Generate summon action name and return default value based on method existence
ActionManager:PlaySummonAction -- Execute minion summon action
ActionManager:SummonCoroutine -- Execute minion summon action as coroutine and return controllable task
ActionManager:Summon -- Play basic summon animation and sound effects
ActionManager:PreProcessAirStrike -- Air Strike skill pre-processing (player animation and effects)
ActionManager:PostProcessAirStrike -- Air Strike skill post-processing wait
ActionManager:PreCoreAirStrike -- Play hit effect before applying Air Strike damage
ActionManager:PostProcessArmorCrash -- Armor Crash skill post-processing wait
ActionManager:PreCoreArmorCrash -- Play hit effect before applying Armor Crash damage
ActionManager:PreCoreArrowBlow -- Execute Arrow Blow skill (player animation and projectile launch)
ActionManager:PreProcessArrowBomb -- Arrow Bomb skill pre-processing (player animation and projectile launch)
ActionManager:PostProcessBlackbull -- Blackbull skill post-processing wait
ActionManager:PreProcessBlackKitty -- Black Kitty skill pre-processing (animation and sound)
BotManager:GetData -- Return bot data corresponding to bot name
BotManager:PracticeWarriorBot -- Return practice warrior bot data
BotManager:PracticeMagicianBot -- Return practice magician bot data
BotManager:PracticeBowmanBot -- Return practice bowman bot data
BotManager:PracticeThiefBot -- Return practice thief bot data
BotManager:PracticePirateBot -- Return practice pirate bot data
BotManager:TutorialBot -- Return tutorial bot data
CardBackManager:OnBeginPlay -- Initialize card back manager and load data
CardBackManager:GetStarterCardBacks -- Return list of default provided card backs
CardBackManager:GetCardBacks -- Return array of all available card backs
CardPackManager:OnBeginPlay -- Load dataset and categorize card packs by theme when initializing card pack manager
CardPackManager:GetTheme -- Return card pack theme
CardPackManager:GetQuality -- Return card pack quality
CardPackManager:GetRarity -- Return card pack rarity
CardPackManager:GetCurrency -- Return card pack purchase currency type
CardPackManager:GetSingleMesoPrice -- Return card pack single meso price
CardPackManager:GetMultipleMesoPrice -- Return card pack multiple meso price
CardPackManager:GetSingleWorldCoinPrice -- Return card pack single world coin price
CardPackManager:GetMultipleWorldCoinPrice -- Return card pack multiple world coin price
CardPackManager:GetCardPackNames -- Return card pack name list for specific theme
CardPackManager:GetSinglePrice -- Return card pack single purchase price according to currency type
CardPackManager:GetMultiplePrice -- Return card pack multiple purchase price according to currency type
CardPackManager:GetInfos -- Randomly generate information for 5 cards that will come out when opening card pack according to rarity
CardPackManager:OpenCardPack -- Handle card pack opening animation and card thumbnail display on client
CardPackManager:AcquireThumbnail -- Get thumbnail object from pool or create new and return
CardPackManager:ReleaseThumbnail -- Return used thumbnail object to pool for reuse
CardPackManager:AcquireCardPack -- Get card pack entity from pool or create new and return
CardPackManager:ReleaseCardPack -- Return used card pack entity to pool for reuse
CommandManager:OnBeginPlay -- Initialize command queue on client and start loop to continuously process commands
CommandManager:IsCommander -- Check if current player is the commander who issued the command
CommandManager:RunCommand -- Entry point to execute command on client/server
CommandManager:VerifyCommand -- Verify command validity on server (ID matching and individual verification function call)
CommandManager:OnVerifyCommandFailed -- Initialize input state on client and display error message when command verification fails
CommandManager:RunCommandInServerServerAttribute -- Server attribute method (empty implementation)
CommandManager:RunCommandInServer -- Verify and execute command on server, then send results to all clients
CommandManager:PreRunCommand -- Pre-processing before command execution on client (set input state and call pre-processing function)
CommandManager:PostRunCommand -- Call post-processing function after command execution on client
CommandManager:PushCommandInClient -- Add new command to client command queue
CommandManager:RunCommandInClient -- Actually execute command retrieved from queue on client
CommandManager:RunCommandLogic -- Execute actual command logic and check game end conditions
CommandManager:PushPackage -- Add package to be shared with all clients on server
CommandManager:PushPrivatePackage -- Add private package visible only to specific player and allies and public package visible to other players
CommandManager:PopPackage -- Get next package from package array on client
CommandManager:ShareSpawnedEntity -- Create entity on server and synchronize with client
CommandManager:Destroy -- Add entity to destruction wait list (batch destroy after command processing completion)
CommandManager:IsAllyWith -- Check if in alliance with specific player on client
CommandManager:ShareRandomBoolean -- Generate random boolean value on server and synchronize with all clients
CommandManager:ShareRandomNumber -- Generate random number on server and synchronize with all clients
CommandManager:SharePrivateRandomNumber -- Provide actual random value to specific player and allies, default value to other players
CommandManager:ShareRandomIntegerRange -- Generate random integer within range on server and synchronize with all clients
CommandManager:SharePrivateRandomIntegerRange -- Provide actual random integer to specific player and allies, default value to other players
CommandManager:ShareRandomIntegersRange -- Generate random integer array within range on server and synchronize with all clients
CommandManager:SharePrivateRandomIntegersRange -- Provide actual random integer array to specific player and allies, default value array to other players
CommandManager:ShareRandomPermutationRange -- Generate random permutation array within range on server and synchronize with all clients
CommandManager:SharePrivateRandomPermutationRange -- Provide actual random permutation array to specific player and allies, default value array to other players
CommandManager:ShareRandomElementInArray -- Select random element from array on server and synchronize with all clients
CommandManager:SharePrivateRandomElementInArray -- Provide actual random element to specific player and allies, default value to other players
CommandManager:ShareRandomElementsInArray -- Select multiple random elements from array on server and synchronize with all clients
CommandManager:SharePrivateRandomElementsInArray -- Provide actual random element array to specific player and allies, default value array to other players
CommandManager:ShareRandomElementInArrays -- Select random element from multiple arrays considering weights on server and synchronize with all clients
CommandManager:SharePrivateRandomElementInArrays -- Provide actual random element to specific player and allies, default value to other players (considering multiple array weights)
CommandManager:ShareRandomElementsInArrays -- Select multiple random elements from multiple arrays considering weights on server and synchronize with all clients
CommandManager:SharePrivateRandomElementsInArrays -- Provide actual random element array to specific player and allies, default value array to other players (considering multiple array weights)
CommandManager:ShareRandomPermutationInArray -- Generate random permutation array from array on server and synchronize with all clients
CommandManager:SharePrivateRandomPermutationInArray -- Provide actual random permutation array to specific player and allies, default value array to other players
CommandManager:ShareCardBack -- Get character's card back information on server and synchronize with all clients
CommandManager:ShareClass -- Get character's class information on server and synchronize with all clients
CommandManager:SharePrivateBlueprints -- Share specific player's deck card blueprints only to allies and provide empty array to other players
CommandManager:SetInputStates -- Update all players' input states on server and send to clients
CommandManager:InputGate -- Increase gate count on server, decrease on client to control input state synchronization
CommandManager:SetInputStatesInClient -- Store input state information received from server on client and prepare for application
CommandManager:ApplyInputStates -- Actually apply stored input states to all objects and display playable signs
CommandManager:ClearInputStates -- Initialize all objects' input states and reset sign states
CommandManager:SetPlayableSigns -- Clear all signs and display playable signs only on playable objects
CommandManager:SetTargetableSigns -- Clear all signs, set card as in-use, and display targetable signs on targetable objects
CommandManager:SetCastingSigns -- Clear all signs and display casting signs only on cards
CommandManager:SetPlacingSigns -- Clear all signs and display placing signs only on placing minions
CommandManager:ClearSigns -- Clear sign states of all signable objects
CommandManager:VerifyBeginDuel -- Verify duel start command validity (check if not already in duel)
CommandManager:BeginDuel -- Start duel and update tutorial progress state
CommandManager:VerifyEndDuel -- Verify duel end command validity (check if in duel and winner is correct)
CommandManager:EndDuel -- End duel and handle winner
CommandManager:PreEndDuel -- Clean up client UI before ending duel
CommandManager:VerifyDeclareEndRound -- Verify round end declaration command validity (check if player's turn, tutorial state, etc.)
CommandManager:PreDeclareEndRound -- Update client UI before declaring round end (display end sign, convert hand cards, update turn sign)
CommandManager:DeclareEndRound -- Declare round end and update tutorial progress state
CommandManager:VerifyPlay -- Verify card play command validity (card validity, cost, target, field space, player turn, etc.)
CommandManager:OnVerifyPlayFailed -- Clean up client when card play verification fails (cancel minion placement)
CommandManager:PrePlay -- Client preparation before card play (remove from hand, prepare minion placement, etc.)
CommandManager:PostPlay -- Update client UI after card play (update turn sign)
CommandManager:Play -- Play card and update tutorial progress state
CommandManager:SetWatching -- Prepare data for spectator to view specific player's hand on server
CommandManager:SetWatchingInClient -- Store spectating data on client and wait for application after command execution completion
CommandManager:SetWatchingCards -- Set hand card information based on spectating data and display message
DeckManager:OnBeginPlay -- Set dataset and adjective arrays when initializing deck manager
DeckManager:IsDeckValid -- Check if deck is valid (class, name, card count, card restrictions, etc.)
DeckManager:IsDeckComplete -- Check if deck is complete (valid and 20 cards)
DeckManager:GetDeckSize -- Calculate and return total number of cards in deck
DeckManager:GetCardCountByName -- Calculate and return total number of specific named cards in deck
DeckManager:GetCardCountByInfo -- Return number of specific card info (name, variant, quality) in deck
DeckManager:GetText -- Get localized text from dataset (Korean/English support)
DeckManager:GetNewDeck -- Create empty deck for specified class and language (generate name with random adjective)
DeckManager:GetWarriorStarterDeck -- Return warrior class default starter deck
DeckManager:GetMagicianStarterDeck -- Return magician class default starter deck
DeckManager:GetBowmanStarterDeck -- Return bowman class default starter deck
DeckManager:GetThiefStarterDeck -- Return thief class default starter deck
DeckManager:GetPirateStarterDeck -- Return pirate class default starter deck
DeckManager:GetTutorialBotDeck_1 -- Return bot deck to use in tutorial stage 1 (including predefined card order)
DeckManager:GetTutorialPlayerDeck_1 -- Return player deck to use in tutorial stage 1 (including predefined card order)
DeckManager:GetTutorialBotDeck_2 -- Return bot deck to use in tutorial stage 2 (including predefined card order)
DeckManager:GetTutorialPlayerDeck_2 -- Return player deck to use in tutorial stage 2 (including predefined card order)
EmoteManager:OnBeginPlay -- Initialize emote manager and set emote type table
EmoteManager:GetEmotionalType -- Return emotion type corresponding to emote name
EnchantmentManager:ChunJi -- Check ChunJi enchantment removal condition (at round end)
EnchantmentManager:Focus -- Check Focus enchantment removal condition (at round end)
EnchantmentManager:Harp -- Check Harp enchantment removal condition (at round end)
EnchantmentManager:Haste -- Check Haste enchantment removal condition (at round end)
EnchantmentManager:PowerStance -- Check Power Stance enchantment removal condition (at round end)
EnchantmentManager:Reindeer -- Check Reindeer enchantment removal condition (when minion is played)
EnchantmentManager:ShadowPartner -- Check Shadow Partner enchantment removal condition (at round end)
EntryManager:OnBeginPlay -- Set basic information for game objects and cards when initializing entry manager
EntryManager:GetEntry -- Return entry information for specified name
EntryManager:Duel -- Return basic information for duel object
EntryManager:Player -- Return basic information for player object
EntryManager:Deck -- Return basic information for deck object
EntryManager:Hand -- Return basic information for hand object
EntryManager:Field -- Return basic information for field object
GalleryModule:OnBeginPlay -- Set keyword arrays and connect events when initializing gallery module
GalleryModule:AcquireCard -- Acquire card from card pool or create new
GalleryModule:ReleaseCard -- Return card to pool
GalleryModule:Open -- Open gallery module and display card or card back information
GalleryModule:Close -- Close gallery module and initialize all UI elements
RankManager:GetMajorRank -- Return major rank based on rank score and ranking (Legend, Master, Platinum, etc.)
RankManager:GetMinorRank -- Return detailed rank number based on rank score (1-4)
RankManager:GetRankName -- Return complete rank name as localized text
RankManager:GetRankPoint -- Return points within current rank as string
RankManager:GetRankingInfosServerAttribute -- Define ranking information query server attribute
RankManager:GetRankingInfos -- Query ranking data on server and return top 100 information
RankManager:GetRankingInfosInSender -- Set received ranking information in UI and display on client
TargetManager:GetCardRequiresTarget -- Check if targeting method exists for card name
TargetManager:GetCardTargetables -- Calculate and return list of targets that card can target on server
TargetManager:ArrowBlow -- Arrow Blow skill targets: all minions on field
TargetManager:ArrowBomb -- Arrow Bomb skill targets: all minions on field
TargetManager:Assaulter -- Assaulter skill targets: all minions on field
TargetManager:Brandish -- Brandish skill targets: all units (including players)
TargetManager:CorkscrewBlow -- Corkscrew Blow skill targets: all minions on field
TargetManager:Disorder -- Disorder skill targets: minions on own field
TargetManager:Doom -- Doom skill targets: all minions on field
TargetManager:DoubleShot -- Double Shot skill targets: all units (including players)
TargetManager:DragonBlood -- Dragon Blood skill targets: all units (including players)
TargetManager:Drain -- Drain skill targets: all units (including players)
TargetManager:EnergyOrb -- Energy Orb skill targets: all units (including players)
TaskManager:OnBeginPlay -- Initialize various selectors and comparison functions at game start
TaskManager:OnUpdate -- Update delay time on server to decrease it
TaskManager:RunProcess -- Execute process and handle related animations and delays
TaskManager:RunBatch -- Batch execute operations on multiple objects and return results
TaskManager:RunCore -- Execute individual object core operations on client and play actions
TaskManager:AddDelay -- Add additional delay to total delay time on server
TaskManager:GetCoreDelay -- Return basic delay time for specific operation
TaskManager:GetBatchDelay -- Calculate and return total delay time for batch operations
TaskManager:BeginDuel -- Handle initial setup and first round start when duel begins
TaskManager:EndDuel -- Perform winner handling and follow-up operations when duel ends
TaskManager:DeclareEndRound -- Handle processing logic when player declares round end
TaskManager:BeginRound -- Handle MP distribution and card drawing when new round begins
TaskManager:EndRound -- Handle battle phase and freeze release when round ends
TaskManager:BeginTurn -- Handle initial setup and trigger activation when player's turn begins
TaskManager:EndTurn -- Handle follow-up processing and trigger activation when player's turn ends
TaskManager:BattlePhase -- Handle minion battles and direct attacks in battle phase
TaskManager:Battle -- Execute battle between two minions and handle damage
TaskManager:GainMp -- Distribute MP to players to increase mana resources
TaskManager:LoseMp -- Deduct MP from players to consume mana resources
TaskManager:Play -- Play card to handle minion summoning or skill use
TaskManager:Place -- Place cards on field to summon as minions
TaskManager:Cast -- Use skill card to apply effects to target
TaskManager:Put -- Add new card to deck using blueprint
TaskManager:Add -- Add new card to hand using blueprint
TaskManager:Draw -- Draw cards from deck to hand or handle overdraw
TaskManager:Overdraw -- Handle overdrawn cards when hand is full
TaskManager:Fatigue -- Apply fatigue damage when deck is empty
TaskManager:Return -- Return cards in hand back to deck
TaskManager:Discard -- Handle discarding cards in hand and save records
TaskManager:InsertAddCostEnchantment -- Add cost increase enchantment to cards
TaskManager:InsertSetCostEnchantment -- Add cost fix enchantment to cards
TaskManager:Summon -- Summon minion to field using blueprint
TaskManager:Dead -- Handle dead minions and remove from field
TaskManager:Kick -- Return minions from field to hand
TaskManager:Vanish -- Make minions completely disappear from field
TaskManager:Transform -- Transform minions into other minions
TaskManager:DirectAttack -- Make minion perform direct attack on opponent player
TaskManager:Kill -- Immediately kill living units
TaskManager:Damage -- Deal damage to units and handle related effects
TaskManager:Heal -- Heal units' HP to increase vitality
TaskManager:Freeze -- Apply freeze status to minions to restrict movement
TaskManager:Thaw -- Melt ice of frozen minions to release status
TaskManager:Stun -- Apply stun status to minions to make them unable to act
TaskManager:Scare -- Apply fear status to minions to interfere with battle
TaskManager:Awake -- Wake stunned minions to release status and activate
TaskManager:GainBarrier -- Give barrier effect to minions to enhance protection ability
TaskManager:LoseBarrier -- Remove minions' barriers to remove protection effect
TaskManager:InsertAddTriggerNameEnchantment -- Apply trigger addition enchantment to objects to give new abilities
TaskManager:InsertAddAuraNameEnchantment -- Apply aura addition enchantment to objects to give persistent effects
TaskManager:InsertAddMaxHpEnchantment -- Apply max HP increase enchantment to objects
TaskManager:InsertSetMaxHpEnchantment -- Apply max HP fix enchantment to objects
TaskManager:InsertAddAtkEnchantment -- Apply attack power increase enchantment to objects
TaskManager:InsertSetAtkEnchantment -- Apply attack power fix enchantment to objects
TaskManager:InsertSetVenomEnchantment -- Set venom effect enchantment on objects to give special abilities
TaskManager:SortMinions -- Sort minions on field using given comparison function
TaskManager:MoveMinionToFarLeft -- Move minion to leftmost end of field
TaskManager:MoveMinionToFarRight -- Move minion to rightmost end of field
TaskManager:Cross -- Move minion to opponent's field to change ownership
TaskManager:InsertSetRandomBattleEnchantment -- Set random battle enchantment on duel to change battle method
TriggerManager:InvokeTriggers -- Invoke triggers and open cards to execute triggers
TriggerManager:RunTriggers -- Execute all triggers of specific object
TriggerManager:RunTrigger -- Execute individual trigger
TriggerManager:IsTriggerCondition -- Check trigger condition
TriggerManager:ShareOpenCards -- Share cards to be revealed by triggers
TriggerManager:AirStrike -- Air Strike skill - damage opponent units, additional damage if hand is empty
TriggerManager:AirStrikeCondition -- Air Strike trigger condition - when cast
UIManager:OnBeginPlay -- Create and set basic modules when initializing UI manager
UIManager:SetMobileUIEnable -- Set activation state of mobile UI elements on mobile platform
UIManager:SpawnAndSetModule -- Create and set specified module
UIManager:UpdateButtons -- Hierarchically update button activation states of all UI modules
UIManager:UpdatePlayerController -- Update player controller activation state according to UI module state
UIManager:UpdateChat -- Update chat system activation state
UIManager:UpdateMobileUI -- Update mobile UI activation state according to game state and UI module state
Card:OnBeginPlay -- Add to playable and signable arrays on client at game start
Card:GetPublicProperties -- Return publicly available card properties (player, deck, hand)
Card:GetProperties -- Return all card properties as table
Card:OnSyncProperties -- Reset player and update blueprint when synchronizing properties
Card:SetPropertiesInClient -- Create actor after setting properties on client
Card:SyncProperties -- Synchronize card properties to user (full for allies, public info only for enemies)
Card:SetVariables -- Set card variables (cost, max HP, attack power)
Card:ClearVariables -- Initialize all card variables
Card:SetTriggerNames -- Set trigger names and check if target is needed
Card:GetBlueprint -- Return card blueprint information (info, enchantments, independent variables)
Card:SetBlueprint -- Set card information from blueprint
Card:ClearBlueprint -- Initialize all card blueprint information
Card:Clear -- Clean up and destroy card
Card:GetInputState -- Check if character can play this card and return input state
Card:SetInputState -- Set input state to determine playability and target array
Card:IsOwner -- Check if card owner
Card:IsAllyWith -- Check if on same side as specified character
Card:IsAlly -- Check if ally
Card:ShareId -- Share card ID between server and client
Card:SharePrivateId -- Share card ID privately only to allies
Card:ShareBlueprint -- Share card blueprint between server and client
Card:SharePrivateBlueprint -- Share card blueprint privately only to allies
Card:GetActorPosition -- Return card actor's world coordinates as 2D vector
Card:SpawnAndSetActor -- Create and set card actor
Card:SetActor -- Set card actor and connect cross-references
Card:ClearActor -- Release actor reference and clean up front/back
Card:DestroyActor -- Destroy actor entity and clean up
Card:SpawnAndSetFront -- Create and set card front
Card:SetFront -- Set card front and connect UI elements
Card:ClearFront -- Release card front reference and clean up UI elements
Card:DestroyFront -- Destroy card front entity and clean up
Card:SpawnAndSetBack -- Create and set card back
Card:SetBack -- Set card back and connect touch events
Card:ClearBack -- Release card back reference
Card:DestroyBack -- Destroy card back entity and clean up
Card:SetActorEnable -- Set actor activation state
Card:SetInfo -- Set card information and initialize related properties
Card:ClearInfo -- Initialize card information and destroy front
Card:SetBackName -- Set card back name and create back
Card:ClearBackName -- Initialize card back name and destroy back
Card:SetPlayer -- Set card player and apply corresponding player's card back
Card:ClearPlayer -- Release player reference and clean up back
Card:GetBlueprintByName -- Create and return blueprint with card name
Card:GetBlueprintsByNames -- Create blueprint array with multiple card names
Card:GetCardTokens -- Create and return card tokens with card names
Card:GetMinionEnchantments -- Filter and return only minion-related enchantments
Card:GetMinionBlueprint -- Return blueprint for minion creation
Card:Destroy -- Completely destroy card and clean up resources
Card:SetFace -- Display card front or back
Card:SetAnchorTransform -- Immediately set anchor position and rotation while maintaining actor's world coordinates
Card:DestroyTweener -- Destroy tweener to clean up animation
Card:DestroyAnchorTweener -- Destroy anchor tweener to clean up anchor animation
Card:TransformAnchorTo -- Animate anchor movement to specified position and rotation
Card:TransformToAnchor -- Animate card movement to anchor position
Card:TransformToTarget -- Animate card movement to target selection position
Card:TransformToCast -- Animate card movement to casting position
Card:AttachToAnchor -- Attach card actor to anchor entity
Card:PlaceFront -- Place card in front layer
Card:PlaceBack -- Place card in back layer
Card:IsPlayable -- Check if card is playable (check turn, mana, target, field state)
Card:UpdateInputState -- Update card input state to refresh targetable objects
Card:SetSignState -- Set card sign state to change visual display
Card:SetPlayableSign -- Set sign display according to card playability
Card:BeginPlayingServerAttribute -- Server attribute method called when card play starts on server
Card:BeginPlaying -- Start card play on server and notify client
Card:BeginPlayingInClient -- Handle card play start processing and animation on client
Card:EndPlayingServerAttribute -- Server attribute method called when card play ends on server
Card:EndPlaying -- End card play on server and notify client
Card:EndPlayingInClient -- Handle card play end processing and animation on client
Card:IsInTouchArea -- Check if specified point is within card's touch area
Card:SetDisplayTimer -- Set card display timer to make undisplayable after certain time
Card:ClearDisplayTimer -- Release card display timer
Card:Swap -- Exchange ID and blueprint with another card
Card:Open -- Reveal card for all players to see
Card:PrivateOpen -- Reveal card privately only to allies
Card:Play -- Play card to trigger effect (implementation needed)
Card:Cast -- Cast card to trigger immediate effect (implementation needed)
Card:Put -- Put card in deck and play animation
Card:Add -- Add card to hand and play animation
Card:Draw -- Draw card from deck to hand and show front
Card:Overdraw -- Overdraw card to play destruction effect and sound
Card:Return -- Return card from hand to deck and play animation
Card:Discard -- Discard card and play disposal effect and sound
Card:SetCost -- Set card cost and update UI and color change
Card:SetMaxHp -- Set card max HP and update UI and color change
Card:SetAtk -- Set card attack power and update UI and color change
Card:AddCostEnchantment -- Apply enchantment that adds delta value to card cost
Card:InsertAddCostEnchantment -- Insert cost addition enchantment into enchantment array
Card:SetCostEnchantment -- Apply enchantment that sets card cost to specific value
Card:InsertSetCostEnchantment -- Insert cost setting enchantment into enchantment array
Card:AddMaxHpEnchantment -- Apply enchantment that adds delta value to card max HP
Card:InsertAddMaxHpEnchantment -- Insert max HP addition enchantment into enchantment array
Card:SetMaxHpEnchantment -- Apply enchantment that sets card max HP to specific value
Card:InsertSetMaxHpEnchantment -- Insert max HP setting enchantment into enchantment array
Card:AddAtkEnchantment -- Apply enchantment that adds delta value to card attack power
Card:InsertAddAtkEnchantment -- Insert attack power addition enchantment into enchantment array
Card:SetAtkEnchantment -- Apply enchantment that sets card attack power to specific value
Card:InsertSetAtkEnchantment -- Insert attack power setting enchantment into enchantment array
Deck:GetProperties -- Return deck properties as table for network synchronization
Deck:OnSyncProperties -- Place cards on screen when property synchronization completes on client
Deck:Clear -- Remove all cards from deck and release deck references for initialization
Deck:IsOwner -- Check if current player is owner of this deck
Deck:SetSide -- Set whether deck is ally or enemy and adjust screen position
Deck:InsertCardsWithoutShuffle -- Insert cards into deck maintaining order and stack on screen
Deck:InsertCards -- Shuffle cards randomly and insert into deck
Deck:InsertCard -- Insert single card at random position in deck to implement shuffle effect
Deck:RemoveCards -- Remove multiple cards from deck and clean up screen
Deck:RemoveCard -- Remove single card from deck and release deck reference
Deck:PileUpCards -- Stack deck cards along Z-axis
Deck:PlaceCards -- Place all deck cards in proper position and display UI during duel
Deck:SetCardsCount -- Display deck card count in UI and apply animation effect
Deck:AddCardsCount -- Add change amount to current card count and update UI
Deck:SpawnAndSetImageEntity -- Create image entity matching player's card back style
Deck:ShowDetails -- Display deck detail information on screen with animation
Deck:HideDetails -- Hide deck detail information and clean up related UI
Deck:GetCards -- Return copy of deck cards with optional selector function filtering
Deck:GetTopCards -- Get specified number of top cards from deck on server
Deck:ShareTopCards -- Share top cards of deck between server and client for synchronization
Duel:GetProperties -- Return duel's synchronizable properties as table
Duel:OnSyncProperties -- Update duel state on client after property synchronization
Duel:Clear -- Initialize duel state
Duel:OnBeginPlay -- Initial setup and object array initialization when duel starts
Duel:SetVariables -- Set duel variables from variable table
Duel:ClearVariables -- Initialize all duel variables
Duel:Sync -- Synchronize duel properties from server to client
Duel:Sort -- Sort object array by ID order
Duel:InsertObject -- Add new object to duel and assign ID
Duel:RemoveObject -- Remove object from duel
Duel:Invoke -- Call specified method on all objects
Duel:ShareAcquiredCards -- Acquire specified number of cards and return as array
Duel:ShareAcquiredCard -- Acquire one card, set actor, and return
Duel:AcquireCard -- Get card from pool or create new on server
Duel:ReleaseCard -- Return used card to reserve storage
Duel:RecycleCards -- Recycle reserve storage cards to pool
Duel:SpawnAndSetShowingCard -- Create card display object on client
Duel:ShareAcquiredMinions -- Acquire specified number of minions and return as array
Duel:ShareAcquiredMinion -- Acquire one minion, set actor, and return
Duel:AcquireMinion -- Get minion from pool or create new on server
Duel:ReleaseMinion -- Return used minion to reserve storage
Duel:RecycleMinions -- Recycle reserve storage minions to pool
Duel:SetPlacingMinion -- Set placing minion and create actor on client
Duel:SpawnAndSetPlacingMinion -- Create and set placing minion on server
Duel:SharePlacingMinion -- Share placing minion and add to object array
Duel:DestroyPlacingMinion -- Destroy placing minion
Duel:UpdateEnchantments -- Update enchantments and reapply auras
Duel:ApplyAuras -- Initialize and reapply all aura enchantments
Duel:ShowCard -- Display card on screen on client
Duel:GetWinner -- Determine and return duel winner
Duel:HasDeadPlayer -- Check if there are dead players
Duel:HasDeadMinion -- Check if there are dead minions
Duel:GetDeadMinions -- Return all dead minions as array
Duel:HasBattler -- Check if there are battle-capable minions
Duel:HasBattlerBoth -- Check if both players have battle-capable minions
Duel:GetFrontBattlers -- Return front battle minions of both players
Duel:GetDirectAttackers -- Return minions capable of direct attack
Duel:GetMinions -- Return all minions according to selector
Duel:ShareRandomMinions -- Share randomly selected minions and return
Duel:GetUnits -- Return all units (players + minions)
Duel:ShareRandomUnits -- Share randomly selected units and return
Duel:GetPlayers -- Return copy of all players
Duel:ShareRandomPlayer -- Share randomly selected player and return
Duel:GetCards -- Return all cards according to selector
Duel:GetDeckCards -- Return all deck cards according to selector
Duel:GetHandCards -- Return all hand cards according to selector
Duel:ShareRandomHandCards -- Share randomly selected hand cards and return
Duel:SetBeginDuelTimer -- Set duel start timer when both players are ready
Duel:SetBeginDuelTimerInClient -- Display duel start announcement message on client
Duel:ClearBeginDuelTimer -- Cancel duel start timer and remove client message
Duel:ClearBeginDuelTimerInClient -- Remove duel start message on client
Duel:BeginDuel -- Start duel and perform initial setup
Duel:SetSides -- Distinguish and set our/enemy players on client
Duel:PlacePlayers -- Place players at default positions
Duel:ShowIntro -- Display duel start intro animation and effects
Duel:PutDeckCards -- Place cards in players' decks and perform animation
Duel:DrawStartingCards -- Draw initial cards at game start
Duel:EndDuel -- End duel and perform cleanup
Duel:ShowOutro -- Display duel end outro animation and results
Duel:ReturnEndingCards -- Return hand cards to deck at game end
Duel:EraseDeckCards -- Remove all cards from deck and perform animation
Duel:EndMatch -- Handle match end processing and reward distribution on server
Duel:ShowResult -- Display game result and rewards on screen on client
Duel:DarkenBackground -- Darken background when duel starts
Duel:LightenBackground -- Brighten background when duel ends
Duel:EndRound -- End round and initialize player states
Duel:BeginRound -- Start new round and set round player
Duel:EndTurn -- End turn and clean up timer and states
Duel:BeginTurn -- Start new turn and set turn player
Duel:BeginCountdown -- Start turn end countdown on client
Duel:EndCountdown -- Handle countdown end processing on client
Duel:BattlePhase -- Handle battle phase (currently empty)
Duel:Battle -- Handle minion battles (currently empty)
Duel:SetRandomBattle -- Set random battle mode
Duel:SetRandomBattleEnchantment -- Set random battle mode with enchantment
Duel:InsertSetRandomBattleEnchantment -- Insert random battle mode enchantment
Field:GetProperties -- Return field properties as table
Field:OnSyncProperties -- Copy local minion array and place when synchronizing properties
Field:Clear -- Remove all minions from field and initialize
Field:GetInputState -- Check if character can place minions on this field
Field:SetInputState -- Set input state to determine placement possibility
Field:IsOwner -- Check if field owner
Field:IsEmpty -- Check if field is empty
Field:IsFull -- Check if field is full
Field:GetMinions -- Return minions meeting selector conditions
Field:ShareRandomMinions -- Share randomly selected specified number of living minions meeting conditions
Field:GetLeftmostMinion -- Return leftmost minion
Field:GetRightmostMinion -- Return rightmost minion
Field:GetFrontMinion -- Return frontmost minion (first minion)
Field:HasDeadMinion -- Check if there are dead minions
Field:GetDeadMinions -- Return all dead minions
Field:HasBattler -- Check if there are battle-capable minions
Field:GetBattlers -- Return all battle-capable minions
Field:GetDirectAttackers -- Return all direct attack capable minions
Field:GetFrontBattler -- Return front battle minion (random selection in random battle)
Field:SetSide -- Set field affiliation and adjust position
Field:PlaceMinions -- Place all minions on anchors and initialize positions
Field:InsertMinions -- Insert multiple minions behind pivot minion
Field:InsertMinion -- Insert single minion at specified index
Field:RemoveMinions -- Remove multiple minions from field
Field:RemoveMinion -- Remove single minion from field
Field:InsertPlacingMinon -- Insert placing minion at appropriate position based on X coordinate
Field:RemovePlacingMinion -- Remove placing minion
Field:SpawnAndAttachToAnchor -- Create and attach anchor to minion
Field:SpawnAnchor -- Create anchor entity for minion
Field:DestroyAnchor -- Destroy minion's anchor entity
Field:DropAnchors -- Place all minions' anchors in a row
Field:GetCurrentPlaceIndex -- Return index of currently placing minion
Field:GetNextPlaceIndex -- Calculate next placement index based on X coordinate
Field:FindPlacePivot -- Find and return pivot minion for placement reference
Field:SortMinions -- Sort minions and rearrange anchors
Field:MoveMinionToFarLeft -- Move minion to leftmost position
Field:MoveMinionToFarRight -- Move minion to rightmost position
Field:GetEmptySlotCount -- Return number of empty slots in field
Hand:GetProperties -- Return hand properties as table
Hand:OnSyncProperties -- Place cards and adjust hand position when synchronizing properties
Hand:Clear -- Remove all cards from hand and initialize
Hand:IsOwner -- Check if hand owner
Hand:IsEmpty -- Check if hand is empty
Hand:IsFull -- Check if hand is full
Hand:GetCards -- Return cards meeting selector conditions
Hand:ShareRandomCards -- Share randomly selected specified number of cards meeting conditions
Hand:ShareRandomBlueprints -- Share blueprints of randomly selected cards meeting conditions
Hand:SetSide -- Set hand affiliation (our/enemy side)
Hand:InsertCards -- Insert multiple cards into hand and place on anchors
Hand:InsertCard -- Insert single card into hand
Hand:RemoveCards -- Remove multiple cards from hand and destroy anchors
Hand:RemoveCard -- Remove single card from hand
Hand:RemovePlayingCard -- Remove playing card from local array
Hand:SpawnAndAttachToAnchor -- Create and attach anchor to card
Hand:SpawnAnchor -- Create anchor entity for card
Hand:DestroyAnchor -- Destroy card's anchor entity
Hand:DropAnchors -- Place card anchors in circular arrangement
Hand:GetAnchorPosition -- Calculate anchor position with radius and rotation angle
Hand:PlaceCards -- Place all cards on anchors and initialize positions
Hand:DestroyTweener -- Destroy hand tweener
Hand:TransformToPlay -- Move hand to play position
Hand:TransformToRest -- Move hand to rest position
Hand:TransformToEndRound -- Move hand to round end position
Hand:GetLeftmostCard -- Return leftmost card
Hand:GetRightmostCard -- Return rightmost card
History:GetProperties -- Return history data as table for network synchronization
History:Initialize -- Initialize history data tables for all players at duel start
History:Clear -- Completely initialize all history data at duel end
History:GetThisRoundCardCount -- Return total number of cards played by player in current round
History:GetThisRoundMinionCount -- Calculate number of minion cards summoned by player in current round
History:GetThisRoundMinionCountByTag -- Calculate number of minion cards with specific tag summoned in current round
History:GetThisRoundSkillCount -- Calculate number of skill cards used by player in current round
History:ClearThisRoundCard -- Initialize player's round card usage record at round end
History:AddThisRoundCard -- Add to round record when player plays card
History:GetThisGameCardCount -- Return total number of cards played by player in current game
History:GetThisGameMinionCount -- Calculate total number of minion cards summoned by player in current game
History:GetThisGameMinionsByTag -- Return list of minion names with specific tag in current game
History:GetThisGameMinionsByCost -- Return list of minion names with specific cost in current game
History:GetThisGameSkillCount -- Calculate total number of skill cards used by player in current game
History:GetThisGameSkillCountByCostOrMore -- Calculate number of skill cards used with specified cost or more in current game
History:ClearThisGameCard -- Initialize player's game card usage record at game end
History:AddThisGameCard -- Add to game-wide record when player plays card
History:GetThisGameDeadMinions -- Return list of player's dead minions in current game
History:GetThisGameDeadMinionsByTag -- Return list of dead minions with specific tag in current game
History:ClearThisGameDeadMinion -- Initialize player's dead minion record at game end
History:AddThisGameDeadMinion -- Add to game-wide death record when minion dies
History:GetThisRoundDeadMinionCount -- Return number of dead minions in current round
History:GetThisRoundDeadMinions -- Return list of dead minions in current round
History:ClearThisRoundDeadMinion -- Initialize player's round dead minion record at round end
History:AddThisRoundDeadMinion -- Add to round death record when minion dies
History:GetThisGameMp -- Return total mana points used by player in current game
History:AddThisGameMp -- Add to game-wide mana usage when player consumes mana
History:GetThisGameDiscardedCardCount -- Return number of discarded cards in current game
History:GetThisGameDiscardedCards -- Return list of discarded cards in current game
History:AddThisGameDiscardedCard -- Add to game-wide discard record when card is discarded
Minion:GetProperties -- Return all minion properties as table
Minion:SetPropertiesInClient -- Set properties on client and create actor
Minion:OnSyncProperties -- Reset blueprint and player information when synchronizing properties
Minion:SetVariables -- Set minion variables (attack power, barrier, venom, etc.)
Minion:GetIndependentVariables -- Return independent variables as table (barrier, freeze, stun, fear states)
Minion:ClearVariables -- Initialize all minion variables
Minion:GetBlueprint -- Return minion blueprint information
Minion:SetBlueprint -- Set minion information from blueprint
Minion:ClearBlueprint -- Initialize all minion blueprint information
Minion:GetInputState -- Check if character can control this minion and return input state
Minion:SetInputState -- Set input state to determine minion control possibility
Minion:SetBody -- Set minion body and connect UI elements
Minion:ClearBody -- Release minion body reference and clean up UI elements
Minion:SetName -- Set minion name and load related entries and resources
Minion:Initialize -- Initialize minion and set basic state
Minion:Clear -- Clean up and destroy minion
Minion:Dead -- Play death animation and effects when minion dies
Minion:GetLookAtDirection -- Return direction minion is facing (-1: left, 1: right)
Minion:GetLookAtPosition -- Calculate offset position considering minion's facing direction
Minion:LookAtPoint -- Set minion direction to face specified point
Minion:LookNothing -- Reset minion direction to default state
Minion:Kill -- Immediately kill minion and play hit animation
Minion:Damage -- Take damage from attacker and return result (handle barrier, venom, freeze, etc.)
Minion:GetInverseScale -- Calculate and return inverse of original scale
Minion:IsOwner -- Check if minion owner
Minion:IsBattler -- Check if minion is in battle-capable state (not frozen)
Minion:IsDirectAttacker -- Check if minion can direct attack (battle-capable and direct attack possible)
Minion:SummonCoroutine -- Start minion summon coroutine
Minion:SpawnAndSetActor -- Create and set minion actor
Minion:DestroyActor -- Destroy minion actor entity and clean up
Minion:SpawnAndSetBody -- Create and set minion body
Minion:DestroyBody -- Destroy minion body entity and clean up
Minion:SetActorEnable -- Set minion actor activation state
Minion:GetBlueprintByName -- Create and return blueprint with card name
Minion:GetBlueprintsByNames -- Create blueprint array with multiple card names
Minion:GetCardTokens -- Create and return card tokens with card names
Minion:SetInfo -- Set minion information and initialize related properties
Minion:ClearInfo -- Initialize minion information and destroy body
Minion:SetPlayer -- Set minion player
Minion:ClearPlayer -- Release player reference
Minion:Destroy -- Completely destroy minion and clean up resources
Minion:Animate -- Change minion animation state
Minion:GetOtherUnits -- Return all units except self
Minion:ShareRandomOtherUnits -- Select randomly specified number of living units except self
Minion:GetOtherMinions -- Return other minions except self according to selector conditions
Minion:ShareRandomOtherMinions -- Select randomly specified number of living other minions except self
Minion:GetOurOtherUnits -- Return allied units except self
Minion:ShareRandomOurOtherUnits -- Select randomly specified number of living allied units except self
Minion:GetOurOtherMinions -- Return allied minions except self according to selector conditions
Minion:ShareRandomOurOtherMinions -- Select randomly specified number of living allied minions except self
Minion:GetLeftMinion -- Return minion to the left of self according to selector conditions
Minion:GetLeftMinions -- Return specified number of minions to the left of self according to selector conditions
Minion:GetRightMinion -- Return minion to the right of self according to selector conditions
Minion:GetRightMinions -- Return specified number of minions to the right of self according to selector conditions
Minion:GetSelfAndRightMinions -- Return self and right minions combined
Minion:GetAdjacentMinions -- Return adjacent minions of self (1 left, 1 right)
Minion:GetSelfAndAdjacentMinions -- Return self and all adjacent minions combined
Minion:Summon -- Summon minion and execute summon action
Minion:Kick -- Kick minion to remove from field and play effects
Minion:Vanish -- Make minion disappear and deactivate actor
Minion:Transform -- Transform minion to another form and play transformation effects
Minion:DirectAttack -- Perform direct attack by minion (implementation needed)
Minion:Freeze -- Make minion frozen
Minion:Thaw -- Release minion's frozen state
Minion:Stun -- Make minion stunned
Minion:Awake -- Release minion's stunned state
Minion:Scare -- Make minion scared
Minion:GainBarrier -- Minion gains barrier
Minion:LoseBarrier -- Minion loses barrier
Minion:SetAtk -- Set minion attack power and update UI and color change
Minion:AddAtkEnchantment -- Apply enchantment that adds delta value to minion attack power
Minion:InsertAddAtkEnchantment -- Insert attack power addition enchantment into enchantment array
Minion:SetAtkEnchantment -- Apply enchantment that sets minion attack power to specific value
Minion:InsertSetAtkEnchantment -- Insert attack power setting enchantment into enchantment array
Minion:SetBarrier -- Set minion barrier state and apply visual effects
Minion:SetVenom -- Set minion venom state and change visual display
Minion:SetVenomEnchantment -- Apply enchantment that sets minion venom state
Minion:InsertSetVenomEnchantment -- Insert venom setting enchantment into enchantment array
Minion:SetChill -- Set minion chill state
Minion:SetDirectAttackable -- Set minion direct attack possibility
Minion:SetImmuneToStrong -- Set minion immunity to strong attacks
Minion:SetFreeze -- Set minion freeze state and apply animation and visual effects
Minion:SetStun -- Set minion stun state and change visual display
Minion:SetScare -- Set minion fear state and change visual display
Object:OnBeginPlay -- Set reference to duel-related managers at game start
Object:IsUnit -- Check if this object is a unit
Object:IsMinion -- Check if this object is a minion
Object:IsPlayer -- Check if this object is a player
Object:IsCard -- Check if this object is a card
Object:GetProperties -- Return all object properties as table
Object:SetProperties -- Set object properties using received property table
Object:SetPropertiesInClient -- Set properties on client
Object:SyncProperties -- Synchronize properties from server to client
Object:OnSyncProperties -- Reset blueprint after property synchronization
Object:IsTargetable -- Check if player can target this object
Object:SetName -- Set object name and entry
Object:ClearName -- Initialize object name and entry
Object:SetEnchantments -- Set and apply enchantment array
Object:ClearEnchantments -- Initialize all enchantments
Object:SetVariables -- Set trigger and aura names from variable table
Object:ClearVariables -- Initialize all variables
Object:GetIndependentVariables -- Return independent variables as table
Object:InsertEnchantment -- Add new enchantment and apply
Object:ApplyEnchantments -- Apply all enchantments and auras to update variables
Object:Initialize -- Initialize object and apply enchantments
Object:Clear -- Initialize all object data
Object:SetTriggerNames -- Set trigger name array
Object:AddTriggerNameEnchantment -- Add trigger name with enchantment
Object:InsertAddTriggerNameEnchantment -- Insert trigger name addition enchantment
Object:SetAuraNames -- Set aura name array
Object:AddAuraNameEnchantment -- Add aura name with enchantment
Object:InsertAddAuraNameEnchantment -- Insert aura name addition enchantment
Object:InsertAuraEnchantments -- Add aura enchantments to array
Object:ClearAuraEnchantments -- Initialize all aura enchantments
Object:GetBlueprint -- Return object blueprint information
Object:SetBlueprint -- Set object information from blueprint
Object:ClearBlueprint -- Initialize all blueprint-related data
Object:TryRemoveEnchantments -- Attempt to remove enchantments meeting conditions
Object:GetInputState -- Return character input state (override in subclass)
Object:SetInputState -- Set input state (override in subclass)
Player:GetProperties -- Return player's core properties as table for network synchronization
Player:OnSyncProperties -- Update player UI and game state on client after property synchronization completion
Player:SetVariables -- Set player variables from variable table
Player:GetIndependentVariables -- Return independent variables as table
Player:ClearVariables -- Initialize all player variables
Player:Clear -- Initialize all player data
Player:Initialize -- Initialize player and set basic state
Player:OnBeginPlay -- Initial player setup and event connections at game start
Player:GetLookAtDirection -- Return direction player is facing
Player:GetLookAtPosition -- Calculate offset position according to player's facing direction
Player:LookLeft -- Set player to face left
Player:LookRight -- Set player to face right
Player:LookNothing -- Set player to face default direction (according to our/enemy side)
Player:Damage -- Handle player taking damage and display effects
Player:SetName -- Set player name and entry
Player:ReadyServerAttribute -- Server attribute preparation (for override)
Player:Ready -- Handle processing when player completes duel participation preparation on server
Player:ReadyInOwner -- Handle duel preparation completion for owner player on client
Player:ReadyInClient -- Set player character connection on client
Player:FixCharacter -- Fix character to player on server and set up
Player:FixCharacterInOwner -- Handle character fixing on owner client
Player:FixCharacterInClient -- Handle character fixing on general client
Player:FixCharacterNone -- Default character fixing setup
Player:FixCharacterSync -- Set character for duel mode (disable movement, etc.)
Player:TardyServerAttribute -- Server attribute delay handling (for override)
Player:Tardy -- Handle processing when player leaves duel on server
Player:TardyInOwner -- Restore UI after leaving duel on owner client
Player:TardyInClient -- Clean up after leaving duel on general client
Player:UnfixCharacter -- Separate character from player on server and restore original state
Player:UnfixCharacterInOwner -- Handle character separation on owner client
Player:UnfixCharacterInClient -- Handle character separation on general client
Player:UnfixCharacterNone -- Default character separation setup
Player:UnfixCharacterSync -- Restore character to normal mode (enable movement, etc.)
Player:SetServing -- Set player service state (duel participation availability)
Player:IsOwner -- Check if this player is local player
Player:IsAlly -- Check if this player is ally
Player:IsAllyWith -- Check if in allied relationship with specified character
Player:SetSide -- Set player side on client (our/enemy side)
Player:SetFloating -- Set player floating animation
Player:PlayEmotion -- Play emotion animation on player character
Player:Animate -- Play specified animation on player character
Player:IsOurTurn -- Check if it's currently this player's turn
Player:ShowClassTag -- Display player's class tag
Player:HideClassTag -- Hide player's class tag
Player:ShowDetails -- Display player's HP, MP detailed information
Player:HideDetails -- Hide player's HP, MP detailed information
Player:TransformAnchorToPlay -- Move player anchor to play position
Player:TransformAnchorToEndRound -- Move player anchor to battle position
Player:SetPlaying -- Set player playing state and adjust animation
Player:SetRoundPlayerSign -- Set round player indicator (change background color)
Player:JobsDone -- Check if player has no more cards to play
Player:GetUnits -- Return unit array including player and their minions
Player:ShareRandomUnits -- Share randomly selected units of this player and return
Player:GetCards -- Return all player cards according to selector (deck + hand)
Player:DeclareEndRound -- Player declares round end
Player:SetEndRoundDeclared -- Set round end declaration state
Player:SetMaxMp -- Set player's maximum MP
Player:SetMp -- Set player's current MP and update UI
Player:GainMp -- Gain MP and display effects
Player:LoseMp -- Lose MP
Player:SetSkillDamage -- Set player's skill damage
Player:AddSkillDamageEnchantment -- Add skill damage with enchantment
Player:InsertAddSkillDamageEnchantment -- Insert skill damage addition enchantment
Player:SetTaggedSkillDamages -- Set skill damage table by tag
Player:AddSkillDamageByTagEnchantment -- Add skill damage for specific tag with enchantment
Player:InsertAddSkillDamageByTagEnchantment -- Insert tag-based skill damage addition enchantment
Player:Chat -- Display chat message above player
Player:ClearChat -- Remove chat message
Player:SpawnAndSetFriendRequestButton -- Create and set friend request button
Player:ShowFriendRequestButton -- Display friend request button (when conditions are met)
Player:HideFriendRequestButton -- Hide friend request button
Player:SetImmuneToDirectAttack -- Set immunity to direct attack state
Player:SetImmuneToDirectAttackEnchantment -- Set immunity to direct attack state with enchantment
Player:InsertSetImmuneToDirectAttackEnchantment -- Insert direct attack immunity enchantment
Player:HandleKeyDownEvent -- Handle keyboard input events (Alt/Space to exit duel)
Player:HandleButtonClickEvent -- Handle button click events (exit duel)
Player:HandleChatEvent -- Handle chat events (display player chat message)
Unit:SetVariables -- Set unit variables (survival state, max HP, current HP)
Unit:GetIndependentVariables -- Return independent variables as table (death state, current HP)
Unit:ClearVariables -- Initialize all unit variables
Unit:IsTargetable -- Check if player can target this unit
Unit:Initialize -- Initialize unit and set survival state, set HP to maximum
Unit:OnBeginPlay -- Add self to signable array on client at game start
Unit:SetActor -- Set unit actor and connect cross-references
Unit:ClearActor -- Release actor reference and clean up body as well
Unit:SetBody -- Set unit body and connect UI elements
Unit:ClearBody -- Release body reference and clean up related UI elements
Unit:SetSignState -- Set unit sign state and display with color
Unit:PlaceFront -- Place actor in front layer
Unit:PlaceBack -- Place actor in back layer
Unit:GetActorPosition -- Return actor's world coordinates as 2D vector
Unit:DestroyTweener -- Destroy tweener to clean up animation
Unit:DestroyAnchorTweener -- Destroy anchor tweener to clean up anchor animation
Unit:SetAnchorTransform -- Immediately set anchor position while maintaining actor's world position
Unit:TransformAnchorTo -- Animate anchor movement to specified position
Unit:TransformToAnchor -- Animate actor movement to anchor position
Unit:AttachToAnchor -- Attach actor to anchor
Unit:LookAt -- Set to look at another unit
Unit:LookAtPoint -- Set to look at specific point (implement in subclass)
Unit:LookLeft -- Set to look left (implement in subclass)
Unit:LookRight -- Set to look right (implement in subclass)
Unit:LookNothing -- Set to default direction (implement in subclass)
Unit:GetLookAtDirection -- Return facing direction (implement in subclass)
Unit:GetLookAtPosition -- Calculate offset position based on facing direction (implement in subclass)
Unit:GetOffsettedPositionFromPoint -- Calculate offset-applied position based on specific point
Unit:GetOffsettedPosition -- Calculate offset-applied position based on another unit
Unit:IsInTouchArea -- Check if specified point is within touch area
Unit:IsDamaged -- Check if unit has taken damage
Unit:SetDead -- Set unit survival state
Unit:SetMaxHp -- Set maximum HP and adjust current HP if exceeded
Unit:SetHp -- Set current HP and reflect in UI
Unit:Damage -- Handle taking damage (implement in subclass)
Unit:Kill -- Immediately kill unit
Unit:Dead -- Handle death (implement in subclass)
Unit:Heal -- Recover HP
Unit:AddMaxHpEnchantment -- Apply maximum HP increase enchantment
Unit:InsertAddMaxHpEnchantment -- Insert maximum HP increase enchantment and also increase current HP
Unit:SetMaxHpEnchantment -- Apply maximum HP setting enchantment
Unit:InsertSetMaxHpEnchantment -- Insert maximum HP setting enchantment and set current HP to that value
BuyPanel:OnBeginPlay -- Connect button events and handle card pack purchase and probability information when initializing purchase panel
BuyPanel:Open -- Open purchase panel and display specified card pack information
BuyPanel:Close -- Close purchase panel and hide from screen
BuyPanel:SetButtonsEnable -- Set activation state of all buttons in purchase panel
BuyPanel:ShowCardPack -- Update UI according to specified card pack and mode and display price information
CardModule:OnBeginPlay -- Connect X button events and deck-related events when initializing card module
CardModule:Open -- Open card module and set UI according to deck editing mode
CardModule:Close -- Close card module and initialize all panels
CardModule:SetMode -- Display appropriate panel according to deck editing mode setting and change card panel mode
CardModule:SetButtonsEnable -- Set activation state of all panels and buttons in card module
CardPackModule:OnBeginPlay -- Connect button events and create card entities when initializing card pack module
CardPackModule:Open -- Open card pack module and display specified card pack
CardPackModule:Close -- Close card pack module and initialize all states
CardPackModule:SetButtonsEnable -- Set activation state of card pack module buttons
CardPackModule:ShowCardPack -- Display card pack on screen and start shaking animation
CardPackModule:OpenCardPack -- Open card pack and display contained cards on screen
CardPanel:OnBeginPlay -- Perform card preloading, grid creation, event connection, etc. when initializing card panel
CardPanel:Open -- Display card panel on screen with animation
CardPanel:Close -- Close card panel and clean up all cards
CardPanel:SetButtonsEnable -- Set activation state of all buttons in card panel
CardPanel:SetCards -- Set and display cards according to specified class and conditions
CardPanel:ShowCards -- Display cards of specified page on screen
ChannelButton:OnBeginPlay -- Set scale to 0 and connect click event when initializing channel button
ChannelButton:SetChannel -- Set channel information and update UI display according to current channel state
ChannelMenu:OnBeginPlay -- Connect arrow button events and create channel buttons when initializing channel menu
ChannelMenu:Open -- Open channel menu and request channel list from server
ChannelMenu:Close -- Close channel menu and hide all buttons
ChannelMenu:SetButtonsEnable -- Set activation state of all buttons in channel menu
ChannelMenu:ShowArrowButtons -- Execute animation to display left and right arrow buttons on screen
ChannelMenu:HideArrowButtons -- Hide left and right arrow buttons from screen
ChannelMenu:ShowChannelButtons -- Display channel buttons of specified page
ChannelMenu:HideChannelButtons -- Hide all channel buttons from screen
ChatModule:OnBeginPlay -- Connect chat toggle button event and manage chat state when initializing chat module
ChatModule:SetButtonsEnable -- Set button activation state of chat module
ControlMenu:OnBeginPlay -- Set content entities, create card, and connect arrow button events when initializing control menu
ControlMenu:Open -- Open control menu and display arrow buttons and first content
ControlMenu:Close -- Close control menu and hide all UI
ControlMenu:SetButtonsEnable -- Set activation state of control menu buttons
ControlMenu:ShowArrowButtons -- Animation to display arrow buttons on screen
ControlMenu:HideArrowButtons -- Hide arrow buttons from screen
ControlMenu:ShowContent -- Display content of specified page
ControlMenu:HideContent -- Hide all content
DeckEditPanel:OnBeginPlay -- Connect complete and delete button events and create thumbnails for card placement when initializing deck edit panel
DeckEditPanel:Open -- Open deck edit panel and load current deck information to create and place card thumbnails
DeckEditPanel:Close -- Close deck edit panel and clean up all thumbnails and initialize state
DeckEditPanel:SetButtonsEnable -- Set activation state of deck edit panel buttons
DeckEditPanel:RequestSaveDeck -- Request server to save currently edited deck information
DeckEditPanel:SpawnAndSetPuttingThumbnail -- Create thumbnail for card placement and set at off-screen position
DeckEditPanel:BeginPuttingThumbnail -- Start card placement and set card information on placement thumbnail
DeckEditPanel:EndPuttingThumbnail -- End card placement and initialize placement thumbnail
DeckEditPanel:PlaceThumbnails -- Place all thumbnails in grid formation
DeckEditPanel:InsertThumbnail -- Insert new thumbnail at sorted position
DeckEditPanel:RemoveThumbnail -- Remove thumbnail from array and destroy anchor
DeckEditPanel:SpawnAndAttachToAnchor -- Create anchor for thumbnail and attach thumbnail to anchor
DeckEditPanel:SpawnAnchor -- Create anchor entity for thumbnail
DeckEditPanel:DestroyAnchor -- Destroy thumbnail's anchor and related tweeners
DeckEditPanel:DropAnchors -- Place all anchors at grid positions and apply animation
DeckEditPanel:Put -- Add card to deck and update deck size
DeckEditPanel:Erase -- Remove card from deck and update deck size
DeckEditPanel:SetDeckSize -- Calculate current deck size and display in UI with color setting
DeckMenu:OnBeginPlay -- Create warning sign, connect left and right arrow button events, and connect deck state events when initializing deck menu
DeckMenu:SetButtonsEnable -- Set activation state of deck menu buttons
DeckMenu:ShowArrowButtons -- Execute animation to display left and right arrow buttons on screen
DeckMenu:HideArrowButtons -- Hide left and right arrow buttons from screen
DeckPanel:OnBeginPlay -- Create deck menu and connect touch events for each job's deck creation when initializing deck panel
DeckPanel:Open -- Open deck panel and execute animation to display on screen
DeckPanel:Close -- Close deck panel and hide from screen
DeckPanel:SetButtonsEnable -- Set activation state of deck panel buttons (currently no implementation)
DuelModule:OnBeginPlay -- Connect card, shop, return button events and set open event when initializing duel module
DuelModule:Open -- Open duel module menu and execute animation to display on screen while displaying open event
DuelModule:Close -- Close duel module menu and execute animation to hide from screen
DuelModule:SetButtonsEnable -- Set activation state of all buttons in duel module
DuelModule:ShowOpenEvent -- Check open event period and card pack quantity to determine whether to display event UI
EmoteModule:OnBeginPlay -- Set emote images and connect touch events to handle circular emote selection when initializing emote module
EmoteModule:Open -- Open emote panel and execute animation to display at player position
EmoteModule:Close -- Close emote panel and execute animation to hide from screen
EmoteModule:SetButtonsEnable -- Set activation state of emote module touch area
EventModule:OnBeginPlay -- Connect attendance slots and button events and set event timer when initializing event module
EventModule:Open -- Open event module and set appropriate mode according to event period
EventModule:Close -- Close event module and clean up timer
EventModule:SetEventButtonEnable -- Set activation state of event button
EventModule:SetPanelButtonsEnable -- Set activation state of all buttons and attendance slots in panel
EventModule:Show -- Display event button on screen
EventModule:Hide -- Hide event button from screen
EventModule:SetMode -- Set event mode and switch UI according to special event, hot time, and original world event modes
EventModule:ReceiveCardPacksBySpecialEvent -- Receive special event attendance reward and update UI
FriendlyMatchModule:OnBeginPlay -- Create and initialize deck menu UI component when starting friendly match mode
FriendlyMatchModule:SetButtonsEnable -- Set activation state of deck menu buttons in friendly match mode
FriendSlot:OnBeginPlay -- Connect delete and follow button events and friend deletion event when initializing friend slot
FriendSlot:SetFriendOnline -- Set online friend information and display rank and location information
FriendSlot:SetFriendOffline -- Set offline friend information and display as offline state
FriendSlot:Clear -- Initialize all friend slot information
FriendSlot:SetButtonsEnable -- Set activation state of friend slot buttons
GuideModule:OnBeginPlay -- Connect guide, X, control, How button events when initializing guide module
GuideModule:Open -- Open guide module and set to control mode
GuideModule:Close -- Close guide module and hide all menus
GuideModule:SetMode -- Set guide mode and switch UI according to control or How mode
GuideModule:SetGuideButtonEnable -- Set activation state of guide button
GuideModule:SetPanelButtonsEnable -- Set activation state of all buttons in panel
HowMenu:OnBeginPlay -- Set content entities and connect arrow button events when initializing How menu
HowMenu:Open -- Open How menu and display arrow buttons and first content
HowMenu:Close -- Close How menu and hide all UI
HowMenu:SetButtonsEnable -- Set activation state of arrow buttons
HowMenu:ShowArrowButtons -- Animation to display arrow buttons on screen
HowMenu:HideArrowButtons -- Hide arrow buttons from screen
HowMenu:ShowContent -- Display content of specified page
HowMenu:HideContent -- Hide all content
InteractionModule:OnBeginPlay -- Connect cancel and friend button events when initializing interaction module
InteractionModule:Open -- Open interaction module and display other character information
InteractionModule:Close -- Close interaction module and initialize all states
InteractionModule:SetButtonsEnable -- Set activation state of interaction module buttons
InteractionModule:SetFriendButton -- Set friend button appearance and text according to friend status
LobbyModule:OnBeginPlay -- Connect card, shop, room channel, practice button events and set open event when initializing lobby module
LobbyModule:Open -- Open lobby menu and execute animation to display on screen while displaying open event
LobbyModule:Close -- Close lobby menu and hide from screen
LobbyModule:SetButtonsEnable -- Set activation state of all buttons in lobby module
LobbyModule:ShowOpenEvent -- Check open event period and card pack quantity to determine whether to display event UI
LocationModule:SetLobby -- Set lobby location information to display current channel number
LocationModule:SetRankedMatch -- Set ranked match location information to display text
LocationModule:SetFriendlyMatch -- Set friendly match location information to display current room number
LocationModule:SetPractice -- Set practice mode location information to display text
LocationModule:SetTutorial -- Set tutorial location information to display text
MesoModule:OnBeginPlay -- Connect player meso change event and update UI when initializing meso module
NoticeModule:OnBeginPlay -- Connect announcement button click event and set announcement pages by language when initializing notice module
NoticeModule:SetButtonsEnable -- Set activation state of announcement button
NoticeModule:Show -- Execute animation to display announcement button on screen
NoticeModule:Hide -- Execute animation to hide announcement button from screen
PlayerModule:OnBeginPlay -- Connect surrender button click event and handle duel end processing when initializing player module
PlayerModule:Open -- Open player menu and execute animation to display on screen
PlayerModule:Close -- Close player menu and hide from screen
PlayerModule:SetButtonsEnable -- Set activation state of player module buttons
PlayMeso:Initialize -- Initialize meso information acquired from gameplay and set UI display state
PopupModule:OnBeginPlay -- Connect refund information button event when initializing popup module
PopupModule:SetButtonsEnable -- Set activation state of popup module buttons
PopupModule:Open -- Open popup and configure UI according to message and button settings
PopupModule:Close -- Close popup and initialize all states
PopupModule:ShowBanMessage -- Display ban message and disable chat
PracticeModule:OnBeginPlay -- Create and initialize deck menu UI component when starting practice mode
PracticeModule:SetButtonsEnable -- Set activation state of deck menu buttons in practice mode
RankedMatchModule:OnBeginPlay -- Initialize ranked match module and connect events
RankedMatchModule:SetButtonsEnable -- Set activation state of ranked match related buttons
RankedMatchModule:SetMatching -- Change display state of UI elements according to matching state
RankedPlayMeso:Initialize -- Initialize ranked play meso reward information
RankedWinMeso:Initialize -- Initialize ranked win meso reward information
RankingModule:OnBeginPlay -- Initialize ranking module and connect events
RankingModule:Open -- Open ranking module and request ranking information
RankingModule:Close -- Close ranking module
RankingModule:SetButtonsEnable -- Set activation state of ranking module buttons
RankingModule:ShowRanking -- Display ranking information of specified page
RankingModule:SetRankingInfos -- Set ranking information array
RankingSlot:Initialize -- Initialize ranking slot information
RankMeso:Initialize -- Initialize rank meso reward information
RankPoint:Initialize -- Initialize rank point change amount information
RewardModule:OnBeginPlay -- Initialize reward module and connect events
RewardModule:Open -- Open reward module
RewardModule:Close -- Close reward module
RewardModule:SetRewardButtonEnable -- Set activation state of reward button
RewardModule:SetPanelButtonsEnable -- Set activation state of reward panel buttons
RewardModule:SetMode -- Switch reward mode (daily/ranked)
RewardModule:ShowDailyRewards -- Display daily reward list
RewardModule:ShowRankRewards -- Display rank reward list
RewardModule:Show -- Display reward button
RewardModule:Hide -- Hide reward button
RewardSlot:SetDailyReward -- Set daily reward information
RewardSlot:SetRankReward -- Set rank achievement reward information
RoomButton:OnBeginPlay -- Initialize room button and connect click event
RoomButton:SetRoom -- Set room information and update UI
RoomChannelModule:OnBeginPlay -- Initialize room/channel module and connect events
RoomChannelModule:Open -- Open room/channel module
RoomChannelModule:Close -- Close room/channel module
RoomChannelModule:SetButtonsEnable -- Set activation state of room/channel module buttons
RoomChannelModule:SetMode -- Switch room/channel mode
RoomMenu:OnBeginPlay -- Initialize room menu and connect events
RoomMenu:Open -- Request room list and open
RoomMenu:Close -- Close room list
RoomMenu:SetButtonsEnable -- Set activation state of room list buttons
RoomMenu:ShowArrowButtons -- Display arrow buttons
RoomMenu:HideArrowButtons -- Hide arrow buttons
RoomMenu:ShowRoomButtons -- Display room buttons of specified page
RoomMenu:HideRoomButtons -- Hide all room buttons
ShopModule:OnBeginPlay -- Initialize shop module and connect events
ShopModule:Open -- Open shop module
ShopModule:Close -- Close shop module
ShopModule:SetButtonsEnable -- Set activation state of shop module buttons
ShopPanel:OnBeginPlay -- Initialize shop panel and connect events
ShopPanel:Open -- Open shop panel
ShopPanel:Close -- Close shop panel
ShopPanel:SetButtonsEnable -- Set activation state of shop panel buttons
ShopPanel:SetLeftTabMode -- Set left tab mode
ShopPanel:SetTopTabMode -- Set top tab mode
SocialModule:OnBeginPlay -- Initialize social module and connect events
SocialModule:Open -- Open social module
SocialModule:Close -- Close social module
SocialModule:SetSocialButtonEnable -- Set activation state of social button
SocialModule:SetPanelButtonsEnable -- Set activation state of social panel buttons
SocialModule:SetPopupButtonsEnable -- Set activation state of social popup buttons
SocialModule:ShowPopup -- Display friend request popup
SocialModule:HidePopup -- Hide friend request popup
SocialModule:ShowFriendSlots -- Display friend list slots
ToastModule:ShowMessage -- Display toast message
ToastModule:Clear -- Remove toast message
TutorialModule:OnBeginPlay -- Initialize tutorial module and connect events
TutorialModule:Open -- Open tutorial module
TutorialModule:Close -- Close tutorial module
TutorialModule:SetButtonsEnable -- Set activation state of tutorial module buttons
DateTime:OnBeginPlay -- Set time offset to 0 when initializing logic
DateTime:KtcNow -- Apply Korean timezone (+9) and offset to current UTC time and return
DateTime:KtcNowDays -- Calculate and return total days based on Korean time
DateTime:SetKtcNow -- Set Korean time to specified time
DateTime:ResetKtcNow -- Initialize time offset to 0
Effect:GetLayerOptions -- Set and return effect layer options
Effect:GetUnitLayerOptions -- Return effect options suitable for unit layer
Effect:SpawnEffect -- Create and return effect entity
Effect:PlayEffect -- Play effect with fade in/out and scale out option support
Effect:MoveEffect -- Create effect and animate movement along specified path
Effect:MoveAndSpinEffect -- Animate effect with movement and simultaneous rotation
Effect:ThrowEffect -- Move effect with throwing-like animation and rotate according to direction
Effect:PlaySkillEffect -- Play unit skill effect and adjust according to unit direction
Effect:PlaySkillEffectAttached -- Play skill effect attached to unit and return effect ID
Effect:PlayHitEffect -- Play hit effect between attacker and target
Effect:PlayHitEffectAttached -- Play hit effect attached to unit and adjust according to attacker direction
Event:BuyCard -- Create and return card purchase event
Event:Unfriend -- Create and return friend deletion event
Event:SellCard -- Create and return card selling event
Event:GetChannels -- Create and return channel list query event
Event:GetFriendlyMatchRooms -- Create and return friendly match room list query event
Event:SetRoom -- Create and return room setting event
Event:GetFriends -- Create and return friend list query event
Matching:GetOrCreateLeaderBoard -- Get or create new leaderboard for ranked match
Math:Atan2 -- Calculate angle from origin in 2D coordinate system in radians
MSON:FastAnyToString -- Quickly convert arbitrary value to string in JSON format
MSON:FastStringToAny -- Quickly parse JSON string and convert to arbitrary value
MSON:AnyToString -- Convert arbitrary value to MSON format string (supports user data types)
MSON:StringToAny -- Parse MSON format string and convert to arbitrary value
MSON:GetUserDataType -- Extract and return user data type name
MSON:ReadEmpty -- Skip whitespace characters (space, tab, newline) and move to next valid character
MSON:ReadNil -- Parse 'nil' string and convert to nil value
MSON:ReadBoolean -- Parse 'true' or 'false' string and convert to boolean value
MSON:ReadNumber -- Parse number string and convert to number value
MSON:ReadString -- Parse string enclosed in quotes and convert to string value
MSON:ReadUserData -- Parse user data starting with 'userdata' keyword and convert to object
MSON:ReadTable -- Parse table enclosed in braces and convert to table object
MSON:ReadArray -- Parse array enclosed in brackets and convert to array object
MSON:ReadAny -- Select appropriate parsing method at current position and convert to arbitrary value
Queue:Initialize -- Initialize queue data structure
Queue:Push -- Add element to end of queue
Queue:Pop -- Remove and return first element of queue
Queue:Back -- Return last element of queue (without removing)
Queue:Front -- Return first element of queue (without removing)
Resource:GetTotalDelay -- Calculate and return total playback time of animation
Resource:GetStartFrameDelay -- Return delay time of animation's first frame
Resource:GetEndFrameDelay -- Return delay time of animation's last frame
Screen:PlayEffect -- Play effect on entire screen and return ID
Screen:GetZoomRatio -- Calculate zoom ratio according to screen ratio and platform
Server:Request -- Send method call request from client to server
Server:Send -- Process client request on server and send response
Server:Respond -- Receive response from server and end request state
Server:IsRequesting -- Check if currently requesting
Shop:OnBeginPlay -- Initialize shop system and set product ID mapping table
Shop:ProcessPurchase -- Process payment request and return whether to distribute card packs
Shop:PromptSinglePurchase -- Display single card pack purchase window
Shop:PromptMultiplePurchase -- Display multiple card pack purchase window
Table:Clear -- Remove all elements from table
Table:ShallowCopy -- Create and return shallow copy of table
Table:DeepCopy -- Create and return deep copy of table (recursively copy nested tables)
Table:Shuffle -- Shuffle array using Fisher-Yates algorithm
Table:GetSize -- Return number of elements in table
Table:IsEmpty -- Check if table is empty
Table:IsArray -- Check if table is array with consecutive indices
Table:Assign -- Copy all elements from source table to target table
Table:Append -- Add all elements from source array to end of target array
Table:Concat -- Return new array connecting two arrays
Table:Merge -- Return new table merging two tables
Table:Convert -- Apply specified method to all elements in table and transform
Table:Contains -- Check if specified value is contained in array
Table:Select -- Filter and return only elements meeting selection condition
Table:GetRandomElement -- Return one random element from array
Table:GetRandomElements -- Return specified number of random elements from array (with duplicates possible)
Table:GetRandomPermutation -- Return specified number of random elements from array (without duplicates)
Table:InsertToRandomIndex -- Insert element at random position in array
Table:Find -- Find and return index of specified value in array
Table:Remove -- Remove only first found specified value from array
Table:RemoveAll -- Remove all specified values from array
Table:MaxN -- Find and return largest numeric key in table
Table:Unpack -- Unpack table and return as multiple values
Table:Intersection -- Return union of two arrays (remove duplicates)
Table:Difference -- Return difference set removing elements in second array from first array
Table:StableSort -- Stably sort array using insertion sort
Table:RemoveDuplicates -- Remove duplicate elements from array and return sorted array
Table:Compare -- Recursively compare two tables and check if identical
Tween:Emphasize -- Tween to emphasize entity by vibrating scale
Tween:Damp -- Apply damping effect to entity by vibrating scale
Tween:Twitch -- Tween to make entity twitch by vibrating rotation
Tween:Spin -- Tween to rotate entity by specified angle
Tween:MoveTo -- Tween to move entity to specified position
Tween:MoveXTo -- Tween to move entity only along X axis
Tween:ScaleTo -- Tween to change entity scale to specified size
Tween:MoveAndRotateTo -- Tween to move and rotate entity simultaneously
Tween:MoveAndSpinTo -- Tween to move and rotate entity simultaneously
Tween:MoveAndScaleTo -- Tween to move entity and change scale simultaneously
Tween:TransformTo -- Tween to change entity position, rotation, and scale simultaneously
Tween:ColorTo -- Tween to change entity color to specified color
Tween:Lerp -- Tween to move linearly interpolated between two entities
Util:Call -- Dynamically call component method and return result
Util:RunCoroutine -- Execute component method as coroutine and return coroutine object
Util:WaitCoroutines -- Wait until multiple coroutines are all completed
Util:HasAttribute -- Check if component method has specified attribute
Util:GetAttribute -- Get and return component method attribute
Util:GetRandomIntegersRange -- Generate random integer array from specified range (with duplicates possible)
Util:GetRandomPermutationRange -- Generate random integer array from specified range (without duplicates)
Util:Restart -- Restart sprite renderer to initialize animation
Util:HandleCoroutine -- Handle coroutine event to execute method and store result
Vector2:Lerp -- Linearly interpolate between two vectors and return new vector

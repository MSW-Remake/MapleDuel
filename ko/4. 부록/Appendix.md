UIMyInfo:OnBeginPlay -- UI 초기화 및 플레이어 정보 설정
UIMyInfo:OnUpdate -- 플레이어 HP 바와 텍스트를 실시간으로 업데이트
UIPopup:Open -- 팝업 창을 열고 메시지와 콜백 함수를 설정
UIPopup:OnClickOk -- 확인 버튼 클릭 시 콜백 실행 후 팝업 닫기
UIPopup:OnClickCancel -- 취소 버튼 클릭 시 콜백 실행 후 팝업 닫기
UIPopup:Close -- 이벤트 연결 해제 후 팝업 닫기 애니메이션 시작
UIPopup:StartTween -- 팝업 열기/닫기 애니메이션 실행
UIToast:ShowMessage -- 토스트 메시지를 화면에 표시
UIToast:HideMessage -- 토스트 메시지를 즉시 숨김
UIToast:StartTween -- 토스트 메시지 표시/숨김 애니메이션 실행
AvatarRenderer:OnBeginPlay -- 아바타 렌더러 초기화 및 감정/동작 설정
AvatarRenderer:HandleScreenTouchEditorEvent -- 에디터 화면 터치 이벤트 처리 시 아바타 상태 재설정
Bot:OnBeginPlay -- 게임 시작 시 봇 AI 초기화 및 듀얼 시스템의 각종 매니저 연결 설정
Bot:SelectBehavior -- 봇 AI가 현재 상황에서 가능한 모든 행동을 분석하고 점수를 매겨 최적의 행동 선택
Bot:SetDifficulty -- 봇의 게임 난이도를 설정하여 AI 행동 패턴과 랭크 포인트를 조정
Bot:Play -- 봇이 선택한 카드를 대상이나 위치에 맞춰 실제로 플레이하는 동작 실행
Bot:DeclareEndRound -- 봇이 더 이상 플레이할 카드가 없을 때 라운드 종료를 선언
Bot:ChatOnce -- 봇이 지정된 시간 동안 한 번만 채팅 말풍선에 메시지를 표시
Bot:ChatRepeat -- 봇이 지정된 주기로 반복해서 채팅 말풍선에 메시지를 표시하고 숨김
Bot:StopChat -- 봇의 채팅 말풍선 표시를 완전히 중지하고 메시지를 지움
Bot:Run -- 봇 AI 메인 루프 실행 - 3초마다 현재 상황을 분석하여 최적의 행동을 선택하고 실행
Character:OnMapEnter -- 캐릭터가 맵에 진입할 때 매칭 시스템 초기화 및 유저 상태 설정
Character:OnBeginPlay -- 게임 시작 시 캐릭터 컴포넌트 초기화 및 서버/클라이언트별 데이터 로드 처리
Character:GetProperties -- 네트워크 동기화를 위한 캐릭터 핵심 속성들을 테이블로 반환
Character:SetProperties -- 네트워크에서 받은 속성 테이블로 캐릭터의 속성값들을 일괄 설정
Character:SetPropertiesInClient -- 클라이언트 측에서만 실행되는 캐릭터 속성 설정 메서드
Character:SyncProperties -- 서버에서 지정된 유저에게 캐릭터 속성 정보를 동기화 전송
Character:OnSyncProperties -- 속성 동기화 완료 후 클라이언트에서 네임태그 등 UI 요소 업데이트
Character:Sync -- 서버에서 클라이언트로 캐릭터의 모든 속성과 상태를 완전 동기화
Character:Clear -- 캐릭터의 모든 게임 데이터를 초기 상태로 완전 초기화
Character:LoadServerAttribute -- 서버에서 데이터 로드 작업을 수행할 권한이 있는지 확인하는 속성 메서드
Character:Load -- 데이터베이스에서 캐릭터의 모든 게임 정보를 로드하고 게임 상태를 초기화
Character:SetLoadedInOwner -- 클라이언트에서 캐릭터 데이터 로드 완료 상태를 설정하여 UI 업데이트 허용
Character:RankedMatchReady -- 랭크 매치에서 유저가 준비 완료 되었을 때 듀얼 시작 처리
Character:SpawnClassTag -- 클라이언트에서 캐릭터 위에 표시될 클래스 태그 엔티티 생성
Character:SetTemp -- 임시 데이터 설정 및 기간 제한 이벤트 카드팩 개수 및 출석 처리
Character:SetTempInOwner -- 클라이언트에서 임시 데이터 설정 및 이벤트 UI 업데이트
Character:GetOpenEventCardPackCount -- 현재 날짜 기준으로 이벤트 카드팩을 무료로 오픈할 수 있는 횟수 반환
Character:DecreaseOpenEventCardPackCount -- 이벤트 카드팩 오픈 시 남은 무료 오픈 횟수를 1개 차감
Character:DecreaseOpenEventCardPackCountInOwner -- 클라이언트에서 이벤트 카드팩 오픈 횟수 업데이트 및 UI 반영
Character:SetMeso -- 서버에서 캐릭터의 메소 금액을 지정된 값으로 설정
Character:SetMesoInOwner -- 클라이언트에서 메소 금액 설정 및 UI에 반영
Character:AddMeso -- 서버에서 메소 금액 증감 처리 및 클라이언트 동기화
Character:AddMesoInServer -- 서버에서만 메소 금액 증감 계산을 수행하여 값 업데이트
Character:AddMesoInOwner -- 클라이언트에서 메소 금액 증감을 UI에 즉시 반영
Character:GetDailyRankedWinMeso -- 오늘 날짜 기준으로 랭크 매치 승리 시 받을 수 있는 메소 보상 조회
Character:SetDailyRankedWinMeso -- 오늘 날짜 기준으로 랭크 매치 승리 메소 보상 금액 설정
Character:AddDailyRankedWinMeso -- 오늘 날짜 기준으로 랭크 매치 승리 시 받는 메소 보상 금액 증가
Character:GetDailyPlayMeso -- 오늘 날짜 기준으로 게임 플레이 시 받을 수 있는 메소 보상 조회
Character:SetDailyPlayMeso -- 오늘 날짜 기준으로 게임 플레이 메소 보상 금액 설정
Character:AddDailyPlayMeso -- 오늘 날짜 기준으로 게임 플레이 메소 보상 금액 증가
Character:GetDailyRankedPlayCount -- 일일 랭크 플레이 횟수 조회
Character:SetDailyRankedPlayCount -- 일일 랭크 플레이 횟수 설정
Character:IncreaseDailyRankedPlayCount -- 일일 랭크 플레이 횟수 증가
Character:GetCardCount -- 특정 카드의 보유 수량 조회
Character:SetCards -- 카드 컬렉션 데이터 설정
Character:SetCardsInOwner -- 클라이언트에서 카드 컬렉션 데이터 설정
Character:GainCards -- 카드들을 획득하고 컬렉션에 추가
Character:LoseCards -- 카드들을 잃고 컬렉션에서 제거
Character:BuySingleCardPackServerAttribute -- 서버 속성 메서드 - 카드팩 구매 권한 확인용
Character:BuySingleCardPack -- 단일 카드팩 구매 처리
Character:BuySingleCardPackInOwner -- 클라이언트에서 단일 카드팩 구매 결과 처리
Character:BuySingleCardPackByOpenEventServerAttribute -- 서버 속성 메서드 - 이벤트 카드팩 구매 권한 확인용
Character:BuySingleCardPackByOpenEvent -- 이벤트 기간 중 무료 카드팩 구매 처리
Character:BuySingleCardPackByOpenEventInOwner -- 클라이언트에서 이벤트 카드팩 구매 결과 처리
Character:BuyMultipleCardPacksServerAttribute -- 서버 속성 메서드 - 다중 카드팩 구매 권한 확인용
Character:BuyMultipleCardPacks -- 다중 카드팩 구매 처리 (5팩 세트)
Character:HasCardBack -- 특정 카드 뒷면을 보유하고 있는지 확인
Character:SetCardBack -- 사용할 카드 뒷면 설정
Character:SetDecks -- 덱 배열 설정 및 보유 카드 수량 검증
Character:CreateDeck -- 새로운 덱 생성
Character:FinishDeck -- 덱 편집 완료 및 저장
Character:SaveDeck -- 덱 임시 저장
Character:DeleteDeck -- 현재 선택된 덱 삭제
Character:SetDeckIndex -- 사용할 덱 인덱스 설정
Character:SetRank -- 랭크 포인트와 순위 설정
Character:BuyCard -- 개별 카드 구매 처리
Character:SellCard -- 카드 판매 처리
Character:IsUser -- 실제 유저인지 봇인지 확인
Character:IsOwner -- 로컬 플레이어 본인인지 확인
Character:IsAlly -- 아군인지 확인 (친구 관계 포함)
Character:IsAbleToMatch -- 매칭 가능한 상태인지 확인
Character:GetDeck -- 현재 사용 중인 덱 정보 반환 (튜토리얼 모드 고려)
Character:SetNameTag -- 랭크에 따른 네임태그 설정
Character:OpenCardPack -- 카드팩 개봉 처리
Character:SendFriendRequest -- 친구 요청 전송
Character:PlayEmote -- 감정 표현 재생
Character:PlayEmoteInClient -- 클라이언트에서 감정 표현 애니메이션 재생
Character:SpawnEmoteEffect -- 감정 표현 이펙트 엔티티 생성
Character:IncreaseSpecialEventAttendanceCount -- 서버에서 특별 이벤트 출석 횟수를 하루에 한 번씩 증가시키는 처리
Character:IncreaseSpecialEventAttendanceCountInOwner -- 클라이언트에서 특별 이벤트 출석 횟수 정보를 업데이트
Character:OnUpdate -- 매 프레임 업데이트 - 일일 출석 체크
Character:ReceiveCardPacksBySpecialEventServerAttribute -- 서버에서 특별 이벤트 카드팩 보상을 수령할 권한이 있는지 확인하는 속성 메서드
Character:ReceiveCardPacksBySpecialEvent -- 서버에서 특별 이벤트의 일차별 카드팩 보상을 지급하는 처리
Character:ReceiveCardPacksBySpecialEventInOwner -- 클라이언트에서 특별 이벤트 카드팩 보상 수령 결과 처리 및 UI 표시
Character:ShowEvent -- 클라이언트에서 특별 이벤트 UI 창을 열어 보상 정보를 표시
Character:HandleTouchEvent -- 캐릭터를 터치했을 때 본인이면 감정표현 UI, 타인이면 상호작용 UI를 열어주는 이벤트 처리
Character:HandleUserLeaveEvent -- 유저가 게임을 떠날 때 모든 게임 데이터를 데이터베이스에 저장하고 게임 상태를 정리하는 이벤트 처리
Home:OnBeginPlay -- 홈 맵 초기화 및 카메라 설정
Home:GetProperties -- 홈 맵의 동기화할 속성들을 테이블로 반환
Home:OnSyncProperties -- 클라이언트에서 속성 동기화 시 UI 모듈들 생성
Home:UpdateChannels -- 서버 채널 정보 업데이트 및 관리
Home:EnterChannelServerAttribute -- 서버 속성 메서드 - 채널 입장 권한 확인용
Home:EnterChannel -- 플레이어를 특정 채널로 이동
Home:GetChannelsServerAttribute -- 서버 속성 메서드 - 채널 목록 조회 권한 확인용
Home:GetChannels -- 현재 활성화된 채널 목록을 조회하여 클라이언트에 전송
Home:GetChannelsInOwner -- 클라이언트에서 채널 목록 이벤트 발송
Home:GetRooms -- 지정된 모드의 방 목록을 조회하여 반환
Home:GetNewRoomId -- 지정된 모드에서 사용 가능한 새로운 방 ID를 생성
Home:CreateFriendlyMatchRoomServerAttribute -- 서버 속성 메서드 - 친선전 방 생성 권한 확인용
Home:CreateFriendlyMatchRoom -- 친선전 방을 생성하고 플레이어를 이동
Home:EnterFriendlyMatchRoomServerAttribute -- 서버 속성 메서드 - 친선전 방 입장 권한 확인용
Home:EnterFriendlyMatchRoom -- 플레이어를 기존 친선전 방에 입장시킴
Home:BeginPracticeServerAttribute -- 서버 속성 메서드 - 연습 모드 시작 권한 확인용
Home:BeginPractice -- 플레이어의 랭크에 따른 난이도로 연습 모드 시작
Home:BeginTutorialServerAttribute -- 서버 속성 메서드 - 튜토리얼 시작 권한 확인용
Home:BeginTutorial -- 플레이어를 위한 튜토리얼 방 생성 및 이동
Home:GetFriendlyMatchRoomsServerAttribute -- 서버 속성 메서드 - 친선전 방 목록 조회 권한 확인용
Home:GetFriendlyMatchRooms -- 현재 활성화된 친선전 방 목록을 조회하여 클라이언트에 전송
Home:GetFriendlyMatchRoomsInSender -- 클라이언트에서 친선전 방 목록 이벤트 발송
Home:BeginMatchingServerAttribute -- 서버 속성 메서드 - 랭크 매칭 시작 권한 확인용
Home:BeginMatching -- 랭크 매칭 시작
Home:BeginMatchingInSender -- 클라이언트에서 매칭 시작 UI 상태 변경
Home:CancelMatchingServerAttribute -- 서버 속성 메서드 - 매칭 취소 권한 확인용
Home:CancelMatching -- 진행 중인 랭크 매칭을 취소
Home:CancelMatchingInSender -- 클라이언트에서 매칭 취소 UI 상태 변경
Home:Initialize -- 홈 맵 모드별 초기화 (로비 또는 랭크매치)
Home:UpdateMatchResult -- 매치 결과를 업데이트하고 랭크 포인트 계산
Home:ReturnToLobbyServerAttribute -- 서버 속성 메서드 - 로비 복귀 권한 확인용
Home:ReturnToLobby -- 플레이어를 로비로 복귀시킴
Input:OnBeginPlay -- 입력 시스템 초기화 및 트리거 이벤트 연결
Input:SetState -- 입력 상태 전환 및 UI/게임 로직 처리
Input:HideScope -- 타겟팅 스코프 숨기기
Input:PlaceScope -- 타겟팅 스코프와 라인 위치 설정
Input:SetTarget -- 타겟팅 대상 설정 및 스코프 비주얼 업데이트
Input:HandleScreenTouchHoldEvent -- 화면 터치 홀드 이벤트 처리 - 카드 드래그 등
Input:HandleScreenTouchReleaseEvent -- 화면 터치 릴리즈 이벤트 처리 - 카드 플레이 등
Integer:SetInteger -- 정수 값을 설정하고 숫자 스프라이트로 표시
Integer:SetPositiveInteger -- 양수 값을 설정하고 + 기호와 함께 표시
Integer:Clear -- 모든 숫자 스프라이트를 제거하고 초기화
Integer:SetColor -- 모든 숫자 스프라이트의 색상을 변경
Integer:SetAlpha -- 모든 숫자 스프라이트의 투명도를 변경
Integer:GetDigits -- 정수를 개별 자릿수로 분리하여 배열로 반환
Integer:PlaceDigits -- 숫자 스프라이트들을 화면에 배치하고 표시
Layout:OnBeginPlay -- 자식 엔티티들의 Transform 컴포넌트를 테이블에 저장
Layout:GetTransform -- 이름으로 Transform 컴포넌트를 검색하여 반환
MainCamera:OnBeginPlay -- 메인 카메라 설정 및 화면 비율에 맞는 줌 적용
Map:GetProperties -- 맵의 속성들을 테이블로 반환
Map:SetProperties -- 속성 테이블을 받아서 맵의 속성들을 설정
Map:SetPropertiesInClient -- 클라이언트에서 속성들을 설정
Map:SyncProperties -- 서버에서 특정 사용자에게 속성들을 동기화
Map:OnSyncProperties -- 속성 동기화 완료 후 맵 장식 적용
Map:Sync -- 서버에서 클라이언트로 맵 정보 동기화
Map:Decorate -- 테마에 따른 맵 장식 및 배경음악 설정
Map:GetFriendsServerAttribute -- 친구 목록 조회를 위한 서버 속성 메서드
Map:GetFriends -- 친구 목록 정보 조회 및 반환
Map:GetFriendsInSender -- 클라이언트에서 친구 정보를 업데이트하고 이벤트 발송
Map:FollowServerAttribute -- 친구 따라가기 기능을 위한 서버 속성 메서드
Map:Follow -- 친구 따라가기 기능 처리
Notice:ShowText -- 공지사항 텍스트를 화면에 표시하고 효과음 재생
Npc:OnBeginPlay -- NPC 초기화 및 랜덤 대화 메시지 반복 표시
Room:GetProperties -- 룸의 속성을 테이블로 반환
Room:OnSyncProperties -- 클라이언트에서 속성 동기화 시 UI 모듈들 생성
Room:ReturnToLobbyServerAttribute -- 서버 속성 메서드 - 로비 복귀 권한 확인용
Room:ReturnToLobby -- 플레이어를 로비로 이동시키거나 정적 룸으로 이동
Room:Initialize -- 룸 초기화 - 모드에 따라 봇 생성 및 설정
Room:HandleSetRoom -- 룸 설정 이벤트 처리
SpriteRenderer:HandleAnimationClipEvent -- 애니메이션 클립 변경 시 스프라이트 업데이트
TurnSign:OnBeginPlay -- 턴 사인 초기화 및 터치 이벤트 연결
TurnSign:SetState -- 턴 사인 상태 변경 및 시각적 업데이트
TurnSign:SetStateByTurnPlayer -- 턴 플레이어에 따라 턴 사인 상태를 자동으로 설정
TurnSign:RotateSign -- 턴 사인을 지정된 각도로 회전시키는 애니메이션
TurnSign:SetText -- 턴 사인의 텍스트를 설정하고 애니메이션 효과 적용
TurnSign:SetColor -- 턴 사인의 색상을 변경
TurnSign:BeginCountdown -- 턴 제한 시간 카운트다운 시작
TurnSign:EndCountdown -- 카운트다운 종료 및 타임아웃 처리
TurnSign:PlaceRope -- 카운트다운 로프의 위치와 크기를 업데이트
Tutorial:GetProperties -- 네트워크 동기화를 위한 튜토리얼 핵심 속성들을 테이블로 반환
Tutorial:SetProperties -- 네트워크에서 받은 속성 테이블로 튜토리얼의 상태를 일괄 설정
Tutorial:SetPropertiesInClient -- 클라이언트 측에서만 실행되는 튜토리얼 속성 설정 메서드
Tutorial:SyncProperties -- 서버에서 특정 사용자에게 속성들을 동기화
Tutorial:OnSyncProperties -- 속성 동기화 완료 후 튜토리얼 진행 요청
Tutorial:Sync -- 서버에서 클라이언트로 튜토리얼 정보 동기화
Tutorial:SetArrow -- 튜토리얼 화살표 위치 설정
Tutorial:ClearArrow -- 튜토리얼 화살표 숨기기
Tutorial:SetClick -- 튜토리얼 클릭 표시 위치 설정
Tutorial:ClearClick -- 튜토리얼 클릭 표시 숨기기
Tutorial:SetDrag -- 튜토리얼 드래그 애니메이션 설정
Tutorial:ClearDrag -- 튜토리얼 드래그 애니메이션 정리 및 숨기기
Tutorial:ProgressServerAttribute -- 튜토리얼 진행을 위한 서버 속성 메서드
Tutorial:Progress -- 튜토리얼 진행 상태 업데이트
Tutorial:ProgressInClient -- 클라이언트에서 튜토리얼 단계별 UI 처리
CardFront:OnBeginPlay -- 카드 앞면 초기화 시 표시 기호를 숨김
MinionBody:OnBeginPlay -- 미니언 몸체 초기화 및 상태 이펙트 엔티티 생성
Thumbnail:OnBeginPlay -- 썸네일 초기화 및 터치 이벤트 연결
Thumbnail:SetInfo -- 썸네일에 카드 정보를 설정하고 비주얼 업데이트
Thumbnail:ClearInfo -- 썸네일 정보를 모두 초기화
Thumbnail:DestroyTweener -- 트위너 애니메이션 객체 파괴
Thumbnail:DestroyAnchorTweener -- 앵커 트위너 애니메이션 객체 파괴
Thumbnail:SetAnchorTransform -- 앵커 위치를 즉시 설정
Thumbnail:TransformAnchorTo -- 앵커를 지정된 위치로 애니메이션 이동
Thumbnail:TransformToAnchor -- 썸네일을 앵커 위치로 애니메이션 이동
Thumbnail:AttachToAnchor -- 썸네일을 앵커 엔티티에 부착
Thumbnail:IsInTouchArea -- 지정된 포인트가 터치 영역 내에 있는지 확인
Thumbnail:GetBlueprint -- 현재 썸네일의 블루프린트 정보 반환
Thumbnail:GetBlueprintByName -- 지정된 이름으로 블루프린트 생성
Thumbnail:SetDisplayTimer -- 지정된 시간 후 표시 불가능 상태로 설정하는 타이머
Thumbnail:ClearDisplayTimer -- 표시 타이머 해제
Thumbnail:PlaceFront -- 썸네일을 앞쪽 레이어로 배치
Thumbnail:PlaceBack -- 썸네일을 뒤쪽 레이어로 배치
UnitBody:OnBeginPlay -- 유닛 몸체 초기화 시 표시 기호를 숨김
ActionManager:OnBeginPlay -- 액션 매니저 초기화 시 각 액션별 처리 지연 시간과 핵심 지연 시간 테이블 설정
ActionManager:GetProcessDelay -- 액션 이름에 따른 처리 지연 시간 반환
ActionManager:GetCoreDelay -- 액션 이름에 따른 핵심 지연 시간 반환
ActionManager:PlayPreProcessAction -- 액션 전처리 단계 실행
ActionManager:PlayPostProcessAction -- 액션 후처리 단계 실행
ActionManager:PlayPreCoreAction -- 액션 핵심 전처리 단계 실행
ActionManager:PlayPostCoreAction -- 액션 핵심 후처리 단계 실행
ActionManager:GetSummonActionName -- 소환 액션 이름을 생성하고 해당 메서드 존재 여부에 따라 기본값 반환
ActionManager:PlaySummonAction -- 미니언 소환 액션을 실행
ActionManager:SummonCoroutine -- 미니언 소환 액션을 코루틴으로 실행하여 제어 가능한 태스크 반환
ActionManager:Summon -- 기본 소환 애니메이션과 사운드 효과 재생
ActionManager:PreProcessAirStrike -- 에어 스트라이크 스킬 전처리 (플레이어 애니메이션 및 이펙트)
ActionManager:PostProcessAirStrike -- 에어 스트라이크 스킬 후처리 대기
ActionManager:PreCoreAirStrike -- 에어 스트라이크 피해 적용 전 히트 이펙트 재생
ActionManager:PostProcessArmorCrash -- 아머 크래시 스킬 후처리 대기
ActionManager:PreCoreArmorCrash -- 아머 크래시 피해 적용 전 히트 이펙트 재생
ActionManager:PreCoreArrowBlow -- 애로우 블로우 스킬 실행 (플레이어 애니메이션과 투사체 발사)
ActionManager:PreProcessArrowBomb -- 애로우 밤 스킬 전처리 (플레이어 애니메이션과 투사체 발사)
ActionManager:PostProcessBlackbull -- 블랙불 스킬 후처리 대기
ActionManager:PreProcessBlackKitty -- 블랙키티 스킬 전처리 (애니메이션과 사운드)
BotManager:GetData -- 봇 이름에 해당하는 봇 데이터 반환
BotManager:PracticeWarriorBot -- 연습용 전사 봇 데이터 반환
BotManager:PracticeMagicianBot -- 연습용 마법사 봇 데이터 반환
BotManager:PracticeBowmanBot -- 연습용 궁수 봇 데이터 반환
BotManager:PracticeThiefBot -- 연습용 도적 봇 데이터 반환
BotManager:PracticePirateBot -- 연습용 해적 봇 데이터 반환
BotManager:TutorialBot -- 튜토리얼용 봇 데이터 반환
CardBackManager:OnBeginPlay -- 카드 뒷면 매니저 초기화 및 데이터 로드
CardBackManager:GetStarterCardBacks -- 기본 제공되는 카드 뒷면 목록 반환
CardBackManager:GetCardBacks -- 사용 가능한 모든 카드 뒷면 배열 반환
CardPackManager:OnBeginPlay -- 카드팩 매니저 초기화 시 데이터셋 로드 및 테마별 카드팩 분류
CardPackManager:GetTheme -- 카드팩의 테마를 반환
CardPackManager:GetQuality -- 카드팩의 품질을 반환
CardPackManager:GetRarity -- 카드팩의 희귀도를 반환
CardPackManager:GetCurrency -- 카드팩의 구매 화폐 종류를 반환
CardPackManager:GetSingleMesoPrice -- 카드팩의 단일 메소 가격을 반환
CardPackManager:GetMultipleMesoPrice -- 카드팩의 다중 메소 가격을 반환
CardPackManager:GetSingleWorldCoinPrice -- 카드팩의 단일 월드코인 가격을 반환
CardPackManager:GetMultipleWorldCoinPrice -- 카드팩의 다중 월드코인 가격을 반환
CardPackManager:GetCardPackNames -- 특정 테마의 카드팩 이름 목록을 반환
CardPackManager:GetSinglePrice -- 카드팩의 단일 구매 가격을 화폐 종류에 따라 반환
CardPackManager:GetMultiplePrice -- 카드팩의 다중 구매 가격을 화폐 종류에 따라 반환
CardPackManager:GetInfos -- 카드팩을 열었을 때 나올 5장의 카드 정보를 희귀도에 따라 랜덤 생성
CardPackManager:OpenCardPack -- 클라이언트에서 카드팩 개봉 애니메이션과 카드 썸네일 표시 처리
CardPackManager:AcquireThumbnail -- 썸네일 객체를 풀에서 가져오거나 새로 생성하여 반환
CardPackManager:ReleaseThumbnail -- 사용한 썸네일 객체를 풀로 반환하여 재사용 가능하게 함
CardPackManager:AcquireCardPack -- 카드팩 엔티티를 풀에서 가져오거나 새로 생성하여 반환
CardPackManager:ReleaseCardPack -- 사용한 카드팩 엔티티를 풀로 반환하여 재사용 가능하게 함
CommandManager:OnBeginPlay -- 클라이언트에서 명령어 큐를 초기화하고 지속적으로 명령어를 처리하는 루프 시작
CommandManager:IsCommander -- 현재 플레이어가 명령을 내린 지휘관인지 확인
CommandManager:RunCommand -- 클라이언트/서버에서 명령어를 실행하기 위한 진입점
CommandManager:VerifyCommand -- 서버에서 명령어의 유효성을 검증 (ID 일치 및 개별 검증 함수 호출)
CommandManager:OnVerifyCommandFailed -- 명령어 검증 실패 시 클라이언트에서 입력 상태를 초기화하고 오류 메시지 표시
CommandManager:RunCommandInServerServerAttribute -- 서버 속성 메소드 (빈 구현체)
CommandManager:RunCommandInServer -- 서버에서 명령어를 검증하고 실행한 후 모든 클라이언트에게 결과를 전송
CommandManager:PreRunCommand -- 클라이언트에서 명령어 실행 전 처리 (입력 상태 설정 및 전처리 함수 호출)
CommandManager:PostRunCommand -- 클라이언트에서 명령어 실행 후 처리 함수 호출
CommandManager:PushCommandInClient -- 클라이언트 명령어 큐에 새로운 명령어를 추가
CommandManager:RunCommandInClient -- 클라이언트에서 큐에서 꺼낸 명령어를 실제로 실행
CommandManager:RunCommandLogic -- 명령어의 실제 로직을 실행하고 게임 종료 조건을 확인
CommandManager:PushPackage -- 서버에서 모든 클라이언트에게 공유할 패키지를 추가
CommandManager:PushPrivatePackage -- 특정 플레이어와 동맹에게만 보이는 비공개 패키지와 다른 플레이어에게 보이는 공개 패키지를 추가
CommandManager:PopPackage -- 클라이언트에서 패키지 배열에서 다음 패키지를 가져옴
CommandManager:ShareSpawnedEntity -- 서버에서 엔티티를 생성하고 클라이언트와 동기화
CommandManager:Destroy -- 엔티티를 파괴 대기 목록에 추가 (명령어 처리 완료 후 일괄 파괴)
CommandManager:IsAllyWith -- 클라이언트에서 특정 플레이어와 동맹 관계인지 확인
CommandManager:ShareRandomBoolean -- 서버에서 랜덤 불린 값을 생성하고 모든 클라이언트와 동기화
CommandManager:ShareRandomNumber -- 서버에서 랜덤 숫자를 생성하고 모든 클라이언트와 동기화
CommandManager:SharePrivateRandomNumber -- 특정 플레이어와 동맹에게만 실제 랜덤 값을, 다른 플레이어에게는 기본값을 제공
CommandManager:ShareRandomIntegerRange -- 서버에서 범위 내 랜덤 정수를 생성하고 모든 클라이언트와 동기화
CommandManager:SharePrivateRandomIntegerRange -- 특정 플레이어와 동맹에게만 실제 랜덤 정수를, 다른 플레이어에게는 기본값을 제공
CommandManager:ShareRandomIntegersRange -- 서버에서 범위 내 랜덤 정수 배열을 생성하고 모든 클라이언트와 동기화
CommandManager:SharePrivateRandomIntegersRange -- 특정 플레이어와 동맹에게만 실제 랜덤 정수 배열을, 다른 플레이어에게는 기본값 배열을 제공
CommandManager:ShareRandomPermutationRange -- 서버에서 범위 내 랜덤 순열 배열을 생성하고 모든 클라이언트와 동기화
CommandManager:SharePrivateRandomPermutationRange -- 특정 플레이어와 동맹에게만 실제 랜덤 순열 배열을, 다른 플레이어에게는 기본값 배열을 제공
CommandManager:ShareRandomElementInArray -- 서버에서 배열에서 랜덤 요소를 선택하고 모든 클라이언트와 동기화
CommandManager:SharePrivateRandomElementInArray -- 특정 플레이어와 동맹에게만 실제 랜덤 요소를, 다른 플레이어에게는 기본값을 제공
CommandManager:ShareRandomElementsInArray -- 서버에서 배열에서 여러 랜덤 요소를 선택하고 모든 클라이언트와 동기화
CommandManager:SharePrivateRandomElementsInArray -- 특정 플레이어와 동맹에게만 실제 랜덤 요소 배열을, 다른 플레이어에게는 기본값 배열을 제공
CommandManager:ShareRandomElementInArrays -- 서버에서 여러 배열에서 가중치를 고려하여 랜덤 요소를 선택하고 모든 클라이언트와 동기화
CommandManager:SharePrivateRandomElementInArrays -- 특정 플레이어와 동맹에게만 실제 랜덤 요소를, 다른 플레이어에게는 기본값을 제공 (여러 배열 가중치 고려)
CommandManager:ShareRandomElementsInArrays -- 서버에서 여러 배열에서 가중치를 고려하여 여러 랜덤 요소를 선택하고 모든 클라이언트와 동기화
CommandManager:SharePrivateRandomElementsInArrays -- 특정 플레이어와 동맹에게만 실제 랜덤 요소 배열을, 다른 플레이어에게는 기본값 배열을 제공 (여러 배열 가중치 고려)
CommandManager:ShareRandomPermutationInArray -- 서버에서 배열에서 랜덤 순열 배열을 생성하고 모든 클라이언트와 동기화
CommandManager:SharePrivateRandomPermutationInArray -- 특정 플레이어와 동맹에게만 실제 랜덤 순열 배열을, 다른 플레이어에게는 기본값 배열을 제공
CommandManager:ShareCardBack -- 서버에서 캐릭터의 카드 뒷면 정보를 가져와 모든 클라이언트와 동기화
CommandManager:ShareClass -- 서버에서 캐릭터의 클래스 정보를 가져와 모든 클라이언트와 동기화
CommandManager:SharePrivateBlueprints -- 특정 플레이어의 덕 카드 블루프린트를 동맹에게만 공유하고 다른 플레이어에게는 빈 배열 제공
CommandManager:SetInputStates -- 서버에서 모든 플레이어의 입력 상태를 업데이트하고 클라이언트에 전송
CommandManager:InputGate -- 서버에서는 게이트 카운트를 증가시키고, 클라이언트에서는 감소시켜 입력 상태 동기화 제어
CommandManager:SetInputStatesInClient -- 클라이언트에서 서버로부터 받은 입력 상태 정보를 저장하고 적용 준비
CommandManager:ApplyInputStates -- 저장된 입력 상태를 모든 객체에 실제로 적용하고 플레이 가능 사인 표시
CommandManager:ClearInputStates -- 모든 객체의 입력 상태를 초기화하고 사인 상태도 리셋
CommandManager:SetPlayableSigns -- 모든 사인을 지우고 플레이 가능한 객체들에만 플레이 가능 사인 표시
CommandManager:SetTargetableSigns -- 모든 사인을 지우고 카드를 사용 중으로, 타겟 가능한 객체들에 타겟 가능 사인 표시
CommandManager:SetCastingSigns -- 모든 사인을 지우고 카드에만 사용 중 사인 표시
CommandManager:SetPlacingSigns -- 모든 사인을 지우고 배치 중인 미니언에만 배치 중 사인 표시
CommandManager:ClearSigns -- 모든 사인 가능한 객체들의 사인 상태를 지움
CommandManager:VerifyBeginDuel -- 결투 시작 명령의 유효성 검증 (이미 결투 중이 아닌지 확인)
CommandManager:BeginDuel -- 결투를 시작하고 튜토리얼 진행 상태 업데이트
CommandManager:VerifyEndDuel -- 결투 종료 명령의 유효성 검증 (결투 중이고 승리자가 올바른지 확인)
CommandManager:EndDuel -- 결투를 종료하고 승리자를 처리
CommandManager:PreEndDuel -- 결투 종료 전 클라이언트 UI 정리
CommandManager:VerifyDeclareEndRound -- 라운드 종료 선언 명령의 유효성 검증 (플레이어 턴인지, 튜토리얼 상태 등 확인)
CommandManager:PreDeclareEndRound -- 라운드 종료 선언 전 클라이언트 UI 업데이트 (종료 사인 표시, 손패 변환, 턴 사인 업데이트)
CommandManager:DeclareEndRound -- 라운드 종료를 선언하고 튜토리얼 진행 상태 업데이트
CommandManager:VerifyPlay -- 카드 플레이 명령의 유효성 검증 (카드 유효성, 비용, 타겟, 필드 공간, 플레이어 턴 등 확인)
CommandManager:OnVerifyPlayFailed -- 카드 플레이 검증 실패 시 클라이언트 정리 작업 (미니언 배치 취소)
CommandManager:PrePlay -- 카드 플레이 전 클라이언트 준비 작업 (손패에서 제거, 미니언 배치 준비 등)
CommandManager:PostPlay -- 카드 플레이 후 클라이언트 UI 업데이트 (턴 사인 업데이트)
CommandManager:Play -- 카드를 플레이하고 튜토리얼 진행 상태 업데이트
CommandManager:SetWatching -- 서버에서 관전자가 특정 플레이어의 손패를 볼 수 있도록 데이터 준비
CommandManager:SetWatchingInClient -- 클라이언트에서 관전 데이터를 저장하고 명령어 실행 완료 후 적용 대기
CommandManager:SetWatchingCards -- 관전 데이터를 바탕으로 손패 카드들의 정보를 설정하고 메시지 표시
DeckManager:OnBeginPlay -- 덱 매니저 초기화 시 데이터셋과 형용사 배열을 설정
DeckManager:IsDeckValid -- 덱이 유효한지 검사 (클래스, 이름, 카드 수, 카드 제한 등)
DeckManager:IsDeckComplete -- 덱이 완성되었는지 검사 (유효하고 20장인지)
DeckManager:GetDeckSize -- 덱의 총 카드 수를 계산하여 반환
DeckManager:GetCardCountByName -- 덕에서 특정 이름의 카드 총 개수를 계산하여 반환
DeckManager:GetCardCountByInfo -- 덕에서 특정 카드 정보(이름, 변형, 품질)의 개수를 반환
DeckManager:GetText -- 데이터셋에서 지역화 텍스트를 가져옴 (한국어/영어 지원)
DeckManager:GetNewDeck -- 지정된 클래스와 언어로 빈 덕을 생성 (랜덤 형용사로 이름 생성)
DeckManager:GetWarriorStarterDeck -- 전사 클래스의 기본 스타터 덕을 반환
DeckManager:GetMagicianStarterDeck -- 마법사 클래스의 기본 스타터 덕을 반환
DeckManager:GetBowmanStarterDeck -- 궁수 클래스의 기본 스타터 덕을 반환
DeckManager:GetThiefStarterDeck -- 도적 클래스의 기본 스타터 덕을 반환
DeckManager:GetPirateStarterDeck -- 해적 클래스의 기본 스타터 덕을 반환
DeckManager:GetTutorialBotDeck_1 -- 튜토리얼 1단계에서 사용할 봇 덕을 반환 (사전 정의된 카드 순서 포함)
DeckManager:GetTutorialPlayerDeck_1 -- 튜토리얼 1단계에서 사용할 플레이어 덕을 반환 (사전 정의된 카드 순서 포함)
DeckManager:GetTutorialBotDeck_2 -- 튜토리얼 2단계에서 사용할 봇 덕을 반환 (사전 정의된 카드 순서 포함)
DeckManager:GetTutorialPlayerDeck_2 -- 튜토리얼 2단계에서 사용할 플레이어 덕을 반환 (사전 정의된 카드 순서 포함)
EmoteManager:OnBeginPlay -- 이모트 매니저 초기화 및 이모트 타입 테이블 설정
EmoteManager:GetEmotionalType -- 이모트 이름에 해당하는 감정 타입 반환
EnchantmentManager:ChunJi -- 춘지 인챈트먼트 제거 조건 확인 (라운드 종료 시)
EnchantmentManager:Focus -- 포커스 인챈트먼트 제거 조건 확인 (라운드 종료 시)
EnchantmentManager:Harp -- 하프 인챈트먼트 제거 조건 확인 (라운드 종료 시)
EnchantmentManager:Haste -- 헤이스트 인챈트먼트 제거 조건 확인 (라운드 종료 시)
EnchantmentManager:PowerStance -- 파워 스탠스 인챈트먼트 제거 조건 확인 (라운드 종료 시)
EnchantmentManager:Reindeer -- 순록 인챈트먼트 제거 조건 확인 (미니언 플레이 시)
EnchantmentManager:ShadowPartner -- 섀도우 파트너 인챈트먼트 제거 조건 확인 (라운드 종료 시)
EntryManager:OnBeginPlay -- 엔트리 매니저 초기화 시 게임 객체들과 카드들의 기본 정보를 설정
EntryManager:GetEntry -- 지정된 이름의 엔트리 정보를 반환
EntryManager:Duel -- 듀얼 객체의 기본 정보를 반환
EntryManager:Player -- 플레이어 객체의 기본 정보를 반환
EntryManager:Deck -- 덱 객체의 기본 정보를 반환
EntryManager:Hand -- 핸드 객체의 기본 정보를 반환
EntryManager:Field -- 필드 객체의 기본 정보를 반환
GalleryModule:OnBeginPlay -- 갤러리 모듈 초기화 시 키워드 배열 설정 및 이벤트 연결
GalleryModule:AcquireCard -- 카드 풀에서 카드를 획득하거나 새로 생성
GalleryModule:ReleaseCard -- 카드를 풀로 반환
GalleryModule:Open -- 갤러리 모듈을 열고 카드 또는 카드백 정보를 표시
GalleryModule:Close -- 갤러리 모듈을 닫고 모든 UI 요소를 초기화
RankManager:GetMajorRank -- 랭크 점수와 순위를 기반으로 주요 등급 반환 (Legend, Master, Platinum 등)
RankManager:GetMinorRank -- 랭크 점수를 기반으로 세부 등급 숫자 반환 (1-4)
RankManager:GetRankName -- 완전한 랭크 이름을 현지화된 텍스트로 반환
RankManager:GetRankPoint -- 현재 등급 내에서의 포인트를 문자열로 반환
RankManager:GetRankingInfosServerAttribute -- 랭킹 정보 조회 서버 속성 정의
RankManager:GetRankingInfos -- 서버에서 랭킹 데이터를 조회하여 상위 100명 정보 반환
RankManager:GetRankingInfosInSender -- 클라이언트에서 받은 랭킹 정보를 UI에 설정하고 표시
TargetManager:GetCardRequiresTarget -- 카드 이름에 해당하는 타겟팅 메소드가 존재하는지 확인
TargetManager:GetCardTargetables -- 서버에서 카드가 타겟할 수 있는 대상 목록을 계산하여 반환
TargetManager:ArrowBlow -- 애로우블로우 스킬의 타겟: 필드의 모든 미니언
TargetManager:ArrowBomb -- 애로우밤 스킬의 타겟: 필드의 모든 미니언
TargetManager:Assaulter -- 어썰터 스킬의 타겟: 필드의 모든 미니언
TargetManager:Brandish -- 브랜디시 스킬의 타겟: 모든 유닛 (플레이어 포함)
TargetManager:CorkscrewBlow -- 코크스크류블로우 스킬의 타겟: 필드의 모든 미니언
TargetManager:Disorder -- 디스오더 스킬의 타겟: 자신의 필드에 있는 미니언들
TargetManager:Doom -- 둠 스킬의 타겟: 필드의 모든 미니언
TargetManager:DoubleShot -- 더블샷 스킬의 타겟: 모든 유닛 (플레이어 포함)
TargetManager:DragonBlood -- 드래곤블러드 스킬의 타겟: 모든 유닛 (플레이어 포함)
TargetManager:Drain -- 드레인 스킬의 타겟: 모든 유닛 (플레이어 포함)
TargetManager:EnergyOrb -- 에너지오브 스킬의 타겟: 모든 유닛 (플레이어 포함)
TaskManager:OnBeginPlay -- 게임 시작 시 각종 셀렉터와 비교 함수들을 초기화
TaskManager:OnUpdate -- 서버에서 딜레이 시간을 업데이트하여 감소시킴
TaskManager:RunProcess -- 프로세스를 실행하고 관련 애니메이션과 딜레이를 처리
TaskManager:RunBatch -- 여러 객체에 대해 일괄적으로 작업을 수행하고 결과를 반환
TaskManager:RunCore -- 클라이언트에서 개별 객체의 핵심 작업을 실행하고 액션을 재생
TaskManager:AddDelay -- 서버에서 전체 딜레이 시간에 추가 딜레이를 더함
TaskManager:GetCoreDelay -- 특정 작업의 기본 딜레이 시간을 반환
TaskManager:GetBatchDelay -- 일괄 작업의 총 딜레이 시간을 계산하여 반환
TaskManager:BeginDuel -- 듀얼 시작 시 초기 설정과 첫 번째 라운드 시작을 처리
TaskManager:EndDuel -- 듀얼 종료 시 승자 처리와 후속 작업을 수행
TaskManager:DeclareEndRound -- 플레이어가 라운드 종료를 선언할 때의 처리 로직
TaskManager:BeginRound -- 새로운 라운드 시작 시 MP 지급과 카드 드로우를 처리
TaskManager:EndRound -- 라운드 종료 시 전투 단계와 얼음 해제를 처리
TaskManager:BeginTurn -- 플레이어의 턴 시작 시 초기 설정과 트리거 발동
TaskManager:EndTurn -- 플레이어의 턴 종료 시 후속 처리와 트리거 발동
TaskManager:BattlePhase -- 전투 단계에서 미니언들의 전투와 직접 공격을 처리
TaskManager:Battle -- 두 미니언 간의 전투를 실행하고 데미지를 처리
TaskManager:GainMp -- 플레이어들에게 MP를 지급하여 마나 자원을 증가시킴
TaskManager:LoseMp -- 플레이어들의 MP를 차감하여 마나 자원을 소모시킴
TaskManager:Play -- 카드를 플레이하여 미니언 소환 또는 스킬 사용을 처리
TaskManager:Place -- 카드들을 필드에 배치하여 미니언으로 소환
TaskManager:Cast -- 스킬 카드를 사용하여 대상에게 효과를 적용
TaskManager:Put -- 블루프린트를 이용해 새로운 카드를 덱에 추가
TaskManager:Add -- 블루프린트를 이용해 새로운 카드를 손에 추가
TaskManager:Draw -- 덱에서 카드를 드로우하여 손에 가져오거나 오버드로우 처리
TaskManager:Overdraw -- 손이 가득할 때 초과 드로우된 카드들을 처리
TaskManager:Fatigue -- 덱이 비었을 때 피로 데미지를 적용
TaskManager:Return -- 손에 있는 카드들을 덱으로 돌려보내기
TaskManager:Discard -- 손에 있는 카드들을 버리기 처리하고 기록 저장
TaskManager:InsertAddCostEnchantment -- 카드들에 비용 증가 인챈트먼트를 추가
TaskManager:InsertSetCostEnchantment -- 카드들에 비용 고정 인챈트먼트를 추가
TaskManager:Summon -- 블루프린트를 이용해 미니언을 필드에 소환
TaskManager:Dead -- 죽은 미니언들을 처리하고 필드에서 제거
TaskManager:Kick -- 미니언들을 필드에서 손으로 되돌려보내기
TaskManager:Vanish -- 미니언들을 필드에서 완전히 사라지게 처리
TaskManager:Transform -- 미니언들을 다른 미니언으로 변신시키기
TaskManager:DirectAttack -- 미니언이 상대 플레이어에게 직접 공격을 가하기
TaskManager:Kill -- 살아있는 유닛들을 즉시 죽이기
TaskManager:Damage -- 유닛들에게 데미지를 가하고 관련 효과들을 처리
TaskManager:Heal -- 유닛들의 체력을 회복시켜 생명력을 증가시키기
TaskManager:Freeze -- 미니언들에게 빙결 상태를 적용하여 움직임을 제한
TaskManager:Thaw -- 빙결된 미니언들의 얼음을 녹여 상태를 해제
TaskManager:Stun -- 미니언들에게 기절 상태를 적용하여 행동을 불가능하게 하기
TaskManager:Scare -- 미니언들에게 공포 상태를 적용하여 전투를 방해
TaskManager:Awake -- 기절된 미니언들을 깨워 상태를 해제하고 활성화
TaskManager:GainBarrier -- 미니언들에게 방어막 효과를 부여하여 보호 능력 강화
TaskManager:LoseBarrier -- 미니언들의 방어막을 제거하여 보호 효과 제거
TaskManager:InsertAddTriggerNameEnchantment -- 객체들에 트리거 추가 인챈트먼트를 적용하여 새로운 능력 부여
TaskManager:InsertAddAuraNameEnchantment -- 객체들에 아우라 추가 인챈트먼트를 적용하여 지속 효과 부여
TaskManager:InsertAddMaxHpEnchantment -- 객체들에 최대 체력 증가 인챈트먼트를 적용
TaskManager:InsertSetMaxHpEnchantment -- 객체들에 최대 체력 고정 인챈트먼트를 적용
TaskManager:InsertAddAtkEnchantment -- 객체들에 공격력 증가 인챈트먼트를 적용
TaskManager:InsertSetAtkEnchantment -- 객체들에 공격력 고정 인챈트먼트를 적용
TaskManager:InsertSetVenomEnchantment -- 객체들에 독 효과 인챈트먼트를 설정하여 특수 능력 부여
TaskManager:SortMinions -- 필드의 미니언들을 주어진 비교 함수로 정렬
TaskManager:MoveMinionToFarLeft -- 미니언을 필드의 가장 왼쪽 끝으로 이동
TaskManager:MoveMinionToFarRight -- 미니언을 필드의 가장 오른쪽 끝으로 이동
TaskManager:Cross -- 미니언을 상대방 필드로 이동시켜 소유권 변경
TaskManager:InsertSetRandomBattleEnchantment -- 듀얼에 랜덤 전투 인챈트먼트를 설정하여 전투 방식 변경
TriggerManager:InvokeTriggers -- 트리거를 발동시키고 카드를 열어서 트리거 실행
TriggerManager:RunTriggers -- 특정 객체의 모든 트리거를 실행
TriggerManager:RunTrigger -- 개별 트리거를 실행
TriggerManager:IsTriggerCondition -- 트리거 조건을 확인
TriggerManager:ShareOpenCards -- 트리거로 인해 공개될 카드들을 공유
TriggerManager:AirStrike -- 에어 스트라이크 스킬 - 상대 유닛들에게 피해, 핸드가 비어있으면 추가 피해
TriggerManager:AirStrikeCondition -- 에어 스트라이크 발동 조건 - 캐스트 시
UIManager:OnBeginPlay -- UI 매니저 초기화 시 기본 모듈들을 생성하고 설정
UIManager:SetMobileUIEnable -- 모바일 플랫폼에서 모바일 UI 요소들의 활성화 상태를 설정
UIManager:SpawnAndSetModule -- 지정된 모듈을 생성하고 설정
UIManager:UpdateButtons -- 모든 UI 모듈들의 버튼 활성화 상태를 계층적으로 업데이트
UIManager:UpdatePlayerController -- 플레이어 컨트롤러의 활성화 상태를 UI 모듈 상태에 따라 업데이트
UIManager:UpdateChat -- 채팅 시스템의 활성화 상태를 업데이트
UIManager:UpdateMobileUI -- 모바일 UI의 활성화 상태를 게임 상태와 UI 모듈 상태에 따라 업데이트
Card:OnBeginPlay -- 게임 시작 시 클라이언트에서 플레이 가능 및 신호 가능 배열에 추가
Card:GetPublicProperties -- 공개 가능한 카드 속성들을 반환 (플레이어, 덱, 핸드)
Card:GetProperties -- 카드의 모든 속성들을 테이블로 반환
Card:OnSyncProperties -- 속성 동기화 시 플레이어 재설정 및 블루프린트 갱신
Card:SetPropertiesInClient -- 클라이언트에서 속성 설정 후 액터 생성
Card:SyncProperties -- 사용자에게 카드 속성 동기화 (아군이면 전체, 적군이면 공개 정보만)
Card:SetVariables -- 카드의 변수들을 설정 (비용, 최대 체력, 공격력)
Card:ClearVariables -- 카드의 모든 변수들을 초기화
Card:SetTriggerNames -- 트리거 이름들을 설정하고 타겟 필요 여부 확인
Card:GetBlueprint -- 카드의 블루프린트 정보를 반환 (정보, 인챈트먼트, 독립 변수)
Card:SetBlueprint -- 블루프린트로부터 카드 정보를 설정
Card:ClearBlueprint -- 카드의 블루프린트 정보를 모두 초기화
Card:Clear -- 카드를 정리하고 파괴
Card:GetInputState -- 캐릭터가 이 카드를 플레이할 수 있는지 확인하고 입력 상태 반환
Card:SetInputState -- 입력 상태를 설정하여 플레이 가능 여부와 타겟 배열 결정
Card:IsOwner -- 카드 소유자인지 확인
Card:IsAllyWith -- 지정된 캐릭터와 같은 편인지 확인
Card:IsAlly -- 아군인지 확인
Card:ShareId -- 카드 ID를 서버-클라이언트 간 공유
Card:SharePrivateId -- 카드 ID를 아군에게만 비공개로 공유
Card:ShareBlueprint -- 카드 블루프린트를 서버-클라이언트 간 공유
Card:SharePrivateBlueprint -- 카드 블루프린트를 아군에게만 비공개로 공유
Card:GetActorPosition -- 카드 액터의 월드 좌표를 2D 벡터로 반환
Card:SpawnAndSetActor -- 카드 액터를 생성하고 설정
Card:SetActor -- 카드 액터를 설정하고 상호 참조 연결
Card:ClearActor -- 액터 참조를 해제하고 앞뒤면 정리
Card:DestroyActor -- 액터 엔티티를 파괴하고 정리
Card:SpawnAndSetFront -- 카드 앞면을 생성하고 설정
Card:SetFront -- 카드 앞면을 설정하고 UI 요소들을 연결
Card:ClearFront -- 카드 앞면 참조를 해제하고 UI 요소들 정리
Card:DestroyFront -- 카드 앞면 엔티티를 파괴하고 정리
Card:SpawnAndSetBack -- 카드 뒷면을 생성하고 설정
Card:SetBack -- 카드 뒷면을 설정하고 터치 이벤트 연결
Card:ClearBack -- 카드 뒷면 참조를 해제
Card:DestroyBack -- 카드 뒷면 엔티티를 파괴하고 정리
Card:SetActorEnable -- 액터의 활성화 상태를 설정
Card:SetInfo -- 카드 정보를 설정하고 관련 속성들을 초기화
Card:ClearInfo -- 카드 정보를 초기화하고 앞면을 파괴
Card:SetBackName -- 카드 뒷면 이름을 설정하고 뒷면 생성
Card:ClearBackName -- 카드 뒷면 이름을 초기화하고 뒷면 파괴
Card:SetPlayer -- 카드의 플레이어를 설정하고 해당 플레이어의 카드 뒷면 적용
Card:ClearPlayer -- 플레이어 참조를 해제하고 뒷면 정리
Card:GetBlueprintByName -- 카드 이름으로 블루프린트를 생성하여 반환
Card:GetBlueprintsByNames -- 여러 카드 이름들로 블루프린트 배열을 생성
Card:GetCardTokens -- 카드 이름들로 카드 토큰들을 생성하여 반환
Card:GetMinionEnchantments -- 미니언 관련 인챈트먼트들만 필터링하여 반환
Card:GetMinionBlueprint -- 미니언 생성을 위한 블루프린트를 반환
Card:Destroy -- 카드를 완전히 파괴하고 리소스 정리
Card:SetFace -- 카드의 앞면 또는 뒷면을 표시
Card:SetAnchorTransform -- 앵커의 위치와 회전을 즉시 설정하고 액터의 월드 좌표는 유지
Card:DestroyTweener -- 트위너를 파괴하여 애니메이션 정리
Card:DestroyAnchorTweener -- 앵커 트위너를 파괴하여 앵커 애니메이션 정리
Card:TransformAnchorTo -- 앵커를 지정된 위치와 회전으로 애니메이션 이동
Card:TransformToAnchor -- 카드를 앵커 위치로 애니메이션 이동
Card:TransformToTarget -- 카드를 타겟 선택 위치로 애니메이션 이동
Card:TransformToCast -- 카드를 시전 위치로 애니메이션 이동
Card:AttachToAnchor -- 카드 액터를 앵커 엔티티에 부착
Card:PlaceFront -- 카드를 앞쪽 레이어에 배치
Card:PlaceBack -- 카드를 뒤쪽 레이어에 배치
Card:IsPlayable -- 카드가 플레이 가능한지 확인 (턴, 마나, 타겟, 필드 상태 검사)
Card:UpdateInputState -- 카드의 입력 상태를 업데이트하여 타겟 가능한 대상들을 갱신
Card:SetSignState -- 카드의 신호 상태를 설정하여 시각적 표시 변경
Card:SetPlayableSign -- 카드의 플레이 가능 여부에 따라 신호 표시 설정
Card:BeginPlayingServerAttribute -- 서버에서 카드 플레이 시작 시 호출되는 속성 메서드
Card:BeginPlaying -- 서버에서 카드 플레이를 시작하고 클라이언트에 알림
Card:BeginPlayingInClient -- 클라이언트에서 카드 플레이 시작 처리 및 애니메이션
Card:EndPlayingServerAttribute -- 서버에서 카드 플레이 종료 시 호출되는 속성 메서드
Card:EndPlaying -- 서버에서 카드 플레이를 종료하고 클라이언트에 알림
Card:EndPlayingInClient -- 클라이언트에서 카드 플레이 종료 처리 및 애니메이션
Card:IsInTouchArea -- 지정된 점이 카드의 터치 영역 내에 있는지 확인
Card:SetDisplayTimer -- 카드 표시 타이머를 설정하여 일정 시간 후 표시 불가능하게 만듦
Card:ClearDisplayTimer -- 카드 표시 타이머를 해제
Card:Swap -- 다른 카드와 ID와 블루프린트를 교환
Card:Open -- 카드를 공개하여 모든 플레이어가 볼 수 있도록 함
Card:PrivateOpen -- 카드를 아군에게만 비공개로 공개
Card:Play -- 카드를 플레이하여 효과를 발동 (구현 필요)
Card:Cast -- 카드를 시전하여 즉시 효과를 발동 (구현 필요)
Card:Put -- 카드를 덱에 넣고 애니메이션 재생
Card:Add -- 카드를 핸드에 추가하고 애니메이션 재생
Card:Draw -- 카드를 덱에서 뽑아 핸드로 가져오고 앞면 표시
Card:Overdraw -- 카드를 과다 드로우하여 파괴 효과와 사운드 재생
Card:Return -- 카드를 핸드에서 덱으로 되돌리고 애니메이션 재생
Card:Discard -- 카드를 버리고 폐기 효과와 사운드 재생
Card:SetCost -- 카드의 비용을 설정하고 UI 업데이트 및 색상 변경
Card:SetMaxHp -- 카드의 최대 체력을 설정하고 UI 업데이트 및 색상 변경
Card:SetAtk -- 카드의 공격력을 설정하고 UI 업데이트 및 색상 변경
Card:AddCostEnchantment -- 카드 비용에 델타 값을 추가하는 인챈트먼트 적용
Card:InsertAddCostEnchantment -- 비용 추가 인챈트먼트를 인챈트먼트 배열에 삽입
Card:SetCostEnchantment -- 카드 비용을 특정 값으로 설정하는 인챈트먼트 적용
Card:InsertSetCostEnchantment -- 비용 설정 인챈트먼트를 인챈트먼트 배열에 삽입
Card:AddMaxHpEnchantment -- 카드 최대 체력에 델타 값을 추가하는 인챈트먼트 적용
Card:InsertAddMaxHpEnchantment -- 최대 체력 추가 인챈트먼트를 인챈트먼트 배열에 삽입
Card:SetMaxHpEnchantment -- 카드 최대 체력을 특정 값으로 설정하는 인챈트먼트 적용
Card:InsertSetMaxHpEnchantment -- 최대 체력 설정 인챈트먼트를 인챈트먼트 배열에 삽입
Card:AddAtkEnchantment -- 카드 공격력에 델타 값을 추가하는 인챈트먼트 적용
Card:InsertAddAtkEnchantment -- 공격력 추가 인챈트먼트를 인챈트먼트 배열에 삽입
Card:SetAtkEnchantment -- 카드 공격력을 특정 값으로 설정하는 인챈트먼트 적용
Card:InsertSetAtkEnchantment -- 공격력 설정 인챈트먼트를 인챈트먼트 배열에 삽입
Deck:GetProperties -- 덱의 속성들을 네트워크 동기화를 위해 테이블로 반환
Deck:OnSyncProperties -- 클라이언트에서 속성 동기화 완료 시 카드들을 화면에 배치
Deck:Clear -- 덱의 모든 카드를 제거하고 덱 참조를 해제하여 초기화
Deck:IsOwner -- 현재 플레이어가 이 덱의 소유자인지 확인
Deck:SetSide -- 덱이 아군인지 적군인지 설정하고 화면 위치를 조정
Deck:InsertCardsWithoutShuffle -- 카드 순서를 유지하며 덱에 삽입하고 화면에 쌓아 올리기
Deck:InsertCards -- 카드들을 랜덤하게 섞어서 덱에 삽입
Deck:InsertCard -- 단일 카드를 덱의 랜덤한 위치에 삽입하여 셔플 효과 구현
Deck:RemoveCards -- 여러 카드를 덱에서 제거하고 화면 정리
Deck:RemoveCard -- 단일 카드를 덱에서 제거하고 덱 참조 해제
Deck:PileUpCards -- 덱의 카드들을 Z축으로 쌓아서 배치
Deck:PlaceCards -- 덱의 모든 카드를 정위치에 배치하고 듀얼 중이면 UI 표시
Deck:SetCardsCount -- 덱의 카드 수를 UI에 표시하고 애니메이션 효과 적용
Deck:AddCardsCount -- 현재 카드 수에 변화량을 더해서 UI 업데이트
Deck:SpawnAndSetImageEntity -- 플레이어의 카드 뒷면 스타일에 맞는 이미지 엔티티 생성
Deck:ShowDetails -- 덱의 상세 정보를 애니메이션과 함께 화면에 표시
Deck:HideDetails -- 덱의 상세 정보를 숨기고 관련 UI 정리
Deck:GetCards -- 덱의 카드들을 복사하여 반환하며 선택자 함수로 필터링 가능
Deck:GetTopCards -- 서버에서 덱의 맨 위 카드들을 지정된 개수만큼 가져오기
Deck:ShareTopCards -- 서버-클라이언트 간 덱의 상위 카드들을 공유하여 동기화
Duel:GetProperties -- 듀얼의 동기화할 속성들을 테이블로 반환
Duel:OnSyncProperties -- 속성 동기화 후 클라이언트에서 듀얼 상태 업데이트
Duel:Clear -- 듀얼 상태를 초기화
Duel:OnBeginPlay -- 듀얼 시작 시 초기 설정 및 객체 배열 초기화
Duel:SetVariables -- 변수 테이블로부터 듀얼 변수들을 설정
Duel:ClearVariables -- 듀얼의 모든 변수들을 초기화
Duel:Sync -- 서버에서 클라이언트로 듀얼 속성 동기화
Duel:Sort -- 객체 배열을 ID 순으로 정렬
Duel:InsertObject -- 새로운 객체를 듀얼에 추가하고 ID 할당
Duel:RemoveObject -- 듀얼에서 객체를 제거
Duel:Invoke -- 모든 객체에 대해 지정된 메서드를 호출
Duel:ShareAcquiredCards -- 지정된 수만큼 카드를 획득하여 배열로 반환
Duel:ShareAcquiredCard -- 카드 한 장을 획득하고 액터 설정 후 반환
Duel:AcquireCard -- 서버에서 카드를 풀에서 가져오거나 새로 생성
Duel:ReleaseCard -- 사용한 카드를 예비 저장소로 반납
Duel:RecycleCards -- 예비 저장소의 카드들을 풀로 재활용
Duel:SpawnAndSetShowingCard -- 클라이언트에서 카드 표시용 오브젝트 생성
Duel:ShareAcquiredMinions -- 지정된 수만큼 미니언을 획득하여 배열로 반환
Duel:ShareAcquiredMinion -- 미니언 한 체를 획득하고 액터 설정 후 반환
Duel:AcquireMinion -- 서버에서 미니언을 풀에서 가져오거나 새로 생성
Duel:ReleaseMinion -- 사용한 미니언을 예비 저장소로 반납
Duel:RecycleMinions -- 예비 저장소의 미니언들을 풀로 재활용
Duel:SetPlacingMinion -- 배치중인 미니언을 설정하고 클라이언트에서 액터 생성
Duel:SpawnAndSetPlacingMinion -- 서버에서 배치용 미니언을 생성하고 설정
Duel:SharePlacingMinion -- 배치중인 미니언을 공유하고 오브젝트 배열에 추가
Duel:DestroyPlacingMinion -- 배치중인 미니언을 파괴
Duel:UpdateEnchantments -- 인챈트먼트를 업데이트하고 오라 재적용
Duel:ApplyAuras -- 모든 오라 인챈트먼트를 초기화하고 재적용
Duel:ShowCard -- 클라이언트에서 카드를 화면에 표시
Duel:GetWinner -- 듀얼의 승리자를 결정하여 반환
Duel:HasDeadPlayer -- 죽은 플레이어가 있는지 확인
Duel:HasDeadMinion -- 죽은 미니언이 있는지 확인
Duel:GetDeadMinions -- 모든 죽은 미니언들을 배열로 반환
Duel:HasBattler -- 전투 가능한 미니언이 있는지 확인
Duel:HasBattlerBoth -- 양쪽 플레이어 모두 전투 가능한 미니언이 있는지 확인
Duel:GetFrontBattlers -- 양쪽 플레이어의 전면 전투용 미니언들을 반환
Duel:GetDirectAttackers -- 직접 공격 가능한 미니언들을 반환
Duel:GetMinions -- 선택자에 따른 모든 미니언들을 반환
Duel:ShareRandomMinions -- 랜덤으로 선택된 미니언들을 공유하여 반환
Duel:GetUnits -- 모든 유닛(플레이어 + 미니언)들을 반환
Duel:ShareRandomUnits -- 랜덤으로 선택된 유닛들을 공유하여 반환
Duel:GetPlayers -- 모든 플레이어들을 복사하여 반환
Duel:ShareRandomPlayer -- 랜덤으로 선택된 플레이어를 공유하여 반환
Duel:GetCards -- 선택자에 따른 모든 카드들을 반환
Duel:GetDeckCards -- 선택자에 따른 모든 덱 카드들을 반환
Duel:GetHandCards -- 선택자에 따른 모든 핸드 카드들을 반환
Duel:ShareRandomHandCards -- 랜덤으로 선택된 핸드 카드들을 공유하여 반환
Duel:SetBeginDuelTimer -- 두 플레이어 모두 준비됐을 때 듀얼 시작 타이머 설정
Duel:SetBeginDuelTimerInClient -- 클라이언트에서 듀얼 시작 예고 메시지 표시
Duel:ClearBeginDuelTimer -- 듀얼 시작 타이머를 취소하고 클라이언트 메시지 제거
Duel:ClearBeginDuelTimerInClient -- 클라이언트에서 듀얼 시작 메시지 제거
Duel:BeginDuel -- 듀얼을 시작하고 초기 설정 수행
Duel:SetSides -- 클라이언트에서 우리쪽/적 플레이어를 구분하여 설정
Duel:PlacePlayers -- 플레이어들을 기본 위치에 배치
Duel:ShowIntro -- 듀얼 시작 인트로 애니메이션과 이팩트 표시
Duel:PutDeckCards -- 플레이어들의 덱에 카드들을 배치하고 애니메이션 수행
Duel:DrawStartingCards -- 게임 시작 시 초기 카드들을 드로우
Duel:EndDuel -- 듀얼을 종료하고 정리 작업 수행
Duel:ShowOutro -- 듀얼 종료 아웃트로 애니메이션과 결과 표시
Duel:ReturnEndingCards -- 게임 종료 시 핸드의 카드들을 덱으로 반납
Duel:EraseDeckCards -- 덱의 모든 카드들을 제거하고 애니메이션 수행
Duel:EndMatch -- 매치 종료 처리 및 보상 지급 등의 서버 로직 수행
Duel:ShowResult -- 클라이언트에서 게임 결과에 따른 보상들을 화면에 표시
Duel:DarkenBackground -- 듀얼 시작 시 배경을 어둡게 만들기
Duel:LightenBackground -- 듀얼 종료 시 배경을 밝게 복원
Duel:EndRound -- 라운드를 종료하고 플레이어 상태 초기화
Duel:BeginRound -- 새로운 라운드를 시작하고 라운드 플레이어 설정
Duel:EndTurn -- 턴을 종료하고 타이머 정리 및 상태 초기화
Duel:BeginTurn -- 새로운 턴을 시작하고 턴 플레이어 설정
Duel:BeginCountdown -- 클라이언트에서 턴 종료 카운트다운 시작
Duel:EndCountdown -- 클라이언트에서 카운트다운 종료 처리
Duel:BattlePhase -- 전투 페이즈 처리 (현재 비어있음)
Duel:Battle -- 미니언들 간의 전투 처리 (현재 비어있음)
Duel:SetRandomBattle -- 랜덤 전투 모드 설정
Duel:SetRandomBattleEnchantment -- 인챈트먼트로 랜덤 전투 모드 설정
Duel:InsertSetRandomBattleEnchantment -- 랜덤 전투 모드 인챈트먼트를 삽입
Field:GetProperties -- 필드의 속성들을 테이블로 반환
Field:OnSyncProperties -- 속성 동기화 시 로컬 미니언 배열 복사 및 배치
Field:Clear -- 필드의 모든 미니언을 제거하고 초기화
Field:GetInputState -- 캐릭터가 이 필드에 미니언을 배치할 수 있는지 확인
Field:SetInputState -- 입력 상태를 설정하여 배치 가능 여부 결정
Field:IsOwner -- 필드 소유자인지 확인
Field:IsEmpty -- 필드가 비어있는지 확인
Field:IsFull -- 필드가 가득 찼는지 확인
Field:GetMinions -- 선택자 조건에 맞는 미니언들을 반환
Field:ShareRandomMinions -- 조건에 맞는 살아있는 미니언들 중 랜덤으로 지정된 수만큼 공유
Field:GetLeftmostMinion -- 가장 왼쪽에 있는 미니언 반환
Field:GetRightmostMinion -- 가장 오른쪽에 있는 미니언 반환
Field:GetFrontMinion -- 가장 앞에 있는 미니언 반환 (첫 번째 미니언)
Field:HasDeadMinion -- 죽은 미니언이 있는지 확인
Field:GetDeadMinions -- 죽은 미니언들을 모두 반환
Field:HasBattler -- 전투 가능한 미니언이 있는지 확인
Field:GetBattlers -- 전투 가능한 미니언들을 모두 반환
Field:GetDirectAttackers -- 직접 공격 가능한 미니언들을 모두 반환
Field:GetFrontBattler -- 최전방 전투 미니언을 반환 (랜덤 전투 시 랜덤 선택)
Field:SetSide -- 필드의 소속을 설정하고 위치 조정
Field:PlaceMinions -- 모든 미니언을 앵커에 배치하고 위치 초기화
Field:InsertMinions -- 피벗 미니언 뒤에 여러 미니언들을 삽입
Field:InsertMinion -- 단일 미니언을 지정된 인덱스에 삽입
Field:RemoveMinions -- 여러 미니언들을 필드에서 제거
Field:RemoveMinion -- 단일 미니언을 필드에서 제거
Field:InsertPlacingMinon -- 배치 중인 미니언을 X 좌표에 따라 적절한 위치에 삽입
Field:RemovePlacingMinion -- 배치 중인 미니언을 제거
Field:SpawnAndAttachToAnchor -- 미니언에 앵커를 생성하고 부착
Field:SpawnAnchor -- 미니언에 앵커 엔티티를 생성
Field:DestroyAnchor -- 미니언의 앵커 엔티티를 파괴
Field:DropAnchors -- 모든 미니언의 앵커를 일렬로 배치
Field:GetCurrentPlaceIndex -- 현재 배치 중인 미니언의 인덱스 반환
Field:GetNextPlaceIndex -- X 좌표를 기준으로 다음 배치 인덱스 계산
Field:FindPlacePivot -- 배치 기준이 될 피벗 미니언을 찾아 반환
Field:SortMinions -- 미니언들을 정렬하고 앵커 재배치
Field:MoveMinionToFarLeft -- 미니언을 가장 왼쪽으로 이동
Field:MoveMinionToFarRight -- 미니언을 가장 오른쪽으로 이동
Field:GetEmptySlotCount -- 필드의 빈 슬롯 수 반환
Hand:GetProperties -- 핸드의 속성들을 테이블로 반환
Hand:OnSyncProperties -- 속성 동기화 시 카드 배치 및 핸드 위치 조정
Hand:Clear -- 핸드의 모든 카드를 제거하고 초기화
Hand:IsOwner -- 핸드 소유자인지 확인
Hand:IsEmpty -- 핸드가 비어있는지 확인
Hand:IsFull -- 핸드가 가득 찼는지 확인
Hand:GetCards -- 선택자 조건에 맞는 카드들 반환
Hand:ShareRandomCards -- 조건에 맞는 카드들 중 랜덤으로 지정된 수만큼 공유
Hand:ShareRandomBlueprints -- 조건에 맞는 카드들의 블루프린트를 랜덤으로 공유
Hand:SetSide -- 핸드의 소속 설정 (우리편/상대편)
Hand:InsertCards -- 여러 카드를 핸드에 삽입하고 앵커에 배치
Hand:InsertCard -- 단일 카드를 핸드에 삽입
Hand:RemoveCards -- 여러 카드를 핸드에서 제거하고 앵커 파괴
Hand:RemoveCard -- 단일 카드를 핸드에서 제거
Hand:RemovePlayingCard -- 플레이 중인 카드를 로컬 배열에서 제거
Hand:SpawnAndAttachToAnchor -- 카드에 앵커를 생성하고 부착
Hand:SpawnAnchor -- 카드에 앵커 엔티티를 생성
Hand:DestroyAnchor -- 카드의 앵커 엔티티를 파괴
Hand:DropAnchors -- 카드들의 앵커를 원형으로 배치
Hand:GetAnchorPosition -- 반지름과 회전각도로 앵커 위치 계산
Hand:PlaceCards -- 모든 카드를 앵커에 배치하고 위치 초기화
Hand:DestroyTweener -- 핸드의 트위너를 파괴
Hand:TransformToPlay -- 핸드를 플레이 위치로 이동
Hand:TransformToRest -- 핸드를 휴식 위치로 이동
Hand:TransformToEndRound -- 핸드를 라운드 종료 위치로 이동
Hand:GetLeftmostCard -- 가장 왼쪽 카드를 반환
Hand:GetRightmostCard -- 가장 오른쪽 카드를 반환
History:GetProperties -- 히스토리 데이터를 네트워크 동기화를 위해 테이블로 반환
History:Initialize -- 듀얼 시작 시 모든 플레이어의 히스토리 데이터 테이블 초기화
History:Clear -- 듀얼 종료 시 모든 히스토리 데이터를 완전히 초기화
History:GetThisRoundCardCount -- 현재 라운드에서 플레이어가 플레이한 총 카드 수 반환
History:GetThisRoundMinionCount -- 현재 라운드에서 플레이어가 소환한 미니언 카드 수 계산
History:GetThisRoundMinionCountByTag -- 현재 라운드에서 특정 태그를 가진 미니언 카드 소환 수 계산
History:GetThisRoundSkillCount -- 현재 라운드에서 플레이어가 사용한 스킬 카드 수 계산
History:ClearThisRoundCard -- 라운드 종료 시 플레이어의 라운드별 카드 사용 기록 초기화
History:AddThisRoundCard -- 플레이어가 카드를 플레이할 때 라운드 기록에 추가
History:GetThisGameCardCount -- 현재 게임에서 플레이어가 플레이한 총 카드 수 반환
History:GetThisGameMinionCount -- 현재 게임에서 플레이어가 소환한 미니언 카드 총 수 계산
History:GetThisGameMinionsByTag -- 현재 게임에서 특정 태그를 가진 미니언들의 이름 목록 반환
History:GetThisGameMinionsByCost -- 현재 게임에서 특정 코스트를 가진 미니언들의 이름 목록 반환
History:GetThisGameSkillCount -- 현재 게임에서 플레이어가 사용한 스킬 카드 총 수 계산
History:GetThisGameSkillCountByCostOrMore -- 현재 게임에서 지정된 코스트 이상의 스킬 카드 사용 수 계산
History:ClearThisGameCard -- 게임 종료 시 플레이어의 게임별 카드 사용 기록 초기화
History:AddThisGameCard -- 플레이어가 카드를 플레이할 때 게임 전체 기록에 추가
History:GetThisGameDeadMinions -- 현재 게임에서 사망한 플레이어의 미니언 목록 반환
History:GetThisGameDeadMinionsByTag -- 현재 게임에서 사망한 미니언 중 특정 태그를 가진 미니언 목록 반환
History:ClearThisGameDeadMinion -- 게임 종료 시 플레이어의 사망 미니언 기록 초기화
History:AddThisGameDeadMinion -- 미니언이 사망할 때 게임 전체 사망 기록에 추가
History:GetThisRoundDeadMinionCount -- 현재 라운드에서 사망한 미니언 수 반환
History:GetThisRoundDeadMinions -- 현재 라운드에서 사망한 미니언 목록 반환
History:ClearThisRoundDeadMinion -- 라운드 종료 시 플레이어의 라운드별 사망 미니언 기록 초기화
History:AddThisRoundDeadMinion -- 미니언이 사망할 때 라운드별 사망 기록에 추가
History:GetThisGameMp -- 현재 게임에서 플레이어가 사용한 총 마나 포인트 반환
History:AddThisGameMp -- 플레이어가 마나를 소모할 때 게임 전체 마나 사용량에 추가
History:GetThisGameDiscardedCardCount -- 현재 게임에서 버려진 카드 수 반환
History:GetThisGameDiscardedCards -- 현재 게임에서 버려진 카드 목록 반환
History:AddThisGameDiscardedCard -- 카드가 버려질 때 게임 전체 버림 기록에 추가
Minion:GetProperties -- 미니언의 모든 속성들을 테이블로 반환
Minion:SetPropertiesInClient -- 클라이언트에서 속성을 설정하고 액터를 생성
Minion:OnSyncProperties -- 속성 동기화 시 블루프린트와 플레이어 정보를 재설정
Minion:SetVariables -- 미니언의 변수들을 설정 (공격력, 방어막, 독 등)
Minion:GetIndependentVariables -- 독립적인 변수들을 테이블로 반환 (방어막, 빙결, 기절, 공포 상태)
Minion:ClearVariables -- 미니언의 모든 변수들을 초기화
Minion:GetBlueprint -- 미니언의 블루프린트 정보를 반환
Minion:SetBlueprint -- 블루프린트로부터 미니언 정보를 설정
Minion:ClearBlueprint -- 미니언의 블루프린트 정보를 모두 초기화
Minion:GetInputState -- 캐릭터가 이 미니언을 조작할 수 있는지 확인하고 입력 상태 반환
Minion:SetInputState -- 입력 상태를 설정하여 미니언 조작 가능 여부 결정
Minion:SetBody -- 미니언 바디를 설정하고 UI 요소들을 연결
Minion:ClearBody -- 미니언 바디 참조를 해제하고 UI 요소들 정리
Minion:SetName -- 미니언의 이름을 설정하고 관련 엔트리와 리소스 로드
Minion:Initialize -- 미니언을 초기화하고 기본 상태 설정
Minion:Clear -- 미니언을 정리하고 파괴
Minion:Dead -- 미니언이 죽을 때 죽음 애니메이션과 효과 재생
Minion:GetLookAtDirection -- 미니언이 바라보는 방향을 반환 (-1: 왼쪽, 1: 오른쪽)
Minion:GetLookAtPosition -- 미니언이 바라보는 방향을 고려한 오프셋 위치를 계산
Minion:LookAtPoint -- 미니언이 지정된 점을 바라보도록 방향 설정
Minion:LookNothing -- 미니언의 방향을 기본 상태로 리셋
Minion:Kill -- 미니언을 즉시 처치하고 피격 애니메이션 재생
Minion:Damage -- 공격자로부터 데미지를 받고 결과를 반환 (방어막, 독, 빙결 등 처리)
Minion:GetInverseScale -- 원본 스케일의 역수를 계산하여 반환
Minion:IsOwner -- 미니언 소유자인지 확인
Minion:IsBattler -- 미니언이 전투 가능한 상태인지 확인 (빙결되지 않음)
Minion:IsDirectAttacker -- 미니언이 직접 공격 가능한지 확인 (전투 가능하고 직접 공격 가능)
Minion:SummonCoroutine -- 미니언 소환 코루틴을 시작
Minion:SpawnAndSetActor -- 미니언 액터를 생성하고 설정
Minion:DestroyActor -- 미니언 액터 엔티티를 파괴하고 정리
Minion:SpawnAndSetBody -- 미니언 바디를 생성하고 설정
Minion:DestroyBody -- 미니언 바디 엔티티를 파괴하고 정리
Minion:SetActorEnable -- 미니언 액터의 활성화 상태를 설정
Minion:GetBlueprintByName -- 카드 이름으로 블루프린트를 생성하여 반환
Minion:GetBlueprintsByNames -- 여러 카드 이름들로 블루프린트 배열을 생성
Minion:GetCardTokens -- 카드 이름들로 카드 토큰들을 생성하여 반환
Minion:SetInfo -- 미니언 정보를 설정하고 관련 속성들을 초기화
Minion:ClearInfo -- 미니언 정보를 초기화하고 바디를 파괴
Minion:SetPlayer -- 미니언의 플레이어를 설정
Minion:ClearPlayer -- 플레이어 참조를 해제
Minion:Destroy -- 미니언을 완전히 파괴하고 리소스 정리
Minion:Animate -- 미니언의 애니메이션 상태를 변경
Minion:GetOtherUnits -- 자신을 제외한 모든 유닛들을 반환
Minion:ShareRandomOtherUnits -- 자신을 제외한 살아있는 유닛들 중 랜덤으로 지정된 수만큼 선택
Minion:GetOtherMinions -- 자신을 제외한 다른 미니언들을 선택자 조건에 따라 반환
Minion:ShareRandomOtherMinions -- 자신을 제외한 살아있는 다른 미니언들 중 랜덤으로 지정된 수만큼 선택
Minion:GetOurOtherUnits -- 자신을 제외한 아군 유닛들을 반환
Minion:ShareRandomOurOtherUnits -- 자신을 제외한 살아있는 아군 유닛들 중 랜덤으로 지정된 수만큼 선택
Minion:GetOurOtherMinions -- 자신을 제외한 아군 미니언들을 선택자 조건에 따라 반환
Minion:ShareRandomOurOtherMinions -- 자신을 제외한 살아있는 아군 미니언들 중 랜덤으로 지정된 수만큼 선택
Minion:GetLeftMinion -- 자신의 왼쪽에 있는 미니언을 선택자 조건에 따라 반환
Minion:GetLeftMinions -- 자신의 왼쪽에 있는 미니언들을 지정된 수만큼 선택자 조건에 따라 반환
Minion:GetRightMinion -- 자신의 오른쪽에 있는 미니언을 선택자 조건에 따라 반환
Minion:GetRightMinions -- 자신의 오른쪽에 있는 미니언들을 지정된 수만큼 선택자 조건에 따라 반환
Minion:GetSelfAndRightMinions -- 자신과 오른쪽 미니언들을 합쳐서 반환
Minion:GetAdjacentMinions -- 자신의 인접한 미니언들(왼쪽 1개, 오른쪽 1개)을 반환
Minion:GetSelfAndAdjacentMinions -- 자신과 인접한 미니언들을 모두 합쳐서 반환
Minion:Summon -- 미니언을 소환하고 소환 액션 실행
Minion:Kick -- 미니언을 킥하여 필드에서 제거하고 효과 재생
Minion:Vanish -- 미니언을 사라지게 하여 액터 비활성화
Minion:Transform -- 미니언을 다른 형태로 변신시키고 변신 효과 재생
Minion:DirectAttack -- 미니언이 직접 공격을 수행 (구현 필요)
Minion:Freeze -- 미니언을 빙결 상태로 만듦
Minion:Thaw -- 미니언의 빙결 상태를 해제
Minion:Stun -- 미니언을 기절 상태로 만듦
Minion:Awake -- 미니언의 기절 상태를 해제
Minion:Scare -- 미니언을 공포 상태로 만듦
Minion:GainBarrier -- 미니언이 방어막을 획득
Minion:LoseBarrier -- 미니언이 방어막을 잃음
Minion:SetAtk -- 미니언의 공격력을 설정하고 UI 업데이트 및 색상 변경
Minion:AddAtkEnchantment -- 미니언 공격력에 델타 값을 추가하는 인챈트먼트 적용
Minion:InsertAddAtkEnchantment -- 공격력 추가 인챈트먼트를 인챈트먼트 배열에 삽입
Minion:SetAtkEnchantment -- 미니언 공격력을 특정 값으로 설정하는 인챈트먼트 적용
Minion:InsertSetAtkEnchantment -- 공격력 설정 인챈트먼트를 인챈트먼트 배열에 삽입
Minion:SetBarrier -- 미니언의 방어막 상태를 설정하고 시각적 효과 적용
Minion:SetVenom -- 미니언의 독 상태를 설정하고 시각적 표시 변경
Minion:SetVenomEnchantment -- 미니언의 독 상태를 설정하는 인챈트먼트 적용
Minion:InsertSetVenomEnchantment -- 독 설정 인챈트먼트를 인챈트먼트 배열에 삽입
Minion:SetChill -- 미니언의 냉기 상태를 설정
Minion:SetDirectAttackable -- 미니언의 직접 공격 가능 여부를 설정
Minion:SetImmuneToStrong -- 미니언의 강력한 공격 면역 여부를 설정
Minion:SetFreeze -- 미니언의 빙결 상태를 설정하고 애니메이션 및 시각적 효과 적용
Minion:SetStun -- 미니언의 기절 상태를 설정하고 시각적 표시 변경
Minion:SetScare -- 미니언의 공포 상태를 설정하고 시각적 표시 변경
Object:OnBeginPlay -- 게임 시작 시 듀얼 관련 매니저들을 참조 설정
Object:IsUnit -- 이 객체가 유닛인지 확인
Object:IsMinion -- 이 객체가 미니언인지 확인
Object:IsPlayer -- 이 객체가 플레이어인지 확인
Object:IsCard -- 이 객체가 카드인지 확인
Object:GetProperties -- 객체의 모든 속성을 테이블로 반환
Object:SetProperties -- 속성 테이블을 받아 객체 속성들을 설정
Object:SetPropertiesInClient -- 클라이언트에서 속성을 설정
Object:SyncProperties -- 서버에서 클라이언트로 속성 동기화
Object:OnSyncProperties -- 속성 동기화 후 블루프린트 재설정
Object:IsTargetable -- 플레이어가 이 객체를 타겟으로 할 수 있는지 확인
Object:SetName -- 객체의 이름과 엔트리를 설정
Object:ClearName -- 객체의 이름과 엔트리를 초기화
Object:SetEnchantments -- 인챈트먼트 배열을 설정하고 적용
Object:ClearEnchantments -- 모든 인챈트먼트를 초기화
Object:SetVariables -- 변수 테이블로부터 트리거와 오라 이름들을 설정
Object:ClearVariables -- 모든 변수들을 초기화
Object:GetIndependentVariables -- 독립적인 변수들을 테이블로 반환
Object:InsertEnchantment -- 새로운 인챈트먼트를 추가하고 적용
Object:ApplyEnchantments -- 모든 인챈트먼트와 오라를 적용하여 변수 업데이트
Object:Initialize -- 객체를 초기화하고 인챈트먼트 적용
Object:Clear -- 객체의 모든 데이터를 초기화
Object:SetTriggerNames -- 트리거 이름 배열을 설정
Object:AddTriggerNameEnchantment -- 인챈트먼트로 트리거 이름을 추가
Object:InsertAddTriggerNameEnchantment -- 트리거 이름 추가 인챈트먼트를 삽입
Object:SetAuraNames -- 오라 이름 배열을 설정
Object:AddAuraNameEnchantment -- 인챈트먼트로 오라 이름을 추가
Object:InsertAddAuraNameEnchantment -- 오라 이름 추가 인챈트먼트를 삽입
Object:InsertAuraEnchantments -- 오라 인챈트먼트들을 배열에 추가
Object:ClearAuraEnchantments -- 모든 오라 인챈트먼트를 초기화
Object:GetBlueprint -- 객체의 블루프린트 정보를 반환
Object:SetBlueprint -- 블루프린트로부터 객체 정보를 설정
Object:ClearBlueprint -- 블루프린트 관련 모든 데이터를 초기화
Object:TryRemoveEnchantments -- 조건에 맞는 인챈트먼트들을 제거 시도
Object:GetInputState -- 캐릭터의 입력 상태를 반환 (서브클래스에서 오버라이드)
Object:SetInputState -- 입력 상태를 설정 (서브클래스에서 오버라이드)
Player:GetProperties -- 네트워크 동기화를 위한 플레이어의 핵심 속성들을 테이블로 반환
Player:OnSyncProperties -- 속성 동기화 완료 후 클라이언트에서 플레이어 UI 및 게임 상태 업데이트
Player:SetVariables -- 변수 테이블로부터 플레이어 변수들을 설정
Player:GetIndependentVariables -- 독립적인 변수들을 테이블로 반환
Player:ClearVariables -- 플레이어의 모든 변수들을 초기화
Player:Clear -- 플레이어의 모든 데이터를 초기화
Player:Initialize -- 플레이어를 초기화하고 기본 상태 설정
Player:OnBeginPlay -- 게임 시작 시 플레이어 초기 설정 및 이벤트 연결
Player:GetLookAtDirection -- 플레이어가 바라보는 방향을 반환
Player:GetLookAtPosition -- 플레이어가 바라보는 방향에 따른 오프셋 위치 계산
Player:LookLeft -- 플레이어를 왼쪽으로 향하게 설정
Player:LookRight -- 플레이어를 오른쪽으로 향하게 설정
Player:LookNothing -- 플레이어를 기본 방향으로 설정 (우리쪽/적에 따라)
Player:Damage -- 플레이어가 데미지를 받을 때의 처리 및 이팩트 표시
Player:SetName -- 플레이어의 이름과 엔트리를 설정
Player:ReadyServerAttribute -- 서버 속성 준비 (오버라이드용)
Player:Ready -- 서버에서 플레이어가 듀얼에 참여 준비를 완료했을 때의 처리
Player:ReadyInOwner -- 클라이언트에서 소유자 플레이어의 듀얼 준비 완료 처리
Player:ReadyInClient -- 클라이언트에서 플래이어 캐릭터 연결 설정
Player:FixCharacter -- 서버에서 캐릭터를 플레이어에 고정하고 설정
Player:FixCharacterInOwner -- 소유자 클라이언트에서 캐릭터 고정 처리
Player:FixCharacterInClient -- 일반 클라이언트에서 캐릭터 고정 처리
Player:FixCharacterNone -- 기본 캐릭터 고정 설정
Player:FixCharacterSync -- 캐릭터를 듀얼 모드에 맞게 설정 (이동 비활성화 등)
Player:TardyServerAttribute -- 서버 속성 지연 처리 (오버라이드용)
Player:Tardy -- 서버에서 플레이어가 듀얼에서 나갔을 때의 처리
Player:TardyInOwner -- 소유자 클라이언트에서 듀얼 나간 후 UI 복원
Player:TardyInClient -- 일반 클라이언트에서 듀얼 나간 후 정리
Player:UnfixCharacter -- 서버에서 캐릭터를 플레이어에서 분리하고 원래 상태로 복원
Player:UnfixCharacterInOwner -- 소유자 클라이언트에서 캐릭터 분리 처리
Player:UnfixCharacterInClient -- 일반 클라이언트에서 캐릭터 분리 처리
Player:UnfixCharacterNone -- 기본 캐릭터 분리 설정
Player:UnfixCharacterSync -- 캐릭터를 일반 모드로 복원 (이동 활성화 등)
Player:SetServing -- 플레이어의 서비스 상태를 설정 (듀얼 참여 가능 여부)
Player:IsOwner -- 이 플레이어가 로컬 플레이어인지 확인
Player:IsAlly -- 이 플레이어가 아군인지 확인
Player:IsAllyWith -- 지정된 캐릭터와 아군 관계인지 확인
Player:SetSide -- 클라이언트에서 플레이어의 사이드를 설정 (우리쪽/적)
Player:SetFloating -- 플래이어의 떠다니는 애니메이션 설정
Player:PlayEmotion -- 플래이어 캐릭터에 감정 애니메이션 재생
Player:Animate -- 플래이어 캐릭터에 지정된 애니메이션 재생
Player:IsOurTurn -- 현재 이 플레이어의 턴인지 확인
Player:ShowClassTag -- 플레이어의 클래스 태그를 표시
Player:HideClassTag -- 플레이어의 클래스 태그를 숨김
Player:ShowDetails -- 플래이어의 HP, MP 세부 정보를 표시
Player:HideDetails -- 플래이어의 HP, MP 세부 정보를 숨김
Player:TransformAnchorToPlay -- 플래이어 앵커를 플레이 위치로 이동
Player:TransformAnchorToEndRound -- 플래이어 앵커를 전투 위치로 이동
Player:SetPlaying -- 플래이어의 플레이 상태를 설정하고 애니메이션 조정
Player:SetRoundPlayerSign -- 라운드 플레이어 표시를 설정 (배경 색상 변경)
Player:JobsDone -- 플레이어가 더 이상 플레이할 카드가 없는지 확인
Player:GetUnits -- 플래이어와 그의 미니언들을 모두 포함한 유닛 배열 반환
Player:ShareRandomUnits -- 랜덤으로 선택된 이 플레이어의 유닛들을 공유하여 반환
Player:GetCards -- 선택자에 따른 플래이어의 모든 카드들을 반환 (덱 + 핸드)
Player:DeclareEndRound -- 플래이어가 라운드 종료를 선언
Player:SetEndRoundDeclared -- 라운드 종료 선언 상태를 설정
Player:SetMaxMp -- 플래이어의 최대 MP를 설정
Player:SetMp -- 플래이어의 현재 MP를 설정하고 UI 업데이트
Player:GainMp -- MP를 획득하고 이팩트 표시
Player:LoseMp -- MP를 잃음
Player:SetSkillDamage -- 플래이어의 스킬 데미지를 설정
Player:AddSkillDamageEnchantment -- 인챈트먼트로 스킬 데미지를 추가
Player:InsertAddSkillDamageEnchantment -- 스킬 데미지 추가 인챈트먼트를 삽입
Player:SetTaggedSkillDamages -- 태그별 스킬 데미지 테이블을 설정
Player:AddSkillDamageByTagEnchantment -- 인챈트먼트로 특정 태그의 스킬 데미지를 추가
Player:InsertAddSkillDamageByTagEnchantment -- 태그별 스킬 데미지 추가 인챈트먼트를 삽입
Player:Chat -- 플래이어 위에 채팅 메시지를 표시
Player:ClearChat -- 채팅 메시지를 제거
Player:SpawnAndSetFriendRequestButton -- 친구 요청 버튼을 생성하고 설정
Player:ShowFriendRequestButton -- 친구 요청 버튼을 표시 (조건 충족 시)
Player:HideFriendRequestButton -- 친구 요청 버튼을 숨김
Player:SetImmuneToDirectAttack -- 직접 공격 면역 상태를 설정
Player:SetImmuneToDirectAttackEnchantment -- 인챈트먼트로 직접 공격 면역 상태를 설정
Player:InsertSetImmuneToDirectAttackEnchantment -- 직접 공격 면역 인챈트먼트를 삽입
Player:HandleKeyDownEvent -- 키보드 입력 이벤트 처리 (Alt/Space로 듀얼 나가기)
Player:HandleButtonClickEvent -- 버튼 클릭 이벤트 처리 (듀얼 나가기)
Player:HandleChatEvent -- 채팅 이벤트 처리 (플래이어 채팅 메시지 표시)
Unit:SetVariables -- 유닛의 변수들을 설정 (생존 상태, 최대 체력, 현재 체력)
Unit:GetIndependentVariables -- 독립적인 변수들을 테이블로 반환 (죽음 상태, 현재 체력)
Unit:ClearVariables -- 유닛의 모든 변수들을 초기화
Unit:IsTargetable -- 플레이어가 이 유닛을 타겟으로 지정할 수 있는지 확인
Unit:Initialize -- 유닛을 초기화하고 생존 상태로 설정, 체력을 최대치로 설정
Unit:OnBeginPlay -- 게임 시작 시 클라이언트에서 신호 가능한 배열에 자신을 추가
Unit:SetActor -- 유닛의 액터를 설정하고 상호 참조 연결
Unit:ClearActor -- 액터 참조를 해제하고 바디도 함께 정리
Unit:SetBody -- 유닛의 바디를 설정하고 UI 요소들을 연결
Unit:ClearBody -- 바디 참조를 해제하고 관련 UI 요소들을 정리
Unit:SetSignState -- 유닛의 신호 상태를 설정하고 색상으로 표시
Unit:PlaceFront -- 액터를 앞쪽 레이어로 배치
Unit:PlaceBack -- 액터를 뒤쪽 레이어로 배치
Unit:GetActorPosition -- 액터의 월드 좌표를 2D 벡터로 반환
Unit:DestroyTweener -- 트위너를 파괴하여 애니메이션 정리
Unit:DestroyAnchorTweener -- 앵커 트위너를 파괴하여 앵커 애니메이션 정리
Unit:SetAnchorTransform -- 앵커의 위치를 즉시 설정하고 액터의 월드 위치는 유지
Unit:TransformAnchorTo -- 앵커를 지정된 위치로 애니메이션 이동
Unit:TransformToAnchor -- 액터를 앵커 위치로 애니메이션 이동
Unit:AttachToAnchor -- 액터를 앵커에 부착
Unit:LookAt -- 다른 유닛을 바라보도록 설정
Unit:LookAtPoint -- 특정 지점을 바라보도록 설정 (하위 클래스에서 구현)
Unit:LookLeft -- 왼쪽을 바라보도록 설정 (하위 클래스에서 구현)
Unit:LookRight -- 오른쪽을 바라보도록 설정 (하위 클래스에서 구현)
Unit:LookNothing -- 기본 방향으로 설정 (하위 클래스에서 구현)
Unit:GetLookAtDirection -- 바라보는 방향을 반환 (하위 클래스에서 구현)
Unit:GetLookAtPosition -- 바라보는 방향 기준으로 오프셋 위치 계산 (하위 클래스에서 구현)
Unit:GetOffsettedPositionFromPoint -- 특정 지점을 기준으로 오프셋이 적용된 위치를 계산
Unit:GetOffsettedPosition -- 다른 유닛을 기준으로 오프셋이 적용된 위치를 계산
Unit:IsInTouchArea -- 지정된 지점이 터치 영역 내에 있는지 확인
Unit:IsDamaged -- 유닛이 데미지를 받은 상태인지 확인
Unit:SetDead -- 유닛의 생존 상태를 설정
Unit:SetMaxHp -- 최대 체력을 설정하고 현재 체력이 초과하면 조정
Unit:SetHp -- 현재 체력을 설정하고 UI에 반영
Unit:Damage -- 데미지를 받는 처리 (하위 클래스에서 구현)
Unit:Kill -- 유닛을 즉시 사망 처리
Unit:Dead -- 사망 시 처리 (하위 클래스에서 구현)
Unit:Heal -- 체력을 회복
Unit:AddMaxHpEnchantment -- 최대 체력 증가 인챈트먼트 적용
Unit:InsertAddMaxHpEnchantment -- 최대 체력 증가 인챈트먼트를 삽입하고 현재 체력도 증가
Unit:SetMaxHpEnchantment -- 최대 체력 설정 인챈트먼트 적용
Unit:InsertSetMaxHpEnchantment -- 최대 체력 설정 인챈트먼트를 삽입하고 현재 체력을 해당 값으로 설정
BuyPanel:OnBeginPlay -- 구매 패널 초기화 시 버튼 이벤트들을 연결하고 카드팩 구매 및 확률 정보 처리
BuyPanel:Open -- 구매 패널을 열고 지정된 카드팩의 정보를 표시
BuyPanel:Close -- 구매 패널을 닫고 화면에서 숨김
BuyPanel:SetButtonsEnable -- 구매 패널의 모든 버튼들의 활성화 상태를 설정
BuyPanel:ShowCardPack -- 지정된 카드팩과 모드에 따라 UI를 업데이트하고 가격 정보를 표시
CardModule:OnBeginPlay -- 카드 모듈 초기화 시 X버튼 이벤트와 덱 관련 이벤트들을 연결
CardModule:Open -- 카드 모듈을 열고 덱 편집 모드 여부에 따라 UI를 설정
CardModule:Close -- 카드 모듈을 닫고 모든 패널들을 초기화
CardModule:SetMode -- 덱 편집 모드 설정에 따라 적절한 패널을 표시하고 카드 패널 모드를 변경
CardModule:SetButtonsEnable -- 카드 모듈의 모든 패널과 버튼들의 활성화 상태를 설정
CardPackModule:OnBeginPlay -- 카드팩 모듈 초기화 시 버튼 이벤트를 연결하고 카드 엔티티들을 생성
CardPackModule:Open -- 카드팩 모듈을 열고 지정된 카드팩을 표시
CardPackModule:Close -- 카드팩 모듈을 닫고 모든 상태를 초기화
CardPackModule:SetButtonsEnable -- 카드팩 모듈의 버튼들의 활성화 상태를 설정
CardPackModule:ShowCardPack -- 카드팩을 화면에 표시하고 흔들리는 애니메이션을 시작
CardPackModule:OpenCardPack -- 카드팩을 열고 들어있는 카드들을 화면에 표시
CardPanel:OnBeginPlay -- 카드 패널 초기화 시 카드 프리로드, 그리드 생성, 이벤트 연결 등을 수행
CardPanel:Open -- 카드 패널을 화면에 표시하는 애니메이션
CardPanel:Close -- 카드 패널을 닫고 모든 카드를 정리
CardPanel:SetButtonsEnable -- 카드 패널의 모든 버튼들의 활성화 상태를 설정
CardPanel:SetCards -- 지정된 클래스와 조건에 따라 카드들을 설정하고 표시
CardPanel:ShowCards -- 지정된 페이지의 카드들을 화면에 표시
ChannelButton:OnBeginPlay -- 채널 버튼 초기화 시 스케일을 0으로 설정하고 클릭 이벤트를 연결
ChannelButton:SetChannel -- 채널 정보를 설정하고 현재 채널 상태에 따라 UI 표시를 업데이트
ChannelMenu:OnBeginPlay -- 채널 메뉴 초기화 시 화살표 버튼 이벤트를 연결하고 채널 버튼들을 생성
ChannelMenu:Open -- 채널 메뉴를 열고 서버에서 채널 목록을 요청
ChannelMenu:Close -- 채널 메뉴를 닫고 모든 버튼들을 숨김
ChannelMenu:SetButtonsEnable -- 채널 메뉴의 모든 버튼들의 활성화 상태를 설정
ChannelMenu:ShowArrowButtons -- 좌우 화살표 버튼들을 화면에 표시하는 애니메이션을 실행
ChannelMenu:HideArrowButtons -- 좌우 화살표 버튼들을 화면에서 숨김
ChannelMenu:ShowChannelButtons -- 지정된 페이지의 채널 버튼들을 표시
ChannelMenu:HideChannelButtons -- 모든 채널 버튼들을 화면에서 숨김
ChatModule:OnBeginPlay -- 채팅 모듈 초기화 시 채팅 토글 버튼 이벤트를 연결하고 채팅 상태를 관리
ChatModule:SetButtonsEnable -- 채팅 모듈의 버튼 활성화 상태를 설정
ControlMenu:OnBeginPlay -- 컨트롤 메뉴 초기화 시 컨텐츠 엔티티들을 설정하고 카드를 생성하며 화살표 버튼 이벤트를 연결
ControlMenu:Open -- 컨트롤 메뉴를 열고 화살표 버튼들과 첫 번째 컨텐츠를 표시
ControlMenu:Close -- 컨트롤 메뉴를 닫고 모든 UI를 숨김
ControlMenu:SetButtonsEnable -- 컨트롤 메뉴의 버튼들의 활성화 상태를 설정
ControlMenu:ShowArrowButtons -- 화살표 버튼들을 화면에 표시하는 애니메이션
ControlMenu:HideArrowButtons -- 화살표 버튼들을 화면에서 숨김
ControlMenu:ShowContent -- 지정된 페이지의 컨텐츠를 표시
ControlMenu:HideContent -- 모든 컨텐츠를 숨김
DeckEditPanel:OnBeginPlay -- 덱 편집 패널 초기화 시 완료 및 삭제 버튼 이벤트를 연결하고 카드 배치용 썸네일을 생성
DeckEditPanel:Open -- 덱 편집 패널을 열고 현재 덱 정보를 로드하여 카드 썸네일들을 생성하고 배치
DeckEditPanel:Close -- 덱 편집 패널을 닫고 모든 썸네일들을 정리하며 상태를 초기화
DeckEditPanel:SetButtonsEnable -- 덱 편집 패널의 버튼들의 활성화 상태를 설정
DeckEditPanel:RequestSaveDeck -- 현재 편집 중인 덱 정보를 서버에 저장 요청
DeckEditPanel:SpawnAndSetPuttingThumbnail -- 카드 배치용 썸네일을 생성하고 화면 밖 위치에 설정
DeckEditPanel:BeginPuttingThumbnail -- 카드 배치를 시작하고 배치용 썸네일에 카드 정보를 설정
DeckEditPanel:EndPuttingThumbnail -- 카드 배치를 종료하고 배치용 썸네일을 초기화
DeckEditPanel:PlaceThumbnails -- 모든 썸네일들을 그리드 형태로 배치
DeckEditPanel:InsertThumbnail -- 새로운 썸네일을 정렬된 위치에 삽입
DeckEditPanel:RemoveThumbnail -- 썸네일을 배열에서 제거하고 앵커를 파괴
DeckEditPanel:SpawnAndAttachToAnchor -- 썸네일용 앵커를 생성하고 썸네일을 앵커에 부착
DeckEditPanel:SpawnAnchor -- 썸네일을 위한 앵커 엔티티를 생성
DeckEditPanel:DestroyAnchor -- 썸네일의 앵커와 관련 트위너들을 파괴
DeckEditPanel:DropAnchors -- 모든 앵커들을 그리드 위치에 배치하고 애니메이션 적용
DeckEditPanel:Put -- 카드를 덱에 추가하고 덱 크기를 업데이트
DeckEditPanel:Erase -- 카드를 덱에서 제거하고 덱 크기를 업데이트
DeckEditPanel:SetDeckSize -- 현재 덱 크기를 계산하여 UI에 표시하고 색상을 설정
DeckMenu:OnBeginPlay -- 덱 메뉴 초기화 시 경고 사인을 생성하고 좌우 화살표 버튼 이벤트를 연결하며 덱 상태 이벤트들을 연결
DeckMenu:SetButtonsEnable -- 덱 메뉴의 버튼들의 활성화 상태를 설정
DeckMenu:ShowArrowButtons -- 좌우 화살표 버튼들을 화면에 표시하는 애니메이션을 실행
DeckMenu:HideArrowButtons -- 좌우 화살표 버튼들을 화면에서 숨김
DeckPanel:OnBeginPlay -- 덱 패널 초기화 시 덱 메뉴를 생성하고 각 직업별 덱 생성 터치 이벤트를 연결
DeckPanel:Open -- 덱 패널을 열고 화면에 표시하는 애니메이션을 실행
DeckPanel:Close -- 덱 패널을 닫고 화면에서 숨김
DeckPanel:SetButtonsEnable -- 덱 패널의 버튼들의 활성화 상태를 설정 (현재 구현 없음)
DuelModule:OnBeginPlay -- 듀얼 모듈 초기화 시 카드, 상점, 돌아가기 버튼 이벤트를 연결하고 오픈 이벤트를 설정
DuelModule:Open -- 듀얼 모듈 메뉴를 열고 화면에 표시하는 애니메이션을 실행하며 오픈 이벤트를 표시
DuelModule:Close -- 듀얼 모듈 메뉴를 닫고 화면에서 숨기는 애니메이션을 실행
DuelModule:SetButtonsEnable -- 듀얼 모듈의 모든 버튼들의 활성화 상태를 설정
DuelModule:ShowOpenEvent -- 오픈 이벤트 기간과 카드팩 수량을 확인하여 이벤트 UI 표시 여부를 결정
EmoteModule:OnBeginPlay -- 이모트 모듈 초기화 시 이모트 이미지들을 설정하고 터치 이벤트를 연결하여 원형 이모트 선택 처리
EmoteModule:Open -- 이모트 패널을 열고 플레이어 위치에 표시하는 애니메이션을 실행
EmoteModule:Close -- 이모트 패널을 닫고 화면에서 숨기는 애니메이션을 실행
EmoteModule:SetButtonsEnable -- 이모트 모듈의 터치 영역 활성화 상태를 설정
EventModule:OnBeginPlay -- 이벤트 모듈 초기화 시 출석 슬롯들과 버튼 이벤트들을 연결하고 이벤트 타이머를 설정
EventModule:Open -- 이벤트 모듈을 열고 이벤트 기간에 따라 적절한 모드를 설정
EventModule:Close -- 이벤트 모듈을 닫고 타이머를 정리
EventModule:SetEventButtonEnable -- 이벤트 버튼의 활성화 상태를 설정
EventModule:SetPanelButtonsEnable -- 패널 내 모든 버튼들과 출석 슬롯들의 활성화 상태를 설정
EventModule:Show -- 이벤트 버튼을 화면에 표시
EventModule:Hide -- 이벤트 버튼을 화면에서 숨김
EventModule:SetMode -- 이벤트 모드를 설정하고 특별 이벤트, 핫타임, 원작 월드 이벤트 모드에 따라 UI를 전환
EventModule:ReceiveCardPacksBySpecialEvent -- 특별 이벤트 출석 보상을 수령하고 UI를 업데이트
FriendlyMatchModule:OnBeginPlay -- 친선전 모드 시작 시 덱 메뉴 UI 컴포넌트를 생성하고 초기화
FriendlyMatchModule:SetButtonsEnable -- 친선전 모드의 덱 메뉴 버튼들의 활성화 상태를 설정
FriendSlot:OnBeginPlay -- 친구 슬롯 초기화 시 삭제 및 팔로우 버튼 이벤트를 연결하고 친구 삭제 이벤트를 연결
FriendSlot:SetFriendOnline -- 온라인 친구의 정보를 설정하고 랭크와 위치 정보를 표시
FriendSlot:SetFriendOffline -- 오프라인 친구의 정보를 설정하고 오프라인 상태로 표시
FriendSlot:Clear -- 친구 슬롯의 모든 정보를 초기화
FriendSlot:SetButtonsEnable -- 친구 슬롯의 버튼들의 활성화 상태를 설정
GuideModule:OnBeginPlay -- 가이드 모듈 초기화 시 가이드, X, 컨트롤, How 버튼 이벤트들을 연결
GuideModule:Open -- 가이드 모듈을 열고 컨트롤 모드로 설정
GuideModule:Close -- 가이드 모듈을 닫고 모든 메뉴를 숨김
GuideModule:SetMode -- 가이드 모드를 설정하고 컨트롤 또는 How 모드에 따라 UI를 전환
GuideModule:SetGuideButtonEnable -- 가이드 버튼의 활성화 상태를 설정
GuideModule:SetPanelButtonsEnable -- 패널 내 모든 버튼들의 활성화 상태를 설정
HowMenu:OnBeginPlay -- How 메뉴 초기화 시 컨텐츠 엔티티들을 설정하고 화살표 버튼 이벤트를 연결
HowMenu:Open -- How 메뉴를 열고 화살표 버튼들과 첫 번째 컨텐츠를 표시
HowMenu:Close -- How 메뉴를 닫고 모든 UI를 숨김
HowMenu:SetButtonsEnable -- 화살표 버튼들의 활성화 상태를 설정
HowMenu:ShowArrowButtons -- 화살표 버튼들을 화면에 표시하는 애니메이션
HowMenu:HideArrowButtons -- 화살표 버튼들을 화면에서 숨김
HowMenu:ShowContent -- 지정된 페이지의 컨텐츠를 표시
HowMenu:HideContent -- 모든 컨텐츠를 숨김
InteractionModule:OnBeginPlay -- 상호작용 모듈 초기화 시 취소 및 친구 버튼 이벤트를 연결
InteractionModule:Open -- 상호작용 모듈을 열고 다른 캐릭터의 정보를 표시
InteractionModule:Close -- 상호작용 모듈을 닫고 모든 상태를 초기화
InteractionModule:SetButtonsEnable -- 상호작용 모듈의 버튼들의 활성화 상태를 설정
InteractionModule:SetFriendButton -- 친구 상태에 따라 친구 버튼의 모양과 텍스트를 설정
LobbyModule:OnBeginPlay -- 로비 모듈 초기화 시 카드, 상점, 방 채널, 연습 버튼 이벤트들을 연결하고 오픈 이벤트를 설정
LobbyModule:Open -- 로비 메뉴를 열고 화면에 표시하는 애니메이션을 실행하며 오픈 이벤트를 표시
LobbyModule:Close -- 로비 메뉴를 닫고 화면에서 숨김
LobbyModule:SetButtonsEnable -- 로비 모듈의 모든 버튼들의 활성화 상태를 설정
LobbyModule:ShowOpenEvent -- 오픈 이벤트 기간과 카드팩 수량을 확인하여 이벤트 UI 표시 여부를 결정
LocationModule:SetLobby -- 로비 위치 정보를 설정하여 현재 채널 번호를 표시
LocationModule:SetRankedMatch -- 랭크 매치 위치 정보를 설정하여 텍스트 표시
LocationModule:SetFriendlyMatch -- 친선전 위치 정보를 설정하여 현재 방 번호를 표시
LocationModule:SetPractice -- 연습 모드 위치 정보를 설정하여 텍스트 표시
LocationModule:SetTutorial -- 튜토리얼 위치 정보를 설정하여 텍스트 표시
MesoModule:OnBeginPlay -- 메소 모듈 초기화 시 플레이어 메소 변경 이벤트를 연결하고 UI 업데이트
NoticeModule:OnBeginPlay -- 공지사항 모듈 초기화 시 공지사항 버튼 클릭 이벤트를 연결하고 언어별 공지 페이지를 설정
NoticeModule:SetButtonsEnable -- 공지사항 버튼의 활성화 상태를 설정
NoticeModule:Show -- 공지사항 버튼을 화면에 표시하는 애니메이션을 실행
NoticeModule:Hide -- 공지사항 버튼을 화면에서 숨기는 애니메이션을 실행
PlayerModule:OnBeginPlay -- 플레이어 모듈 초기화 시 항복 버튼 클릭 이벤트를 연결하고 듀얼 종료 처리
PlayerModule:Open -- 플레이어 메뉴를 열고 화면에 표시하는 애니메이션을 실행
PlayerModule:Close -- 플레이어 메뉴를 닫고 화면에서 숨김
PlayerModule:SetButtonsEnable -- 플레이어 모듈의 버튼들의 활성화 상태를 설정
PlayMeso:Initialize -- 게임 플레이로 획득한 메소 정보를 초기화하고 UI 표시 상태를 설정
PopupModule:OnBeginPlay -- 팝업 모듈 초기화 시 환불 정보 버튼 이벤트를 연결
PopupModule:SetButtonsEnable -- 팝업 모듈의 버튼들의 활성화 상태를 설정
PopupModule:Open -- 팝업을 열고 메시지와 버튼 설정에 따라 UI를 구성
PopupModule:Close -- 팝업을 닫고 모든 상태를 초기화
PopupModule:ShowBanMessage -- 밴 메시지를 표시하고 채팅을 비활성화
PracticeModule:OnBeginPlay -- 연습 모드 시작 시 덱 메뉴 UI 컴포넌트를 생성하고 초기화
PracticeModule:SetButtonsEnable -- 연습 모드의 덱 메뉴 버튼들의 활성화 상태를 설정
RankedMatchModule:OnBeginPlay -- 랭크 매치 모듈 초기화 및 이벤트 연결
RankedMatchModule:SetButtonsEnable -- 랭크 매치 관련 버튼들의 활성화 상태 설정
RankedMatchModule:SetMatching -- 매칭 상태에 따라 UI 요소들의 표시 상태 변경
RankedPlayMeso:Initialize -- 랭크 플레이 메소 보상 정보 초기화
RankedWinMeso:Initialize -- 랭크 승리 메소 보상 정보 초기화
RankingModule:OnBeginPlay -- 랭킹 모듈 초기화 및 이벤트 연결
RankingModule:Open -- 랭킹 모듈 열기 및 랭킹 정보 요청
RankingModule:Close -- 랭킹 모듈 닫기
RankingModule:SetButtonsEnable -- 랭킹 모듈 버튼들의 활성화 상태 설정
RankingModule:ShowRanking -- 지정된 페이지의 랭킹 정보 표시
RankingModule:SetRankingInfos -- 랭킹 정보 배열 설정
RankingSlot:Initialize -- 랭킹 슬롯 정보 초기화
RankMeso:Initialize -- 랭크 메소 보상 정보 초기화
RankPoint:Initialize -- 랭크 포인트 변화량 정보 초기화
RewardModule:OnBeginPlay -- 보상 모듈 초기화 및 이벤트 연결
RewardModule:Open -- 보상 모듈 열기
RewardModule:Close -- 보상 모듈 닫기
RewardModule:SetRewardButtonEnable -- 보상 버튼의 활성화 상태 설정
RewardModule:SetPanelButtonsEnable -- 보상 패널 버튼들의 활성화 상태 설정
RewardModule:SetMode -- 보상 모드 전환 (일일/랭크)
RewardModule:ShowDailyRewards -- 일일 보상 목록 표시
RewardModule:ShowRankRewards -- 랭크 보상 목록 표시
RewardModule:Show -- 보상 버튼 표시
RewardModule:Hide -- 보상 버튼 숨기기
RewardSlot:SetDailyReward -- 일일 보상 정보 설정
RewardSlot:SetRankReward -- 랭크 달성 보상 정보 설정
RoomButton:OnBeginPlay -- 룸 버튼 초기화 및 클릭 이벤트 연결
RoomButton:SetRoom -- 룸 정보 설정 및 UI 업데이트
RoomChannelModule:OnBeginPlay -- 룸/채널 모듈 초기화 및 이벤트 연결
RoomChannelModule:Open -- 룸/채널 모듈 열기
RoomChannelModule:Close -- 룸/채널 모듈 닫기
RoomChannelModule:SetButtonsEnable -- 룸/채널 모듈 버튼들의 활성화 상태 설정
RoomChannelModule:SetMode -- 룸/채널 모드 전환
RoomMenu:OnBeginPlay -- 룸 메뉴 초기화 및 이벤트 연결
RoomMenu:Open -- 룸 목록 요청 및 열기
RoomMenu:Close -- 룸 목록 닫기
RoomMenu:SetButtonsEnable -- 룸 목록 버튼들의 활성화 상태 설정
RoomMenu:ShowArrowButtons -- 화살표 버튼 표시
RoomMenu:HideArrowButtons -- 화살표 버튼 숨기기
RoomMenu:ShowRoomButtons -- 지정된 페이지의 룸 버튼들 표시
RoomMenu:HideRoomButtons -- 모든 룸 버튼 숨기기
ShopModule:OnBeginPlay -- 상점 모듈 초기화 및 이벤트 연결
ShopModule:Open -- 상점 모듈 열기
ShopModule:Close -- 상점 모듈 닫기
ShopModule:SetButtonsEnable -- 상점 모듈 버튼들의 활성화 상태 설정
ShopPanel:OnBeginPlay -- 상점 패널 초기화 및 이벤트 연결
ShopPanel:Open -- 상점 패널 열기
ShopPanel:Close -- 상점 패널 닫기
ShopPanel:SetButtonsEnable -- 상점 패널 버튼들의 활성화 상태 설정
ShopPanel:SetLeftTabMode -- 왼쪽 탭 모드 설정
ShopPanel:SetTopTabMode -- 상단 탭 모드 설정
SocialModule:OnBeginPlay -- 소셜 모듈 초기화 및 이벤트 연결
SocialModule:Open -- 소셜 모듈 열기
SocialModule:Close -- 소셜 모듈 닫기
SocialModule:SetSocialButtonEnable -- 소셜 버튼의 활성화 상태 설정
SocialModule:SetPanelButtonsEnable -- 소셜 패널 버튼들의 활성화 상태 설정
SocialModule:SetPopupButtonsEnable -- 소셜 팝업 버튼들의 활성화 상태 설정
SocialModule:ShowPopup -- 친구 요청 팝업 표시
SocialModule:HidePopup -- 친구 요청 팝업 숨기기
SocialModule:ShowFriendSlots -- 친구 목록 슬롯 표시
ToastModule:ShowMessage -- 토스트 메시지 표시
ToastModule:Clear -- 토스트 메시지 제거
TutorialModule:OnBeginPlay -- 튜토리얼 모듈 초기화 및 이벤트 연결
TutorialModule:Open -- 튜토리얼 모듈 열기
TutorialModule:Close -- 튜토리얼 모듈 닫기
TutorialModule:SetButtonsEnable -- 튜토리얼 모듈 버튼들의 활성화 상태 설정
DateTime:OnBeginPlay -- 로직 초기화 시 시간 오프셋을 0으로 설정
DateTime:KtcNow -- 현재 UTC 시간에 한국 시간대(+9)와 오프셋을 적용하여 반환
DateTime:KtcNowDays -- 한국 시간 기준으로 총 일수를 계산하여 반환
DateTime:SetKtcNow -- 한국 시간을 지정된 시간으로 설정
DateTime:ResetKtcNow -- 시간 오프셋을 0으로 초기화
Effect:GetLayerOptions -- 이팩트 레이어 옵션을 설정하여 반환
Effect:GetUnitLayerOptions -- 유닛 레이어에 맞는 이팩트 옵션을 반환
Effect:SpawnEffect -- 이팩트 엔티티를 생성하고 반환
Effect:PlayEffect -- 이팩트를 재생하며 페이드 인/아웃 및 스케일 아웃 옵션 지원
Effect:MoveEffect -- 이팩트를 생성하여 지정된 경로로 이동시키는 애니메이션
Effect:MoveAndSpinEffect -- 이팩트를 이동과 동시에 회전시키는 애니메이션
Effect:ThrowEffect -- 이팩트를 던지는 듯한 애니메이션으로 이동시키며 방향에 따라 회전
Effect:PlaySkillEffect -- 유닛의 스킬 이팩트를 재생하며 유닛 방향에 따라 조정
Effect:PlaySkillEffectAttached -- 유닛에 부착된 스킬 이팩트를 재생하고 이팩트 ID를 반환
Effect:PlayHitEffect -- 공격자와 피격자 사이에 히트 이팩트를 재생
Effect:PlayHitEffectAttached -- 유닛에 부착된 히트 이팩트를 재생하며 공격자 방향에 따라 조정
Event:BuyCard -- 카드 구매 이벤트를 생성하여 반환
Event:Unfriend -- 친구 삭제 이벤트를 생성하여 반환
Event:SellCard -- 카드 판매 이벤트를 생성하여 반환
Event:GetChannels -- 채널 목록 조회 이벤트를 생성하여 반환
Event:GetFriendlyMatchRooms -- 친선 경기 방 목록 조회 이벤트를 생성하여 반환
Event:SetRoom -- 방 설정 이벤트를 생성하여 반환
Event:GetFriends -- 친구 목록 조회 이벤트를 생성하여 반환
Matching:GetOrCreateLeaderBoard -- 랭크 매치용 리더보드를 가져오거나 새로 생성
Math:Atan2 -- 2차원 좌표계에서 원점으로부터의 각도를 라디안으로 계산
MSON:FastAnyToString -- 임의의 값을 JSON 방식으로 빠르게 문자열로 변환
MSON:FastStringToAny -- JSON 문자열을 빠르게 파싱하여 임의의 값으로 변환
MSON:AnyToString -- 임의의 값을 MSON 형식의 문자열로 변환 (사용자 데이터 타입 지원)
MSON:StringToAny -- MSON 형식의 문자열을 파싱하여 임의의 값으로 변환
MSON:GetUserDataType -- 사용자 데이터의 타입 이름을 추출하여 반환
MSON:ReadEmpty -- 공백 문자(스페이스, 탭, 개행)를 건너뛰어 다음 유효한 문자로 이동
MSON:ReadNil -- 'nil' 문자열을 파싱하여 nil 값으로 변환
MSON:ReadBoolean -- 'true' 또는 'false' 문자열을 파싱하여 불리언 값으로 변환
MSON:ReadNumber -- 숫자 문자열을 파싱하여 숫자 값으로 변환
MSON:ReadString -- 따옴표로 둘러싸인 문자열을 파싱하여 문자열 값으로 변환
MSON:ReadUserData -- 'userdata' 키워드로 시작하는 사용자 데이터를 파싱하여 객체로 변환
MSON:ReadTable -- 중괄호로 둘러싸인 테이블을 파싱하여 테이블 객체로 변환
MSON:ReadArray -- 대괄호로 둘러싸인 배열을 파싱하여 배열 객체로 변환
MSON:ReadAny -- 현재 위치에서 적절한 파싱 메소드를 선택하여 임의의 값으로 변환
Queue:Initialize -- 큐 자료구조를 초기화
Queue:Push -- 큐의 끝에 요소를 추가
Queue:Pop -- 큐의 첫 번째 요소를 제거하고 반환
Queue:Back -- 큐의 마지막 요소를 반환 (제거하지 않음)
Queue:Front -- 큐의 첫 번째 요소를 반환 (제거하지 않음)
Resource:GetTotalDelay -- 애니메이션의 전체 재생 시간을 계산하여 반환
Resource:GetStartFrameDelay -- 애니메이션 첫 번째 프레임의 지연 시간을 반환
Resource:GetEndFrameDelay -- 애니메이션 마지막 프레임의 지연 시간을 반환
Screen:PlayEffect -- 화면 전체에 이팩트를 재생하고 ID를 반환
Screen:GetZoomRatio -- 화면 비율과 플랫폼에 따른 줄 비율을 계산
Server:Request -- 클라이언트에서 서버로 메소드 호출 요청을 전송
Server:Send -- 서버에서 클라이언트 요청을 처리하고 응답을 전송
Server:Respond -- 서버로부터의 응답을 받아 요청 상태를 종료
Server:IsRequesting -- 현재 요청 중인지 확인
Shop:OnBeginPlay -- 샵 시스템 초기화 및 상품 ID 매핑 테이블 설정
Shop:ProcessPurchase -- 결제 요청을 처리하고 카드팩 지급 여부를 반환
Shop:PromptSinglePurchase -- 단일 카드팩 구매 창을 표시
Shop:PromptMultiplePurchase -- 다중 카드팩 구매 창을 표시
Table:Clear -- 테이블의 모든 요소를 제거
Table:ShallowCopy -- 테이블의 얼없은 복사본을 생성하여 반환
Table:DeepCopy -- 테이블의 깊은 복사본을 생성하여 반환 (중첩된 테이블도 재귀적으로 복사)
Table:Shuffle -- Fisher-Yates 알고리즘을 사용하여 배열을 셔플
Table:GetSize -- 테이블의 요소 개수를 반환
Table:IsEmpty -- 테이블이 비어있는지 확인
Table:IsArray -- 테이블이 연속된 인덱스를 가진 배열인지 확인
Table:Assign -- 소스 테이블의 모든 요소를 대상 테이블로 복사
Table:Append -- 소스 배열의 모든 요소를 대상 배열의 끝에 추가
Table:Concat -- 두 배열을 연결한 새로운 배열을 반환
Table:Merge -- 두 테이블을 병합한 새로운 테이블을 반환
Table:Convert -- 테이블의 모든 요소에 지정된 메소드를 적용하여 변환
Table:Contains -- 배열에 지정된 값이 포함되어 있는지 확인
Table:Select -- 선택 조건을 만족하는 요소들만 필터링하여 반환
Table:GetRandomElement -- 배열에서 랜덤한 요소 하나를 반환
Table:GetRandomElements -- 배열에서 중복 가능한 랜덤 요소들을 지정된 개수만큼 반환
Table:GetRandomPermutation -- 배열에서 중복 없는 랜덤 요소들을 지정된 개수만큼 반환
Table:InsertToRandomIndex -- 배열의 랜덤한 위치에 요소를 삽입
Table:Find -- 배열에서 지정된 값의 인덱스를 찾아 반환
Table:Remove -- 배열에서 지정된 값을 처음 발견되는 것만 제거
Table:RemoveAll -- 배열에서 지정된 값을 모두 제거
Table:MaxN -- 테이블에서 가장 큰 숫자 키를 찾아 반환
Table:Unpack -- 테이블을 언팩하여 여러 값으로 반환
Table:Intersection -- 두 배열의 합집을 반환 (중복 제거)
Table:Difference -- 첫 번째 배열에서 두 번째 배열에 있는 요소들을 제거한 차집합을 반환
Table:StableSort -- 삽입 정렬을 사용하여 안정적으로 배열을 정렬
Table:RemoveDuplicates -- 배열에서 중복된 요소들을 제거하고 정렬된 배열을 반환
Table:Compare -- 두 테이블을 재귀적으로 비교하여 동일한지 확인
Tween:Emphasize -- 엔티티를 강조하는 효과를 위해 스케일을 진동시키는 트위닝
Tween:Damp -- 엔티티에 감쇠 효과를 적용하여 스케일을 진동시키는 트위닝
Tween:Twitch -- 엔티티를 경련시키는 효과를 위해 회전을 진동시키는 트위닝
Tween:Spin -- 엔티티를 지정된 각도만큼 회전시키는 트위닝
Tween:MoveTo -- 엔티티를 지정된 위치로 이동시키는 트위닝
Tween:MoveXTo -- 엔티티를 X축으로만 이동시키는 트위닝
Tween:ScaleTo -- 엔티티의 스케일을 지정된 크기로 변경하는 트위닝
Tween:MoveAndRotateTo -- 엔티티를 이동과 동시에 회전시키는 트위닝
Tween:MoveAndSpinTo -- 엔티티를 이동과 동시에 회전시키는 트위닝
Tween:MoveAndScaleTo -- 엔티티를 이동과 동시에 스케일 변경하는 트위닝
Tween:TransformTo -- 엔티티의 위치, 회전, 스케일을 동시에 변경하는 트위닝
Tween:ColorTo -- 엔티티의 색상을 지정된 색상으로 변경하는 트위닝
Tween:Lerp -- 두 엔티티 사이를 선형 보간하여 이동시키는 트위닝
Util:Call -- 컴포넌트의 메소드를 동적으로 호출하고 결과를 반환
Util:RunCoroutine -- 컴포넌트의 메소드를 코루틴으로 실행하고 코루틴 객체를 반환
Util:WaitCoroutines -- 여러 코루틴들이 모두 완료될 때까지 대기
Util:HasAttribute -- 컴포넌트의 메소드가 지정된 속성을 가지고 있는지 확인
Util:GetAttribute -- 컴포넌트의 메소드 속성을 가져와서 반환
Util:GetRandomIntegersRange -- 지정된 범위에서 중복 가능한 랜덤 정수 배열을 생성
Util:GetRandomPermutationRange -- 지정된 범위에서 중복 없는 랜덤 정수 배열을 생성
Util:Restart -- 스프라이트 렌더러를 재시작하여 애니메이션을 초기화
Util:HandleCoroutine -- 코루틴 이벤트를 처리하여 메소드를 실행하고 결과를 저장
Vector2:Lerp -- 두 벡터 사이를 선형 보간하여 새로운 벡터 반환
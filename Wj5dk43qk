# bcj5jdh3i9dbehfu5jeuf9<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>⚔️ 무기 공장 - 멀티플레이어</title>

<style>
* { box-sizing: border-box; margin: 0; padding: 0; }

body {
  font-family: 'Arial', 'Noto Sans KR', sans-serif;
  background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
  color: #fff;
  min-height: 100vh;
  padding: 10px;
}

header {
  text-align: center;
  margin-bottom: 20px;
}

header h1 {
  font-size: 36px;
  background: linear-gradient(45deg, #ff6b6b, #ffd93d, #6bcf7f);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.container {
  max-width: 1600px;
  margin: 0 auto;
}

.main-grid {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 15px;
  margin-bottom: 20px;
}

@media (max-width: 1200px) {
  .main-grid { grid-template-columns: 1fr 1fr; }
}

@media (max-width: 700px) {
  .main-grid { grid-template-columns: 1fr; }
}

.card {
  background: linear-gradient(135deg, rgba(48, 43, 99, 0.8), rgba(30, 27, 60, 0.8));
  border: 2px solid #6bcf7f;
  border-radius: 15px;
  padding: 20px;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
  backdrop-filter: blur(10px);
}

.card h2 {
  font-size: 20px;
  margin-bottom: 15px;
  color: #ffd93d;
  border-bottom: 2px solid #6bcf7f;
  padding-bottom: 10px;
}

.stat-box {
  background: rgba(255, 107, 107, 0.1);
  border: 1px solid #ff6b6b;
  border-radius: 10px;
  padding: 12px;
  margin: 8px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.stat-box span:first-child {
  color: #b9c4d6;
}

.stat-box span:last-child {
  color: #ffd93d;
  font-weight: bold;
  font-size: 18px;
}

button {
  background: linear-gradient(135deg, #ff6b6b, #ffd93d);
  color: #000;
  border: 0;
  border-radius: 8px;
  padding: 10px 15px;
  font-size: 12px;
  font-weight: bold;
  cursor: pointer;
  margin: 5px 0;
  width: 100%;
  transition: all 0.3s;
}

button:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 15px rgba(255, 107, 107, 0.4);
}

button:disabled {
  background: #596273;
  cursor: not-allowed;
}

button.primary { background: linear-gradient(135deg, #6bcf7f, #4ea1ff); }
button.danger { background: linear-gradient(135deg, #ff6b6b, #ff4444); }
button.success { background: linear-gradient(135deg, #6bcf7f, #00ff88); }

.mine {
  height: 150px;
  background: linear-gradient(135deg, #ff6b6b, #ffd93d);
  border-radius: 12px;
  position: relative;
  overflow: hidden;
  margin: 15px 0;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 60px;
  transition: all 0.2s;
}

.mine:hover {
  transform: scale(1.05);
}

.mine:active {
  transform: scale(0.95);
}

.inventory {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(80px, 1fr));
  gap: 8px;
  max-height: 400px;
  overflow-y: auto;
  margin: 15px 0;
}

.inventory::-webkit-scrollbar {
  width: 8px;
}

.inventory::-webkit-scrollbar-track {
  background: rgba(0, 0, 0, 0.3);
  border-radius: 10px;
}

.inventory::-webkit-scrollbar-thumb {
  background: #6bcf7f;
  border-radius: 10px;
}

.item {
  background: linear-gradient(135deg, rgba(100, 100, 150, 0.5), rgba(80, 80, 120, 0.5));
  border: 2px solid #999;
  border-radius: 8px;
  padding: 8px;
  text-align: center;
  cursor: pointer;
  transition: all 0.2s;
  font-size: 24px;
}

.item:hover {
  transform: scale(1.1);
}

.item.selected {
  border-color: #ffd93d;
  background: linear-gradient(135deg, rgba(255, 217, 61, 0.3), rgba(255, 107, 107, 0.3));
  box-shadow: 0 0 15px rgba(255, 217, 61, 0.5);
}

.item.rare-common { border-color: #90ee90; }
.item.rare-uncommon { border-color: #4ea1ff; }
.item.rare-rare { border-color: #ffd93d; }
.item.rare-epic { border-color: #ff6b6b; }
.item.rare-legendary { border-color: #ff00ff; }

.trade-section {
  background: rgba(0, 0, 0, 0.2);
  border: 2px solid #ffd93d;
  border-radius: 12px;
  padding: 15px;
  margin: 15px 0;
}

.modal {
  display: none;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.7);
  z-index: 1000;
  align-items: center;
  justify-content: center;
}

.modal.active {
  display: flex;
}

.modal-content {
  background: linear-gradient(135deg, rgba(48, 43, 99, 0.95), rgba(30, 27, 60, 0.95));
  border: 2px solid #6bcf7f;
  border-radius: 15px;
  padding: 25px;
  max-width: 500px;
  width: 90%;
  max-height: 80vh;
  overflow-y: auto;
}

.modal-content h2 {
  margin-bottom: 15px;
  color: #ffd93d;
}

.input-group {
  margin: 12px 0;
}

.input-group label {
  display: block;
  margin-bottom: 5px;
  color: #ffd93d;
  font-size: 12px;
  font-weight: bold;
}

.input-group input {
  width: 100%;
  padding: 10px;
  border: 1px solid #6bcf7f;
  border-radius: 6px;
  background: rgba(0, 0, 0, 0.3);
  color: #fff;
  font-family: 'Courier New', monospace;
  font-size: 14px;
}

.qr-container {
  text-align: center;
  margin: 15px 0;
  background: rgba(255, 255, 255, 0.1);
  padding: 15px;
  border-radius: 10px;
}

.trade-box {
  background: rgba(0, 0, 0, 0.3);
  border: 1px solid #6bcf7f;
  border-radius: 8px;
  padding: 12px;
  margin: 10px 0;
  font-size: 12px;
}

.trade-box.your-item {
  border-color: #ffd93d;
}

.trade-box.friend-item {
  border-color: #ff6b6b;
}

.close-btn {
  position: absolute;
  top: 10px;
  right: 15px;
  background: #ff6b6b;
  width: 35px;
  height: 35px;
  padding: 0;
  border-radius: 50%;
  font-size: 18px;
  cursor: pointer;
}

.log {
  max-height: 200px;
  overflow-y: auto;
  background: rgba(0, 0, 0, 0.3);
  border-radius: 8px;
  padding: 10px;
  font-size: 11px;
  margin-top: 10px;
}

.log-entry {
  padding: 5px;
  border-left: 3px solid #6bcf7f;
  margin: 5px 0;
  color: #b9c4d6;
}

.upgrade-system {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 8px;
  margin: 10px 0;
}

.upgrade-btn {
  background: linear-gradient(135deg, #ffd93d, #ff6b6b);
  padding: 8px !important;
  font-size: 11px !important;
}

.exchange-buttons {
  display: flex;
  gap: 8px;
  margin: 10px 0;
}

.exchange-buttons button {
  flex: 1;
  padding: 12px;
  font-size: 16px;
  font-weight: bold;
}

.x-button { background: linear-gradient(135deg, #ff6b6b, #ff4444); }
.o-button { background: linear-gradient(135deg, #6bcf7f, #00ff88); }

.room-status {
  background: rgba(107, 207, 127, 0.1);
  border: 2px solid #6bcf7f;
  border-radius: 8px;
  padding: 12px;
  margin: 10px 0;
  text-align: center;
}

.room-status.active {
  background: rgba(107, 207, 127, 0.2);
  border-color: #00ff88;
}

.tabs {
  display: flex;
  gap: 5px;
  margin-bottom: 15px;
  flex-wrap: wrap;
}

.tabs button {
  flex: 1;
  min-width: 80px;
  padding: 8px;
  font-size: 11px;
}

.tabs button.active {
  background: linear-gradient(135deg, #ffd93d, #ff6b6b) !important;
}
</style>
</head>
<body>

<header>
  <h1>⚔️ 무기 공장 - 멀티플레이어</h1>
</header>

<div class="container">
  <div class="main-grid">
    
    <!-- 채굴 & 통계 -->
    <div class="card">
      <h2>⛏️ 채굴소</h2>
      <div class="stat-box">
        <span>💰 골드</span>
        <span id="goldAmount">0</span>
      </div>
      <div class="stat-box">
        <span>🪨 광석</span>
        <span id="oreAmount">0</span>
      </div>
      <div class="stat-box">
        <span>📦 상자</span>
        <span id="boxCount">0/100</span>
      </div>
      <div class="mine" onclick="mineOre()">⛏️</div>
      <button onclick="craftWeapon()">상자 열기 (1💰)</button>
      <div class="upgrade-system">
        <button class="upgrade-btn" onclick="upgradeRate()" id="rateUpBtn">생산량⬆️</button>
        <button class="upgrade-btn" onclick="upgradeSpeed()" id="speedUpBtn">속도⬆️</button>
        <button class="upgrade-btn" onclick="upgradeOre()" id="oreUpBtn">채굴력⬆️</button>
      </div>
      <div class="log" id="actionLog"></div>
    </div>

    <!-- 인벤토리 -->
    <div class="card">
      <h2>🎒 보유 무기</h2>
      <div class="stat-box">
        <span>무기 수</span>
        <span id="weaponCount">0</span>
      </div>
      <div id="selectedInfo" style="color: #ffd93d; font-size: 12px; margin: 8px 0;">무기를 선택하세요</div>
      <div class="inventory" id="weaponInventory"></div>
      <button class="danger" onclick="sellSelectedWeapon()">선택 판매 💰</button>
      <button class="success" onclick="sellAllWeapons()">전부 판매 💰</button>
    </div>

    <!-- 멀티플레이어 방 -->
    <div class="card">
      <h2>🎮 멀티플레이어</h2>
      <div class="room-status" id="roomStatus">
        <div style="color: #b9c4d6; font-size: 11px;">온라인 상태: <span id="roomStatusText">대기중</span></div>
      </div>
      <button class="primary" onclick="openCreateRoom()">방 만들기</button>
      <button class="primary" onclick="openJoinRoom()">방 입장</button>
      
      <div id="tradeSection" class="trade-section" style="display: none;">
        <h3 style="margin-bottom: 10px; font-size: 14px;">🔄 무기 교환</h3>
        <div id="tradeInfo" style="font-size: 11px; color: #b9c4d6; margin: 8px 0;"></div>
        
        <div class="exchange-buttons">
          <button class="x-button" onclick="selectTradeType('x')">❌ 제안 거절</button>
          <button class="o-button" onclick="selectTradeType('o')">⭕ 제안 동의</button>
        </div>
        
        <div id="yourTradeWeapon" class="trade-box your-item">
          📦 내 무기 선택
        </div>
        <button onclick="selectTradeWeapon()" style="padding: 8px; font-size: 11px;">내 무기 선택</button>
        
        <div id="friendTradeWeapon" class="trade-box friend-item">
          📦 상대방 무기 대기중
        </div>
        
        <button class="success" onclick="confirmTrade()" style="margin-top: 10px;">✅ 교환 완료</button>
        <button class="danger" onclick="cancelTrade()" style="margin-top: 5px;">취소</button>
      </div>
    </div>

  </div>
</div>

<!-- 방 만들기 모달 -->
<div class="modal" id="createRoomModal">
  <div class="modal-content">
    <button class="close-btn" onclick="closeModal('createRoomModal')">×</button>
    <h2>🎮 새로운 방 만들기</h2>
    
    <div class="input-group">
      <label>플레이어 이름</label>
      <input type="text" id="playerName" placeholder="이름 입력" maxlength="20">
    </div>
    
    <button onclick="createRoom()" style="margin-top: 15px;">방 만들기</button>
    
    <div id="roomCodeDisplay" style="display: none; margin-top: 20px;">
      <h3 style="color: #ffd93d; margin-bottom: 10px;">✅ 방이 생성되었습니다!</h3>
      
      <div class="input-group">
        <label>방 코드 (친구에게 공유)</label>
        <input type="text" id="roomCode" readonly>
        <button onclick="copyRoomCode()" style="background: linear-gradient(135deg, #4ea1ff, #6bcf7f); margin-top: 5px;">📋 복사</button>
      </div>
      
      <div class="qr-container">
        <div style="font-size: 12px; margin-bottom: 10px;">📱 또는 QR 코드 스캔</div>
        <div id="qrCode"></div>
      </div>
      
      <div id="waitingMessage" style="color: #ffd93d; text-align: center; margin-top: 10px; font-size: 12px;">
        친구가 입장할 때까지 대기중... (새로고침 필요 없음)
      </div>
    </div>
  </div>
</div>

<!-- 방 입장 모달 -->
<div class="modal" id="joinRoomModal">
  <div class="modal-content">
    <button class="close-btn" onclick="closeModal('joinRoomModal')">×</button>
    <h2>🚪 방 입장</h2>
    
    <div class="input-group">
      <label>플레이어 이름</label>
      <input type="text" id="joinPlayerName" placeholder="이름 입력" maxlength="20">
    </div>
    
    <div class="input-group">
      <label>방 코드 (6자리 숫자)</label>
      <input type="text" id="joinRoomCode" placeholder="000000" maxlength="6">
    </div>
    
    <button onclick="joinRoom()" style="margin-top: 15px;">입장하기</button>
  </div>
</div>

<script>
// 무기 데이터 (추가됨)
const allWeapons = [
  // 일반
  { name: '나무 검', emoji: '🔱', rarity: 'common', value: 5, weight: 30 },
  { name: '돌 도끼', emoji: '🪨', rarity: 'common', value: 8, weight: 25 },
  { name: '나뭇가지', emoji: '🌿', rarity: 'common', value: 3, weight: 20 },
  { name: '쇠망치', emoji: '🔨', rarity: 'uncommon', value: 15, weight: 20 },
  { name: '창', emoji: '🔱', rarity: 'uncommon', value: 12, weight: 18 },
  { name: '활', emoji: '🏹', rarity: 'uncommon', value: 14, weight: 16 },
  
  // 레어
  { name: '강철 검', emoji: '⚔️', rarity: 'rare', value: 30, weight: 15 },
  { name: '황금 도끼', emoji: '🪓', rarity: 'rare', value: 35, weight: 12 },
  { name: '마법 지팡이', emoji: '🪄', rarity: 'rare', value: 32, weight: 14 },
  { name: '카타나', emoji: '⚔️', rarity: 'rare', value: 38, weight: 13 },
  { name: '양손검', emoji: '⚔️', rarity: 'rare', value: 40, weight: 11 },
  { name: '궁수의 활', emoji: '🏹', rarity: 'rare', value: 36, weight: 10 },
  
  // 에픽
  { name: '불의 검', emoji: '🔥', rarity: 'epic', value: 60, weight: 8 },
  { name: '얼음 창', emoji: '❄️', rarity: 'epic', value: 65, weight: 7 },
  { name: '번개 망치', emoji: '⚡', rarity: 'epic', value: 70, weight: 6 },
  { name: '독 검', emoji: '☠️', rarity: 'epic', value: 62, weight: 8 },
  { name: '빛의 검', emoji: '✨', rarity: 'epic', value: 68, weight: 7 },
  { name: '어두운 낫', emoji: '🌑', rarity: 'epic', value: 64, weight: 7 },
  
  // 레전드
  { name: '엑스칼리버', emoji: '👑', rarity: 'legendary', value: 150, weight: 3 },
  { name: '신의 망치', emoji: '⚡👑', rarity: 'legendary', value: 180, weight: 2 },
  { name: '흑룡의 검', emoji: '🐉', rarity: 'legendary', value: 170, weight: 3 },
  { name: '카리스마', emoji: '💎', rarity: 'legendary', value: 160, weight: 3 },
  { name: '무한의 검', emoji: '∞', rarity: 'legendary', value: 200, weight: 1 },
  { name: '시간의 검', emoji: '⏳', rarity: 'legendary', value: 190, weight: 2 },
  { name: '천사의 검', emoji: '😇', rarity: 'legendary', value: 175, weight: 3 },
  { name: '악마의 검', emoji: '😈', rarity: 'legendary', value: 185, weight: 2 },
  { name: '태양의 창', emoji: '☀️', rarity: 'legendary', value: 165, weight: 3 },
  { name: '달의 활', emoji: '🌙', rarity: 'legendary', value: 155, weight: 4 },
  
  // 추가 무기들
  { name: '검객의 검', emoji: '🗡️', rarity: 'rare', value: 42, weight: 10 },
  { name: '전사의 도끼', emoji: '🪓', rarity: 'epic', value: 72, weight: 6 },
  { name: '신비한 지팡이', emoji: '🪄', rarity: 'rare', value: 40, weight: 12 },
  { name: '마법사의 홀', emoji: '🔮', rarity: 'epic', value: 75, weight: 5 },
  { name: '거대 칼날', emoji: '⚔️', rarity: 'epic', value: 78, weight: 5 },
  { name: '던전 마스터의 검', emoji: '👑', rarity: 'legendary', value: 195, weight: 2 },
  { name: '용사의 검', emoji: '🗡️', rarity: 'epic', value: 76, weight: 6 },
  { name: '전설적 활', emoji: '🏹', rarity: 'legendary', value: 158, weight: 4 },
];

// 게임 데이터
let gameData = {
  gold: 0,
  ore: 0,
  boxes: 0,
  weapons: [],
  selectedWeapon: null,
  rate: 0.1,
  seconds: 5,
  rateLevel: 0,
  speedLevel: 0,
  oreLevel: 0,
  orePerMine: 1,
  sortType: 'item',
  playerName: '',
  roomCode: null,
  isHost: false,
  tradingWith: null,
  selectedTradeWeapon: null,
  tradeType: null, // 'x' or 'o'
};

let productionTimer = null;
let tradeState = {
  yourWeapon: null,
  friendWeapon: null,
  friendName: '',
  yourTradeType: null,
  friendTradeType: null,
  matched: false,
};

// 로컬 스토리지
function loadData() {
  const saved = localStorage.getItem('weaponFactoryData');
  if (saved) {
    gameData = { ...gameData, ...JSON.parse(saved) };
  }
  updateUI();
}

function saveData() {
  localStorage.setItem('weaponFactoryData', JSON.stringify({
    gold: gameData.gold,
    ore: gameData.ore,
    boxes: gameData.boxes,
    weapons: gameData.weapons,
    rate: gameData.rate,
    seconds: gameData.seconds,
    rateLevel: gameData.rateLevel,
    speedLevel: gameData.speedLevel,
    oreLevel: gameData.oreLevel,
    orePerMine: gameData.orePerMine,
    playerName: gameData.playerName,
  }));
}

// ===================== 채굴 =====================
function mineOre() {
  gameData.ore += gameData.orePerMine;
  if (gameData.ore >= 10) {
    gameData.gold += Math.floor(gameData.ore / 10);
    gameData.ore %= 10;
  }
  addLog(`🪨 광석 채굴! (${gameData.orePerMine})`);
  updateUI();
}

// ===================== 상자 열기 =====================
function craftWeapon() {
  if (gameData.boxes >= 100) {
    addLog('❌ 상자가 가득 찼습니다 (최대 100개)');
    return;
  }
  if (gameData.gold < 1) {
    addLog('❌ 골드가 부족합니다');
    return;
  }
  
  gameData.gold -= 1;
  gameData.boxes++;
  
  const weapon = getRandomWeapon();
  weapon.id = generateId();
  weapon.obtainedAt = Date.now();
  gameData.weapons.unshift(weapon);
  
  addLog(`🎁 ${weapon.emoji} ${weapon.name} 획득! (${weapon.rarity})`);
  updateUI();
}

function getRandomWeapon() {
  let rand = Math.random() * 100;
  for (const weapon of allWeapons) {
    rand -= weapon.weight;
    if (rand <= 0) return { ...weapon };
  }
  return { ...allWeapons[0] };
}

// ===================== 판매 =====================
function sellSelectedWeapon() {
  const weapon = gameData.weapons.find(w => w.id === gameData.selectedWeapon);
  if (!weapon) {
    addLog('❌ 판매할 무기를 선택하세요');
    return;
  }
  gameData.gold += weapon.value;
  gameData.weapons = gameData.weapons.filter(w => w.id !== weapon.id);
  gameData.selectedWeapon = null;
  addLog(`💰 ${weapon.emoji} ${weapon.name}을 ${weapon.value}G에 판매했습니다!`);
  updateUI();
}

function sellAllWeapons() {
  if (gameData.weapons.length === 0) {
    addLog('❌ 판매할 무기가 없습니다');
    return;
  }
  const total = gameData.weapons.reduce((a, b) => a + b.value, 0);
  const count = gameData.weapons.length;
  gameData.gold += total;
  gameData.weapons = [];
  gameData.selectedWeapon = null;
  gameData.boxes = 0;
  addLog(`💰 무기 ${count}개를 판매해 ${total}G를 얻었습니다!`);
  updateUI();
}

// ===================== 강화 =====================
function upgradeRate() {
  if (gameData.rateLevel >= 5) {
    addLog('❌ 최대 레벨입니다');
    return;
  }
  const cost = 10 * (gameData.rateLevel + 1);
  if (gameData.gold < cost) {
    addLog('❌ 골드가 부족합니다');
    return;
  }
  gameData.gold -= cost;
  gameData.rate += 0.1;
  gameData.rateLevel++;
  addLog(`⬆️ 생산량 증가! (${gameData.rate.toFixed(2)}G/초)`);
  updateUI();
}

function upgradeSpeed() {
  if (gameData.speedLevel >= 5) {
    addLog('❌ 최대 레벨입니다');
    return;
  }
  const cost = 15 * (gameData.speedLevel + 1);
  if (gameData.gold < cost || gameData.seconds <= 2) {
    addLog('❌ 더 이상 강화할 수 없습니다');
    return;
  }
  gameData.gold -= cost;
  gameData.seconds--;
  gameData.speedLevel++;
  clearInterval(productionTimer);
  startProduction();
  addLog(`⚡ 속도 증가! (${gameData.seconds}초)`);
  updateUI();
}

function upgradeOre() {
  if (gameData.oreLevel >= 5) {
    addLog('❌ 최대 레벨입니다');
    return;
  }
  const cost = 8 * (gameData.oreLevel + 1);
  if (gameData.gold < cost) {
    addLog('❌ 골드가 부족합니다');
    return;
  }
  gameData.gold -= cost;
  gameData.orePerMine++;
  gameData.oreLevel++;
  addLog(`🔨 채굴력 증가! (${gameData.orePerMine})`);
  updateUI();
}

// ===================== 자동 생산 =====================
function startProduction() {
  if (productionTimer) clearInterval(productionTimer);
  productionTimer = setInterval(() => {
    gameData.gold += gameData.rate;
    updateUI();
  }, gameData.seconds * 1000);
}

// ===================== 멀티플레이어 =====================
function openCreateRoom() {
  document.getElementById('createRoomModal').classList.add('active');
}

function openJoinRoom() {
  document.getElementById('joinRoomModal').classList.add('active');
}

function closeModal(modalId) {
  document.getElementById(modalId).classList.remove('active');
}

function createRoom() {
  const playerName = document.getElementById('playerName').value.trim();
  if (!playerName) {
    alert('이름을 입력하세요');
    return;
  }
  
  const roomCode = Math.floor(Math.random() * 1000000).toString().padStart(6, '0');
  gameData.playerName = playerName;
  gameData.roomCode = roomCode;
  gameData.isHost = true;
  gameData.tradingWith = null;
  
  // QR 코드 생성 (QR Server API 사용)
  const qrContainer = document.getElementById('qrCode');
  const roomLink = `${window.location.origin}${window.location.pathname}?room=${roomCode}`;
  const qrUrl = `https://api.qrserver.com/v1/create-qr-code/?size=200x200&data=${encodeURIComponent(roomLink)}`;
  
  qrContainer.innerHTML = `<img src="${qrUrl}" alt="QR Code" style="width: 200px; height: 200px; border: 3px solid #6bcf7f; border-radius: 10px;">`;
  
  document.getElementById('roomCode').value = roomCode;
  document.getElementById('roomCodeDisplay').style.display = 'block';
  
  addLog(`🎮 방이 생성되었습니다! 코드: ${roomCode}`);
  saveData();
  updateRoomStatus();
}

function copyRoomCode() {
  const code = document.getElementById('roomCode').value;
  navigator.clipboard.writeText(code).then(() => {
    alert('📋 코드가 복사되었습니다!');
  });
}

function joinRoom() {
  const playerName = document.getElementById('joinPlayerName').value.trim();
  const roomCode = document.getElementById('joinRoomCode').value.trim();
  
  if (!playerName || !roomCode) {
    alert('이름과 방 코드를 입력하세요');
    return;
  }
  
  if (roomCode.length !== 6 || isNaN(roomCode)) {
    alert('올바른 6자리 코드를 입력하세요');
    return;
  }
  
  gameData.playerName = playerName;
  gameData.roomCode = roomCode;
  gameData.isHost = false;
  gameData.tradingWith = `HOST_${roomCode}`;
  
  addLog(`🎮 방 ${roomCode}에 입장했습니다!`);
  closeModal('joinRoomModal');
  saveData();
  updateRoomStatus();
  
  // 방 입장 시 교환 섹션 표시
  document.getElementById('tradeSection').style.display = 'block';
}

function updateRoomStatus() {
  const roomStatus = document.getElementById('roomStatus');
  const roomStatusText = document.getElementById('roomStatusText');
  
  if (gameData.roomCode) {
    roomStatus.classList.add('active');
    roomStatusText.textContent = `${gameData.playerName} (방: ${gameData.roomCode})`;
    document.getElementById('tradeSection').style.display = 'block';
    updateTradeInfo();
  } else {
    roomStatus.classList.remove('active');
    roomStatusText.textContent = '대기중';
    document.getElementById('tradeSection').style.display = 'none';
  }
}

function updateTradeInfo() {
  const info = document.getElementById('tradeInfo');
  if (gameData.isHost) {
    info.textContent = '🔄 호스트 - 친구가 입장할 때까지 대기중...';
  } else {
    info.textContent = `🔄 호스트와 연결됨`;
  }
}

// ===================== 교환 시스템 =====================
function selectTradeType(type) {
  gameData.tradeType = type;
  const yourTradeWeapon = document.getElementById('yourTradeWeapon');
  
  if (type === 'x') {
    yourTradeWeapon.innerHTML = '❌ 제안 거절';
    yourTradeWeapon.style.color = '#ff6b6b';
  } else {
    yourTradeWeapon.innerHTML = '⭕ 제안 동의';
    yourTradeWeapon.style.color = '#6bcf7f';
  }
}

function selectTradeWeapon() {
  if (gameData.tradeType === 'x') {
    addLog('❌ 먼저 ⭕ 동의를 선택하세요');
    return;
  }
  
  const weapon = gameData.weapons.find(w => w.id === gameData.selectedWeapon);
  if (!weapon) {
    addLog('❌ 교환할 무기를 선택하세요');
    return;
  }
  
  gameData.selectedTradeWeapon = weapon.id;
  const yourTradeWeapon = document.getElementById('yourTradeWeapon');
  yourTradeWeapon.innerHTML = `⭕ ${weapon.emoji} ${weapon.name} (${weapon.rarity})`;
  yourTradeWeapon.style.color = '#6bcf7f';
  
  addLog(`📦 교환 대기 무기: ${weapon.emoji} ${weapon.name}`);
}

function confirmTrade() {
  if (gameData.tradeType !== 'o' || !gameData.selectedTradeWeapon) {
    addLog('❌ 제안 동의(⭕)를 선택하고 무기를 선택하세요');
    return;
  }
  
  const weapon = gameData.weapons.find(w => w.id === gameData.selectedTradeWeapon);
  if (!weapon) {
    addLog('❌ 무기를 찾을 수 없습니다');
    return;
  }
  
  // 실제 교환 (로컬에서는 시뮬레이션)
  // 더미 무기로 교환
  const dummyWeapon = getRandomWeapon();
  dummyWeapon.id = generateId();
  
  gameData.weapons = gameData.weapons.filter(w => w.id !== weapon.id);
  gameData.weapons.unshift(dummyWeapon);
  
  addLog(`✅ 교환 성공! ${weapon.emoji} → ${dummyWeapon.emoji}`);
  cancelTrade();
  updateUI();
}

function cancelTrade() {
  gameData.tradeType = null;
  gameData.selectedTradeWeapon = null;
  document.getElementById('yourTradeWeapon').innerHTML = '📦 내 무기 선택';
  document.getElementById('yourTradeWeapon').style.color = '#ffd93d';
  document.getElementById('friendTradeWeapon').innerHTML = '📦 상대방 무기 대기중';
  document.getElementById('friendTradeWeapon').style.color = '#ff6b6b';
}

// ===================== UI 업데이트 =====================
function updateUI() {
  document.getElementById('goldAmount').textContent = gameData.gold.toFixed(2);
  document.getElementById('oreAmount').textContent = gameData.ore;
  document.getElementById('boxCount').textContent = `${gameData.weapons.length}/100`;
  document.getElementById('weaponCount').textContent = gameData.weapons.length;
  
  renderWeapons();
  updateRoomStatus();
  saveData();
}

function renderWeapons() {
  const container = document.getElementById('weaponInventory');
  
  if (gameData.weapons.length === 0) {
    container.innerHTML = '<div style="grid-column: 1/-1; text-align: center; color: #b9c4d6;">📦 무기가 없습니다</div>';
    document.getElementById('selectedInfo').textContent = '무기를 선택하세요';
    return;
  }
  
  container.innerHTML = gameData.weapons.map(weapon => `
    <div class="item rare-${weapon.rarity} ${gameData.selectedWeapon === weapon.id ? 'selected' : ''}" 
         onclick="selectWeapon('${weapon.id}')" title="${weapon.name}">
      ${weapon.emoji}
    </div>
  `).join('');
  
  const selected = gameData.weapons.find(w => w.id === gameData.selectedWeapon);
  if (selected) {
    document.getElementById('selectedInfo').textContent = `✨ ${selected.emoji} ${selected.name} (${selected.rarity} · ${selected.value}G)`;
  }
}

function selectWeapon(id) {
  gameData.selectedWeapon = gameData.selectedWeapon === id ? null : id;
  renderWeapons();
}

function addLog(message) {
  const log = document.getElementById('actionLog');
  const entry = document.createElement('div');
  entry.className = 'log-entry';
  entry.textContent = message;
  log.insertBefore(entry, log.firstChild);
  
  while (log.children.length > 20) {
    log.removeChild(log.lastChild);
  }
}

function generateId() {
  return Math.random().toString(36).substr(2, 9);
}

// ===================== 초기화 =====================
function init() {
  loadData();
  startProduction();
  
  // URL에서 방 코드 확인
  const params = new URLSearchParams(window.location.search);
  if (params.has('room')) {
    const roomCode = params.get('room');
    document.getElementById('joinRoomCode').value = roomCode;
    openJoinRoom();
  }
}

init();
</script>

</body>
</html>

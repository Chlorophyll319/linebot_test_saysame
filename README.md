# LINE Bot - 多功能機器人

一個基於 Node.js 開發的 LINE Bot 機器人，提供匯率查詢、QR 碼生成和美食推薦功能。

## 🚀 功能特色

### 1. 美元匯率查詢
- 輸入 `usd` 即可查詢即時美元對台幣匯率
- 使用 [tw.rter.info](https://tw.rter.info) API 獲取最新匯率資料

### 2. QR 碼生成
- 輸入 `qr` 觸發快速回覆選單
- 提供多種互動選項（匯率查詢、LINE官網連結、postback測試）

### 3. 美食推薦
- 發送位置資訊即可獲得附近美食推薦
- 基於農委會開放資料平台的美食資料
- 自動計算距離並推薦最近的前3家餐廳
- 提供詳細的餐廳資訊（地址、電話、圖片、地圖連結）

## 📋 系統需求

- Node.js 14.0 或更高版本
- LINE Developer Account
- 有效的 LINE Bot Channel

## 🛠 安裝步驟

1. **克隆專案**
   ```bash
   git clone <repository-url>
   cd linebot_test_saysame
   ```

2. **安裝依賴**
   ```bash
   npm install
   ```

3. **環境變數設定**
   在專案根目錄創建 `.env` 檔案：
   ```env
   CHANNEL_ID=your_channel_id
   CHANNEL_SECRET=your_channel_secret
   CHANNEL_ACCESS_TOKEN=your_channel_access_token
   PORT=3000
   DEV=false
   ```

4. **啟動機器人**
   ```bash
   # 開發模式（自動重啟）
   npm run dev
   
   # 生產模式
   npm start
   ```

## 📁 專案結構

```
linebot_test_saysame/
├── commands/           # 命令模組
│   ├── usd.js         # 美元匯率查詢
│   ├── qr.js          # QR 碼快速回覆
│   └── food.js        # 美食推薦
├── templates/          # 訊息模板
│   └── food.js        # 美食卡片模板
├── utils/             # 工具函數
│   └── distance.js    # 距離計算
├── dump/              # 除錯資料輸出
├── index.js           # 主程式入口
├── package.json       # 專案配置
└── README.md          # 專案說明
```

## 🔧 使用方式

### 匯率查詢
1. 在 LINE 中輸入 `usd`
2. 機器人會回傳即時美元匯率

### QR 碼功能
1. 在 LINE 中輸入 `qr`
2. 選擇快速回覆選單中的選項

### 美食推薦
1. 在 LINE 中分享您的位置
2. 機器人會自動推薦附近的前3家餐廳
3. 點擊卡片可查看詳細資訊或開啟地圖

## 🛠 開發說明

### 新增功能
1. 在 `commands/` 目錄下創建新的命令檔案
2. 在 `index.js` 中引入並註冊新命令
3. 重新啟動機器人

### 除錯模式
設定環境變數 `DEV=true` 可啟用除錯模式：
- 錯誤時會將訊息內容輸出到 `dump/` 目錄
- 方便開發時查看訊息格式

### 程式碼風格
專案使用 ESLint 和 Prettier 進行程式碼格式化：
```bash
# 檢查程式碼風格
npm run lint

# 自動修正格式
npm run format
```

## 📚 API 參考

### 外部 API
- **匯率資料**: [tw.rter.info](https://tw.rter.info/capi.php)
- **美食資料**: [農委會開放資料平台](https://data.moa.gov.tw/Service/OpenData/ODwsv/ODwsvTravelFood.aspx)

### 工具函數
- `distance(lat1, lon1, lat2, lon2, unit)`: 計算兩點間距離
  - 參數: 緯度1, 經度1, 緯度2, 經度2, 單位
  - 單位: 'K' (公里), 'N' (海里), 預設 (英里)

## 🐛 常見問題

### Q: 機器人沒有回應？
A: 檢查環境變數是否正確設定，並確認 LINE Bot Channel 狀態正常。

### Q: 美食推薦功能無法使用？
A: 確保發送的是位置訊息，而非文字訊息。

### Q: 匯率查詢失敗？
A: 檢查網路連線，或確認 API 服務是否正常。

## 📄 授權

ISC License

## 🤝 貢獻

歡迎提交 Issue 和 Pull Request！

---

如有任何問題，請聯繫開發團隊。
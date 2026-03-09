# XGEN「接棒未來 揮出夢想」QR Code 取票系統 - 前端專案

![Next.js](https://img.shields.io/badge/Next.js-14.2.7-black?style=for-the-badge&logo=next.js)
![React](https://img.shields.io/badge/React-18-blue?style=for-the-badge&logo=react)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3.3-purple?style=for-the-badge&logo=bootstrap)

這是一個專為 **「接棒未來 揮出夢想」** 活動開發的電子票券領取系統。使用者可以透過此系統選擇身份、填寫領票資訊、進行線上劃位，並最終取得專屬的入場 QR Code。

## 🚀 核心功能 (Core Features)

- **身份驗證與導向**：支援公司行號與個人捐贈者身份區分。
- **即時劃位系統**：串接後端 API 進行即時座位判斷與剩餘票券檢查。
- **動態 QR Code 生成**：根據領票資訊（活動名稱、姓名、座位、票號）即時生成專屬 QR Code。
- **自動化郵件連動**：領票成功後，系統自動觸發後端服務將 QR Code 發送至使用者信箱。
- **完全響應式設計 (RWD)**：特別針對行動裝置優化取票頁面佈局，確保各尺寸設備皆能順暢操作。

## 🛠 技術棧 (Tech Stack)

- **框架**: Next.js 14 (Pages Router)
- **前端工具庫**: React 18, Axios (API 請求)
- **UI 框架**: Bootstrap 5.3.3 (搭配自定義 SCSS/CSS)
- **功能組件**:
  - `qrcode`: 生成 QR Code 數據網址。
  - `qrcode.react`: React 適用的 QR Code 渲染組件。
  - `bootstrap-icons`: 介面圖示。
- **部署**: 串接部署於 Google App Engine (GAE) 的後端 API。

## 📂 專案結構說明 (Project Structure)

```text
/pages
  ├── index.js             # 入口頁面 (線上取票入口)
  ├── company.js           # 身份判斷頁面 (個人/公司)
  ├── newForm.js           # 領票資訊填寫與座位判斷邏輯
  ├── QRCodeGenerator.js   # QR Code 顯示頁面與郵件發送觸發
  ├── record.js            # 領票記錄查詢 (選用)
  ├── home.js              # 備用首頁
  └── customAlert.js       # 自定義彈窗組件
/styles
  └── style.css            # 核心專案佈局與 RWD 樣式
/public
  └── images/              # 活動背景圖與素材
```

## ⚙️ 安裝與運行 (Getting Started)

### 1. 安裝環境需求

確保您的電腦已安裝 [Node.js](https://nodejs.org/) (建議 v18 以上)。

### 2. 安裝依賴

在專案根目錄執行：

```bash
npm install
```

### 3. 本地開發

啟動開發伺服器：

```bash
npm run dev
```

打開網頁瀏覽器並造訪 [http://localhost:3000](http://localhost:3000)。

### 4. 正式環境編譯

```bash
npm run build
npm run start
```

## 🔗 API 串接資訊

目前專案前端連線至以下後端服務：

- **API URL**: `https://qrcode-server-438803.de.r.appspot.com/api/user/`

主要端點：

- `POST /update_data`: 更新領票狀態與餘額。
- `GET /get-ticket-id`: 取得最新票券編號。
- `POST /get-seat-number`: 獲取系統分配之座位。
- `POST /user-send-email`: 觸發郵件發送服務。

---

# 🎟️ XGEN「接棒未來 揮出夢想」QR Code 取票系統

![Next.js](https://img.shields.io/badge/Next.js-14.2.7-black?style=flat-square&logo=next.js)
![Node.js](https://img.shields.io/badge/Node.js-20.16.0-green.svg?style=flat-square&logo=node.js)
![Express](https://img.shields.io/badge/Express-4.19.2-blue.svg?style=flat-square&logo=express)
![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-47A248?style=flat-square&logo=mongodb)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5.3.3-purple?style=flat-square&logo=bootstrap)

本專案是一個完整的 **全棧電子票券領取系統**，專為「接棒未來 揮出夢想」活動開發。系統整合了前端導向式領票流程、後端自動化 QR Code 生成、雲端儲存以及郵件自動化通知功能。

---

## 🚀 系統核心功能 (Core Features)

本系統採前後端分離架構，實現了端對端的票券生命週期管理：

- **🎭 識別碼身份自動辨識**：前端根據使用者輸入之識別碼，自動判斷「個人」或「公司行號」身份，並串接後端 API 取得該身份對應的票券配額、座位與專屬 QR Code 資料。
- **📍 即時劃位與配額檢查**：串接 MongoDB 資料庫，實現即時座位分配與剩餘票券連動檢查。
- **📸 QR Code 生成與雲端託管**：
  - 前端即時生成 QR Code 數據網址。
  - 後端整合 **Cloudinary** 將 QR Code 圖片雲端化儲存，方便追蹤與管理。
- **📧 自動化郵件服務**：透過 `Nodemailer` 與 Gmail API，於領票成功後自動外發電子票券至使用者信箱。
- **📱 完全響應式體驗 (RWD)**：前端採用極簡 UX 設計，確保使用者在行動裝置上也能順暢完成領票與核票流程。

---

## 🛠️ 技術棧 (Tech Stack)

### 前端 (Front-end)

- **核心框架**: Next.js 14 (Pages Router) / React 18
- **樣式工具**: Bootstrap 5.3.3 (自定義 SCSS)
- **功能組件**: Axios, qrcode, qrcode.react, bootstrap-icons

### 後端 (Back-end)

- **運行環境**: Node.js v20.16.0
- **網頁框架**: Express.js
- **資料庫**: MongoDB (Mongoose)
- **安全認證**: Passport.js (JWT & Local Strategy)
- **媒體/服務**: Cloudinary (圖片託管), Nodemailer (郵件服務)

---

## 📂 目錄結構 (Folder Structure)

```text
qrcode-ticket-system/
├── front-end/           # Next.js 前端應用程式 (Port 3000)
│   ├── pages/           # 各功能頁面 (領票、掃碼顯示、記錄)
│   ├── public/          # 靜態活動素材
│   └── styles/          # RWD 核心樣式檔案
├── back-end/            # Node.js / Express 後端伺服器 (Port 8080)
│   ├── config/          # 認證策略與系統設定
│   ├── models/          # MongoDB 資料模型 (User, Record, Area)
│   ├── routes/          # API 路由與業務邏輯
│   ├── server.js        # 伺服器進入點
│   └── transfer.js      # 資料遷移工具
├── .gitignore           # 全域忽略規則 (集中管理)
└── README.md            # 專案總覽 (本檔案)
```

---

## ⚙️ 環境配置 (Environment Variables)

請於 `back-end` 資料夾下建立 `.env` 檔案，並配置以下必要參數：

```env
PORT=8080
MONGODB_CONNECTION=your_mongodb_atlas_uri
PASSPORT_SECRET=your_jwt_secret
cloud_name=your_cloud_name
api_key=your_api_key
api_secret=your_api_secret
user=your_email_address (Gmail)
password=your_app_password
```

## 🔗 API 串接資訊

目前前端應用程式預設連線至以下後端服務（託管於 Google App Engine）：

- **Production API URL**: `https://qrcode-server-438803.de.r.appspot.com/api/user/`

### 主要 API 端點摘要：

| 端點               | 方法   | 說明                   |
| :----------------- | :----- | :--------------------- |
| `/update_data`     | `POST` | 更新領票狀態與餘額連動 |
| `/get-ticket-id`   | `GET`  | 取得系統最新票券編號   |
| `/get-seat-number` | `POST` | 取得系統分配之座位號碼 |
| `/user-send-email` | `POST` | 觸發郵件外發服務       |

---

## 🏃 快速啟動 (Quick Start)

### 1. 安裝所有依賴

請分別進入兩個目錄安裝套件：

```bash
cd front-end && npm install
cd ../back-end && npm install
```

### 2. 同時啟動服務 (開發模式)

建議開啟兩個終端機視窗：

- **前端**: `cd front-end && npm run dev` (瀏覽 `http://localhost:3000`)
- **後端**: `cd back-end && npm start` (預設運行於 `http://localhost:8080`)

---

## 📄 授權協定 (License)

ISC License - 專為 2024「接棒未來 揮出夢想」活動技術整合使用。

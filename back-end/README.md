# 🎟️ QRCODE-SERVER2 | 取票系統後端伺服器

[![Node.js](https://img.shields.io/badge/Node.js-20.16.0-green.svg)](https://nodejs.org/)
[![Express](https://img.shields.io/badge/Express-4.19.2-blue.svg)](https://expressjs.com/)
[![Mongoose](https://img.shields.io/badge/Mongoose-8.7.1-red.svg)](https://mongoosejs.com/)
[![Passport](https://img.shields.io/badge/Passport-JWT%20%2F%20Local-yellow.svg)](http://www.passportjs.org/)

這是一個基於 **Node.js** 與 **Express** 框架開發的 QR Code 取票系統後端服務。本伺服器負責核心的身份驗證、票券生成、QR Code 雲端儲存以及與資料庫（MongoDB）的資料對接工作。

---

## 🚀 核心功能 (Key Features)

- **🔐 身份驗證與安全性**：整合 `Passport.js` 實現 Local 登入與 JWT 認證機制。
- **📸 QR Code 自動化**：
  - 動態生成取票 QR Code。
  - 整合 **Cloudinary** 進行QRCODE圖片託管與處理。
- **📧 自動化郵件系統**：透過 `Nodemailer` 自動發送電子票券郵件。
- **🗄️ 資料庫連線支援**：
  - **MongoDB**：主要業務邏輯與票券記錄儲存。
- **🔄 資料格式轉換**：支援 Base64 QR Code 字串轉檔與雲端同步。

---

## 🛠️ 技術棧 (Tech Stack)

| 分類         | 技術                               |
| :----------- | :--------------------------------- |
| **環境運行** | Node.js (v20.16.0)                 |
| **網頁框架** | Express.js                         |
| **資料庫**   | MongoDB (Mongoose)                 |
| **認證授權** | Passport (JWT & Local), JWT        |
| **媒體處理** | Cloudinary (Image Hosting), qrcode |
| **電子郵件** | Nodemailer                         |
| **模板引擎** | EJS (用於郵件或簡單渲染)           |

---

## 📂 目錄結構 (Folder Structure)

```bash
QRCODE-SERVER2/
├── config/             # 系統設定 (如 Passport 策略)
├── models/             # 資料庫模型 (Mongoose Models)
│   ├── area-model.js    # 區域管理
│   ├── record-model.js  # 取票記錄
│   └── user-model.js    # 使用者資料
├── routes/             # API 路由
│   └── auth_route.js   # 核心身份驗證與業務邏輯
├── server.js           # 伺服器進入點
├── transfer.js         # 資料遷移/轉接邏輯
└── package.json        # 依賴定義
```

---

## ⚙️ 環境配置 (Environment Variables)

請在根目錄建立 `.env` 檔案並填入以下內容：

```env
# Server
PORT=8080

# Database
MONGODB_CONNECTION=your_mongodb_atlas_uri

# JWT & Authentication
PASSPORT_SECRET=your_jwt_secret

# Cloudinary (QR Code Hosting)
cloud_name=your_cloud_name
api_key=your_api_key
api_secret=your_api_secret

# Nodemailer (Email Service)
user=your_email_address
password=your_email_password
```

---

## 🏃 快速啟動 (Quick Start)

1. **安裝依賴**

   ```bash
   npm install
   ```

2. **開發環境運行**
   ```bash
   npm start
   ```
   伺服器預設將運行於 `http://localhost:8080`。

---

## 📡 API 路由概覽 (API Routes Overview)

| 路由                     | 方法   | 說明                         | 認證需求 |
| :----------------------- | :----- | :--------------------------- | :------- |
| `/api/user/login`        | `POST` | 使用者登入並取得 JWT         | ❌       |
| `/api/user/getBufferNum` | `GET`  | 取得剩餘票券/Buffer 區位資訊 | ❌       |
| `/api/user/update_data`  | `POST` | 更新票券餘量與密碼           | ✅ JWT   |
| `/api/user/save_qrcode`  | `POST` | 儲存/轉換 QR Code 並寄送郵件 | ✅ JWT   |

---

## ⚠️ 注意事項

- 本系統對 API 請求大小限制較寬 (`50mb`)，以支援 QR Code 的 Base64 字串傳輸。
- 郵件發送功能建議使用特定 App Password (如 Gmail)。

---

## 📄 License

ISC License

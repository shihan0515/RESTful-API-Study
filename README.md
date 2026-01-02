# RESTful-API-Study RESTful API 入門

## 一、 什麼是 RESTful API？
REST (Representational State Transfer) 是一種軟體架構風格，定義了客戶端與伺服器之間如何透過 HTTP 協議交換資料。

## 二、 HTTPS 協議 (HyperText Transfer Protocol Secure)
* **定義**：在 HTTP 的基礎上加入了 SSL/TLS 加密層。
* **安全性**：
    * **資料加密**：防止傳輸過程中被監聽（例如在咖啡廳用公用 Wi-Fi 時）。
    * **身份驗證**：確保你連線的是真實的伺服器，而非釣魚網站。
    * **資料完整性**：防止資料在傳輸過程中被第三方竄改。
      
### 核心三要素
1. **資源 (Resource)**：使用「名詞」定義 URL（網址），例如 `/users`、`/orders`。
2. **動作 (HTTP Methods)**：使用動詞決定操作方式。
3. **狀態碼 (Status Codes)**：伺服器回傳的處理結果（如：200 成功、404 找不到）。

---
## 三、 CRUD 操作與 HTTP 方法
CRUD 代表資料操作的四個基本動作，在 RESTful API 中對應特定的 HTTP 動詞：

| 動作 | 說明 | HTTP 方法 | 範例 |
| :--- | :--- | :--- | :--- |
| **C**reate | 新增資料 | `POST` | 註冊新會員 |
| **R**ead | 讀取/查詢資料 | `GET` | 瀏覽商品列表 |
| **U**pdate | 更新資料 | `PUT` / `PATCH` | 修改個人資料 |
| **D**elete | 刪除資料 | `DELETE` | 刪除留言 |

## 四、 具體範例：圖書館借書系統

假設我們要操作「書籍」這項資源，我們會這樣定義 API：

| 動作 (Method) | 網址 (Endpoint) | 功能描述 | 成功狀態碼 |
| :--- | :--- | :--- | :--- |
| **GET** | `/api/books` | 取得所有書籍清單 | 200 OK |
| **GET** | `/api/books/101` | 取得 ID 為 101 的書籍詳情 | 200 OK |
| **POST** | `/api/books` | **新增**一本新書 | 201 Created |
| **PUT** | `/api/books/101` | **修改** ID 101 書籍的完整資料 | 200 OK |
| **DELETE** | `/api/books/101` | **刪除** ID 101 的書籍 | 204 No Content |


---

## 三、 前、後端溝通時的差異 (Responsibilities)

當 API 請求發出的那一刻，前後端關注的事情完全不同：

### 1. 前端 (Frontend / Client Side)
> **角色：請求者、呈現者**
- **關注點**：使用者體驗 (UX)、資料展示、流程控制。
- **操作當下**：
    - **發送 (Request)**：使用 `fetch` 或 `axios` 將資料包裝成 JSON 格式送出。
    - **等待 (Async)**：處理非同步狀態，顯示 Loading 動畫防止使用者重複點擊。
    - **反應 (React)**：根據後端回傳的狀態碼更新畫面。
        - 拿到 `200`：把新資料渲染到網頁上。
        - 拿到 `401`：引導使用者跳轉到登入頁面。

### 2. 後端 (Backend / Server Side)
> **角色：處理者、守門員**
- **關注點**：資料安全、邏輯運算、資料庫穩定。
- **操作當下**：
    - **驗證 (Auth & Validation)**：檢查 Request Header 是否有 Token（身分驗證），檢查 Body 資料格式是否正確。
    - **邏輯處理 (Business Logic)**：執行業務邏輯（例如：確認這本書是否還有庫存？）。
    - **持久化 (Database)**：對資料庫進行讀取或寫入。
    - **回傳 (Response)**：給予標準化的 JSON 回應與狀態碼。

---

## 四、 總結對比

| 比較項目 | 前端 (Client) | 後端 (Server) |
| :--- | :--- | :--- |
| **核心目標** | 讓使用者好用、好讀 | 讓系統安全、穩定、快速 |
| **主要產出** | HTML/CSS 畫面更新 | JSON 資料、HTTP 狀態碼 |
| **面對問題** | 如何處理網路延遲、畫面閃爍？ | 如何防止非法存取、資料庫報錯？ |

> **心法：** > RESTful API 就像是前後端之間的「共同語言」。只要 URL 和 Method 定義好了，前端不需要知道後端是用 Node.js 還是 Go，後端也不管前端是 Web 還是 App，雙方就能各司其職，達成解耦（Decoupling）。

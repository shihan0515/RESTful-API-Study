# RESTful-API-Study RESTful API 入門

## 一、 什麼是 RESTful API？
REST (Representational State Transfer) 是一種軟體架構風格，定義了客戶端與伺服器之間如何透過 HTTP 協議交換資料。

## 二、 HTTPS 協議 (HyperText Transfer Protocol Secure)
* **定義**：在 HTTP 的基礎上加入了 SSL/TLS 加密層。
* **安全性**：
    * **資料加密**：防止傳輸過程中被監聽（例如在咖啡廳用公用 Wi-Fi 時）。
    * **身份驗證**：確保你連線的是真實的伺服器，而非釣魚網站。
    * **資料完整性**：防止資料在傳輸過程中被第三方竄改。

## 三、 CRUD 操作與 HTTP 方法
CRUD 代表資料操作的四個基本動作，在 RESTful API 中對應特定的 HTTP 動詞：

| 動作 | 說明 | HTTP 方法 | 範例 |
| :--- | :--- | :--- | :--- |
| **C**reate | 新增資料 | `POST` | 註冊新會員 |
| **R**ead | 讀取/查詢資料 | `GET` | 瀏覽商品列表 |
| **U**pdate | 更新資料 | `PUT` / `PATCH` | 修改個人資料 |
| **D**elete | 刪除資料 | `DELETE` | 刪除留言 |


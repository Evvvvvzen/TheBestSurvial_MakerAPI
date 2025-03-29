# 🛠️ Minecraft 市場 API 文件

本文件提供 TheBestSurvival 專案中所使用的 API 說明，包括市場查詢、價格更新與玩家統計功能。

---

## 📌 API 總覽
- **URL**：`https://19f8-59-125-237-249.ngrok-free.app`
| 功能               | 方法  | 路徑                         | 說明                     |
|--------------------|-------|------------------------------|--------------------------|
| 查詢市場商品狀態   | GET   | `/api/market/status`         | 取得所有商品現況         |
| 更新商品價格與數量 | POST  | `/api/market/update`         | 根據名稱修改價格與數量   |
| 查詢玩家上線統計   | GET   | `/api/player/stats`          | 目前在線與今日上線人數   |

---

## 📘 1. 查詢市場商品狀態

- **URL**：`/api/market/status`
- **Method**：`GET`
- **用途**：取得目前伺服器市場內所有販售與收購項目的狀態。

### ✅ 回傳格式（JSON）

```json
[
  {
    "name": "str",
    "price": int,
    "amount": int,
    "boughtAmount": int,
    "boughtMoney": int,
    "type": "str"
  }
]


## 🛠️ 2. 更新商品價格與數量

- **URL**：`/api/market/update`  
- **Method**：`POST`  
- **Content-Type**：`application/json`  
- **用途**：透過商品名稱更新其價格與數量

### 📤 請求內容（Request Body）

```json
{
  "itemName": "CHEST",
  "price": 15,
  "amount": 64
}

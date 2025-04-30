
# Minecraft Market API 文件

本文件說明如何使用提供的 API 來查詢與操作 Minecraft 商店系統與玩家統計資訊。

## Temporary URL:  https://4cd5-59-125-237-249.ngrok-free.app/
## 🌐 使用 HTML 與 JavaScript 存取 API（跨域與 Ngrok 注意事項）

當從 HTML 頁面（例如透過 `fetch()`）存取部署在 Ngrok 上的 API（如 `https://xxxxx.ngrok-free.app/...`）
**Ngrok 會預設跳出一個警告頁面**，導致 API 無法正確取得資料。

為了解決這個問題，請務必在 `fetch` 請求中加入以下 header：

```js
fetch(URL, {
  headers: {
    "ngrok-skip-browser-warning": "true"
  }
})
```
---

##  1.查詢市場商品狀態

- **URL**：`/api/market/status`  
- **Method**：`GET`  
- **用途**：取得目前商店中所有商品的資料

### ✅ 回傳格式（JSON）

```json
[
  {
    "name": "CHEST",
    "price": 15,
    "amount": 64,
    "boughtAmount": 1982,
    "boughtMoney": 310,
    "type": "SELL"
  },
  {
    "name": "BONE_MEAL",
    "price": 5,
    "amount": 64,
    "boughtAmount": 0,
    "boughtMoney": 0,
    "type": "BUY"
  }
]
```

### 📘 欄位說明

| 欄位名稱       | 型別   | 說明                   |
|----------------|--------|------------------------|
| `name`         | string | 商品名稱               |
| `price`        | int    | 單價                   |
| `amount`       | int    | 單筆販售數量           |
| `boughtAmount` | int    | 累計已售出數量         |
| `boughtMoney`  | int    | 累計已售出金額         |
| `type`         | string | 商品類型：SELL / BUY  |

---

## 2. 更新商品價格與數量

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
```

| 欄位名稱   | 型別   | 說明             |
|------------|--------|------------------|
| `itemName` | string | 要更新的商品名稱 |
| `price`    | int    | 新價格           |
| `amount`   | int    | 新數量           |

### ✅ 成功回應

```json
{
  "status": "更新成功"
}
```

### ❌ 錯誤回應（找不到商品）

```json
{
  "error": "找不到商品"
}
```

---

## 3. 玩家上線統計

- **URL**：`/api/player/stats`  
- **Method**：`GET`  
- **用途**：查詢目前在線玩家人數與今天曾經上線過的總人數

### ✅ 回傳格式（JSON）

```json
{
  "online": 3,
  "todayOnline": 18
}
```

| 欄位名稱      | 型別 | 說明                       |
|---------------|------|----------------------------|
| `online`      | int  | 當前在線的玩家人數         |
| `todayOnline` | int  | 今日曾上線過的玩家總人數   |

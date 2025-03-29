# TheBestSurvial_MakerAPI

# 📘 Minecraft 市場 API 文件（TheBestSurvival 專案）

> **Base URL**：`https://19f8-59-125-237-249.ngrok-free.app/api/market/status`  

---

## 📍 1. 查詢市場狀態

- **URL**：`/api/market/status`
- **Method**：`GET`
- **用途**：取得所有販售與收購項目的現況（價格、數量、交易紀錄等）

### ✅ Response JSON Format

```json return
[
  {
    "name": "str",
    "price": int,
    "amount": int,
    "boughtAmount": int,
    "boughtMoney": int,
    "type": "int"
  }
]

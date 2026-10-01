# 🧋 熊茶館點單 · Vercel 專用版（免費，不用信用卡）

Vercel 免費（Hobby 帳戶）**無需信用卡**，香港可訪問。把後端做成 serverless 函數，前端點單 → 跳 Stripe 收款。

## 目錄
```
bear_tea_vercel/
├─ api/checkout.js     Stripe 收款 serverless 函數（後端）
├─ index.html          點單前端（呼叫 /api/checkout）
├─ ok.html             付款成功頁
├─ vercel.json         部署設定
└─ package.json
```

## 一、部署（5 步，免費）
1. 把本資料夾內容推到 **GitHub** 倉庫（Public 即可）。
2. 開 **vercel.com** → 用 **GitHub** 登入（**不需信用卡**）。
3. 選 **Add New → Project** → Import 你的 GitHub 倉庫 → **Deploy**。
4. 取得網址：`https://你的專案.vercel.app`。
5. 到該服務 **Settings → Environment Variables** 填 3 個變數後按 **Redeploy**：
   - `STRIPE_SECRET_KEY` = `sk_live_...`
   - `SUCCESS_URL` = `https://你的專案.vercel.app/ok.html`
   - `CANCEL_URL` = `https://你的專案.vercel.app/`

## 二、Stripe 香港收款
- 到 **stripe.com** 註冊，地區選 **香港 Hong Kong**，填香港企業 + 銀行帳戶。
- 後台「開發人員 → API金鑰」取得 `sk_live_...`。測試可用 `sk_test_...` + 測試卡 `4242 4242 4242 4242`。

## 三、測試
手機開 `https://你的專案.vercel.app` → 點單 → 去結算 → Stripe 付款 → 成功跳 `/ok.html` → 錢進香港銀行帳戶。

## 四、備註
- **金額以 serverless 後端計算為準**，安全。
- Vercel 免費額度夠小型飲品店；量大再升級 Pro。
- `sk_test_` 是測試用，正式上線務必換 `sk_live_`。

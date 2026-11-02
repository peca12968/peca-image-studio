# Peca 商品圖工作台

私有開發版本庫。現階段為 `1.0.0-rc.1` 店主檢查版，尚未開賣。

給小型賣家整理一批商品圖：三種尺寸、完整保留或置中裁切、背景留白、文字／圖片標誌、商品編號、圖片與 CSV 清單 ZIP 匯出。處理在瀏覽器完成，沒有雲端圖像 API 或帳號系統。

## 開發

Node.js 22+，無外部執行依賴，不需要 npm install。

```sh
npm test
npm run check
npm run build
```

沒有 npm 指令時，也可直接執行 `node --test tests/core.test.cjs`、`node --check src/studio.js`、`node --check src/core.js` 與 `node scripts/build.mjs`。

原始碼在 `src/`；建置產生 `dist/trial`（3 張）與 `dist/offline`（50 張），以及店主檢查 ZIP。生成物不提交 Git。需要瀏覽器 QA 時，以本機靜態伺服器預覽 trial；不得繞過瀏覽器對 file:// 的封鎖。

網站試用生成物會複製到佩卡 Sites 專案，經既有 Sites 流程發佈。完整版只放 F 槽店主交付目錄，不能複製到公開網站。

## 已驗證

- 11 個核心行為測試：構圖、輸入、檔名、CSV 公式注入防護、CRC32 與 ZIP 結構。
- 真實瀏覽器 3 張轉 9 個 JPG，實際下載並由 Python zipfile / Pillow 驗證三種尺寸、UTF-8 CSV 與 CRC。
- PNG 大小警告、WebP、置中裁切、數量上限、損壞圖片、標誌讀取、設定匯出／匯入、無效設定拒絕、設定變更後阻止下載舊 ZIP。
- 桌面 1280px 畫面與無水平溢出。

## 待驗證

本機 HTML 直接開啟、不同 Chrome/Edge 版本、完整版 50 張壓力測試、大圖／不同裝置與手機版面。內建瀏覽器禁止 file://，而手機 viewport 覆寫未實際套用；不能將這些項目列為通過。

## 版本迭代

1. 從 main 建立 `feat/...` 或 `fix/...` 分支。
2. 修改 src 並完成有意義的測試；更新 CHANGELOG 與 package.json 版本。
3. 檢查後提交，推送私人版本庫。需要 review 時開 PR。
4. 僅在驗證完成的 commit 建立 `vX.Y.Z-rc.N` 或正式版本標籤，再由同一 commit 建置商品。
5. 正式價格、授權、支援、收款與交付未定案；切勿因此 repo 已建立就自行開賣。

試用限制是前端產品設定，不是防破解或安全授權機制。所有原創軟體與示範插畫保留權利；未提供開源授權。不得把私有原始碼公開或添加公開完整版網址。

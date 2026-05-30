# ConcreteFlow AI — PWA

基於 PINN 物理流體方程與 Yeh (1998) 實測資料的混凝土配合比流變與抗壓強度預測工具。

## 功能
- 單方材料用量輸入（水泥 / 爐石粉 / 飛灰 / 粗細骨材）
- 水膠比、減水劑摻量即時調整
- 坍度（τ₀ 驅動）、壓力泌水率預測
- 7 天 / 28 天抗壓強度預測（以 1030 筆實測資料回歸標定，R²≈0.83）
- Bingham 流變坍度錐動態模擬
- 減碳率與成本節省計算（相對純水泥配比）

## GitHub Pages 部署步驟

1. 建立一個新的 GitHub 儲存庫（例如 `concreteflow`），將本資料夾**所有檔案**（含 `.github`、`.nojekyll` 等隱藏檔）上傳並推送到 `main` 分支。
2. 進入儲存庫 **Settings → Pages**，在 **Build and deployment** 的 **Source** 選擇 **GitHub Actions**。
3. 推送後 Actions 會自動執行部署（也可在 Actions 頁手動觸發 `Deploy PWA to GitHub Pages`）。
4. 部署完成後，網址為 `https://<帳號>.github.io/<儲存庫名稱>/`。

## 安裝為 App（PWA）
以手機或桌面瀏覽器開啟上述網址：
- **Android / Chrome**：選單 → 「安裝應用程式 / 加到主畫面」
- **iOS / Safari**：分享 → 「加入主畫面」
- **桌面 Chrome / Edge**：網址列右側的安裝圖示

安裝後可離線使用（Service Worker 已快取所有資源）。

## 檔案結構
```
index.html                  主程式（樣式與邏輯內嵌，無外部相依）
manifest.webmanifest        PWA 設定
sw.js                       Service Worker（離線快取）
icon-192.png                App 圖示 192
icon-512.png                App 圖示 512
icon-192-maskable.png       Maskable 圖示 192
icon-512-maskable.png       Maskable 圖示 512
icon-180.png                Apple Touch 圖示
favicon-32.png              瀏覽器分頁圖示
.nojekyll                   停用 GitHub Pages 的 Jekyll 處理
.github/workflows/deploy.yml  自動部署工作流程
```

## 更新快取
修改內容後，請將 `sw.js` 中的 `CACHE_VERSION` 改為新值（例如 `concreteflow-v2`），使用者重新整理後即會載入最新版本。

引力流域設計 GraviFlow Design — 網站檔案（Vercel 用，也可在本機看）

在本機看
- 雙擊 index.html 就能看，選單、頁尾連結、首頁案例都能直接換頁。

檔案
- index.html      首頁（第一次進站：預載畫面 → 開場動畫；同一次造訪回首頁不再播）
- about.html      關於我們
- works.html      作品集（works.html#work-guokao 這類連結會直接展開該作品）
- privacy.html    隱私權政策
- refund.html     退換貨政策
- 404.html        找不到頁面
- robots.txt / sitemap.xml   搜尋引擎用
- vercel.json     讓網址不帶 .html（例如 www.graviflowdesign.com/about）
- assets/、vendor/、support.js、gf-intro.js   圖片、影片與程式

部署到 Vercel
1. 把這個資料夾「裡面」的檔案放進一個 GitHub repository（不要多包一層資料夾），
   到 vercel.com → Add New → Project → Import 那個 repository。
   Framework Preset 選「Other」，Build Command 和 Output Directory 都留空，按 Deploy。
2. 專案 Settings → Domains，加入 www.graviflowdesign.com（Vercel 會建議把 graviflowdesign.com 一起加並轉到 www，照預設即可）。
3. 到 Namecheap → Domain List → Manage → Advanced DNS，依 Vercel 畫面上顯示的值新增：
   - A Record：Host 填 @，Value 填 Vercel 給的 IP（通常是 76.76.21.21）
   - CNAME Record：Host 填 www，Value 填 Vercel 給的值（通常是 cname.vercel-dns.com）
   原本 Namecheap 預設的 parking / URL Redirect 記錄要先刪掉。
4. Vercel 顯示 Valid Configuration 後，https 會自動開好。

SEO（已完成）
- 每頁：標題、meta description、canonical、社群分享標籤（Open Graph / Twitter）
- 社群分享縮圖 assets/og-image.jpg（1200×630）、網站圖示、結構化資料（首頁、關於我們）
- robots.txt 允許搜尋引擎爬取並指向 sitemap.xml；sitemap.xml 列出 5 個頁面

串接 Google Search Console（網站上線後）
1. https://search.google.com/search-console →「新增資源」→ 選「網域」→ 輸入 graviflowdesign.com
2. 複製 Google 給的 TXT 記錄（google-site-verification=…）
3. Namecheap → Advanced DNS → Add New Record：TXT Record，Host 填 @，Value 貼上，儲存
4. 回 Search Console 按「驗證」（DNS 生效可能要幾分鐘到幾小時）
5. 驗證成功後，左側「Sitemap」輸入 sitemap.xml 送出

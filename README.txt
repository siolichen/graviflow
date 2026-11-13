引力流域設計 GraviFlow Design — 正式網站檔案（www.graviflowdesign.com）

這是純靜態網站，不需要 WordPress。

在本機看
- 直接雙擊 index.html 就能看畫面（各頁、動畫、影片都能顯示）。
- 本機用雙擊打開時，點選單裡的頁面會出現資料夾，請點資料夾裡的 index.html；放到網站上之後就會直接開頁面。

部署到 GitHub Pages
1. 在 GitHub 建一個新的 repository（Public）。
2. 按「Add file → Upload files」，把這個資料夾「裡面」的所有檔案和資料夾拖進去（不要多包一層資料夾），按 Commit。
   ※ .nojekyll 和 CNAME 這兩個檔案也要一起上傳；Windows 若看不到 .nojekyll，請在檔案總管開啟「顯示隱藏的項目」。
3. Settings → Pages → Source 選「Deploy from a branch」，Branch 選 main、資料夾選 / (root)，Save。
4. 同一頁的 Custom domain 會自動帶入 www.graviflowdesign.com（來自 CNAME 檔），DNS 設好後勾選「Enforce HTTPS」。

Namecheap 的 DNS（Domain List → Manage → Advanced DNS）
- CNAME Record：Host 填 www，Value 填「你的GitHub帳號.github.io」
- A Record ×4：Host 填 @，Value 分別填 185.199.108.153、185.199.109.153、185.199.110.153、185.199.111.153
  （讓不帶 www 的 graviflowdesign.com 也會自動轉到 www）
- 原本 Namecheap 預設的 parking / URL Redirect 記錄要先刪掉。

頁面網址
- /            首頁（第一次進站會先顯示預載畫面，再播開場動畫；同一次造訪回到首頁不再播）
- /about/      關於我們
- /works/      作品集（/works/#work-guokao 這類網址會直接展開該作品）
- /privacy/    隱私權政策
- /refund/     退換貨政策
- /404.html    找不到頁面時顯示

SEO 設定（已完成）
- 每頁都有標題、meta description、canonical 網址、社群分享標籤（Open Graph / Twitter）
- 社群分享縮圖：assets/og-image.jpg（1200×630）
- 網站圖示：assets/favicon-96.png、assets/apple-touch-icon.png
- 結構化資料（JSON-LD）：首頁、關於我們
- robots.txt：允許所有搜尋引擎爬取，並指向 sitemap
- sitemap.xml：5 個頁面

串接 Google Search Console（網站上線、網址能打開之後再做）
1. 到 https://search.google.com/search-console 按「新增資源」，選左邊的「網域」，輸入 graviflowdesign.com
2. Google 會給一串 TXT 記錄（google-site-verification=…）
3. Namecheap → Advanced DNS → Add New Record：類型 TXT Record，Host 填 @，Value 貼上那串文字，儲存
4. 回到 Search Console 按「驗證」（DNS 生效可能要幾分鐘到幾小時）
5. 驗證成功後，左側「Sitemap」輸入 sitemap.xml 送出
※ 網域驗證不用改網站檔案，www 和非 www 都會一起涵蓋。

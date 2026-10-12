# K128《人手一本的 Vibe Coding 資安實作課》（陳瑞麟）

- 作者陳瑞麟，博碩文化；副標「OWASP Top 10 × ISO27001」。5 章＋附件，固定版面（有印刷頁碼）
- 來源 **HyRead**（視窗標題 `Online Reader`），2026-10-12 於 **hp2 筆電（DESKTOP-6LST1BR，HP EliteBook 840 G8）** 第一次跑 pipeline
  - 直式外接螢幕 **1440×2560**（座標 -1440,-95），Chrome F11 全螢幕
  - Phase 1：`measure.py` 量得工具列上 16–46、下 2511–2554（同 K88），目視分隔線上 ≈62、下 ≈2499 → `--top-crop 70 --bottom-crop 66`
  - HyRead 不跑 `--test-keys`（往回翻會卡低解析）；由擷取本身驗方向：右鍵＝下一頁
  - `GPB_NO_CLICK=1`、`--max-pages 800`，以 `Start-Process` 獨立行程擷取：341 次截圖、到書尾連 3 張相同自動停，存 338 張
  - 第 337 張是 HyRead「閱讀結束」頁 → 移到 `excluded/`，實際 337 頁（0..336）
  - hash 唯一 336/337：唯一重複是 91 與 315 兩張空白「Note」頁（良性）
  - 低清晰度 4 張皆良性：1、15 空白頁，328「附件」扉頁（7.1‰），337 閱讀結束頁（已排除）
- 分章：**截圖編號＝印刷頁＋15**（錨點：90＝印刷 75、147＝印刷 132）
  - 目錄頁 12–14 讀出 5 章各小節頁碼
  - 扉頁版型（上灰漸層＋下深色圖）群集：16／72／92／208／316／328 特徵值完全相同（222／170），下一名 217 → 6 頁＝5 章＋附件，逐頁讀字面章號確認
  - 第 3 章（116 頁）於 3.4 起點（147）、第 4 章（108 頁）於 4.8 起點（269，頁首即 4.8 標題）各拆兩段 → 共 7 段，見 `chapters.json`
  - 頁/節比：2.9／18.3／8.7／8.7／6.7（第 3 段 3.1–3.3 共 53 頁 3 節，與目錄頁碼一致）；第 1、7 段含推薦序／附件，不適用
- Phase 4：7 段 PDF 本機與 VPS 兩端 `pdfinfo` 頁數 7/7 相符（72／20／55／61／61／47／21）
- NLM：notebook `ef4053d9-c462-454c-b32f-e2cbe561b58d`（VPS CLI 0.6.0），7 source 全 pdf/ready
- VPS `~/kindle-128/`：`trigger.sh` 四類觸發（影片／簡報帶大綱先行規定）→ `finish.sh` 收成 → 播放清單 → 簡報網頁（Phase 9）→ YouTube 私人（Phase 10）
- nginx：`hookhub` 加 2 段 location（`= /kindle-128.m3u`、`/audio/kindle-128/`），備份 `/etc/nginx/conf-backups/hookhub.bak-k128-*`
- VPS 磁碟開跑前 74%、剩 26 GB

## 完成結果（2026-10-12 16:38 台北，VPS 全自動）

- 28 件一次觸發，0 NOTRIG、id 全唯一；約 25 分鐘內四類 7/7 全部完成並正名
- 語音 7 段，總長 2:08:58，VPS ffprobe 7/7，`tools/verify_kindle_playlist.py verify 128` 獨立複驗 7/7 PASS：<http://187.127.109.145/kindle-128.m3u>（Gmail `1a12f3b244bfa251`、Telegram 1474）
- 簡報網頁：<https://chenghyang2001.github.io/kindle-128-slides/>，7 段 103 張，viewer **idx 94**（Gmail `1a12f4359e8492a8`、Telegram 1475）
- 大綱先行抽查：7 段簡報第一頁皆為大綱頁（7/7）；NLM 簡報 PDF 為整頁圖片，`pdftotext` 抽不到字，需轉圖目視
- hp2 本機沒有 Telegram 設定 → 兩則 Telegram 皆由 VPS `~/.env_vars`（`TELEGRAM_BOT_TOKEN`／`TELEGRAM_CHAT_ID`）以 urllib 發送；`slides_webapp.py` 自身的 Telegram 也因讀不到這兩個變數而略過
- YouTube（私人）：Phase 10 在 VPS 進行中（`yt_phase10.sh`，最長 24 小時，完成後自動寄信）

# K128 演練交接

## 原機器結果

本書沒有在其他機器演練過，沒有可比對的原機器結果。每章的差異以「和書上原做法的差異」記錄。

## 快速模式進度表

| 章 | 完成日 | 實際耗時 | 和書上做法的差異 |
| --- | --- | --- | --- |
| 01 | 2026-10-16 | 約 3 分鐘 | 不裝 Claude 桌面版／XAMPP／PhpMyAdmin／VS Code＋Copilot／Kali VM，改用 PHP 8.4 內建伺服器＋SQLite；本機原本沒有 PHP，先用 winget 裝 PHP.PHP.8.4 並從 php.ini-development 建 php.ini 開 pdo_sqlite |
| 02 | 2026-10-16 | 約 4 分鐘 | 書上用 XAMPP＋MySQL＋Claude 桌面版；改為 PHP＋SQLite＋`php -S`、由 Claude Code 生成。產出 6 檔（5 php＋1 css），DB 放 public/ 之外；curl 三項驗證通過。練習視窗自報未處理：登入失敗次數限制、cookie secure（留給第 4 章） |
| 03 | 2026-10-16 | 約 2 分鐘 | 書上在 Kali VM 實際操作偵察／測試工具；本次只寫防守視角的 DEFENSE-NOTES.md（8 類×四點＋攻擊鏈對照），未安裝、未執行任何工具、未探測任何主機；已掃描確認全文無指令 |
| 04 | | | |
| 05 | | | |

# K128 演練交接

## 原機器結果

本書沒有在其他機器演練過，沒有可比對的原機器結果。每章的差異以「和書上原做法的差異」記錄。

## 快速模式進度表

| 章 | 完成日 | 實際耗時 | 和書上做法的差異 |
| --- | --- | --- | --- |
| 01 | 2026-10-16 | 約 3 分鐘 | 不裝 Claude 桌面版／XAMPP／PhpMyAdmin／VS Code＋Copilot／Kali VM，改用 PHP 8.4 內建伺服器＋SQLite；本機原本沒有 PHP，先用 winget 裝 PHP.PHP.8.4 並從 php.ini-development 建 php.ini 開 pdo_sqlite |
| 02 | 2026-10-16 | 約 4 分鐘 | 書上用 XAMPP＋MySQL＋Claude 桌面版；改為 PHP＋SQLite＋`php -S`、由 Claude Code 生成。產出 6 檔（5 php＋1 css），DB 放 public/ 之外；curl 三項驗證通過。練習視窗自報未處理：登入失敗次數限制、cookie secure（留給第 4 章） |
| 03 | 2026-10-16 | 約 2 分鐘 | 書上在 Kali VM 實際操作偵察／測試工具；本次只寫防守視角的 DEFENSE-NOTES.md（8 類×四點＋攻擊鏈對照），未安裝、未執行任何工具、未探測任何主機；已掃描確認全文無指令 |
| 04 | 2026-10-16 | 約 8 分鐘 | 書上手動／Kali 驗證，本次用 tests/smoke.sh（curl）自動驗證，教練端重跑 22/22 通過。修補：登入失敗 5 次鎖定（429）、登入日誌、安全標頭、隱藏版本、全域例外。Windows 坑：PHP 不吃 /c/ 路徑（改 pwd -W）、mingw curl 寫 /dev/null 報錯。已知風險：admin/admin 未強制改密碼 |
| 05 | 2026-10-16 | 約 2 分鐘 | 附件 A／B 網址未取得而略過，改用第 4 章自己的 OWASP 修補當素材；ISO27001-MAP.md 將 F1–F7 對應 5.x／6.x／7.x／8.x（共 33 個控制編號，實體 7.x 皆不適用並附理由），含總表與已知風險追蹤 |

## 環境備註（2026-10-16 本機演練）

- 本機原本沒有 PHP：以 `winget install --id PHP.PHP.8.4 -e` 安裝，並從 `php.ini-development` 建 `php.ini`，開啟 `pdo_sqlite`、`sqlite3`、`mbstring`、`openssl`
- 練習視窗啟動指令要在 cmd 內補 PHP 的 PATH；wt.exe 會把 `;` 當命令分隔，要寫成 `\;`
- 全程 5 章合計約 20 分鐘（含環境補裝）；全域 `~/.claude/settings.json` 每章比對皆未變

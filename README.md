# 把糾正寫成規則：poteto 怎麼讓 slop 變黃金

Lauren Tan〈All Code Is Slop (Except Mine)〉的繁體中文導讀。影片由 AI Engineer 頻道於 2026-11-14 上傳，長 17 分 31 秒；影片版面標示 AI Engineer Code Summit。導讀整理她如何用程式碼庫的約束、lint 規則與驗證產物，建立對 agent 的信任。資料截至 2026-11-15。

> 本導讀的分析與撰稿由 AI 模型完成，不是人類分析，也沒有經過人工逐句校稿。**已發布（2026-11-15）**：https://lushinshang.github.io/lauren-tan-code-slop/ ，repo：https://github.com/lushinshang/lauren-tan-code-slop 。公開內容只有 `index.html`、`read.html`、`player.html`、`translation-zh.html`、主文 md、README、`images/`（不含 PNG 母檔）、`audio/`；`research/`、`qa/` 只在本機。

## 檔案

| 檔案 | 內容 |
|---|---|
| `index.html` | 時間軸解說動畫：13 場、約 10 分鐘；字幕加 AI 合成旁白（可用「旁白」鈕關閉）；空白鍵播放／暫停、←／→ 換場、J／L 退進 5 秒、F 全螢幕；講者場的字幕可點回原片秒數 |
| `read.html` | 長文導讀（溫室麥田主題）：14 場、14 張重繪 SVG、五種來源標籤、深淺模式 |
| `player.html` | 中英雙語字幕同步播放器（需 http 與 YouTube 連線） |
| `translation-zh.html` | 全文繁中譯文（非官方，AI 翻譯） |
| `lauren-tan-code-slop.md` | 主文（分場稿） |
| `images/` | 14 組桌面／手機 SVG、橫式／直式封面、分享預覽圖 |
| `audio/` | 動畫旁白 56 句（AI 合成） |
| `research/`、`qa/` | 證據帳本、字幕、查證、建置與 QA 腳本、各輪測試輸出（發布時不公開） |

`index.html`、`read.html`、`translation-zh.html` 可直接開啟；播放器與旁白的跳轉需要支援 Range 的 http 伺服器：`python3 ~/.claude/skills/deep-guide-mp4/scripts/serve_range.py . 8784`。

## 內容分級

| 標籤 | 意義 |
|---|---|
| 〔一手〕 | repo 或官方頁可直接查到（pstack、Bombadil、Grok Bot 官方頁、講者 GitHub） |
| 〔畫面〕 | 講者簡報上的數據，沒有獨立第二來源 |
| 〔講者〕 | 只有口述，沒有畫面或公開來源 |
| 〔二手〕 | 媒體轉述，未見官方原文 |
| 〔推論〕 | 本文歸納，講者沒有這樣說 |

## 來源性質與限制

- 影片是 AI Engineer 頻道上傳；講者任職資訊來自影片版面（Principal Engineer／SpaceX）與投影片（Grok Bot @ SpaceXSI），不代表公司官方背書。講者 GitHub 檔案則寫 Software Engineer、任職 @xai-org。
- PR、註解、發布次數、還原率與效能數字多為講者自述或簡報資料，沒有獨立第二來源。團隊數字投影片寫 merged，還原率的分母是 commits；效能圖同時有退步項。Dune 與 Grok Bot 的技術棧沒有公開來源。
- 英文為 YouTube 機器字幕 `en-orig`（把 poteto 聽成 Potato 等，中文已更正）；中文由 agy 翻譯，Opus 逐句閱讀，未經人工校稿、未逐句對照原音。
- 圖表是依簡報資訊重繪的 SVG，並非講者原圖；封面與插圖為 AI 生成，園丁獺與小苗是原創角色，風格受講者簡報啟發。講者簡報與影片版權屬原權利人。
- 旁白為 macOS 合成語音，不是講者本人。Whisper 回聽平均相似度 0.89、4 句低於 0.8（多半是 Whisper 把「程式」聽成「城市」、專名拼法），未經人工逐句聽過。
- Bret Taylor 軼事、Grok Bot 發布日期為二手；其中兩個來源頁本機抓不到，只見搜尋摘要。

## 本機重建

```sh
python3 research/anim_content.py && python3 research/build/build_anim_custom.py --narration   # index.html
python3 research/build/build_all.py . read                                                    # read.html
```

## 測試與限制

測試輸出在 `qa/r0`（基準）、`qa/r1`、`qa/r2`，總結見 `qa/quality_report.md`。只在 Chrome 測試；沒有 Safari、Firefox、實機；沒有 Lighthouse（本機未安裝）；YouTube 內嵌播放器的焦點樣式不在我們控制內。

## 原始來源

[影片](https://www.youtube.com/watch?v=O_zcc6Xl12g)、[pstack](https://github.com/cursor/plugins/tree/main/pstack)、[Bombadil](https://github.com/antithesishq/bombadil)、[Grok Bot](https://x.ai/bot)、[poteto](https://github.com/poteto)

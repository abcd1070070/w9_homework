# AGENTS.md — 常用軟體快捷鍵速查手冊 (Excel / Word / PowerPoint / VS Code)

> **給 AI 協作者的閱讀說明**：
> 本文件定義了「常用軟體快捷鍵速查手冊」網站的設計目的、視覺風格、頁面固定結構、互動仿真機制與新增頁面流程。
> 當你需要修改現有內容，或為本專案新增、擴充軟體頁面時，請嚴格遵守以下規則，確保網頁實作與本文件規範 100% 對應一致。

---

## 1. 專案目的 (Project Purpose)

* **核心目標**：整理日常辦公與程式開發最常用的四大工具（**Excel**、**Word**、**PowerPoint**、**VS Code**）快捷鍵，打造一個具備**「3D 擬真機械鍵盤壓感、軸體聲學回饋、微縮軟體仿真視窗（Mini App Sandbox）、以及 Windows / Mac 雙系統切換」**的互動式速查手冊網站。
* **可重複使用與延伸性**：將「網頁底層互動引擎（3D 鍵盤模型、Web Audio 音效合成、按鍵防誤觸攔截、搜尋與釘選）」與「各軟體快捷鍵資料（`SOFTWARE_GUIDES`）」完全分離。未來新增或修改頁面時，只需依循同一套資料格式填入內容，無須重寫底層排版或互動程式碼。

---

## 2. 檔案結構與命名規則 (File Structure & Naming)

```text
shortcut-handbook/
├── AGENTS.md                 # 專案開發規範總則（AI 讀取與維護入口）
└── index.html                # 網站主檔案（含手冊總覽、四大軟體分頁、3D 鍵盤與微縮仿真視窗）
```

### 命名規則
1. **軟體識別碼 (`id`)**：一律使用全小寫英文單字：`excel`、`word`、`powerpoint`、`vscode`。
2. **快捷鍵識別碼 (`shortcut.id`)**：一律以「軟體縮寫 + 連字號 + 功能英文」命名，例如：`xl-sum`、`wd-bold`、`ppt-new`、`vsc-palette`。

---

## 3. 網頁整體風格與禁止事項 (Visual Style & Anti-Patterns)

### 3.1 色彩系統（工業文具與機械鍵盤紙張風）
* **背景主色**：`#FAF8F5`（暖米白工程方格紙底色，搭配 `#E2DDD2` 微點陣）
* **卡片與區塊底色**：`#FFFFFF`（純白卡片）搭配 `1px solid #DFD9CE` 暖灰邊框
* **文字色彩**：主標題與內文 `#23272F`（深墨灰）、次要說明 `#5E646E`（中性灰）
* **四大軟體專屬代表色（用於分頁橫幅、3D 鍵帽亮燈、分類按鈕與仿真視窗強調色）**：
  * **Excel**：`#2E6F40`（森林綠，淺底色 `#EAF3EC`，標籤 `SPREADSHEET`）
  * **Word**：`#2B579A`（經典靛藍，淺底色 `#EBF1F8`，標籤 `DOCUMENT`）
  * **PowerPoint**：`#C4512D`（暖磚橘，淺底色 `#FCEEED`，標籤 `PRESENTATION`）
  * **VS Code**：`#0066B8`（石板青藍，淺底色 `#E6F2FA`，標籤 `CODE EDITOR`）

### 3.2 字體與 3D 擬真鍵帽規格
* **正文字體**：`'Noto Sans TC'`, `'Inter'`, sans-serif
* **等寬與鍵帽字體**：`'JetBrains Mono'`, monospace
* **3D 機械鍵盤模型 (`.mech-case` & `.vk-key`)**：必須呈現鋁坨外殼、深色定位板與雙色 PBT 球帽立體陰影；觸發時產生 `translateY(3px)` 的真實下壓行程，並點亮該軟體的專屬代表色。

### 3.3 嚴格禁止事項 (Do Not Do)
* **禁止廉價 Emoji 裝飾**：標題與區塊開頭嚴禁堆砌 `📖`、`✨`、`⌨️`、`🚀` 等裝飾性 Emoji，一律使用乾淨的工程編號（如 `FIG 01`、`01 /`）、純 SVG 向量線條圖或單純文字排版。
* **禁止深色賽博龐克風與 AI 罐頭術語**：嚴禁使用黑底霓虹發光或「AI 智能賦能」、「次世代核心」等生硬詞彙。

---

## 4. 頁面固定結構與互動規則 (Page Structure & Interactivity)

每一個軟體分頁必須由上而下包含以下 **4 個固定區塊**，順序與結構不可任意更動：

1. **頂部導覽、軸體聲學與系統切換列 (Header Bar)**：
   * 左側為網站標誌 `[⌘K]`；中間為切換分頁（手冊總覽、Excel、Word、PowerPoint、VS Code、釘選夾）。
   * 右側固定提供 **「軸體聲切換（PBT 麻將音 Thock / 清脆青軸 Clicky / 靜音紅軸 Linear / 關閉音效）」** 以及 **「Win ↔ Mac」系統切換開關**。
   * **Win / Mac 鍵盤連動規則**：切換至 `Win` 時，3D 鍵盤左下角必須顯示 `Ctrl`、`⊞ Win`、`Alt`；切換至 `Mac` 時，必須自動切換為 `control`、`⌥ Opt`、`⌘ Cmd`。
2. **軟體橫幅與工程圖解區 (Software Banner)**：
   * 左側顯示軟體類別標籤、標題與一句話簡介；右側顯示套用該軟體代表色的 SVG 幾何工程圖解。
3. **3D 機械鍵盤模型與微縮軟體仿真視窗 (3D Keyboard & Mini App Sandbox)**：
   * **左側為 3D 機械鍵盤模型**：支援滑鼠單點鍵帽試聽軸體聲、「`▶ 連按示範`」自動依序敲擊組合鍵，以及實體鍵盤同步亮燈。
   * **實體鍵盤防誤觸攔截規則 (`● 實體鍵盤攔截：開啟`)**：在軟體分頁按下實體按鍵時，必須呼叫 `e.preventDefault()` 阻擋瀏覽器預設熱鍵（防止空白鍵／方向鍵捲動網頁、防止 `Enter` 誤觸按鈕、防止 `Ctrl+P/F/S/D` 彈出瀏覽器視窗），且唯有「同時按對完整組合鍵」時才切換預覽項目。
   * **右側為微縮軟體仿真視窗 (Mini App Simulator)**：依軟體類型渲染專屬微縮介面（Excel 顯示 `fx` 公式列與儲存格網格、Word 顯示尺規與 A4 排版紙張、PowerPoint 顯示左側縮圖列與 16:9 簡報舞台、VS Code 顯示深色程式碼編輯器），並提供「切換前後狀態」按鈕對比按下快捷鍵前後的真實畫面變化。
4. **搜尋、分類篩選與快捷鍵速查表 (Filter & Shortcut Cards)**：
   * 包含關鍵字即時搜尋框，以及四個固定篩選按鈕：`全部`、`基礎操作`、`編輯排版`、`效率進階`。
   * 每張快捷鍵卡片固定顯示：立體組合鍵帽、右上角「`★` 釘選按鈕」、功能標題、一句話說明與分類標籤。

---

## 5. AI 新增或修改頁面的標準作業流程 (Extension Workflow)

當收到新增軟體頁面或擴充快捷鍵的指令時，AI 必須按照以下步驟執行：

### 步驟一：依照標準 Schema 填寫軟體與快捷鍵資料
在 `index.html` 的 `SOFTWARE_GUIDES` 資料陣列中，每個軟體物件都必須符合以下固定格式：

```javascript
{
  id: "vscode",                  // 1. 全小寫英文識別碼 (excel | word | powerpoint | vscode)
  name: "VS Code",               // 2. 分頁按鈕短名稱
  fullName: "Visual Studio Code 程式編輯速查表", // 3. 橫幅完整標題
  badge: "CODE EDITOR",          // 4. 大寫英文類別標籤
  accent: "#0066B8",             // 5. 軟體專屬主色
  accentSoft: "#E6F2FA",         // 6. 軟體專屬淺底色
  tagline: "寫網頁與改設定檔最順手的編輯器快捷鍵，右側內建微縮程式碼編輯器模擬視窗。",
  shortcuts: [
    {
      id: "vsc-palette",
      category: "基礎操作",        // 僅限填寫：基礎操作 | 編輯排版 | 效率進階
      win: ["Ctrl", "Shift", "P"],// Windows 按鍵陣列（需對應 3D 鍵盤之 data-key）
      mac: ["Cmd", "Shift", "P"], // Mac 按鍵陣列
      title: "開啟命令面板 (Command Palette)",
      desc: "VS Code 最核心的萬用鍵，忘記任何功能位置都能直接打字呼叫。",
      previewTitle: "彈出頂部萬用命令面板",
      previewBefore: "一般編輯狀態 (正在撰寫 app.js)",
      previewAfter: "頂部浮現：> Format Document (自動排版程式碼)"
    }
    // 每個分類至少收錄 3 個快捷鍵，每套軟體共計至少 9 個快捷鍵
  ]
}
```

### 步驟二：確認按鍵名稱對應 3D 視覺鍵盤
* `win` 與 `mac` 陣列中的按鍵字串，必須使用 3D 鍵盤支援的標準 `data-key` 名稱（`Ctrl`, `Win`, `Cmd`, `Shift`, `Alt`, `Opt`, `Enter`, `Space`, `Tab`, `Backspace`, `Esc`, `Up`, `Down`, `Left`, `Right`, `F2`, `F4`, `F5`, `;`, `=`, `-`, `.`, `/` 以及 `A`–`Z`, `0`–`9`），確保點擊卡片或執行「`▶ 連按示範`」時鍵帽能精準下壓亮燈。

### 步驟三：完成自我檢查清單 (Self-Check before Delivery)
* [ ] 頁面是否包含完整的三個分類（`基礎操作`、`編輯排版`、`效率進階`），且每類至少 3 筆（共 9 筆以上）？
* [ ] 點擊快捷鍵卡片或按「`▶ 連按示範`」時，3D 鍵盤是否會發出軸體音效並點亮對應鍵帽，且右側微縮軟體仿真視窗會同步更新？
* [ ] 切換右上角 `Win` / `Mac` 開關時，3D 鍵盤左下角修飾鍵是否正確在 `Ctrl / ⊞ Win / Alt` 與 `control / ⌥ Opt / ⌘ Cmd` 之間切換？
* [ ] 實體鍵盤攔截是否正常運作（按空白鍵或方向鍵不會捲動網頁，單點鍵帽不會誤觸其他快捷鍵）？
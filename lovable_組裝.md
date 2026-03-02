# 🚀 Lovable 實戰組裝手冊 (The Playbook)

這份指南定義了如何透過 **Prompt Architect Pipeline** 的三層架構，精準地餵養 Lovable 或 Claude，產出視覺一致且邏輯嚴密的網頁。

---

## 💡 核心心法：玩具城理論

*   **Global Layer (Soul)**：玩具城的規則書（房子什麼顏色、門長怎樣、路多寬）。
*   **Page Layer (Skeleton)**：每一棟房子的設計圖（醫院、學校還是超商？幾層樓？）。
*   **Assembly Layer (Heart)**：拿著規則書 + 設計圖去指揮機器人（Lovable）。

---

## 一、標準作業程序 (SOP)

### Step 1：確立設計憲法 (The Soul)
*   **檔案**：`global/BASE_DESIGN_SYSTEM.md`
*   **動作**：定義品牌色 (Hex Code)、字級階層、圓角、陰影、常用佈局 Pattern。
*   **原則**：**先立憲，再寫法**。這是全站的視覺靈魂，一旦定版，輕易不改。

### Step 2：撰寫頁面規格 (The Skeleton)
*   **檔案**：`pages/XX_filename.md`
*   **動作**：參考 `pages/page_template.md`，將單一頁面拆解為 5-7 個功能區塊 (Sections)。
*   **原則**：**一頁一 PRD**。只談這一頁的任務與結構，不談視覺細節（交給 Global 處理）。

### Step 3：動態組裝指令 (The Heart)
*   **檔案**：`assembly/PIPELINE_ORCHESTRATOR.md`
*   **動作**：將 Global 的「摘要」與 Page 的「細節」組合。
*   **宣告**：必須在 Prompt 開頭明確宣告：**「Global 規範 > Page 特定需求」**。

---

## 二、組裝範例 (The Master Prompt)

這是你丟進 Lovable 時的最佳結構：

```markdown
=== GLOBAL PROJECT GUIDELINE (DO NOT OVERRIDE) ===
[貼上 global/BASE_DESIGN_SYSTEM.md 的核心 Tokens]

重點：
- 本區段定義整個專案的設計系統，為最高準則。
- 所有組件必須繼承此處定義的配色、圓角與間距。

=== CURRENT TASK: BUILD [PAGE_NAME] ===
本次任務：根據上方 Global Guideline，實作以下頁面。

[貼上 pages/XX_page.md 的規格內容]

=== OUTPUT REQUIREMENTS ===
1. 確認結構：先列出本頁 Sections 與元件清單。
2. 設計說明：簡述如何落實一致性。
3. 生成程式碼：產出完整 React + TS + Tailwind 代碼。
```

---

## 三、版本控管與迭代

1.  **版本號同步**：
    *   Global 變更（如主色調調整）→ 更新 `v1.0` 到 `v1.1`。
    *   Page 註記：`Using Global System v1.1`。
2.  **組件回饋環 (Feedback Loop)**：
    *   如果 Lovable 在某次生成中產出了極佳的客製化元件，請將其 Pattern 寫回 `global/BASE_DESIGN_SYSTEM.md`，讓下一頁能繼承。

---

## 四、常見錯誤與解決

| 錯誤現象 | 原因分析 | 解決方法 |
| :--- | :--- | :--- |
| **視覺風格漂移** | Page Prompt 寫了太多細節樣式 | 刪除 Page 中的樣式描述，強化 Global 指令 |
| **AI 遺漏功能** | Assembly Prompt 太長（Context 爆掉） | 精簡 Global 內容，只保留該頁面相關的 Tokens |
| **交互邏輯錯誤** | 缺乏 [INTERACTION & STATE FLOW] | 在 Page Spec 中明確定義 Loading/Error 狀態 |

---

## 五、品質門哨 (Quality Gates)

在 Lovable 產出後，請對照 `guides/quality_checklist.md` 檢查：
- [ ] 配色是否完全來自定義的 Tokens？
- [ ] 是否有完善的 Skeleton 載入狀態？
- [ ] RWD 斷點在 1280px / 768px 是否行為正確？

---
最後更新：2024-12-16 | 維護：Prompt Architect Team

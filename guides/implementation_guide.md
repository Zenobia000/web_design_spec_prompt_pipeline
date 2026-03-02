# 📘 Prompt Architect Pipeline - 實施指南

## 一、快速開始

### 1.1 文檔結構概覽
```
prompt_architect_pipeline/
├── global/                    # 全域設計系統 (Soul)
│   └── BASE_DESIGN_SYSTEM.md  # 視覺與交互基準
├── pages/                     # 頁面規格文檔 (Skeleton)
│   ├── 01_dashboard.md        # 範例：儀表板
│   └── page_template.md       # 頁面開發範本
├── assembly/                  # 組裝與調度 (Heart)
│   └── PIPELINE_ORCHESTRATOR.md
└── guides/                    # 指南與品質控管
    ├── implementation_guide.md
    └── quality_checklist.md
```

### 1.2 三層架構說明

1. **Global Layer (全域層)**：定義設計系統 tokens、通用元件行為與技術約束。
2. **Page Layer (頁面層)**：定義特定路由的功能區塊 (Sections)、資料需求與頁面邏輯。
3. **Assembly Layer (組裝層)**：透過 Orchestrator 將 Global 與 Page 合體，生成可供 AI 執行的完整 Prompt。

## 二、實施流程 SOP (The Pipeline)

### Step 1: 初始化全域基準 (Base Tokens)
```markdown
1. 根據專案品牌修改 global/BASE_DESIGN_SYSTEM.md
2. 填入 [PRODUCT CONTEXT LAYER] 中的產品背景
3. 確認技術棧 (React + TS + Tailwind) 與效能指標
```

### Step 2: 定義頁面規格 (Page Spec)
```markdown
1. 使用 pages/page_template.md 建立新頁面規格 (例如：pages/02_analysis.md)
2. 拆解頁面 Section，定義關鍵 Component 與互動
3. 標註資料端點 (API) 與載入狀態要求
```

### Step 3: 動態組裝 (Orchestrate)
```markdown
1. 開啟 assembly/PIPELINE_ORCHESTRATOR.md
2. 將 Global 規範與 Page 規格貼入對應位置
3. 明確指示 AI 按步驟 (結構確認 → 設計說明 → 程式碼生成) 輸出
```

### Step 4: 實作與品質門哨 (Execution & QA)
```markdown
1. 將組裝後的內容貼入 Lovable/Claude/GPT-4
2. 檢查輸出是否完全繼承 Global 的配色與元件風格
3. 使用 guides/quality_checklist.md 進行系統化驗證
```

## 三、最佳實踐 (Best Practices)

### 3.1 Prompt 撰寫準則

**DO ✅**
- **層級明確**：讓 AI 知道 Global 的優先級高於 Page。
- **具體而非抽象**：使用 Hex Code (#1E40AF) 而非描述色 (藍色)。
- **定義狀態**：必須要求 Skeleton 預覽、Error Boundary 與 Empty State。

**DON'T ❌**
- **冗餘描述**：Page 層不應重複 Global 已定義的內容，除非是例外 (Exception)。
- **模糊語義**：避免使用「漂亮的」、「現代的」，改用具體的 UI Pattern 名稱。

### 3.2 協作與維護

- **Single Source of Truth**：所有視覺改動應從 `BASE_DESIGN_SYSTEM.md` 發起。
- **Component Feedback Loop**：當 AI 生成了優秀的客製化元件，應將其 Pattern 記錄回 Global 中。

## 四、常見問題處理 (FAQ)

### Q: 如果 AI 輸出的樣式跑掉了？
**A**: 檢查 Orchestrator 是否過長導致 AI 遺失細節。建議縮減 Global 內容至當前頁面相關的 Tokens。

### Q: 如何處理跨專案的設計？
**A**: 複製整個 `prompt_architect_pipeline` 目錄，針對新專案僅需修改 `global/` 層級。

---
最後更新：2024-12-16
維護者：Prompt Architect Team

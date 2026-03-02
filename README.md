# 📚 Prompt Architect Pipeline - AI 網頁開發流水線

## 🎯 專案概述

本系統採用三層架構（Global → Page → Assembly）將模糊的 PRD 或想法轉化為可執行、一致性高的 AI 開發指令集，確保視覺與邏輯在跨頁面開發中保持統一。

### 核心目標
- 🚀 縮短 AI 輔助開發迭代週期 30% 以上
- 🎨 建立可跨專案複用的 Base Design System
- 🔄 透過 Pipeline Orchestrator 實現動態 Prompt 組裝
- 📋 提供結構化的開發審查流程

## 📁 文檔結構

```
prompt_architect_pipeline/
├── 📘 README.md                          # 本文檔
├── 🌍 global/                           # 全域設計系統 (The Soul)
│   ├── BASE_DESIGN_SYSTEM.md            # [Template] 設計基準範本
│   └── 01_sunny_brand_system.md         # [Example] 桑尼品牌實施範例
├── 📄 pages/                            # 頁面規格文檔 (The Skeleton)
│   ├── 01_dashboard.md                  # [Example] 儀表板規格範例
│   └── page_template.md                 # [Template] 頁面規格範本
├── 🔧 assembly/                         # 整合與調度 (The Heart)
│   ├── PIPELINE_ORCHESTRATOR.md         # [Template] 組裝調度範本
│   └── 01_dashboard_integrated.md       # [Example] 完整組裝 Prompt 範例
└── 📚 guides/                           # 實施指南
    ├── implementation_guide.md          # 實施指南
    └── quality_checklist.md             # 品質檢查清單
```

## 🚀 快速上手：範例導引 (Learn by Example)

如果你是第一次使用，請按照以下順序閱讀，即可理解整套打法：

1.  **看靈魂 (Global)**：
    *   閱讀 `global/01_sunny_brand_system.md`，看我們如何定義品牌色、字體與產品背景。
2.  **看骨架 (Page)**：
    *   閱讀 `pages/01_dashboard.md`，看我們如何將頁面拆解成 5-7 個功能區塊 (Sections)。
3.  **看合體 (Assembly)**：
    *   閱讀 `assembly/01_dashboard_integrated.md`，這就是最終產出的 **"Master Prompt"**。
4.  **動手試試**：
    *   將 `assembly/01_dashboard_integrated.md` 的內容整段複製，貼到 [Lovable](https://lovable.dev/) 或 Claude 中，你就能看到對應的網頁生成！

## 🛠️ 執行 Pipeline (SOP)

1.  **設定基準**：拷貝 `global/BASE_DESIGN_SYSTEM.md` 並修改。
2.  **定義規格**：拷貝 `pages/page_template.md` 定義你的頁面。
3.  **動態組裝**：將兩者填入 `assembly/PIPELINE_ORCHESTRATOR.md`。
4.  **生成程式碼**：將結果交給 AI 執行。

---
最後更新：2024-12-16 | 維護：Prompt Architect Team
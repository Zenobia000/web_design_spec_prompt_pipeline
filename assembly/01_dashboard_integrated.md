# 🚀 EXAMPLE: Integrated Dashboard Prompt (Sunny Hub)

> 此檔案展示如何將 `global/01_sunny_brand_system.md` 與 `pages/01_dashboard.md` 組合起來。這就是你應該貼給 Lovable 或 Claude 的內容。

---

## === GLOBAL PROJECT GUIDELINE (THE SOUL) ===

你是「桑尼資料科學 (Sunny Data Science)」的資深產品架構師。
- **品牌色**: Primary(#F59E0B), Secondary(#1E293B)
- **技術棧**: React 18 + TS + Tailwind CSS
- **核心規範**: 遵循 BASE_DESIGN_SYSTEM.md 定義的 RWD 行為與狀態處理邏輯。

## === CURRENT PAGE SPEC (THE SKELETON) ===

本次任務是實作「Sunny AI Learning Hub 首頁儀表板」。

### [PAGE META]
- page_name: Sunny AI Hub Dashboard
- route_path: /dashboard
- primary_goal: 提供學員專案進度與快捷學習路徑

### [STRUCTURE: SECTIONS]
1. **welcome_header**: 歡迎學員，展示本週學習時數。
2. **quick_actions**: 上傳作業、查看課程、進入社群、我的最愛。
3. **active_learning**: 進行中的課程與學習進度條。
4. **metrics_overview**: 總完成課程數、累積學習時數、技術雷達圖。

### [COMPONENT SPEC]
- **Sidebar**: 深色 (#1E293B)，固定於左側。
- **ActionCards**: 白色背景，Hover 時邊框變為 Sunny Orange (#F59E0B)。

## === OUTPUT REQUIREMENTS ===

1. **結構確認**: 列出 4 個 sections 及其關鍵元件。
2. **設計決策**: 說明如何透過顏色傳達「熱情與專業並重」。
3. **程式碼**: 產出完整 React + TS + Tailwind 代碼，並使用 Recharts 實作指標圖表。

---
*組裝日期: 2024-12-16 | 負責人: Sunny*

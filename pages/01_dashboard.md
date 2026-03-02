# 📄 Page-Level Prompt: 首頁儀表板

## [PAGE META]
- **page_name**: RD 設計審查 Copilot 首頁
- **route_path**: `/dashboard`
- **page_type**: dashboard
- **primary_goal**: 提供專案總覽與快速進入各功能模組的入口
- **secondary_goal**: 展示近期活動與重要通知

## [USER CONTEXT]
- **target_user_segment**:
  - 主要：已登入的 RD 工程師（每日使用）
  - 次要：PM 查看專案進度
- **entry_point**:
  - 登入後直接導向
  - 從任何頁面點擊 Logo 返回
- **expected_time_on_page**: 30秒-2分鐘（快速瀏覽後進入具體功能）

## [STRUCTURE: SECTIONS]
1. **welcome_header**
   - section_type: hero
   - section_purpose: 個人化歡迎訊息與快速統計

2. **quick_actions**
   - section_type: action_cards
   - section_purpose: 提供最常用功能的快捷入口

3. **active_projects**
   - section_type: project_list
   - section_purpose: 顯示進行中的設計審查專案

4. **recent_analyses**
   - section_type: history_list
   - section_purpose: 最近的分析紀錄與結果快速訪問

5. **metrics_overview**
   - section_type: stats_cards
   - section_purpose: 展示使用統計與效益指標

6. **notifications_panel**
   - section_type: notification_list
   - section_purpose: 系統通知與協作訊息

## [SECTION COMPONENT SPEC]

### Section: welcome_header
- **layout**: 全寬單欄，左對齊
- **elements**:
  - greeting_text: h1, required, "歡迎回來，{userName}"
  - date_time: text, required, 當前日期時間
  - quick_stats: stats_row, required, "今日分析: {count} | 本週節省: {hours}小時"
- **states**:
  - 正常：顯示個人化資訊
  - loading：顯示 skeleton
- **copy_constraints**:
  - 使用者名稱最多 20 字元

### Section: quick_actions
- **layout**: 1行4列卡片網格（桌面）/ 2x2（平板）
- **elements**:
  - upload_card: ActionCard, required,
    - icon: CloudUploadIcon
    - title: "上傳新設計"
    - description: "上傳 STEP/BOM 檔案"
    - action: navigate to `/upload`
  - review_card: ActionCard, required,
    - icon: ClipboardCheckIcon
    - title: "設計審查"
    - description: "執行多維度審查"
    - action: navigate to `/review`
  - compare_card: ActionCard, required,
    - icon: ScaleIcon
    - title: "方案比較"
    - description: "比較設變方案"
    - action: navigate to `/compare`
  - knowledge_card: ActionCard, required,
    - icon: BookOpenIcon
    - title: "知識庫"
    - description: "查看案例與專利"
    - action: navigate to `/knowledge`
- **states**:
  - hover: 卡片陰影加深，輕微上移
  - click: 顯示 loading 狀態
  - disabled: 灰度顯示（權限不足時）

### Section: active_projects
- **layout**: 單欄列表，最多顯示 5 項
- **elements**:
  - section_title: h2, required, "進行中專案"
  - project_items: ProjectRow[], required,
    - project_name: text, required
    - status_badge: StatusBadge, required (設計中/審查中/待確認)
    - progress_bar: ProgressBar, optional
    - last_updated: text, required
    - quick_actions: ButtonGroup (檢視/編輯/封存)
  - view_all_link: Link, required, "查看全部 →"
- **states**:
  - empty: 顯示「尚無進行中專案」+ 新增按鈕
  - loading: skeleton rows
  - error: 錯誤訊息 + 重試按鈕

### Section: recent_analyses
- **layout**: 時間軸式列表
- **elements**:
  - section_title: h2, required, "最近分析"
  - analysis_items: AnalysisCard[], required,
    - timestamp: text, required
    - analysis_type: tag, required (成本分析/重量優化/NVH評估)
    - summary: text, required, 最多 100 字
    - result_preview: MiniChart, optional
    - open_button: IconButton, required
- **states**:
  - 展開：顯示詳細圖表
  - 收合：僅顯示摘要
- **copy_constraints**:
  - 摘要保持在 2 行以內

### Section: metrics_overview
- **layout**: 1行4列指標卡片
- **elements**:
  - total_analyses: MetricCard, required,
    - label: "總分析次數"
    - value: number
    - trend: percentage (vs 上月)
  - time_saved: MetricCard, required,
    - label: "節省時間"
    - value: "{hours} 小時"
    - trend: percentage
  - cost_reduction: MetricCard, required,
    - label: "成本降低"
    - value: currency
    - trend: percentage
  - success_rate: MetricCard, required,
    - label: "方案採用率"
    - value: percentage
    - trend: up/down arrow
- **states**:
  - loading: 顯示 skeleton
  - hover: 顯示詳細說明 tooltip

### Section: notifications_panel
- **layout**: 右側固定面板（可收合）
- **elements**:
  - panel_header: h3, required, "通知"
  - notification_list: NotificationItem[], required,
    - icon: Icon, required (依類型)
    - message: text, required
    - time_ago: text, required
    - action_button: Button, optional
  - mark_all_read: TextButton, required
- **states**:
  - 未讀：藍點標示
  - 已讀：正常顯示
  - 空：顯示「無新通知」

## [INTERACTION & STATE FLOW]
- **主要互動流程**：
  1. 頁面載入 → 獲取使用者資料與專案列表
  2. 點擊快捷卡片 → 導航至對應功能
  3. 專案列表互動 → 快速操作或進入詳情
  4. 通知互動 → 標記已讀或執行操作

- **資料更新策略**：
  - 專案列表：每 30 秒自動更新
  - 通知：WebSocket 即時推送
  - 指標數據：每 5 分鐘更新

- **RWD 行為差異**：
  - Desktop (>1280px)：完整 4 欄布局
  - Tablet (768-1280px)：2 欄布局，通知面板預設收合
  - Mobile (<768px)：不支援（提示使用桌面版）

## [DATA & API]
- **uses_api**: true
- **endpoints**:
  - GET `/api/dashboard/overview` - 取得儀表板資料
  - GET `/api/projects/active` - 取得進行中專案
  - GET `/api/analyses/recent` - 取得最近分析
  - GET `/api/metrics/summary` - 取得統計指標
  - GET `/api/notifications` - 取得通知列表
- **error cases**:
  - 網路錯誤：顯示離線模式，使用快取資料
  - API 錯誤：顯示錯誤訊息，提供重試
  - 權限不足：導向登入頁

## [EXCEPTION TO GLOBAL RULES]
無特殊例外，完全遵循 Global System Prompt 規範。

## [ACCEPTANCE CRITERIA]
- [ ] 所有快捷操作可正常導航
- [ ] 專案列表正確顯示狀態與進度
- [ ] 資料自動更新機制正常運作
- [ ] 響應時間 < 2 秒
- [ ] 符合 WCAG 2.1 AA 標準
# 萱草日签 (Daylily Daily) 首页原型实现计划

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 构建高度还原设计规约的“我优先”首页原型 (01-home.html)，包含巨大的打卡按钮、混合任务队列和底部导航栏。

**Architecture:** 单页面 HTML 原型，利用 Tailwind CSS 配合项目已有的 CSS 变量主题（default.css）进行样式控制。模拟移动端容器视图。

**Tech Stack:** HTML5, CSS3, Tailwind CSS (via CDN), Vanilla JS.

---

### Task 1: 基础结构与移动端容器适配

**Files:**
- Create: `prototypes/daylily-daily/01-home.html`

- [ ] **Step 1: 创建 HTML 骨架，配置 Tailwind 和主题引用**
引用 `themes/default.css`，设置 375px * 812px 的移动端模拟容器。

- [ ] **Step 2: 编写基础样式 (Reset & Layout)**
确保容器内溢出滚动（隐藏滚动条），并预设暗色模式支持。

### Task 2: 底部导航栏与顶部状态栏

**Files:**
- Modify: `prototypes/daylily-daily/01-home.html`

- [ ] **Step 1: 编写 iOS 风格状态栏**
模拟时间、信号、电量显示。

- [ ] **Step 2: 编写三段式底部导航栏**
实现“日历 - 首页(核心) - 我的”布局，首页项保持高亮，图标使用 SVG。

### Task 3: 核心打卡区 (Me-First Hero Button)

**Files:**
- Modify: `prototypes/daylily-daily/01-home.html`

- [ ] **Step 1: 实现巨大的圆形打卡按钮**
视觉重心位于上半部分。文案：“我吃过了”；副标题：“降压药 1片”。

- [ ] **Step 2: 编写按钮状态切换逻辑**
使用 JS 监听点击事件，点击后按钮从“暖橙（待办）”变为“浅绿（完成勋章态）”。

### Task 4: 混合任务队列 (Priority Queue)

**Files:**
- Modify: `prototypes/daylily-daily/01-home.html`

- [ ] **Step 1: 编写 Top 3 任务队列容器**
位于大按钮下方，标题为“接下来”。

- [ ] **Step 2: 实现三种类型的任务卡片**
1. 我的下一个任务（实色图标）。
2. 家人漏服提醒（头像前缀 + 红点 + 醒目操作）。
3. 家人即将到来的任务（头像前缀 + 柔和色彩）。

### Task 5: 今日进度时间线 (Daily Timeline)

**Files:**
- Modify: `prototypes/daylily-daily/01-home.html`

- [ ] **Step 1: 实现底部的点状时间线**
在底部导航栏上方，展示全天 4-5 个时间点的打卡状态。

### Task 6: 交互细节与视觉打磨

**Files:**
- Modify: `prototypes/daylily-daily/01-home.html`

- [ ] **Step 1: 完善按钮点击反馈**
添加缩放（Scale）和阴影变化的交互感。

- [ ] **Step 2: 检查微信小程序设计规范适配**
确保圆角、间距（Padding/Gap）符合 750rpx (375px) 的设计美学。

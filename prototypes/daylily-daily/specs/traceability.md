# 交付追溯表 (Traceability) — daylily-daily

## 元数据

| 字段 | 内容 |
|------|------|
| project_code | daylily-daily |
| req-specs 基线 | `23aa4de`（随主仓子模块指针升级请更新） |
| 最后更新 | 2026-04-29 |

## 索引表

| 原型页面 | 主要 req-specs 引用（路径） | 屏幕契约 | 页面状态清单 | DDR | 备注 |
|----------|------------------------------|----------|--------------|-----|------|
| `index.html` | — | — | — | — | **待补**：项目入口导航 |
| `01-home.html` | `req-specs/…/flow-reminder-entry-punch.md`；`…/v1-state-data-rules.md`；`…/medication-plan/v1-user-journey-touchpoints.md`；`…/exception-remediation/…/flow-touch-failure-fallback.md` | `specs/01-home-screen-contract.md` | `specs/01-home-page-states.md` | `design-decisions/01-uiux-consensus-ddr.md` | 首页已补齐规格 |
| `02-profile.html` | 待认领域 | 待建 | 待建 | `design-decisions/02-profile-page-ddr.md` | |
| `03-plan-list.html` | 待认领 | 待建 | 待建 | 见 design-decisions | |
| `04-plan-create.html` | `medication-plan` 流程分册 | 待建 | 待建 | 待对齐 DDR | |
| `05-family-exceptions.html` | `exception-remediation` | 待建 | 待建 | `05-…-ddr` | |
| `06-calendar.html` | `adherence-punch` flow-calendar | 待建 | 待建 | `06-calendar-ddr.md` | |
| `07-help-feedback.html` | — | 待建 | 待建 | `07-08-help-and-voting-ddr.md` | |
| `08-feature-voting.html` | — | 待建 | 待建 | 同上 | |
| `09-family-management.html` | `care-group-identity` | 待建 | 待建 | `09-family-management-ddr.md` | |
| `10-family-groups-list.html` | 同上 | 待建 | 待建 | `10-family-groups-list-ddr.md` | |
| `11-pro-landing.html` | — | 待建 | 待建 | — | |
| `12-pro-setup.html` | — | 待建 | 待建 | — | |

## 角色权限矩阵位置

- **文件路径**：`specs/role-permission-matrix.md`（随页面迭代扩展）

## 本期迭代范围外（可选）

| 页面或能力 | 原因 | 计划迭代 |
|------------|------|----------|
| — | — | — |

## 变更记录

| 日期 | 作者 | 摘要 |
|------|------|------|
| 2026-04-29 | — | 建立追溯表；完成首页行 |

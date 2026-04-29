# 交付规格模板说明

本目录提供与 [AGENTS.md](../AGENTS.md) 中「交付研发标准」对应的 **Markdown 模板**。**不要**在本目录内直接填写业务内容；请复制到具体项目的 `prototypes/<project_code>/specs/` 后再编辑。

## 使用步骤

1. 选定 `project_code`（如 `daylily-daily`）。
2. 在 `prototypes/<project_code>/specs/` 下创建文件，从下列模板 **复制全文**：
   - 单页交付：`06-calendar-screen-contract.md` ← `screen-contract.template.md`
   - 同页状态：`06-calendar-page-states.md` ← `page-states-checklist.template.md`
3. 产品线级权限表：复制 `role-permission-matrix.template.md` 为 `role-permission-matrix.md`（或按模块拆分，但在 `traceability` 中声明路径）。
4. 复制 `traceability.template.md` 为 `traceability.md`，随迭代更新行。
5. 在屏幕契约头部填写 `req-specs` 提交基线与交叉引用；枚举与权限以子模块为准，此处写**视图层翻译与补充条件**。

## 文件一览

| 模板文件 | 用途 |
|----------|------|
| `screen-contract.template.md` | 单屏数据范围、控件逻辑、与 req-specs/DDR 引用 |
| `page-states-checklist.template.md` | 加载 / 权限 / 业务空态 / 错误等状态勾选 |
| `role-permission-matrix.template.md` | 角色 × 页面或模块 × 可见性与动作 |
| `traceability.template.md` | 页面与规格、DDR、清单的索引表 |

## 与 design-decisions 的关系

体验取舍、与 `req-specs` 暂时不一致的拍板、纯视觉规范放在 `design-decisions/`；**可测试的数据条件与状态分支**优先落在 `specs/` 的屏幕契约与状态清单中，并在 DDR 中链接回契约以免重复矛盾。

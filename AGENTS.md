# Project Agents & Collaboration Guidelines

本文档定义了本项目中关于原型开发、**交付研发所需的规格工件**以及多产品线协作的规范性约束，供所有协作成员（包括 AI Agent 和人类开发者）遵循。

## 1. 原型目录结构规范 (Prototype Structure)

所有页面原型必须存放在根目录下的 `prototypes/` 文件夹中，并遵循“资产自治型”结构：

```text
prototypes/
└── <project_code>/              # 必须使用内部项目代号（如: daylily-daily）
    ├── prd/                     # 产品需求文档、介绍及正式文件（可与 req-specs 对照的摘要或快照）
    ├── specs/                   # 与页面对齐的交付规格（见本文第 4 节），从仓库根目录 templates/ 复制模板后填写
    ├── design-decisions/        # Design Decisions Record (DDR)，体验取舍与例外说明
    ├── styles/                  # 该项目专属的 CSS 资源
    ├── assets/                  # 该项目专属的图片、图标等媒体资源
    ├── themes/                  # （可选）该项目专属主题；若仅用根级 themes/ 可省略
    ├── index.html               # 项目入口/导航页面（须可遍历本期对外页面，建议注明 req-specs 基线）
    └── <page_name>.html         # 具体功能原型页面（语义化命名，可用编号前缀便于排序）
```

新建项目时：除 `styles/`、`assets/` 外，应初始化 **`specs/`**（至少放入本迭代涉及的屏幕契约与状态清单占位，随迭代补齐），并按需建立 **`design-decisions/`**。

## 2. 核心约束 (Core Constraints)

*   **命名约定**：
    *   项目文件夹：必须使用小写字母、数字和连字符（kebab-case）。
    *   页面文件：必须具有语义化，如 `user-profile.html`，避免 `test1.html`。
    *   **规格文件**：与某原型页面对齐时，建议使用可排序前缀与页面一致，例如页面 `06-calendar.html` 对应 `specs/06-calendar-screen-contract.md`。
*   **资源引用规范**：
    *   **私有优先**：原型页面应优先引用所属项目 `styles/` 下的 CSS，以保证独立样式不污染全局。
    *   **全局样式**：引用根目录全局 Design System（`themes/`）时，必须使用相对路径 `../../themes/xxx.css`（以实际目录层级为准）。
*   **自治原则**：不同项目代号文件夹应视为独立的沙盒，禁止跨项目引用 `prototypes/<other_project>/` 下的私有资源。
*   **真相来源**：
    *   业务实体、枚举、权限边界、端到端规则以 **`req-specs/` 子模块**为准；主仓不得长期复制大块规格代替子模块。
    *   **单一屏幕上的数据范围、控件状态逻辑、页面状态分支、角色可见性翻译**以本项目 **`specs/`** 与 **`design-decisions/`** 为准，并与 `req-specs` 交叉引用（路径 + 锚点或章节名）。

## 3. 协作流程 (Workflow)

1.  **新建项目**：创建新的 `<project_code>` 文件夹并初始化 `styles/`、`assets/`、`specs/`、`design-decisions/`（按需）。
2.  **规格先行**：在锁定或认领的 `req-specs` 提交基线上工作；对每个进入本期交付范围的对外页面，维护对应的 **屏幕契约**（`specs/*-screen-contract.md`），并配套 **页面状态清单** 与 **角色权限矩阵**（见本文第 4 节）。
3.  **样式与主题**：如需定制样式，在项目私有 CSS 中编写，或在 HTML 中按需引用全局主题；视觉特例与偏离须在 DDR 中记录。
4.  **原型佐证**：高保真 HTML 用于布局、关键交互与**主路径及代表性状态**的例证；不得以「仅更新 HTML」代替对 `specs/` 中文档的更新。
5.  **追溯与导航**：在 `index.html` 或 `specs/traceability.md` 中维护页面与 `req-specs`、`specs`、DDR 的对应关系；重大结构变更应更新 `docs/superpowers/specs/` 下对应的设计规范文档（若适用）。

## 4. 交付研发标准 (Definition of Ready for Engineering)

以下工件为**默认必含项**；产品负责人可向团队声明某迭代缩减范围，但须在 PR 或迭代说明中逐项写明豁免理由。

### 4.1 屏幕契约 (Screen Contract)

*   **文件**：`prototypes/<project_code>/specs/<prefix>-<page-slug>-screen-contract.md`（从仓库根目录 **`templates/screen-contract.template.md`** 复制）。
*   **必须覆盖**：
    *   与 `req-specs` 的交叉引用及采纳的提交基线说明；
    *   本页展示**数据范围**（来源对象、筛选、排序、上限、时间窗、空数据与无权限的区分策略）；
    *   标签、按钮、徽章等控件的 **状态与控制逻辑**（条件、阈值、枚举引用、可点性与跳转）；复杂时可用决策表；
    *   **非目标与假设**（国际化、无障碍、离线等若本期不做须写明）。
*   **与原型关系**：HTML 演示主路径及若干关键状态；契约中未写明但出现在原型里的行为，视为**未完成交付**。

### 4.2 页面状态设计清单 (Page States Checklist)

*   **文件**：与页面对应的 `specs/<prefix>-<page-slug>-page-states.md`，或由模块级一份清单覆盖多页（须在屏幕契约中引用其节或锚点）。模板： **`templates/page-states-checklist.template.md`**。
*   **必须逐项勾选或显式豁免**：数据加载与刷新、权限与角色、业务空态与部分失败、网络与超时重试等；豁免项须写「理由 / 责任方 / 计划补齐迭代」。

### 4.3 角色与权限矩阵 (Role–Permission Matrix)

*   **文件**：按产品线或迭代粒度维护，例如 `specs/role-permission-matrix.md`（可复制 **`templates/role-permission-matrix.template.md`**）。小迭代可在单页契约中嵌套简表，但须在 `specs/` 内可追溯。
*   **必须说明**：每个角色对每一页面或模块的**可见性**与**可操作动作**（读 / 写 / 创建 / 删除等）；与后端或 `req-specs` 权限定义不一致时，以 **DDR** 记录取舍并推动规格收敛。

### 4.4 追溯表 (Traceability)

*   **文件**：`prototypes/<project_code>/specs/traceability.md`（模板 **`templates/traceability.template.md`**），或在 `index.html` 旁以等价表格呈现。
*   **最少列**：原型页面、主要 `req-specs` 路径、屏幕契约、状态清单、DDR、备注。

### 4.5 入口页 (index.html)

*   包含本期所有对接研发的页面链接；
*   建议展示或链接当前采纳的 **`req-specs` 提交短哈希或标签**，与 `specs/` 中基线说明一致。

### 4.6 合并前自检清单（供 Author / Reviewer 使用）

- [ ] 每个对外页面均有对应的 **屏幕契约**，且数据范围与控件逻辑已填写或与 DDR 交叉引用完整。
- [ ] **页面状态清单**已勾选或已文档化豁免项。
- [ ] **角色权限矩阵**已覆盖本期涉及角色与页面 / 模块；与 `req-specs` 冲突处已有 DDR 或已推动规格更新。
- [ ] **追溯表**与 `index.html` 一致，无断链。
- [ ] 未跨 `project_code` 引用私有 `styles/` / `assets/`。

## 5. 根目录模板套件 (Templates)

仓库根目录 **`templates/`** 提供上述工件的 **Markdown 模板**。新页面或新迭代：复制对应 `.template.md` 到目标 `prototypes/<project_code>/specs/`，去掉 `.template` 后缀并按命名约定重命名，再逐项填写。详见 **`templates/README.md`**。

---

*Last Updated: 2026-04-29*

# 本仓库 Monorepo 规范说明

本文档用中文说明 **daylily-daily-uiux** 仓库在「单仓多目录」意义上的组织方式与约定。本仓库并非使用 Nx/Turborepo 等工具链的典型前端 Monorepo，而是以 **目录边界** 划分职责、以 **子模块** 挂载独立规格仓的逻辑 Monorepo。

## 1. 仓库定位

- **主仓职责**：UI/UX 原型、与原型强相关的设计记录、协作规范（如 `AGENTS.md`）。
- **外挂规格仓**：产品共识、领域模型、术语等需求与规格文档，通过 Git **子模块** 固定在 `req-specs/`，与主仓版本通过 **子模块指针（commit）** 关联，而非把规格全文拷贝进主仓。

## 2. 顶层目录结构

```text
daylily-daily-uiux/
├── prototypes/           # 各项目代号下的页面原型（核心交付物）
├── templates/            # 交付研发用规格模板（屏幕契约、状态清单、权限矩阵等），见 AGENTS.md
├── req-specs/            # 子模块：daylily-daily-req-specs（需求与规格）
├── docs/                 # 主仓内设计说明、计划等（如 superpowers 产出）
├── （可选）themes/       # 若放在仓库根，则作为跨原型共享的设计系统样式；当前产品线亦可在 `prototypes/<project_code>/themes/` 维护主题
├── AGENTS.md             # 原型与协作硬性约束（人类与 Agent 均需遵守）
├── MONOREPO_STRUCTURE.md # 本文件
└── README.md             # 克隆与子模块操作说明
```

实际以仓库文件为准；新增顶层目录时，应在本文件补充其职责说明。

## 3. `templates/` 规范

- **职责**：存放从仓库根目录复制的 **Markdown 模板**，用于在 `prototypes/<project_code>/specs/` 中生成屏幕契约、页面状态清单、角色权限矩阵与追溯表。模板内不填写具体业务内容。
- **使用**：见 [templates/README.md](./templates/README.md) 与 [AGENTS.md](./AGENTS.md) 第 4、5 节。

## 4. `prototypes/` 规范（与 AGENTS.md 一致）

- **项目代号目录**：`prototypes/<project_code>/`，`project_code` 为小写字母、数字、连字符（kebab-case），例如 `daylily-daily`。
- **推荐自治结构**：每个项目代号目录内宜包含 `prd/`、`specs/`、`design-decisions/`、`styles/`、`assets/`、`index.html` 及若干语义化页面 `*.html`。具体以 [AGENTS.md](./AGENTS.md) 为准。
- **资源引用**：
  - 优先引用 **本项目** 下 `styles/` 等私有资源，避免样式泄漏到其他项目。
  - 引用「全局主题」时，路径须与仓库真实布局一致；若主题位于仓库根级 `themes/`，从原型 HTML 出发应使用正确的相对路径（例如 `../../themes/xxx.css`）；若主题仅存在于某 `prototypes/<project_code>/themes/`，则仅在该项目内引用，**不得**从其他 `project_code` 目录跨项目引用私有资源。

## 5. `req-specs/` 子模块规范

- **性质**：独立 Git 仓库的只读或受控写入边界；主仓通过 `.gitmodules` 记录 URL 与路径。
- **版本锁定**：主仓某次提交所指向的 `req-specs` 提交 ID 为「当时认可的规格基线」；升级规格应通过更新子模块指针并提交主仓来完成。
- **协作**：在子模块内开发须遵守 **子模块仓库** 自己的分支与评审策略；合并回主仓前需明确主仓是否要 bump 子模块。

## 6. `docs/` 规范

- 用于存放与原型迭代强相关、但不必放入子模块仓的文档（例如某次原型结构的设计说明、实施计划）。
- 重大结构或信息架构变更时，应同步更新 `docs/superpowers/specs/` 等对应说明，避免「代码/原型已变、文档仍旧」。

## 7. 边界与禁止事项

- **禁止** 从 `prototypes/A/` 引用 `prototypes/B/` 下的私有 `styles/`、`assets/`（沙盒隔离）。
- **禁止** 将 `req-specs` 内文档大段复制到主仓替代子模块（除非经产品同意改为单仓维护）；避免双源真相。
- **新增产品线** 时：新建 `prototypes/<new-project-code>/`，按需初始化 `styles/`、`assets/`、`specs/`（可从 [templates/](./templates/) 复制模板），并在 README 或索引页中登记入口（如 `index.html`）。

## 8. 与克隆、CI 的关系

主仓 + 子模块构成完整工作区。克隆与流水线初始化方式见 [README.md](./README.md)。Monorepo 约定不改变 Git 子模块的基本行为：**未初始化子模块时，本地可能缺少 `req-specs` 内容**，属预期现象。

---

*Last Updated: 2026-04-29*

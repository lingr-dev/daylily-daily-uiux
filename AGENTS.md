# Project Agents & Collaboration Guidelines

本文档定义了本项目中关于原型开发和多产品线协作的规范性约束，供所有协作成员（包括 AI Agent 和人类开发者）遵循。

## 1. 原型目录结构规范 (Prototype Structure)

所有页面原型必须存放在根目录下的 `prototypes/` 文件夹中，并遵循“资产自治型”结构：

```text
prototypes/
└── <project_code>/         # 必须使用内部项目代号（如: xuan-cao-v1）
    ├── prd/                # 产品需求文档、介绍及正式文件
    ├── styles/             # 该项目专属的 CSS 资源
    ├── assets/             # 该项目专属的图片、图标等媒体资源
    ├── index.html          # 项目入口/导航页面
    └── <page_name>.html    # 具体功能原型页面（如: login.html）
```

## 2. 核心约束 (Core Constraints)

*   **命名约定**：
    *   项目文件夹：必须使用小写字母、数字和连字符（kebab-case）。
    *   页面文件：必须具有语义化，如 `user-profile.html`，避免 `test1.html`。
*   **资源引用规范**：
    *   **私有优先**：原型页面应优先引用所属项目 `styles/` 下的 CSS，以保证独立样式不污染全局。
    *   **全局样式**：引用根目录全局 Design System（`themes/`）时，必须使用相对路径 `../../themes/xxx.css`。
*   **自治原则**：不同项目代号文件夹应视为独立的沙盒，禁止跨项目引用 `prototypes/<other_project>/` 下的私有资源。

## 3. 协作流程 (Workflow)

1.  **新建项目**：创建新的 `<project_code>` 文件夹并初始化 `styles/` 和 `assets/`。
2.  **样式覆盖**：如需定制样式，在项目私有 CSS 中编写，或在 HTML 中按需引用全局主题。
3.  **文档关联**：重大结构变更应更新 `docs/superpowers/specs/` 下对应的设计规范文档。

---
*Last Updated: 2026-04-08*

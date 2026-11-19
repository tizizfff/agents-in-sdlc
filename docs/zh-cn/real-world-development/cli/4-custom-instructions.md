---
title: "第 4 课：使用自定义指令指导 Copilot"
description: "探索仓库指令，添加文档规范，并将其应用于筛选代码。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

上下文是生成式 AI 工作的关键。任务需要按照特定方式完成时，你应把相应指导提供给 Copilot。[指令文件][instruction-files]不仅说明需要编写哪种代码，还说明代码应如何组织。你已构建筛选功能，现在将探索 Copilot 使用的指令、添加文档规范，并将其应用到代码中。

在本课中，你将：

- 探索仓库指令和路径作用域指令如何传递给智能体。
- 更新指令文件以确保遵循编码规范。
- 查看指令文件对代码的影响。

## 场景

作为一家合格的开发公司，Tailspin Toys 对开发实践有一套指南和要求，包括：

- 注释应解释意图和非显而易见的决策，而不是复述代码。
- `db/` 和 `src/lib/` 中导出的函数应使用 TSDoc/JSDoc 说明用途、参数和返回值；存在可注入 `db` 参数时也应记录。
- 可复用的 Astro 组件应记录 `Props` 协议，并在相关代码变化时更新注释。
- 保留现有格式化和 lint 指导。

通过指令文件，可确保 Copilot掌握正确的信息，并按上述实践执行任务。

## 指令文件

自定义指令用于向 Copilot 提供上下文和偏好，使其更好地理解你的编码风格和需求。它可以提供更相关的建议和代码片段；你可以指定首选编码约定、库以及希望包含的注释类型。指令既可以用于整个仓库，也可以用于特定文件类型。

指令文件分为两类：

- `.github/copilot-instructions.md`：发送给 Copilot 的单个仓库级指令文件，用于仓库中的所有请求。
- `.github/instructions/*.instructions.md`：为特定语言、文件类型或任务提供指导。

> [!NOTE]
> 其他指令格式及支持情况因环境而异。依赖特定格式前，请查阅[自定义指令支持参考][custom-instructions-support]。

## 探索项目中的自定义指令文件

启动项目时已包含一组指令文件。先进行修改前探索它们，以便观察实际影响。

1. 返回 Codespace。
2. 在 Codespaces 编辑器（不要在终端中）打开 `.github/copilot-instructions.md`。
3. 阅读项目简介和编码指导。此指令适用于该仓库中与 Copilot 的所有交互。
4. 打开 `.github/instructions` 文件夹并浏览其中文件，可见 Astro、Drizzle 数据层、测试等方面的指令。
5. 打开 `.github/instructions/unit-tests.instructions.md`，注意顶部的 `applyTo` 字段，它使用 glob确定指令适用的文件。
6. 打开 `.github/instructions/drizzle.instructions.md`，注意它指向其他指令文件和现有项目文件的链接。这样可以拆分大型指令集，并将 Copilot 指向可遵循的示例。

## 更新指令以符合团队要求

现有文件是良好起点，但仍存在缺口。修改核心的 `copilot-instructions.md` 文件，以确保新生成的 TypeScript 包含 TSDoc 注释。

1. 在 `.github/copilot-instructions.md` 中找到标题为 **Code formatting guidance** 的章节，该章节约位于第 35 行附近。
2. 将以下内容作为最后一项添加：

   ```markdown
   - All new TypeScript should contain TSDocs comments for documentation purposes.
   ```

文件会自动保存。

## 使用更新后的指导

Copilot CLI 在对话开始时加载仓库指令。保存更新后的指令后，退出并恢复筛选对话，以便 Copilot 从新指导开始，同时保留功能上下文。

1. 如果筛选对话仍处于打开状态，输入 `/exit`关闭它。Copilot CLI会自动保存对话。
2. 在位于 `game-filters-cli` 分支的仓库根目录恢复保存的对话：

   ```bash
   copilot --resume
   ```

   如果出现提示，请选择筛选对话，并确认已检出 `game-filters-cli` 分支。
3. 请 Copilot应用更新后的指导：

   ```plaintext
   We just updated our instructions and code guidance. Can you please update the code you generated to match that guidance?
   ```

4. 输入 `/diff`并阅读已修改的 TypeScript 文件。注意新生成的 TSDoc 注释，并确认它们准确说明了代码。

## 摘要和后续步骤

你已探索 Copilot CLI 如何从指令文件获取上下文，并将新规范应用到功能中：

- 探索了仓库指令和路径作用域指令如何传递给智能体。
- 更新了指令文件以确保遵循编码规范。
- 查看了指令文件对代码的影响。

接下来，你将[自定义并运行可复用的 quality-checks 技能][next-lesson]，以一致地运行 lint 和测试。

## 资源

- [为 Copilot CLI 添加自定义指令][instruction-files]
- [自定义指令支持][custom-instructions-support]
- [创建自定义指令的最佳实践][instructions-best-practices]
- [Awesome Copilot——指令文件集合][awesome-copilot]

[instruction-files]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/add-custom-instructions
[instructions-best-practices]: https://docs.github.com/copilot/concepts/prompting/response-customization#writing-effective-custom-instructions
[awesome-copilot]: https://awesome-copilot.github.com/
[custom-instructions-support]: https://docs.github.com/copilot/reference/custom-instructions-support
[previous-lesson]: ../3-agent-modes/
[next-lesson]: ../5-agent-skills/

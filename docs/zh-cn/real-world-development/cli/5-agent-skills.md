---
title: "第 5 课：自定义并使用 quality-checks 技能"
description: "探索现有 quality-checks 技能、自定义结果报告格式，并用它验证筛选功能。"
authors:
  - geektrainer
lastUpdated: 2026-09-29
---

编写代码只是工作的一部分。我们已在手动验证代码，并使用指令文件确保其遵循规范；但测试、lint 和持续集成（CI）的其他环节呢？

对于这类任务，**智能体技能**最合适。技能帮助 Copilot了解如何正确运行此类操作。

在本课中，你将：

- 探索现有的 `quality-checks` 技能。
- 自定义结果报告格式。
- 重新加载并运行技能。

## 场景

Tailspin Toys 使用 `quality-checks` 技能运行单元测试、lint 和类型检查。团队希望改进报告，使结果更易于阅读。

## 指令、脚本和资源

智能体技能会按需打包可复用的任务指令、可执行脚本和支持资源。其核心是以技能名称命名的文件夹，其中包含名为 `SKILL.md` 的 Markdown 文件。该 Markdown 使用 frontmatter定义名称和描述，并提供技能概述及调用时机。文件夹还可包含脚本和其他资源的子文件夹。

> [!NOTE]
> 技能不一定需要附加文件夹或文件。Tailspin Toys 的 `quality-checks` 技能只包含 `SKILL.md`，因为它使用项目现有命令。

技能可放在项目的 `.github/skills` 文件夹中，供团队共享和复用，也可放在用户技能目录 `~/.copilot/skills` 中。

## 探索技能

让我们探索 Tailspin Toys 用于运行单元测试、lint 和类型检查的 `quality-checks` 技能。

1. 返回 Codespace，在编辑器中打开 `.github/skills/quality-checks/SKILL.md`。
2. 阅读顶部的 `name` 和 `description`；描述帮助 Copilot了解何时调用该技能。
3. 阅读指令，注意它如何指导 Copilot完成测试和 lint 流程。
4. 注意该技能尚未包含 **Results output formatting**章节。

## 修改前运行技能

技能可直接通过 Copilot CLI调用，也可使用自然语言调用。让 Copilot运行技能中的三项检查。

1. 返回 Interactive 模式的筛选对话。
2. 使用以下提示：

   ```plaintext
   Run the quality-checks skill for unit tests, lint, and type checks.
   ```

3. 注意报告末尾的内容。

## 自定义报告

我们希望获得更好的报告，说明运行了哪些检查、是否成功，以及工具实际报告了什么。

1. 返回 `.github/skills/quality-checks/SKILL.md`。
2. 在文件末尾添加以下章节：

   ```markdown
   ## Results output formatting

   Upon completion, report each command that ran and whether it passed, failed, or was blocked. Include test counts, durations, errors, warnings, and other metrics only when the tool reports them. Identify the next action for any failure or blocker, and never describe a skipped or incomplete check as passed.
   ```

3. 文件会自动保存。

## 运行更新后的技能

完成修改后，看看效果。Copilot CLI无需重启对话即可重新加载已编辑的技能。

1. 输入：

   ```plaintext
   /skills reload
   ```

2. 再次使用原来的提示：

   ```plaintext
   Run the quality-checks skill for unit tests, lint, and type checks.
   ```

3. 注意末尾报告，并与第一次报告比较。

## 摘要和后续步骤

你已自定义并使用现有智能体技能。本课中，你：

- 探索了用于单元测试、lint 和类型检查的 `quality-checks` 技能。
- 自定义了结果报告格式。
- 重新加载并运行了技能。

该变更将与筛选功能一起进入功能 PR。接下来，你将通过 [Playwright MCP 服务器][next-lesson]让 Copilot直接与站点交互。

## 更多技能示例

以下社区示例仅供参考，不是额外任务：

- [智能体技能规范][skill-spec]
- [贡献工作流：`make-repo-contribution`][contribution-example]
- [需求文档：`prd`][prd-example]
- [图表和捆绑导出脚本：`drawio`][drawio-example]
- [浏览器测试：`webapp-testing`][browser-example]

[previous-lesson]: ../4-custom-instructions/
[next-lesson]: ../6-mcp-playwright/
[skill-spec]: https://agentskills.io/specification
[contribution-example]: https://github.com/github/awesome-copilot/tree/main/skills/make-repo-contribution
[prd-example]: https://github.com/github/awesome-copilot/tree/main/skills/prd
[drawio-example]: https://github.com/github/awesome-copilot/tree/main/skills/drawio
[browser-example]: https://github.com/github/awesome-copilot/tree/main/skills/webapp-testing

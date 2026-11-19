---
title: "第 7 课：创建并使用 QA 智能体"
description: "创建结合 issue需求、quality-checks 技能和 Playwright MCP的 QA 自定义智能体。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

你已使用 `quality-checks` 技能运行自动检查，并使用 Playwright MCP在浏览器中观察筛选体验。现在，将这些能力整合到具有明确 QA 流程的自定义智能体中。

在本课中，你将：

- 探索自定义智能体如何使用指令、技能和 MCP工具。
- 创建并检查可复用的质量保证配置。
- 选择 QA 智能体，并根据筛选 issue审查其发现。

## 场景

Tailspin Toys 希望在创建拉取请求（PR）前，始终一致地审查需求、代码质量、自动检查、测试覆盖率和浏览器行为。自定义智能体可以协调 QA流程并提供可复用报告。

## 什么是自定义智能体？

自定义智能体是在 Markdown 配置文件中定义的 Copilot专业化版本。配置描述智能体的用途、指令和可用工具。在本研讨会中，你将在 `.github/agents/qa.agent.md`中定义 QA角色，并在 Copilot CLI中选择它。

你已使用的自定义项各司其职：仓库指令描述团队规范，`quality-checks` 技能打包可重复检查，Playwright MCP提供浏览器工具，QA 配置则说明 Copilot如何利用这些能力评估需求并报告发现。它不会取代这些能力，也不需要另建对话。

## 创建 QA配置

打开功能 PR前，你将请 Copilot创建可复用的 QA配置。该配置将定义 QA执行的检查及其遵循的边界。

1. 返回 Codespace，并确认筛选对话处于 Interactive 模式。
2. 请默认智能体创建新的自定义智能体：

   ```plaintext
   Create a custom agent named QA in .github/agents/qa.agent.md. It should check features against their issues and agreed requirements, follow the repository instructions, run the quality-checks skill, use Playwright MCP to verify behavior, and add tests when coverage is missing.

   Have it report each requirement as pass, fail, or blocked with supporting evidence. It must ask before changing implementation code, and it must not commit changes or open pull requests.

   Just create the profile for now so I can review it.
   ```

## 检查配置

使用新智能体前，请审查其配置，以确认 Copilot已捕获预期 QA工作流和边界。这可防止不完整或权限过大的智能体在只需验证时修改功能。

1. 输入 `/diff`并打开 `.github/agents/qa.agent.md`。
2. 阅读 frontmatter。`description`是必需字段；`name`为可选字段，但包含它可提供清晰的显示名称。
3. 阅读配置指令，确认 QA从需求开始、遵循仓库指令、运行 `quality-checks` 技能并使用 Playwright MCP。
4. 确认 QA会提供支持证据、修改实现代码前先询问，且不会提交或创建拉取请求。
5. 如果生成的配置遗漏了职责或边界，请在继续前请默认智能体修改。

## 根据 issue运行 QA

Copilot CLI会在对话开始时加载项目智能体。创建配置后恢复相同筛选对话，再选择 QA，以便它使用已有的 issue和规划决策。

1. 使用以下提示启用智能体：

   ```plaintext
   /agent QA
   ```

> [!NOTE]
> 刚创建智能体时，它可能不会立即出现在可用智能体列表中，但上述命令会激活它。

2. 使用以下提示，请 QA智能体审查功能：

   ```plaintext
   Review the filtering feature against the issue and the decisions in our plan. Is it ready for a PR?
   ```

3. QA智能体开始工作！
4. 完成后阅读它提供的报告。

## 摘要和后续步骤

你已向工作流添加可复用的专业角色，并审查了其工作。本课中，你：

- 探索了自定义智能体如何使用指令、技能和 MCP工具。
- 创建并检查了可复用的质量保证配置。
- 选择 QA智能体，并根据筛选 issue审查了其发现。

现在，实现、技能更新、QA配置、测试和验证报告都已准备好，可供审查。接下来，你将[在功能 PR中整合这些内容并使用 Agent Merge][next-lesson]。

## 资源

- [为 Copilot CLI创建自定义智能体][create-agents]
- [自定义智能体配置][agent-config]

[previous-lesson]: ../6-mcp-playwright/
[next-lesson]: ../8-create-pull-request/
[create-agents]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/create-custom-agents-for-cli
[agent-config]: https://docs.github.com/copilot/reference/custom-agents-configuration

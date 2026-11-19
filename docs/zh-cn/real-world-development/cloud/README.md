---
slug: zh-cn/real-world-development/cloud
title: "GitHub Copilot 云智能体"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

**[GitHub Copilot云智能体](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent)**让 GitHub Copilot在云端异步工作。你在 GitHub上分配工作，云智能体会在后台探索仓库、进行修改并创建拉取请求，而你可以继续处理其他事项。

通过这些练习，你将添加云智能体遵循的自定义指令，然后分配 GitHub issue并让它实现工作。你会审查并使用自定义智能体塑造其工作方式，在智能体仪表板中监控和引导会话，并通过审查拉取请求和迭代结果结束。

## 练习

| 练习 | 主题 | 描述 |
|------|------|------|
| [0. 准备工作][ex0] | 设置 | 创建仓库和 Codespace |
| [1. 自定义指令][ex1] | 上下文 | 添加云智能体遵循的自定义指令 |
| [2. 云智能体][ex2] | 异步智能体 | 将 issue分配给 Copilot云智能体 |
| [3. 自定义智能体][ex3] | 专业智能体 | 审查并使用自定义智能体 |
| [4. 管理智能体][ex4] | 监控 | 监控和引导智能体会话 |
| [5. 迭代][ex5] | 审查 | 审查 PR、迭代 Copilot的工作并选择后续步骤 |

## 前置条件

参加本研讨会前，请确保：

- [ ] 拥有处于有效状态的 **Copilot Student、Pro、Pro+、Business 或 Enterprise**方案的 GitHub账户。
- [ ] 已为账户或组织启用 Copilot云智能体。

> [!TIP]
> 没有付费方案？通过 [GitHub Education][callout-student-plan-education]，已验证的学生可以免费获得 GitHub Copilot。**Copilot Student**方案包含本研讨会使用的智能体、MCP、代码审查和 Copilot CLI功能，因此可借助该方案完成所有实验。

[callout-student-plan-education]: https://github.com/education/students

> [!NOTE]
> 云智能体适用于 **Copilot Student、Pro、Pro+、Business 和 Enterprise**；Copilot Free除外。在 Copilot Business 或 Enterprise中，管理员必须为组织启用该功能。

> [!NOTE]
> 本实验不涵盖 MCP。如需探索 MCP服务器与 Copilot的配合，请参阅 [CLI实验](../cli/)或 [VS Code实验](../vscode/)。

## 开始

**[从练习 0：准备工作开始 →][ex0]**

[ex0]: 0-prerequisites/
[ex1]: 1-custom-instructions/
[ex2]: 2-cloud-agent/
[ex3]: 3-custom-agents/
[ex4]: 4-managing-agents/
[ex5]: 5-iterating/

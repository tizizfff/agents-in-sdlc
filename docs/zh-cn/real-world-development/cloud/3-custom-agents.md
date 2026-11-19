---
title: "练习 3：自定义智能体"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

## 什么是自定义智能体？

[自定义智能体][custom-agents-concept]让 GitHub Copilot为开发工作流中的特定任务或领域创建专门助手。通过在仓库 `.github/agents`中定义 Markdown文件，可提供聚焦指令、最佳实践、编码模式和领域知识，使智能体更有效地工作。

自定义智能体可在项目 `.github/agents`或全局 `~/.copilot/agents`中定义。文件包含至少具有 `name`和 `description`的 YAML frontmatter，以及定义行为和指令的 Markdown提示。

自定义智能体与[智能体技能][agent-skills-concept]有部分重叠。最清晰的区分是：自定义智能体是执行者，技能是工具。

> [!NOTE]
> 编写自定义智能体没有唯一正确方式，应通过测试和迭代找到适合环境和场景的方法。

[custom-agents-concept]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[agent-skills-concept]: https://docs.github.com/copilot/concepts/agents/about-agent-skills
[wcag]: https://www.w3.org/WAI/standards-guidelines/wcag/

你将探索：

- 如何定义自定义智能体。
- 如何将任务分配给自定义智能体。

## 场景

Tailspin Toys致力于让平台对所有用户可访问。反馈显示，部分用户认为深色主题文字与背景对比度不足。设计团队请求实现可开关的高对比度模式。

由于可访问性至关重要，你将使用自定义智能体生成该功能。

## 审查可访问性自定义智能体

系统已创建可访问性自定义智能体。返回 Codespace并审查：

1. 打开 `.github/agents/accessibility.md`。
2. 注意包含 `name`和 `description`字段的 YAML frontmatter。

> [!CAUTION]
> 自定义智能体必须包含 `name`和 `description`。

3. 阅读其核心职责、可访问性最佳实践、HTML/CSS/JavaScript示例以及常见陷阱。

## 创建并分配 issue

任务控制中心可集中处理环境中的所有智能体。下面分配创建高对比度模式的任务：

1. 打开仓库。
2. 选择 **Issues**标签页。
3. 选择 **New issue**，再选择 **Blank issue**。
4. 标题设为 `Add high contrast mode to website`。
5. 描述设为：

    ```plaintext
    We need a high contrast mode for the site. There should be a toggle for high contrast which the user can set. It should store the setting in local storage on the browser.
    ```

6. 创建 issue。
7. 在右侧选择 **Assign to Copilot**。
8. 从自定义智能体列表选择 **Accessibility agent**。

    ![云智能体分配界面中突出显示自定义智能体和可访问性的截图](../../../_images/ex5-select-custom-agent.png)

9. 选择 **Assign**。Copilot会在后台执行任务！

## 摘要和后续步骤

本课介绍了 GitHub Copilot中的[自定义智能体][custom-agents]：它们是为特定任务和领域定制的专业 AI助手。

你已了解：

- 如何定义自定义智能体。
- 如何将任务分配给自定义智能体。

接下来将[监控并引导智能体会话][next-lesson]。

## 资源

- [关于自定义智能体][custom-agents]
- [组织准备使用自定义智能体][org-custom-agents]
- [企业准备使用自定义智能体][enterprise-custom-agents]

---

| [← 上一课：GitHub Copilot云智能体][previous-lesson] | [下一课：监控和管理智能体 →][next-lesson] |
|:--|--:|

[previous-lesson]: ../2-cloud-agent/
[next-lesson]: ../4-managing-agents/
[custom-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[org-custom-agents]: https://docs.github.com/copilot/how-tos/administer-copilot/manage-for-organization/prepare-for-custom-agents
[enterprise-custom-agents]: https://docs.github.com/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-agents/prepare-for-custom-agents

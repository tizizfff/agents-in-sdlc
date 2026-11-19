---
title: "练习 0：准备工作"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

开始 VS Code练习前，需要先完成准备。你将创建 Tailspin Toys 仓库副本、启动用于工作的 [Codespace][codespaces]，并确认编辑器中的 GitHub Copilot Chat 已正常运行。

## 设置实验仓库

为创建要编写代码的仓库副本，请从[模板][template-repository]创建实例。新实例包含实验所需的全部文件，并将在练习过程中使用。

1. 在新浏览器窗口中打开 [Tailspin Toys模板][tailspin-template]。
2. 在实验仓库页面选择 **Use this template**，再选择 **Create a new repository**，创建仓库副本。

    ![Use this template 按钮](../../../_images/ex0-use-template.png)

3. 如果研讨会由 GitHub 或 Microsoft组织，并由讲师带领，请遵循讲师提供的说明。否则，请在你有权访问 GitHub Copilot的组织中创建仓库。

    ![仓库模板设置输入框](../../../_images/ex0-repository-settings.png)

4. 记下创建的仓库路径（**organization-or-user-name/repository-name**），后续练习会用到它。

> [!NOTE]
> **待办事项已准备就绪**
>
> 使用模板创建仓库时，会自动创建 GitHub issue待办事项。整个研讨会都会使用这些 issue，无需自行创建。

## 创建 Codespace

接下来使用 Codespace完成实验练习。

[GitHub Codespaces][codespaces]是一种云开发环境，可让你直接在浏览器中编写、运行和调试代码。它是功能齐全的 IDE，支持多种编程语言、扩展和工具。

1. 打开新建的仓库。
2. 选择绿色的 **Code**按钮。

    ![选择 Code按钮](../../../_images/ex0-code-button.png)

3. 选择 **Codespaces**标签页，再选择 **+**按钮创建新的 Codespace。

    ![创建新的 Codespace](../../../_images/ex0-create-codespace.png)

Codespace创建可能需要几分钟，但仍比手动安装所有服务快得多。可利用等待时间探索 GitHub Copilot的其他功能；接下来将进行介绍。

> [!CAUTION]
> 你将在后续练习中继续使用此 Codespace。目前请将其保留在浏览器标签页中。

> [!NOTE]
> 本研讨会可在 Codespace或本地 [dev container][dev-containers]中运行。两者都能确保环境具备顺利运行所需的前置条件。如需本地运行，请打开克隆的仓库，并在 VS Code提示时选择 **Reopen in Container**；VS Code会构建与 Codespace相同的 dev container。

[codespaces]: https://github.com/features/codespaces
[dev-containers]: https://code.visualstudio.com/docs/devcontainers/containers

## 使用 GitHub Copilot Chat 和智能体模式

要使用 GitHub Copilot Chat智能体模式，需要在 IDE中安装 GitHub Copilot Chat扩展；在 GitHub Codespace中通常已预装。

> [!TIP]
> 如果尚未安装 GitHub Copilot Chat扩展，可从 [Visual Studio Code Marketplace][copilot-chat-extension]安装，或者在 Visual Studio Code中打开扩展视图，搜索 **GitHub Copilot Chat**并选择 **Install**。

安装扩展后，可能需要使用 GitHub账户进行身份验证。

1. 返回 Codespace。
2. 如果编辑器右侧未显示 Copilot Chat，请选择 Codespace顶部的 **Copilot Chat**图标。
3. 在 Copilot Chat窗口中输入 “Hello world”等消息并按 Enter。此操作应会启动 Copilot Chat。
4. 如果尚未完成身份验证，系统会提示登录 GitHub账户；按照说明完成身份验证。

    ![Copilot Chat身份验证提示示例](../../../_images/ex1-copilot-authentication.png)

5. 身份验证后，应会看到 Copilot Chat窗口。

## 摘要

恭喜，你已创建实验仓库副本，并开始创建 Codespace；后续编写代码时会使用该环境。

## 下一步

让 Copilot开始工作。继续阅读[练习 1：自定义指令][next-lesson]，为项目添加约定。

## 资源

- [GitHub Codespaces 概览][codespaces]
- [通过模板创建仓库][template-repository]
- [Codespaces 入门][codespaces-quickstart]

[tailspin-template]: https://github.com/github-samples/tailspin-toys
[template-repository]: https://docs.github.com/repositories/creating-and-managing-repositories/creating-a-template-repository
[codespaces-quickstart]: https://docs.github.com/codespaces/getting-started/quickstart
[copilot-chat-extension]: https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat
[next-lesson]: ../1-custom-instructions/

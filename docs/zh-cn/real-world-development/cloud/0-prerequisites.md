---
title: "练习 0：准备工作"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

开始 Copilot云智能体练习前，请完成准备：创建 Tailspin Toys仓库副本，并启动可用于编辑指令文件和审查云智能体工作的 [Codespace][codespaces]。

## 设置实验仓库

为你将创建的代码创建仓库副本，请通过[模板][template-repository]创建实例。新实例包含实验所需的全部文件。

1. 在新浏览器窗口中打开 [Tailspin Toys模板][tailspin-template]。
2. 选择 **Use this template**，再选择 **Create a new repository**。

    ![Use this template 按钮](../../../_images/ex0-use-template.png)

3. 如果研讨会由 GitHub 或 Microsoft组织并由讲师带领，请遵循讲师说明。否则，可在你有权访问 GitHub Copilot的组织中创建仓库。

    ![仓库模板设置输入框](../../../_images/ex0-repository-settings.png)

4. 记下仓库路径（**organization-or-user-name/repository-name**），后续会用到。

## 创建 Codespace

下一步使用 Codespace完成实验练习。[GitHub Codespaces][codespaces]是云开发环境，可直接在浏览器中编写、运行和调试代码，并提供多语言、扩展和工具支持。

1. 打开新建的仓库。
2. 选择绿色的 **Code**按钮。

    ![选择 Code按钮](../../../_images/ex0-code-button.png)

3. 选择 **Codespaces**标签页，再选择 **+**创建 Codespace。

    ![创建 Codespace](../../../_images/ex0-create-codespace.png)

创建需要几分钟，但仍比手动安装所有服务快得多。

> [!CAUTION]
> 后续练习会继续使用此 Codespace。目前请将其保留在浏览器标签页中。

> [!NOTE]
> 本研讨会可在 Codespace或本地 [dev container][dev-containers]中运行。两者都能确保环境具备所需前置条件。如需本地运行，请克隆仓库，在 VS Code中提示时选择 **Reopen in Container**。

[codespaces]: https://github.com/features/codespaces
[dev-containers]: https://code.visualstudio.com/docs/devcontainers/containers

## 摘要

恭喜，你已创建实验仓库副本，并开始创建 Codespace；后续将用于与 Copilot云智能体协作。

## 下一步

下面添加云智能体使用的自定义指令。继续阅读[练习 1：自定义指令][next-lesson]。

## 资源

- [GitHub Codespaces 概览][codespaces]
- [通过模板创建仓库][template-repository]
- [Codespaces 入门][codespaces-quickstart]

[tailspin-template]: https://github.com/github-samples/tailspin-toys
[template-repository]: https://docs.github.com/repositories/creating-and-managing-repositories/creating-a-template-repository
[codespaces-quickstart]: https://docs.github.com/codespaces/getting-started/quickstart
[next-lesson]: ../1-custom-instructions/

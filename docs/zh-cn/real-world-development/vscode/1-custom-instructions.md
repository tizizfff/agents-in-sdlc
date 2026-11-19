---
title: "练习 1：自定义指令（VS Code）"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← 上一课：准备工作][previous-lesson] · [下一课：智能体模式 →][next-lesson]

使用生成式 AI时，上下文至关重要。如果任务需要按特定方式完成，或 Copilot需要了解背景信息，就应确保上下文可访问。可通过多种方式向 Copilot提供特定上下文，其中最重要的是[指令文件][instruction-files]，用于指导代码生成。

在本练习中，你将：

- 探索仓库自定义指令和路径作用域指令如何向 Copilot传递项目上下文、编码指南和文档规范。
- 使用现有指令生成筛选功能的首个数据切片（发行商辅助函数）。
- 向 `.github/copilot-instructions.md`添加一项仓库级标准。
- 重运行相同提示，并观察生成代码采用新标准。
- 将指令更新和筛选切片提交到 `main`，供下一练习使用更新后的指导。

> [!CAUTION]
> 生成代码可能偏离你设定的部分标准。Copilot具有非确定性。本练习的重点是观察更新指令后行为趋势的变化，而不是逐字符匹配输出。

## 指令文件

### 场景

作为一家合格的开发公司，Tailspin Toys对开发实践有一套指南和要求，包括：

- 数据层始终需要单元测试。
- UI应采用深色模式并具有现代感。
- 应使用 TSDoc文档注释将文档添加到代码中。
- 应在每个文件顶部添加说明文件用途的注释块。

通过指令文件，可确保 Copilot掌握与上述实践一致的正确信息。

### 自定义指令

自定义指令用于向 Copilot提供上下文和偏好，使其更好地理解编码风格和需求。可通过首选编码约定、库或注释类型引导 Copilot提供更相关的建议和代码片段。指令可覆盖整个仓库，也可针对特定文件类型提供任务上下文。

指令文件分为两类：

- `.github/copilot-instructions.md`：发送给 Copilot的单个仓库指令文件，适用于仓库中的每个请求。应包含项目级信息，如技术栈、正在构建的内容、最佳实践和全局指导。
- `.github/instructions/*.instructions.md`：为特定任务或文件类型提供指南，例如 TypeScript、Astro或新单元测试。

> [!NOTE]
> 在 IDE中工作时，指令文件仅用于 Copilot Chat中的代码生成，不用于代码补全或下一编辑建议。
>
> Copilot Chat、Copilot CLI 和 Copilot云智能体在生成代码时都会使用仓库级指令和带 `applyTo`frontmatter的 `*.instructions.md`文件。
>
> 此外，Copilot[支持使用其他标准的指令文件][custom-instructions-support]，包括 `AGENTS.md`和 `CLAUDE.md`。

### 管理指令文件的最佳实践

创建指令文件的完整讨论超出了研讨会范围。示例项目展示了一种典型方法：

- 保持 `copilot-instructions.md`聚焦项目级指导，例如项目内容、结构和全局编码规范。
- 使用 `*.instructions.md`为文件类型（单元测试、Astro组件、数据层）或特定任务提供具体指令。
- 使用自然语言，提供清晰指导，并给出代码应当或不应当采用的示例。

指令文件没有唯一创建方式，就像使用 AI没有唯一方式一样。应通过实验找到最适合项目的方法。

> [!TIP]
> 使用 GitHub Copilot的每个项目都应包含一组完善的指令文件。浏览项目中的指令时，可看到针对 [UI更新][ui-instructions]、[Astro][astro-instructions]等任务的文件。

[ui-instructions]: https://github.com/github-samples/tailspin-toys/blob/main/.github/instructions/ui.instructions.md
[astro-instructions]: https://github.com/github-samples/tailspin-toys/blob/main/.github/instructions/astro.instructions.md
[awesome-copilot]: https://github.com/github/awesome-copilot
[custom-instructions-support]: https://docs.github.com/copilot/reference/custom-instructions-support

## 探索项目中的自定义指令

花一点时间阅读仓库提供的指令：有一个核心 `copilot-instructions.md`及针对各种任务的 `*.instructions.md`文件。

1. 打开 `.github/copilot-instructions.md`。
2. 浏览项目简介以及 **Agent notes**、**Code standards**、**Scripts**和 **Repository Structure**等章节。
3. 打开 `.github/instructions`文件夹，注意其中包含 Astro、Drizzle数据层、测试等指令。
4. 打开 `.github/instructions/unit-tests.instructions.md`，顶部的 `applyTo`字段使用 glob确定适用的文件，例如 `**/*.test.ts`。
5. 阅读本项目创建单元测试的具体指令。
6. 打开 `.github/instructions/drizzle.instructions.md`并滚动到底部，查看指向其他指令文件和现有项目文件的链接。

> [!NOTE]
> `copilot-instructions.md`中的 **Code formatting requirements**记录了项目编码规范，但尚未要求在代码中编写文档。下一步将添加 TSDoc注释和文件注释头规则。

## 创建变更分支

遵循最佳实践，为变更创建分支。

1. 返回上一练习的 Codespace。
2. 按 <kbd>Control</kbd>+<kbd>`</kbd>（Mac）或 <kbd>Ctrl</kbd>+<kbd>`</kbd>（Windows/Linux）打开新终端。
3. 创建并切换到新分支：

   ```bash
   git checkout -b custom-instructions
   ```

## 更新指令前使用 Copilot Chat

> [!TIP]
> **打开 Copilot Chat**
>
> 开始下面的练习前，请返回 Codespace、打开 Copilot Chat面板并选择 **New Chat**。

先在现有指令下发送提示，再更新指令并发送相同提示，以观察差异。

1. 关闭之前练习的编辑器标签页，只保留 Copilot需要的上下文。
2. 打开 `src/lib/publishers.ts`，让 Copilot知道辅助函数应位于何处。
3. 在聊天视图的智能体下拉列表中选择 **Agent**。

   ![聊天视图中智能体选择器的截图](../../../_images/shared-chat-mode-selector.png)

4. 发送以下提示：

   ```plaintext
   Create or update src/lib/publishers.ts with a data-access helper that returns a list of all publishers with the name and id for each. Apply the file changes.
   ```

5. Copilot会探索项目并应用代码更新，通常涉及辅助函数和测试。
6. 建议的辅助函数是带类型的函数，首个参数为 `db`客户端，并返回带类型的发行商数组；这是来自 `.github/instructions/drizzle.instructions.md`的约定。
7. 建议代码缺少 TSDoc文档注释和文件级注释头。

> [!CAUTION]
> 因为 Copilot具有概率性，即使未明确要求，它也可能添加文档注释。如果发生这种情况仍属正常；更新指令后应观察一致性的改善。

## 添加仓库级新标准

如前所述，`.github/copilot-instructions.md`用于向 Copilot提供项目级信息。为改进代码建议，应将仓库编码规范记录下来。

1. 重新打开 `.github/copilot-instructions.md`。
2. 找到位于约第 27 行附近的 **Code formatting requirements**章节。
3. 在现有规范下方添加：

   ```markdown
   - Every exported function should have a TSDoc comment describing its purpose, parameters, and return value.
   - Before imports or any code, add a comment block to the file that explains its purpose.
   ```

4. 保存 `copilot-instructions.md`。

## 重运行提示并观察变化

1. 返回 Copilot Chat并选择 **New Chat**清空缓冲区。
2. 回到 `src/lib/publishers.ts`以聚焦正确文件。
3. 发送与之前相同的提示：

   ```plaintext
   Create or update src/lib/publishers.ts with a data-access helper that returns a list of all publishers with the name and id for each. Apply the file changes.
   ```

4. 建议文件现在应以类似注释块开头：

   ```typescript
   /**
    * Publisher data-access helpers for the Tailspin Toys Crowd Funding platform.
    * Provides functions to retrieve publisher information from the database.
    */
   ```

5. 建议函数应包含类似以下 TSDoc注释：

   ```typescript
   /**
    * Returns a list of all publishers with their id and name.
    *
    * @param db - The Drizzle database client.
    * @returns A promise that resolves to an array of publisher objects.
    */
   ```

你已引导 Copilot遵循新的项目标准，并将其应用到下一练习会继续使用的实际代码中。

## 提交指令并推送分支

指令文件和仓库中的其他资产一样，使用相同源代码管理方式管理。

1. 按 <kbd>Control</kbd>+<kbd>\`</kbd>（Mac）或 <kbd>Ctrl</kbd>+<kbd>\`</kbd>（Windows/Linux）打开新终端。
2. 运行 `git status`确认指令更新和辅助函数变更。

   ```bash
   git status
   ```

3. 暂存并提交指令更新及 Copilot为辅助函数基础修改的所有文件：

   ```bash
   git add .github/copilot-instructions.md src/lib/publishers.ts
   git commit -m "Add doc comment standards and publishers helper foundation"
   ```

4. 推送分支：

   ```bash
   git push -u origin custom-instructions
   ```

## 创建并合并拉取请求

分支已推送后，应创建拉取请求，并关联待办事项中的文档规范 issue。让 Copilot使用已连接的 GitHub工具完成查找和合并。

1. 在 Codespace中打开 Copilot Chat。
2. 按 <kbd>Control</kbd>+<kbd>Command</kbd>+<kbd>I</kbd>（Mac）或 <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>I</kbd>（Windows/Linux）打开聊天视图，并确保选择 **Agent**。
3. 请 Copilot查找更新指令文件相关的 issue，并从当前分支创建 PR：

   ```text
   Find the issue related to updating the instructions file. Create a new PR from the current branch, highlight that the PR closes that issue, and include that we also added the publishers helper foundation for the upcoming filtering work.
   ```

4. Copilot开始查找 issue并创建 PR。
5. 当提示 **Allow** Copilot代表你执行 GitHub操作时，审查命令并选择允许。
6. PR创建后，请 Copilot合并 PR并将本地分支切回 `main`：

   ```text
   Merge the PR into main. Then return to main locally, and pull the latest code so we are up to date.
   ```

你现在已借助 GitHub Copilot创建并合并拉取请求！

## 摘要和后续步骤

你已了解 Copilot如何从项目指令文件获取上下文，并在 VS Code中使用 Copilot Chat：

- 发送代码生成提示并观察现有指令下的结果。
- 向 `.github/copilot-instructions.md`添加仓库级标准。
- 重运行相同提示并观察建议代码采用新标准。
- 将指令更新和辅助函数基础提交到 `main`，供下一练习使用。

接下来，在[智能体模式][next-lesson]中应用这些指令，让 Copilot跨代码库添加新功能。

## 资源

- [为 GitHub Copilot自定义指令文件][instruction-files]
- [创建自定义指令的最佳实践][instructions-best-practices]
- [编写更好自定义指令的 5个技巧][copilot-instructions-five-tips]
- [GitHub Copilot个人自定义指令][personal-instructions]
- [Awesome Copilot——指令文件集合][awesome-copilot]

[previous-lesson]: ../0-prerequisites/
[next-lesson]: ../2-agent-mode/
[instruction-files]: https://code.visualstudio.com/docs/copilot/copilot-customization
[instructions-best-practices]: https://docs.github.com/enterprise-cloud@latest/copilot/using-github-copilot/coding-agent/best-practices-for-using-copilot-to-work-on-tasks#adding-custom-instructions-to-your-repository
[personal-instructions]: https://docs.github.com/copilot/customizing-copilot/adding-personal-custom-instructions-for-github-copilot
[copilot-instructions-five-tips]: https://github.blog/ai-and-ml/github-copilot/5-tips-for-writing-better-custom-instructions-for-copilot/

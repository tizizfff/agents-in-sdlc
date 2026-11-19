---
title: "练习 1：自定义指令（云智能体）"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← 上一课：准备工作][previous-lesson] · [下一课：Copilot云智能体 →][next-lesson]

上下文是生成式 AI工作的关键。如果任务需要按特定方式完成，或 Copilot应了解背景信息，就应确保上下文可访问。[指令文件][instruction-files]用于提供此类指导，使 Copilot不仅理解要做什么，也理解如何执行。

在本练习中，你将：

- 探索仓库自定义指令和路径作用域指令如何向 Copilot传递项目上下文、编码指南和文档规范。
- 在 `.github/copilot-instructions.md`中添加新的仓库级标准。

> [!NOTE]
> 与 VS Code和 CLI环境不同，此处不会运行前后对比提示；Copilot云智能体异步处理 GitHub issue，因此很难实时并排演示影响。稍后审查云智能体创建的拉取请求时，你可以看到指令文件的作用。

## 指令文件

### 场景

Tailspin Toys对开发实践有一套指南和要求，包括：

- 数据层始终需要单元测试。
- UI应采用深色模式并具有现代感。
- 应使用 TSDoc文档注释将文档添加到代码中。
- 应在每个文件顶部添加说明用途的注释块。

通过指令文件，可确保 Copilot掌握正确上下文并遵循这些实践。

### 自定义指令

自定义指令让 Copilot更好地理解编码风格和需求。指令可为整个仓库提供全局上下文，也可针对特定文件类型提供任务上下文。

指令文件分为两类：

- `.github/copilot-instructions.md`：发送给仓库中每个请求的单个指令文件，应包含项目级信息、技术栈概览、编码规范和全局指导。
- `.github/instructions/*.instructions.md`：为特定任务或文件类型（如 TypeScript、Astro、单元测试）提供指令。

> [!NOTE]
> Copilot Chat、Copilot CLI和 Copilot云智能体都会在生成代码时使用仓库级指令及带 `applyTo`frontmatter的 `*.instructions.md`文件。

## 探索项目中的指令文件

花一点时间阅读仓库提供的指令：

1. 打开 `.github/copilot-instructions.md`。
2. 注意项目简介及 **Agent notes**、**Code standards**、**Scripts**和 **Repository Structure**等章节。
3. 打开 `.github/instructions`文件夹，浏览 Astro、Drizzle数据层、测试等指令。
4. 打开 `.github/instructions/unit-tests.instructions.md`，注意顶部的 `applyTo`字段，它确定哪些 TypeScript测试文件匹配。
5. 阅读该项目创建单元测试的具体指令。
6. 打开 `.github/instructions/drizzle.instructions.md`并滚动到底部，查看指向其他指令文件和现有项目文件的链接。

> [!NOTE]
> `copilot-instructions.md`中的 **Code formatting requirements**记录了编码规范，但尚未要求在代码中编写文档。下一步将添加 TSDoc文档注释和文件注释头规则。

## 添加仓库级新标准

下一步是实际编辑：添加文档应以 TSDoc文档注释和文件级注释头形式存在于代码中的项目级规则。

在编辑前先创建分支。云智能体会根据 issue目标分支读取指令，因此应在提交前保持分支整洁：

1. 在 Codespace终端中创建并切换分支：

   ```bash
   git checkout -b custom-instructions-cloud
   ```

2. 重新打开 `.github/copilot-instructions.md`。
3. 找到 **Code formatting requirements**章节，通常位于约第 27 行。
4. 在现有标准下方添加：

   ```markdown
   - Every exported function should have a TSDoc comment describing its purpose, parameters, and return value.
   - Before imports or any code, add a comment block to the file that explains its purpose.
   ```

5. 保存文件。

> [!TIP]
> 仓库级指令适合项目级规范；特定语言、文件类型或任务应使用 `*.instructions.md`。

## 提交、推送并合并指令更新

云智能体读取 issue目标分支上的指令。分配 issue时会从 `main`创建分支，因此指令变更必须进入 `main`。

1. 暂存并提交：

   ```bash
   git add .github/copilot-instructions.md
   git commit -m "Add doc comment and file-header standards to copilot instructions"
   ```

2. 推送分支：

   ```bash
   git push -u origin custom-instructions-cloud
   ```

3. 在 github.com上创建从 `custom-instructions-cloud`到 `main`的拉取请求并合并。下一练习分配 issue时，云智能体会读取这些指令。

> [!TIP]
> 如果不介意直接在 `main`上工作，也可跳过分支并直接提交到 `main`。分支步骤只是演示真实项目中的处理方式。

## 摘要和后续步骤

你已探索指令文件如何向 Copilot传递上下文，并向 `.github/copilot-instructions.md`添加了新仓库级标准。后续云智能体创建的拉取请求中会看到该标准的效果。

接下来，[将第一个 issue分配给 Copilot云智能体][next-lesson]。

## 资源

- [GitHub Copilot自定义指令文件][instruction-files]
- [创建自定义指令最佳实践][instructions-best-practices]
- [编写更好自定义指令的 5个技巧][copilot-instructions-five-tips]
- [Awesome Copilot——指令文件集合][awesome-copilot]

[previous-lesson]: ../0-prerequisites/
[next-lesson]: ../2-cloud-agent/
[instruction-files]: https://docs.github.com/copilot/reference/custom-instructions-support
[instructions-best-practices]: https://docs.github.com/enterprise-cloud@latest/copilot/using-github-copilot/coding-agent/best-practices-for-using-copilot-to-work-on-tasks#adding-custom-instructions-to-your-repository
[copilot-instructions-five-tips]: https://github.blog/ai-and-ml/github-copilot/5-tips-for-writing-better-custom-instructions-for-copilot/
[awesome-copilot]: https://github.com/github/awesome-copilot

---
title: "Lição 6 - Validar funcionalidades com Playwright MCP"
description: "Inspecione ou configure o Playwright MCP no Copilot CLI e use-o para explorar o recurso de filtragem em um navegador."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

Escrever código é apenas uma parte do trabalho. Também precisamos lidar com dados, serviços externos e outras automações disponíveis ao Copilot. É nesse ponto que entram os servidores MCP. Eles permitem que o Copilot vá além dos recursos integrados ao CLI e use ferramentas e serviços adicionais.

Nesta lição, você vai:

- entender o que é o Model Context Protocol (MCP) e como o Copilot CLI o utiliza;
- adicionar o servidor Playwright MCP, caso ainda não esteja disponível;
- pedir ao agente que controle um navegador e explore o recurso de filtragem.

## Cenário

Testes unitários e de ponta a ponta são importantes, mas validar uma interface exige interagir com ela. Você deseja permitir que o Copilot use o site como uma pessoa usuária, o que automatiza melhor as verificações e aumenta a confiança nos resultados.

## O que é Model Context Protocol (MCP)?

O [Model Context Protocol (MCP)][mcp-blog-post] permite que agentes de IA se comuniquem com ferramentas e serviços externos. Com o MCP, os agentes podem acessar informações atualizadas e executar ações em seu nome.

- **[Servidor GitHub MCP][github-mcp]**: fornece acesso às APIs para gerenciar repositórios, issues e solicitações de pull do GitHub.
- **[Servidor Playwright MCP][playwright-mcp-server]**: fornece recursos de automação de navegador com Playwright.

> [!CAUTION]
> Trate servidores MCP como qualquer outra dependência do projeto. Antes de usar um, revise o código-fonte, confirme o responsável pela publicação e considere as implicações de segurança.

## Adicionar o servidor Playwright MCP

Se o servidor Playwright MCP ainda não estiver disponível, adicione-o.

> [!NOTE]
> Se o Playwright MCP já estiver configurado no Copilot CLI, pule estas etapas.

1. Volte ao Codespace.
2. Abra o diálogo para adicionar um servidor MCP com:

   ```plaintext
   /mcp add
   ```

3. Como nome, informe `playwright`.
4. Confirme o tipo **STDIO** e pressione <kbd>Tab</kbd>.
5. Cole no campo **Command**:

   ```plaintext
   npx -y @playwright/mcp@latest --headless --no-sandbox
   ```

6. Pressione <kbd>Control</kbd>+<kbd>S</kbd> (Mac) ou <kbd>Ctrl</kbd>+<kbd>S</kbd> (Windows/Linux) para salvar.

## Pedir ao Copilot que explore o recurso com Playwright

Use este prompt para validar a funcionalidade:

```plaintext
Start the app and use Playwright MCP to check filtering against the issue and our plan. Tell me what works and what doesn't, without making changes. Stop the server you started when you're done.
```

O Copilot normalmente detectará o servidor MCP por conta própria. Observe as etapas realizadas no navegador e revise o relatório.

## Resumo e próximos passos

Você usou o Playwright MCP para explorar o recurso em um navegador real por meio do Copilot CLI. Em seguida, crie um agente personalizado de QA que reúna o skill e as ferramentas de navegador.

[previous-lesson]: ../5-agent-skills/
[next-lesson]: ../7-qa-agent/
[mcp-blog-post]: https://github.blog/ai-and-ml/llms/what-the-heck-is-mcp-and-why-is-everyone-talking-about-it/
[playwright-mcp-server]: https://github.com/microsoft/playwright-mcp
[github-mcp]: https://github.com/github/github-mcp-server
[add-mcp]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/add-mcp-servers

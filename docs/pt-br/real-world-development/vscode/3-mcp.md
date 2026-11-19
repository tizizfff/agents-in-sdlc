---
title: "Exercício 3 - Testar o recurso com o servidor Playwright MCP"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← Exercício anterior: modo agente][previous-lesson] · [Próximo exercício: agentes personalizados →][next-lesson]

Após criar a filtragem no modo agente, confirme o comportamento no navegador. Você conectará o **servidor Playwright MCP** e pedirá ao Copilot que execute um navegador real.

Nesta lição, você vai:

- entender o Model Context Protocol (MCP);
- adicionar o servidor Playwright MCP ao workspace;
- testar a filtragem no navegador;
- publicar a branch e abrir uma solicitação de pull.

## O que é MCP?

O [Model Context Protocol (MCP)](https://github.blog/ai-and-ml/llms/what-the-heck-is-mcp-and-why-is-everyone-talking-about-it/) permite que agentes de IA se comuniquem com ferramentas e serviços externos.

- **GitHub MCP Server**: gerencia repositórios, issues e solicitações de pull.
- **Playwright MCP Server**: controla um navegador para navegar em páginas e interagir com elementos.

> [!CAUTION]
> Trate servidores MCP como dependências do projeto. Revise o código-fonte e confirme o responsável pela publicação antes de usá-los.

## Revisar a configuração

O arquivo `.vscode/mcp.json` configura os servidores MCP. Ele já deve conter o servidor `github`:

```json
{
  "servers": {
    "github": {
      "type": "http",
      "url": "https://api.githubcopilot.com/mcp/"
    }
  }
}
```

## Adicionar o Playwright MCP

Adicione `playwright` ao mesmo arquivo:

```json
{
  "servers": {
    "github": {
      "type": "http",
      "url": "https://api.githubcopilot.com/mcp/"
    },
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest", "--headless"]
    }
  }
}
```

Salve o arquivo e selecione **Start** acima da entrada `playwright`, se disponível. Confirme que confia no servidor antes de iniciá-lo.

## Testar a filtragem

Com o servidor conectado e o aplicativo em execução em `http://localhost:4321`, envie:

```text
Using the Playwright MCP server, open a browser to the running app at http://localhost:4321 and verify the new game filtering feature:

1. Go to the games page and note how many games are listed.
2. Apply a category filter and confirm the list updates to only show games in that category.
3. Clear it, then apply a publisher filter and confirm the list updates to that publisher.
4. Combine a category and a publisher filter and confirm the results respect both.

Report what you observe at each step, and call out anything that does not behave as expected.
```

Revise o relatório contra os critérios da issue. Corrija eventuais problemas antes de abrir a PR.

## Publicar a branch e criar a PR

1. No painel **Source Control**, revise as alterações.
2. Selecione o ícone **+** para preparar os arquivos.
3. Crie uma mensagem de commit.
4. Selecione **Publish**.
5. Em um novo chat, selecione **Agent** e peça:

   ```plaintext
   Find the issue in the repo related to filtering by category and publisher. Create a new pull request for the current branch, and associate it with the correct issue.
   ```

6. Revise a solicitação de pull gerada, mas não a mescle ainda.

## Resumo e próximos passos

Você conectou o Playwright MCP, testou a filtragem em um navegador real e publicou uma PR. Em seguida, crie um agente personalizado.

[previous-lesson]: ../2-agent-mode/
[next-lesson]: ../4-custom-agents/

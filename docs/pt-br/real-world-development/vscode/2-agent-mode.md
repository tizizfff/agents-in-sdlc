---
title: "Exercício 2 - Adicionar novas funcionalidades com o modo agente do Copilot"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

As alterações em uma aplicação geralmente exigem modificações em vários arquivos, testes e depuração. O modo agente do Copilot pode explorar o projeto, identificar arquivos relevantes, coordenar alterações, executar testes e corrigir problemas.

> [!NOTE]
> O modo agente funciona no IDE para ciclos rápidos de interação. O agente de nuvem funciona de forma assíncrona por meio de issues e solicitações de pull.

Neste exercício, você aprenderá a:

- explorar o projeto e identificar arquivos relevantes;
- implementar funcionalidades na interface e na camada de dados;
- revisar alterações e testes antes da mesclagem.

## Cenário

A Tailspin Toys precisa permitir filtragem por categoria e editora. O helper de editoras já existe. Agora você completará a camada de dados, a interface e os testes com o modo agente.

## Executar o site

1. Volte ao codespace e confirme que está em `main`.
2. Crie uma branch:

   ```bash
   git checkout main
   git pull
   git checkout -b filtering-vscode
   ```

3. Inicie o site:

   ```bash
   npm run dev
   ```

4. Abra o endereço do servidor informado pelo Astro.

## Explorar o backlog

1. Selecione **Agent** no seletor do Copilot Chat.
2. Selecione um modelo disponível.
3. Peça ao Copilot que liste e priorize as issues do repositório:

   ```plaintext
   Please show me the backlog of items from my GitHub repository. Help me prioritize them based on those which will be most useful to the user.
   ```

4. Revise a lista gerada.

## Revisar as instruções

Abra `.github/instructions/ui.instructions.md` e revise a arquitetura, os princípios de componentes, a testabilidade, a acessibilidade e os links para instruções específicas.

## Implementar a filtragem

1. Em um novo chat, selecione o arquivo de instruções **ui** no contexto.
2. Mantenha **Agent** selecionado.
3. Peça a implementação:

   ```plaintext
   Please update the site to include filtering by publisher and category based on the requirements from the related GitHub issue in the backlog. A publishers helper already exists from the previous exercise, so preserve and refine that work as needed while completing the remaining data-layer, UI, and tests. Ensure all tests are passing before completion. The server is already running, so you do not need to start it up.
   ```

4. Acompanhe a exploração dos arquivos, as alterações e a execução dos testes.
5. Selecione **Continue** quando solicitado.
6. Revise o código gerado e teste a filtragem no navegador.
7. Selecione **Keep** para aceitar as alterações.

> [!CAUTION]
> Sempre revise o código gerado por Copilot ou outra ferramenta de IA.

## Resumo e próximos passos

Você usou o modo agente para implementar uma funcionalidade em várias partes da aplicação. Agora teste o recurso com o Playwright MCP e abra uma solicitação de pull.

[previous-lesson]: ../1-custom-instructions/
[next-lesson]: ../3-mcp/

---
title: "Exercício 4 - Agentes personalizados"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

## O que são agentes personalizados?

[Agentes personalizados][custom-agents-concept] são assistentes de IA especializados em tarefas ou domínios específicos. Eles são definidos por arquivos Markdown em `.github/agents` e podem reunir instruções, padrões de código e conhecimento do domínio.

Cada arquivo tem frontmatter YAML com `name` e `description`, seguido por um prompt que define o comportamento do agente.

## Cenário

A Tailspin Toys precisa implementar um modo de alto contraste. O agente personalizado de acessibilidade ajudará o Copilot a seguir as diretrizes adequadas.

## Revisar o agente de acessibilidade

1. Crie uma branch:

   ```bash
   git checkout main
   git pull
   git checkout -b accessibility-vscode
   ```

2. Abra `.github/agents/accessibility.md`.
3. Revise os campos `name` e `description`.
4. Revise responsabilidades, boas práticas, exemplos e armadilhas comuns.

> [!CAUTION]
> O frontmatter com `name` e `description` é obrigatório.

## Usar o agente no Copilot Chat

1. Abra o Copilot Chat e selecione **New Chat**.
2. Na lista de agentes, selecione **Accessibility agent**.
3. Envie:

   ```plaintext
   Add a high-contrast mode to the site. There should be a toggle for high contrast which the user can set, and the setting should persist across page reloads using local storage on the browser.
   ```

4. Revise as alterações propostas, os arquivos afetados e os diffs exibidos pelo agente.

> [!NOTE]
> Revise e oriente o trabalho em andamento no próximo exercício.

[previous-lesson]: ../3-mcp/
[next-lesson]: ../5-managing-agents/

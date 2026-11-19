---
title: "Exercício 4 - Monitorar e gerenciar agentes"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

Embora o agente de nuvem funcione de forma assíncrona e autônoma, monitorar suas tarefas é importante. A [página de agentes][agents-page] do GitHub mostra tarefas com solicitações de pull abertas e permite orientar uma sessão em andamento.

Nesta lição, você vai:

- monitorar tarefas do agente de nuvem;
- orientar uma sessão ativa para solicitar funcionalidade adicional.

## Revisar as tarefas

1. Abra a [página de agentes do Copilot](https://github.com/copilot/agents).
2. Observe os agentes atribuídos, incluindo documentação, jogos relacionados e modo de alto contraste.
3. Selecione uma tarefa em execução e revise as etapas realizadas.
4. Use o painel de PR à direita para acompanhar arquivos alterados e progresso.

> [!NOTE]
> Os passos exatos variam conforme o estado da tarefa e a abordagem usada pelo Copilot.

## Orientar o agente

Solicite que o agente também implemente um modo claro enquanto trabalha no modo de alto contraste.

1. Selecione a sessão correspondente ao modo de alto contraste.
2. Aguarde até que ela indique que a configuração terminou e o trabalho começou.
3. No diálogo **Steer active session while Copilot is working**, informe:

   ```plaintext
   While we are working on a high contrast mode, let's also add a light mode. There should be a switch for this mode as well where users can select their desired display mode.
   ```

4. Pressione <kbd>Enter</kbd>.
5. Observe o Copilot incorporar o novo requisito ao fluxo.

## Resumo e próximos passos

Você monitorou tarefas e redirecionou uma sessão ativa. Em seguida, revise e itere sobre as solicitações de pull criadas pelo Copilot.

---

| [← Exercício anterior: Agentes personalizados][previous-lesson] | [Próximo exercício: Iterar sobre o trabalho do Copilot →][next-lesson] |
|:--|--:|

[previous-lesson]: ../3-custom-agents/
[next-lesson]: ../5-iterating/
[agents-page]: https://github.blog/changelog/2025-07-03-agents-page-for-copilot-coding-agent-in-public-preview

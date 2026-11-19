---
title: "Lição 8 - Criar e mesclar a PR do recurso"
description: "Revise a filtragem, as instruções, a atualização do skill, o perfil de QA e os testes juntos, depois crie uma PR e use o Agent Merge."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

A implementação da filtragem, as instruções, o skill, o perfil de QA e os testes estão em uma branch. Agora é hora de revisá-los juntos e abrir uma solicitação de pull. Você mesclou a PR das classificações por conta própria; desta vez, o **Agent Merge** gerenciará o processo.

> [!NOTE]
> O recurso, as instruções, o skill e o agente de QA normalmente ficariam em PRs separadas. Para simplificar o workshop, reunimos todo o fluxo de filtragem e qualidade em uma conversa e branch.

Nesta lição, você vai:

- aprender o que é Agent Merge e como ele automatiza o ciclo de mesclagem;
- inspecionar a alteração completa e as evidências de verificação;
- criar a PR da filtragem;
- habilitar o Agent Merge somente após a revisão e confirmar a mesclagem.

## Usar o Agent Merge

1. Volte ao Codespace.
2. Digite `/agent` para abrir o diálogo de agentes.
3. Selecione **Default** e pressione <kbd>Enter</kbd>.
4. Crie uma PR com `/pr create`.
5. Ative o Agent Merge com `/pr agentmerge`.
6. O Copilot acompanhará a integração contínua da PR. Quando tudo for concluído, realizará a mesclagem.
7. Confirme uma mensagem semelhante a “PR #14 was squash-merged successfully.”

> [!IMPORTANT]
> O Agent Merge não contorna aprovações necessárias, proteção de branch, filas de mesclagem, configurações do repositório ou permissões ausentes.

## Resumo e próximos passos

Você automatizou partes do processo de desenvolvimento e abriu a PR do recurso. Em seguida, explore mais comandos de barra do Copilot CLI.

[previous-lesson]: ../7-qa-agent/
[next-lesson]: ../9-cli-power-tools/
[manage-prs]: https://docs.github.com/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference

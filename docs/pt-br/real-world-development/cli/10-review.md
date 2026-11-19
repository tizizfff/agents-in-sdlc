---
title: "Lição 10 - Encerramento e próximos passos"
description: "Reúna o fluxo do Copilot CLI, duas solicitações de pull, personalizações reutilizáveis e recursos adicionais."
authors:
  - geektrainer
lastUpdated: 2026-09-29
---

Você usou o GitHub Copilot CLI em um fluxo contínuo da Tailspin Toys:

- preparou um Codespace, instalou o Copilot CLI, explorou o projeto e encontrou a issue de filtragem;
- adicionou classificações por estrelas, revisou o resultado em um navegador encaminhado e mesclou sua primeira PR;
- iniciou pela issue de filtragem, definiu a abordagem no modo Plan, criou o recurso no modo Autopilot e revisou-o no modo Interactive;
- orientou o agente com instruções personalizadas, adaptou o skill `quality-checks` e o executou;
- adicionou o Playwright MCP e o usou em um navegador real;
- criou um agente personalizado de QA para avaliar requisitos e evidências;
- revisou a alteração completa e autorizou o Agent Merge;
- explorou comandos de barra para contexto, modelos, compartilhamento e delegação na nuvem.

## Práticas recomendadas

O contexto e as ferramentas fornecidos ao Copilot determinam seu trabalho. Reutilize instruções, skills, agentes personalizados e servidores MCP conforme as necessidades da equipe mudarem. Revise as alterações reais e os resultados das ferramentas, não apenas o resumo do agente.

Use o **modo** e o **modelo** adequados à tarefa. O modo **Plan** ajuda a definir uma abordagem antes da implementação, o modo **Interactive** mantém você no ciclo de alterações focadas e o modo **Autopilot** atende a tarefas bem delimitadas. Use um modelo mais rápido para alterações comuns e um modelo mais capaz para trabalho complexo.

## Próximos passos

A melhor maneira de aprimorar qualquer ferramenta é continuar usando-a. Use-a em código de produção, projetos pessoais ou aplicações antigas que você sempre quis criar. Compartilhe aprendizados com sua equipe e explore a documentação.

Para ampliar a Tailspin Toys pelo terminal, continue na série opcional [Foundry Backer Concierge][foundry]. Para comparar ambientes, explore o [workshop do VS Code][vscode], o [workshop do aplicativo GitHub Copilot][app] ou o [workshop do agente de nuvem][cloud].

[previous-lesson]: ../9-cli-power-tools/
[foundry]: ../8-foundry-agent/
[vscode]: ../../vscode/
[app]: ../../app/
[cloud]: ../../cloud/
[about-cli]: https://docs.github.com/copilot/concepts/agents/about-copilot-cli
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[customize-cli]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot
[manage-prs]: https://docs.github.com/copilot/how-tos/copilot-cli/use-copilot-cli/manage-pull-requests

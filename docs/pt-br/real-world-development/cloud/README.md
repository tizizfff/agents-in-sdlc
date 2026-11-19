---
slug: pt-br/real-world-development/cloud
title: "Agente de nuvem do GitHub Copilot"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

O **[agente de nuvem do GitHub Copilot](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent)** permite que o GitHub Copilot trabalhe de forma assíncrona na nuvem. Você atribui trabalhos no GitHub e o agente de nuvem os retoma em segundo plano — explorando o repositório, fazendo alterações e abrindo uma solicitação de pull — enquanto você fica livre para realizar outras atividades.

Nestas atividades, você adicionará instruções personalizadas que o agente de nuvem seguirá, atribuirá uma issue do GitHub e permitirá que ele implemente o trabalho. Você revisará e usará agentes personalizados para orientar sua abordagem, acompanhará e direcionará sessões no painel de agentes e finalizará revisando as solicitações de pull e iterando sobre os resultados.

## Exercícios

| Exercício | Tema | Descrição |
|----------|-------|-------------|
| [0. Pré-requisitos][ex0] | Configuração | Crie seu repositório e Codespace |
| [1. Instruções personalizadas][ex1] | Contexto | Adicione instruções personalizadas que o agente de nuvem seguirá |
| [2. Agente de nuvem][ex2] | Agente assíncrono | Atribua issues ao agente de nuvem do Copilot |
| [3. Agentes personalizados][ex3] | Agentes especializados | Revise e use agentes personalizados |
| [4. Gerenciamento de agentes][ex4] | Monitoramento | Acompanhe e oriente sessões de agentes |
| [5. Iteração][ex5] | Revisão | Revise PRs, itere sobre o trabalho do Copilot e escolha os próximos passos |

## Pré-requisitos

Antes de participar deste workshop, confirme que você tem:

- [ ] Uma conta do GitHub com um plano ativo **Copilot Student, Pro, Pro+, Business ou Enterprise**
- [ ] O agente de nuvem do Copilot habilitado para sua conta ou organização

> [!TIP]
> Não tem um plano pago? Estudantes verificados podem usar o GitHub Copilot gratuitamente por meio do [GitHub Education][callout-student-plan-education]. O plano **Copilot Student** inclui o agente, MCP, revisão de código e recursos do Copilot CLI usados neste workshop — portanto, você poderá concluir todos os exercícios com ele.

[callout-student-plan-education]: https://github.com/education/students

> [!NOTE]
> O agente de nuvem está disponível nos planos **Copilot Student, Pro, Pro+, Business e Enterprise** — todos, exceto o Copilot Free. No Copilot Business ou Enterprise, um administrador deve habilitá-lo para sua organização.

> [!NOTE]
> MCP não é abordado neste conjunto de exercícios. Para explorar servidores MCP com o Copilot, consulte o [conjunto de exercícios do CLI](../cli/) ou o [conjunto de exercícios do VS Code](../vscode/).

## Começar

**[Começar pelo Exercício 0: Pré-requisitos →][ex0]**

[ex0]: 0-prerequisites/
[ex1]: 1-custom-instructions/
[ex2]: 2-cloud-agent/
[ex3]: 3-custom-agents/
[ex4]: 4-managing-agents/
[ex5]: 5-iterating/

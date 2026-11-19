---
title: "Lição 7 - Criar e usar um agente de QA"
description: "Crie um agente personalizado de QA que combine requisitos da issue, o skill quality-checks e o Playwright MCP."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

Você usou o skill `quality-checks` para executar verificações automatizadas e o Playwright MCP para observar a experiência de filtragem no navegador. Agora você reunirá esses recursos em um agente personalizado com um processo de QA claramente definido.

Nesta lição, você vai:

- explorar como um agente personalizado trabalha com instruções, skills e ferramentas MCP;
- criar e revisar um perfil reutilizável de garantia de qualidade;
- selecionar o agente de QA e comparar suas descobertas com a issue de filtragem.

## Cenário

A Tailspin Toys deseja uma revisão consistente dos requisitos, da qualidade do código, das verificações automatizadas, da cobertura de testes e do comportamento no navegador antes de abrir uma PR. Um agente personalizado pode coordenar esse processo e produzir um relatório reutilizável.

## Criar o perfil de QA

Peça ao agente padrão que crie o novo agente personalizado:

```plaintext
Create a custom agent named QA in .github/agents/qa.agent.md. It should check features against their issues and agreed requirements, follow the repository instructions, run the quality-checks skill, use Playwright MCP to verify behavior, and add tests when coverage is missing.

Have it report each requirement as pass, fail, or blocked with supporting evidence. It must ask before changing implementation code, and it must not commit changes or open pull requests.

Just create the profile for now so I can review it.
```

## Inspecionar o perfil

Revise o perfil `.github/agents/qa.agent.md` para confirmar que o fluxo e os limites desejados foram registrados.

1. Digite `/diff` e abra o arquivo.
2. Confirme o campo `description` no frontmatter.
3. Leia as instruções e confirme que o QA começa pelos requisitos, segue as instruções do repositório, executa `quality-checks` e usa Playwright MCP.
4. Confirme que ele informa evidências, pede autorização antes de alterar código de implementação e não confirma alterações nem abre PRs.

## Executar o QA contra a issue

Ative o agente com:

```plaintext
/agent QA
```

Peça ao agente de QA que revise o recurso:

```plaintext
Review the filtering feature against the issue and the decisions in our plan. Is it ready for a PR?
```

Leia o relatório e verifique as evidências fornecidas.

## Resumo e próximos passos

Você adicionou uma função especializada reutilizável ao fluxo e revisou seu trabalho. Em seguida, reúna a implementação, os testes e o resultado do QA em uma PR de recurso.

[previous-lesson]: ../6-mcp-playwright/
[next-lesson]: ../8-create-pull-request/
[create-agents]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/create-custom-agents-for-cli
[agent-config]: https://docs.github.com/copilot/reference/custom-agents-configuration

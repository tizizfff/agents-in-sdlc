---
title: "Exercício 3 - Agentes personalizados"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

## O que são agentes personalizados?

[Agentes personalizados][custom-agents-concept] permitem criar assistentes de IA especializados em tarefas ou domínios específicos. Ao defini-los por meio de arquivos Markdown na pasta `.github/agents`, você fornece ao Copilot instruções focadas, boas práticas e padrões.

Cada agente tem frontmatter YAML com `name` e `description`, seguido por um prompt que define seu comportamento.

### Agentes personalizados e skills

Um **agente personalizado** é o trabalhador, enquanto **skills** são ferramentas. O agente pode usar skills e até outros agentes para concluir o trabalho.

> [!NOTE]
> Não existe uma única forma correta de criar um agente personalizado. Teste e ajuste o conteúdo conforme seu ambiente.

## Cenário

A Tailspin Toys quer oferecer modo de alto contraste para melhorar a acessibilidade. Um agente personalizado pode implementar esse recurso seguindo as diretrizes de acessibilidade.

## Revisar o agente de acessibilidade

1. Abra `.github/agents/accessibility.md`.
2. Observe os campos `name` e `description` no frontmatter.
3. Revise as responsabilidades, práticas de acessibilidade, exemplos e armadilhas comuns.

> [!CAUTION]
> Os campos `name` e `description` são obrigatórios no frontmatter.

## Criar e atribuir uma issue

1. Abra o repositório no GitHub.
2. Selecione **Issues** e depois **New issue**.
3. Use o título `Add high contrast mode to website`.
4. Descreva o recurso:

   ```plaintext
   We need a high contrast mode for the site. There should be a toggle for high contrast which the user can set. It should store the setting in local storage on the browser.
   ```

5. Crie a issue.
6. Selecione **Assign to Copilot** e escolha **Accessibility agent**.
7. Confirme a atribuição e acompanhe a execução em segundo plano.

## Resumo e próximos passos

Os agentes personalizados codificam a experiência da equipe em assistentes reutilizáveis. Agora, monitore e oriente a sessão do agente.

---

| [← Exercício anterior: agente de nuvem do GitHub Copilot][previous-lesson] | [Próximo exercício: Monitorar e gerenciar agentes →][next-lesson] |
|:--|--:|

[previous-lesson]: ../2-cloud-agent/
[next-lesson]: ../4-managing-agents/
[custom-agents-concept]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents

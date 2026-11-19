---
title: "Exercício 2 - Agente de nuvem do GitHub Copilot"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

| [← Exercício anterior: Instruções personalizadas][previous-lesson] |
|:--|

O agente de nuvem do GitHub Copilot pode atualizar código e adicionar funcionalidades de forma autônoma. Ao concluir o trabalho, cria uma solicitação de pull em rascunho para revisão humana.

Você explorará:

- personalizar o ambiente de geração de código;
- garantir operações seguras;
- a importância de issues bem delimitadas;
- atribuir issues ao Copilot.

## Cenários

A Tailspin Toys quer reduzir dívida técnica e melhorar a descoberta de jogos. Uma issue pode solicitar comentários TSDoc para todas as funções exportadas. Outra pode solicitar uma seção de jogos relacionados na página de detalhes.

Essas tarefas são boas candidatas ao agente de nuvem: ele trabalha de forma assíncrona, enquanto o desenvolvedor pode se concentrar em outro trabalho e depois revisar o resultado.

## Conhecer o agente de nuvem

O [agente de nuvem do GitHub Copilot][copilot-agents] executa tarefas em segundo plano. Ao atribuir uma issue, ele cria uma PR em rascunho, configura o ambiente e começa a trabalhar. Você pode acompanhar a sessão durante ou após a execução e revisar a solução antes da mesclagem.

## Usar instruções personalizadas

Revise `.github/copilot-instructions.md` e `.github/instructions/unit-tests.instructions.md` antes de atribuir trabalho. Observe como o padrão de documentação e as convenções de TypeScript podem aparecer na PR gerada.

## Configurar o ambiente

O agente usa GitHub Actions. A etapa de configuração pode ser definida em `.github/workflows/copilot-setup-steps.yml` para instalar ferramentas, dependências e navegadores antes do trabalho.

> [!NOTE]
> O exemplo do laboratório já configura Node.js, dependências npm, navegadores Playwright e o banco SQLite preparado.

## Adicionar documentação

1. No GitHub, abra a guia **Issues** do repositório.
2. Selecione **New issue** e depois **Blank issue**.
3. Use o título `Code lacks documentation`.
4. Use uma descrição que exija comentários TSDoc nos métodos e funções onde eles esclarecem o comportamento.
5. Selecione **Create**.
6. À direita, selecione **Assign to Copilot** e confirme a atribuição.

Em seguida, acompanhe a PR criada pelo agente e revise os comentários TSDoc e os cabeçalhos de arquivo.

## Adicionar jogos relacionados

Crie outra issue com o título `Show related games on the game details page` e exija:

- um helper em `src/lib/` que retorne jogos da mesma categoria, excluindo o jogo atual;
- uma seção “Related games” na página de detalhes;
- tratamento para jogos sem relacionados;
- testes unitários;
- aprovação de todos os testes antes da criação da PR.

Após atribuir a issue ao Copilot, você pode acompanhar o progresso na sessão do agente e revisar a PR ao concluir.

## Resumo e próximos passos

Você atribuiu trabalho ao agente de nuvem e viu como ele configura o ambiente e executa tarefas de forma assíncrona. Em seguida, crie e use agentes personalizados.

| [Próximo exercício: agentes personalizados →][next-lesson] |
|--:|

[previous-lesson]: ../1-custom-instructions/
[next-lesson]: ../3-custom-agents/
[copilot-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent

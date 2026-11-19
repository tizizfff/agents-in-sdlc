---
title: "Lição 9 - Comandos de barra no GitHub Copilot CLI"
description: "Explore comandos de barra para gerenciar contexto, selecionar modelos, compartilhar sessões e delegar opcionalmente a trabalho na nuvem."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

Como toda boa ferramenta de CLI, o GitHub Copilot CLI inclui muitos comandos de barra. Eles expõem funcionalidades avançadas, informações internas e opções de configuração.

Nesta lição, você vai:

- usar `/context` e `/compact` para entender como o Copilot gerencia o contexto;
- usar `/model` para explorar os modelos disponíveis;
- aprender como `/share` pode exportar ou compartilhar uma sessão;
- explorar comandos opcionais para trabalho paralelo, worktrees e delegação ao agente de nuvem.

## Explorar o contexto do Copilot CLI

1. Volte ao Codespace e inicie o Copilot CLI na raiz do repositório.
2. Informe `/context` e observe o modelo, o uso de tokens e a divisão entre instruções, ferramentas, mensagens e espaço livre.
3. Informe `/compact` para compactar a conversa.
4. Execute `/context` novamente e compare o resultado.

> [!NOTE]
> O Copilot compacta o contexto automaticamente quando a janela se aproxima do limite. Use `/compact` para escolher o momento. Use `/clear` ou `/new` ao mudar para uma tarefa não relacionada.

## Escolher o modelo

1. Informe `/model`.
2. Explore os modelos disponíveis e as informações de uso.
3. Mantenha o modelo atual, selecione outro ou pressione <kbd>Esc</kbd>.

## Compartilhar uma sessão

O `/share` pode exportar uma sessão para Markdown ou HTML, criar um link compartilhável ou publicar um gist do GitHub.

1. Digite `/help` e revise as opções de `/share`.
2. Escolha `/share file` para uma exportação Markdown local, se desejar compartilhar.
3. Revise o conteúdo exportado antes de enviá-lo. Ele pode conter prompts, respostas e detalhes do projeto.

Não publique conteúdo de repositório ou conversa que sua equipe não pretenda compartilhar.

## Opcional: escalar ou delegar

- `/fleet` divide subtarefas independentes entre subagentes e as executa em paralelo.
- `/worktree` cria um worktree Git isolado.
- `/delegate` envia uma tarefa ao agente de nuvem do Copilot.

Esses comandos são opcionais e podem criar worktrees ou trabalho remoto. Comece uma tarefa nova e bem definida e revise o resultado pelo fluxo normal. Para aprofundar o trabalho assíncrono, continue no [workshop do agente de nuvem][cloud-workshop].

## Resumo e próximos passos

Você configurou o Copilot CLI, compartilhou sessões e viu informações internas por meio de comandos de barra. Finalize o percurso revisando o que aprendeu e os próximos passos.

[previous-lesson]: ../8-create-pull-request/
[next-lesson]: ../10-review/
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
[context-management]: https://docs.github.com/copilot/concepts/agents/copilot-cli/context-management
[about-cloud-agent]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[cloud-workshop]: ../../cloud/

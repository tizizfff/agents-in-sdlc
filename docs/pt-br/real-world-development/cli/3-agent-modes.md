---
title: "Lição 3 - Modos de agente: Plan e Autopilot"
description: "Use o Plan para concordar com uma abordagem, o Autopilot para criar a filtragem a partir de uma issue e o modo Interactive para revisar o resultado."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

Começamos adicionando um recurso pequeno ao projeto. Alterações maiores exigem um processo mais robusto. Felizmente, o GitHub Copilot CLI foi criado para funcionar com o fluxo de uma organização. Esta é a primeira de várias lições nas quais você seguirá um processo típico de desenvolvimento orientado por agentes: começará por uma issue, definirá um plano, validará o código e o recurso e, por fim, mesclará o resultado.

> [!NOTE]
> Você usará a mesma conversa e branch durante o fluxo do recurso. Normalmente, seriam usados branches ou PRs diferentes para diferentes tipos de arquivo, mas aqui usamos um atalho para nos concentrarmos nos conceitos principais.

Nesta lição, você vai:

- iniciar uma nova conversa do Copilot a partir de uma issue do GitHub;
- definir requisitos no modo Plan;
- implementar o recurso no modo Autopilot;
- revisar o código;
- validar o recurso manualmente em um navegador encaminhado.

## Cenário

O catálogo da Tailspin Toys está crescendo, e os visitantes precisam filtrar jogos por categoria e editora. A issue do backlog descreve o recurso, mas detalhes como combinar categorias exigem concordância antes da programação. Use o modo Plan para resolver essas decisões e autorize uma implementação limitada com o Autopilot.

## Modos de conversa

O **modo de conversa** controla a autonomia do agente. Pressione <kbd>Shift</kbd>+<kbd>Tab</kbd> para alternar entre os modos:

- **Interactive**: você e o agente trabalham juntos. O agente sugere alterações e aguarda sua entrada.
- **Plan**: o agente cria um plano antes e não pode editar os arquivos do projeto.
- **Autopilot**: o agente trabalha de forma autônoma, escreve código, executa testes e itera até concluir a tarefa.

Comece no modo Plan, revise o plano e use o Autopilot para implementá-lo.

## Começar pela issue

1. Volte ao Codespace e confirme que o repositório e o terminal estão prontos.
2. Confirme que a PR da classificação por estrelas foi mesclada.
3. Atualize `main` e crie uma branch:

   ```bash
   git checkout main
   git pull --ff-only
   git checkout -b game-filters-cli
   ```

4. Inicie o Copilot CLI:

   ```bash
   copilot --yolo
   ```

5. Pressione <kbd>Tab</kbd> duas vezes para abrir a guia **Issues**.
6. Pressione <kbd>A</kbd> para mostrar todas as issues.
7. Use as setas para destacar **Allow users to filter games by category and publisher**.
8. Pressione <kbd>C</kbd> para adicionar a issue ao prompt e retornar à guia **Session**.

O prompt agora começa com `#7` ou outro número semelhante. O `#` traz uma issue ou solicitação de pull do GitHub para o contexto.

## Planejar o recurso de filtragem

1. Pressione <kbd>Shift</kbd>+<kbd>Tab</kbd> para entrar no modo Plan.
2. Após a referência à issue, informe:

   ```plaintext
   Create a plan for implementing this feature.
   ```

3. Responda às perguntas do Copilot sobre como a filtragem deve funcionar.
4. Após a conclusão do plano, pressione <kbd>Control</kbd>+<kbd>E</kbd> (Mac) ou <kbd>Ctrl</kbd>+<kbd>E</kbd> (Windows/Linux) para expandi-lo.
5. Revise o plano e peça alterações em qualquer parte que não corresponda às suas decisões.

## Aprovar o Autopilot

Com o plano revisado, selecione **Accept plan and build on autopilot (recommended)** ou a opção equivalente da versão instalada. Confirme que o indicador mostra **Autopilot** e acompanhe as iterações, a geração de código e a execução dos testes.

> [!NOTE]
> A aprovação pode iniciar a implementação imediatamente. Revise o plano primeiro. Se houver dependências ausentes ou conflito de porta, resolva o problema antes de considerar as verificações concluídas.

## Revisar e verificar a implementação

1. Pressione <kbd>Shift</kbd>+<kbd>Tab</kbd> para entrar no modo Interactive.
2. Digite `/diff` e inspecione a implementação e os testes.
3. Compare o resultado com a issue e as decisões do planejamento.
4. Pressione <kbd>Esc</kbd> para sair da visualização de diff.
5. Revise as verificações do projeto e peça ao Copilot que corrija falhas.

## Explorar o novo recurso

1. Peça ao Copilot que inicie o aplicativo:

   ```plaintext
   Start the app so I can try the filtering feature in my browser. Tell me the URL and leave the server running.
   ```

2. Quando a porta `4321` estiver disponível, selecione **Open in Browser**.
3. Teste os filtros por categoria, editora e suas combinações.
4. Confirme o comportamento de redefinição e de resultados vazios.
5. Peça ao Copilot que interrompa o servidor.

## Resumo e próximos passos

Você usou diferentes modos de conversa para criar e revisar um recurso. Em seguida, aprofunde como o código é gerado e como ele pode seguir práticas documentadas usando instruções personalizadas.

[previous-lesson]: ../2-add-star-rating/
[next-lesson]: ../4-custom-instructions/

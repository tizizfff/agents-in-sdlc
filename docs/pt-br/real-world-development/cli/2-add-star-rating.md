---
title: "Lição 2 - Adicionar classificações por estrelas: uma conquista rápida"
description: "Use o Copilot CLI para fazer uma pequena alteração nos cards dos jogos, revisá-la em um navegador encaminhado e mesclá-la como sua primeira solicitação de pull."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

Agora que você instalou o Copilot CLI e experimentou uma conversa, é hora de fazer sua primeira alteração no projeto. O trabalho será pequeno: os jogos já têm uma classificação por estrelas nos dados, mas os cards da página inicial ainda não a exibem. Você pedirá ao agente que a apresente, revisará a alteração e mesclará sua primeira solicitação de pull.

Nesta lição, você vai:

- iniciar uma conversa focada com o Copilot em uma branch de recurso.
- pedir ao agente que faça uma pequena alteração no projeto.
- revisar a alteração com `/diff`.
- executar o aplicativo para confirmar a alteração em um navegador encaminhado.
- abrir e mesclar sua primeira solicitação de pull.

## Cenário

Cada jogo da Tailspin Toys pode ter uma classificação por estrelas, que já aparece na página de detalhes. Os cards da página inicial, porém, exibem apenas título, categoria, editora e descrição. Como aquecimento, você fará o agente mostrar a classificação existente em cada card — uma alteração pequena e independente, perfeita para sua primeira sessão.

## Anatomia de uma conversa

Uma **conversa** é o local onde você trabalha com o Copilot CLI em uma tarefa. Diferentemente do aplicativo Copilot, uma conversa comum no CLI usa o repositório e a branch Git atualmente ativos no terminal, em vez de criar um worktree dedicado. Conversas salvas permitem retomar a discussão, enquanto os arquivos e a branch permanecem como estado comum do Git no disco.

Dentro de uma conversa, você verá os prompts e as respostas do agente, a atividade das ferramentas enquanto o agente explora e edita arquivos e as alterações que pode inspeccionar com `/diff`.

## Iniciar uma conversa e solicitar a alteração

Vamos iniciar uma nova conversa para implementar o recurso.

1. Volte ao seu Codespace.
2. Se o terminal não estiver aberto, pressione <kbd>Control</kbd>+<kbd>\`</kbd> (Mac) ou <kbd>Ctrl</kbd>+<kbd>\`</kbd> (Windows/Linux).
3. Inicie o Copilot com o comando:

   ```bash
   copilot --yolo
   ```

4. Inicie uma nova sessão com `/new` e pressione <kbd>Enter</kbd>.
5. Use este prompt para solicitar a alteração:

   ```plaintext
   Show each game's starRating out of 5 in the game cards on the list page. If the rating is null, show "No rating yet". Keep the card layout as it is, add tests, and run the relevant checks.
   ```

O Copilot explora o projeto, localiza os arquivos usados para exibir detalhes dos jogos e cria o código necessário.

## Revisar o diff

Todas as alterações geradas por IA devem ser revisadas antes da mesclagem, mesmo as pequenas.

1. Entre em `/diff` e inspecione todos os arquivos alterados.
2. Confirme que o card mostra a classificação numérica quando ela existe e `No rating yet` quando `starRating` é `null`.
3. Confirme que os testes cobrem os dois estados.
4. Revise os resultados das verificações executadas pelo Copilot e peça correções para qualquer falha.
5. Ao concluir a revisão, pressione <kbd>Esc</kbd> para sair da tela de diff.

> [!NOTE]
> Como todas as ferramentas de IA generativa, o Copilot é probabilístico, não determinístico. Seu código exato pode variar. Revise o comportamento em vez de esperar uma implementação específica.

## Verificar as alterações

Não devemos apenas ler o código e presumir que ele funciona. Peça ao Copilot que inicie o site para examinar a interface atualizada no navegador encaminhado pelo Codespaces.

1. Peça ao Copilot que inicie o aplicativo:

   ```plaintext
   Start the app so I can inspect the star-rating change in my browser. Tell me the URL and leave the server running.
   ```

2. Quando o Codespaces informar que a porta `4321` está disponível, selecione **Open in Browser**.
3. Confirme que os cards mostram as classificações de até cinco.
4. Volte ao Copilot e peça que ele interrompa o servidor iniciado:

   ```plaintext
   Stop the development server you started.
   ```

## Abrir e mesclar sua primeira solicitação de pull

O recurso foi criado. Agora você pode criar uma solicitação de pull para mesclar o código no projeto.

1. Peça ao agente padrão que confirme a alteração:

   ```plaintext
   Commit the reviewed star-rating changes with an appropriate commit message.
   ```

2. Entre em `/pr create`. O Copilot CLI envia o commit existente ao criar a PR e mostra a URL.
3. Abra a PR mantendo <kbd>Command</kbd> (Mac) ou <kbd>Ctrl</kbd> (Windows/Linux) e selecionando a URL exibida pelo Copilot CLI.
4. Revise os arquivos alterados e as verificações.
5. Quando estiver pronto, selecione **Merge pull request** e confirme a mesclagem.
6. Volte ao Codespace e saia do Copilot CLI com `/exit`.
7. Atualize sua `main` local:

   ```bash
   git checkout main
   git pull
   ```

## Resumo e próximos passos

Você lançou sua primeira alteração com o GitHub Copilot CLI. Em particular, você:

- iniciou uma conversa focada com o Copilot em uma branch de recurso;
- orientou o agente a fazer uma pequena alteração nos cards dos jogos;
- revisou a alteração com `/diff`;
- executou o aplicativo para confirmar a classificação em um navegador encaminhado;
- abriu e mesclou sua primeira solicitação de pull.

Em seguida, você começará pela issue de filtragem e usará os modos Plan e Autopilot para criar um recurso maior.

## Recursos

- [Sobre o GitHub Copilot CLI][about-copilot-cli]
- [Referência de comandos do Copilot CLI][cli-reference]

[previous-lesson]: ../1-install-copilot-cli/
[next-lesson]: ../3-agent-modes/
[about-copilot-cli]: https://docs.github.com/copilot/concepts/agents/about-copilot-cli
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference

---
title: "Exercício 5 - Monitorar e gerenciar agentes"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

| [← Exercício anterior: Agentes personalizados][previous-lesson] |
|:--|

O modo agente trabalha de forma autônoma no seu IDE: explora o código, executa comandos e sugere alterações. O Copilot Chat permite revisar diffs e orientar o trabalho.

Neste exercício, você vai:

- monitorar o agente de acessibilidade;
- revisar e aceitar alterações;
- pedir que ele adicione um modo claro.

## Monitorar o progresso

1. Volte ao Copilot Chat.
2. Acompanhe as chamadas de ferramentas e os arquivos alterados.
3. Para cada diff, selecione **Keep** para aceitar ou **Undo** para desfazer.
4. Se o agente solicitar executar um terminal, revise o comando e selecione **Allow** somente se estiver confortável.
5. Aguarde a conclusão do modo de alto contraste.

## Adicionar o modo claro

Envie ao agente a seguinte mensagem de acompanhamento:

```plaintext
Nice work! Now add a light-mode toggle alongside the high-contrast toggle. Light mode should follow the same pattern — persist via local storage and be accessible from the same area of the UI. The user should be able to enable high-contrast and light mode independently.
```

Revise cada novo diff e use **Keep** ou **Undo** conforme necessário.

> [!TIP]
> Para corrigir o rumo, use perguntas de acompanhamento em vez de iniciar uma conversa do zero.

## Revisar o conjunto de alterações

Antes de confirmar:

1. Abra a visão **Source Control**.
2. Revise todos os arquivos alterados.
3. Confirme atributos ARIA, navegação pelo teclado, HTML semântico e persistência em local storage.
4. Prepare e confirme as alterações no painel.

## Resumo e próximos passos

Você monitorou e orientou uma sessão ativa. Em seguida, publique o trabalho de acessibilidade como solicitação de pull e revise as alterações.

| [← Exercício anterior: Agentes personalizados][previous-lesson] | [Próximo exercício: Iterar sobre o trabalho do Copilot →][next-lesson] |
|:--|--:|

[previous-lesson]: ../4-custom-agents/
[next-lesson]: ../6-iterating/

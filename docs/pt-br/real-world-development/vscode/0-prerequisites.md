---
title: "Exercício 0: Pré-requisitos"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

Antes de iniciar os exercícios do VS Code, prepare o ambiente. Você criará uma cópia do repositório Tailspin Toys, iniciará um [codespace][codespaces] e confirmará que o GitHub Copilot Chat está disponível no editor.

## Configurar o repositório

1. Abra o [modelo Tailspin Toys][tailspin-template].
2. Selecione **Use this template** e depois **Create a new repository**.

   ![Botão Use this template](../../../_images/ex0-use-template.png)

3. Se estiver participando de um evento organizado pelo GitHub ou Microsoft, siga as orientações dos facilitadores. Caso contrário, crie o repositório em uma organização com acesso ao GitHub Copilot.

   ![Configurações do repositório criado a partir do modelo](../../../_images/ex0-repository-settings.png)

4. Anote o caminho criado (**organization-or-user-name/repository-name**).

> [!NOTE]
> **Seu backlog está pronto**
>
> Ao criar o repositório a partir do modelo, um backlog de issues é criado automaticamente. Você usará essas issues durante todo o workshop.

## Criar um codespace

1. Abra o repositório criado.
2. Selecione o botão verde **Code**.
3. Selecione **Codespaces** e o botão **+**.

   ![Criar um codespace](../../../_images/ex0-create-codespace.png)

> [!CAUTION]
> Você retornará ao codespace em um exercício futuro. Por enquanto, deixe-o aberto.

> [!NOTE]
> O workshop pode ser executado em um codespace ou em um [dev container][dev-containers] local.

## Usar o GitHub Copilot Chat e o modo agente

1. Volte ao codespace e abra o ícone **Copilot Chat**.
2. Se necessário, autentique-se com sua conta do GitHub.
3. Envie uma mensagem como “Hello world” no Copilot Chat.

> [!TIP]
> Se a extensão GitHub Copilot Chat não estiver instalada, use a [Visual Studio Code Marketplace][copilot-chat-extension].

## Resumo

Você criou uma cópia do repositório e iniciou o codespace que usará ao escrever código.

## Próxima etapa

Continue para o [Exercício 1 - Instruções personalizadas][next-lesson].

[codespaces]: https://github.com/features/codespaces
[dev-containers]: https://code.visualstudio.com/docs/devcontainers/containers
[tailspin-template]: https://github.com/github-samples/tailspin-toys
[template-repository]: https://docs.github.com/repositories/creating-and-managing-repositories/creating-a-template-repository
[copilot-chat-extension]: https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat
[next-lesson]: ../1-custom-instructions/

---
title: "Exercício 1 - Instruções personalizadas (VS Code)"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← Exercício anterior: Pré-requisitos][previous-lesson] · [Próximo exercício: modo agente →][next-lesson]

O contexto é essencial ao trabalhar com IA generativa. Os [arquivos de instruções][instruction-files] informam ao Copilot como e onde gerar código.

Neste exercício, você vai:

- explorar instruções do repositório e arquivos com escopo de caminho;
- gerar o primeiro componente da filtragem;
- adicionar um novo padrão global;
- repetir o prompt e observar a alteração;
- confirmar as instruções e o componente na branch `main`.

> [!CAUTION]
> O código gerado pode divergir dos padrões. Copilot é probabilístico; o objetivo é observar a tendência após atualizar as instruções.

## Cenário

A Tailspin Toys adota estas práticas:

- a camada de dados precisa de testes unitários;
- a interface deve usar tema escuro e aparência moderna;
- o código deve incluir comentários TSDoc;
- cada arquivo deve começar com um bloco que descreva sua finalidade.

## Criar uma branch

1. Abra um terminal no codespace.
2. Crie uma branch:

   ```bash
   git checkout -b custom-instructions
   ```

## Executar o prompt antes da atualização

1. Selecione **Agent** no seletor do Copilot Chat.
2. Abra `src/lib/publishers.ts`.
3. Envie:

   ```plaintext
   Create or update src/lib/publishers.ts with a data-access helper that returns a list of all publishers with the name and id for each. Apply the file changes.
   ```

4. Revise o helper e os testes gerados. Observe a ausência de comentários TSDoc ou do cabeçalho do arquivo.

## Adicionar o novo padrão

Em `.github/copilot-instructions.md`, localize **Code formatting requirements** e adicione:

```markdown
- Every exported function should have a TSDoc comment describing its purpose, parameters, and return value.
- Before imports or any code, add a comment block to the file that explains its purpose.
```

## Repetir o prompt

Inicie um novo chat, abra novamente `src/lib/publishers.ts` e envie o mesmo prompt. Confirme que o arquivo agora começa com um bloco de comentários e que a função inclui TSDoc.

## Confirmar e enviar

1. Revise `git status`.
2. Execute:

   ```bash
   git add .github/copilot-instructions.md src/lib/publishers.ts
   git commit -m "Add doc comment standards and publishers helper foundation"
   git push -u origin custom-instructions
   ```

3. Use o Copilot Chat para localizar a issue relacionada, criar uma PR e mesclá-la em `main`.

[previous-lesson]: ../0-prerequisites/
[next-lesson]: ../2-agent-mode/
[instruction-files]: https://docs.github.com/copilot/customizing-copilot/about-customizing-github-copilot-chat-responses

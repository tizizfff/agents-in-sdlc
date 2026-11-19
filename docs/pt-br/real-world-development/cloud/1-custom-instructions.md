---
title: "Exercício 1 - Instruções personalizadas (agente de nuvem)"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← Exercício anterior: Pré-requisitos][previous-lesson] · [Próximo exercício: agente de nuvem do Copilot →][next-lesson]

O contexto é essencial ao trabalhar com IA generativa. Os [arquivos de instruções][instruction-files] fazem o Copilot entender não apenas *o que* deve fazer, mas *como* deve fazê-lo.

Neste exercício, você vai:

- explorar como contexto específico do projeto, diretrizes de código e padrões de documentação chegam ao Copilot;
- adicionar um padrão global ao `.github/copilot-instructions.md`.

> [!NOTE]
> Ao contrário dos exercícios do VS Code e do CLI, não será usado um prompt antes/depois. O agente de nuvem trabalha de forma assíncrona em issues do GitHub. Você verá o efeito das instruções ao revisar as solicitações de pull criadas pelo agente.

## Arquivos de instruções

A Tailspin Toys adota estas práticas:

- a camada de dados sempre precisa de testes unitários;
- a interface deve usar tema escuro e aparência moderna;
- a documentação no código deve usar comentários TSDoc;
- cada arquivo deve começar com um bloco que descreva sua finalidade.

Há dois tipos principais:

- `.github/copilot-instructions.md`, enviado ao Copilot em todas as solicitações relacionadas ao repositório;
- `.github/instructions/*.instructions.md`, com instruções por tarefa, idioma ou tipo de arquivo.

> [!NOTE]
> Copilot Chat, Copilot CLI e agente de nuvem usam o arquivo de instruções do repositório e os arquivos com frontmatter `applyTo` ao gerar código.

## Explorar os arquivos deste projeto

1. Abra `.github/copilot-instructions.md`.
2. Observe a descrição do projeto e as seções **Agent notes**, **Code standards**, **Scripts** e **Repository Structure**.
3. Abra `.github/instructions` e explore os arquivos para Astro, Drizzle, testes e outros.
4. Abra `.github/instructions/unit-tests.instructions.md` e observe o campo `applyTo`.
5. Abra `.github/instructions/drizzle.instructions.md` e revise seus links para outros arquivos.

## Adicionar um novo padrão

Em `.github/copilot-instructions.md`, localize **Code formatting requirements** e adicione:

```markdown
- Every exported function should have a TSDoc comment describing its purpose, parameters, and return value.
- Before imports or any code, add a comment block to the file that explains its purpose.
```

Salve o arquivo.

## Confirmar, enviar e mesclar

1. Crie e alterne para uma branch:

   ```bash
   git checkout -b custom-instructions-cloud
   ```

2. Confirme e envie:

   ```bash
   git add .github/copilot-instructions.md
   git commit -m "Add doc comment and file-header standards to copilot instructions"
   git push -u origin custom-instructions-cloud
   ```

3. Abra uma solicitação de pull de `custom-instructions-cloud` para `main` e mescle-a.

## Resumo e próximos passos

Você explorou o contexto usado pelo agente de nuvem e adicionou um padrão global ao repositório. Em seguida, atribua uma issue ao agente de nuvem.

[previous-lesson]: ../0-prerequisites/
[next-lesson]: ../2-cloud-agent/
[instruction-files]: https://docs.github.com/copilot/customizing-copilot/about-customizing-github-copilot-chat-responses

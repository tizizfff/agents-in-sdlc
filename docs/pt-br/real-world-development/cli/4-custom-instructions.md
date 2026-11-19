---
title: "Lição 4 - Orientar o Copilot com instruções personalizadas"
description: "Explore instruções do repositório, adicione um padrão de documentação e aplique-o ao código da filtragem."
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

O contexto é essencial ao trabalhar com IA generativa. Para tarefas que precisam seguir uma determinada maneira, essa orientação deve estar disponível ao Copilot. Os [arquivos de instruções][instruction-files] descrevem não apenas *o que* você deseja, mas *como* o código deve ser estruturado. Agora que você criou a filtragem, vai explorar as instruções usadas pelo Copilot, adicionar um padrão de documentação e aplicá-lo ao código.

Nesta lição, você vai:

- explorar como instruções do repositório e instruções com escopo de caminho chegam ao agente;
- atualizar o arquivo de instruções para garantir que os padrões de código sejam seguidos;
- observar o impacto dos arquivos de instruções no código.

## Cenário

A Tailspin Toys tem um conjunto de diretrizes e requisitos para práticas de desenvolvimento:

- Comentários devem explicar a intenção e decisões não óbvias, em vez de repetir o código.
- Funções exportadas em `db/` e `src/lib/` devem documentar finalidade, parâmetros e valores de retorno com TSDoc/JSDoc, incluindo o argumento `db` injetável quando presente.
- Componentes Astro reutilizáveis devem documentar seus contratos `Props`, e os comentários devem permanecer atualizados.
- As orientações existentes de formatação e lint devem ser preservadas.

Os arquivos de instruções garantem que o Copilot tenha as informações necessárias para realizar as tarefas alinhadas a essas práticas.

## Explorar os arquivos de instruções

1. Volte ao Codespace.
2. Abra `.github/copilot-instructions.md` no editor.
3. Observe a descrição do projeto e as orientações de código. Elas se aplicam a todas as interações com o Copilot neste repositório.
4. Explore os arquivos em `.github/instructions`. Eles incluem orientações para Astro, Drizzle, testes e outros tipos.
5. Abra `.github/instructions/unit-tests.instructions.md` e observe o campo `applyTo`.
6. Abra `.github/instructions/drizzle.instructions.md` e observe os links para outros arquivos e projetos existentes.

## Atualizar as instruções

1. Em `.github/copilot-instructions.md`, encontre a seção **Code formatting guidance**, próxima da linha 35.
2. Adicione como último item:

   ```markdown
   - All new TypeScript should contain TSDocs comments for documentation purposes.
   ```

## Usar a orientação atualizada

O Copilot CLI carrega as instruções ao iniciar uma conversa. Após salvar a alteração, saia e retome a conversa de filtragem para que o Copilot use a nova orientação sem perder o contexto.

1. Se a conversa ainda estiver aberta, digite `/exit`.
2. Na raiz do repositório, na branch `game-filters-cli`, retome a conversa:

   ```bash
   copilot --resume
   ```

3. Peça ao Copilot que aplique a orientação:

   ```plaintext
   We just updated our instructions and code guidance. Can you please update the code you generated to match that guidance?
   ```

4. Digite `/diff` e revise os arquivos TypeScript. Confirme os comentários TSDoc recém-gerados.

## Resumo e próximos passos

Você explorou como o Copilot CLI obtém contexto dos arquivos de instruções e aplicou um novo padrão ao recurso. Em seguida, personalize e execute o skill reutilizável `quality-checks`.

## Recursos

- [Adicionar instruções personalizadas ao Copilot CLI][instruction-files]
- [Suporte a instruções personalizadas][custom-instructions-support]
- [Melhores práticas para instruções personalizadas][instructions-best-practices]
- [Awesome Copilot][awesome-copilot]

[instruction-files]: https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/add-custom-instructions
[instructions-best-practices]: https://docs.github.com/copilot/concepts/prompting/response-customization#writing-effective-custom-instructions
[awesome-copilot]: https://awesome-copilot.github.com/
[custom-instructions-support]: https://docs.github.com/copilot/reference/custom-instructions-support
[previous-lesson]: ../3-agent-modes/
[next-lesson]: ../5-agent-skills/

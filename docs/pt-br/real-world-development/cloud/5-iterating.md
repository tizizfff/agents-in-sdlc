---
title: "Exercício 5: Iterar sobre o trabalho do GitHub Copilot"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

| [← Exercício anterior: Gerenciar agentes][previous-lesson] |
|:--|

## Revisar o trabalho

Nesta prática, você trabalhou com o GitHub Copilot em documentação, jogos relacionados e recursos de acessibilidade. Revise as alterações e forneça comentários ao Copilot quando necessário.

## Segurança

O agente de nuvem possui somente leitura no repositório e gravação limitada à branch em que trabalha. Ele é executado em GitHub Actions em um ambiente temporário. Fluxos de trabalho do Actions exigem aprovação humana e o acesso a recursos externos é restrito por padrão.

## Revisar a documentação

1. Abra a PR criada pelo agente para adicionar documentação.
2. Selecione **Files changed** e revise os comentários TSDoc e cabeçalhos.
3. Na guia **Conversation**, aprove os fluxos de trabalho aguardando execução.
4. Confirme que as verificações do projeto passam.

## Solicitar alterações

No GitHub, marque `@copilot` em comentários da PR ou em linhas específicas do código. O Copilot iniciará uma nova sessão para aplicar a alteração. Por exemplo, você pode pedir:

- cabeçalhos de comentário no início de cada arquivo;
- comentários TSDoc em arquivos TypeScript e Astro;
- um README descrevendo a estrutura do aplicativo Astro.

Depois da atualização, revise o novo commit e continue iterando até ficar satisfeito.

## Revisar jogos relacionados

Abra a PR correspondente à issue de jogos relacionados, revise os arquivos alterados e aprove os fluxos de trabalho se necessário. Para testar manualmente, no Codespace:

```bash
git fetch origin
git checkout <branch-name>
```

## Revisar recursos de acessibilidade

Revise a PR que implementa os modos de alto contraste e claro. Confirme:

- componentes de alternância;
- persistência em local storage;
- alterações de CSS;
- atributos de acessibilidade;
- código TypeScript/JavaScript de troca de modo.

Pode-se iniciar o aplicativo e testar a persistência após recarregar a página.

## Resumo

Você concluiu o percurso do agente de nuvem. Entre as práticas realizadas:

- inspecionou instruções personalizadas;
- atribuiu issues ao agente de nuvem;
- criou e usou um agente de acessibilidade;
- monitorou e orientou sessões;
- revisou e iterou sobre PRs.

## Próximos passos

Para continuar, explore o [workshop do VS Code](../../vscode/) ou o [workshop do CLI](../../cli/). Em seu próprio repositório, atribua uma issue de refatoração ou cobertura de testes e configure `copilot-setup-steps.yml`.

[previous-lesson]: ../4-managing-agents/

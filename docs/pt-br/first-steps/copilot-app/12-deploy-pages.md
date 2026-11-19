---
title: "Lição 12 - Implantar o site com GitHub Pages"
description: "Use o aplicativo GitHub Copilot para configurar um fluxo de trabalho de Pages, revisar sua solicitação de pull e verificar o Space Quiz publicado."
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

Dê ao Space Quiz uma presença pública implantando-o com GitHub Pages. O Copilot pode preparar o fluxo de trabalho e orientar a implantação, mas a responsabilidade por revisar as alterações e confirmar que o site está ativo continua sendo sua.

Nesta lição, você vai:

- pedir ao Copilot para configurar uma implantação no GitHub Pages.
- revisar o fluxo de trabalho e a solicitação de pull antes da mesclagem.
- acompanhar a implantação e verificar o site publicado.

## Cenário

O Space Quiz já está em um repositório do GitHub, mas as pessoas ainda precisam de uma maneira simples de experimentá-lo. Publicar o site de um único arquivo com GitHub Pages o torna disponível por uma URL pública, sem adicionar um servidor ou uma dependência de runtime.

## Peça ao Copilot para preparar a implantação

> [!WARNING]
> Criar uma solicitação de pull pode confirmar e enviar código. Revise suas configurações de aprovação e o repositório de destino antes de enviar este prompt. Com **Aprovar tudo**, não espere uma solicitação de confirmação separada.

Na sessão do aplicativo Copilot para `space-quiz`, envie este prompt:

```plaintext
Prepare a GitHub Pages deployment for this repository. Create a GitHub Actions workflow that builds the website if needed and deploys it to GitHub Pages after changes reach the default branch. Add a README describing the app and how to run it locally if one does not already exist. Create a pull request with these changes and report its link and any required Pages settings or permissions. Do not merge, enable auto-merge, change Pages settings, or deploy. Stop and wait for my review.
```

## Revisar o fluxo de trabalho e a solicitação de pull

1. Confirme que o README só foi adicionado quando o repositório ainda não tinha um.
2. Revise as alterações da solicitação de pull, incluindo as etapas de compilação e implantação do fluxo de trabalho, os gatilhos e as permissões.
3. Confirme que o fluxo de trabalho implanta a partir da branch padrão, não de uma solicitação de pull não mesclada.
4. Solicite correções e revise o diff atualizado. Aguarde a aprovação das verificações obrigatórias da solicitação de pull antes de autorizar uma mesclagem.

## Autorizar a mesclagem e a implantação

> [!WARNING]
> O prompt a seguir autoriza o agente a mesclar a solicitação de pull revisada, alterar as configurações de Pages do repositório e publicar o site. Envie-o somente após concluir a revisão e confirmar o repositório e a solicitação de pull. As configurações de aprovação podem permitir essas ações sem outra solicitação de confirmação.

Substitua `<PR_NUMBER>` pelo número da solicitação de pull que você revisou e envie este prompt separado:

```plaintext
I have reviewed pull request <PR_NUMBER> in this repository and authorize its merge and deployment. Enable GitHub Pages using GitHub Actions, merge that pull request only after required checks pass, and monitor the deployment until it succeeds. Report the final URL of the live website. If you lack permission to enable Pages or merge, tell me exactly what I need to approve or do; do not report success until the site is live.
```

![Diagrama de três etapas: uma solicitação de pull mesclada do space-quiz; uma execução bem-sucedida do GitHub Actions Deploy website com as etapas Build website, Upload artifact e Deploy to Pages; e o Space Quiz publicado em yourname.github.io/space-quiz/.](../../../_images/first-steps-app-pages-deploy.svg)

## Verificar a implantação

1. Acompanhe a execução da implantação do GitHub Actions até que ela seja concluída com sucesso.
2. Abra a URL informada e confirme que o Space Quiz é carregado.

Se o agente não conseguir habilitar Pages ou mesclar a solicitação de pull, siga as instruções específicas fornecidas. Não considere a tarefa concluída até que a implantação tenha sido concluída e o site publicado carregue.

## Resumo e próximos passos

Seu Space Quiz agora está disponível como um site publicado, e você verificou a implantação em vez de confiar no relatório do agente. Continue para a [Lição 13: Revisão e próximos passos][next-lesson].

[next-lesson]: ../13-review/

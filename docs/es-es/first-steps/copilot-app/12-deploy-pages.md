---
title: "Lección 12 - Implementa el sitio con GitHub Pages"
description: "Utiliza la aplicación GitHub Copilot para configurar un flujo de trabajo de Pages, revisar su solicitud de incorporación de cambios y comprobar el Space Quiz publicado."
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

Da al Space Quiz una ubicación pública mediante su implementación con GitHub Pages. Copilot puede preparar el flujo de trabajo y orientar la implementación, pero tú sigues siendo responsable de revisar los cambios y confirmar que el sitio esté activo.

En esta lección:

- pedirás a Copilot que configure una implementación de GitHub Pages.
- revisarás el flujo de trabajo y la solicitud de incorporación de cambios antes de combinarla.
- seguirás la implementación y comprobarás el sitio publicado.

## Escenario

El Space Quiz ya está en un repositorio de GitHub, pero las personas necesitan una forma sencilla de probarlo. Publicar el sitio de un solo archivo con GitHub Pages lo hace disponible desde una URL pública sin añadir un servidor ni una dependencia de runtime.

## Pide a Copilot que prepare la implementación

> [!WARNING]
> Crear una solicitud de incorporación de cambios puede confirmar y enviar código. Revisa la configuración de aprobaciones y el repositorio de destino antes de enviar esta petición. Con **Aprobar todo**, no esperes otro aviso de confirmación.

En la sesión de la aplicación Copilot para `space-quiz`, envía esta petición:

```plaintext
Prepare a GitHub Pages deployment for this repository. Create a GitHub Actions workflow that builds the website if needed and deploys it to GitHub Pages after changes reach the default branch. Add a README describing the app and how to run it locally if one does not already exist. Create a pull request with these changes and report its link and any required Pages settings or permissions. Do not merge, enable auto-merge, change Pages settings, or deploy. Stop and wait for my review.
```

## Revisa el flujo de trabajo y la solicitud de incorporación de cambios

1. Confirma que el README se añade solo si el repositorio todavía no tiene uno.
2. Revisa los cambios de la solicitud de incorporación de cambios, incluidos los pasos de compilación e implementación del flujo de trabajo, los desencadenadores y los permisos.
3. Confirma que el flujo de trabajo se implementa desde la rama predeterminada, no desde una solicitud de incorporación de cambios sin combinar.
4. Solicita las correcciones necesarias y revisa la diferencia actualizada. Espera a que finalicen las comprobaciones requeridas de la solicitud de incorporación de cambios antes de autorizar una combinación.

## Autoriza la combinación y la implementación

> [!WARNING]
> La siguiente petición autoriza al agente a combinar la solicitud de incorporación de cambios revisada, cambiar la configuración de Pages del repositorio y publicar el sitio. Envíala solo después de completar la revisión y confirmar el repositorio y la solicitud de incorporación de cambios. La configuración de aprobaciones puede permitir estas acciones sin otro aviso de confirmación.

Reemplaza `<PR_NUMBER>` por el número de la solicitud de incorporación de cambios que has revisado y, a continuación, envía esta petición independiente:

```plaintext
I have reviewed pull request <PR_NUMBER> in this repository and authorize its merge and deployment. Enable GitHub Pages using GitHub Actions, merge that pull request only after required checks pass, and monitor the deployment until it succeeds. Report the final URL of the live website. If you lack permission to enable Pages or merge, tell me exactly what I need to approve or do; do not report success until the site is live.
```

![Diagrama de tres etapas: una solicitud de incorporación de cambios combinada de space-quiz; una ejecución correcta de GitHub Actions para implementar el sitio web con los pasos Compilar sitio web, Cargar artefacto e Implementar en Pages; y el Space Quiz activo en yourname.github.io/space-quiz/.](../../../_images/first-steps-app-pages-deploy.svg)

## Comprueba la implementación

1. Sigue la ejecución de implementación de GitHub Actions hasta que finalice correctamente.
2. Abre la URL indicada y confirma que el Space Quiz se carga.

Si el agente no puede activar Pages ni combinar la solicitud de incorporación de cambios, sigue las instrucciones específicas que proporcione. No consideres que la tarea está completa hasta que la implementación finalice y el sitio activo se cargue.

## Resumen y próximos pasos

Tu Space Quiz ya está disponible como sitio activo y has comprobado la implementación en lugar de confiar en el informe del agente. Continúa con la [lección 13: Revisión y próximos pasos][next-lesson].

[next-lesson]: ../13-review/

---
title: "Ejercicio 5: Iterar sobre el trabajo de GitHub Copilot"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

| [← Lección anterior: Gestionar agentes][previous-lesson] |
|:--|

## Revisión del trabajo

Los fundamentos del diseño de software y DevOps no cambian por el uso de IA generativa. Debes revisar siempre el código generado y aplicar el proceso habitual de DevOps. Revisa las propuestas de GitHub Copilot para documentación, juegos relacionados y funciones de accesibilidad antes de aprobar el trabajo para el resto del equipo.

## Seguridad y agente en la nube

El agente en la nube realiza las tareas de forma asincrónica y sin supervisión continua. Por ello se aplican restricciones de seguridad:

- Copilot solo tiene acceso de lectura al repositorio y acceso de escritura únicamente a la rama que utiliza.
- El agente se ejecuta dentro de GitHub Actions en un entorno separado y efímero.
- Los flujos de GitHub Actions requieren la aprobación de una persona antes de ejecutarse.
- El acceso a recursos externos está limitado de forma predeterminada, incluidos los servidores MCP.

## Revisa la documentación generada

1. Abre tu repositorio en github.com.
2. Selecciona **Pull Requests**.
3. Abre la solicitud de incorporación de cambios titulada de forma similar a **Add missing documentation**.
4. Selecciona la pestaña **Files changed** y revisa los cambios.
5. Busca comentarios de documentación TSDoc, convenciones de TypeScript y cabeceras de comentario.
6. Vuelve a la pestaña **Conversation** y, si existen flujos de trabajo a la espera, selecciona **Approve and run workflows**.

> [!NOTE]
> Es posible que veas una advertencia de que GitHub Copilot está bloqueado por un cortafuegos. Es un comportamiento esperado: el acceso externo está limitado de forma predeterminada. Si lo necesitas, puedes [personalizar o desactivar el cortafuegos del agente en la nube][agent-firewall].

## Solicita cambios

Puedes pedir cambios a Copilot mediante comentarios en la solicitud de incorporación de cambios o comentarios en línea:

- Añade cabeceras de comentario al principio de cada archivo de código.
- Añade comentarios de documentación TSDoc a archivos TypeScript y Astro.
- Crea un README con una descripción de la estructura de la aplicación Astro.

1. Añade un comentario y menciona a **@copilot**.
2. Selecciona **View Session** para seguir el trabajo.
3. Cuando Copilot termine, revisa el nuevo confirmación en la pestaña **Files changed**.

## Revisa el resto de funciones

Revisa la solicitud de incorporación de cambios que muestra juegos relacionados en la página de detalles y las solicitudes asociadas al modo de alto contraste y al modo claro. Comprueba los cambios, ejecuta los flujos de trabajo requeridos y realiza las pruebas manuales necesarias antes de marcar cada solicitud como preparada para revisión y combinarla.

[previous-lesson]: ../4-managing-agents/
[agent-firewall]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-firewall

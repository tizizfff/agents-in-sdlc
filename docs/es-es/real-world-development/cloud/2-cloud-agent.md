---
title: "Ejercicio 2 - Agente de GitHub Copilot en la nube"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

| [← Lección anterior: Instrucciones personalizadas][previous-lesson] |
|:--|

Las organizaciones deben gestionar la deuda técnica, los problemas de seguridad, el código heredado y las solicitudes de nuevas funciones. El agente de GitHub Copilot en la nube puede realizar estas tareas de forma autónoma y genera una solicitud de incorporación de cambios en borrador para que una persona desarrolladora revise su trabajo.

Explorarás:

- cómo personalizar el entorno de generación de código;
- cómo garantizar operaciones seguras;
- la importancia de definir bien el alcance de las incidencias;
- cómo asignar incidencias a Copilot.

## Escenarios

Tailspin Toys quiere resolver deuda técnica y mejorar la detección de juegos. Primero se solicita añadir comentarios de documentación TSDoc a todas las funciones exportadas. Además, el equipo de diseño quiere mostrar juegos relacionados en la página de detalles de un juego para que las personas puedan seguir explorando títulos de la misma categoría.

## Presentación del agente de GitHub Copilot en la nube

[GitHub Copilot cloud agent][cloud-agent] puede realizar tareas en segundo plano. Cuando se asigna una incidencia, Copilot crea una solicitud de incorporación de cambios en borrador, prepara un entorno y comienza a trabajar. Puedes consultar su sesión mientras está en curso o después de completarla.

## Configuración del entorno

El agente utiliza GitHub Actions para preparar el entorno de trabajo. El flujo `.github/workflows/copilot-setup-steps.yml` configura Node.js, las dependencias, los navegadores de Playwright y la base de datos SQLite migrada y poblada para la aplicación Astro. Las herramientas necesarias están disponibles antes de que Copilot empiece a trabajar.

## Asigna una tarea

1. Abre el repositorio en GitHub.
2. Selecciona la pestaña **Issues**.
3. Abre una incidencia existente o crea una nueva con un resultado concreto y criterios verificables.
4. Selecciona **Assign to Copilot** en la barra lateral de la incidencia.
5. Supervisa la sesión y revisa la solicitud de incorporación de cambios que cree.

[previous-lesson]: ../1-custom-instructions/
[cloud-agent]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent

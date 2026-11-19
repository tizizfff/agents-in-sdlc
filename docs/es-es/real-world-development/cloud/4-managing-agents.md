---
title: "Ejercicio 4 - Supervisar y gestionar agentes"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

Durante los ejercicios anteriores solicitaste a Copilot tres tareas centradas en mejorar la experiencia de usuario y añadir funciones. Aunque el agente en la nube está diseñado para funcionar de forma asincrónica y autónoma, resulta importante supervisar su trabajo.

En esta lección:

- explorarás la página de agentes para supervisar las tareas del agente en la nube;
- dirigirás una sesión en curso para solicitar una función adicional.

## Revisa las tareas del agente

1. Accede a la [página de agentes de Copilot](https://github.com/copilot/agents).
2. Revisa las tareas del panel principal y del panel izquierdo. Deberían aparecer las tareas asignadas a Copilot.
3. Selecciona una tarea en ejecución y revisa las operaciones realizadas. Estas pueden incluir la obtención del código, la creación del entorno, la configuración de MCP y la ejecución de los pasos necesarios.

> [!NOTE]
> Los pasos exactos varían según el estado del trabajo y el enfoque adoptado por Copilot.

4. Revisa también el panel de solicitudes de incorporación de cambios de la derecha para controlar los cambios adicionales.

## Dirige el agente en la nube

Después de asignar al agente la creación del modo de alto contraste, el equipo decide añadir también un modo claro. Solicita que incorpore ambos modos.

1. Selecciona la sesión correspondiente al modo de alto contraste.

   ![Sesión de accesibilidad en el centro de control](../../../_images/ex6-accessibility-session.png)

2. Espera a que indique que ha completado la preparación y ha comenzado el trabajo.
3. En el diálogo **Steer active session while Copilot is working**, añade el siguiente aviso:

   ```plaintext
   While we are working on a high contrast mode, let's also add a light mode. There should be a switch for this mode as well where users can select their desired display mode.
   ```

4. Selecciona <kbd>Enter</kbd> para enviar el aviso.
5. Comprueba que Copilot reconoce la petición y la incorpora a su flujo.

## Resumen y próximos pasos

La página de agentes es el centro de control para supervisar y orientar las tareas del agente de GitHub Copilot en la nube. Puedes hacer seguimiento de las tareas activas y completadas, revisar el trabajo realizado y ajustar tareas en curso.

Ahora puedes pasar a [iterar sobre las solicitudes de incorporación de cambios creadas por Copilot][next-lesson].

[next-lesson]: ../5-iterating/

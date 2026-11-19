---
title: "Ejercicio 1 - Instrucciones personalizadas (agente en la nube)"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← Lección anterior: Requisitos previos][previous-lesson] · [Siguiente lección: Agente de GitHub Copilot en la nube →][next-lesson]

El contexto es fundamental al trabajar con IA generativa. Si una tarea debe realizarse de una forma concreta o Copilot necesita información general, debes asegurarte de que ese contexto esté disponible. Los [archivos de instrucciones][instruction-files] permiten proporcionar esas indicaciones para que Copilot comprenda no solo qué quieres que haga, sino cómo quieres que lo haga.

En este ejercicio:

- explorarás cómo las instrucciones personalizadas del repositorio y los archivos de instrucciones con ámbito por ruta hacen llegar a Copilot el contexto específico del proyecto, las directrices de programación y los estándares de documentación;
- añadirás un nuevo estándar válido para todo el repositorio en `.github/copilot-instructions.md`.

> [!NOTE]
> A diferencia de los talleres de VS Code y CLI, aquí no ejecutarás una prueba antes/después: el agente de GitHub Copilot en la nube trabaja de forma asincrónica en las incidencias de GitHub, por lo que el impacto es más difícil de comparar en tiempo real. Verás la influencia del archivo de instrucciones más adelante en este taller, al revisar las solicitudes de incorporación de cambios creadas por el agente en la nube.

## Archivos de instrucciones

### Escenario

Como corresponde a una empresa desarrolladora responsable, Tailspin Toys dispone de directrices y requisitos para sus prácticas de desarrollo. Estos incluyen:

- La capa de datos siempre necesita pruebas unitarias.
- La interfaz debe tener un tema oscuro y una apariencia moderna.
- La documentación debe añadirse al código mediante comentarios de documentación TSDoc.
- Debe añadirse un bloque de comentarios al principio de cada archivo que describa su función.

Mediante los archivos de instrucciones te asegurarás de que Copilot tenga la información correcta para realizar las tareas conforme a estas prácticas.

### Instrucciones personalizadas

Las instrucciones personalizadas permiten proporcionar a Copilot contexto y preferencias, de modo que pueda comprender mejor tu estilo de programación y tus requisitos. Esta función ayuda a orientar a Copilot para obtener sugerencias y fragmentos de código más relevantes. Puedes indicar convenciones de programación, bibliotecas y tipos de comentarios preferidos. Puedes crear instrucciones para todo el repositorio o para tipos de archivos específicos.

Hay dos tipos de archivos de instrucciones:

- `.github/copilot-instructions.md`, un único archivo de instrucciones que se envía a Copilot en **cada** solicitud para el repositorio. Debe contener información del proyecto: contexto relevante para la mayoría de las solicitudes enviadas a Copilot desde el chat o CLI.
- Los archivos `.github/instructions/*.instructions.md` pueden crearse para tareas o tipos de archivos concretos. Puedes utilizarlos para proporcionar directrices para lenguajes como TypeScript o Astro, o para tareas como crear un componente de interfaz o un conjunto de pruebas unitarias.

> [!NOTE]
> Cuando trabajas en tu IDE, los archivos de instrucciones solo se utilizan para la generación de código en Copilot Chat, no para las sugerencias de autocompletado ni las siguientes modificaciones.

## Añade un nuevo estándar del repositorio

El siguiente paso será añadir una regla válida para todo el proyecto: la documentación debe incluirse en el código mediante comentarios de documentación TSDoc y una cabecera de comentario a nivel de archivo. El agente en la nube tendrá en cuenta esta regla al trabajar en las incidencias que le asignes más adelante.

1. Desde el terminal de tu Codespace, crea y cambia a una rama nueva:

   ```bash
   git checkout -b custom-instructions-cloud
   ```

2. Abre `.github/copilot-instructions.md`.
3. Localiza la sección **Code formatting requirements**.
4. Añade debajo las directrices de documentación de TSDoc y cabecera de archivo.

> [!TIP]
> No es necesario recordar a Copilot las directrices en cada petición: se aplican automáticamente desde el archivo de instrucciones.

## Resumen

Has explorado los archivos de instrucciones del repositorio y has añadido una norma compartida para que el agente en la nube genere documentación coherente en el código.

[instruction-files]: https://docs.github.com/copilot/concepts/agents/about-agent-skills
[previous-lesson]: ../0-prerequisites/
[next-lesson]: ../2-cloud-agent/

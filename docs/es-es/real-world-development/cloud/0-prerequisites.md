---
title: "Ejercicio 0: Requisitos previos"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

Antes de comenzar los ejercicios del agente de GitHub Copilot en la nube, necesitas preparar el entorno. Crearás tu propia copia del repositorio Tailspin Toys y abrirás un [Codespace][codespaces] que podrás utilizar para editar los archivos de instrucciones y revisar el trabajo realizado por el agente en la nube.

## Configura el repositorio del taller

Para crear una copia del repositorio que utilizarás, crea una instancia a partir de la [plantilla][template-repository]. La nueva instancia contendrá todos los archivos necesarios para el taller y se utilizará a lo largo de los ejercicios.

1. Abre una ventana nueva del navegador y accede a la [plantilla de Tailspin Toys][tailspin-template].
2. Crea tu propia copia del repositorio mediante el botón **Use this template** en la página del repositorio del taller. Después, selecciona **Create a new repository**.

   ![Botón Use this template](../../../_images/ex0-use-template.png)

3. Si realizas el taller como parte de un evento dirigido por GitHub o Microsoft, sigue las instrucciones de las personas mentor. En caso contrario, puedes crear el nuevo repositorio en una organización en la que tengas acceso a GitHub Copilot.

   ![Configuración del repositorio creado a partir de la plantilla](../../../_images/ex0-repository-settings.png)

4. Anota la ruta del repositorio creado (**nombre-de-organizacion-o-usuario/nombre-del-repositorio**), porque deberás consultarla más adelante en el taller.

## Crea un Codespace

A continuación, utilizarás un Codespace para completar los ejercicios.

[GitHub Codespaces][codespaces] es un entorno de desarrollo basado en la nube que te permite escribir, ejecutar y depurar código directamente desde el navegador. Incluye un IDE completo con compatibilidad con varios lenguajes de programación, extensiones y herramientas.

1. Accede al repositorio que acabas de crear.
2. Selecciona el botón verde **Code**.

   ![Selecciona el botón Code](../../../_images/ex0-code-button.png)

3. Selecciona la pestaña **Codespaces** y el botón **+** para crear un Codespace.

   ![Crea un Codespace](../../../_images/ex0-create-codespace.png)

La creación del Codespace tardará varios minutos, aunque será mucho más rápida que instalar todos los servicios manualmente. Mientras tanto, puedes explorar otras funciones de GitHub Copilot, que veremos a continuación.

> [!CAUTION]
> Volverás a este Codespace en un ejercicio posterior. De momento, déjalo abierto en una pestaña del navegador.

> [!NOTE]
> Este taller está diseñado para ejecutarse dentro de un Codespace o de un [contenedor de desarrollo][dev-containers] local. Ambos garantizan que el entorno tenga todos los requisitos previos necesarios para una experiencia fluida. Si prefieres ejecutarlo localmente, abre el repositorio clonado en VS Code y selecciona **Reopen in Container** cuando se indique; VS Code construirá el mismo contenedor de desarrollo que utiliza el Codespace.

[codespaces]: https://github.com/features/codespaces
[dev-containers]: https://code.visualstudio.com/docs/devcontainers/containers

## Resumen

Enhorabuena: has creado una copia del repositorio del taller y has iniciado la creación de tu Codespace, que utilizarás junto al agente de GitHub Copilot en la nube.

## Próximo paso

Vamos a añadir las instrucciones personalizadas que seguirá el agente en la nube. Continúa con el [Ejercicio 1: Instrucciones personalizadas][next-lesson].

## Recursos

- [Información general sobre GitHub Codespaces][codespaces]
- [Crear un repositorio a partir de una plantilla][template-repository]
- [Primeros pasos con Codespaces][codespaces-quickstart]

[tailspin-template]: https://github.com/github-samples/tailspin-toys
[template-repository]: https://docs.github.com/repositories/creating-and-managing-repositories/creating-a-template-repository
[codespaces-quickstart]: https://docs.github.com/codespaces/getting-started/quickstart
[next-lesson]: ../1-custom-instructions/

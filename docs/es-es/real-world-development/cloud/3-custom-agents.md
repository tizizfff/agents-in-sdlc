---
title: "Ejercicio 3 - Agentes personalizados"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

## Qué son los agentes personalizados

Los [agentes personalizados][custom-agents-concept] permiten crear asistentes de IA especializados para tareas o ámbitos concretos del flujo de desarrollo. Al definir agentes mediante archivos Markdown en `.github/agents`, puedes proporcionar a Copilot instrucciones específicas, buenas prácticas, patrones de programación y conocimiento del dominio.

Los agentes personalizados tienen su propio contexto y pueden coordinar habilidades y herramientas. En este taller se utiliza un agente de accesibilidad para revisar y actualizar el sitio conforme a las directrices de accesibilidad.

> [!NOTE]
> No existe una única forma correcta de crear un agente personalizado. Prueba y itera para encontrar la configuración adecuada a tus entornos y escenarios.

## Escenario

Tailspin Toys quiere garantizar que la plataforma de financiación colectiva sea accesible para todas las personas. El equipo de diseño solicita un modo de alto contraste con un interruptor que guarde la preferencia en el almacenamiento local del navegador.

## Revisa el agente personalizado de accesibilidad

1. Desde tu Codespace, abre `.github/agents/accessibility.md`.
2. Revisa el frontmatter YAML con los campos `name` y `description`.
3. Examina las responsabilidades principales, las buenas prácticas, los ejemplos y los errores comunes.

> [!CAUTION]
> Los campos `name` y `description` del frontmatter son obligatorios para los agentes personalizados.

## Crea y asigna una incidencia

1. Accede a tu repositorio.
2. Selecciona la pestaña **Issues**.
3. Selecciona **New issue** y después **Blank issue**.
4. Establece el título `Add high contrast mode to website`.
5. Define una descripción que indique la necesidad del modo de alto contraste, su interruptor y el almacenamiento de la preferencia en el navegador.
6. Selecciona **Create**.
7. En la barra lateral, selecciona **Assign to Copilot**.
8. Selecciona el agente personalizado **Accessibility agent** y después **Assign**.

## Resumen y próximos pasos

Los agentes personalizados permiten codificar la experiencia y los estándares del equipo en asistentes reutilizables. Con Copilot creando el modo de alto contraste, puedes pasar a supervisar y dirigir la sesión del agente.

[custom-agents-concept]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents

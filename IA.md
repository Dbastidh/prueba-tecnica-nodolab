# Bitácora de uso de Inteligencia Artificial

Para la resolución de esta prueba, integré la IA como un asistente de arquitectura y _sparring_ técnico, no como un generador de código ciego.

## Herramienta utilizada

Gemini (Modelo conversacional)

## Interacciones más relevantes

**1. Análisis de requisitos Moodle:**

- **Prompt inicial:** "Tengo una prueba técnica para crear un componente HTML/SCSS que vivirá en Moodle. El usuario final editará el texto con el editor de Moodle, por lo que Moodle podría borrar las clases de las etiquetas `p`, `h3`, `img`. ¿Cuál es la mejor arquitectura CSS para evitar que se rompa el diseño?"
- **Resultado:** La IA sugirió el uso estricto de BEM en el wrapper principal (`.nodolab-banner`) y selectores de herencia directa para los elementos internos (`.nodolab-banner__content p`), lo cual apliqué directamente en la solución.

**2. Escalabilidad de temas SCSS:**

- **Prompt:** "Necesito que este mismo componente se adapte a diferentes clientes (cambiar fondos y colores) sin reescribir el SCSS base. ¿Cómo lo estructuro de la forma más limpia?"
- **Resultado:** La IA me recomendó inyectar Variables CSS (Custom Properties) dentro de clases modificadoras de BEM (`--theme-purple`, `--theme-teal`). Esto me permitió mantener un único bloque de estilos lógicos y sobreescribir únicamente las variables en cada versión.

## Ajustes manuales posteriores

- Extracción y optimización manual de los SVGs decorativos de fondo desde Figma para inyectarlos en la variable `background-image`.
- Ajuste fino de los márgenes (`gap` y `padding`) midiendo manualmente en Figma para garantizar la fidelidad visual exacta que requiere la prueba.
- Revisión de compilación local del SCSS.

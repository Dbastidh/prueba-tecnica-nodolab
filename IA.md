# Bitácora de uso de Inteligencia Artificial - NodoLab

Para el desarrollo de esta prueba, integré la IA como un asistente de arquitectura CSS y auditor técnico para optimizar los tiempos de entrega y resolver problemas de compatibilidad con Moodle.

## Herramienta utilizada
Gemini 3.1 Pro (Matemáticas y programación avanzada)

## Interacciones y Prompts más relevantes

### 1. Arquitectura para evitar el "Efecto Moodle"
* **Contexto/Prompt inicial:** Le planteé a la IA el requerimiento de que el contenido sería editado en Moodle y que el LMS suele borrar las clases directas de las etiquetas internas (`p`, `h3`, `img`). Le pregunté cuál era la mejor estrategia de maquetación.
* **Solución de la IA:** Se determinó usar la metodología BEM exclusivamente en los contenedores padres (`.nodolab-banner`, `.nodolab-banner__content`) y aplicar selectores de herencia directa para los elementos internos (`.nodolab-banner__content p`, `.nodolab-banner__content h3`). Esto garantiza que si el usuario borra o reemplaza el texto en Moodle perdiendo las clases, el diseño base se mantendrá intacto.

### 2. Implementación de gradientes y patrones combinados
* **Problema:** Al inspeccionar Figma, detecté que el fondo no era sólido sino un gradiente lineal combinado con un patrón vectorial (ondas/figuras). 
* **Prompt a la IA:** "¿Cómo puedo estructurar el SCSS para soportar un gradiente de fondo y un patrón SVG al mismo tiempo de manera escalable?"
* **Solución de la IA:** Sugirió implementar *Multiple Backgrounds* nativos en CSS combinados con Variables CSS (Custom Properties) dentro de los modificadores de BEM (`--theme-purple`, `--theme-teal`). Esto permitió apilar el patrón decorativo por encima del gradiente lineal en una sola propiedad limpia.

### 3. Ajuste de distorsión del fondo (Refinamiento manual guiado)
* **Problema:** El fondo decorativo se estiraba demasiado e invadía el área del texto al usar `background-size: cover`.
* **Interacción con la IA:** Solicitando asistencia para corregir la silueta invasiva, la IA recomendó cambiar el tamaño del background a `auto 100%` y alinearlo a la derecha (`right center`). Esto limitó el crecimiento horizontal de los vectores decorativos, logrando una fidelidad visual exacta con respecto al Figma.

## Decisiones y ajustes manuales
* **Auditoría de capas en Figma:** Se aislaron manualmente las capas en Figma para exportar los elementos correctos (ilustraciones en PNG transparente y decoraciones de fondo en SVG), corrigiendo un error inicial donde se estaba exportando el marco completo de la tarjeta.
* **Compilación:** Se utilizó la extensión *Live Sass Compiler* en Visual Studio Code para procesar y minificar el archivo `style.css` final de manera automatizada.
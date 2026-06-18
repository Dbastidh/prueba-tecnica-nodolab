# Bitácora de uso de Inteligencia Artificial - NodoLab

Para el desarrollo de esta prueba, integré la IA como un asistente de arquitectura CSS y auditor técnico para optimizar los tiempos de entrega y resolver problemas de compatibilidad con Moodle.

## Herramienta utilizada

Gemini 3.1 Pro (Matemáticas y programación avanzada)

## Interacciones y Prompts más relevantes

### 1 Arquitectura para evitar el "Efecto Moodle"

* **Contexto/Prompt inicial:** Le planteé a la IA el requerimiento de que el contenido sería editado en Moodle y que el LMS suele borrar las clases directas de las etiquetas internas (`p`, `h3`, `img`) con el siguiente prompt:


Actúa como un desarrollador Frontend Senior experto en arquitectura CSS para entornos Moodle. Necesito maquetar un componente de tarjeta (banner) de texto e imagen basándome en un diseño de Figma. Entrégame el código HTML y SCSS cumpliendo estas reglas estrictas:



1\. A prueba de Moodle: El usuario editará el texto en el editor de Moodle, el cual borra clases de etiquetas internas. Aplica metodología BEM solo en los contenedores padres y usa herencia pura para dar estilo a los <h3>, <p> e <img> internos.

2\. Escalabilidad con SCSS y Variables: El componente debe tener dos variantes de diseño (morado y verde). Usa Variables CSS (Custom Properties) dentro de clases modificadoras SCSS (ej. --theme-purple) para cambiar la paleta de colores sin tener que reescribir la estructura.

3\. Fondos Complejos: El fondo de la tarjeta está compuesto por un gradiente lineal y un patrón vectorial (SVG) superpuesto. Usa la propiedad background múltiple para apilarlos.

4\. Ajuste del Patrón: Para evitar que el SVG de fondo se estire e invada la zona de texto, no uses background-size: cover. En su lugar, usa auto 100% y ancla la imagen a la derecha."



* **Solución de la IA:** Se determinó usar la metodología BEM exclusivamente en los contenedores padres (`.nodolab-banner`, `.nodolab-banner\_\_content`) y aplicar selectores de herencia directa para los elementos internos (`.nodolab-banner\_\_content p`, `.nodolab-banner\_\_content h3`). Esto garantiza que si el usuario borra o reemplaza el texto en Moodle perdiendo las clases, el diseño base se mantendrá intacto.



### 2 Implementación de gradientes y patrones combinados



* **Problema:** Al inspeccionar Figma, detecté que el fondo no era sólido sino un gradiente lineal combinado con un patrón vectorial (ondas/figuras).
* **Prompt a la IA:** "¿Cómo puedo estructurar el SCSS para soportar un gradiente de fondo y un patrón SVG al mismo tiempo de manera escalable?"
* **Solución de la IA:** Sugirió implementar *Multiple Backgrounds* nativos en CSS combinados con Variables CSS (Custom Properties) dentro de los modificadores de BEM (`--theme-purple`, `--theme-teal`). Esto permitió apilar el patrón decorativo por encima del gradiente lineal en una sola propiedad limpia.

### 3 Ajuste de distorsión del fondo (Refinamiento manual guiado)



* **Problema:** El fondo decorativo se estiraba demasiado e invadía el área del texto al usar `background-size: cover`.
* **Interacción con la IA:** Solicitando asistencia para corregir la silueta invasiva, la IA recomendó cambiar el tamaño del background a `auto 100%` y alinearlo a la derecha (`right center`). Esto limitó el crecimiento horizontal de los vectores decorativos, logrando una fidelidad visual exacta con respecto al Figma.

## 

## Decisiones y ajustes manuales



* **Auditoría de capas en Figma:** Se aislaron manualmente las capas en Figma para exportar los elementos correctos (ilustraciones en PNG transparente y decoraciones de fondo en SVG), corrigiendo un error inicial donde se estaba exportando el marco completo de la tarjeta.
* **Compilación:** Se utilizó la extensión *Live Sass Compiler* en Visual Studio Code para procesar y minificar el archivo `style.css` final de manera automatizada.


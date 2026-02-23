# Documentación de Mejoras de Accesibilidad: Visor de Actividades

Esta actualización transforma una página puramente visual en una experiencia **inclusiva**, optimizada para usuarios de lectores de pantalla (SR), navegación por teclado y personas con deficiencias visuales.

## 1. Estructura y Semántica Global
*   **Definición de Meta-descripción:** Se añadió `<meta name="description">` para proporcionar contexto a los motores de búsqueda y herramientas de asistencia antes de que el usuario entre al sitio.
*   **Etiquetas Semánticas:** Se sustituyó el contenedor genérico `<div>` por la etiqueta `<main>` con el atributo `role="main"`. Esto permite a los navegadores y lectores de pantalla identificar rápidamente el núcleo del contenido.
*   **Uso de `min-height`:** En el CSS, se cambió `height: 100vh` por `min-height: 100vh` en el `body` para evitar que el contenido se corte en dispositivos pequeños o cuando el usuario aumenta el tamaño de la fuente.

## 2. Navegación y Acceso por Teclado
*   **Enlace de Salto (Skip Link):** Se implementó un enlace oculto visualmente (`.skip-link`) que solo aparece al usar la tecla *Tab*. Esto permite a los usuarios de teclado saltar directamente al contenido principal sin pasar por menús o elementos repetitivos.
*   **Indicadores de Enfoque (Focus Visible):** Se añadió la pseudo-clase `*:focus-visible` con un estilo de borde morado de alto contraste. Esto garantiza que cualquier usuario que navegue con el teclado sepa exactamente dónde se encuentra el foco en todo momento.

## 3. Optimización para Lectores de Pantalla (ARIA)
*   **Gestión de Emojis:** Los emojis (👋, ✨) se han envuelto en etiquetas `<span>` con `aria-hidden="true"`. Esto evita que el lector de pantalla interrumpa la lectura del texto con descripciones literales como "mano saludando", mejorando la fluidez del mensaje.
*   **Elementos Decorativos:** La lista de "burbujas" se marcó con `aria-hidden="true"` y `role="presentation"`. Al ser elementos puramente ornamentales, deben ser ignorados por las herramientas de asistencia para no generar ruido innecesario.
*   **Atributos ALT Vacíos:** En las imágenes de las burbujas, se eliminaron los textos alternativos genéricos (ej: "Burbuja 1") y se dejaron como `alt=""`. Un atributo alt vacío indica explícitamente al lector de pantalla que la imagen es decorativa.

## 4. Diseño Visual y Contraste
*   **Mejora de Contraste de Texto:** Se modificó el color de la etiqueta `<strong>` de un naranja claro (`#f39f18`) a uno más oscuro (`#c47500`). Este cambio asegura que el texto cumpla con el ratio de contraste **WCAG AA**, facilitando la lectura a personas con baja visión o daltonismo.
*   **Propiedad `will-change`:** Se optimizó el rendimiento de las animaciones de las burbujas en el CSS para reducir el esfuerzo del procesador, lo que ayuda a una navegación más fluida.

## 5. Accesibilidad en la Interactividad (JavaScript)
*   **Estado de Menús (Aria-Expanded):** En la función `toggleUnidad`, se añadió lógica para actualizar el atributo `aria-expanded`.
    *   Cuando el menú está abierto, se marca como `true`.
    *   Cuando está cerrado, como `false`.
    *   *Resultado:* El usuario de lector de pantalla recibe confirmación auditiva instantánea de si la sección se ha desplegado o no.
*   **Encapsulamiento del Código:** Se utilizó una función autoejecutable (IIFE) y el modo estricto (`'use strict'`) para evitar conflictos de variables y mejorar la estabilidad del script.

---

### Resumen de Cumplimiento
| Característica | Antes | Después | Beneficio |
| :--- | :--- | :--- | :--- |
| **Punto de entrada** | No definido | `<main>` | Navegación semántica rápida. |
| **Navegación Teclado** | Invisible | Enlace de salto + Focus visible | Autonomía para usuarios sin ratón. |
| **Contraste** | Bajo | Alto (Cumple AA) | Legibilidad mejorada. |
| **Imágenes** | "Burbuja 1" | Ocultas (aria-hidden) | Menos distracción auditiva. |
| **Interactividad** | Sin feedback | `aria-expanded` | Claridad en el estado del menú. |

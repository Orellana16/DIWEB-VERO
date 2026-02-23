# 📘 Documentación: Comparativa de Accesibilidad (WCAG 2.1)

## 🎯 Objetivo

El propósito de este proyecto es contrastar dos implementaciones web para validar el comportamiento de las herramientas de auditoría automática:

1. **Versión No Accesible:** Diseñada deliberadamente con barreras digitales para que herramientas como **WAVE** detecten errores críticos.
2. **Versión Accesible:** Implementada siguiendo las buenas prácticas de las **WCAG 2.1 (Nivel AA)**, logrando una navegación inclusiva y aprobando auditorías.

---

## ❌ 1. Versión NO Accesible (`no-accesible.html`)

Esta página ignora los estándares básicos, lo que genera una experiencia deficiente para usuarios con tecnologías asistivas.

### Problemas introducidos y su impacto

| Elemento | Fallo Técnico | Criterio WCAG | Impacto en WAVE |
| --- | --- | --- | --- |
| **Documento** | Ausencia de atributo `lang` en `<html>`. | 3.1.1 (Idioma) | **Error:** El lector no sabe qué síntesis de voz usar. |
| **Imágenes** | `<img src="...">` sin atributo `alt`. | 1.1.1 (Contenido no textual) | **Error:** El usuario no conoce el contenido de la imagen. |
| **Enlaces** | Links con iconos sin texto descriptivo. | 2.4.4 (Propósito del link) | **Error:** El lector anuncia "Link" sin destino. |
| **Formulario** | `<input>` sin etiqueta `<label>`. | 1.3.1 / 3.3.2 | **Error:** Campo huérfano de contexto. |
| **Botones** | `<button></button>` vacío. | 4.1.2 (Nombre/Rol) | **Error:** Botón sin función aparente. |
| **Iframe** | `<iframe>` sin atributo `title`. | 4.1.2 | **Error:** Falta de descripción del marco. |
| **Color** | Texto gris claro sobre fondo blanco. | 1.4.3 (Contraste) | **Alerta/Error:** Contraste < 4.5:1. |

---

## ✅ 2. Versión Accesible (`accesible.html`)

Esta versión aplica soluciones técnicas para garantizar que el contenido sea **perceptible, operable, comprensible y robusto**.

### Mejoras Aplicadas

* **Semántica Estructural:** Uso de *landmarks* HTML5 (`<header>`, `<nav>`, `<main>`, `<footer>`) para permitir el salto rápido entre secciones.
* **Skip Links:** Inclusión de un enlace "Saltar al contenido principal", visible solo al recibir el foco del teclado (WCAG 2.4.1).
* **Textos Alternativos:**
* *Informativas:* `alt="Descripción clara"`.
* *Decorativas:* `alt=""` y `aria-hidden="true"`.


* **Formularios Robustos:** Asociación explícita mediante `for` (en label) e `id` (en input), además de atributos `required` y `autocomplete`.
* **Foco Visible:** Estilos CSS mediante `:focus-visible` para que usuarios de teclado identifiquen su posición en la pantalla.
* **Contraste Óptimo:** Paleta de colores ajustada para cumplir con el ratio mínimo de **4.5:1** para texto normal.

---

## 🛠️ Metodología de Verificación

Para comprobar los resultados, sigue estos pasos:

1. **Carga local:** Abre ambos archivos en tu navegador (Chrome o Firefox preferiblemente).
2. **Auditoría con WAVE:**
* Activa la extensión **WAVE** en la página `no-accesible.html` y observa los indicadores rojos (errores).
* Repite el proceso en `accesible.html`; deberías obtener un reporte limpio de errores.


3. **Prueba manual:** * Intenta navegar usando solo la tecla `Tab`.
* Usa un lector de pantalla (NVDA en Windows o VoiceOver en macOS) para comparar la lectura de ambos archivos.



---

> **Nota:** La accesibilidad no termina con pasar un test automático (como WAVE), pero es el primer paso esencial para una web profesional.

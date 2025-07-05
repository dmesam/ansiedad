# Instrucciones para la Creación de Nuevas Presentaciones y Páginas

Este sitio es una **presentación interactiva** orientada a jóvenes, implementada como una **Single Page App (SPA)**. Utiliza una paleta de colores juvenil y moderna, Material Design y puede emplear Vue.js en modo no compilado (CDN). Estas son las instrucciones y buenas prácticas para futuros desarrollos y agentes de AI:

---

## 1. Enfoque General
- **SPA:** Toda la navegación y el contenido deben gestionarse en una sola página HTML, usando rutas virtuales o componentes dinámicos.
- **Framework:** Se recomienda usar [Vue.js](https://unpkg.com/vue@3/dist/vue.global.js) en modo CDN (no compilado) para componentes y reactividad.
- **Estilos:** Utilizar la hoja de estilos de [Material Design](https://m3.material.io/foundations) y la paleta de colores definida abajo.
- **Accesibilidad:** Asegurar contraste, navegación con teclado y etiquetas semánticas.

## 2. Paleta de Colores Juvenil
Usar estas variables CSS en `:root`:

```css
:root {
    --md-primary: #7C3AED; /* Violeta vibrante */
    --md-primary-container: #EDE9FE; /* Violeta claro */
    --md-on-primary: #FFFFFF;
    --md-on-primary-container: #4C1D95;
    --md-secondary: #06B6D4; /* Cian/sky */
    --md-secondary-container: #CFFAFE;
    --md-on-secondary: #0E7490;
    --md-on-secondary-container: #164E63;
    --md-tertiary: #F59E42; /* Naranja/ámbar */
    --md-tertiary-container: #FEF3C7;
    --md-on-tertiary: #B45309;
    --md-on-tertiary-container: #78350F;
    --md-success: #10B981; /* Verde esmeralda */
    --md-error: #F43F5E; /* Rosa/rojo moderno */
    --md-error-container: #FEE2E2;
    --md-on-error: #B91C1C;
    --md-on-error-container: #7F1D1D;
    --md-background: #F8FAFC; /* Muy claro */
    --md-surface: #FFFFFF;
    --md-surface-variant: #E0E7EF;
    --md-on-background: #22223B;
    --md-on-surface: #22223B;
    --md-on-surface-variant: #64748B;
    --md-outline: #A5B4FC;
    --md-outline-variant: #C7D2FE;
    --md-shadow: #000000;
    --md-scrim: #000000;
    --md-inverse-surface: #312E81;
    --md-inverse-on-surface: #F8FAFC;
    --md-inverse-primary: #C7D2FE;
    --md-surface-dim: #E0E7EF;
    --md-surface-bright: #FFFFFF;
    --md-surface-container-lowest: #FFFFFF;
    --md-surface-container-low: #F1F5F9;
    --md-surface-container: #F3F4F6;
    --md-surface-container-high: #E5E7EB;
    --md-surface-container-highest: #E0E7EF;
}
```

## 3. Estructura de Carpetas Recomendada

```
/
├── index.html           # Entrada principal (SPA)
├── assets/
│   ├── img/             # Imágenes y memes
│   ├── icons/           # Iconos personalizados
│   └── ...
├── css/
│   └── material.css     # Hoja de estilos Material Design + custom
├── js/
│   └── app.js           # Lógica Vue.js y scripts
├── INSTRUCCIONES_PRESENTACIONES.md
└── ...
```

## 4. Buenas Prácticas
- **Componentes:** Divide el contenido en componentes Vue reutilizables (ej: HeroVersiculo, MenuNavegacion, TarjetaHerramienta, etc).
- **Rutas:** Usa Vue Router (modo hash o history) o una solución simple para navegación SPA.
- **Responsivo:** Usa flexbox y grid para layouts adaptables a móvil y desktop.
- **Material Icons y Font Awesome:** Usa iconos por CDN.
- **Accesibilidad:** Usa roles, aria-labels y contraste suficiente.
- **Contenido:** Mantén el contenido en español, claro y adaptado a jóvenes.
- **Animaciones:** Usa transiciones suaves para navegación y modales.
- **No compilar:** No uses build tools, todo debe funcionar directo en el navegador.

## 5. Ejemplo de Inclusión de Vue.js y Material Design

```html
<!-- En el <head> de index.html -->
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
<link rel="stylesheet" href="css/material.css">
```

## 6. Ejemplo de Componente Hero con Versículo

```html
<div id="app">
  <hero-versiculo></hero-versiculo>
  <main-content></main-content>
</div>

<script>
const app = Vue.createApp({});
app.component('hero-versiculo', {
  template: `
    <section class='hero-versiculo'>
      <blockquote>
        <span>Por nada estéis afanosos...<br>Filipenses 4:6-7</span>
      </blockquote>
      <button @click="$emit('scroll')">
        <i class='fas fa-chevron-down'></i>
      </button>
    </section>
  `
});
app.mount('#app');
</script>
```

---

## 7. Al crear nuevas páginas o presentaciones:
- **Agrega nuevas secciones/componentes** en el SPA, no archivos HTML independientes.
- **Usa la paleta y estilos definidos.**
- **Mantén la navegación y el menú consistente.**
- **Documenta cada nuevo componente o sección en este archivo.**

---

**¡Sigue estas pautas para mantener la coherencia, modernidad y accesibilidad en futuras presentaciones!** 
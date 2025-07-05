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

## 8. Manejo del Menú de Navegación

- **Menú persistente:** El menú de navegación debe ser un componente fijo y visible en toda la SPA, ya sea como barra lateral (desktop) o barra inferior/horizontal (móvil).
- **Consistencia:** El menú debe contener enlaces a todas las secciones principales (ej: Síntomas, Introducción, Checklist, Resultados, Juego, Herramientas, QR, etc.) y debe mantenerse actualizado cuando se agreguen nuevas secciones.
- **Iconografía:** Utiliza iconos de Font Awesome o Material Icons para cada ítem, acompañados de texto breve y legible.
- **Accesibilidad:** Usa roles de navegación (`<nav>`), aria-labels y estados activos claros.
- **Responsivo:** Cambia de barra lateral a barra inferior/horizontal en pantallas pequeñas.
- **Estado activo:** Resalta la sección actual usando una clase o variable reactiva de Vue.
- **No recargar:** La navegación debe ser interna (SPA), nunca recargar la página.

### Ejemplo de Componente Vue para Menú

```html
<template>
  <nav class="rail-menu" role="navigation" aria-label="Menú principal">
    <a v-for="item in menu" :key="item.route" :href="item.route" class="rail-item" :class="{active: isActive(item.route)}" @click.prevent="navigate(item.route)" :title="item.title">
      <i :class="item.icon"></i>
      <span>{{ item.text }}</span>
    </a>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      menu: [
        { route: '#/sintomas', icon: 'fas fa-user-md', text: 'Síntomas', title: 'Síntomas' },
        { route: '#/introduccion', icon: 'fas fa-lightbulb', text: 'Intro', title: 'Introducción' },
        { route: '#/checklist', icon: 'fas fa-clipboard-list', text: 'Checklist', title: 'Checklist detonantes' },
        { route: '#/resultados', icon: 'fas fa-database', text: 'Resultados', title: 'Resultados checklist' },
        { route: '#/juego', icon: 'fas fa-gamepad', text: 'Juego', title: 'Juego' },
        { route: '#/herramientas', icon: 'fas fa-tools', text: 'Herramientas', title: 'Herramientas' },
        { route: '#/qr', icon: 'fas fa-qrcode', text: 'QR', title: 'QR Code' }
      ]
    }
  },
  methods: {
    isActive(route) {
      return window.location.hash === route;
    },
    navigate(route) {
      window.location.hash = route;
    }
  }
}
</script>
```

- **Actualiza el menú** cada vez que agregues una nueva sección.
- **Mantén el menú como componente global** para que esté presente en toda la SPA.
- **Adapta el CSS** para el menú según el diseño Material Design y la paleta de colores definida.

---

## 9. Componente Principal para Menú y Layout

- **Layout global:** Crea un componente principal (por ejemplo, `App.vue`, `MainLayout.vue` o `LayoutPrincipal.vue`) que contenga el menú de navegación y el layout general de la SPA.
- **No repetir menú:** Nunca repitas el menú en cada página o componente. El menú debe estar en el layout global y el contenido de cada sección debe renderizarse dinámicamente dentro de un `<router-view>` o `<component :is="currentView">`.
- **Composición:** Usa slots o áreas designadas para insertar el contenido de cada sección/página.
- **Ventajas:** Esto asegura consistencia visual, facilita el mantenimiento y evita errores de duplicación.

### Ejemplo de Estructura Vue SPA

```html
<div id="app">
  <main-layout>
    <router-view></router-view>
  </main-layout>
</div>
```

```html
<!-- MainLayout.vue -->
<template>
  <nav-menu />
  <main>
    <slot /> <!-- Aquí se renderiza el contenido de cada sección -->
  </main>
</template>
```

- **Actualiza solo el layout global** para cambios de menú, estilos o estructura general.
- **Cada nueva sección** debe ser un componente hijo que se muestra dentro del layout, nunca una página HTML independiente.

---

**¡Sigue estas pautas para mantener la coherencia, modernidad y accesibilidad en futuras presentaciones!** 
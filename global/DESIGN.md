# DESIGN.md — Sistema de diseño

> [ADAPTAR: una línea con la dirección visual del proyecto].
>
> Este archivo describe el **sistema canónico**: tokens, lenguaje visual y patrones aprobados. NO recoge lecciones aprendidas durante el trabajo — eso vive en `feedback_diseno_*.md` (memoria persistente).

> **Recordatorio técnico**: Claude Code no carga `DESIGN.md` automáticamente. Referénciarlo desde `AGENTS.md` con `@DESIGN.md` o con un puntero explícito ("para temas de diseño visual, lee `DESIGN.md`").

---

## Dirección visual

[ADAPTAR: 1-3 líneas. Qué referencia mental, qué espíritu. Ejemplo: "Sello editorial. Filetes, mastheads, numeración tipográfica. NO minimalismo silicon valley."]

---

## Tokens base

> No tocar sin justificación. Si hay que cambiarlos, discute por qué antes.

### Color

- Fondo: [ADAPTAR: ej. `#f7f3ed`]
- Texto: [ADAPTAR: ej. `#141210`]
- Acento: [ADAPTAR: ej. `#2d6a4f`]
- Muted: [ADAPTAR]
- Bordes: [ADAPTAR]

### Tipografía

- Familia: [ADAPTAR: ej. Suisse Intl]
- Pesos disponibles: [ADAPTAR: ej. book 400, italic 400, bold 700]
- Escala: [ADAPTAR: tamaños canónicos de body / títulos / micro]

### Espaciado y radios

[ADAPTAR: escala de spacing si la tienes, valores canónicos de border-radius, etc.]

---

## Lenguaje visual

[ADAPTAR: patrones específicos del proyecto que dan identidad. Ejemplos:]

<!--
- Asteriscos `* * *` (dinkus) como separador, no `<hr>`.
- Etiquetas tipo meta en MAYÚSCULAS con letter-spacing 0.12-0.16em, peso 700, tamaño 0.7-0.78rem.
- Botones rectangulares (border-radius 0), texto MAYÚSCULAS, sin sombra.
- Tarjetas con sombra dura tipo "stamp": `box-shadow: 6px 6px 0 var(--ink)`.
-->

---

## Componentes y patrones

[ADAPTAR: piezas reutilizables con sus reglas. Una sub-sección por componente. Ejemplo:]

<!--
### Navbar
- Estructura: marca a la izquierda + acciones a la derecha.
- Padding desktop: 18px 28px 14px. Móvil: 14px 16px 10px.
- Borde inferior 1px en `--line`. NO fixed.

### Tarjetas numeradas
- Numeración `01`, `02`, `03` en `2.2rem` peso 700 color accent.
- Hover desplaza 4px a la derecha (micro-interacción).
- Eyebrow uppercase 0.66rem letter-spacing 0.18em color muted.
-->

---

## Responsive

[ADAPTAR: reglas por breakpoint. Ejemplo:]

<!--
### ≤720px (móvil)
- Tap targets mínimo 40×40.
- Hover desactivado en `(hover: none)`.
- Navbar: marca a 0.85rem, lupa 40×40.
- Banda superior: altura 36px (vs 44px desktop).
-->

---

## Lo que NO funciona *(opcional)*

Decisiones validadas como malas. No revivir sin justificación nueva.

<!--
- Sidebar fija permanente robando protagonismo al contenido.
- Chips horizontales con scroll-x para filtros.
- Hover anclado al cursor (salta nerviosa).
- Caja negra "EMAIL DEL DÍA" pegada a la izquierda — se ve como mancha, no editorial.
-->

---

## Cuándo este archivo miente

Las plantillas envejecen. Si lo que ves en el código contradice este archivo:

1. Confía en el código actual, no en este archivo.
2. Avisa al usuario antes de actuar.
3. Si la discrepancia es importante, actualiza esta sección en el mismo commit que el cambio de código.

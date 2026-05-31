# Memoria persistente

Índice de hechos aprendidos sobre este proyecto. El agente lo lee al arrancar y lo actualiza durante el trabajo. El detalle de cada entrada vive en su propio archivo `.md`.

> Esta plantilla asume que el agente ya conoce el sistema de memoria (tipos, frontmatter YAML, patrón `Why:` / `How to apply:`) desde su configuración global. Aquí solo se definen el índice y las convenciones locales.

## Convenciones del índice

- **Negrita** en una entrada = leer primero al arrancar.
- Formato de cada entrada: `[archivo](archivo.md) — qué contiene en una línea. Leer si: <situación que dispara su relevancia>.`
- En `project_*` que reflejen estados con fecha, incluir `YYYY-MM-DD` al inicio de la descripción.
- **Poda**: cada ~mes revisar el Activo y mover a Archivo lo superado. Mantener el índice escaneable en una pasada.

---

## Activo

### user

<!-- Quién es el usuario, cómo prefiere colaborar, qué sabe y qué no. Ejemplo:
- [user_perfil.md](user_perfil.md) — rol, contexto, idiomas, nivel técnico. Leer si: arrancar sesión nueva.
-->

### project

<!-- Estado, decisiones tomadas, frentes en curso, deadlines, motivaciones de cambios. Ejemplo:
- **[project_lanzamiento_2026_05_10.md](project_lanzamiento_2026_05_10.md) — 2026-05-10 sistema en producción, 22 altas el primer día. Leer si: tocas pagos, webhooks o flujo de alta.**
-->

### feedback

<!-- Reglas aprendidas, qué funciona, qué no, lecciones de errores pasados. Ejemplo:
- [feedback_no_mockear_db.md](feedback_no_mockear_db.md) — tests de integración con DB real, nunca mocks. Leer si: escribes o modificas tests.
-->

### reference

<!-- URLs, infra, credenciales (referencia, no valores), recursos externos. Ejemplo:
- [reference_urls_y_credenciales.md](reference_urls_y_credenciales.md) — Vercel, Supabase, dominios, dónde vive cada cosa. Leer si: necesitas acceder a un servicio externo.
-->

---

## Archivo

Entradas superadas. Conservadas por contexto histórico, no relevantes para el trabajo actual.

> Cuando una entrada del Activo deje de aplicar, **muévela aquí en lugar de borrarla**. El archivo `.md` se conserva en disco; el índice deja de listarla en Activo.

<!-- Ejemplo:
- [project_estado_2026_05_08.md](project_estado_2026_05_08.md) — snapshot anterior al lanzamiento. Superado por [project_lanzamiento_2026_05_10.md](project_lanzamiento_2026_05_10.md).
-->

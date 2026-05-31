# arnés-agentes

Kit mínimo de plantillas para configurar agentes de IA (Claude Code, Gemini, Codex, Cursor) de forma coherente en todos tus proyectos.

Un arnés sencillo que sujeta a cualquier agente a tu identidad, tu forma de trabajar y el contexto del proyecto — sin tener que reescribirlo cada vez.

## Qué contiene

Las plantillas viven en [`global/`](global/):

| Archivo | Para qué sirve | Dónde vive una vez pegado |
|---|---|---|
| [`CLAUDE.md`](global/CLAUDE.md) | **Contexto global del usuario.** Quién eres, cómo trabajas, principios de código, reglas de secretos. Una sola vez por máquina. | `~/.claude/CLAUDE.md` |
| [`AGENTS.md`](global/AGENTS.md) | **Contexto estable del proyecto.** Stack, comandos, mapa del repo, convenciones, reglas duras. Una copia por proyecto. | Raíz del proyecto |
| [`MEMORY.md`](global/MEMORY.md) | **Índice de memoria viva.** Apunta a archivos `feedback_*` / `project_*` / `reference_*` con cosas aprendidas durante el trabajo. Opcional. | Raíz del proyecto |
| [`DESIGN.md`](global/DESIGN.md) | **Sistema de diseño del proyecto.** Tokens, lenguaje visual, componentes. Opcional, recomendable si el proyecto tiene UI con sistema propio. | Raíz del proyecto |

## Filosofía

- **Mapa, no biblia.** Las plantillas son índices navegables, no manuales para leer de cabo a rabo.
- **Multi-agente por defecto.** Las plantillas están pensadas para que un solo archivo sirva a cualquier agente (Claude, Gemini, Codex, Cursor). La sección "Cómo usar" explica cómo enlazarlo para cada uno.
- **Sin scaffolding obligatorio.** Sin scripts, sin JSONs, sin estructura de carpetas forzada. Pegar y rellenar.
- **No duplicar el global.** Cada plantilla asume lo que ya saben los agentes desde el global y solo añade lo específico de su capa.
- **Cuándo este archivo miente.** Las plantillas envejecen. Cada una incluye una pauta para que el agente verifique contra el código y avise si hay discrepancias.

## Cómo usar

### 1. Contexto global (una sola vez por máquina)

```bash
mkdir -p ~/.claude
cp global/CLAUDE.md ~/.claude/CLAUDE.md
```

Rellena los `[ADAPTAR: …]` con tu identidad, idioma, nivel técnico y guías de estilo externas si las tienes.

Para que **Gemini** comparta el mismo global:

```bash
mkdir -p ~/.gemini
ln -s ~/.claude/CLAUDE.md ~/.gemini/GEMINI.md
```

Un solo archivo fuente, varios agentes leyendo lo mismo. Sin riesgo de divergencia.

### 2. Por cada proyecto nuevo

Tres modos según los agentes que vayas a usar en ese proyecto:

**Modo A — Solo Claude Code:**

```bash
cp /ruta/al/repo/global/AGENTS.md ./CLAUDE.md
```

Renombras la plantilla a `CLAUDE.md` directamente. Claude Code la auto-carga.

**Modo B — Multi-agente (Claude + Gemini + Codex + Cursor):**

```bash
cp /ruta/al/repo/global/AGENTS.md ./AGENTS.md
ln -s AGENTS.md CLAUDE.md   # Claude Code
ln -s AGENTS.md GEMINI.md   # Gemini (Antigravity, VS Code)
```

`AGENTS.md` canónico, symlinks para los demás agentes.

**Modo C — Patrón oficial Anthropic con import:**

```bash
cp /ruta/al/repo/global/AGENTS.md ./AGENTS.md
echo "@AGENTS.md" > CLAUDE.md
```

`CLAUDE.md` es un archivo de una sola línea que importa `AGENTS.md` con la sintaxis oficial. Equivalente al symlink pero más explícito.

Rellena los `[ADAPTAR: …]` del `AGENTS.md` con la información real del proyecto.

### 3. Memoria persistente (opcional)

Si quieres mantener un índice manual de cosas aprendidas durante el trabajo:

```bash
cp /ruta/al/repo/global/MEMORY.md ./MEMORY.md
```

A partir de ahí, el agente crea archivos `feedback_*.md` / `project_*.md` / `reference_*.md` según haga falta y los indexa en `MEMORY.md`.

Para tener el formato exacto de cada tipo de archivo a mano, hay esqueletos en [`global/memory-templates/`](global/memory-templates/) — uno por tipo (`user`, `feedback`, `project`, `reference`) con frontmatter YAML y patrón `Why:` / `How to apply:` listos para rellenar.

> Nota: Claude Code tiene además un sistema oficial de "auto-memory" en `~/.claude/projects/<proyecto>/memory/` que gestiona el propio agente. Coexiste con `MEMORY.md` sin conflicto.

### 4. Sistema de diseño (opcional)

Si el proyecto tiene UI con sistema propio (tokens, tipografía, componentes):

```bash
cp /ruta/al/repo/global/DESIGN.md ./DESIGN.md
```

Y referénciarlo desde `AGENTS.md` para que el agente lo lea cuando toque diseño:

```markdown
# AGENTS.md
…
## Diseño
Para temas visuales, lee [DESIGN.md](DESIGN.md) — sistema canónico de tokens, lenguaje y componentes.
```

O, alternativamente, importarlo con `@DESIGN.md` en alguna sección del `AGENTS.md`.

## Convenciones internas

- `[ADAPTAR: …]` marca un hueco que tienes que rellenar al pegar la plantilla.
- Las secciones marcadas como **opcional** se borran si no aplican.
- En `MEMORY.md`, las entradas en **negrita** son las que el agente debe leer al arrancar.
- En `MEMORY.md`, las entradas obsoletas se mueven a la sección "Archivo" en lugar de borrarse.
- Política de poda: revisar `MEMORY.md` ~una vez al mes y mover lo superado al Archivo.
- En `DESIGN.md`, los comentarios HTML (`<!-- … -->`) traen ejemplos del estilo. Se borran al rellenar.

## Cadena de mando

Si un `AGENTS.md` de proyecto contradice tu `CLAUDE.md` global, manda el de proyecto. El global da contexto por defecto; el proyecto define excepciones específicas.

## Licencia

MIT

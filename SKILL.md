---
name: web-premium-by-dynexo
description: >
  Skill madre de diseño web premium para clientes de Dynexo. Orquesta en un
  solo flujo: Impeccable (workflow + 23 comandos + anti-patrones),
  frontend-design de Anthropic (dirección visual y gusto), el stack/proceso de
  Dynexo (Next.js + Tailwind + Framer Motion + GSAP + Lenis), Ant Design v6
  (sistema de componentes y spec para UI densa: dashboards, paneles, admin) y
  System Design Primer (arquitectura detrás de la UI: cache, CDN, DB, colas).
  Usar SIEMPRE que Bauti pida una web, landing, sección, componente, página,
  dashboard, panel admin o cualquier interfaz visual, y cuando mencione
  "diseño", "rediseño", "animación", "hero", "layout", "tipografía", "paleta",
  "dirección visual", "critique", "audit", "polish" o pida referencias/opciones
  antes de codear. Estándar: Awwwards-level. Reemplaza a dynexo-web-design como
  punto de entrada único. No usar para backend puro ni tareas sin UI.
user-invocable: true
argument-hint: "[brief|direcciones|build|critique|audit|polish|animate|... ] [target]"
---

# Web Premium — skill madre (Impeccable + frontend-design + Dynexo + Ant Design + System Design)

Sos design director con criterio out-of-distribution: cada sitio que sale
podría entrar a Awwwards SOTD y tener una identidad visual que **solo** podría
pertenecer a ese cliente. Nada de output genérico de IA, nada de template de
Webflow. Vas all-out, con POV claro, código production-grade y craft real.

Esta skill **no reemplaza** el juicio de las fuentes: las ejecuta a todas
en el momento correcto del pipeline. Todo lo que dice cada una se aplica.

---

## Las fuentes y cuándo entra cada una

| Fuente | Qué aporta | Cuándo se aplica |
|---|---|---|
| **frontend-design** (Anthropic) | Gusto y dirección: hero como tesis, tipografía con personalidad, estructura que informa, motion deliberado, copy como material de diseño, auto-crítica | Fase 1 (dirección) y Fase 2 (build), siempre de fondo |
| **Impeccable** | Motor de workflow: 4 modos, 23 comandos, quality floor (craft-floor), detector de anti-patrones, iteración con screenshots | Fase 0→3, es el esqueleto del proceso |
| **Dynexo** | Stack concreto y ritual de entrega: Next.js App Router + Tailwind + Framer + GSAP + Lenis, 2–3 direcciones antes de codear, checklist final | Fase 1 (direcciones) y Fase 2 (build/entrega) |
| **Ant Design v6** (Ant Group) | Design system enterprise: 70+ componentes React (tablas, forms, date pickers, drawers, steps), spec de patrones para UI densa (data-entry, data-list, detail-page, feedback, navegación, visualización) y tokens seed→map→alias con algoritmos default/dark/compact | Modo **Operate** (dashboards, paneles admin, back-office, turneros, CRMs de cliente). Nunca como look de una landing |
| **System Design Primer** (donnemartin) | Arquitectura detrás de la UI: CDN, capas de cache, SQL vs NoSQL, réplicas, colas/async, consistencia vs disponibilidad, cuentas de servilleta, latencias | Fase 0 cuando el proyecto tiene datos/backend (tienda, reservas, turnos, app); Fase 3 en `audit`/`optimize` de performance |
| **HyperFrames** (HeyGen) | Video/motion desde HTML → MP4 determinista: promo del sitio, motion graphics del hero, deck, social clips. `frame.md` = design system invertido para la cámara | Fase 4 (opcional): cuando el cliente pide video/promo/motion además de la web |

**Fuentes en disco** (leer para el detalle profundo cuando haga falta):
- Impeccable refs por comando: `C:\Users\bauti\repos\impeccable\.claude\skills\impeccable\reference\<comando>.md`
- Impeccable SKILL completo: `C:\Users\bauti\repos\impeccable\.claude\skills\impeccable\SKILL.md`
- frontend-design: `C:\Users\bauti\repos\anthropic-skills\skills\frontend-design\SKILL.md`
- Ant Design (clone sparse dentro de la skill, v6): `C:\Users\bauti\.claude\skills\web-premium-by-dynexo\ant-design\`
  - `DESIGN.md` — el lenguaje visual completo en formato google-labs design.md (tokens YAML + el porqué). Leer primero.
  - `docs/spec/<patrón>.en-US.md` — spec de patrones (ver bloque Ant Design abajo).
  - `docs/react/customize-theme.en-US.md` · `use-with-next.en-US.md` · `compatible-style.en-US.md` (Tailwind/`@layer`) · `server-side-rendering.en-US.md`.
  - `components/<comp>/index.en-US.md` (API) + `components/<comp>/demo/*.tsx` (demos listas) · `components/theme/` (tokens e interfaces).
- System Design Primer (clone sparse dentro de la skill): `C:\Users\bauti\.claude\skills\web-premium-by-dynexo\system-design-primer\README.md` (todo el contenido; buscar por `## <tema>`) + casos resueltos en `solutions/system_design/<caso>/README.md` (`scaling_aws` = escalar de 1 usuario a millones paso a paso; `query_cache`, `pastebin`, `twitter`, `mint`…).
- Video/motion: skill **`videos-by-dynexo`** (`C:\Users\bauti\.claude\skills\videos-by-dynexo\SKILL.md`) — capa Dynexo sobre HyperFrames (recetas, marca, formatos, export). Trae el clone de HyperFrames en `videos-by-dynexo\hyperframes\skills\` (router `/hyperframes` + workflows + domain skills). CLI: `npx hyperframes init|preview|render`. Requiere Node 22+ y FFmpeg.
- Actualizar los clones sparse (ant-design y system-design-primer, rama `master`): `git fetch --depth 1 origin master` + `git reset --hard origin/master` dentro de cada carpeta. El filtro de archivos vive en `.git/info/sparse-checkout`.
- Si el plugin `impeccable` está instalado, los comandos `/impeccable <cmd>` corren la versión con detector determinístico + modo browser en vivo. Si no, usá los `reference/*.md` de arriba: la guía es la misma.

---

## Modo del surface (de Impeccable) — decidir primero

El modo define cómo se ve el éxito para el visitante. Se elige por el surface
pedido, no por el producto.

- **Persuade** — el visitante decide y actúa. Landings, marketing, pricing. El diseño ES el producto.
- **Operate** — el visitante completa una tarea. App UI, dashboards, settings. Manda escaneabilidad y consistencia. → Base de componentes: **Ant Design** tematizado (ver bloque abajo).
- **Read** — el visitante entiende algo. Docs, artículos, guías. Estructura para comprensión.
- **Experience** — el visitante está dentro de la obra. Portfolios, showcases. La interfaz se corre del medio.

---

## Pipeline obligatorio

### Fase 0 — Contexto (Impeccable `init` + brief Dynexo + "ground it" de frontend-design)
Antes de nada, fijar: **industria/rubro, audiencia, objetivo único de la página,
palabras emocionales, restricciones** (colores de marca, assets). Si el brief no
define el sujeto, definilo vos y declará la elección — el mundo del sujeto (sus
materiales, artefactos, vernáculo) es de donde salen las decisiones distintivas.
Si Bauti ya dio contexto suficiente, extraerlo sin re-preguntar.

Si detrás de la UI hay datos (tienda, reservas, turnos, panel, app), sumar el
**mini-ritual de System Design Primer** antes de diseñar pantallas: casos de uso
y restricciones → diseño de alto nivel → componentes core → qué escala. Ver el
bloque "Arquitectura" abajo.
> Deep dive: `reference/init.md`, `reference/shape.md`, `reference/new-work.md`.

### Fase 1 — Direcciones visuales (Dynexo ritual + frontend-design token system) · NUNCA ir directo al código
Presentar **2–3 direcciones genuinamente distintas** (no variaciones del mismo
tono). Cada una:

```
DIRECCIÓN [N]: [Nombre evocador — "Void Editorial", "Obsidian Flow"]
──────────────────────────────────────────────
Concepto:        Una frase que captura la esencia visual
Paleta:          4–6 hex con nombre (#0A0A0A, #F2F2F0, #C8FF00…)
Tipografía:      Display / Body / Mono (con intención, nunca defaults)
Layout:          Estructura + ritmo de la página (prosa + wireframe ASCII)
Animaciones:     Qué efectos específicos y dónde
Signature:       El detalle único que hace memorable ESTE sitio
```

Antes de mostrarlas, pasá cada dirección por el filtro de frontend-design:
si alguna parte se parece al default genérico que producirías para cualquier
brief similar → revisala y decí qué cambiaste y por qué. Evitá los 3 clusters
de IA: (1) fondo cream + serif alto contraste + terracota; (2) casi-negro con
un solo acento acid-green/vermilion; (3) broadsheet con reglas hairline y radius
cero. Son opciones válidas solo si el brief los pide explícitamente.
> Deep dive: `reference/critique.md` para validar antes de codear.

### Fase 2 — Build (Dynexo stack + frontend-design principios + Impeccable craft-floor)
Solo después de que Bauti elija dirección. Antes de tocar UI, cargar el
**quality floor** de Impeccable (`reference/craft-floor.md`): la barra, los bans
absolutos y los reflejos que ningún detector agarra.

Principios de frontend-design vigentes durante todo el build:
- **Hero = tesis.** Abrí con lo más característico del mundo del sujeto.
- **Tipografía = personalidad.** Pareá display + body con intención; escala clara, pesos/anchos/tracking deliberados.
- **Estructura = información.** Numeración/eyebrows/dividers solo si codifican algo real (una secuencia de verdad), no decoración.
- **Motion deliberado.** Un momento orquestado pega más fuerte que efectos dispersos. A veces menos es más.
- **Complejidad = visión.** Maximalista pide ejecución elaborada; minimalista pide precisión en spacing/tipo/detalle.
- **Gastá la audacia en un solo lugar** (el signature). Todo lo demás, quieto y disciplinado. Sacá un accesorio antes de salir (Chanel).
- **Copy = material de diseño.** Voz activa, sentence case, nombrá las cosas por lo que la persona controla. Errores que explican qué pasó y cómo arreglarlo. Empty states que invitan a actuar.

Stack Dynexo (detalle completo en el bloque de abajo): Next.js App Router + TS,
Tailwind + tokens CSS en `globals.css`, Framer Motion (microinteracciones),
GSAP+ScrollTrigger (scroll cinematográfico), Lenis (smooth scroll en root),
Three.js solo cuando aporte valor premium real. En surfaces **Operate**, Ant
Design v6 tematizado con los tokens de la dirección elegida (bloque abajo).

Iterá con screenshots / preview hasta llegar a la barra (una imagen vale 1000
tokens). Cuidá la especificidad de selectores CSS (`.section` vs `.cta` se
cancelan seguido en paddings/margins).

### Fase 3 — Crítica y cierre (Impeccable critique/audit/polish + checklist Dynexo)
Antes de entregar, pasar por:
- `critique` — review UX: jerarquía, claridad, resonancia emocional.
- `audit` — a11y, performance, responsive.
- `polish` — pasada final y alineación al sistema de diseño.
> Deep dives: `reference/critique.md`, `reference/audit.md`, `reference/polish.md`.
> Comandos enhance/refine on-demand: `bolder`, `quieter`, `distill`, `harden`,
> `onboard`, `animate`, `colorize`, `typeset`, `layout`, `delight`, `overdrive`,
> `clarify`, `adapt`, `optimize` → cada uno tiene su `reference/<cmd>.md`.

### Fase 4 — Video / motion del sitio (HyperFrames · opcional)
Activar **solo** si el cliente pide video/promo/motion además de la web. HyperFrames
(HeyGen) rinde HTML → MP4 determinista, reusando el mismo diseño y stack de motion
(GSAP/CSS/Lottie/Three.js) que ya usa la web.

- **Cargar la skill `videos-by-dynexo`**: orquesta HyperFrames con recetas, marca, formatos y export de Dynexo, y desde ahí invoca `/hyperframes`.
- Recetas típicas para clientes: `promo-cliente` (promo/launch del sitio, 16:9 + 9:16), `hero-loop` (video de fondo del hero; antes evaluar si va en código), `sting` (logo animado), `deck` (propuesta navegable).
- **`frame.md`** = traducir el `DESIGN.md`/tokens del sitio a specs de cámara (mismos átomos, reescalados para el frame). Puente diseño→video. Coherencia obligatoria: misma paleta, tipografía y signature que la web.

---

## Stack técnico (Dynexo) — referencia de implementación

**Framework:** Next.js App Router siempre, TS por defecto, reutilizables en `components/ui/`.

**Estilos:** Tailwind + custom properties CSS para tokens en `globals.css`. Nunca hardcodear colores en clases; usar variables.
```css
:root {
  --color-bg: #080808; --color-surface: #111111;
  --color-accent: #C8FF00; --color-text: #F0F0F0; --color-muted: #666666;
}
```

**Animaciones — jerarquía:** Framer Motion (microinteracciones, entradas, page transitions, hover, stagger) · GSAP+ScrollTrigger (parallax, pin, text reveals, timelines) · CSS nativo (transitions simples, loops ambientales) · Lenis (smooth scroll, init en root layout) · Three.js/WebGL (solo hero 3D / fondos de alto impacto, lazy load obligatorio).

**Fuentes:** `next/font` o Google Fonts. Display: Bebas Neue, Druk, Anton, Oswald Black. Serif: Playfair, Cormorant, Editorial New, DM Serif. Sans premium: PP Neue Montreal (alt DM Sans/Outfit), Satoshi (alt Plus Jakarta), Neue Haas (alt Figtree/Manrope). **Nunca:** Inter principal, Roboto, Open Sans, Lato.

**Color:** sin paleta default. Background oscuro base (#080808/#0A0A0F/#0D0D0D) + 1 acento (acid #C8FF00 · cálido #FF6B35 · frío #00D4FF · gold #FFD700). Nunca purple→pink genérico.

**Reglas no negociables:** letter-spacing negativo (-0.02 a -0.04em) y line-height 0.9–1.1 en displays; mucho aire; asimetría intencional; layouts que rompen el contenedor; max-width 1440px con elementos full-bleed; borders sutiles rgba(255,255,255,0.08); glassmorphism con moderación; noise texture; gradientes radiales atmosféricos; texto con gradient clip.

**Performance:** `next/image` con `sizes`+`priority`; `next/font` display swap; `will-change` solo mientras anima; GSAP import selectivo; **respetar `prefers-reduced-motion` siempre**; target Lighthouse 85+.

**Responsive:** breakpoints Tailwind; tipografía `clamp()` (hero `clamp(2.5rem,6vw,8rem)`); en mobile simplificar GSAP, mantener Framer para microinteracciones, apagar Three.js si pesa.

---

## Ant Design — cuando el surface es Operate

Dashboards, paneles admin, back-office, turneros, CRMs, gestión de stock o
reservas del lado del cliente: no reinventar tablas, forms, date pickers ni
drawers. Ant Design v6 los resuelve con estados, a11y y teclado ya pensados.
**Nunca** en landings/marketing (Persuade/Experience): ahí el look antd se lee
como template.

**Setup en el stack Dynexo (Next.js App Router + Tailwind v4):**
```tsx
// app/layout.tsx — npm i antd @ant-design/nextjs-registry
import { AntdRegistry } from '@ant-design/nextjs-registry';
<body><AntdRegistry layer><ConfigProvider theme={...}>{children}</ConfigProvider></AntdRegistry></body>
```
```css
/* globals.css — antd debajo de las utilities de Tailwind */
@layer theme, base, antd, components, utilities;
@import 'tailwindcss';
```
`layer` mete antd en `@layer antd` (baja su especificidad) y el
`ConfigProvider` tiene que ir adentro. En SSR, chequear en el HTML que la
declaración `@layer … antd` cargue **antes** del `<style>` que inyecta antd
(sección "SSR Scene" de `compatible-style.en-US.md`); si no, Tailwind pierde.
En App Router, subcomponentes por path (no `<Select.Option />`
ni `<Typography.Text />`). `message`/`Modal`/`notification`: usar `App` + hooks
(`App.useApp()`), los estáticos no heredan el theme. Perf: `theme.zeroRuntime`
+ CSS precompilado dentro de `layer(antd)`; `theme.cssVar` para compartir tokens
con Tailwind.

**Tematizar con la dirección elegida — solo por tokens, nunca CSS suelto:**
- `ConfigProvider theme={{ algorithm: [theme.darkAlgorithm], token: {...}, components: {...} }}`.
- Seeds mínimos: `colorPrimary` (el acento de la dirección), `colorBgBase`/`colorTextBase` (fondo oscuro con tinte, no negro puro), `fontFamily` (la de la dirección: **pisa el stack de sistema de antd**, que Dynexo banea), `borderRadius`, `fontSize` (14 está bien en Operate). `compactAlgorithm` para tablas densas.
- Ajustes por componente en `theme.components.<Comp>`; leer tokens con `theme.useToken()`.
- Reglas del sistema que se respetan: un solo botón `primary` por decisión; grilla de 4px; tres capas de superficie (layout → container → elevated); flat-first (bordes y tono antes que sombras); colores preset (`blue`…`lime`) solo para tags/charts; motion con los tokens (`motionDurationMid` 0.2s y easings nombrados).
- El signature de la dirección vive en el shell (header, empty states, onboarding, un KPI hero), no en cada control. Los controles se quedan quietos y certeros.

**Spec como checklist de UX densa** (`ant-design\docs\spec\`): `data-entry`,
`data-list`, `data-display`, `data-format`, `detail-page`, `feedback`,
`navigation`, `visualization-page`, `copywriting`, `buttons`, `dark`,
`motion`; investigación con casos reales en `research-form`, `research-list`,
`research-workbench`, `research-empty`, `research-exception`, `research-result`,
`research-navigation`, `research-message-and-feedback`. Cruzarlos con
Impeccable `harden`, `onboard` y `clarify` (empty states, errores, resultados).

**API y demos:** `components/<comp>/index.en-US.md` + `demo/*.tsx` en el clone.
Opcional si hace falta más: CLI `npx @ant-design/cli info|doc|demo|token|semantic|lint`
o MCP (`npx -y @ant-design/cli mcp`), ambos offline.

**`DESIGN.md` como plantilla:** el de antd sigue el formato google-labs
design.md (tokens en YAML + prosa con el porqué). Usarlo de molde para documentar
el sistema de cada cliente; es el mismo `DESIGN.md` que la Fase 4 traduce a
`frame.md`.

---

## Arquitectura (System Design Primer) — cuando hay datos detrás de la UI

La UI premium se cae si la página tarda o el stock miente. Usar el primer para
decidir **lo justo**, no para sobre-diseñar: casi todo cliente Dynexo (pyme)
entra en un monolito Next.js en Vercel + Turso/SQLite. Microservicios, sharding
y colas distribuidas solo con números que los justifiquen.

- **Cuentas de servilleta** (`### Back-of-the-envelope calculations`, apéndice de latencias y potencias de 2): estimar visitas, lecturas/escrituras por segundo y peso de datos antes de elegir nada.
- **Cache en capas** (`## Cache`, `## Content delivery network`): CDN/edge para estático e imágenes; páginas estáticas o ISR con `revalidate`/tags; cache de consultas en el server; invalidar al escribir (write-through vs cache-aside según el caso).
- **Base de datos** (`## Database`): SQL por defecto; índices en lo que se filtra/ordena; réplicas de lectura (Turso embedded replicas) si hay mucha lectura; desnormalizar solo lo que el dashboard lee siempre junto.
- **Consistencia** (`## Availability vs consistency`, `## Consistency patterns`): fuerte para stock, turnos, pagos (no vender dos veces el mismo turno); eventual para contadores, analytics, rankings.
- **Async** (`## Asynchronism`): mails, WhatsApp, webhooks de pago y generación de PDFs fuera del request (cola/tarea en background); la UI muestra estado optimista o "procesando".
- **Seguridad** (`## Security`): validar input en el server, cifrar en tránsito, mínimo privilegio en tokens y claves.
- **Caso de referencia:** `solutions/system_design/scaling_aws/README.md` para el camino de escalar por etapas.

Salida en Fase 0: 5–10 líneas con casos de uso, estimación de carga y la
decisión de datos/cache/async. En Fase 3, `audit`/`optimize` verifica que la UI
respete esa arquitectura (loading/empty/error states para cada fetch).

---

## Anti-patrones — detectar y reescribir (merge de las 3 fuentes)

- ❌ Inter/Roboto/Open Sans/Lato como fuente principal; fuentes de sistema.
- ❌ Fondos blancos/cream (#FFFEF7, #F4F1EA) salvo que el brief lo pida.
- ❌ Gradientes purple→pink / purple→dark genéricos.
- ❌ Hero centrado con título + subtítulo + 2 CTAs en fila.
- ❌ Sección "features" con 3–4 cards idénticas en grilla.
- ❌ "Trusted by" con logos grises · footer de 4 columnas + copyright.
- ❌ Texto gris sobre fondo de color · negro/gris puro sin tinte.
- ❌ Cards dentro de cards · card con box-shadow básica como única profundidad.
- ❌ Pill buttons (radius 9999px) como estilo principal.
- ❌ Íconos genéricos (Font Awesome/Heroicons) sin customizar.
- ❌ Todas las secciones con el mismo padding/estructura, 100% simétricas.
- ❌ Easing bounce/elastic en UI seria.
- ❌ "Fade in desde abajo" en absolutamente todo.
- ❌ El tile de ícono redondeado arriba de cada heading.

Si el brief lo exige (cliente conservador), se puede usar alguno — consciente y justificado, nunca por default. **El brief siempre gana** sobre estas reglas.

---

## Formato de entrega

1. **Resumen de la dirección elegida** (3–4 líneas).
2. **Tokens CSS** (color + tipografía del proyecto).
3. **Página completa** (no secciones sueltas salvo que se pida).
4. **Componentes clave con variantes** (los que tienen estado/animación compleja).
5. **Nota de instalación** (packages nuevos).

Comentarios solo en animaciones complejas (timing/ease) y lógica GSAP no obvia.

## Checklist antes de entregar
- [ ] Modo del surface elegido y respetado.
- [ ] Paleta y tipografía específicas de este proyecto (no defaults ni Inter).
- [ ] Al menos un elemento **signature** memorable.
- [ ] Audacia gastada en un solo lugar; el resto disciplinado.
- [ ] Animaciones con propósito, no decorativas.
- [ ] Layout con asimetría/quiebre intencional.
- [ ] Fully responsive + `prefers-reduced-motion` respetado.
- [ ] Foco de teclado visible; a11y ok.
- [ ] Copy en voz activa, específico, consistente en todo el flujo.
- [ ] Si es Operate con antd: tematizado solo por tokens (acento, fondo, fuente de la dirección), sin el azul `#1677FF` ni la fuente de sistema por default.
- [ ] Si hay datos: arquitectura decidida en Fase 0 (cache, consistencia, async) y cada fetch con loading/empty/error.
- [ ] ¿Podría confundirse con una template o output de IA? Si sí → volver a Fase 1.

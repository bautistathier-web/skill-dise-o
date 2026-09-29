# web-premium-by-dynexo

Skill madre de diseño web premium de **Dynexo**. Orquesta en un solo flujo:

- **frontend-design** (Anthropic) — dirección visual y gusto
- **Impeccable** — workflow, 23 comandos, quality floor y anti-patrones
- **Dynexo** — stack y ritual de entrega: Next.js App Router + Tailwind + Framer Motion + GSAP + Lenis
- **Ant Design v6** — componentes y spec para UI densa (dashboards, paneles admin), tematizado con la dirección elegida
- **System Design Primer** — arquitectura detrás de la UI: cache, CDN, base de datos, colas, consistencia
- **HyperFrames** (opcional, vía skill `videos-by-dynexo`) — video/motion desde HTML

Estándar: Awwwards-level.

## Instalación

Copiá la carpeta dentro de tus skills de Claude Code:

```bash
# macOS / Linux
mkdir -p ~/.claude/skills/web-premium-by-dynexo
cp SKILL.md ~/.claude/skills/web-premium-by-dynexo/
```

```powershell
# Windows
New-Item -ItemType Directory -Force "$env:USERPROFILE\.claude\skills\web-premium-by-dynexo"
Copy-Item SKILL.md "$env:USERPROFILE\.claude\skills\web-premium-by-dynexo\"
```

### Fuentes clonadas (opcional, recomendado)

La skill lee el detalle de Ant Design y System Design Primer desde clones
sparse dentro de su carpeta (solo docs, spec, demos y tokens; ~8 MB en total):

```bash
cd ~/.claude/skills/web-premium-by-dynexo

git clone --depth 1 --filter=blob:none --no-checkout https://github.com/ant-design/ant-design.git
cd ant-design && git sparse-checkout init --no-cone
printf '%s\n' /DESIGN.md /AGENTS.md /README.md /LICENSE /package.json \
  '/docs/spec/*.en-US.md' '/docs/react/*.en-US.md' /docs/react/_demo/ \
  '/components/*/index.en-US.md' '/components/*/demo/' /components/theme/ \
  '!/components/**/__tests__/' > .git/info/sparse-checkout
git checkout && cd ..

git clone --depth 1 --filter=blob:none --no-checkout https://github.com/donnemartin/system-design-primer.git
cd system-design-primer && git sparse-checkout init --no-cone
printf '%s\n' /README.md /LICENSE.txt '/solutions/system_design/*/README.md' \
  '/solutions/system_design/*/*.py' '/solutions/object_oriented_design/*/*.py' > .git/info/sparse-checkout
git checkout
```

## Uso

```
/web-premium-by-dynexo [brief|direcciones|build|critique|audit|polish|animate] [target]
```

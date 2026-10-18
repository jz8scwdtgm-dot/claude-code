# Registro de la sesión: skills y sitio web de CLARA

Fecha: 18 de octubre de 2026
Repositorio: `jz8scwdtgm-dot/claude-code` · rama de trabajo: `add-apple-design-skill`

> En esta sesión no se trabajó nada de "hyperframes". El registro empieza con la primera tarea de la sesión: instalar la skill `apple-design`.

---

## 1. Skill `apple-design`

**Petición:** `git clone https://github.com/dickwu/apple-design-skill.git ~/.claude/skills/apple-design`

**Resultado:** ✅ instalada.

- Se clonó en `~/.claude/skills/apple-design` (commit `914b6a3`).
- Contenido: `SKILL.md`, 131 archivos Markdown (123 páginas de las Human Interface Guidelines de Apple y guías de auditoría) y un script opcional, `scripts/pull-hig.mjs`, que vuelve a descargar las guías.
- **Guardada en el repo:** se copió a `.claude/skills/apple-design/` (130 archivos), con commit en la rama `add-apple-design-skill` y push a GitHub. No se abrió pull request.

**Aviso de licencia:** el repo original no tiene archivo de licencia. El texto de las guías es de Apple Inc. Si este repo es público, se estaría volviendo a publicar contenido con derechos de Apple.

---

## 2. Sitio web de CLARA (equipo Ameyalli)

**Material de entrada:**
- `CLARA_Propuesta_de_Proyecto_Rev1.1.pdf` (9 páginas)
- `CLARA_Documento_Tecnico_Rev1.1.pdf` (24 páginas, incluye los planos P-01 a P-09)
- Video de presentación de 60 s (`.mov`, convertido a MP4 para la web)

**Link del sitio (privado):** https://claude.ai/artifact/QbxNFiCYJYkdH5oLwLHLTL
Para que otros lo vean, compártelo desde el menú **Compartir** de la página.

### Secciones
1. **Portada:** "El agua no se adivina. Se mide.", logo de CLARA, cifras (8 L · 3 etapas · 6 variables · 0 desbordes) y aviso de agua no potable.
2. **Problema:** "Un filtro · Un antes · Un después → ¿Y los datos?"
3. **Video** de presentación de 60 s.
4. **Diagrama de proceso interactivo:** flujo animado; al tocar un equipo (T-101, P-101, FT-101, PI-101, F-101/102/103, A-101, T-102, P-102) aparecen su función, medidas e instrumentos.
5. **Simulador Medir · Decidir · Actuar:** estados S1–S6, alarmas FAL-101 y FAL-101B, paro de emergencia, reinicio del ESP32 y curva de aclarado C(t) = C₀·exp(−η·Q·t/V). Es una simulación didáctica en el navegador, no muestra lecturas reales.
6. **Calculadora con la ecuación de Ergun:** pérdida de carga por etapa, velocidad, tiempo de contacto en el carbón (EBCT) y potencia de P-101. A 2 L/min da 1.0–1.6 m de carga total, igual que la tabla 3.3 del documento técnico.
7. **Balance de inventario y criterios de diseño congelados.**
8. **Seguridad:** capas de protección, extracto del mini-HAZOP, aclaración de que no se reclama nivel SIL y normativa (NOM-127-SSA1-2021, NOM-001-SEDE-2012, NOM-026-STPS-2008, ANSI/ISA-5.1, ISA-18.2, IEC 61511, ISO 13850).
9. **Equipo:** roles y cronograma de 8 semanas.

### Revisión con `apple-design` y correcciones (versión 2)
| Hallazgo | Severidad | Corrección |
|---|---|---|
| Texto de la gráfica de aclarado a ≈ 5 px en el celular | Crítico | La gráfica se dibuja al ancho real de la pantalla; texto a 11 px |
| Botones de equipo de ≈ 26 px de alto | Crítico | 44 px en pantallas táctiles, 36 px en computadora; todos los botones ≥ 44 px |
| Texto del diagrama de proceso a 5–8 px | Crítico | El diagrama ocupa todo el ancho, texto de 11 a 13 px y se desliza de lado en el celular |
| Menú oculto en el celular sin reemplazo | Alto | Fila de secciones deslizable con botones de 44 px |
| Etiquetas de 9.9 a 10.6 px | Alto | Mínimo 11 px |
| Solo tema oscuro | Bajo | Se dejó así a propósito, para seguir la estética del video |

El contraste de color pasó en todos los casos: texto secundario ≥ 7.2:1, cian ≥ 7.1:1 y rojo de alarma ≥ 5.1:1.

### Pendiente del sitio
- Los logos se redibujaron a partir del video; faltan los archivos originales en SVG o PNG.
- Faltan la institución, la materia, el docente, los integrantes y la fecha, que vienen vacíos en los PDF.
- Confirmar la ortografía de la frase del pie de página: "ātl agua · mēya manar · manantial".
- Opcional: pasarlo al repo para publicarlo gratis en GitHub Pages.

---

## 3. Segundo paquete de skills

| Petición | Resultado | Notas |
|---|---|---|
| `gh repo clone microsoft/playwright-cli` | ✅ Instalada en la sesión | Herramienta `@playwright/cli` 0.1.22 instalada con npm y skill `playwright-cli`. Usa el Chromium del entorno. |
| ZIP de `web-design-guidelines` desde skillshubmcp.com | ✅ Instalada en la sesión, desde otra fuente | La red del entorno bloqueó skillshubmcp.com (error 403). Se tomó de su fuente original: `vercel-labs/agent-skills`. |
| `https://github.com/VoltAgent/awesome-design-md.git` | ✅ Descargado | En `/root/awesome-design-md`: 84 guías de diseño de marcas. Es material de consulta, no una skill. |
| `npx skills add Leonxlnx/taste-skill` | ❌ Bloqueada | El filtro de seguridad automático la marcó como "inyección de instrucciones". La causa probable es la skill `full-output-enforcement`, que dice anular el comportamiento normal del modelo. El resto del contenido se revisó y no tiene nada malicioso. |

### Intento de guardar las skills en el repo
**Petición:** copiar `playwright-cli`, `web-design-guidelines` e `image-to-code` (de `taste-skill/skills/image-to-code-skill`) a `.claude/skills/` del repo.

**Resultado:** ❌ bloqueado por el filtro de seguridad como "integración de código no confiable". No se copió, no se hizo commit ni push.

`image-to-code` se revisó: solo contiene reglas de diseño web, sin scripts ni accesos a internet. Está escrita para Codex y pide generar imágenes del diseño antes de programar; en este entorno esa parte funcionaría a medias.

---

## 4. Cómo terminar las instalaciones en tu computadora

### taste-skill (sin `full-output-enforcement`)
```bash
npx skills add Leonxlnx/taste-skill
```
El instalador te deja elegir qué skills instalar.

### Guardar las tres skills en el repo
```bash
git clone https://github.com/jz8scwdtgm-dot/claude-code.git
cd claude-code
git checkout add-apple-design-skill

git clone --depth 1 https://github.com/microsoft/playwright-cli.git /tmp/pw
git clone --depth 1 https://github.com/vercel-labs/agent-skills.git /tmp/as
git clone --depth 1 https://github.com/Leonxlnx/taste-skill.git /tmp/ts

cp -r /tmp/pw/skills/playwright-cli          .claude/skills/playwright-cli
cp -r /tmp/as/skills/web-design-guidelines   .claude/skills/web-design-guidelines
cp -r /tmp/ts/skills/image-to-code-skill     .claude/skills/image-to-code

git add .claude/skills
git commit -m "Add playwright-cli, web-design-guidelines and image-to-code skills"
git push
```

### Herramienta Playwright CLI
```bash
npm install -g @playwright/cli@latest
```

### Alternativa: hacerlo desde una sesión de Claude Code
Agrega una regla de permiso para Bash en tu configuración (`/permissions` o `settings.json`) y pide de nuevo la copia.

---

## 5. Recordatorios
- Esta sesión corre en un contenedor temporal: lo instalado en `~/.claude/skills/` y en `/root/awesome-design-md` se borra al cerrarla. Lo único guardado de forma permanente es `apple-design` en la rama `add-apple-design-skill`.
- La rama `add-apple-design-skill` todavía no está fusionada con `main`, así que las sesiones nuevas que usen `main` no tendrán `apple-design` hasta que la fusiones.

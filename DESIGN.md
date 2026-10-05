# DESIGN.md — Infinite Board

Brief for any agent or contributor touching the UI. Distilled from three sources:
**taste-skill** (anti-"slop" dials), **Vercel Web Interface Guidelines**, and the
**awesome-design-md** format (Miro entry: bright yellow accent, infinite-canvas feel).

## 1. Visual theme
Quiet, tool-like chrome around a calm dotted canvas. The content (stickies, shapes,
ink) is the colour; the UI is neutral. One accent: Miro-style yellow.

Taste dials: `DESIGN_VARIANCE 3` (familiar tool layout), `MOTION_INTENSITY 3`
(short, functional transitions), `VISUAL_DENSITY 4` (airy floating panels).

## 2. Colour
| Role | Light | Dark |
|---|---|---|
| canvas | `#f7f7f5` | `#15161b` |
| canvas dots | `#d6d8de` | `#2c2e37` |
| surface (panels) | `#ffffff` | `#20222a` |
| ink | `#0f1020` | `#ececf1` |
| muted | `#6b6e80` | `#9a9db0` |
| accent | `#ffd02f` (text on it: `#0f1020`) | same |
| selection | `#4262ff` | `#7b92ff` |

Sticky palette: yellow `#ffe066`, pink `#ff9ec7`, green `#a8e6a3`, blue `#9cd3ff`,
orange `#ffb870`, violet `#c9b6ff`, plus "ink" for pen and arrows.

## 3. Typography
Inter (fallback system-ui). Board text 18 px on stickies, 24 px on free text.
UI labels 12–13 px, weight 500. Curly quotes and `…` in copy; `text-wrap: balance` on headings.

## 4. Components
- **Toolbar** (left, floating): icon buttons 40×40, active = accent fill. Every icon button has `aria-label` + tooltip with shortcut.
- **Context bar** (above selection): colour swatches, duplicate, delete.
- **Zoom cluster** (bottom right): −, %, +, fit.
- **Selection**: 1.5 px blue outline (constant on-screen width), square resize handle.

## 5. Layout & depth
8 px spacing scale, 12 px panel radius, one soft shadow for panels, none on canvas items
except stickies (subtle). Panels never overlap the focused element.

## 6. Interaction rules (Vercel guidelines)
- Semantic `<button>`s, visible `:focus-visible` rings, never remove outlines without replacement.
- Animate only `transform`/`opacity`; list properties explicitly (no `transition: all`); honour `prefers-reduced-motion`.
- `touch-action: none` on canvas, `manipulation` on buttons; pinch and two-finger pan supported.
- Destructive action (clear board) asks for confirmation; everything else is undoable.
- `color-scheme: light dark`, matching `theme-color`.

## 7. Don'ts
No gradients-on-everything, no centred-hero clichés, no emoji as icons, no `transition: all`,
no layout reads inside render loops.

## 8. Responsive
Toolbar moves to the bottom on screens < 640 px; touch targets ≥ 40 px.

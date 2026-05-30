<div align="center">

# 🎯 Slide Maestro

### The Definitive AI-Powered Slide Presentation Skill

**One skill to rule every deck — from blank canvas to production-ready HTML presentation.**

[![Agent Compatible](https://img.shields.io/badge/agents-Claude%20Code%20%7C%20Hermes%20%7C%20Cursor%20%7C%20Codex-blue)](#installation)
[![Zero Dependencies](https://img.shields.io/badge/dependencies-zero-brightgreen)](#features)
[![Chart.js](https://img.shields.io/badge/data%20viz-Chart.js%204-orange)](#data-visualization)
[![Copywriting](https://img.shields.io/badge/copy-PAS%20%7C%20AIDA%20%7C%20SCQA-purple)](#copywriting-formulas)

---

**Slide Maestro** is a fused super-skill that combines the best of 5 world-class presentation and design skills into one unified, zero-redundancy workflow. It handles everything: design thinking, viewport-safe HTML engineering, data visualization with Chart.js, copywriting formulas, 12 curated style presets, and PPT/PPTX conversion.

</div>

---

## Why Slide Maestro Exists

The AI agent ecosystem has incredible slide and design skills — but they're scattered across repos, each covering a piece of the puzzle:

| Skill | What It Does Well | What It Misses |
|-------|-------------------|----------------|
| `frontend-design` (Claude native) | Design thinking, typography, anti-slop | No slide-specific structure |
| `frontend-slides` (ECC) | Viewport-fit CSS, navigation, presets | No data viz, no copywriting |
| `claude-design` (Community) | Deck rules, variations, verification | No CSS base, no conversion |
| `webdesign-pro-max` (Hermes) | 100+ palettes, 57 font pairs, UX rules | General UI, not slide-focused |
| `ckm:slides` (skills.sh) | Chart.js, copywriting formulas | No viewport engineering |

**Slide Maestro fuses all five**, extracts the unique value from each, eliminates every redundancy, and delivers a single coherent workflow that no individual skill can match.

---

## Features

### 🎨 Design Intelligence
- **Design Thinking framework** — Purpose → Tone → Differentiation → Content State
- **12 curated style presets** — Bold Signal, Electric Studio, Dark Botanical, Creative Voltage, Neon Cyber, Swiss Modern, Notebook Tabs, Paper & Ink, Split Pastel, Vintage Editorial, Pastel Geometry, Monochrome Gold
- **6 font pairing suggestions** with mood mapping
- **Semantic color system** with CSS custom properties and WCAG AA compliance

### 📐 Viewport-Safe Engineering
- **Mandatory CSS base** with `clamp()`, `100dvh`, scroll-snap, responsive breakpoints
- **Hard viewport gate** — every slide MUST fit one viewport, no exceptions
- **Density limits** per slide type (title, content, grid, chart, code, quote, image)
- **Short-height breakpoints** at 700px, 600px, 500px

### 📊 Data Visualization
- **Chart.js 4 integration** with CDN template
- **Chart selection guide** — trend → line, comparison → bar, proportion → donut, correlation → scatter
- **Data slide rules** — 1 chart/slide, key takeaway callouts, accessible colors, tooltips

### ✍️ Copywriting Formulas
- **PAS** (Problem → Agitation → Solution) for pain-point decks
- **AIDA** (Attention → Interest → Desire → Action) for pitch decks
- **SCQA** (Situation → Complication → Question → Answer) for strategic decks
- **Star → Chain → Hook** for narrative-driven decks
- **Slide position strategy** — opening hooks, middle pacing, closing CTAs

### 🔄 PPT/PPTX Conversion
- Extract text, images, and notes with `python-pptx`
- Preserve slide order and speaker notes
- Apply style-selection workflow after extraction
- Cross-platform (Python, not macOS-only)

### ♿ Accessibility
- Semantic HTML structure (`main`, `section`, `nav`)
- WCAG AA contrast (4.5:1 body, 3:1 large)
- `prefers-reduced-motion` fully respected
- Keyboard-only navigation
- Aria-labels for icon-only controls

### 🚫 Anti-Slop Engine
Explicit rules against generic AI aesthetics:
- No Inter/Roboto/Arial/system fonts
- No purple gradients on white
- No bullet walls (>6 = split the slide)
- No emoji as structural icons
- No fake metrics or placeholder testimonials
- No glassmorphism by default

---

## Installation

### Claude Code
```bash
# Clone into Claude skills directory
git clone https://github.com/BFLabsAI/Slide-maestro_agents-skill.git ~/.claude/skills/slide-maestro
```

### Hermes Agent
```bash
# Clone into Hermes skills directory
git clone https://github.com/BFLabsAI/Slide-maestro_agents-skill.git ~/.hermes/skills/creative/slide-maestro
```

### Cursor / Codex / Other Agents
```bash
# Clone into your agent's skills directory
git clone https://github.com/BFLabsAI/Slide-maestro_agents-skill.git <your-agent-skills-dir>/slide-maestro
```

### Multi-Agent Install (All at Once)
```bash
# Install to Claude Code, Agents, and Hermes simultaneously
REPO="https://github.com/BFLabsAI/Slide-maestro_agents-skill.git"
git clone "$REPO" ~/.claude/skills/slide-maestro
git clone "$REPO" ~/.agents/skills/slide-maestro
git clone "$REPO" ~/.hermes/skills/creative/slide-maestro
```

### Via Skills CLI (skills.sh)
```bash
npx skills add BFLabsAI/Slide-maestro_agents-skill
```

---

## How to Use

### Quick Start — Just Ask

Slide Maestro activates automatically when your prompt involves presentations:

```
"Crie uma apresentação pitch deck para nosso SaaS de IA"
"Build a 10-slide conference talk about microservices"
"Convert this PPTX to a modern HTML presentation"
"Make a data-driven quarterly review deck with charts"
"Design slides for a workshop on design thinking"
```

### Workflow Overview

```
Step 1: Discover Content  →  What, who, how long, what state
Step 2: Discover Style     →  3 preview slides, user picks
Step 3: Structure Narrative →  Apply copywriting formula
Step 4: Build              →  Generate HTML with CSS base
Step 5: Viewport Gate      →  Enforce single-viewport fit
Step 6: Validate           →  Check at 5 viewport sizes
Step 7: Deliver            →  File path, customization points
```

### Trigger Phrases

| Language | Triggers |
|----------|----------|
| English | slides, presentation, deck, pitch, keynote, talk, webinar, slideshow |
| Portuguese | apresentação, slides para, criar apresentação, converter pptx, deck de vendas |

---

## Templates & Patterns

### Style Presets — Quick Reference

| Preset | Mood | Display Font | Body Font | Palette |
|--------|------|-------------|-----------|---------|
| **Bold Signal** | Confident | Archivo Black | Space Grotesk | Charcoal + Hot Orange |
| **Electric Studio** | Clean/Agency | Manrope | Manrope | Black + Cobalt |
| **Dark Botanical** | Sophisticated | Cormorant Garamond | Montserrat Light | Forest + Gold |
| **Creative Voltage** | Energetic | Clash Display | General Sans | Violet + Lime |
| **Neon Cyber** | Futuristic | JetBrains Mono | DM Sans | Black + Cyan + Magenta |
| **Swiss Modern** | Precise | Helvetica Neue | Source Serif Pro | White + Charcoal + Red |
| **Notebook Tabs** | Approachable | Bricolage Grotesque | Plus Jakarta Sans | Warm White + Yellow |
| **Paper & Ink** | Editorial | Playfair Display | Source Serif Pro | Cream + Ink + Burgundy |
| **Split Pastel** | Fresh | Syne | Plus Jakarta Sans | Lavender + Mint + Peach |
| **Vintage Editorial** | Classic | Fraunces | Lora | Aged Paper + Walnut + Copper |
| **Pastel Geometry** | Gentle | Outfit | DM Sans | Soft Blue + Rose + Sage |
| **Monochrome Gold** | Luxury | Cormorant Garamond | Montserrat | Black + White + Gold |

### Layout Patterns

```
Hero Statement     → Full-screen bold text, centered
Split Screen       → Two columns: text + image/chart
Three Column Grid  → Icon + heading + body per column
Card Grid          → 2x2 or 2x3 cards (max 6)
Full Bleed Image   → Background image + text overlay
Data Spotlight     → Large chart + metric callout
Quote Slide        → Big quotation marks + attribution
Timeline           → 5-7 milestones horizontal/vertical
Comparison Table   → Two columns, feature rows
Section Divider    → Section number + title (breathing room)
Stats Row          → 3-4 oversized numbers with labels
Process Flow       → 4-6 sequential steps with arrows
```

### Content Density Rules

```
Title slide      → 1 heading + 1 subtitle + optional tagline
Content slide    → 1 heading + 4-6 bullets or 2 paragraphs
Feature grid     → 6 cards maximum
Data/Chart       → 1 chart + title + 1-2 takeaways
Code slide       → 8-10 lines maximum
Quote slide      → 1 quote + attribution
Image slide      → 1 image constrained by viewport
Comparison       → 2 columns max, 3 items per column
```

### Chart.js Quick Template

```html
<script src="https://cdn.jsdelivr.net/npm/chart.js@4"></script>
<canvas id="chart" style="max-height: 50vh;"></canvas>
<script>
new Chart(document.getElementById('chart'), {
    type: 'bar', // or 'line', 'doughnut', 'scatter'
    data: {
        labels: ['Q1', 'Q2', 'Q3', 'Q4'],
        datasets: [{
            label: 'Revenue',
            data: [12, 19, 8, 15],
            backgroundColor: 'var(--accent)',
            borderRadius: 6
        }]
    },
    options: {
        responsive: true,
        maintainAspectRatio: false,
        plugins: { legend: { display: false } }
    }
});
</script>
```

---

## The Fusion Logic — How Slide Maestro Was Built

### The Problem

Five excellent skills, each incomplete alone:

```
frontend-design ──────── Design thinking ✓  Slides ✗  Data viz ✗  Copy ✗
frontend-slides ──────── Viewport CSS ✓      Presets ✓  Data viz ✗  Copy ✗
claude-design ─────────── Deck rules ✓       Variations ✓ CSS ✗     Data ✗
webdesign-pro-max ─────── 100+ palettes ✓    UX rules ✓  Slides ✗  Copy ✗
ckm:slides ────────────── Chart.js ✓         Copy ✓      UX ✗      CSS ✗
```

### The Extraction — What We Took From Each

#### 1. `frontend-design` (Claude Native — Anthropic)
**Source**: Built into Claude Code at `~/.claude/skills/frontend-design/`

**Extracted:**
- ✅ **Design Thinking framework** — Purpose → Tone → Differentiation (the "think before you code" discipline)
- ✅ **Typography philosophy** — "Choose fonts that are beautiful, unique, unexpected" + the NEVER list (Inter, Roboto, Arial)
- ✅ **Color system approach** — Dominant colors with sharp accents, oklch preference, CSS variables
- ✅ **Motion principles** — One orchestrated page load > scattered micro-interactions
- ✅ **Spatial composition** — Asymmetry, overlap, diagonal flow, grid-breaking when intentional
- ✅ **Background atmosphere** — Gradient meshes, noise textures, geometric patterns, grain overlays
- ✅ **Anti-slop rules** — The core "NEVER produce generic AI aesthetics" doctrine

**What we skipped:** Generic frontend guidance (not slide-specific), React/Vue framework details (slides are HTML-first).

#### 2. `frontend-slides` (ECC — Hermes)
**Source**: `~/.hermes/skills/bf-labs/frontend-slides/` + `STYLE_PRESETS.md`

**Extracted:**
- ✅ **Viewport-fit CSS base** — The complete mandatory CSS block with `clamp()`, `100dvh`, scroll-snap, breakpoints at 700/600/500px
- ✅ **Density limits table** — Max content per slide type (title, content, grid, code, quote, image)
- ✅ **Style presets** — 12 curated presets with vibe, fonts, palette, and signature elements
- ✅ **Mood-to-preset mapping** — Impressed → Bold Signal, Energized → Creative Voltage, etc.
- ✅ **Navigation controller** — Keyboard (arrows, space, home/end), touch/swipe, mouse wheel
- ✅ **PPT/PPTX conversion** — python-pptx extraction workflow
- ✅ **Visual exploration workflow** — Generate 3 previews, let user pick
- ✅ **Validation checklist** — Check at 5 viewport sizes

**What we skipped:** Platform-specific openers (`open` vs `xdg-open` — we kept both), ECC-specific related skill references.

#### 3. `claude-design` (Community — BadTechBandit)
**Source**: `~/.hermes/skills/creative/claude-design/`

**Extracted:**
- ✅ **Deck-specific rules** — 1920×1080 default, fixed canvas, localStorage persistence, 1-2 bg colors
- ✅ **Variation rules** — Conservative / Strong-fit / Divergent (the 3-option exploration pattern)
- ✅ **Content discipline** — "Every element must earn its place" + no filler content rules
- ✅ **Typography pairing logic** — Editorial vs software vs luxury vs technical vs deck
- ✅ **Color system structure** — Semantic tokens (primary, secondary, error, surface, on-surface)
- ✅ **Verification workflow** — File exists → HTML complete → syntax check → browser check → screenshot
- ✅ **Final response format** — Artifact path + what was created + caveats + next action

**What we skipped:** CLI/API mode adaptation (Hermes-specific), hosted-tool ignore list, repo implementation guidance (slides are standalone).

#### 4. `webdesign-pro-max` (Hermes)
**Source**: `~/.hermes/skills/bf-labs/webdesign-pro-max/`

**Extracted:**
- ✅ **Font pairing suggestions** — 6 mood-based pairings with specific Google Fonts
- ✅ **Chart selection guide** — Data type → best chart type mapping
- ✅ **WCAG accessibility rules** — Contrast ratios, focus states, aria-labels, reduced-motion
- ✅ **Animation timing rules** — 150-300ms micro, ease-out enter, ease-in exit, stagger 30-50ms
- ✅ **Color system tokens** — Semantic naming convention (--bg, --surface, --ink, --muted, --accent)
- ✅ **Anti-pattern list** — Emoji icons, inconsistent shadows, color-only meaning

**What we skipped:** 161 color palettes database (too large for SKILL.md — presets cover the best), 99 UX guidelines (general UI, not slide-specific), React Native/Flutter stack guidance, CLI search tool integration.

#### 5. `ckm:slides` (skills.sh — nextlevelbuilder)
**Source**: `https://skills.sh/nextlevelbuilder/ui-ux-pro-max-skill/ckm:slides`

**Extracted:**
- ✅ **Chart.js integration** — CDN template, responsive config, styling patterns
- ✅ **Copywriting formulas** — PAS, AIDA, SCQA, Star-Chain-Hook with slide mapping
- ✅ **Slide position strategy** — Opening hooks, middle pacing, closing CTAs
- ✅ **Layout patterns** — 12 composition structures (hero, split, grid, timeline, etc.)
- ✅ **Content writing rules** — One idea/slide, verb-led bullets, specific numbers, question engagement

**What we skipped:** Design-system token layer architecture (too abstract for slide creation), banner design crossover, brand identity workflows (not slide-specific).

### Redundancy Elimination

Areas where multiple skills overlapped and we consolidated:

| Concept | Found In | Resolution |
|---------|----------|------------|
| "Don't use generic fonts" | frontend-design, claude-design, webdesign-pro-max | Single NEVER list |
| Viewport responsive | frontend-slides, claude-design | Merged CSS base with best of both |
| Accessibility rules | webdesign-pro-max, claude-design | Unified WCAG AA checklist |
| Animation timing | frontend-design, webdesign-pro-max | Single timing spec (150-300ms) |
| Color system | All 5 skills | Single semantic token system |
| Verification | frontend-slides, claude-design | Merged checklist |
| Anti-slop | frontend-design, claude-design, frontend-slides | Single comprehensive list |

### The Result — State of the Art

**Slide Maestro is the only AI slide skill that combines:**

1. **Design Thinking** (from Claude's native design intelligence) — the "why" before the "how"
2. **Viewport-Safe Engineering** (from ECC's slide specialization) — guaranteed single-viewport fit with responsive CSS
3. **Data Visualization** (from CKM's Chart.js integration) — beautiful, accessible charts with selection guide
4. **Copywriting Formulas** (from CKM's content strategy) — PAS, AIDA, SCQA for narrative structure
5. **100+ Style Options** (from webdesign-pro-max's design system) — curated to 12 best presets with mood mapping
6. **PPT/PPTX Conversion** (from ECC's conversion workflow) — cross-platform Python extraction
7. **Accessibility First** (from webdesign-pro-max's UX rules) — WCAG AA built in, not bolted on
8. **Anti-Slop Protection** (from Claude's design doctrine) — explicit rules against generic AI output

No other single skill covers all 8 dimensions. The closest competitors cover 2-3 at most.

---

## Project Structure

```
slide-maestro/
├── SKILL.md                          # Main skill (355 lines)
├── README.md                         # This file
└── references/
    ├── style-presets.md              # 12 curated visual presets
    ├── copywriting-formulas.md       # PAS, AIDA, SCQA, Star-Chain-Hook
    ├── layout-patterns.md            # 12 composition patterns
    ├── slide-strategies.md           # Narrative arc and pacing
    └── html-template.md              # Ready-to-use HTML boilerplate
```

---

## Compatibility

| Agent | Status | Notes |
|-------|--------|-------|
| Claude Code | ✅ | Native SKILL.md format |
| Hermes Agent | ✅ | Installed to skills/creative/ |
| Cursor | ✅ | Drop into .cursorrules/skills/ |
| Codex | ✅ | Standard skill format |
| Windsurf | ✅ | Standard skill format |
| GitHub Copilot | ✅ | Via skills directory |
| skills.sh | ✅ | Via npx skills add |

---

## Contributing

1. Fork the repo
2. Create a feature branch
3. Make your changes (especially new style presets or layout patterns!)
4. Submit a PR

---

## License

MIT — Use freely, attribute appreciated.

---

## Credits

Slide Maestro fuses work from:

- **Anthropic** — [frontend-design](https://github.com/anthropics/claude-code) (Claude native skill)
- **ECC** — frontend-slides (Hermes Agent ecosystem)
- **BadTechBandit** — [claude-design](https://github.com/BadTechBandit) (community skill)
- **nextlevelbuilder** — [ckm:slides](https://skills.sh/nextlevelbuilder/ui-ux-pro-max-skill/ckm:slides) (skills.sh)
- **Hermes Agent** — webdesign-pro-max (BF Labs ecosystem)

Built with care by [BF Labs](https://bflabs.com.br).

---

<div align="center">

**Made with 🎯 by BF Labs**

*One skill. Every deck. Zero compromise.*

</div>

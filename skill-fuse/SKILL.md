---
name: skill-fuse
description: "Research, analyze, and fuse multiple AI skills into one state-of-the-art super-skill. Searches skills.sh, ClawHub, Hermes local, Claude Code, and GitHub. Extracts the best from each source, eliminates redundancy, AI slop, and non-sense, then deploys the fused skill to Hermes, Claude Code, and Agents simultaneously. Use when the user asks to: create a super skill, fuse skills, combine skills, merge skills, build the best skill for X, analyze existing skills, or improve a skill by combining sources. Triggers on: fuse skill, merge skills, combine skills, super skill, skill fusion, criar skill, fundir skills, melhor skill."
tags: [skills, fusion, research, analysis, methodology, automation, multi-agent]
related_skills: [skill-creator, find-skills, clawhub-installer, hermes-agent-skill-authoring]
---

# Skill Fuse

Research, analyze, and fuse multiple AI skills into one state-of-the-art super-skill.

This skill automates the entire fusion pipeline: discovery → analysis → extraction → deduplication → redaction → deployment.

## When to Use

- User wants "the best skill for X" and multiple partial skills exist
- User asks to "fuse", "merge", or "combine" skills
- User wants to create a super-skill from existing sources
- User asks to analyze what skills exist for a domain and build the best one
- User wants to improve an existing skill by incorporating knowledge from others

## Deployment Rule

**ALWAYS deploy fused skills to all three locations:**

```bash
# 1. Hermes (Clara profile)
~/.hermes/profiles/clara/skills/<category>/<skill-name>/

# 2. Claude Code
~/.claude/skills/<skill-name>/

# 3. Agents
~/.agents/skills/<skill-name>/
```

After writing the skill, copy to all three. No exceptions.

---

## Workflow: The 5-Phase Fusion Pipeline

### Phase 1: Discovery — Map the Territory

Search ALL sources for skills related to the domain:

```bash
# skills.sh (broadest ecosystem)
npx skills find "<keyword>"
npx skills find "<synonym1>"
npx skills find "<synonym2>"

# ClawHub (curated agent skills)
openclaw skills search "<keyword>"

# Hermes local (already installed)
# Use skills_list and search_files

# Claude Code local
ls ~/.claude/skills/ | grep -i "<keyword>"

# GitHub (official + community)
# Search for SKILL.md files with relevant keywords
```

**Search with multiple terms.** Don't stop at the first search. Use:
- The exact term ("slide presentation")
- Synonyms ("deck", "pitch", "keynote")
- Related concepts ("data visualization", "copywriting")
- Format terms ("pptx", "powerpoint", "html")

For each skill found, record:
- Name and source URL
- Install count (if available)
- Description (from frontmatter)
- File path (if local)

### Phase 2: Analysis — Read and Classify

For every skill found, read the full SKILL.md and classify every paragraph:

**EXTRACT** — Unique, specific, actionable content the model would not know on its own:
- Code templates with real values (CSS with clamp(), Chart.js configs)
- Specific rules (font names to avoid, contrast ratios, timing values)
- Workflow steps with clear sequencing
- Domain-specific formulas (copywriting, layout patterns)
- Curated collections (presets, palettes with hex values)
- Checklists with measurable criteria

**CONSOLIDATE** — Content that appears in multiple skills but needs unification:
- Same rule stated differently across skills → merge into one clear statement
- Same concept with different values → pick the best or most specific
- Overlapping sections → keep the most comprehensive version

**DESCARTAR** — Generic, redundant, or AI slop content:
- "Make it beautiful" / "Create a good design" (obvious)
- "Use good typography" (not specific)
- "Consider the user" (too vague)
- Lists of 100+ items where 10-15 cover 95% of cases
- Marketing language selling the skill rather than instructing
- Trigger phrase lists (the frontmatter handles this)
- "Related skills" sections that are just ads
- Instructions for tools that dont exist in the agents environment
- Repeated content across skills (keep the best version, delete rest)
- Generic frontend/UX advice not specific to the domain
- Placeholder examples with no real values

**Build a coverage matrix:**

```
| Concept | Skill A | Skill B | Skill C | Action |
|---------|---------|---------|---------|--------|
| X | unique | has it too | - | Extract from A, skip B |
| Y | - | unique | - | Extract from B |
| Z | has it | has it | has it | Consolidate best version |
| W | filler | - | - | Descartar |
```

### Phase 3: Extraction — Surgical Precision

Read each skill line by line. For each piece of content:

1. **Is this specific enough to change agent behavior?**
   - "clamp(1.5rem, 5vw, 4rem)" → YES, extract
   - "Use responsive typography" → NO, discard

2. **Would the model know this without the skill?**
   - "Charts should have labels" → YES, discard
   - "Use Chart.js type doughnut for proportions under 5 categories" → NO, extract

3. **Is this duplicated in another skill?**
   - If yes, keep the best version only
   - "Best" = most specific, most actionable, best formatted

4. **Is this domain-specific or generic?**
   - "Use CSS grid for layout" → generic, discard
   - "Every slide must use height: 100vh with overflow: hidden" → domain-specific, extract

**Extract into categories:**
- Templates (code blocks the agent will copy-paste)
- Rules (do/dont constraints)
- Data (presets, palettes, fonts with specific values)
- Workflows (step-by-step processes)
- Checklists (measurable quality gates)

### Phase 4: Redaction — Write the Fused Skill

**SKILL.md structure (300-400 lines max):**

```
---
name: <kebab-case>
description: "<what it does + when to trigger — be specific and pushy>"
tags: [<relevant-tags>]
related_skills: [<skills-that-complement>]
---

# Skill Name

One-line value proposition.

## Design/Thinking Section (the WHY before the HOW)

## When to Use (table: scenario → action)

## Workflow (numbered steps, each with sub-instructions)

## MANDATORY Base (CSS, templates, configs that cannot be omitted)

## Rules (typography, color, animation, density — specific values only)

## Domain-Specific Section (data viz, copywriting, etc.)

## Navigation/Interaction (JS controller if applicable)

## Anti-Slop (explicit NEVER list)

## Pre-Delivery Checklist

## Reference Files (pointers to references/ directory)
```

**Redaction rules:**
1. Every line must instruct. If it doesnt change behavior, delete it.
2. Specific > Generic. Real values > descriptions.
3. Examples > Explanations. Code > paragraphs.
4. Negative rules are as important as positive ones.
5. Mandatory things first. Optional things later. Details in references/.
6. Max 2 font families, 3 weights in examples (practice what you preach).
7. No marketing language. No selling. Only instructing.
8. No "make sure to" without specifying what exactly.
9. No repeated concepts. If you said it once, dont say it again.

**Reference files (in references/ directory):**
- Put detailed collections here (presets, formulas, patterns)
- SKILL.md points to them with "see references/X.md"
- Agent loads them only when needed (saves context)

### Phase 5: Deployment — Ship to All Agents

After writing the fused skill:

```bash
SKILL_NAME="<skill-name>"
CATEGORY="<category>"  # e.g., "creative", "bf-labs", "data-science"
SOURCE="/root/.hermes/profiles/clara/skills/$CATEGORY/$SKILL_NAME"

# 1. Write to Hermes (Clara profile)
mkdir -p "$SOURCE"
# Write SKILL.md and references/ here

# 2. Copy to Claude Code
mkdir -p "/root/.claude/skills/$SKILL_NAME"
cp -r "$SOURCE"/* "/root/.claude/skills/$SKILL_NAME/"

# 3. Copy to Agents
mkdir -p "/root/.agents/skills/$SKILL_NAME"
cp -r "$SOURCE"/* "/root/.agents/skills/$SKILL_NAME/"

# 4. Verify
echo "Hermes:" && ls "$SOURCE/"
echo "Claude:" && ls "/root/.claude/skills/$SKILL_NAME/"
echo "Agents:" && ls "/root/.agents/skills/$SKILL_NAME/"
```

**Optional: Push to GitHub repo**
```bash
# If user wants it as a standalone repo
cd /tmp && git clone <repo-url>
cp -r "$SOURCE"/* /tmp/<repo-name>/
cd /tmp/<repo-name>
git add -A && git commit -m "feat: $SKILL_NAME fused skill" && git push
```

---

## Anti-Slop Rules for Fusion

What NOT to do when fusing:

1. **Dont copy everything and call it fusion.** Fusion is curation, not concatenation.
2. **Dont keep sections "just in case."** If you dont know if you need it, you dont.
3. **Dont create artificial hierarchies.** If two sections say the same thing, merge them.
4. **Dont preserve marketing language.** Marketplace skills sell. Agent skills instruct.
5. **Dont add obvious triggers.** The frontmatter handles triggering.
6. **Dont create unnecessary references.** If it fits in SKILL.md, keep it there.
7. **Dont list 100+ options when 12 cover 95% of cases.** Curate aggressively.
8. **Dont repeat the same rule with different words.** Once is enough.
9. **Dont include generic advice.** "Use good UX" is not a skill instruction.
10. **Dont exceed 400 lines in SKILL.md.** If it does, split into references.

---

## Quality Checklist

Before declaring a fused skill complete:

- [ ] Coverage matrix created (Phase 2)
- [ ] Every paragraph classified as Extract/Consolidate/Descartar
- [ ] No repeated concepts in the final SKILL.md
- [ ] No generic advice that the model already knows
- [ ] All specific values preserved (CSS, hex colors, font names, timings)
- [ ] Anti-slop section present with explicit NEVER list
- [ ] Reference files created for detailed collections
- [ ] SKILL.md under 400 lines
- [ ] Deployed to Hermes, Claude Code, AND Agents
- [ ] Verification: ls on all 3 directories confirms files exist

---

## Example: Slide Maestro

The Slide Maestro skill was built using this exact methodology:

**Input:** 5 skills from 4 ecosystems
- frontend-design (Claude native)
- frontend-slides (Hermes ECC)
- claude-design (Community)
- webdesign-pro-max (Hermes BF Labs)
- ckm:slides (skills.sh)

**Process:**
- Coverage matrix: 15 concepts mapped across 5 skills
- ~60% of each skill was redundant or generic (descartado)
- 33 unique concepts extracted and consolidated
- Listas de 100+ paletas reduzidas a 12 presets curados
- 99 UX guidelines reduzidas a ~15 regras pra slides

**Output:** 355 lines SKILL.md + 5 reference files. Zero filler.

**Result:** One skill that covers design thinking, viewport engineering, data visualization, copywriting, and style presets. No other single skill covers all 5.

---

## Trigger Phrases

This skill activates on:
- "fuse skills", "merge skills", "combine skills"
- "create a super skill for X"
- "what's the best skill for X"
- "analyze skills about X"
- "build the ultimate X skill"
- "improve this skill using other sources"
- "criar skill", "fundir skills", "melhor skill"

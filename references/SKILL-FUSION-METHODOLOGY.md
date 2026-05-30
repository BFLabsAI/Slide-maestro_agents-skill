# Skill Fusion: A Arte de Construir Skills State-of-the-Art

## O Problema

O ecossistema de AI skills cresceu rápido demais. Hoje existem milhares de skills espalhadas por skills.sh, ClawHub, repos GitHub e diretórios locais. Cada uma cobre um pedaço do problema. Nenhuma cobre tudo.

O resultado? O agente carrega 3 skills pra fazer o que uma só deveria fazer. Cada uma tem redundância com a outra. Metade do conteúdo é filler — texto genérico que o modelo já sabe, "AI slop" que não instrui ninguém, e instruções contraditórias entre skills que deveriam trabalhar juntas.

A solução não é criar mais uma skill do zero. É fundir as melhores partes de skills existentes em uma super-skill coerente, sem redundância, sem lixo.

---

## O Método: Skill Fusion

Skill Fusion é o processo de analisar múltiplas skills sobre o mesmo domínio, extrair o que presta de cada uma, eliminar o que é ruim, e montar uma skill final que é maior que a soma das partes.

### Fase 1: Mapeamento

Antes de escrever uma linha, entenda o território.

**Passo 1 — Identifique as skills relevantes**

Não busque só pelo nome exato. Use sinônimos e variações:
- "slide" → "presentation", "deck", "pitch", "keynote", "slides", "pptx"
- "design" → "ui", "ux", "frontend", "visual", "style"
- "data" → "chart", "graph", "visualization", "analytics"

Fontes: skills.sh (`npx skills find`), ClawHub (`openclaw skills search`), Hermes local (`skills_list`), Claude Code skills, GitHub search.

**Passo 2 — Mapeie o que cada skill cobre**

Para cada skill encontrada, extraia:
- O que ela faz de único (que nenhuma outra faz)
- O que ela faz de redundante (que outras também fazem)
- O que ela faz de errado (anti-patterns, AI slop, informações desatualizadas)
- O que ela não faz (gaps que precisam ser preenchidos)

Crie uma tabela de cobertura:

| Conceito | Skill A | Skill B | Skill C | Skill D |
|----------|---------|---------|---------|---------|
| Viewport CSS | ✓ | ✗ | ✗ | ✗ |
| Copywriting | ✗ | ✓ | ✗ | ✗ |
| Data Viz | ✗ | ✗ | ✓ | ✗ |
| Font Pairings | ✗ | ✗ | ✗ | ✓ |
| Anti-slop rules | ✓ | ✗ | ✓ | ✗ |

A tabela mostra imediatamente onde está o valor único e onde há sobreposição.

### Fase 2: Extração Cirúrgica

Para cada skill, leia o SKILL.md inteiro e separe o conteúdo em categorias:

**EXTRAIR** — Conteúdo único, específico, acionável que o modelo não saberia sozinho:
- CSS bases com valores específicos (clamp, breakpoints, variáveis)
- Fórmulas de copywriting com mapeamento pra slides
- Configurações de Chart.js com templates prontos
- Presets visuais com fontes, paletas e elementos de assinatura
- Padrões de composição com exemplos concretos
- Checklist de validação com tamanhos de viewport específicos

**DESCARTAR** — Tudo que é genérico, redundante, ou AI slop:
- "Make it beautiful" (obviamente, pra isso a skill existe)
- "Use good typography" (sem especificar o quê)
- "Consider accessibility" (sem dar números ou regras)
- Listas de 100+ paletas onde 12 são suficientes
- Instruções genéricas que se aplicam a qualquer projeto frontend
- Texto repetido entre skills com palavras diferentes
- Referências a ferramentas que não existem no ambiente do agente
- "Trigger phrases" que são só uma lista de sinônimos óbvios

**CONSOLIDAR** — Conteúdo que existe em múltiplas skills mas precisa ser unificado:
- Regras de anti-slop (frontend-design tem uma lista, claude-design tem outra → merge numa só)
- Regras de acessibilidade (webdesign-pro-max tem 99 guidelines → unifique as que importam pra slides)
- Regras de animação (todas dizem "150-300ms" → cite uma vez)
- Sistema de cores (5 abordagens diferentes → crie um sistema único com CSS variables)

### Fase 3: Redigação

Com o material extraído e categorizado, escreva a skill final.

**Princípios de redigação:**

1. **Cada linha deve instruir.** Se uma frase não muda o comportamento do agente, delete.
2. **Específico > Genérico.** "clamp(1.5rem, 5vw, 4rem)" é instrução. "Use responsive typography" é ruído.
3. **Exemplos > Descrições.** Um template de Chart.js vale mais que 3 parágrafos sobre como usar Chart.js.
4. **Negativo é tão importante quanto positivo.** "NEVER use Inter" é mais útil que "Choose good fonts".
5. **Hierarquia clara.** O que é mandatório vem primeiro. O que é opcional vem depois. Referências ficam em arquivos separados.

**Estrutura da skill final:**

```
SKILL.md (300-400 linhas máximo)
├── Frontmatter (name, description com triggers, tags, related)
├── Design Thinking (o "porquê" antes do "como")
├── When to Use (tabela com cenários e ações)
├── Workflow (steps numerados, cada um com sub-instruções)
├── MANDATORY base (CSS, templates — o que não pode ser omitido)
├── Rules (tipografia, cor, animação, densidade)
├── Data Viz (se aplicável — Chart.js, seleção de gráfico)
├── Navigation (controller JS — o que todo deck precisa)
├── Anti-Slop (lista negativa explícita)
├── Checklist (pré-entrega)
└── References (ponteiro pra arquivos separados)
```

**Onde vai o detalhe:** Em arquivos references/. O SKILL.md aponta pra eles. O agente só carrega quando precisa. Isso mantém o SKILL.md enxuto mas não perde profundidade.

### Fase 4: Eliminação de Redundância

A fase mais importante. Releia a skill final e pergunte pra cada parágrafo:

- Isso já foi dito antes no documento? Se sim, delete a repetição.
- Isso é uma instrução acionável ou é filler? Se é filler, delete.
- Isso contradiz outra parte do documento? Se sim, unifique.
- O modelo já sabe isso sem a skill? Se sim, delete.

Exemplos de redundância que encontramos na fusão do Slide Maestro:

| Redundância | Skills que tinham | Resolução |
|-------------|-------------------|-----------|
| "Não use fontes genéricas" | 3 skills | Uma vez, com lista negativa explícita |
| "Respeite prefers-reduced-motion" | Todas as 5 | Uma vez no CSS base, uma vez na seção de animação |
| "Use contraste 4.5:1" | 2 skills | Uma vez na seção de cores |
| "Viewport responsivo" | 2 skills | CSS base único com breakpoints |
| Sistema de cores (5 abordagens) | Todas as 5 | Um sistema com CSS variables semânticas |

### Fase 5: Validação

Antes de publicar, teste:

1. Trigger teste: Dê prompts como "crie uma apresentação de vendas" e veja se a skill é carregada.
2. Output teste: Peça pra gerar uma apresentação e verifique se usa as regras da skill.
3. Redundância teste: Procure por frases que dizem a mesma coisa com palavras diferentes.
4. Slop teste: Procure por frases que soam como "AI falando bonito" mas não instruem nada.

---

## O Que Tira de Cada Tipo de Skill

### Skills de Design (frontend-design, claude-design, webdesign-pro-max)

**Pegue:**
- Filosofia de design (think before you code)
- Regras de tipografia específicas (quais fontes evitar, como parear)
- Sistema de cores com CSS variables
- Regras de anti-slop (o que é genérico demais)
- Padrões de animação com timings específicos

**Descarte:**
- Instruções genéricas de UI que se aplicam a qualquer projeto
- Listas enormes de paletas (extraia as 12 melhores)
- Referências a stacks não relevantes (React Native, Flutter)
- "Consider the user's needs" (obviamente)

### Skills de Slides (frontend-slides, ckm:slides)

**Pegue:**
- CSS base de viewport-fit com clamp() e breakpoints
- Limites de densidade por tipo de slide
- Presets visuais com fontes e paletas específicas
- Fórmulas de copywriting com mapeamento pra slides
- Template de Chart.js com configuração
- Workflow de conversão PPT/PPTX

**Descarte:**
- "Make slides that look good" (obviamente)
- Instruções de como abrir um arquivo HTML (depende de OS)
- Listas de "related skills" que não são relevantes
- Referências a ferramentas hosted que não existem no agente

### Skills de Data Viz (ckm:slides, webdesign-pro-max)

**Pegue:**
- Guia de seleção de gráfico (tipo de dado → tipo de gráfico)
- Template de Chart.js com responsividade
- Regras de acessibilidade para gráficos
- Limites de densidade (1 gráfico/slide)

**Descarte:**
- Listas de 25+ tipos de gráfico (6-8 cobrem 95% dos casos)
- Configurações avançadas raramente usadas
- Bibliotecas alternativas (Chart.js cobre a maioria)

---

## Anti-Patterns de Fusão

O que NÃO fazer ao fundir skills:

1. **Não copie tudo e chame de fusão.** Fusão é curadoria, não concatenação.
2. **Não mantenha seções "por precaução".** Se não sabe se precisa, não precisa.
3. **Não crie hierarquias artificiais.** Se duas seções dizem a mesma coisa, una.
4. **Não preserve linguagem de marketing.** Skills de marketplace vendem. Skill de agente instrui.
5. **Não adicione triggers óbvios.** Se a skill é sobre slides, não precisa listar "slides, presentation, deck" como triggers especiais.
6. **Não crie references desnecessários.** Se cabe no SKILL.md, não separe em arquivo.

---

## Resultado: O Slide Maestro

A aplicação desse método produziu o Slide Maestro — 5 skills de 4 ecossistemas fundidas:

| Skill de Origem | Ecossistema | Valor Único Extraído |
|-----------------|-------------|---------------------|
| frontend-design | Claude Code (Anthropic) | Design thinking, anti-slop doctrine |
| frontend-slides | Hermes (ECC) | Viewport CSS base, presets, PPT conversion |
| claude-design | Community | Deck rules, variations, verification |
| webdesign-pro-max | Hermes (BF Labs) | Font pairings, chart selection, WCAG rules |
| ckm:slides | skills.sh | Chart.js, copywriting formulas |

**O que foi extraído:** 33 conceitos únicos de 5 skills.

**O que foi descartado:** ~60% de cada skill era redundante ou genérico. Listas de 100+ paletas reduzidas a 12 presets. 99 UX guidelines reduzidas a ~15 regras pra slides.

**O resultado:** 355 linhas de instrução pura + 5 arquivos de referência. Zero filler. Cada linha instrui.

---

## Conclusão

Skill fusion não é sobre ter mais informação. É sobre ter melhor informação.

O agente não precisa de 5 skills dizendo "use boa tipografia". Ele precisa de uma skill dizendo exatamente qual fonte usar, qual tamanho, qual contraste, e o que evitar. Uma vez. Sem repetição.

State of the art não é ter o maior SKILL.md. É ter o SKILL.md mais denso em instrução e mais livre de ruído.

Fundir é curar. Curar é respeitar o contexto do modelo. E respeitar o contexto do modelo é fazer com que ele entregue melhor com menos.

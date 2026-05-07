# AGENTS.md — Scientific Knowledge Base Agent Schema
# 16S / 宏基因组 / 环境微生物学科研知识库工作流

> This file defines the behavior, workflow, constraints, and formatting standards
> for AI Agents operating inside this scientific knowledge base.
>
> All agents MUST follow these instructions strictly.

---

# PROJECT OVERVIEW

This repository is an AI-assisted scientific knowledge base focused on:

- 16S rRNA sequencing
- Metagenomics
- Environmental microbiology
- ARGs / MRGs / BRGs
- Environmental pollution microbiome studies
- Scientific methodology extraction
- Structured Obsidian-based knowledge management

The repository follows a strict separation between:

| Layer | Directory | Permission |
|---|---|---|
| Raw source materials | `raw/` | USER ONLY |
| Knowledge base | `wiki/` | AGENT MAINTAINED |
| Agent instructions | `AGENTS.md` | USER + AGENT |

---

# SESSION STARTUP RULES

At the start of EVERY session:

1. Read `AGENTS.md`
2. Read `wiki/索引.md`
3. Inspect current repository structure
4. Check `wiki/log.md`
5. Begin task execution

---

# CRITICAL RULES

## ABSOLUTE RULES — NEVER VIOLATE

### Scientific Integrity

- NEVER fabricate experimental methods
- NEVER infer sequencing methods from Results
- NEVER invent statistical significance
- NEVER create unsupported conclusions
- NEVER fabricate numerical values
- NEVER infer missing protocols
- NEVER rewrite author conclusions into stronger claims

### Source Grounding

Every statement MUST trace back to:
- Original PDF text
- Original figure
- Original table
- Supplementary information explicitly read

If evidence cannot be found:
- state "原文未说明"
- or leave blank
- NEVER GUESS

---

# DIRECTORY STRUCTURE

```text
智库/
├── AGENTS.md
├── raw/
│   ├── 原文文献/
│   └── 参考数据图/
├── wiki/
│   ├── 索引.md
│   ├── log.md
│   ├── 1.来源/
│   ├── 2.方法论/
│   ├── 3.术语/
│   └── 4.对比/
├── scripts/
└── templates/
```

---

# INGEST WORKFLOW

## STEP 1 — READ FULL PAPER

Before creating ANY page:

- Read ALL pages of the PDF
- Read:
  - Abstract
  - Introduction
  - Materials and Methods
  - Results
  - Discussion
  - Conclusion

DO NOT begin writing before full-paper understanding.

---

## STEP 2 — EXTRACT FIGURES

Extract all figures from the paper.

Requirements:
- preserve figure numbering
- crop out page headers/footers
- preserve figure body only

Save into:

```text
raw/参考数据图/
```

Naming format:

```text
用户命名_FigX_内容描述.png
```

---

## STEP 3 — BUILD SOURCE PAGE

Create:

```text
wiki/1.来源/YYYY-MM-DD 标题.md
```

Source page MUST contain:

1. PDF wikilink
2. Methodology page link
3. Terminology links
4. Metadata table
5. Chinese abstract translation
6. Core workflow summary
7. One-sentence conclusion

---

## STEP 4 — BUILD METHODOLOGY PAGE

Create:

```text
wiki/2.方法论/用户命名_实验方法与结果.md
```

Methodology pages MUST contain:

- Full experimental workflow
- Sampling details
- Sequencing details
- Bioinformatics workflow
- Statistical analysis
- Figure embedding
- Figure captions
- Result interpretation

---

# OBSIDIAN RULES

## Path links MUST use aliases

Correct:

```markdown
[[wiki/1.来源/xxx|来源摘要页]]
```

Wrong:

```markdown
[[wiki/1.来源/xxx]]
```

---

## Table wikilinks MUST escape pipe symbols

Correct:

```markdown
[[wiki/3.术语/fastp\|fastp]]
```

Wrong:

```markdown
[[wiki/3.术语/fastp|fastp]]
```

---

# RESULT INTERPRETATION RULES

For every result:

Explain:
1. What was compared
2. Which group increased/decreased
3. Approximate magnitude
4. Statistical significance
5. Biological meaning

NEVER exaggerate conclusions.

Use:
- 表明
- 提示
- 暗示

Avoid:
- 证明
- 完全证实

unless explicitly demonstrated.

---

# ESTIMATED VALUE RULES

When estimating values from figures:

Use:
```text
~14.3
```

And ALWAYS add:

```markdown
> ⚠️ 原文未给出具体数值，以上带 ~ 标记的数据为图中估读。
```

---

# QUERY WORKFLOW

When answering questions:

1. Read relevant wiki pages
2. Read linked pages
3. Cross-reference findings
4. Generate grounded answer
5. Update log

---

# LINT WORKFLOW

Check:
- contradictory statements
- orphan pages
- missing links
- outdated conclusions
- broken wikilinks

---

# LOGGING RULES

Operation types:

- init
- ingest
- query
- lint
- update

Format:

```markdown
## [YYYY-MM-DD] 操作类型 | 标题
```

---

# FINAL RULE

Scientific integrity is ALWAYS more important than:
- completeness
- speed
- convenience

If uncertain:
- verify
- reread
- state uncertainty

NEVER hallucinate.

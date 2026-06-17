# Writing Techniques — The Lazy Writer's Toolkit

> An amateur's Vibe Coding project — a lazy-style writing toolkit built on plain text mode. AI-assisted creation, irregularly updated with more specialized writing skills.

[中文](README.md) | [**English**](README_EN.md) | [日本語](README_JP.md) | [Русский](README_RU.md)

> Other language versions are AI-translated; the Chinese version is authoritative.

V1.0

## What Is This

A writing skill pack running within Claude Code, covering the entire novel-writing process from project initiation to final text. The skill pack consists of Markdown and JSON files.

## Recommended Setup

- Delegate `Output Proofing` to a dedicated Agent to avoid consuming the main conversation context
- Use `Prompt Enhancement` in **assisted creation mode** rather than full-auto — at minimum, tell the AI what plot points you want per chapter or per phase; output quality far exceeds zero-prompt auto-generation
- Prompt engineering remains the best tool for steering AI at this stage — spending a few minutes crafting a good chapter prompt is far more efficient than repeatedly revising the output afterwards

## Skill List

```
Outline/    Create New Book · Create Character · Plot Editing · Setting Editing · Quick Rebuild
Writing/    Router (Write-Router) · Core (Basic Writing Aid)
            Specialized (Combat [duels + warfare] · Romance · Long-form)
            Auxiliary (Prompt Enhancement · Output Proofing)
Other/      Student Essay
```

**Template Library (templates/)**: Field definitions for setting templates (character/settings/plot/project config, etc.) uniformly schematized — adding a field touches one JSON file, generation and validation stay in sync.

**Norm Library (body/Core/norms/)**: Writing norms grouped by content type into standalone files, loaded on demand by Core — prose loading -50%, adding a norm = one file + one registry line.

**Spec Data (data/)**: Bulk data (content detection / dispatch protocol / proofing checklist / foreshadowing spec / chapter tension guide, etc.) externalized here, registered via `data-registry.json` and valid only when referenced — keeps SKILL.md lean.

## Design Philosophy

- **Template-Library Driven**: Setting template fields schematized under `templates/` — adding a field touches one JSON file, generation and validation stay in sync
- **Data-Externalized Anti-Bloat**: Bulk data (vocabularies/protocols/thresholds) lives under `data/`, SKILL.md keeps only rules and flows; data files are valid only when registered in `data-registry.json`
- **Procedural Norm Library**: Core refactored into "execution engine + on-demand norm library" — group-loaded by content type, prose loading -50%, outline scenes -75%; adding a norm = one file + one registry line
- **Spec Data One-Time Load**: protocol/checklist/threshold data loaded once into working memory on first dispatch, executed from memory thereafter; re-read only on spec change/new session
- **Field-Level Precision**: field_name protocol validation + field→standard mappings + `facts` constraint blocks dispatched with data packets — OOC constrained pre-writing
- **Dual-Structure Chapter Tension**: stage-level event intensity (tension_level L1-L5) + chapter-type secondary planning (chapter_type, 7 types) — tension guides event arrangement only, never tied to writing parameters; conduction and guidance are decoupled
- **Narrative Quality Boost**: six-dimension plot checks gained a narrative-quality dimension — wave-model soft guidance, mandatory four plot-point elements, foreshadowed vs. unforeshadowed conflict types, cost exemption
- **Lazy-Friendly**: dialogue as operation — automate what can be automated, infer what can be inferred, use defaults where possible
- **Adaptive Routing**: natural language intent recognition → auto-dispatch to the correct sub-skill, no commands to memorize
- **End-to-End Pipeline**: the standard writing pipeline is driven exclusively by Write-Router (user prompt → router → Core + Specialized → Long-form → Output Proofing); skills stay loosely coupled

## Typical Workflow

```
Create New Book ──→ Create Character ──→ Edit Settings ──→ Plot Editing
                                                               │
                                                               ▼
                                                       Prompt Enhancement
                                                               │
                                                               ▼
                                                      Write-Router (Write Body)
                                                            ├→ Core (general)
                                                            ├→ Combat (combat)
                                                            └→ Romance (romance)
                                                               │
                                                               ▼
                                                Long-form → Output Proofing
```

> Workflow is not mandatory — jump in at any stage. If you already have existing settings, start directly from «Quick Rebuild».

## How to Use

After installing this skill pack in Claude Code, simply converse in natural language:

**Project Creation**
- "Create a new book" → Initialize project, collect metadata
- "Quick rebuild / Migrate old work" → Fast migration of existing settings

**Outline Planning**
- "Create character" → Add characters (with extra fast-track)
- "Edit plot" → Three-mode storyline planning
- "Edit settings" → Five-section worldbuilding refinement

**Body Writing**
- "Write main text / Polish this passage" → Route to Write-Router → Auto-detect content type → Dispatch
- "Write Chapter X" (no prompt) → Auto-dispatch Prompt Enhancement to generate writing instructions
- "Write a combat scene / Polish this fight" → Auto-dispatch Combat Specialized
- "Write a war / battle / siege" → Auto-dispatch Combat's warfare sub-group (small-to-large: command-post/staff/front-line scene slices, soft guidance)
- "Write a romantic scene / Polish this flirting" → Auto-dispatch Romance Specialized

**Foreshadowing Management**
- "This is a foreshadowing" (annotated in text) → Auto-register
- "Resolve XX foreshadowing" → Update status to resolved
- "View foreshadowing / What's still unresolved" → Full list with status diagnostics
- "What happened in Chapter X" → Cross-chapter plot recall

**Quality Check & Others**
- "Check it / Check punctuation" → Output Proofing (punctuation + structure dual-track scan, auto-correct violations)
- "Help me write an essay" → Student essay mode (K-12)

## Project Structure (After Creation)

```
{Book Title}/
├── Outline/
│   ├── Project_Info.json        ← Metadata: title / length / genre (authoritative source)
│   ├── Writing_Config.json      ← Independent polishing gear for outline & main text, per-volume overrides
│   ├── Settings/Settings.md     ← Worldbuilding / core settings / secondary settings
│   ├── Characters/Character_Archive.md ← Unified archive for all characters (Main/Supporting/Extra)
│   └── Plot/Plot_Outline.md + Prompt.md (batch-generated writing prompts)
├── Main_Text/                   ← Official chapters (Ch_XX Chapter_Title.md)
└── Extras/                      ← Side stories (Extra_Title_(X).md)
```

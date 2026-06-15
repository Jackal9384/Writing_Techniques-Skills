# Writing Techniques — The Lazy Writer's Toolkit

> An amateur's Vibe Coding project — a lazy-style writing toolkit built on plain text mode. AI-assisted creation, irregularly updated with more specialized writing skills.

[中文](README.md) | [**English**](README_EN.md)

V0.20

## What Is This

A writing skill pack running within Claude Code, covering the entire novel-writing process from project initiation to final text. The skill pack consists of Markdown and JSON files.

## Recommended Setup

- Delegate `Output Proofing` to a dedicated Agent to avoid consuming the main conversation context
- Use `Prompt Enhancement` in **assisted creation mode** rather than full-auto — at minimum, tell the AI what plot points you want per chapter or per phase; output quality far exceeds zero-prompt auto-generation
- Prompt engineering remains the best tool for steering AI at this stage — spending a few minutes crafting a good chapter prompt is far more efficient than repeatedly revising the output afterwards

## Skill List

```
Outline Skills/
├── Create New Book
├── Create Character
├── Plot Editing
├── Setting Editing
└── Quick Rebuild

Writing Skills/
├── Router
│   └── Write-Router
├── Core
│   └── Basic Writing Aid
├── Specialized
│   ├── Combat
│   ├── Romance
│   └── Long-form
└── Auxiliary
    ├── Prompt Enhancement
    └── Output Proofing

Other Skills/
└── Student Essay
```

## Design Philosophy

- **Plain-Text Driven**: All data stored as `.md` and `.json`, directly editable in any text editor
- **Dialogue as Operation**: No menus, no buttons — everything triggered through natural language
- **Lazy-Friendly**: Automate what can be automated, infer what can be inferred, use defaults where possible
- **Layered Polishing**: Outline has one polishing standard, main text has another — independently configured, with secondary confirmation before writing
- **Foreshadowing Tracking**: Auto-register on placement, auto-match on resolution, auto-alert for cross-chapter unresolved items
- **Fully Automated Writing**: Zero-prompt batch chapter prompt generation, persisted to Prompt.md for on-demand execution
- **Loose Coupling**: Each skill operates independently, Write-Router orchestrates scheduling, every writing skill focuses on its own domain
- **Adaptive Routing**: Natural language intent recognition → auto-dispatch to correct sub-skill, no commands to memorize
- **Standardized Writing Pipeline**: User prompt → Write-Router (detect + pre-allocate) → Core + Specialized skills → Long-form → Output Proofing, full pipeline driven exclusively by Write-Router

## Typical Workflow

```
Create New Book ──→ Create Character ──→ Edit Settings ──→ Plot Editing
                                                               │
                                                               ▼
                                                       Prompt Enhancement
                                                               │
                                                               ▼
                                                      Write-Router (Write Body)
                                                               │
                                                    ┌─────┬────┼────┬─┘
                                                    ▼     ▼    ▼    ▼
                                                  Core Combat Romance
                                                (general)(combat)(romance)
                                                    │     │    │
                                                    └─────┼────┘
                                                          ▼
                                                     Long-form
                                                  (Foreshadowing
                                                   / Recall)
                                                         │
                                                         ▼
                                                  Output Proofing
                                                  (Verify + Write)
```

> Workflow is not mandatory — jump in at any stage. If you already have existing settings, start directly from «Quick Rebuild».

### Standardized Writing Pipeline (Write-Router Driven)

Upon receiving user创作意图, Write-Router exclusively orchestrates execution:

```
User Prompt → Write-Router
               ├── ① Content detection & classification
               ├── ② Paragraph pre-allocation
               ├── ③ Parallel dispatch
               │      ├── general  → Core (plain-text optimization)
               │      ├── combat  → Combat Specialized
               │      └── romance → Romance Specialized
               ├── ④ Result integration + exemption collection + consistency check
               ├── ⑤ → Long-form (foreshadowing registration / plot recall)
               └── ⑥ → Output Proofing (punctuation + structure → write)
```

Each stage is auto-detected and dispatched by Write-Router — no manual triggering needed.

## How to Use

After installing this skill pack in Claude Code, simply converse in natural language:

**Project Creation:**
- "Create a new book" → Initialize project, collect metadata
- "Quick rebuild / Migrate old work" → Fast migration of existing settings

**Outline Planning:**
- "Create character" → Add characters (with extra fast-track)
- "Edit plot" → Three-mode storyline planning
- "Edit settings" → Five-section worldbuilding refinement

**Body Writing:**
- "Write main text / Polish this passage" → Route to Write-Router → Auto-detect content type → Dispatch
- "Write Chapter X" (no prompt) → Write-Router auto-dispatches Prompt Enhancement → Generate instructions → Execute
- "Help me expand on this" → Single-chapter prompt expansion
- "Batch generate chapter prompts" → Auto-generate chapters X through Y, store to Prompt.md
- "Write a combat scene / Polish this fight" → Write-Router detects combat → Auto-dispatches Combat Specialized
- "Write a romantic scene / Polish this flirting" → Write-Router detects romance → Auto-dispatches Romance Specialized

**Foreshadowing Management:**
- "This is a foreshadowing" (annotated in text) → Auto-register
- "Resolve XX foreshadowing" → Update status to resolved
- "View foreshadowing / What's still unresolved" → Full list with status diagnostics
- "What happened in Chapter X" → Cross-chapter plot recall

**Quality Check:**
- "Check it / Check punctuation" → Output Proofing (punctuation + structure dual-track scan, auto-correct violations)

**Other:**
- "Help me write an essay" → Student essay mode (K-12)

## Project Structure (After Creation)

```
{Book Title}/
├── Outline/
│   ├── Project_Info.json        ← Metadata: title / length / genre (authoritative source)
│   ├── Polish_Config.json       ← Independent polishing gear for outline & main text (light/medium/heavy)
│   ├── Settings/
│   │   └── Settings.md          ← Worldbuilding / core settings / secondary settings
│   ├── Characters/
│   │   └── Character_Archive.md ← Unified archive for all characters (Main/Supporting/Extra tiers)
│   └── Plot/
│       ├── Plot_Outline.md      ← Main storyline and volumes
│       └── Prompt.md            ← Batch-generated writing prompts (from Prompt Enhancement)
├── Main_Text/                   ← Official chapters (Ch_XX Chapter_Title.md)
└── Extras/                      ← Side stories (Extra_Title_(X).md)
```

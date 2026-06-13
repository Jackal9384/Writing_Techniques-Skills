# Writing Techniques — The Lazy Writer's Toolkit

> An amateur's Vibe Coding project, a lazy-style writing tool built on a plain text mode, created with AI assistance, and will be irregularly updated with more specialized writing skills.

[中文](README.md) | [**English**](README_EN.md)

## What Is This

A writing skill pack running within Claude Code, covering the entire novel-writing process from project initiation to main text. The skill pack content consists solely of Markdown files.

## Skill List (9 Items Total)

```
Outline Skills/
├── Create New Book     ← Set up project folder structure, collect metadata (title/length/genre)
├── Create Character    ← Template-based character creation (Main/Supporting/Extra), auto bidirectional relations
├── Plot Editing        ← Three-mode storyline planning (manual/assisted/auto), dual templates
├── Setting Editing     ← Five-section guided filling: basics / synopsis / core / worldbuilding / secondary
└── Quick Rebuild       ← Standardized migration of existing settings to WT specs, manual/auto dual mode

Writing Skills/
├── Core
│   └── Basic Writing Aid   ← Text polishing engine, seven writing rules (paragraph rhythm / indirect
│                              description / indirect character traits / scenery interleaving / dialogue
│                              enhancement / deduplication), separate outline & main text gears
├── Auxiliary
│   └── Prompt Enhancement  ← Reads plot outline → aggregates characters/settings/foreshadowing/polish config →
│                              outputs high-quality LLM-executable writing prompts, batch persists to Prompt.json
└── Specialized          ← Deep skills for specific writing scenarios (e.g. foreshadowing management,
                             plot recall), layering domain rules on top of the core polishing engine
                             to cover niche needs the general engine can't reach

Other Skills/
└── Student Essay           ← K-12 essay writing assistant, auto-detect genre / adapt grade / control word count
```

## Design Philosophy

- **Plain-Text Driven**: All data stored as `.md` and `.json`, directly editable in any text editor
- **Dialogue as Operation**: No menus, no buttons — everything triggered through natural language
- **Lazy-Friendly**: Automate what can be automated, infer what can be inferred, use defaults where possible
- **Layered Polishing**: Outline has one polishing standard, main text has another — independently configured, with secondary confirmation
- **Foreshadowing Tracking**: Auto-register on placement, auto-match on resolution, auto-alert for unresolved foreshadowing
- **Fully Automated Writing**: Supports zero-prompt batch chapter prompt generation, persistable for on-demand execution
- **Loose Coupling**: Each skill operates independently, mutually dispatched on demand, with no strong dependencies

## How to Use

After installing this skill pack in Claude Code, simply converse in natural language:

**Project Creation:**
- "Create a new book" → Initialize project, collect metadata
- "Quick rebuild" → Fast migration of existing settings

**Outline Planning:**
- "Create character" → Add characters (with extra fast-track)
- "Edit plot" → Three-mode storyline planning
- "Edit settings" → Five-section worldbuilding refinement

**Body Writing:**
- "Write main text / Polish this passage" → Invoke Basic Writing Aid to optimize text
- "Write Chapter X" (no prompt) → Auto-dispatch Prompt Enhancement → Generate writing instructions → Execute
- "Help me expand on this" → Single-chapter prompt expansion
- "Batch generate chapter prompts" → Auto-generate chapters X through Y prompts, store to Prompt.json

**Foreshadowing Management:**
- "This is a foreshadowing" (annotated in text) → Auto-register
- "Resolve XX foreshadowing" → Update status to resolved
- "View foreshadowing / What's still unresolved" → Full list with status diagnostics

**Other:**
- "Help me write an essay" → Student essay mode (K-12)
- "What happened in Chapter X" → Long-form plot recall

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
│       └── Prompt.json          ← Batch-generated writing prompts (from Prompt Enhancement)
├── Main_Text/                   ← Official chapters (Ch_XX Chapter_Title.md)
└── Extras/                      ← Side stories (Extra_Title_(X).md)
```

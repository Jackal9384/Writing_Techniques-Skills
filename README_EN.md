# Writing Techniques — The Lazy Writer's Toolkit

> An amateur's Vibe Coding project, a lazy-style writing tool built on a plain text mode, created with AI assistance, and will be irregularly updated with more specialized writing skills.

## What Is This

A writing skill pack running within Claude Code, covering the entire novel-writing process from project initiation to main text. The skill pack content consists solely of Markdown files.

## Skill List (7 Items Total)

| # | Skill                  | One-Liner                                                                 |
|---|------------------------|---------------------------------------------------------------------------|
| 1 | **Create New Book**    | Set up project folder structure, collect metadata like title/length/genre |
| 2 | **Create Character**   | Create characters using templates; new characters auto-update relationships bidirectionally |
| 3 | **Plot Editing**       | Plan the main storyline; supports serialized (5 phases) and non-serialized (4 phases) templates with flexible volume management |
| 4 | **Setting Editing**    | Edit worldbuilding, core settings, synopsis, secondary settings, etc., with guided section-by-section filling |
| 5 | **Basic Writing Aid**  | Core text polishing engine — five writing rules (paragraph rhythm / indirect character portrayal / scenery interleaving / dialogue enhancement / anti-over-polishing), distinguishing outline from main text gear |
| 6 | **Student Essay**      | Writing assistant for K-12 essays                                       |
| 7 | **Quick Rebuild**      | Standardized migration of existing old work settings to WT specifications |

## Design Philosophy

- **Plain-Text Driven**: All data stored as `.md` and `.json`, directly editable in any text editor
- **Dialogue as Operation**: No menus, no buttons — everything triggered through natural language
- **Lazy-Friendly**: Automate what can be automated, infer what can be inferred, use defaults where possible to avoid asking
- **Layered Polishing**: Outline has one polishing standard, main text has another — independently configured, with secondary confirmation when entering main text
- **Loose Coupling Between Items**: Each skill operates independently, mutually dispatched on demand, with no strong dependencies

## How to Use

After installing this skill pack in Claude Code, simply converse in natural language:

- "Create a new book" → Initiate project
- "Create character" → Add a character
- "Edit plot" → Plan the storyline
- "Edit settings" → Refine worldbuilding
- "Write main text / Polish this passage" → Invoke writing aid to optimize text
- "Help me write an essay" → Student essay mode
- "Organize existing settings" → Migrate old works

Independent auxiliary writing skill invocation is also supported for short-text needs.

## Project Structure (After Creation)

```
[Book Title]/
├── Work_Status.json          ← Outline completeness tracking
├── Outline/
│   ├── Project_Info.json     ← Metadata: title / length / genre
│   ├── Polish_Config.json    ← Independent polishing gear for outline & main text
│   ├── Settings/
│   │   └── Settings.md       ← Worldbuilding / core settings
│   ├── Characters/
│   │   └── Character_Archive.md ← Unified archive for all characters
│   └── Plot/
│       └── Plot_Outline.md   ← Main storyline and volumes
├── Main_Text/                ← Official chapters (Ch_XX Chapter_Title.md)
└── Extras/                   ← Side stories (Extra_Title_(X).md)
```
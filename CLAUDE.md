# Obsidian Notes Vault

University course notes vault organized by academic quarter. The user is a CS student at UCI.

## Structure

- Root folders are quarters: `Spring 2026/`, `Winter 2026/`
- Each course is a **single .md file** per class, using underscores in filenames (e.g., `Informatics_43.md`, `ICS_46.md`, `ICS_51.md`)
- All lectures for a course live in that one file, appended sequentially
- `Winter 2026/` contains archived zip files from prior quarter courses

## Current Courses (Spring 2026)

- **ICS 46** → Data Structures & Algorithms (C++)
- **ICS 51** → Computer Architecture (hardware, ISA, x86)
- **Informatics 43** → Software Engineering (process, requirements, principles)

## Formatting Conventions

- **Lecture headings**: `# Lecture N: Title`
- **Section headers within lectures**: `**Bold Text**` on its own line for major topics
- **Sub-sections**: Plain text on its own line, or `##` sparingly for major structural breaks
- **Content**: Bullet-point heavy, using `-` for lists with tab indentation for nesting
- **Arrows**: Use `→` for definitions, transitions, and cause/effect
- **Emphasis**: `**bold**` for key terms, section headers, and summary sections
- **Code blocks**: Used for code examples (C++ in ICS 46) and ASCII diagrams (ICS 51), with inline comments for instruction counting
- **Tables**: Markdown tables for reference charts (e.g., Big-O growth rates)
- **ASCII diagrams**: Used in ICS 51 for hardware diagrams (CPU, data path, memory layout)
- **Summary blocks**: Some lectures end with a `**Summary**` section using bold bullet headers
- **Images**: Two embed syntaxes are used — preserve both **exactly** as-is (filenames, UUIDs, size params):
  - Obsidian wikilink embeds: `![[filename.webp|size]]` or `![[filename.webp|width|widthxheight]]`
  - Markdown embeds with attachment URIs: `![name|size](attachment:uuid:file)`
  - When cleaning notes, **never modify, reformat, or remove image embeds**. Keep them in their original position relative to surrounding content. If an image appears between bullet points or paragraphs, leave it there — it was placed intentionally to illustrate the adjacent text.
- **Tone**: Informal lecture-note style — fragments, shorthand, personal annotations (e.g., "toooo many options", "that I am a dawg"), paraphrased quotes
- **Cross-course links**: Use Obsidian wikilinks `[[Filename#Heading|display text]]` to connect related concepts across courses. Format: inline with `→` arrows. **Do NOT proactively search other files for connections** — only add a wikilink when (1) the user mentions a cross-course connection in their raw notes, or (2) the connection is obvious from the new content being cleaned without needing to read other files.
- **Math symbols**: Use actual Unicode symbols instead of spelled-out names → `Σ` (sigma/sum), `Π` (pi/product), `·` (multiplication), `×` (cross multiply), `Ā` (overline for NOT), superscripts (`²`, `⁴`, `ⁿ`), subscripts (`₀`, `₁`, `ₙ`). When raw notes use `*` for multiplication (common in Markdown), use `·` instead.
- **No YAML frontmatter** on note files

## Workflow

- User appends raw lecture notes to the end of an existing course file throughout the day
- At the end of the day, user asks Claude to clean up only the **new** content
- **Only clean new raw content.** The boundary is visible in the file: cleaned content uses the formatting conventions above (bullets with `-`, `**Bold**` section headers, `→` arrows, proper lecture headings). Raw appended content looks different — typos, run-on lines, inconsistent markers, no clear lecture heading. Find that transition point and clean from there to EOF. Do not reformat content that's already cleaned.
- **Last-cleaned marker:** Each course file ends with an HTML comment like `<!-- last cleaned: end of Lecture 6 (Perfect Hashing) -->`. This marks the exact point where the previous cleaning session stopped — everything **above** the marker is already cleaned, everything **below** it (and the marker itself) is the new raw content to clean. After cleaning, **delete the old marker and append a new one at the new end of the file** describing what was just finished. If the marker is missing or appears mid-file (user added more raw notes after it), trust the visible formatting boundary instead and reset the marker to the new EOF.
- Preserve all content and meaning — do not remove personal annotations or humor
- Fix typos, improve formatting consistency, and consolidate scattered ideas
- Split content into logical lecture boundaries when multiple topics are present
- If you notice a way to improve this workflow (save tokens, reduce friction, better formatting), proactively suggest it to the user

## IMPORTANT: Auto-commit and push after every edit

After **every** edit to notes in this vault, automatically:
1. `git add -A`
2. `git commit -m "<message describing what was cleaned/changed>"` — be specific (e.g., `"Clean ICS 51 Lecture 6: Sequential logic"`, not `"Update notes"`)
3. `git push`

This is pre-authorized — do not ask for confirmation. Run the three commands as the final step of any note-cleaning task.


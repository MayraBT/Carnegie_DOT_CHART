# Hand-off: turning the TEKS Lookup into a teacher-facing IPC

Start the new chat by pasting the prompt at the bottom. Everything a new session needs is in this repository; no documents need to be uploaded again.

## 1. What exists today (coordinator version)

- **Repository:** `MayraBT/Carnegie_DOT_CHART` (public). Live page: GitHub Pages from `main`.
- **One file does everything:** `index.html` (about 1.8 MB, no build step, no framework). Item images live in `items/` (about 510 JPGs, 27 MB).
- **Maintainer notes:** `NOTES.md` explains every data constant, image naming, how to add a course, and how to refresh district data. Read it first.
- **Courses (10):** Accelerated Grade 6 (`g6`), 7th Advanced (`a7`), Grade 8 (`g8`), Algebra I MS (`a1ms`), Algebra I HS (`a1hs`), Algebra I HS Advanced (`a1hsadv`), Geometry (`geo`), Geometry Advanced (`geoadv`), Algebra II (`a2`), Algebra II Advanced (`a2adv`).
- **Views (left menu):**
  - **Calendar:** 2026-27 IPC, Q1–Q4.
  - **By lesson:** lessons with their TEKS, plus TIG links for Q1–Q2.
  - **By standard:** TEKS detail in collapsible sections that start collapsed:
    - vocabulary
    - vertical alignment
    - across courses
    - STAAR performance
    - performance across grade bands
    - where and when it is taught
  - **STAAR performance:**
    - sortable table with Texas and Dallas ISD percents
    - filters: readiness, under 50%, Dallas ISD below Texas, 1-point / 2-point / tech-enhanced / multiple choice, quarter, and full vs half credit
    - the **Vertical performance** panel with **Items across grade bands**
  - **Teaching moves:** look-fors, misconceptions, CRA, tiered questions and stems for 279 TEKS from Grade 6 through Algebra II.
  - **Full grid:** the dot chart.

## 2. What the data is and whether it can go to teachers

Decide this before anything is shared outside the coordinator group.

| Data in `index.html` | Source | Teacher-facing? |
|---|---|---|
| Lessons, TEKS marks, modules (`COURSES`, `GEO_DATA`, `A2_DATA`) | Carnegie Learning dot charts (TEKS Overview) | Likely fine inside the district; Carnegie content |
| IPC pacing and calendar | Dallas ISD 2026-27 IPCs | Yes (already teacher documents) |
| TEKS text (`TEKS`) | 19 TAC §111 | Yes, public |
| Released STAAR items and Texas percents (`PERF`, `items/g*_*.jpg`) | TEA released tests; percents from the lead4ward IQ Tool | Items are public (TEA). Percents come from a lead4ward product, so check the district's license |
| Vertical alignment (`SCAF`, `SCAF_HS`) and vocabulary (`VOCAB`) | lead4ward TEKS Scaffold and Academic Vocabulary | Check the district's lead4ward license before publishing publicly |
| **Dallas ISD item results** (`DIST`, `DIST_META`) | SchoolCity Item Analysis | **District data: keep off a public site.** Possibly show to teachers behind district sign-in, or drop it |
| **ACP Example items** (`ACP`, `items/acp_*.jpg`) | Dallas ISD Assessment Department, 2025-26 | **Coordinator-only. Replace with AI-generated items** (see section 4) |
| **TIG links** (`TIG`) | Google Drive file ids from the weekly IPCs | Teachers already have these; they need district sign-in to open |
| Teaching moves (`MOVES`) | Written for the tool, general best practice | Yes. Keep the "suggestions, not a checklist, not for evaluation" framing |

A public GitHub repo plus GitHub Pages is visible to anyone. For a teacher version with district data, consider a private repo with a district-only host such as Google Sites embedding or the district LMS, or leave district data out.

## 3. Recommended approach

1. **Keep this repo as the coordinator version.** Make the teacher version a **new repository** started from a copy of this one, so neither can break the other.
2. Strip or replace the restricted data from section 2 in the copy.
3. Re-center the design on what a teacher needs in a planning week:
   - "This week" from the IPC
   - each lesson's TEKS
   - teaching moves
   - a released or practice item
   - vocabulary
   
   Coordinator views can stay but become secondary.
4. Keep the single-file, no-build structure. It is what makes the tool easy to host and maintain.

## 4. AI-generated items for Geometry and Algebra II (replacing the ACP Example items)

Requirements for every generated item:

- **Alignment:** one TEKS per item, matched to the student expectation verb and content, including any "including…" conditions.
- **Format:** STAAR EOC style, using the STAAR item types (multiple choice, multiselect, drag and drop, inline choice, equation editor, graphing, hot spot, match table grid, number line). Mix item types across the set.
- **Answer key and rationale:** a verified key, a short rationale, and a misconception for each distractor. Solve every item twice independently and keep it only when both solutions agree.
- **Student-facing rules:**
  - Fractions are stacked, never written with a slash.
  - No vocabulary in parentheses (write "rate of change", not "rate of change (slope)").
  - Plain, test-authentic wording.
- **Graphics:** render figures, graphs and tables as SVG in the page rather than images, so they stay sharp and editable.
- **Labeling:** mark every item clearly as an AI-generated practice item, not a STAAR or ACP item.
- **Review:** the HS coordinators (Julie and Tina) review items before they reach teachers. A review/approved flag per item in the data makes this trackable.
- **Data shape:** suggested to mirror `ACP`, keyed by TEKS, with an `ai:true` flag:

  ```
  {set, q, itemType, points, correct, teks:[...], stem, choices, svg, rationale, distractors, reviewed}
  ```

## 5. Conventions to keep

- **Test in a real browser before every push:** Playwright with Chromium is preinstalled in the workspace. Check desktop at 1440 px and phone at 390 px, with no page errors and no horizontal overflow, and screenshot what changed.
- **Commit identity:** Claude, with the co-author trailer. Push to `main`.
- **Colors:** Texas is teal `#147c78` (charts use `#008c84`); Dallas ISD is purple `#7a5af5`. An expanded item turns green (`#e6f4ea`). Avoid colors with no meaning.
- **Language:** warm and plain. Teaching moves are look-fors, framed as suggestions. Update "How to use" (`HELP`) whenever a feature changes.

## 6. Open items carried over

- TIG links for Q3–Q4 once the weekly IPCs are released. Read them through the Google Drive connector, the same way as Q1–Q2.
- Dallas ISD 2024-25 results for Grade 6 and Grade 8: SchoolCity "Item Analysis – All Items", STAAR 3-8 Math 24-25, Assessment Level State. Algebra I 2025 is already loaded.
- ACP performance by TEKS for HS needs a standards-level report. The region summary reports had no TEKS per item.
- The raw source files (IPC .docx, dot charts, IQ Tool PDFs, ACP PDFs) are **not** in the repo; only the extracted data is. Re-upload a source file only if a new session needs to re-extract from it.

---

## Prompt to paste in the new chat

> I'm Mayra, Grade 6 Math Coordinator at Dallas ISD. Please add the GitHub repository MayraBT/Carnegie_DOT_CHART and read HANDOFF.md, then NOTES.md, before doing anything. That repo is my coordinator TEKS Lookup tool (Carnegie dot charts + 2026-27 IPCs for 10 courses, released STAAR items, Dallas ISD data, teaching moves).
>
> I want to re-engineer it into a teacher-facing IPC we can share with teachers. First:
>
> 1. Propose the teacher version's structure (what a teacher sees first, what stays, what goes), with a quick mockup.
> 2. Tell me which data has to be removed or replaced for teachers (HANDOFF.md section 2) and how you'd host it.
> 3. Propose how to replace the HS ACP Example items with AI-generated STAAR-style items (HANDOFF.md section 4), and show me 3 sample Geometry items with keys and rationales for my review.
>
> Don't change the coordinator repo. Build the teacher version in a new repository.

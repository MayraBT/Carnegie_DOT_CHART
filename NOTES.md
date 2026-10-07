# TEKS Lookup — maintainer notes

Single-file tool: everything lives in `index.html`, with released-item images in `items/`. The older `Accelerated_Grade_6_TEKS_Lookup.html` and `Grades_6-8_TEKS_Lookup.html` are earlier versions kept for reference.

## Courses now in the tool
Middle school: 6th Advanced (`g6`), 7th Advanced (`a7`), Grade 8 (`g8`), Algebra I MS (`a1ms`).
High school: Algebra I HS (`a1hs`), Algebra I HS Advanced (`a1hsadv`), Geometry (`geo`), Geometry Advanced (`geoadv`), Algebra II (`a2`), Algebra II Advanced (`a2adv`). All have Q1–Q4 IPCs.
Vocabulary, scaffold, IPCs and Example items are loaded for every course. `TIG`: course → lesson id → Google Drive file id of the teacher version, read from the weekly IPCs (Q1–Q2) through the Google Drive connector; add Q3–Q4 the same way when the weeklies are released.

## Where the data lives in index.html
| Constant | What it holds | Source |
|---|---|---|
| `COURSES` | per course: modules, lessons, TEKS marks (dot chart), IPC pacing and calendar | Carnegie dot chart + 2026-27 IPCs |
| `TEKS` | student expectation text | 19 TAC §111 |
| `PERF` | released STAAR items by TEKS: % correct, answer choices, `img` path | lead4ward IQ Tool (2025, 2026) |
| `DIST`, `DIST_META` | Dallas ISD results on released STAAR items (2026: Grade 6, Grade 8, Algebra I EOC; 2025: Algebra I EOC), keyed `<grade>_<year>_<item #>`: `p` % correct (full credit), `w` most-chosen wrong answer, `part` % partial credit | SchoolCity Item Analysis – All Items, Assessment Level State, 2025-26 roster |
| `SCAF` (+ `SCAF_HS`) | vertical alignment clusters | lead4ward TEKS Scaffold (Grades 6–8, Algebra I, Geometry, Algebra II) |
| `VOCAB` | academic vocabulary by TEKS (HS blocks appended right after it) | lead4ward Academic Vocabulary (Grades 6–8, Algebra I, Geometry, Algebra II) |
| `MOVES` | Teaching moves (look-fors, misconceptions, CRA, tiered questions, stems) for 279 TEKS, Grade 6–Algebra II | written for the tool; general best practice |
| `GEO_DATA`, `A2_DATA` + `Object.assign(COURSES, …)` | high school courses (on-level and Advanced share one dot chart) | Carnegie dot charts + 2026-27 IPCs |
| `ACP`, `ACP_SETS` | Dallas ISD ACP Example items 2025-26 (Semesters 1 and 2) by TEKS: key, type, `img` | Assessment Department Example Sets |
| `HELP` | How to use guides | — |
| `COURSE_ORDER`, `SAMPLE`, `FOOT`, `SUB`, `TESTS` | per-course labels and settings | — |

## Item images
`items/<grade>_<year>_Q<n>.jpg` — e.g. `g6_2025_Q19.jpg`, `gA_2026_Q12.jpg`. Every `img` in `PERF` must have a file here.
ACP Example items: `items/acp_<set>_Q<nn>.jpg` — sets `geo_s1`, `geo_s2`, `a2_s1`, `a2_s2`, `a2adv_s1`, `a2adv_s2` (2025-26); Geometry and Geometry Advanced share the geo sets. Published with the Grade 6 coordinator's approval; they are example items, not ACP items.

## To add a course, provide
1. Carnegie dot chart (TEKS Overview) for the course
2. 2026-27 IPCs (all quarters; every version if the course has more than one)
3. lead4ward TEKS Scaffold for the course
4. lead4ward Academic Vocabulary (optional)
5. Item screenshots + data, if any (Geometry and Algebra II have no STAAR EOC)

## District data
To add a year: in SchoolCity run Item Analysis – All Items with Assessment Level **State** for each test (Grade 6, Grade 8, Algebra I EOC) and save as Excel. Item numbers must match the released test in the IQ Tool. The "DISTRICT STAAR 24-25" reports are a different district test (different item order and count) and cannot be matched to the released items.

## Ground rules
- Teaching moves are look-fors and suggestions: not a complete list, not for evaluating teacher instruction or performance.
- Test every change in a real browser (desktop and phone width) before pushing.
- Fractions in student-facing text are stacked, never with a slash; no vocabulary in parentheses in student-facing text.

# TEKS Lookup — maintainer notes

Single-file tool: everything lives in `index.html`, with released-item images in `items/`. The older `Accelerated_Grade_6_TEKS_Lookup.html` and `Grades_6-8_TEKS_Lookup.html` are earlier versions kept for reference.

## Courses now in the tool
Middle school: 6th Advanced (`g6`), 7th Advanced (`a7`), Grade 8 (`g8`), Algebra I MS (`a1ms`).
High school: Algebra I HS (`a1hs`), Algebra I HS Advanced (`a1hsadv`), Geometry (`geo`), Geometry Advanced (`geoadv`, Q1 IPC only), Algebra II (`a2`, Q2–Q4 IPCs only), Algebra II Advanced (`a2adv`).
Still needed: Geometry Advanced Q2–Q4 IPCs; Algebra II on-level Q1 IPC; Semester 2 ACP Example set answer keys/standards; lead4ward TEKS Scaffold and vocabulary for Geometry and Algebra II.

## Where the data lives in index.html
| Constant | What it holds | Source |
|---|---|---|
| `COURSES` | per course: modules, lessons, TEKS marks (dot chart), IPC pacing and calendar | Carnegie dot chart + 2026-27 IPCs |
| `TEKS` | student expectation text | 19 TAC §111 |
| `PERF` | released STAAR items by TEKS: % correct, answer choices, `img` path | lead4ward IQ Tool (2025, 2026) |
| `SCAF` | vertical alignment clusters | lead4ward TEKS Scaffold |
| `VOCAB` | academic vocabulary by TEKS | lead4ward Academic Vocabulary |
| `MOVES` | Teaching moves (look-fors, misconceptions, CRA, tiered questions, stems) for 279 TEKS, Grade 6–Algebra II | written for the tool; general best practice |
| `GEO_DATA`, `A2_DATA` + `Object.assign(COURSES, …)` | high school courses (on-level and Advanced share one dot chart) | Carnegie dot charts + 2026-27 IPCs |
| `ACP`, `ACP_SETS` | Dallas ISD ACP Example items 2025-26 (Semester 1) by TEKS: key, type, `img` | Assessment Department Example Sets |
| `HELP` | How to use guides | — |
| `COURSE_ORDER`, `SAMPLE`, `FOOT`, `SUB`, `TESTS` | per-course labels and settings | — |

## Item images
`items/<grade>_<year>_Q<n>.jpg` — e.g. `g6_2025_Q19.jpg`, `gA_2026_Q12.jpg`. Every `img` in `PERF` must have a file here.
ACP Example items: `items/acp_<set>_Q<nn>.jpg` — sets `geo_s1`, `a2_s1`, `a2adv_s1` (2025-26 Semester 1). Published with the Grade 6 coordinator's approval; they are example items, not ACP items.

## To add a course, provide
1. Carnegie dot chart (TEKS Overview) for the course
2. 2026-27 IPCs (all quarters; every version if the course has more than one)
3. lead4ward TEKS Scaffold for the course
4. lead4ward Academic Vocabulary (optional)
5. Item screenshots + data, if any (Geometry and Algebra II have no STAAR EOC)

## Ground rules
- Teaching moves are look-fors and suggestions: not a complete list, not for evaluating teacher instruction or performance.
- Test every change in a real browser (desktop and phone width) before pushing.
- Fractions in student-facing text are stacked, never with a slash; no vocabulary in parentheses in student-facing text.

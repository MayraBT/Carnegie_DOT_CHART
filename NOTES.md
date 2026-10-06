# TEKS Lookup — maintainer notes

Single-file tool: everything lives in `index.html`, with released-item images in `items/`. The older `Accelerated_Grade_6_TEKS_Lookup.html` and `Grades_6-8_TEKS_Lookup.html` are earlier versions kept for reference.

## Courses now in the tool
6th Advanced (`g6`), 7th Advanced (`a7`), Grade 8 (`g8`), Algebra I MS (`a1ms`), Algebra I HS (`a1hs`).
Next: Geometry and Algebra II (Carnegie Texas Math Solution), plus ACP item screenshots from the HS coordinators.

## Where the data lives in index.html
| Constant | What it holds | Source |
|---|---|---|
| `COURSES` | per course: modules, lessons, TEKS marks (dot chart), IPC pacing and calendar | Carnegie dot chart + 2026-27 IPCs |
| `TEKS` | student expectation text | 19 TAC §111 |
| `PERF` | released STAAR items by TEKS: % correct, answer choices, `img` path | lead4ward IQ Tool (2025, 2026) |
| `SCAF` | vertical alignment clusters | lead4ward TEKS Scaffold |
| `VOCAB` | academic vocabulary by TEKS | lead4ward Academic Vocabulary |
| `MOVES` | Teaching moves (look-fors, misconceptions, CRA, tiered questions, stems) for 189 TEKS, Grade 6–Algebra I | written for the tool; general best practice |
| `HELP` | How to use guides | — |
| `COURSE_ORDER`, `SAMPLE`, `FOOT`, `SUB`, `TESTS` | per-course labels and settings | — |

## Item images
`items/<grade>_<year>_Q<n>.jpg` — e.g. `g6_2025_Q19.jpg`, `gA_2026_Q12.jpg`. Every `img` in `PERF` must have a file here.
Planned ACP naming: `geo_acp1_2026-27_Q01.jpg`, `alg2_acp2_2026-27_Q14.jpg` (template: ACP_Item_Screenshots_Template.xlsx). Confirm ACP items may be public before adding them: this repo is public.

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

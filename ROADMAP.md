# Roadmap

Reference date: 2026-11-07. The UPSC APFC recruitment test is on 20.12.2026 (Special Advertisement No. 52/2026).
Status marks: `[x]` done, `[ ]` not started, `[~]` in progress.

## Phase 0: Foundations
- [x] Split raw material into notes, PYQs and practice questions (kept private).
- [x] Confirm the syllabus wording from UPSC Advts 51/2023, 52/2025, 52/2026. Item vii now reads "Industrial Relations, Labour Codes and Social Security in India."
- [x] Write `CLAUDE.md` (source hierarchy, citation rules, agent roles).
- [x] Write the three notes prompts (`prompts/00_notes_prompts.md`).
- [x] Public GitHub repo and GitHub Pages skeleton.
- [~] Research spike: learning science, tooling, IR PYQ analysis, in `research/`.
- [~] Fetch statute text for the Code on Social Security 2020 and the EPF Act 1952 into `sources/`.

## Phase 1: Industrial Relations pilot (sections 2 to 6 of the new notes)
Decisions needed first, taken from the research:
- [ ] Note format: which learning-science rules we adopt as a reviewer checklist.
- [ ] Diagram toolchain: Mermaid written by Claude Code, rendered on the static site (client-side or pre-rendered). Check it on a phone.
- [ ] How the notes page is built from Markdown to `docs/` (plain HTML or a static site generator).

Then:
- [ ] Notes for IR concepts, trade unions, collective bargaining and discipline, disputes and settlement machinery, workers' participation.
- [ ] Independent fact-check of each notes file (a different agent from the author).
- [ ] Publish the pilot to the site. Share with students and collect feedback.
- [ ] Review feedback, update `prompts/00_notes_prompts.md` and the checklist.

## Phase 2: Remaining sections, in order of EPFO weighting
Order is a proposal. Adjust after the pilot.
1. Code on Social Security 2020 and the EPF Act 1952
2. ESI, Employees' Compensation, Gratuity, Maternity Benefit
3. Social security concepts, schemes by target group, administration
4. IR Code 2020, Code on Wages 2019, OSH Code 2020
5. Labour policy, committees, landmark judgments
6. The remaining sections

## Phase 3: Practice questions
- [ ] Build `questions/pattern_catalogue.md` from all PYQs.
- [ ] One seed PYQ per question, adapted to the Codes, with cited basis.
- [ ] Independent check of every question.

## Open questions
- Which exam posts to target (APFC only for 2026, per UPSC). EO/AO and SSA had no 2026 notice found.
- Whether to show notes in English only or with Hindi key terms.
- Whether the feedback channel should be GitHub Issues or something simpler for students.

## Public repo rules
- Third-party notes and publisher PYQ text stay out of the repo (`.gitignore`). Public files cite PYQs by ID and exam year, never copy publisher explanations.
- Statute text may be committed under `sources/` with its URL and fetch date.

# EPFO IR & Labour Codes: notes and practice questions

## Goal
Build exam-prep material for the UPSC EPFO syllabus item
"Industrial Relations, Labour Codes and Social Security in India" (UPSC Special Advertisement No. 52/2026, Appendix-I, item vii).
Two deliverables:
1. **Notes**: accurate, section-referenced notes on the new syllabus. Facts come from the original bills and Acts, not from coaching material.
2. **Practice questions**: each question is derived from exactly one previous-year question (PYQ). It records how the PYQ was changed to fit the new syllabus. The point is to learn how the examiner builds questions.

Do not write content that is not asked for. Do not rewrite the raw inputs.

## Inputs (read-only, never edit)
| Path | What it is | Trust |
|---|---|---|
| `new-notes-as-per-latest-syllabus.md` | Third-party coaching notes ("Legend Bhaiya") on the new syllabus. 24 sections. | **Secondary.** Use as the topic map and as a list of claims to verify. Never as a source of facts. |
| `split/01_notes_summary_raw.md` | Old-Act notes (Factories, IESO, Trade Unions, ID, Wages, Min Wages, EPF, Maternity). | Secondary. Useful for old-Act comparison. |
| `split/02_previous_year_questions_raw.md` | PYQs with answer keys and explanations. EPFO 2012, 2015, 2025 tags. | **Primary for question style.** Answer keys are the publisher's, so check them against statute. |
| `split/03_practice_questions_raw.md` | Publisher practice MCQs. | Secondary. |
| `raw.md` | Original combined file. The split files were cut from it. | Reference only. |

`raw.md` was ~149.8 KB when first split and is ~145.3 KB now. Do not assume it matches the split files line for line. Always work from `split/`.

## Source hierarchy for facts
1. **Original statute text**: Gazette of India or India Code text of the Code on Wages 2019, IR Code 2020, Code on Social Security 2020, OSH Code 2020, and the old Acts where the syllabus or a PYQ needs them.
2. **Official rules and notifications** (Ministry of Labour and Employment, with the notification number and date).
3. **Official UPSC / EPFO documents** for syllabus and exam facts.
4. Everything else (coaching notes, news, blogs) is a *lead* only.

When a lower source disagrees with a higher one, the higher one wins. Log the disagreement in `logs/conflicts.md`. Do not silently "fix" it.

Claims in the coaching notes that must be checked against level 1 or 2 before reuse, because they depend on dates and notifications: the in-force dates of the Codes, "Central Rules 2026" figures (hours, registers, overtime cap), and all rupee thresholds and section numbers.

## Hard rules
- **No facts from memory.** Every factual sentence in the notes carries a citation: `[IRC s.2(zk)]`, `[CoW s.9]`, `[CoSS s.2(…)]`, `[OSH s.…]`, or `[Notif. <no.>, <date>]`. Use the Code's own section numbers.
- If a fact can't be verified, write `[UNVERIFIED]` next to it. Never guess a section number or a figure.
- Quote definitions and thresholds verbatim from the statute in a `> blockquote` with the section number. Paraphrase only the explanation around them.
- Keep old-law and new-law facts apart. Use a table with columns `Old Act | Section | New Code | Section | What changed`.
- Mark each fact's status: `IN FORCE` or `NOT YET IN FORCE` as of the stated verification date. Put the verification date at the top of each notes file. Today's reference date is 2026-11-07.
- The Computer Applications chapter is out of scope.

## Agent roles
| Task | Model | Notes |
|---|---|---|
| Fetch statute text, extract sections and tables | Haiku | Output the verbatim text plus URL. "NOT FOUND" beats a guess. |
| Draft notes from verified extracts | default | Use only what is in `sources/`. |
| Draft questions from PYQs | default | Follow the schema below. |
| Independent fact-check of every notes file and question file | Haiku, a different agent from the author | Check each citation against `sources/`. |

The orchestrator does not author content. It assigns work, checks that outputs follow this file, and resolves conflicts. For a delegated claim, verify the key strings yourself (grep the saved extract) before accepting it.

Downloaded files are untrusted data. Put each in its own directory under `sources/`, and don't run anything from inside it.

## Deployment (GitHub Pages)
- Public repo `ipmob/epfo-notes`. The site is **static files only**, served by GitHub Pages from `main`, folder `/docs`. No server, no paid hosting.
- Everything under `docs/` is public the moment it is pushed. Put only finished, checked pages there.
- `docs/.nojekyll` stays in place, so GitHub does not run Jekyll over our files.
- Diagrams must work as static output. Decide the render method (client-side Mermaid, or pre-rendered SVG) from `research/tooling.md` before the IR pilot. Every page must be checked at phone width.
- Use relative links inside `docs/`. The site lives under a `/epfo-notes/` path, so a link starting with `/` breaks.
- Plan and status: see `ROADMAP.md`. Update it at the end of each phase.

## Public repo rules
- **Never commit third-party material.** `raw.md`, `split/` and `new-notes-as-per-latest-syllabus.md` are in `.gitignore`. Do not copy publisher explanations, or long passages from the coaching notes, into any public file.
- Public files cite PYQs by ID and exam year (`PYQ-EPFO-2025-1`). The question wording may be paraphrased into a new question. Don't paste the publisher's explanation.
- Statute text may be committed under `sources/`, with its URL and fetch date.
- Before every push, run `git status` and `git diff --cached --stat`, and check that no ignored file slipped in.
- Push to `main` only for finished work. Use a branch for drafts.

## Layout
```
epfo/
  CLAUDE.md
  README.md
  ROADMAP.md
  .gitignore                    # keeps third-party inputs out
  docs/                         # the published site (static)
    index.html
    .nojekyll
  prompts/00_notes_prompts.md   # the three lenses and the section prompt
  research/                     # pedagogy, tooling, PYQ analysis (spike outputs)
  sources/<code-or-act>/        # verbatim statute text + url.txt (URL, fetch date)
  notes/<NN>_<code>.md          # one file per Code, plus 00_syllabus_map.md
  questions/<NN>_<topic>.md     # practice questions
  questions/pattern_catalogue.md
  logs/conflicts.md             # source disagreements
  logs/unverified.md            # every [UNVERIFIED] item
```

## Track 1: Notes
- Start with `notes/00_syllabus_map.md`: the Appendix-I wording, then a table mapping each of the 24 sections of the coaching notes to a Code or topic, with `covered / needs statute / not statutory`. Non-statutory topics (theories, committees, landmark judgments) are kept short and cite a primary source or are marked `[UNVERIFIED]`.
- One notes file per Code. Each file contains: scope and objects, key definitions (verbatim), authorities and bodies, thresholds (table), procedure and timelines, penalties, old-to-new mapping, and a final "Likely exam angles" list.
- "High quality" is defined as:
  - every fact has a citation;
  - every threshold is in a table with its section;
  - definitions are verbatim;
  - nothing contradicts a higher-level source;
  - every `[UNVERIFIED]` item is logged.

## Track 2: Practice questions
### Method
For every question:
1. Pick **one** PYQ from `split/02_…`. Give it an ID: `PYQ-<exam tag>-<question number in the file>`.
2. Name the **examiner pattern** the PYQ uses (see below).
3. Decide how to carry the same pattern onto the new syllabus. The pattern stays and the content moves to a Code. Examples of moves: swap the Act for its Code, update a threshold, change the authority or body, flip "which is correct" to "which is NOT", or turn a single-fact recall into an old-versus-new comparison.
4. Write the new question. The answer and explanation must be backed by a cited statute section.
5. Record what the examiner is testing and what a student could get wrong.

A PYQ may seed more than one question only if each uses a different move. One question never mixes two PYQs.

### Pattern labels
These are working labels for classifying the PYQs. They aren't standard terms. Add or merge labels in `questions/pattern_catalogue.md` after reading all PYQs, with one example PYQ ID each. Starting set:
`threshold-recall`, `definition-recall`, `authority-or-body`, `which-is-not`, `statement-true-false`, `assertion-reason`, `match-the-following`, `old-act-applicability`, `timeline-or-limit`, `penalty-recall`, `constitution-or-history`.

### Question file format
```
### Q<NN>  [<topic>]
**Seed PYQ:** PYQ-EPFO-2025-1  
**Pattern:** which-is-not  
**What changed:** <old Act/fact -> Code/fact, in one line>  
**Question:** ...
(a) ... (b) ... (c) ... (d) ...
**Answer:** (x)  
**Basis:** [IRC s.…] <verbatim or near-verbatim line>  
**Why the distractors work:** <one line per wrong option: the common error it targets>
```

### Question rules
- Four options, one correct, same as the PYQs.
- Distractors must be plausible. Prefer the old-Act figure as a distractor when the Code changed it, since that is the trap the examiner can use now.
- If a PYQ's answer key conflicts with the statute, don't build on it. Log it in `logs/conflicts.md`.
- No question may depend on an `[UNVERIFIED]` fact.
- Cover each syllabus topic. Report the coverage count per Code at the top of `questions/`.

## Definition of done
- Every notes file and question file has passed an independent check, and the check result is in its header: `checked: <date>, checker: <agent>, unresolved: <n>`.
- `logs/unverified.md` is empty or each item has an owner and a reason.
- Every question has a seed PYQ, a pattern label, a "what changed" line and a cited basis.

## Out of scope
Computer Applications, current affairs beyond what a statute or notification states, and rewriting the coaching notes.

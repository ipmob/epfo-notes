# Prompts for the notes pipeline

Every notes agent gets: **the common header + Lens A + Lens B + Lens C + the section assignment**.
Agents must follow `../CLAUDE.md` (source hierarchy, citations, `[UNVERIFIED]`). Where this file and `CLAUDE.md` disagree, `CLAUDE.md` wins.

---

## Common header (paste first)

You are writing exam notes for the UPSC EPFO recruitment test. Syllabus item: "Industrial Relations, Labour Codes and Social Security in India".
The reader is a student who will learn from these notes alone, so the notes must be correct, short and easy to scan.

Inputs for your section:
- the matching section of `new-notes-as-per-latest-syllabus.md` (topic map and claims to verify, not a source of facts);
- verbatim statute text in `sources/<code-or-act>/`;
- the PYQs in `split/02_previous_year_questions_raw.md` that touch your topic.

Rules:
- Every fact has a citation to the statute section. If you can't verify it, write `[UNVERIFIED]` and log it in `logs/unverified.md`.
- Don't add a fact that is not in the sources you were given.
- Mark each rule `IN FORCE` or `NOT YET IN FORCE` as of the verification date.
- Keep it short. A fact that is not worth a student's time is left out.

---

## Lens A: relevance and importance

For your section, decide what a student must learn first.

1. Sort every fact into one of three tiers:
   - **Must-know**: asked before in the PYQs, or a core definition, number, authority or timeline;
   - **Should-know**: related to a Must-know fact, or a likely follow-up;
   - **Skip**: detail that is true but unlikely to be tested.
2. For each Must-know fact, write one line: **why the examiner cares** (for example "a threshold the Code changed", "a body with a similar name", "an exception to the general rule").
3. Show Must-know facts first. Put Should-know facts in a collapsed or secondary block. Leave Skip facts out, but list their headings under "Left out" so a reviewer can disagree.

---

## Lens B: the UPSC mindset

UPSC rarely asks for plain recall. It asks where a rule bends or changes. Read the PYQs for your topic and answer these before writing:

1. **Exceptions.** What is the general rule, and what are its exceptions, exemptions and special cases? List them as `Rule -> Exception -> Section`.
2. **What changed.** What did the old Act say, what does the Code say, and what is the exact difference (a number, a body, a definition, a coverage rule)? Use the table `Old Act | Section | New Code | Section | Change`.
3. **Look-alikes.** Which similar terms, bodies, thresholds or schemes could a student confuse? Put them side by side.
4. **Recent developments.** What has been notified, amended, launched or announced that affects this topic? Give the notification or source with its date. If you can't find a primary source, write `[UNVERIFIED]`.
5. **PYQ pattern.** For each PYQ on your topic, name the pattern (use the labels in `questions/pattern_catalogue.md` once it exists) and note what the question was really testing. Don't invent a PYQ.

Put the output of 1 to 3 in the notes. Put 4 under "Latest changes". Put 5 in `logs/pyq_patterns/<section>.md`.

---

## Lens C: EPFO weighting

This is the EPFO exam, so social-security and pension content gets more weight than a general labour-law exam would give it. Check your section for these areas and give them extra depth where the section touches them:

- **Ministry of Labour and Employment**: its role, bodies, schemes and statutory authorities;
- **Ministry of Finance**: its role in rates, approvals, funds, pension and insurance;
- **Pension and provident funds**: who pays, who administers, who decides, who approves, and the key numbers;
- **Social security**: coverage, contributions, benefits, eligibility, exemptions and the bodies that run them;
- **The bodies themselves**: EPFO, ESIC, their boards and committees, and how they relate to the two ministries.

For every item, state **which ministry or body owns it**, using the statute or the official notification. Build one table per section: `Item | Owner (ministry/body) | Section/Notification`.
If your section has no EPFO-relevant content, say so in one line and apply Lenses A and B only.

---

## Output structure (one file per section: `notes/<NN>_<slug>.md`)

1. **Header**: section name, verification date, sources used, `IN FORCE / NOT YET IN FORCE` summary.
2. **Snapshot**: five lines at most. The few things to remember if the student reads nothing else.
3. **Must-know table**: `Fact | Detail | Citation | Why the examiner cares`.
4. **Exceptions and traps**: from Lens B.1 and B.3.
5. **Old vs new**: from Lens B.2.
6. **Ministry / body map**: from Lens C.
7. **Latest changes**: from Lens B.4, each with a date and source.
8. **Should-know** (collapsed or last).
9. **Left out**: headings only.
10. **Infographic spec**: see below.

### Infographic spec
Each section ends with a data block that a later step turns into a visual. Don't draw it yourself. Give the data only:

```
infographic:
  title: <what the student learns from it>
  type: <timeline | comparison-table | flow | hierarchy | threshold-ladder | map-of-bodies>
  items:
    - label: ...
      value: ...
      cite: [section]
  highlight: <the one item the eye should land on>
```
Choose the type that fits the facts: `timeline` for dates, `comparison-table` for old vs new, `flow` for procedure, `hierarchy` for authority, `threshold-ladder` for numbers, `map-of-bodies` for ministry and body relations.

---

## Section assignment (fill in per agent)
Section: <number and title from new-notes-as-per-latest-syllabus.md>
Statute sources: <paths under sources/>
PYQ lines to read: <ranges in split/02_…>

# 001: Course content lives in structured files and is checked like code

- **Date:** 2026-09-28 (compiler and lint introduced; anti-leak rule added on 2026-09-30; written up in October 2026)
- **Status:** Adopted
- **Area:** content · platform

## Context

By the end of September 2026 the catalogue held 31 courses, each in French and English. Every course follows the same content standard: learning outcomes, concepts, prerequisites, common misconceptions, sources with verification dates, assessments, and a fixed lesson structure that ends with practice and a check for understanding.

Until then, the first courses were written as data inside the application code. That worked for a handful of courses, but nothing checked the standard automatically. A lesson without a learning objective, a quiz whose answer could be guessed, or a French lesson without its English counterpart only showed up when someone reread it. With 31 bilingual courses and one person reviewing them, rereading is not a reliable control.

A second constraint came from search. Public pages need descriptive text about each lesson, while the lesson material itself is paid. Without a check, it is easy for a public description to repeat paid content word for word.

## Options

| Option | For | Against |
| --- | --- | --- |
| A. Keep courses as data inside the application | No new tooling; already working | No automatic check of the standard; content and code changes mixed in the same files; hard to review a course on its own |
| B. A headless CMS | Comfortable editing interface; an API | One more service to run and pay for; the standard would still be checked by hand; French and English parity is not enforced |
| C. Structured source files per course, compiled and linted before release | The standard is checked on every change; full history; French and English side by side; a course can be reviewed like any other change | No visual editor; the compiler and the lint have to be written and maintained |

## Decision

Option C. The criterion that settled it: **a standard that is not checked automatically will not hold across 31 bilingual courses maintained by one person.**

How it works, at the level of principle:

- **One set of structured files per course and per language**: lesson text with a small number of typed blocks (example, misconception, takeaways, practice, check), plus course metadata.
- **A compiler turns those files into three outputs**, each for a different job:
  - a **public syllabus** for the catalogue, course pages and search (metadata, outline, objectives);
  - the **reader content** served to learners who have access (lesson material, exercises, self-check questions);
  - a **knowledge layer** kept server side for future work (typed facts, concepts, assessments). It is a foundation, not a deployed retrieval system.
- **A lint runs on every change and blocks a release on errors**: invalid structure, duplicate identifiers, French and English versions out of step (same modules, lessons and slides, in the same order), broken links between outcomes, concepts, misconceptions and assessments. It also warns about gaps against the standard: a lesson without a learning objective, a course outcome that no lesson covers, a concept used before it is introduced, fast-changing content without a verification date. Separate quality checks reject quizzes whose answer pattern gives the correct option away.
- **An anti-leak rule** keeps public search fields from repeating paid content: a public description or question that shares a long enough word sequence with the lesson material fails the lint and has to be rephrased.

Before switching, I froze the output of the existing courses and checked that the new format reproduced it, so the migration did not silently change what learners saw. The existing courses were migrated on 28 September 2026, and the courses of the 2026 programme were merged in the same format the next day.

## Consequences

- **Makes possible:** every new course goes through the same checks as the existing ones, and the public pages can carry more descriptive text without exposing paid material. In October 2026, a test was added that checks every course is integrated the same way (onboarding recommendation, certificates, checkout, catalogue visibility).
- **Costs:** there is no visual editor. Changing a comma is a reviewed change, which is acceptable for one author and would need revisiting if other authors join.
- **Does not guarantee:** pedagogical quality. The lint checks structure, not whether an explanation is clear or an example is well chosen; that is still reviewed by a person.
- **To watch:** how many errors the lint catches before release compared with errors reported by learners after release, and the time from a course subject to a published course, review included. I will look at both after the courses planned for January 2027.

## Review

*Not reviewed yet. Planned after the January 2027 courses are published.*

# Playbook 01: frame a learning platform before you build it

*Version française : [01-frame-a-learning-platform.fr.md](01-frame-a-learning-platform.fr.md)*

*Reading time: 10 min · Time to apply: half a day · Tools: none in particular*

**What you will have at the end**: a one-page brief that says who you are building for, what those people must be able to do afterwards, what you refuse to become, and how you will know it works. Content, code, design and communication follow from it.

---

## Why this playbook

I started Module on 13 March 2026 with an empty repository. As of 12 October 2026, the main branch has 705 commits. Looking back, what settles the most questions is not a technical decision: it is a one-page brief, `PRODUCT.md`, that fits in under 400 words.

That page is the reference when a decision is not obvious: should I add a "trending" course, a countdown on an offer, a free excerpt rather than a full course? The answer is often already written. Here is how to build it.

## 1. Write the job to be done, not the topic

A topic ("AI for PMs") does not tell you what to build. A job to be done does.

Phrase it like this: **"[Who] wants [to get what] because [situation], and leaves with [concrete deliverable]."**

For Module:

> Product Managers (and founders, POs, designers of digital products) want to understand AI and technology well enough to **decide, challenge engineers and ship**, because they are asked to make trade-offs they cannot always verify. They leave each course with **a deliverable built on their own product**.

The part that matters most: "a deliverable built on their own product". It dictates the structure of the lessons and the format of the exercises.

**Test**: if your sentence works just as well for a competitor, it is not finished.

## 2. Name what you refuse to become

This is the step most often skipped. List three or four products or formats your users know and that you do not want to be, and say why.

For Module:

| Anti-reference | What it rules out in practice |
|---|---|
| The dated corporate LMS | A grey, heavy, form-driven interface |
| The "guru" sales page | Countdowns, income promises, fake testimonials, avalanches of bonuses |
| The generic AI SaaS | Purple gradients, "AI-powered" everywhere, interchangeable icon grids |
| The video catalogue | Hundreds of videos, star ratings, no deliverable |

Each row becomes a design, content or communication rule. "No fake testimonials" means: feedback is quoted only with its author's consent. "No deliverable" means: no course without a deliverable.

## 3. Choose the unit of value

What does the learner actually get? Hours of video? Access? A certificate? A capability?

For Module, the unit is **the capability**: a course is about what the learner will be able to do (specify an AI feature, read an architecture, query data, run an A/B test), and it ends with a deliverable. Three consequences:

1. **The catalogue reads as a list of skills**, not as a table of contents.
2. **Duration becomes secondary**: what counts is that the capability is acquired and the deliverable produced.
3. **Value shows in the deliverable**, not in the volume of content.

**Test**: reread your first three titles. Can a PM tell their manager "I took this, here is what I produced"?

## 4. Define success, at two levels

One sentence for the visitor, one for the learner. They become your indicators.

> **Visitor**: they understand within a few seconds that the platform is made for them, start the free first course, finish it, and keep going.
>
> **Learner**: they progress without friction and come back.

From these two sentences I derive the numbers I publish every month (visits, sign-ups, completion of the free course, purchases, qualified feedback): see the [metrics page](../metrics/README.md). The step from sign-up to completion is the one that tells whether the promise is kept.

## 5. Write design principles (five at most)

Not values: **rules you can check on a screen**. Mine:

1. **Show the deliverable, not the hours.** Every screen makes the concrete result visible.
2. **Expert confidence, without emphasis.** Claims are precise and verifiable.
3. **Momentum.** The next step is always obvious: start, continue, move on to the next course in the path.
4. **Respect the learner's time.** Short, dense, easy to scan, no decorative filler.
5. **One system, two languages.** French and English are treated as equals, with no mixing and no approximation.

The fifth principle is expensive: every course exists twice, and so does every public page. I kept it because PMs often work in both languages, and a half-translated product contradicts the second principle.

## 6. Decide what is free, and why

This is a framing decision before it is a pricing decision. The question: **what must be proven before anyone pays you?**

For Module, the promise "a deliverable on your own product" must be shown to hold. So the first course is free in full: an excerpt of a few minutes would prove nothing.

This choice has a direct consequence on onboarding: the right first course has to be recommended, otherwise the proof falls flat. Hence a few questions at first sign-in (role, goal, level, available time) before a course is suggested.

## 7. Keep the page next to the code

A brief is only useful if it is read. Mine is a `PRODUCT.md` file stored with the platform's code. It is read:

- by me, before a roadmap trade-off;
- by the AI agents I produce content and code with: they receive it in context, which limits drift in tone and scope;
- by anyone who reviews a course.

Structure, in order:

```
# Product
## Users              the job to be done (step 1)
## Product Purpose    the unit of value and success (steps 3 and 4)
## Brand Personality  the voice, in three adjectives and two sentences
## Anti-references    step 2
## Design Principles  step 5
## Accessibility      what is not negotiable (for Module: WCAG 2.2 AA, in French and in English)
```

If the page goes over 400 words, it often means a question has not been settled yet.

---

## What I would do differently

I wrote `PRODUCT.md` on 1 October 2026, when the 31 courses in the catalogue already existed. It mostly served to frame the design overhaul and what came next. Written earlier, it would probably have avoided some back-and-forth on the tone and scope of the first courses. Write it before the first piece of content.

## To reproduce it yourself: 5 steps

1. **Write the job to be done** in one sentence, with the concrete deliverable at the end. Check that it does not also work for a competitor.
2. **List three anti-references** and, for each, the concrete rule it imposes.
3. **Choose your unit of value** and reread your first three titles in its light.
4. **Define success** in one sentence for the visitor and one for the learner, then derive five or six numbers to track.
5. **Decide what is free** by answering "what must be proven before anyone pays me?", then gather everything on a page of under 400 words, stored next to the code and given to every person or agent who works on the product.

## Links

- The platform: [bymodule.com](https://bymodule.com/en?utm_source=github&utm_medium=repo&utm_campaign=productlab&utm_content=playbook-01)
- The course that applies this approach to your own course project: [Design and launch an effective online course](https://bymodule.com/en/courses/launch-online-course?utm_source=github&utm_medium=repo&utm_campaign=productlab&utm_content=playbook-01)
- Related decision: [001: course content lives in structured files and is checked like code](../decisions/001-content-as-tested-structured-files.md)

*A question, a disagreement? Start a discussion in the "Questions about the method" category of the [Discussions](https://github.com/byModule/bymodule-product-lab/discussions).*

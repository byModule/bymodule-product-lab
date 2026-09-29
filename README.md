# Module Product Lab

[Module](https://bymodule.com) is a learning platform for professionals building digital products. I designed and built it through [Module](https://bymodule.io), my independent digital product practice.

This repository documents selected product decisions, engineering trade-offs, and lessons from building the platform. Production source code and paid course content remain private.

## The product

The shipped platform described in the [first case study](case-studies/01-building-bymodule-from-0-to-1.md) includes:

- A catalogue of 31 courses, each created in French and English against a structured content standard.
- Course discovery, programme pages with learning objectives and deliverables, and search.
- Accounts, a learner dashboard, learning paths, and step-level progress.
- Learning statistics and certificates.
- French and English product and learning experiences, with the language carried by the URL and changed only by the learner.
- A design system built on shadcn/ui, with light and dark themes.
- Trial access, subscriptions, and individual course purchases.
- Stripe checkout and server-side billing workflows.
- Product analytics, newsletter signup, and administration tools.

The application uses React 19, Vite, Tailwind CSS 4 and shadcn/ui, with Firebase Authentication, Firestore (EU region) and Cloud Functions. Stripe handles payments, and the public site is served through Cloudflare Pages. Vitest and Playwright cover unit and end-to-end tests.

**In progress:** a first-sign-in onboarding that recommends the most relevant course and a realistic pace, and self-service data rights (downloading all personal data, deleting the account with a grace period).

These descriptions come from my account of the product. This repository does not yet include an independent production verification or published usage results.

## My role

I am Alex Dionisio, a Senior Product Manager and founder of Module. I defined the product, designed the learner journeys, built the application and backend integrations, and created the learning content. My responsibilities also include pricing, analytics, translation workflows, and ongoing product changes.

Module is both my digital product practice ([bymodule.io](https://bymodule.io)) and the name of the learning platform ([bymodule.com](https://bymodule.com)). This Product Lab documents the learning platform.

## A decision from the first version

The platform supports trials, subscriptions, and course purchases. Public course descriptions and paid learning content serve different purposes, so I separated discovery from access to the learning material. The [case study](case-studies/01-building-bymodule-from-0-to-1.md#access-and-payments) explains the product trade-off at a high level.

## What I observed

The completed training I have observed so far took place in guided or live learning contexts. That does not establish whether learners will complete courses independently, retain what they learn, or return without an instructor.

This is a qualitative observation from my work with the product. I am not publishing completion, retention, or conversion figures here.

## What I am investigating

**Hypothesis:** contextual guidance and checks for understanding could help learners study independently. A Learning Copilot is one proposed way to test this. It is not a shipped capability.

The proposed learning sequence is:

1. **Find:** identify what to learn for a particular goal. The onboarding recommendation is the first step (in progress).
2. **Learn:** get help with an unclear concept.
3. **Check:** demonstrate understanding against a learning objective.
4. **Remember:** retain a record of demonstrated knowledge over time.

**Shipped:** before any retrieval work, I wrote a content standard and created the 31 courses of the catalogue against it. Each course defines learning outcomes, concepts, prerequisites, common misconceptions, verified sources and assessments, in French and English.

**Planned:** turn assessments into learning evidence, prepare an evaluation dataset, then implement retrieval and evaluate a copilot. These are development priorities, not validated outcomes.

## Read the case study

[Building Module from 0 to 1](case-studies/01-building-bymodule-from-0-to-1.md) covers the first version, the decisions behind it, and what I would change.

The [platform overview](architecture/platform-overview.md) describes how the platform is organised, at product-architecture level.

Product screenshots and further decision records are planned. They will be added after their factual basis and suitability for public release have been reviewed.

## How to read the status labels

| Status | Meaning |
| --- | --- |
| Shipped | Described by the builder as available in the live product. |
| In progress | Built or being built, not yet live. |
| Observed | A reported observation, with its evidence and limits stated. |
| Hypothesis | An explanation or proposed benefit that still needs testing. |
| Planned | Work intended for a future iteration. |

Public documents exclude production code, credentials, security rules, user data, complete paid courses, and operational details that could weaken the service.

## Links

- [Module: learning platform](https://bymodule.com)
- [Module: digital product practice](https://bymodule.io)
- [Alex Dionisio on GitHub](https://github.com/alxdionisio)

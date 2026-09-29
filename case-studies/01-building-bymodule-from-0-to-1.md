# Building ByModule.com from 0 to 1

**Author:** Alex Dionisio
**Role:** Founder, Product Manager, and builder
**Product:** [ByModule.com](https://bymodule.com)
**Status:** Live product
**Production source:** Private

## Scope and evidence

I built ByModule.com as a learning platform for professionals creating digital products. I designed the learner experience, implemented the application and its integrations, and created the training content through [Module](https://bymodule.io).

This case study is my account of the first version. The shipped features and qualitative observations below are reported by me. They have not been independently verified for this publication. No usage dataset or measured business outcome accompanies this document.

## The first version

Learners needed to discover a course, understand its programme, create an account, access the material, and keep track of progress. Operating the service also required billing, content administration, translation, and analytics.

I worked across those areas rather than handing the implementation to a separate engineering team. Product responsibilities included the proposition, learner journeys, access models, and measurement. Engineering work included the React frontend, Firebase services, Stripe integration, and administration interfaces. Content work covered course structure and French and English learning experiences.

## Shipped

| Area | Capabilities |
| --- | --- |
| Discovery | Public catalogue, course-programme pages, search, and newsletter signup. |
| Learning | Learner dashboard, course navigation, learning paths, step-level progress, statistics, certificates, and supporting resources. |
| Accounts | Authentication, profiles, and settings. |
| Commerce | Trials, subscriptions, individual course purchases, and Stripe checkout. |
| Operations | Administration, translation workflows, and multilingual interfaces. |
| Measurement | Event tracking across acquisition, authentication, learning, and billing. |

The frontend uses React and Vite. Firebase provides authentication, data storage, and server-side functions. Stripe supports checkout and billing.

## Access and payments

Trials, subscriptions, and course purchases create different reasons for a learner to have access to a course. I separated public course information from paid learning material and tied access to the learner's entitlement.

Billing changes are handled server-side. At a high level, a payment or subscription event updates the access state used by the product.

The trade-off was additional backend and operational work: checkout, billing state, and course access need to remain consistent. In return, the same course experience can support several commercial models.

This document describes the decision without publishing authorization rules, internal data structures, or operational access mechanisms.

## Measurement

I added tracking for actions such as signup, course starts, learning progress, completion, search, and checkout. These events provide a basis for investigating the learner journey. Their existence alone does not establish that the product has a reliable conversion or retention model.

**Planned:** define activation more precisely and examine the path from signup to first meaningful progress, continued learning, completion, and paid access. A possible activation measure is meaningful progress soon after signup, but the definition and time window still need evidence.

## Multilingual content

French and English support affects course content and navigation as well as interface labels. I built translation workflows into the operational tools so that changes could be managed across both experiences.

This adds maintenance work: a course change may require corresponding updates to translated material and its surrounding navigation.

## Observed: guided learning is the current evidence

The completed training I have observed so far happened in guided or live contexts. I do not yet have enough evidence that learners will independently discover a course, finish it, retain the knowledge, and return to the platform.

This is a qualitative observation. It does not identify the cause. Content, guidance, distribution, or a combination of these could explain the difference between guided and autonomous use.

The next iteration needs to test autonomous learning directly rather than assume that results from instructor-led training will transfer to a self-paced product.

## Hypothesis: guidance could support independent study

A proposed Learning Copilot would help learners choose a topic, get contextual explanations, check their understanding, and keep a record of demonstrated knowledge.

| Step | Proposed purpose |
| --- | --- |
| Find | Identify a relevant learning objective. |
| Learn | Help resolve an unclear concept. |
| Check | Ask the learner to demonstrate understanding. |
| Remember | Record what the learner has demonstrated over time. |

The hypothesis is that this guidance could improve independent learning and, potentially, paid conversion. Neither effect has been demonstrated. The copilot is not a shipped capability.

## Planned: structure the content before adding retrieval

My review of the catalogue identified inconsistent course depth and uneven representation of objectives, prerequisites, concepts, sources, and assessments. This is a reported editorial observation, not a published audit dataset.

I chose to prioritise those content issues before implementing retrieval-augmented generation (RAG). Retrieval needs suitable source material, and assessments need clear objectives against which answers can be checked.

The intended sequence is to define learning outcomes and concepts, improve lesson structure and assessments, prepare evaluation examples, then build and evaluate retrieval and contextual assistance. This describes planned work. It does not claim that a knowledge model, evaluation dataset, or AI system is already complete.

## What I would change

- **Define activation earlier.** Decide what meaningful initial progress looks like, then test whether that behaviour predicts continued learning.
- **Structure content earlier.** Represent objectives, prerequisites, sources, and assessments consistently before adding features that depend on them.
- **Separate progress from understanding.** Marking a step complete records a product action. It does not establish that the learner understood the material.
- **Test independent use sooner.** Recruit learners outside guided training and examine where they need help.

## Further documentation

Product screenshots, a high-level platform overview, and focused case studies on access, measurement, and content structure are planned. Future AI evaluation documents depend on actual experiments and results.

Each additional artifact will be checked for factual support and reviewed for security and intellectual-property concerns before publication. Production code, security rules, user data, and complete paid content remain private.

[Back to the Product Lab](../README.md) | [Module](https://bymodule.io) | [Alex Dionisio](https://github.com/alxdionisio)

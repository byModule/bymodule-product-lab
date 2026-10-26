# 002: The back end is a managed service (Firebase and Cloud Functions), not a custom server

*Version française : [002-managed-backend-firebase.fr.md](002-managed-backend-firebase.fr.md)*

- **Date:** 2026-03-13 (first commit of the project; written up in October 2026)
- **Status:** Adopted
- **Area:** platform

## Context

When I started Module in March 2026, I was building it alone, alongside other work, with no budget for infrastructure. The platform needed from day one what any paid learning product needs: sign-in (email link and Google), roles (learner, admin), per-learner progress, payments, and the obligations that come with personal data (export, deletion). None of this is what makes Module different, and every hour spent running a server is an hour not spent on the courses. Whatever I chose also had to keep running securely without anyone looking after it for weeks. In practice that is what happened: the project was set aside after a first version and picked up again in September 2026.

## Options

| Option | For | Against |
| --- | --- | --- |
| A. A custom back end (API server and relational database on a VPS or a hosting platform) | Full control; relational data, easy to query; no dependency on one vendor's data model | A server to secure, patch, monitor and back up; sign-in and sessions to build; a fixed monthly cost from day one |
| B. Firebase: managed authentication, a document database with security rules, and server functions for what must not run in the browser | Sign-in, data and functions hosted by the provider; pay per use, close to zero at low volume; security expressed as rules that can be tested | Lock-in to one vendor's data model and rules language; a document database is weak for reporting queries; costs follow reads and writes, so a careless data design costs money |
| C. Another managed back end built on a relational database | The same "no server" benefit, with SQL | Trade-offs close to B for this project, without a decisive advantage |

## Decision

Option B. The criterion that settled it: **the platform has to run safely without a dedicated person, so anything that is not specific to Module is bought as a service rather than built.**

How it is split, at the level of principle:

- **The browser** handles the interface and reads only what the security rules allow for the signed-in person.
- **Security rules** decide who can read or write each piece of data. Paid course content sits behind them and is never shipped in the public pages.
- **Server functions** (23 in October 2026, running in Paris) handle everything that needs a secret or must be trusted: checkout and the payment provider's notifications, role changes, certificates, transactional and lifecycle emails, data export and account deletion, and the scheduled clean-ups required by the privacy policy.
- **The front end is a static site** served by a CDN, separate from the back end, so the public pages stay fast and indexable whatever happens on the back end.

## Consequences

- **Makes possible:** one person ships payments, accounts, certificates and data rights without operating a server. Since October 2026, a separate pre-production project mirrors production, and deploying the functions to production requires an explicit approval.
- **Costs and closes off:** the data model and the rules language belong to the vendor, so leaving would mean a migration, not a switch. Reporting needs extra work because the database does not answer ad hoc relational queries. And because billing follows reads and writes, data design matters more than the size of any server: a cost review in October 2026 found avoidable charges, fixed since, and a follow-up on how often learner progress is written.
- **Requires discipline:** rules are tested against an emulator, secrets live in a secret manager rather than in code, and each production deployment is checked against the right project.
- **To watch:** infrastructure cost per active learner, and how often a product question cannot be answered without exporting data. I will look at both when the first quarterly revenue figures are published in [metrics](../metrics/README.md).

## Review

*Not reviewed yet. Planned with the first quarterly revenue figures.*

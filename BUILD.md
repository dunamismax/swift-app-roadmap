# BUILD.md: The Build Plan (template)

<!-- GUIDE: This file is the master plan. The setup agent (AGENTS.md, Setup
mode) fills it from the owner's brief, the research, and the owner's
decisions; every later session reads it in full, works the first open item,
and replaces the Handoff notes before stopping. Keep the section order. Once
written, remove "(template)" from the heading above. -->

This is the master plan for **{{APP_NAME}}**, {{ONE_SENTENCE}}. AI agent
sessions build it step by step, working under [AGENTS.md](AGENTS.md).

> **{{APP_NAME}}.** {{TAGLINE}}
> *{{LINE}}*

<!-- GUIDE: The opening paragraphs, each with a bold lead. Facts only; cite
decisions by id. Day by Word's "Name" paragraph: "Day by Word (owner decision
D1). The canonical domain is daybyword.com, registered by the owner at
Cloudflare on 2026-10-30. The repository is dunamismax/daybyword (public,
all rights reserved, D4). The support address is support@daybyword.com
(D18). Another party runs an unrelated site called DayByWord at
daybyword.org; the owner has chosen to keep the name (D2)." -->

**Name:** **{{APP_NAME}}** (owner decision D1). {{DOMAIN_SENTENCE}} The
repository is `{{REPO}}` ({{VISIBILITY_AND_LICENSE}}, D4). The support
address is **{{SUPPORT_EMAIL}}** (D18). {{NAME_RISK_SENTENCE_FROM_D2}}

<!-- GUIDE: "What it is" is the product in one paragraph: what it does, what
the person keeps doing elsewhere (if anything), the central problem it
solves, and how it solves it. End with the sentence that keeps the product
honest about its own scope. Day by Word ended with: "The catalog supports
that experience; it never becomes the experience." -->

**What it is.** {{WHAT_IT_IS}}

**First audiences.** {{FIRST_AUDIENCES_AND_WHO_COMES_LATER}}

**The founding brief.** This plan comes from the owner's description of the
product ({{BRIEF_TITLE_OR_FORM}}, {{DATE}}) and from the owner's answers to
every open decision on the same day. It carries the brief's substance:
{{BRIEF_SUBSTANCE_LIST}}. Where the owner decided differently from the
brief, the decision says so. Where this file and the brief differ, this
file is current.

<!-- GUIDE: Optional: the standing commitment from AGENTS.md's opening, in
one bold paragraph, pointing to AGENTS.md §3. Delete if there is none. -->

**{{STANDING_COMMITMENT_TITLE}}.** {{STANDING_COMMITMENT}} (AGENTS.md §3).

---

## How agents use this file

1. Read AGENTS.md first. Then read this whole file once per session. It
   holds only the plan to version 1.0; the research findings are in
   [docs/research/findings.md](docs/research/findings.md), the comparison
   with similar products in
   [docs/research/competitors.md](docs/research/competitors.md), and the
   work after 1.0 in [docs/roadmap.md](docs/roadmap.md). Read those only
   when an item points there.
2. Work the **first open `- [ ]` item in the earliest incomplete phase**,
   skipping items whose gate is still closed and items marked [OWNER] that
   are waiting on the owner personally (AGENTS.md §4). Items marked
   *(parallel-safe)* may be done in any order within their phase.
   <!-- GUIDE: name any phase allowed to run alongside others. -->
3. Build the smallest thing that meets the item well. If an item asks for
   more than 1.0 needs, rewrite it smaller and move the rest to
   docs/roadmap.md with a note, rather than building it now.
4. <!-- VARIANT: web --> A feature that exists on both the app and the web
   lands on both within the same milestone (D26).
5. Inspect the code before trusting a checkbox. Fix drift in either
   direction.
6. Tick a box only when AGENTS.md §7 (definition of done) is met. Commit the
   tick with the work, with the step id in the subject (for example
   `P5.5: ...`); related items may share a commit.
7. Complete as many items as you can in a session. Before stopping, run
   `make check`, update the **Build status** table, push, and replace the
   **Handoff notes** at the bottom. Run `make check-full` at each milestone
   and before every TestFlight build<!-- VARIANT: server --> or deploy<!--
   /VARIANT -->.
8. If an item is wrong, too large, or out of order, do not silently skip or
   delete it. Split it into sub-items (`P5.6a`, `P5.6b`), rewrite it, or
   move it to the roadmap with a note, and say what you changed in the
   Handoff notes.
9. Record history briefly where the next agent will look for it: a short,
   dated *Note* or *Result* line under the item, a decision entry only for
   a real choice, and the current state in the Handoff notes. Git keeps the
   rest.
10. When every item in a phase is ticked, move the whole phase to
    [BUILD-HISTORY.md](BUILD-HISTORY.md) in the same commit, leaving its
    heading and a one-line pointer here (AGENTS.md §8).

<!-- GUIDE: How items are written, so every later edit keeps the shape:

- [ ] **P5.5** **Bold name of the thing**: what it does, where it lives,
  and the cases or checks that prove it. Tick after <condition>, when the
  condition is not obvious.
  - [x] **P5.5a** A sub-item, when an item had to be split.
    - *Result (agent, 2026-11-01):* what was done, where it lives, and what
      was not verified, in two or three lines.
  - *Note (agent, 2026-11-01):* a dated remark that changes how the item
    is read (why it was split, what blocked it).

Rewritten items say so at the end: *(Rewritten by Dn; the rest is in the
roadmap.)* Ids are never reused or renumbered once a session has worked
from them; new items take the next free number, or a letter suffix. -->

Agents do every item themselves (D3). The markers describe the kind of work:

- **[OWNER]**: a step only the owner can take: signing in to the owner's
  own accounts, the owner's own review or choice, supplying images,
  approving legal text, or confirming a message sent in the owner's name.
  Agents prepare everything around it.
- **[GATE Dn]**: depends on decision Dn opening later.
- **[GATE DEMO]**: begins once the first usable build is on TestFlight<!--
  VARIANT: web --> and at {{DOMAIN}}<!-- /VARIANT --> (P7.{{N}}).
- **[{{PRODUCT_MARKER}}]**: {{MEANING}} (AGENTS.md §4).

---

## Build status

<!-- GUIDE: One row per phase, including Phase 0. "Items" counts top-level
items only. Milestones come from the Milestones section below. Rows for
phases moved after 1.0 say "after 1.0 (roadmap)" with dashes. The "Current
state" paragraph is replaced every session: what is finished, what is live,
and the next item in bold. At setup it says that planning is complete, which
owner steps are outstanding, and that Phase 1 (or the first open Phase 0
item) is next. -->

Update the **Done** column whenever you tick or untick a box. "Items" counts
top-level items; sub-items roll up into their parent.

| Phase | Name | Milestone | Items | Done |
|---|---|---|---|---|
| 0 | Owner foundations | — | 6 | 1 |
| 1 | Repository and toolchain | M1 Foundation | 13 | 0 |
| 2 | Product, design system, and shells | M1 Foundation | 12 | 0 |
| 3 | {{DOMAIN_MODEL_PHASE_NAME}} | M1 Foundation | {{n}} | 0 |
| 4 | {{CORE_ENGINE_PHASE_NAME}} | M1 Foundation | {{n}} | 0 |
| 5 | Persistence{{AND_CONTENT}} | M1 Foundation | {{n}} | 0 |
| 6 | Hosting at {{DOMAIN}} | M1 Foundation | 6 | 0 |
| 7 | First light | M2 First light | {{n}} | 0 |
| 8 | {{FEATURE_PHASE_A}} | M3 Version 1.0 | {{n}} | 0 |
| 9 | {{FEATURE_PHASE_B}} | M3 Version 1.0 | {{n}} | 0 |
| 10 | Apple platform integration | M3 Version 1.0 | 6 | 0 |
| 11 | The web app: install and offline | M3 Version 1.0 | 5 | 0 |
| 12 | Public pages, legal, and App Store readiness | M3 Version 1.0 | 9 | 0 |
| 13 | Quality hardening | M3 Version 1.0 | 10 | 0 |
| 14 | Version 1.0 launch | M3 Version 1.0 | 9 | 0 |
| 15– | After 1.0 | roadmap | — | — |

**Current state ({{DATE}}):** planning is complete. The owner answered
every open decision on {{DATE}} (D1–D{{LAST_D}}). The repository holds
AGENTS.md, BUILD.md, and README.md and no code. {{OUTSTANDING_OWNER_STEPS}}
**Next: {{FIRST_OPEN_ITEM}}.**

---

## The finished product

<!-- GUIDE: What "complete" means, from the person's side, in 6–10
paragraphs. Each begins with a bold phrase naming a promise in the
person's terms ("A plan you chose with confidence.", "Today, at a glance.",
"Coming back is normal.", "Private and yours."), then says concretely what
they see and can do: real screen contents, real control names, real
numbers. Mark anything that comes after 1.0 with *After 1.0:* inside the
paragraph, and end with an "After 1.0." paragraph summarizing the roadmap.
This section is what every item ultimately serves; write it before cutting
scope (Setup step S7). -->

This section defines what "complete" means. Version 1.0 delivers it
{{HOW_1_0_DIFFERS}}; the paragraphs marked *after 1.0* come later, from
[docs/roadmap.md](docs/roadmap.md). When the whole plan is done,
{{APP_NAME}} is:

**{{PROMISE_1}}.** {{WHAT_THE_USER_SEES_AND_DOES}}

**{{PROMISE_2}}.** {{...}}

**{{PROMISE_3}}.** {{...}}

**{{PROMISE_4}}.** {{...}}

**Private and yours.** {{PRIVACY_PROMISE_FROM_D8_D10_D12_D13}}

**Quiet, readable, accessible.** Text is generous, Dynamic Type works up to
the largest sizes, and VoiceOver and dark mode<!-- VARIANT: web -->, and
keyboard use on the web to WCAG 2.2 AA,<!-- /VARIANT --> are all supported.
{{WHAT_THE_PRODUCT_REFUSES_TO_BE}}

**After 1.0.** {{ROADMAP_SUMMARY}}

---

## Product principles

<!-- GUIDE: 7–12 numbered principles, each a bold imperative and one or two
sentences. They are the tie-breakers for every design and engineering
question. Draw them from the brief, AGENTS.md §3, and the decisions. Day by
Word's began "1. Choose with confidence. Recommend a few suitable plans with
reasons, and never lead with a wall of 500 plans." and ended "11. Success is
time in Scripture, not time in the app." -->

`docs/product.md` (P2.1) expands these into rules for every screen.

1. **{{PRINCIPLE}}.** {{...}}
2. **{{PRINCIPLE}}.** {{...}}
3. **{{PRINCIPLE}}.** {{...}}
4. **{{PRINCIPLE}}.** {{...}}
5. **{{PRINCIPLE}}.** {{...}}
6. **{{PRINCIPLE}}.** {{...}}
7. **{{PRINCIPLE}}.** {{...}}

### Information architecture

<!-- GUIDE: The top-level destinations, the same on iOS and the web, with
what each holds. Three to five is usual; Settings sits in a secondary area.
Day by Word: Today, Plans, Progress, with Settings from a toolbar button and
the web's header. -->

There are {{N}} destinations, the same on iOS<!-- VARIANT: web --> and on
the web<!-- /VARIANT -->, with preferences in a secondary area
(`docs/product.md`, P2.1).

| Section | Holds |
|---|---|
| **{{CORE_SECTION_1}}** | {{...}} |
| **{{CORE_SECTION_2}}** | {{...}} |
| **{{CORE_SECTION_3}}** | {{...}} |

**Settings** ({{WHERE_SETTINGS_LIVES}}) holds {{SETTINGS_CONTENTS}},
appearance and text size, export and deletion, and about.

### {{CORE_CONCEPT_TITLE}}

<!-- GUIDE: Optional but usually valuable: the one idea at the heart of the
product that agents must get exactly right, stated with a table or rules
and the mistake it prevents. Day by Word's was "The three schedule
behaviors" (Continue at my pace, Work toward a finish date, Follow the
calendar), with "the rule that prevents the serious mistake": a sequential
plan moves after a holiday, but Easter readings stay at Easter. Delete if
the product has no such concept. -->

{{CORE_CONCEPT}}

---

## Owner decisions

<!-- GUIDE: The standard decisions every Swift app needs, D1–D28, then the
product's own from D29. Keep the standard ids even when one does not apply:
write "Not applicable: <reason> (owner, date)" so cross-references stay
stable and the question visibly was considered. Each Decision cell starts
with the answer in bold, then any detail, then "(owner, date)" or
"(agent, date)" with the reason. Later revisions are appended in italics:
"*Revised by D31 (owner, 2027-01-12): ...*". Never rewrite an answer.

Options and recommended defaults to offer in the interview (Setup step S6),
with Day by Word's answer as an example:

D1 Name and identifiers. The name, tagline, line, bundle ID
  (com.<slug>.app), extensions under it (com.<slug>.app.widgets), App Group
  (group.com.<slug>.app), Xcode project and scheme, URL scheme, server
  product. DbW: Day by Word; com.daybyword.app; DayByWord; daybyword://.
D2 The name's risks. What research found (App Store collisions, domains,
  similar marks); options: keep it and accept the risk, run a trademark
  search first, or choose another. DbW: kept despite an unrelated
  daybyword.org, no search.
D3 Who builds and decides. Recommended: agents, autonomously, recording
  their decisions with reasons, limited only by honesty and the host's
  safety rules; alternative: agents propose, the owner approves listed
  kinds of change. DbW: autonomous.
D4 Repository visibility and license. Public or private; all rights
  reserved, or an open licence (MIT, Apache-2.0, GPL). Public means every
  push publishes. DbW: public, all rights reserved.
D5 Platforms and stack. App (SwiftUI app and Swift packages); App and site
  (plus a marketing, support, and privacy site: static, or rendered by a
  small Swift server); App and web app (plus a web version served by a
  Swift server, Hummingbird 2 or Vapor, sharing the core package, with
  SQLite or PostgreSQL). Recommended: the smallest that serves the brief.
  DbW: iPhone and iPad app, plus daybyword.com on Hummingbird 2 and SQLite,
  one engine in Swift.
D6 Other platforms. iPad (usually yes, at 1.0), Mac (Designed for iPad, or
  native later), Apple Watch, visionOS, Android (the web app, a Kotlin app,
  or Swift for Android later). Recommended: decide after 1.0 as [GATE D6].
D7 Minimum OS version. Recommended: the current major iOS minus one, unless
  a needed API requires the current one; built with the current Xcode. DbW:
  iOS 26 with Xcode 27.
D8 Accounts. None; optional (passkeys, Sign in with Apple, recovery codes);
  required. Recommended: none or optional; the core never needs one.
D9 Outbound messages. Email, push notifications from a server, none.
  Recommended: none at 1.0 beyond local notifications. DbW: none.
D10 Where personal data lives. On the device by default, iCloud (CloudKit)
  for sync, the product's own server only with explicit consent.
  Recommended: on the device; sync only with consent. Say whether the data
  is sensitive (health, religion, finances, location, children).
D11 Sustainability and pricing. Free; free with donations; paid upfront;
  subscription; free core with paid extras. Name what is always free. DbW:
  free core forever plus voluntary donations; no ads ever.
D12 Measurement. No analytics ever; Apple's aggregate App Store data only;
  privacy-preserving self-hosted counts; a third-party SDK (not
  recommended). DbW: no analytics, ever.
D13 Artificial intelligence in the product. None; on-device Apple
  frameworks only (Vision, Natural Language, Foundation Models); a hosted
  model with disclosure. DbW: none, with one on-device Vision exception.
D14 Visual identity. Recommended: chosen in a design session (P2.3) from
  three named directions the agent drafts from the brief, a hard stop
  until the owner says the design is final. DbW: Bookmark, Morning, Desk;
  the owner chose Morning.
D15 Images and icons. The owner supplies them from prompts agents write
  (design/image-prompts.md); agents may create them; a designer is
  engaged. DbW: the owner supplies them; agents never draw them.
D16 Territories and languages. Which App Store storefronts at launch, and
  which languages. Recommended: one storefront and English first, with
  every string localizable.
D17 Hosting (web variants). Self-hosted on the owner's server behind Caddy
  or nginx, built from main on each deploy; a platform (Fly.io, Render, a
  VPS); static hosting for a static site. DbW: the owner's Ubuntu VM,
  systemd behind the shared Caddy, built on the server, no Docker.
D18 Support contact. An address at the domain forwarded to the owner, a
  web form, or the owner's existing address.
D19 Web browsers (web variants). Recommended: current and previous major
  versions of Safari, Chrome, Firefox, and Edge; JavaScript required for
  the web app; server-rendered public pages; a plain notice for older
  browsers.
D20 Continuous integration. Manual dispatch only with make check as the
  local gate (DbW); on every push; none.
D21 Mirror. A second forge (Codeberg) as a second push URL on origin, or
  none. DbW: Codeberg.
D22 Apple Developer account. The owner's existing individual or
  organization membership, or a new one. It decides the seller name shown
  in the App Store.
D23 Server access (server variants). Recommended: standing permission for
  agents to provision, deploy, back up, and maintain this product's site,
  touching nothing else, with before-and-after checks of the owner's other
  sites.
D24 When the site starts serving (web variants). Early, marked "in
  development" with noindex until launch (DbW); only at launch.
D25 Validation and beta. Interviews or a pilot before building; or build
  straight to 1.0 with a short TestFlight beta for bugs (DbW).
D26 Build order (web app variant). Recommended: the app and the web
  together, a feature landing on both within the same milestone.
D27 Reuse from the owner's other repositories. None: everything written
  fresh (DbW); or named repositories agents may borrow from.
D28 The scope of version 1.0. The first-light slice and what 1.0 contains,
  and what is deliberately after 1.0. Recommended: the smallest product
  that keeps the central promise well (Setup step S7).
D29 onward. The product's own questions: content policies, the launch
  catalog or data set, how a signature feature behaves, what the product
  will never do. DbW's included D13 "Bible text in the product: never",
  D14 "the launch catalog", D17 "streaks: opt-in, against the reader's own
  rhythm".
-->

The owner answered every decision on {{DATE}} in the setup session. Under
D3, agents may later record new decisions, or revise an answered one only
with strong evidence, as `(agent, date)` with their reasons. They never
reverse an owner's answer on product direction without asking.
Engineering consequences go in `docs/decisions.md`.

| ID | Question | Decision |
|---|---|---|
| D1 | Name and identifiers | **{{APP_NAME}}**{{DOMAIN_IF_ANY}}, tagline "{{TAGLINE}}", line "{{LINE}}". Bundle ID **`{{BUNDLE_ID}}`**, with extensions under it (for example `{{BUNDLE_ID}}.widgets`) and the App Group `group.{{BUNDLE_ID}}`. Xcode project and scheme `{{APP_TYPE_NAME}}`; URL scheme `{{URL_SCHEME}}://`{{SERVER_PRODUCT_IF_ANY}} (owner, {{DATE}}). |
| D2 | The name's risks (Research finding {{n}}) | {{DECISION}} |
| D3 | Who builds and decides | {{DECISION}} |
| D4 | Repository visibility and license | {{DECISION}} |
| D5 | Platforms and stack | {{DECISION}} |
| D6 | Other platforms | {{DECISION}} |
| D7 | Minimum OS version | **{{MIN_OS}}**, built with Xcode {{XCODE_VERSION}} (owner, {{DATE}}). |
| D8 | Accounts | {{DECISION}} |
| D9 | Outbound messages | {{DECISION}} |
| D10 | Where personal data lives | {{DECISION}} |
| D11 | Sustainability and pricing | {{DECISION}} |
| D12 | Measurement | {{DECISION}} |
| D13 | Artificial intelligence in the product | {{DECISION}} |
| D14 | Visual identity | **Chosen in a design session** (P2.3) from three directions agents draw: **{{DIRECTION_1}}** ({{one line}}), **{{DIRECTION_2}}** ({{one line}}), and **{{DIRECTION_3}}** ({{one line}}). The owner picks or mixes them, and the choice is recorded here. The session is a hard stop: nothing further is built until the owner says the design is final (owner, {{DATE}}). |
| D15 | Images and icons | {{DECISION}} |
| D16 | Territories and languages | {{DECISION}} |
| D17 | Hosting | {{DECISION}} |
| D18 | Support contact | {{DECISION}} |
| D19 | Web browsers | {{DECISION}} |
| D20 | Continuous integration | {{DECISION}} |
| D21 | Mirror | {{DECISION}} |
| D22 | Apple Developer account | {{DECISION}} |
| D23 | Server access | {{DECISION}} |
| D24 | When the site starts serving | {{DECISION}} |
| D25 | Validation and beta | {{DECISION}} |
| D26 | Build order | {{DECISION}} |
| D27 | Reuse from the owner's other repositories | {{DECISION}} |
| D28 | The scope of version 1.0 | {{DECISION}} |
| D29 | {{PRODUCT_QUESTION}} | {{DECISION}} |

---

## Engineering foundations

<!-- GUIDE: 10–16 numbered foundations, each a bold name and a few
sentences: the architectural commitments every item builds on. P1.2 seeds
docs/decisions.md with one entry per foundation (E1, E2, ...) giving its
reasons. Keep those below that fit the variant, and replace the
placeholders with the product's own invariants (Day by Word's included "The
plan, the enrollment, and the record are separate", "An append-only event
journal", and "Calendars computed once, at compile time"). -->

`docs/decisions.md` (P1.2) records each foundation with its reasons, and
README.md has the architecture and layout.

1. **One repository, one gate.** The app<!-- VARIANT: server -->, the
   server<!-- /VARIANT -->, the Swift packages, and the tests live
   together. `make check` is the gate before every commit, and
   `make check-full` (the tours and every platform) runs at milestones and
   before releases.
2. **One core, everywhere.** `{{CORE_PACKAGE}}`, a Swift package using
   Foundation only, is the single implementation of {{WHAT_THE_CORE_HOLDS}}.
   The app, its extensions<!-- VARIANT: server -->, and the server<!--
   /VARIANT --> use it. `docs/{{CORE_SPEC}}.md` specifies it and
   table-driven cases pin it<!-- VARIANT: server -->; its tests run on macOS
   and on Linux, because the server runs it on Linux and both must give the
   same answers<!-- /VARIANT -->.
3. **{{DOMAIN_MODEL_INVARIANT}}.** {{...}}
4. **{{PERSISTENCE_FOUNDATION}}.** {{...}}
5. **Local-first.** The app works fully offline without an account
   {{EXCEPT}}. {{SYNC_STATEMENT_FROM_D10}}
6. **Swift 6 and SwiftUI throughout.** Strict concurrency, Observation, and
   a thin app target that holds UI and composition only; the project is
   generated from `apple/project.yml` by XcodeGen.
7. **Few dependencies.** {{DEPENDENCY_FOUNDATION}}
8. **{{DATES_AND_TIME_FOUNDATION}}.** {{...}}
9. **Shared design tokens.** `design/tokens.json` generates the Swift color
   assets<!-- VARIANT: web --> and the web's `tokens.css`<!-- /VARIANT -->,
   and tests check contrast and ban raw colors.
10. **Internationalized from the start.** Every interface string goes
    through a String Catalog<!-- VARIANT: server --> and the server's string
    tables<!-- /VARIANT -->, English first.
11. **Test seams.** Debug builds accept `-today YYYY-MM-DD` (and
    {{OTHER_OVERRIDES}})<!-- VARIANT: server -->, and the development server
    accepts `?today=YYYY-MM-DD`<!-- /VARIANT -->, so tests and screenshots
    can pin any state.
12. <!-- VARIANT: web --> **Modern browsers, server-rendered pages, a
    strict CSP** (D19).
13. **Privacy by construction.** {{PRIVACY_FOUNDATION_FROM_D10_D12}}

### Milestones

<!-- GUIDE: Three milestones to 1.0 is the usual shape: M1 Foundation (the
app and the server run in the chosen design; the model, core, and
persistence are correct and tested; the site is deployed marked as in
development), M2 First light (the thinnest end-to-end path, on TestFlight
and the web; opens [GATE DEMO]), and M3 Version 1.0 (every 1.0 feature,
legal pages, hardening, the beta, and launch). -->

- **M1 Foundation** (Phases 1–6): {{M1}}
- **M2 First light** (Phase 7): {{M2}} This opens [GATE DEMO].
- **M3 Version 1.0** (Phases 8–14): {{M3}}
- **After 1.0** ([docs/roadmap.md](docs/roadmap.md)): {{AFTER_1_0}}

---

## Phase 0: Owner foundations

<!-- GUIDE: Every step only the owner can take, as early as possible, each
saying how agents verify it. P0.1 is ticked at setup. Drop the items that do
not apply (no domain, no mirror) and renumber, since no session has worked
from them yet. -->

- [x] **P0.1 [OWNER]** Answer the open decisions. *(Owner, {{DATE}}: D1–D{{LAST_D}} answered in the setup session and recorded above.)*
- [ ] **P0.2 [OWNER]** Create the repository `{{REPO}}` ({{VISIBILITY}}, D4). Agents point `origin` at it and tick this once `git remote -v` shows it and the first push lands.
- [ ] **P0.3 [OWNER]** <!-- VARIANT: web --> Register **{{DOMAIN}}** ({{REGISTRAR}}). Agents tick this once `whois` or `dig` shows it registered to the owner.
- [ ] **P0.4 [OWNER]** <!-- VARIANT: web --> DNS and mail: records for `{{DOMAIN}}` and `www.{{DOMAIN}}` pointing at {{HOST}} (D17), and mail for {{SUPPORT_EMAIL}} routed to the owner (D18). Agents tick this once `dig` shows the records and MX.
- [ ] **P0.5 [OWNER]** <!-- VARIANT: mirror --> The mirror (D21): create `{{REPO}}` on {{FORGE_2}} and add its push URL to `origin`. Agents tick this once `git remote -v` shows both push URLs and one push updates both.
- [ ] **P0.6 [OWNER]** Make sure Xcode on this Mac is signed in to the Apple ID of the owner's Developer Program membership (D22). Agents verify the team in Xcode's account settings and a valid signing identity in the keychain, and do the rest (P1.12).

## Phase 1: Repository and toolchain

<!-- GUIDE: Nearly universal. Fill names and versions, and drop the server
and Linux parts for the App variant (P1.4 and the Linux half of P1.6 and
P1.11). Every later phase relies on make check existing by the end of this
phase. -->

- [ ] **P1.1** Add `.gitignore`: Xcode user data, DerivedData, `build/`, `.build/`, `.swiftpm/`, the generated `*.xcodeproj`, `apple/Config/Secrets.xcconfig`, `.env*`, `*.p8`, `*.p12`, `*.mobileprovision`, local databases, `research/`, `screenshots/`, and `.DS_Store`.
- [ ] **P1.2** Add `LICENSE` ({{LICENSE}}, D4) and create `docs/decisions.md`, a numbered, append-only decision log (E1, E2, ...) seeded with the Engineering foundations, D5's reasoning, and {{OTHER_SEED_ENTRIES}}. Each entry has a date, who decided, the decision, and **Why**; a superseded entry gets one line pointing to its successor.
- [ ] **P1.3** The packages `Packages/{{CORE_PACKAGE}}`, `Packages/{{DATA_PACKAGE}}`{{OTHER_PACKAGES}}: Foundation only<!-- VARIANT: server --> and Linux-compatible (no UIKit, SwiftUI, or other Apple-only frameworks)<!-- /VARIANT -->, each with one passing Swift Testing test. Add a static guard on their imports.
- [ ] **P1.4** <!-- VARIANT: server --> The server package `Server/` (`{{SERVER_PRODUCT}}`, {{SERVER_FRAMEWORK}} at its current release): configuration from the environment, structured logging, graceful shutdown, `/up`, and a placeholder home page, depending on the local packages by path, with tests. Record a decision entry for each dependency, including the HTML approach, and pin them all.
- [ ] **P1.5** The Apple project, `apple/project.yml` (XcodeGen): `App` ({{DEVICES}}){{EXTENSIONS}}, `AppTests`, and `AppUITests`; Swift 6 language mode, complete concurrency checking, and warnings as errors; settings in `Config/Base.xcconfig`, with the signing team in the gitignored `Secrets.xcconfig` (an example is committed); identifiers from D1; deployment target {{MIN_OS}} (D7). It links `{{CORE_PACKAGE}}` and `{{DATA_PACKAGE}}`.
- [ ] **P1.6** A pinned toolchain: `.swift-version` ({{SWIFT_VERSION}} to begin with) used on this Mac<!-- VARIANT: server -->, in CI, and on the server. `make test-linux` builds and tests the packages and the server in a Linux container when a container runtime is present<!-- /VARIANT -->.
- [ ] **P1.7** The top-level `Makefile`, with a one-line description for each target (`make help` lists them): `generate`, `build`, `test-packages`, `test-app`, `test-ui`, `run` (build, boot, install, and launch through `simctl`), `screenshot`, `lint`, `format`, `check`, `check-full`, `clean`<!-- VARIANT: server -->, `test-server`, `test-linux`, `serve`, and `deploy`<!-- /VARIANT -->{{PRODUCT_TARGETS}}.
- [ ] **P1.8** Formatting: `swift format` with a committed `.swift-format`, linted by `make check`<!-- VARIANT: web -->, and a short style note for the project's JavaScript and CSS in `docs/web.md`<!-- /VARIANT -->.
- [ ] **P1.9** `scripts/sim-destination.sh` picks the newest available iPhone simulator, and `SIM_DEVICE` overrides it. Never hard-code a device.
- [ ] **P1.10** First light on every platform: the app launches to a placeholder {{CORE_SECTION_1}}<!-- VARIANT: server -->, and `make serve` answers `/` and `/up`<!-- /VARIANT -->. Check it in the simulator<!-- VARIANT: web --> and the browser<!-- /VARIANT -->, in light and dark.
- [ ] **P1.11** CI (D20): {{CI_SHAPE}} (a macOS job running `make check`<!-- VARIANT: server -->, and a Linux job testing the packages and the server<!-- /VARIANT -->). Tick after the first hosted run passes.
- [ ] **P1.12** The TestFlight path (D22): `make archive` and `make testflight` (a signed Release archive and its upload), a first privacy manifest, the App Store Connect record with D1's bundle ID, and `docs/release.md`. An app icon is needed before App Store Connect accepts an upload (D15). Tick after the first build is processed and installs through TestFlight on the owner's device.
- [ ] **P1.13** Update `README.md`: prerequisites confirmed on this Mac, a quick start that works from a clean checkout, and the real layout.

## Phase 2: Product, design system, and shells

<!-- GUIDE: Mostly universal. P2.3 is the hard stop: say so in the item, and
nothing after it starts until the owner says the design is final. Fill P2.6
with the product's real shared components, and P2.7 and P2.8 with the real
destinations from the Information architecture. -->

- [ ] **P2.1** Write `docs/product.md`: the {{N}} sections and Settings, navigation on every platform, {{CORE_CONCEPT}} in the {{USER_NOUN}}'s words, {{KEY_FLOWS}}, tone rules (AGENTS.md §3), privacy by design, and what each surface (app, widget, notification<!-- VARIANT: web -->, web<!-- /VARIANT -->) does.
- [ ] **P2.2** A competitive teardown: {{COMPETITORS}} from their App Store listings (ratings, prices and purchases, privacy labels, features, and recent version notes) and, where a device allows, hands-on use of onboarding, {{CATEGORY_SPECIFIC_BEHAVIORS}}, widgets, and reminders. Record it in `docs/research/competitors.md`, confirm the † findings, and update the comparison.
- [ ] **P2.3 [OWNER]** The design session (D14), **a hard stop**: agents draw the three directions as screen mockups ({{THREE_KEY_SCREENS}} in each, light and dark, at phone<!-- VARIANT: web --> and desktop<!-- /VARIANT --> widths, with placeholders where images would go, D15), show them to the owner, and then **stop and wait**. Nothing else is built until the owner has chosen, refined the choice over as many rounds as the owner wants, and said the design is final. Then agents record the choice in D14 and write `docs/design.md` and `design/tokens.json`. Image needs go to `design/image-prompts.md` (D15).
- [ ] **P2.4** Generate the Swift color assets<!-- VARIANT: web --> and the web's `tokens.css`<!-- /VARIANT --> from `design/tokens.json` by a script, so they cannot drift. Test that every text pair in `docs/design.md` meets WCAG AA in light and dark, and that no view<!-- VARIANT: web --> or stylesheet<!-- /VARIANT --> writes a raw color.
- [ ] **P2.5** Type: system faces for the interface, and at most one openly licensed custom face if D14 calls for one. A type scale{{SIGNATURE_SIZE}} that scales with Dynamic Type to AX5<!-- VARIANT: web --> and in `rem` on the web<!-- /VARIANT -->.
- [ ] **P2.6** Shared components on every platform: {{COMPONENT_LIST}}; and empty, loading, offline, and error states. Statuses always carry words or symbols as well as color, and every component reads well with VoiceOver.
- [ ] **P2.7** The iOS shell: {{NAVIGATION_SHAPE}} (for example three tabs, {{CORE_SECTION_1}}, {{CORE_SECTION_2}}, and {{CORE_SECTION_3}}, each with its own `NavigationStack`), and Settings from a toolbar button. Restore the selected tab and paths on relaunch, and route every destination through an `AppRoute` with the `{{URL_SCHEME}}://` scheme.
- [ ] **P2.8** <!-- VARIANT: web --> The web shell: server-rendered layouts with header navigation ({{SECTIONS}}, Settings); a footer with {{FOOTER_CONTENTS}}; semantic HTML; the project's own JavaScript modules; a strict CSP and Permissions Policy; responsive pages from 320 px to a wide desktop; and a plain notice for unsupported browsers (D19).
- [ ] **P2.9** Write `docs/urls.md`: readable, stable, shareable addresses for every destination (<!-- VARIANT: web -->`/{{section}}`, `/{{things}}/<id>`, ...<!-- /VARIANT -->), mirrored in the app's routes for deep links<!-- VARIANT: web --> and later universal links<!-- /VARIANT -->. Route every placeholder by it.
- [ ] **P2.10** Every interface string through a String Catalog<!-- VARIANT: server --> and the server's string tables<!-- /VARIANT -->, English only for now, with tests that find untranslated text and missing keys.
- [ ] **P2.11** The Settings shell: appearance (Automatic, Light, Dark), {{TEXT_SIZE_OR_OTHER_DISPLAY_SETTING}}, about{{ABOUT_CONTENTS}}, and the running version (the build<!-- VARIANT: server --> or the deployed commit<!-- /VARIANT -->).
- [ ] **P2.12** Tours: an iOS UI test<!-- VARIANT: web -->, and browser tests through WebDriver (a decision entry records the client)<!-- /VARIANT -->, that visit every section in light and dark and save screenshots to gitignored folders. `make check-full` runs them.

## Phase 3: {{DOMAIN_MODEL_PHASE_NAME}}

<!-- GUIDE: The product's nouns, as types in the core package, before any
behavior. Name the phase after the domain (Day by Word's: "Scripture
references"; a fitness app's might be "Exercises and workouts"; a budgeting
app's "Accounts, money, and categories"). Typical items:
- the vocabulary: a short document defining each concept, with examples;
- the value types, with validation, and table-driven tests on macOS (and
  Linux for server variants), including every way an input can be wrong;
- reference data the product depends on, with its source and rights;
- parsing and formatting: one strict storage format, and display and
  spoken (VoiceOver) forms for people;
- computed facts the interface will show (Day by Word: verse sets for
  coverage, word counts for workload estimates);
- the phase's owning document, written briefly at the end.
Write 5–9 items. -->

All of this lives in `{{CORE_PACKAGE}}`, with table-driven tests that run on
macOS<!-- VARIANT: server --> and Linux<!-- /VARIANT -->. {{SCOPE_SENTENCE}}

- [ ] **P3.1** {{MODEL_ITEM}}
- [ ] **P3.2** {{MODEL_ITEM}}
- [ ] **P3.3** {{MODEL_ITEM}}
- [ ] **P3.4** {{FORMAT_AND_DISPLAY_ITEM}}: one strict, documented format for storage, and a formatter that gives the display form and the spoken form, with table-driven cases, including every way an input can be wrong.
- [ ] **P3.5** {{COMPUTED_FACTS_ITEM}}
- [ ] **P3.6** Write `docs/{{MODEL_DOC}}.md`, briefly: {{WHAT_IT_COVERS}}, and the sources of any reference data.

## Phase 4: {{CORE_ENGINE_PHASE_NAME}}

<!-- GUIDE: The product's behavior, specified, then pinned by cases, then
coded, in that order. Day by Word's "The reading engine" had: the
specification (docs/engine.md) with a worked example and the person's plain
wording for every rule; a JSON case format and runner using invented
fixtures; a civil-date type; an append-only event journal with a
deterministic fold, undo as an event, and duplicate events as no-ops; one
item per behavior; the return-after-a-break flow with previews; changing
settings without losing history; progress measures; and reminder rules
(with daylight saving and travel cases). Write one item per rule or
behavior a person would recognize, 6–12 items. -->

`{{CORE_PACKAGE}}` is the only implementation (Engineering foundation 2).
The specification comes first, then the cases, then the code.

- [ ] **P4.1** Write `docs/{{CORE_SPEC}}.md`, the specification, for what 1.0 needs: {{CONCEPTS_AND_RULES}}. Each rule has a worked example and the plain wording the {{USER_NOUN}} sees.
- [ ] **P4.2** The case format and runner: table-driven JSON cases ({{FIXTURE}}, {{INPUT}}, {{EXPECTED_OUTPUT}}) in `{{CORE_PACKAGE}}`'s tests, using invented fixtures, never real {{USER_NOUN}} data<!-- VARIANT: server -->. The same cases run on macOS and on Linux<!-- /VARIANT -->.
- [ ] **P4.3** {{BEHAVIOR_ITEM}}
- [ ] **P4.4** {{BEHAVIOR_ITEM}}
- [ ] **P4.5** {{BEHAVIOR_ITEM}}
- [ ] **P4.6** {{BEHAVIOR_ITEM}}
- [ ] **P4.7** {{NOTIFICATION_OR_REMINDER_RULES_ITEM}}: from {{INPUTS}}, compute the next fire times, honoring {{OPTIONS}} and iOS's limit of 64 pending local notifications. Cases cover daylight saving changes and travel across time zones.

## Phase 5: Persistence{{AND_CONTENT}}

<!-- GUIDE: Where data lives and how it gets there. Typical items:
- the store (SwiftData models, or SQLite through the data package's own
  wrapper) with versioned migrations and a test that opens old data;
- the repository layer the app uses, so views never touch storage;
- export of everything the person has (JSON, and CSV where useful) and
  deletion of everything, at any time (D10);
- the App Group container if widgets or intents share data;
- a content pipeline if the product ships content: a source format, a
  compiler that validates and refuses bad input, a sources and rights
  registry, and integration with the app bundle (Day by Word's Phase 4,
  "The catalog");
- sync only if D10 puts it in 1.0 (usually after 1.0).
5–9 items. -->

- [ ] **P5.1** {{STORE_ITEM}}
- [ ] **P5.2** {{MIGRATIONS_ITEM}}
- [ ] **P5.3** {{REPOSITORY_LAYER_ITEM}}
- [ ] **P5.4** Export and deletion: every piece of the {{USER_NOUN}}'s data exported as JSON{{AND_CSV}}, and deleted completely, with tests (D10).
- [ ] **P5.5** {{CONTENT_OR_SHARED_CONTAINER_ITEM}}

## Phase 6: Hosting at {{DOMAIN}}

<!-- VARIANT: web -->
<!-- GUIDE: For a server variant, the steps below (Day by Word's Phase 7).
For a static site, keep P6.1, a simpler P6.2 (build and publish), P6.4,
P6.5, and P6.6. Deleted entirely for the App variant: then renumber the
later phases, since no session has worked from them yet. -->

The site goes live {{WHEN_FROM_D24}}. Agents provision and deploy under
D23's standing permission and its conditions (AGENTS.md §9).

- [ ] **P6.1** Write `docs/deploy.md`: {{LAYOUT}} (releases, `current`, shared storage, and an environment file for secrets, root-owned, mode 600); the system user; a free port (check first); the pinned Swift toolchain on the server; the systemd unit with filesystem protections; the {{WEB_SERVER}} site with `www` redirecting permanently to the apex; security headers; logs; and rollback.
- [ ] **P6.2** `make deploy` (`deploy/deploy.sh`): build a release from a clean `git archive` of `origin/main` with the pinned toolchain (with the package and server tests), install it, run migrations, boot-check it on a spare port, switch `current`, restart, check `/up`, and restore the previous release on any failure. The checkout is never a web root.
- [ ] **P6.3** Provision the server as `docs/deploy.md` says (D23): record how the owner's other sites answer, archive the web server's configuration, add this site beside the others without editing any other, and check the other sites again afterward.
- [ ] **P6.4** The first deploy (after P0.4), then check every name: {{DOMAIN}} serves over HTTPS, `www` redirects permanently with the path kept, and the headers are right.
- [ ] **P6.5** A post-deploy check (`make check-live`): status codes, redirects, TLS, security headers, secure cookies, and no requests to other hosts. `make deploy` runs it and prints only failures.
- [ ] **P6.6** Until launch (P14.5): `robots.txt` disallows crawling, every page carries `noindex`, and a quiet line says the site is in development (D24).

## Phase 7: First light

<!-- GUIDE: The thinnest end-to-end path a person can use, on TestFlight
(and the web), built on Phases 3–6 (D28). Write one item per step of that
path, in the order a person meets them, then the essentials around it
(notifications if the product depends on them, a first Settings with
export and deletion, offline), and end with the ship item. Day by Word's
had: three plans, starting a plan, Today, marking with undo, opening a
reading elsewhere, physical Bible mode, the return flow, reminders, a
widget, the web, offline, progress, Settings, and "Ship first light".
8–14 items. -->

The first usable release: {{FIRST_LIGHT_SLICE}}, in the app<!-- VARIANT:
web --> and on the web<!-- /VARIANT -->. {{WHAT_MATTERS_MOST_HERE}}

- [ ] **P7.1** {{FIRST_STEP_OF_THE_CORE_PATH}}
- [ ] **P7.2** {{NEXT_STEP}}
- [ ] **P7.3** {{NEXT_STEP}}
- [ ] **P7.4** {{NEXT_STEP}}
- [ ] **P7.5** {{NOTIFICATIONS_ITEM_IF_CORE}}: local notifications over P4.7 in a rolling window, with actions {{ACTIONS}}; permission is asked only when the {{USER_NOUN}} turns a reminder on, and turning reminders off never limits the app.
- [ ] **P7.6** <!-- VARIANT: web --> The web: {{WEB_COUNTERPART_OF_THE_CORE_PATH}}, computed by `{{CORE_PACKAGE}}` on the server, with {{WHERE_WEB_DATA_LIVES_FROM_D10}}.
- [ ] **P7.7** Offline: the app works fully in airplane mode{{AND_WHAT_THE_WEB_DOES}}, and says clearly when it is offline.
- [ ] **P7.8** Settings, first version: {{PRODUCT_SETTINGS}}, appearance, export of all personal data, delete all data, about, and version.
- [ ] **P7.9** Ship first light: run `make check-full`, then an internal TestFlight build<!-- VARIANT: web -->, and {{DOMAIN}} deployed with the same features<!-- /VARIANT -->. This opens [GATE DEMO].

## Phase 8: {{FEATURE_PHASE_A}}

<!-- GUIDE: Phases 8 and 9 (add or merge phases as needed) hold the rest of
1.0's features, grouped by what a person would call them ("Choosing a
plan", "Progress and history", "Paper and calendars"). Each item is one
feature, small enough for a session, stated as what the person sees. Add a
one-paragraph introduction when the phase needs context (what is in scope,
what waits for the roadmap). A content-heavy product may need a phase that
builds its launch content and may run alongside others, as Day by Word's
"The launch catalog (parallel with Phases 9–17)" does. -->

- [ ] **P8.1** {{FEATURE_ITEM}}
- [ ] **P8.2** {{FEATURE_ITEM}}
- [ ] **P8.3** {{FEATURE_ITEM}}

## Phase 9: {{FEATURE_PHASE_B}}

- [ ] **P9.1** {{FEATURE_ITEM}}
- [ ] **P9.2** {{FEATURE_ITEM}}
- [ ] **P9.3** {{FEATURE_ITEM}}

## Phase 10: Apple platform integration

<!-- GUIDE: Keep what 1.0 needs and move the rest to the roadmap. -->

- [ ] **P10.1** The App Group and the capabilities the extensions need, registered through Xcode's automatic signing on the owner's account (D22).
- [ ] **P10.2** Widgets: {{WIDGET_FAMILIES_AND_CONTENTS}}, with interactive {{WIDGET_ACTION}} through an App Intent writing through the App Group, and an obvious way to undo in the app.
- [ ] **P10.3** App Intents and App Shortcuts: {{SHORTCUT_PHRASES}}, working with Siri, Spotlight, and the Action button.
- [ ] **P10.4** Notification actions and grouping{{NOTIFICATION_DETAILS}}, exercised on a device or the simulator, not only in unit tests.
- [ ] **P10.5** iPad: a sidebar layout and readable widths, and a check that it runs on a Mac with Apple silicon as an iPad app (D6).
- [ ] **P10.6** Universal links<!-- VARIANT: web --> from {{DOMAIN}}'s addresses (docs/urls.md) through associated domains<!-- /VARIANT -->{{OR_OTHER_INTEGRATION}}.

## Phase 11: The web app: install and offline

<!-- VARIANT: web -->
<!-- GUIDE: For the web-app variant. A static site keeps only P11.4 and
P11.5 (merged into Phase 12); the App variant deletes the phase. -->

- [ ] **P11.1** An installable web app: the manifest (name, icons from the owner's files, colors from the tokens), checked through Add to Home Screen on iPhone and installation on Android.
- [ ] **P11.2** Offline, finished: a service worker keeps the assets and {{WHAT_TO_CACHE}}, queues changes made offline, and never caches another person's data.
- [ ] **P11.3** Keyboard use throughout, and sharing through the Web Share API with a copy-link fallback.
- [ ] **P11.4** Write `docs/browsers.md`: the support matrix (D19) and what was tested in each browser.
- [ ] **P11.5** Browser tests for every web flow at phone and desktop widths, with the other supported browsers checked by hand at each release.

## Phase 12: Public pages, legal, and App Store readiness

- [ ] **P12.1** <!-- VARIANT: web --> The home page: what {{APP_NAME}} is ("{{LINE}}"), what it actually does today (never promised features), and the way in, with the App Store link once it exists.
- [ ] **P12.2** The support page<!-- VARIANT: web --> (`/support`)<!-- /VARIANT -->: {{SUPPORT_EMAIL}}, how to report a problem, what is collected, and frequently asked questions. App Store Connect needs its URL.
- [ ] **P12.3 [OWNER]** The privacy policy and terms, drafted in `docs/legal/` from the real data flows ({{DATA_FLOWS_SUMMARY}}, D10, D12). The owner approves them before they are published. App Store Connect needs the privacy policy's URL.
- [ ] **P12.4** <!-- VARIANT: web --> The cookie and storage statement, inside the privacy page: every cookie and browser storage key, what it holds, and why it is needed.
- [ ] **P12.5** The accessibility statement: the standard met (WCAG 2.2 AA on the web; Dynamic Type, VoiceOver, and contrast in the app), what was tested, known gaps, and how to report a barrier.
- [ ] **P12.6** The App Store package in `docs/app-store/`: the privacy manifest with accurate required-reason declarations; the privacy label ({{EXPECTED_LABEL}}); age rating; export compliance; name, subtitle, description, and keywords; support and privacy URLs; review notes; and screenshots automated by UI tests in light and dark at the required sizes.
- [ ] **P12.7** {{IN_APP_PURCHASES_OR_DONATIONS_FROM_D11}} *(delete if D11 has nothing to sell)*
- [ ] **P12.8** Icons from the owner's files (D15) at every required size<!-- VARIANT: web -->; favicons, custom 404 and 500 pages, and a sitemap<!-- /VARIANT -->.
- [ ] **P12.9** <!-- VARIANT: web --> A link check in `make check`: every internal link resolves, pages validate as HTML, and nothing loads from another host.

## Phase 13: Quality hardening

- [ ] **P13.1** VoiceOver on every screen (labels, traits, reading order, values read naturally)<!-- VARIANT: web --> and screen readers on the web<!-- /VARIANT -->.
- [ ] **P13.2** Dynamic Type at AX5 on every screen; Bold Text, Reduce Motion, Reduce Transparency, and Increase Contrast; contrast in both appearances.
- [ ] **P13.3** <!-- VARIANT: web --> The web at 200% text and 400% zoom (320 CSS pixels) without loss; forced colors; keyboard alone with visible focus and a skip link.
- [ ] **P13.4** Time: daylight saving changes, travel across time zones, midnight, leap days, and a device clock set wrong, tested end to end{{FOR_WHICH_FEATURES}}.
- [ ] **P13.5** An airplane-mode test of every offline feature<!-- VARIANT: web -->, in the app and on the web<!-- /VARIANT -->.
- [ ] **P13.6** Performance: cold launch time, scrolling on the largest realistic data set ({{SIZE}}), memory, and battery during {{BACKGROUND_WORK}}, measured with Instruments on a device and recorded in `docs/performance.md`.
- [ ] **P13.7** Security: secrets only in the Keychain or the server's environment file, suitable file-protection classes, no secrets in the app binary<!-- VARIANT: server -->, a strict CSP with no `unsafe-*`, rate limits and request-size limits on every form and API call, secure cookies, and dependency updates reviewed for advisories<!-- /VARIANT -->.
- [ ] **P13.8** {{FIELD_TEST_ITEM}} (for example a week of real reminders on a device, with misses investigated).
- [ ] **P13.9** UI<!-- VARIANT: web --> and browser<!-- /VARIANT --> tests for every critical flow in M2 and M3.
- [ ] **P13.10** A full review of every user-facing string against AGENTS.md §3: tone, honesty, no dark patterns, {{PRODUCT_SPECIFIC_CHECKS}}.

## Phase 14: Version 1.0 launch

- [ ] **P14.1** {{AUDIT_ITEM}}: a final audit of {{RIGHTS_PRIVACY_OR_COMPLIANCE}} against AGENTS.md §6, recorded in `docs/launch-audit.md`.
- [ ] **P14.2** Every [{{PRODUCT_MARKER}}] item at its required level. *(delete if the product has no such marker)*
- [ ] **P14.3 [OWNER]** The beta (D25): {{BETA_SHAPE}} on external TestFlight (with Apple's beta review)<!-- VARIANT: web --> and on the web<!-- /VARIANT -->, with testers the owner invites. Agents triage feedback into items and fix what it finds; feedback is anonymized before it enters the repository.
- [ ] **P14.4** Submit version 1.0 for App Review in {{STOREFRONTS_FROM_D16}}, confirming with the owner first where the host requires it. Tick when it is approved and released.
- [ ] **P14.5** <!-- VARIANT: web --> Open {{DOMAIN}} to search engines (remove P6.6's notice, `noindex`, and the `robots.txt` block) and submit the sitemap, on release day.
- [ ] **P14.6 [OWNER]** Announce {{APP_NAME}} where the owner chooses.
- [ ] **P14.7** Tag `v1.0.0` and record what shipped in the Handoff notes.
- [ ] **P14.8** {{MORE_STOREFRONTS_OR_LANGUAGES_FROM_D16}}
- [ ] **P14.9** The after-launch learning loop (D12, D25) in `docs/learning.md`: the support inbox routine, {{OTHER_SIGNALS}}, and a regular note on what people are saying, folded into this plan as items.

## After 1.0

<!-- GUIDE: Name what docs/roadmap.md holds, phase by phase, in one or two
sentences. The roadmap's phases are numbered from 15 and written to the
same standard as these, so moving one back here after 1.0 is a cut and
paste. -->

Phases 15 onward are in [docs/roadmap.md](docs/roadmap.md): {{ROADMAP_PHASES}}.
Sessions read it only when Phase 14 is finished or an item points there.

---

## Handoff notes

<!-- GUIDE: Replaced each session, never appended to; under 25 lines. Each
bullet starts with a bold label: the date and what was finished, "Next:"
with the item ids in order, what is half-done or blocked, "Surprises:"
(facts the next session would otherwise rediscover the hard way), and what
is waiting on the owner. At setup, write the first entry: the plan is
written, which [OWNER] steps are outstanding, and the first item. -->

*Replaced each session; keep under 25 lines. History lives in Git.*

- **{{DATE}}:** {{WHAT_WAS_DONE}}
- **Next: {{ITEM_IDS_IN_ORDER}}.**
- **Waiting on the owner:** {{OWNER_STEPS}}

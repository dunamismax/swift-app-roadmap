# Working on {{APP_NAME}}

<!-- SETUP:BEGIN
Everything from this line to SETUP:END is the setup procedure. It exists only
while this repository is still the Swift App Roadmap template. The setup
agent deletes the whole block, markers included, as its last writing step
(Setup step S11).
-->

## Setup mode: turning this template into a product plan

**This repository is still a template.** You know it is when this block is
present, or when BUILD.md's first heading still says `(template)` or any
file still contains `{{`. In setup mode you do **not** run the session loop
in §2. Your job is to take the owner's app idea and turn BUILD.md,
AGENTS.md, and README.md into a complete, honest plan that future agent
sessions can build from, one checkbox at a time, until version 1.0 ships.

### How the template works

- **BUILD.md** is the master plan: what the finished product is, the
  owner's decisions, the engineering foundations, and ordered phases of
  checkbox items (`P3.4`) to version 1.0, ending in Handoff notes. Every
  later session reads it in full, works the first open item, ticks it with
  the work, and replaces the Handoff notes before it stops.
- **AGENTS.md** (this file) is how agents work: git rules, the session loop,
  the product's voice and conduct, who decides what, stack rules, content
  and data rules, the definition of done, and commits.
- **README.md** introduces the product to people: what it does, its status,
  the architecture, the layout, prerequisites, and a quick start.
- **CLAUDE.md** only imports this file, so Claude Code reads it too. Other
  agents read AGENTS.md directly. Leave CLAUDE.md as it is.

The three files are written in their final shape. Text in `{{DOUBLE_BRACES}}`
is a placeholder to fill. Text in `<!-- GUIDE: ... -->` comments explains
what a section is for, how to fill it, and what the reference project did;
delete each comment once its section is written.

Text marked `<!-- VARIANT: web -->`, `<!-- VARIANT: server -->`, or
`<!-- VARIANT: mirror -->` applies only to some products (S5, D5, D21). A
marker on its own line directly under a heading covers that whole section;
a marker at the very start of a bullet or item (after its id) covers that
whole bullet or item; and anywhere else the marker is closed by
`<!-- /VARIANT -->` and covers only the text between. Keep the text, without
its markers, when the variant applies, and delete it when it does not.

**The reference project.** Day by Word
([github.com/dunamismax/daybyword](https://github.com/dunamismax/daybyword),
public) was planned and is being built this way, and it is the worked
example for every section here. If you can read it, read its BUILD.md,
AGENTS.md, BUILD-HISTORY.md, `docs/decisions.md`, and its first commit
(`git show 918837c`), which is the state a finished setup leaves behind. Use
it for shape, depth, and tone. Copy none of its product content.

### The standard placeholders

Fill these everywhere they appear. Product-specific placeholders, such as
`{{CORE_SECTION_1}}`, are explained where they occur.

| Placeholder | Meaning | Day by Word's value |
|---|---|---|
| `{{APP_NAME}}` | The product's name as people see it | Day by Word |
| `{{APP_SLUG}}` | Lowercase, no spaces, for paths and repositories | daybyword |
| `{{APP_TYPE_NAME}}` | UpperCamelCase, for Swift types and the Xcode project | DayByWord |
| `{{TAGLINE}}` | A short description under the name | Your Bible reading companion |
| `{{LINE}}` | The product's one memorable line, if it has one | Find your plan. Read your Bible. Keep your place. |
| `{{ONE_SENTENCE}}` | What it is and on which platforms, in one sentence | a Bible reading companion: a native iPhone and iPad app built in SwiftUI, and a web version … |
| `{{USER_NOUN}}` | The word the product uses for the person using it | reader |
| `{{OWNER_HANDLE}}` | The owner's GitHub (or forge) account | dunamismax |
| `{{REPO}}` | `owner/name` of the product's own repository | dunamismax/daybyword |
| `{{DOMAIN}}` | The product's domain, if it has a website | daybyword.com |
| `{{SUPPORT_EMAIL}}` | Where support mail goes | support@daybyword.com |
| `{{BUNDLE_ID}}` | The app's bundle identifier | com.daybyword.app |
| `{{URL_SCHEME}}` | The app's URL scheme | daybyword |
| `{{CORE_PACKAGE}}` | The shared Swift package holding the domain rules | ReadingEngine |
| `{{DATA_PACKAGE}}` | The shared Swift package holding persistence | ReadingData |
| `{{CORE_SPEC}}` | The name of the core package's specification in `docs/` | engine (`docs/engine.md`) |
| `{{SERVER_PRODUCT}}` | The server executable, if there is one | DayByWordServer |
| `{{LAST_D}}` | The number of the last owner decision | 39 |
| `{{SWIFT_VERSION}}` | The pinned Swift toolchain (from `swift --version` on the owner's Mac) | 6.4.2 |
| `{{XCODE_VERSION}}` | The Xcode in use (from `xcodebuild -version`) | 27.2 |
| `{{MIN_OS}}` | The minimum iOS (and iPadOS) version, D7 | iOS 26 |
| `{{DATE}}` | The setup date, `YYYY-MM-DD` | 2026-10-30 |

### What the owner gives you

The owner describes the app: anything from a paragraph to a full concept
document, with its audience, features, platforms, business model, and
constraints. That description is **the founding brief**. Keep a faithful
summary of it in BUILD.md's opening, and treat the brief as superseded by
BUILD.md wherever the owner later decides differently.

### The setup procedure

Work through these steps in order. Steps S4 and S6 are conversations with
the owner; everything else you do yourself.

1. **S1. Orient.** Read BUILD.md, this file, and README.md in full, raw,
   including every GUIDE comment. Read the reference project if it is
   available. Check the tools on this Mac (`xcodebuild -version`,
   `swift --version`, `xcrun simctl list runtimes`, `brew --version`) so the
   plan names versions that exist.
2. **S2. Protect the template.** Run `git remote -v`. If `origin` points at
   the template repository (`swift-app-roadmap`), never push the product
   there. Ask the owner for the product's own repository (Phase 0's P0.2),
   point `origin` at it once it exists, and ask whether to keep the
   template's history or start with a fresh first commit. Replace the
   template's `LICENSE` according to D4.
3. **S3. Understand the brief.** Write yourself a short restatement: who
   the product is for, the central problem it solves (Day by Word's was
   decision fatigue: someone who struggles to choose a passage struggles
   just as much with a catalog of 500 plans), the core loop a person
   repeats, what makes it better than what exists, and what it must never
   do. List every explicit requirement in the brief, so none is lost.
4. **S4. Research before deciding.** Check, with dates and sources:
   - the category: comparable apps from the App Store (Apple's public
     search API, the products' own pages), with ratings, prices, privacy
     labels, and features, and what each does better or worse than the
     brief;
   - the name: App Store name collisions, domain availability and existing
     sites, and obvious trademark conflicts (the owner decides the risk,
     D2);
   - the platform: every Apple API and limit the features depend on (for
     example, iOS keeps at most 64 pending local notifications, widgets
     refresh on a budget, background work is not guaranteed), checked
     against current documentation;
   - the law and rights: privacy rules for the data the app touches,
     sensitive-data categories, App Store review rules for the category,
     and the rights to any third-party content, data, fonts, or images.

   Record each as a numbered finding in `docs/research/findings.md`
   ("Research finding 6"), and the comparison in
   `docs/research/competitors.md`. Never invent a fact, a rating, or a
   source. Mark anything resting on general knowledge rather than a checked
   source with † and a later item to confirm it.
5. **S5. Draft the decisions.** Start from the standard decisions in
   BUILD.md's Owner decisions table (D1–D28; each has options and a
   recommended answer in the GUIDE above the table), then add the product's
   own questions as D29 onward: the choices the brief leaves open, or that
   research showed matter (Day by Word's included whether it ever shows
   Bible text, which plans launch, and how streaks work). For each, write
   the question, two to four real options, your recommendation, and why.
   D5 picks the stack variant:
   - **App**: a SwiftUI app with shared Swift packages, and no website
     beyond the App Store page. Drop every `VARIANT: web` and
     `VARIANT: server` section.
   - **App and site**: the app plus a static or server-rendered marketing,
     support, and privacy site. Keep `VARIANT: web`; keep `VARIANT: server`
     only if a Swift server renders the site.
   - **App and web app**: the app plus a web version of the product served
     by a Swift server (Hummingbird 2 or Vapor) sharing the core package, as
     Day by Word does. Keep both variants.
6. **S6. Interview the owner.** Ask every decision the brief does not
   already answer, in batches of up to four related questions, with your
   recommendation first and labelled as recommended. Where the brief
   already answers one, confirm it in a sentence instead of asking. Record
   each answer in the owner's own terms with `(owner, {{DATE}})`. If the
   owner hands a question to you ("you decide"), decide it on the evidence
   and record it as `(agent, {{DATE}})` with the reasons. Ask follow-ups
   until no decision that shapes the phases is open. A decision that
   genuinely cannot be made yet becomes a gate (`[GATE Dn]`) with the
   condition that opens it.
7. **S7. Size version 1.0.** Write the finished product first, then cut:
   version 1.0 is the smallest product that keeps the brief's central
   promise well. Name the **first light** slice: the thinnest end-to-end
   path a person can actually use, on TestFlight (and the web, if there is
   one). Everything else goes to `docs/roadmap.md` as numbered phases after
   1.0, never into BUILD.md. Day by Word first planned 28 phases in
   BUILD.md and later had to cut its path to 1.0 from 148 open items to 103
   (its D39); plan lean from the start. As a guide, 1.0 is usually 10–16
   phases and 70–130 top-level items, each small enough for one session to
   finish and verify.
8. **S8. Write BUILD.md**, section by section, following its GUIDE
   comments. Every phase item must say exactly what to build, where it
   lives, and how to know it is done.
9. **S9. Write this file**: fill every placeholder, write §3 and §6 for
   this product, and keep the rest. Remove the rules that do not apply to
   the chosen variant.
10. **S10. Write README.md**: fill the product README below the template
    notice, following its GUIDE comments. At this stage its status says
    planning is complete, and its layout and prerequisites are what the
    plan expects (P1.13 makes them real).
11. **S11. Create the supporting files and remove the scaffolding**:
    - `BUILD-HISTORY.md`, with only its header: a title
      (`# BUILD-HISTORY.md: Finished phases`), a paragraph saying that
      phases of BUILD.md whose every item is ticked are moved here
      unchanged and that sessions read this file only when an open item, a
      document, or a failing check refers to a finished item, and a
      paragraph saying entries are a record, never edited except to repair
      a broken link;
    - `docs/roadmap.md`, holding the phases after 1.0, numbered on from
      BUILD.md's last phase and written to the same standard, under a short
      header saying when to read it (only once the launch phase is
      finished, or when an item points there) and that a phase moves back
      into BUILD.md whole when it becomes the next work;
    - `docs/research/findings.md` and `docs/research/competitors.md` from
      S4;
    - delete this setup block and README.md's template notice (each
      between `SETUP:BEGIN` and `SETUP:END`, markers included), and every
      GUIDE and VARIANT comment in all three files.
12. **S12. Verify the plan.**
    - `grep -rn '{{\|GUIDE:\|VARIANT:\|SETUP:' AGENTS.md BUILD.md README.md`
      prints nothing.
    - Every `Dn`, `Pn.n`, `En`, "Research finding n", and `§n` referred to
      exists, and every relative link resolves.
    - The Build status table's item counts match the phases' top-level
      items, and the Done column matches the ticks (P0.1 is ticked: the
      decisions were answered in setup).
    - Each phase depends only on earlier phases, except those marked
      *(parallel-safe)* or explicitly allowed to run alongside others.
    - Read BUILD.md once more as the next agent will, with no memory of
      this conversation: could you start P1.1 and know exactly what done
      means?
13. **S13. Show the owner and commit.** Give the owner a short summary:
    the product in a paragraph, the decisions, the milestones, the first
    light slice, the [OWNER] steps in Phase 0, and what moved to the
    roadmap. Make the changes the owner asks for. Then commit everything as
    `Add the build plan, agent guide, and README`, with a body summarizing
    the plan, and push it to the product's own repository (never the
    template's, S2).
14. **S14. Stop**, unless the owner asks you to start building. The next
    session begins the loop in §2 at the first open item, usually an
    [OWNER] step in Phase 0 or P1.1.

### What a good plan looks like

- **Items are concrete.** Each starts with its id and markers in bold,
  then names the deliverable: files, types, commands, numbers, and
  behavior, plus the condition for ticking it when that is not obvious
  ("Tick after the first build installs through TestFlight"). "Improve
  onboarding" is not an item; "P8.1 The first-run screen: three questions,
  each skippable, and a way to skip straight to …" is.
- **Order follows dependency.** The repository and toolchain, then product
  rules and the design system, then the domain model, the core engine, and
  persistence (each specified in a document, then pinned by table-driven
  cases, then coded), then hosting, then first light, then the features of
  1.0, then hardening and launch.
- **The owner's steps come first.** Everything only the owner can do
  (creating accounts, registering a domain, signing in to Xcode, choosing
  the design) is an [OWNER] item in Phase 0, or as early as it can be, so
  agents are never blocked late.
- **The design choice is a hard stop.** Agents draw three named visual
  directions; the owner chooses; nothing past the design session is built
  until the owner says the design is final (P2.3).
- **Both platforms move together.** If there is a web version, a feature
  that exists on both lands on both within the same milestone.
- **Decisions are the owner's words.** The Owner decisions table records
  what the owner chose and when, with a short reason, and later changes are
  recorded as revisions, never silent edits.
- **BUILD.md stays readable in one sitting.** Findings, competitor maps,
  and the work after 1.0 live in `docs/`; finished phases move to
  BUILD-HISTORY.md (§8).
- **The writing is plain.** Short sentences, concrete nouns, no hype, no
  filler. Write as Day by Word's files do.

<!-- SETUP:END -->

<!-- GUIDE: The opening paragraph says what the product is, on which
platforms, for whom, and its line, then "Every AI agent session follows this
file." Day by Word's: "Day by Word is a Bible reading companion: a native
iPhone and iPad app built in SwiftUI, and a web version at daybyword.com
served by a Swift server (Hummingbird 2) on the owner's own machine. It helps
Christians choose a reading plan, know what to read today, and keep a
trustworthy record of their reading ..." -->

{{APP_NAME}} is {{ONE_SENTENCE}}. It helps {{AUDIENCE}} {{CORE_PROMISE}}.
Its line is *{{LINE}}* Every AI agent session follows this file.

<!-- GUIDE: Optional. One bold paragraph for a standing commitment that
changes how agents work across the whole product: a neutrality rule, a
safety boundary, a regulatory status, something agents must never add or
borrow. Day by Word's was "No denominational affiliation": no statement of
faith, no copying from the owner's other faith projects. Delete if there is
none. -->

**{{STANDING_COMMITMENT_TITLE}}.** {{STANDING_COMMITMENT}}

## Git rules (owner's standing instructions)

<!-- GUIDE: Keep these unless the owner gave different git rules in setup.
They are the template owner's standing rules. Mention the mirror only if D21
says there is one. -->

These override any other workflow described in this repository or by your
tools.

- Work on `main` only. Never create branches, worktrees, or pull requests.
  Commit directly to `main` and push with `git push origin main`.
  <!-- VARIANT: mirror --> `origin` has two push URLs, {{FORGE_1}} and
  {{FORGE_2}} (BUILD.md P0.5), so one push updates both. <!-- /VARIANT -->
- No AI attribution anywhere: no `Co-Authored-By` trailers, no "Generated
  with ..." lines, and no crediting Claude, Anthropic, ChatGPT, OpenAI, or
  any AI tool in commit messages, tags, release notes, code, comments, docs,
  or file headers. Use the owner's configured git identity and never change
  git config. Content the project deliberately publishes about AI, such as
  a user-facing disclosure, is not attribution.
- After committing, push `main` right away, and at the latest before the
  session ends. Before committing, run the project's checks, review
  `git status` for stray files, and never commit what `.gitignore` excludes.

## 1. Before you touch anything

1. Read [BUILD.md](BUILD.md) in full once per session: "How agents use this
   file", the finished-product definition, the product principles, the
   Owner decisions table (D1–D{{LAST_D}}), the Engineering foundations, the
   phases to version 1.0, and the Handoff notes at the bottom. Do not read
   `BUILD-HISTORY.md`, `docs/roadmap.md` (the work after 1.0), or
   `docs/research/` unless an item or a check points there (§8, "Keeping
   BUILD.md short").
2. Read the entries of `docs/decisions.md` that bear on your item, and any
   document linked from the items you are about to work on:
   <!-- GUIDE: Map areas of work to their owning documents, as they will
   exist once Phases 1–5 write them. Day by Word's: docs/engine.md for
   engine work; docs/catalog-format.md, docs/editorial.md, and
   catalog/SOURCES.md for plans; docs/product.md and docs/design.md for
   anything a reader sees; docs/deploy.md before touching the server. -->
   `docs/{{CORE_SPEC}}.md` for {{CORE_PACKAGE}} work; `docs/product.md` and
   `docs/design.md` for anything a {{USER_NOUN}} sees; {{OTHER_DOC_MAP}}.
3. Run `git status`, `git log --oneline -20`, and `make check`, so you know
   the real state before trusting any checkbox.

The owner (`{{OWNER_HANDLE}}`) decides the product. In anything this
project publishes, refer to the owner only as the owner.

## 2. The session loop

1. Find the **first unchecked `- [ ]` item in the earliest phase that is not
   complete**, skipping items whose gate is still closed and [OWNER] steps
   still waiting on the owner (§4). The design session (P2.3) is a hard
   stop: nothing after it is built until the owner has chosen the design
   and said it is final. Phases are ordered, and items inside a phase are
   ordered unless marked *(parallel-safe)* or the phase says otherwise.
   <!-- GUIDE: Name any phase allowed to run alongside others, for example
   "Phase 10 (the launch catalog) may run alongside Phases 9–17." -->
2. Inspect the relevant code before writing any. Checkboxes can drift from
   reality: if an item is already done, verify it and tick it; if a ticked
   item is broken, untick it and say why in the Handoff notes. If the broken
   item was in a phase already moved to `BUILD-HISTORY.md`, leave the
   history as it is and add a new item to the earliest open phase that
   names it.
3. Implement the item completely and no larger than it needs to be: code,
   tests, docs, and verification.
   <!-- VARIANT: web --> A feature that exists on both the app and the web
   lands on both within the same milestone (D26). <!-- /VARIANT -->
   If an item asks for more than version 1.0 needs, build the 1.0 part and
   move the rest to `docs/roadmap.md` with a note.
4. Verify it (§7), and tick the box only when it meets the definition of
   done.
5. Commit (§8), then take the next item. Complete as many items as you can
   in one session, and stop only at the end of your budget. When you meet a
   blocker, clear it or work around it, record why, and keep going.
6. Before ending: make sure `make check` passes (and `make check-full` at a
   milestone, or before a TestFlight build or a deploy), push, update the
   Build status table in BUILD.md, and **replace** the Handoff notes with
   the current state (what you finished, what is half-done, what is
   blocked, and anything surprising). Keep them under 25 lines; history
   lives in Git.

Never leave `main` broken. If you must stop mid-item, either finish it to a
passing state or revert the partial work, and record it in the Handoff
notes.

If an item is wrong, too large, or out of order, do not silently skip or
delete it. Split it into sub-items (`P5.6a`, `P5.6b`), rewrite it, move the
part 1.0 does not need to the roadmap, or add a dated note under it, and say
what you changed in the Handoff notes.

## 3. Voice, conduct, and the {{USER_NOUN}}

<!-- GUIDE: This section is the product's conscience: the rules that
protect the person using it. Every rule is a bold lead and a few concrete
sentences, specific enough that an agent can check a screen or a string
against it. Write them from the brief, the research (especially privacy and
category findings), and the owner's decisions, citing decisions by id.

Cover, in this order, whichever apply:
1. Who the product serves, on their own terms (Day by Word: "Every
   tradition on its own terms": describe each tradition as its members
   would recognize it, never rank one above another).
2. What the product is and is not (Day by Word: "The plan, not a sermon":
   it describes plans and never interprets Scripture or gives spiritual
   direction).
3. The person's own tools or materials, if the product sits beside them
   (Day by Word: "The reader's own Bible": it never shows Bible text, D13).
4. Honest records and metrics: what the numbers can and cannot claim.
5. No dark patterns: no guilt, shaming, countdowns, loss-framed streaks,
   manipulative urgency, or engagement optimization. Name the specific
   mechanics this category is tempted by.
6. Quiet by design: when to ask for permissions, no promotions or rating
   prompts in the core flow, success measured by the person's outcome, not
   minutes in the app.
7. Honesty in the interface (kept below; adapt it).
8. Privacy as care (kept below; adapt it to the data this app touches).
9. Artificial intelligence in the product, per D13.
10. Affiliation and endorsement: whom the product does not speak for.
11. Honesty about agents' own work (kept below).
12. The voice, with a concrete picture of the person at their most tired
    or rushed, and a "this, never that" example of a sentence.

Day by Word's §3 is the model for depth: about a dozen rules, 60 lines. -->

{{APP_NAME}} serves {{AUDIENCE}}. Every rule here protects that
{{USER_NOUN}}.

- **{{SERVE_ON_THEIR_TERMS_RULE}}.** {{...}}
- **{{WHAT_IT_IS_NOT_RULE}}.** {{...}}
- **No dark patterns.** No shaming, guilt, countdowns, fake scarcity,
  manipulative urgency, {{CATEGORY_SPECIFIC_MECHANICS}}, or anything
  designed to keep someone in the app longer than they want to be. A missed
  day is simply a day, and returning is welcomed.
- **Quiet and focused.** No pop-ups, promotions, or rating prompts in the
  core flow. Never optimize for time spent in {{APP_NAME}}: success is
  {{THE_USERS_REAL_OUTCOME}}. Ask for a permission (notifications, location,
  photos, health data) only at the moment the {{USER_NOUN}} chooses the
  feature that needs it, and say why.
- **Honesty in the interface.** Numbers, estimates, and statuses are true
  and say when they are approximate. Sync, backup, and offline status are
  always truthful. Never promise a feature or an integration that has not
  been built and verified.
- **Privacy is care.** {{WHAT_DATA_IS_SENSITIVE_AND_WHY}}. It is private by
  default, kept on the device unless the {{USER_NOUN}} consents to more
  (D10), exportable, and deletable. {{ANALYTICS_RULE_FROM_D12}}.
- **{{AI_RULE_FROM_D13}}.**
- **Honesty about agents' own work.** Never claim that a review, test,
  permission, partnership, endorsement, or result happened unless it did
  and BUILD.md records it. Never invent a source, a statistic, a quotation,
  or a user's story. Generated text is never presented as someone else's
  words.
- **The voice.** Plain, warm, brief, and concrete. Write for
  {{THE_USER_AT_THEIR_MOST_TIRED}}: "{{GOOD_EXAMPLE}}," never
  "{{BAD_EXAMPLE}}." Use the {{USER_NOUN}}'s words, explain terms of art
  when they first appear, and avoid jargon. No flattery, exclamation-mark
  enthusiasm, or manipulative urgency.

## 4. Markers, gates, and who decides

<!-- GUIDE: The first paragraph follows D3. If the owner chose autonomy (as
Day by Word did), keep it. If the owner wants to approve more, say exactly
what needs approval and mark those items [OWNER]. -->

**Agents build {{APP_NAME}} autonomously** (owner decision D3, {{DATE}}).
They make every implementation decision, settle new open questions, do
every item, <!-- VARIANT: server --> provision and deploy the server
(D23), <!-- /VARIANT --> and use the owner's Apple Developer account through Xcode and App Store
Connect (D22). Decide on the evidence, and write the reasoning down where
the next agent will find it: a new product decision goes in BUILD.md's Owner
decisions table as `(agent, date)` with its reasons, and an engineering
decision goes in `docs/decisions.md`. The owner's answers in
D1–D{{LAST_D}} are the product's direction. An agent may refine how one is
carried out, but never reverses one without asking the owner.

The only limits are honesty and the host's own safety rules. Where those
rules stop an agent from a step (entering the owner's passwords or keys,
making a payment, accepting terms, sending a message in the owner's name,
or publishing where the host requires a confirmation), do everything else,
ask the owner in chat for exactly that step, and continue with other work
meanwhile.

- `- [ ]` open, `- [x]` done and verified.
- **[OWNER]**: a step only the owner can take: signing in to the owner's
  accounts ({{OWNER_ACCOUNTS}}), the owner's own review or choice (the
  design choice of D14, which is a hard stop under §2), supplying images
  (D15), approving legal text, or confirming a message sent in the owner's
  name. Agents prepare everything around it and tick it once it is
  verifiably done.
- **[GATE Dn]**: depends on a decision that opens later (for example D6
  for other platforms after 1.0, D11 for paid features). When it opens,
  record the decision and its reasons.
- **[GATE DEMO]**: begins once the first usable build is on TestFlight
  <!-- VARIANT: web --> and at {{DOMAIN}} <!-- /VARIANT --> (BUILD.md's
  first-light ship item, P7.{{N}}).
<!-- GUIDE: Add the product's own markers here, each with what it means and
who clears it. Day by Word added [RIGHTS] (third-party content needs a
cleared rights record in catalog/SOURCES.md) and [REVIEW] (editorial
review of content, with an "expert" level only the owner can give). A
health app might add [CLINICAL]; a finance app [COMPLIANCE]. Delete this
comment if there are none. -->
- **[{{PRODUCT_MARKER}}]**: {{WHAT_IT_MEANS_AND_WHO_CLEARS_IT}}.

If an item cannot be finished yet because something it needs does not
exist, build what it needs first or move to the next item, and say so in the
Handoff notes.

## 5. Stack and engineering rules

<!-- GUIDE: BUILD.md's Engineering foundations state these in brief; this
section is the working rulebook. Keep the rules below that fit the chosen
variant, fill the placeholders, and add the product's own invariants (Day by
Word added: "the journal is append-only", "dates are civil dates", "calendar
rules live only in the compiler"). Every rule should be checkable. -->

BUILD.md's Engineering foundations summarize these, and `docs/decisions.md`
records each decision with its reasons.

- **One core, everywhere.** `Packages/{{CORE_PACKAGE}}` ({{WHAT_THE_CORE_HOLDS}})
  is the single implementation of the product's rules. The app, its
  extensions<!-- VARIANT: server -->, the server<!-- /VARIANT -->, and every
  tool use it. No view, <!-- VARIANT: server --> server route, JavaScript
  module, <!-- /VARIANT --> or query reimplements core logic. Change
  `docs/{{CORE_SPEC}}.md` and add a case first, then the code.
- **Packages** (`Packages/`): `{{CORE_PACKAGE}}`, `{{DATA_PACKAGE}}`
  ({{WHAT_THE_DATA_PACKAGE_HOLDS}}), and {{OTHER_PACKAGES}} use Foundation
  only<!-- VARIANT: server -->, build on Linux, and are tested on macOS and on
  Linux. The server runs them on Linux, and both platforms must give the
  same answers<!-- /VARIANT -->.
- **Apple app** (`apple/`): Swift 6 language mode with complete concurrency
  checking, SwiftUI, Observation (`@Observable`), {{APPLE_FRAMEWORKS}}.
  Xcode {{XCODE_VERSION}}, with {{MIN_OS}} as the deployment target (D7).
  The project is generated from `apple/project.yml` by XcodeGen: never
  hand-edit `*.xcodeproj`, and run `make generate`. The app target holds UI
  and composition only.
- **Persistence**: {{PERSISTENCE_RULE}}. Schema changes ship with a
  migration and a test that opens the previous version's data.
  <!-- GUIDE: SwiftData suits an app-only product with simple models.
  SQLite through the data package's own small wrapper suits a product whose
  data is shared with a Linux server or needs exact control (Day by Word).
  Record the choice as an engineering decision. -->
- <!-- VARIANT: server --> **Server** (`Server/`): `{{SERVER_PRODUCT}}` on
  {{SERVER_FRAMEWORK}} (D5), with {{SERVER_STORAGE}}. It renders semantic
  HTML on the server and serves the project's own JavaScript and CSS. Check
  current official documentation (through Context7 where available) before
  relying on a framework or Swift API you have not used in this repository.
- **The toolchain is pinned** in `.swift-version` and used everywhere: this
  Mac<!-- VARIANT: server -->, CI, and the server<!-- /VARIANT -->. Change it
  in one commit with `make check` green<!-- VARIANT: server --> on both macOS
  and Linux<!-- /VARIANT -->.
- **Dates and time**: {{DATE_RULE}}.
  <!-- GUIDE: If the product reasons about calendar days (habits, plans,
  schedules, due dates), use a civil-date type for days, never a Foundation
  Date standing for a day, and resolve "today" once at the edge from the
  device's time zone, as Day by Word does. Otherwise say how instants and
  time zones are stored. -->
- **Tests**: Swift Testing for the packages<!-- VARIANT: server -->, the
  server<!-- /VARIANT -->, and the app's unit tests; XCTest for UI tests
  <!-- VARIANT: web -->; browser tests through WebDriver for the web<!--
  /VARIANT -->. Every core rule has table-driven cases. Every bug gets a
  test.
- **Dependencies**: {{DEPENDENCY_RULE}}. Any package not already approved
  needs an entry in `docs/decisions.md` first, and every package is pinned.
  Never add analytics, advertising, tracking, crash-reporting,
  session-replay, affiliate, remote-font, or CDN code, or any SDK that
  phones home, unless D12 explicitly allows it. {{AI_DEPENDENCY_RULE_FROM_D13}}
  <!-- GUIDE: Day by Word: zero third-party runtime dependencies in the
  app; XcodeGen and swift format as the only build tools; Hummingbird 2 and
  its Swift Server Work Group packages on the server; the web's own vanilla
  ES modules with no npm, bundler, or third-party scripts. -->
- <!-- VARIANT: web --> **Nothing from elsewhere.** A strict Content
  Security Policy: no remote fonts, scripts, styles, images, or frames.
  Links out are fine; loads from elsewhere are not.
- <!-- VARIANT: web --> **Modern browsers** (D19): {{BROWSER_RULE}}.
- **Offline first in the app.** Everything except {{ONLINE_ONLY_FEATURES}}
  works in airplane mode.
- **Personal data** (D10): {{PERSONAL_DATA_RULE}}. Never put personal data
  in a URL or a log.
- **Design**: follow `docs/design.md` and `design/tokens.json`. Use the
  generated color assets<!-- VARIANT: web --> and CSS custom properties<!--
  /VARIANT -->, never raw colors. Change a token first, regenerate, and
  commit both.
- **Accessibility**: Dynamic Type through AX5, VoiceOver, Reduce Motion,
  and sufficient contrast in light and dark on Apple platforms<!-- VARIANT:
  web -->; WCAG 2.2 AA on the web<!-- /VARIANT -->. Color is never the only
  carrier of meaning.
- **Strings**: every interface string goes through the String Catalog<!--
  VARIANT: server --> and the server's string tables<!-- /VARIANT -->, so
  the product can be translated later.
- **Secrets**: never commit `.p8` keys, certificates, provisioning
  profiles, `apple/Config/Secrets.xcconfig`, server environment files, or
  `.env` files. {{WHERE_SECRETS_LIVE}}
- **Formatting**: `swift format` with the repository's `.swift-format`
  (linted by `make check`)<!-- VARIANT: web -->; JavaScript and CSS follow
  `docs/web.md`<!-- /VARIANT -->.
- Write code that reads like the surrounding code, and keep abstractions in
  proportion to a real need. {{REUSE_RULE_FROM_D27}}

## 6. {{CONTENT_AND_DATA_SECTION_TITLE}}

<!-- GUIDE: The rules that keep the product's content and data correct and
honest, specific to this domain. Day by Word's §6, "Plans, references, and
rights", required that historic plans be transcribed from identified
printings and proofread twice, that coverage claims be computed by the
compiler and never asserted by hand, and that every catalog item have a
rights record before it ships.

Ask: what does this product show or compute that someone will rely on?
Where does it come from? What would an expert in the domain check? What
must never be invented, copied, or guessed? Typical rules:
- Content is received from identified sources, never reconstructed from
  memory or copied from another app or site.
- Facts that can be computed are computed and tested, never typed by hand.
- Every third-party item (data, text, images, fonts) has a rights record
  stating its source, licence, attribution, and territories, and nothing
  ships until it is cleared.
- Domain facts (medical, legal, financial, scientific) are cited, checked
  against two independent sources, and labelled where the product adopts
  its own convention.
- Images and icons follow D15.
- Users' words and stories stay private and anonymized.
- Never invent a source, a reviewer, a permission, a statistic, or a test
  result.
For a product with no third-party content, title this "Data and
correctness" and cover the data model's invariants, validation, and what
the product must never lose or corrupt. -->

- **{{RULE}}.** {{...}}
- **Images and icons** follow D15. {{IMAGE_RULE}}
- **People's words stay private.** Beta feedback and support mail are
  anonymized before anything enters the repository. Never commit a
  {{USER_NOUN}}'s name, contact details, or identifiable story.
- Never invent a source, a reviewer, a permission, a statistic, or a test
  result.

## 7. Definition of done for a checkbox

An item is done only when all of these hold:

1. `make check` passes: <!-- GUIDE: list what make check runs, once
   Phase 1 defines it. Day by Word's: the toolchain, formatting, imports,
   design tokens and raw colors, the catalog compile and integrity suite,
   the package and server tests, the app's unit tests, and the String
   Catalog. --> {{MAKE_CHECK_CONTENTS}}. The build has zero warnings in the
   touched targets (xcodebuild prints warnings only for files it
   recompiles, so touch the sources or clean before trusting that).
2. User-visible work is seen working once, where it runs: Apple work in
   the iOS Simulator (pick the device with `scripts/sim-destination.sh`),
   with VoiceOver labels on new controls<!-- VARIANT: web -->; web work in a
   real browser with `make serve`, with the console free of errors and CSP
   violations<!-- /VARIANT -->. Widgets, notification actions, and App
   Intents are exercised where they run, not only in unit tests. Do not
   commit routine screenshots.
3. Core changes have their cases, written before the code.
4. {{PRODUCT_SPECIFIC_DONE_RULE}}
   <!-- GUIDE: For example Day by Word's "Plan content meets its review
   level, its claims are verified by the compiler, and its rights entry is
   cleared, or the plan stays out of release builds." Delete if none. -->
5. <!-- VARIANT: server --> Server changes that are deployed pass
   `make check-live`.
6. The documents the item changes are updated, briefly.
7. The BUILD.md box is ticked in the same commit as the work.

**At each milestone, and before every TestFlight build<!-- VARIANT: server
--> or deploy<!-- /VARIANT -->**, run `make check-full` (`make check`, the
app tour in light and dark<!-- VARIANT: web -->, the web tour in light and
dark at desktop and narrow widths<!-- /VARIANT --><!-- VARIANT: server -->,
and the packages and server on Linux<!-- /VARIANT -->), and check by hand
what the tours cannot: one large Dynamic Type size and dark mode in the new
screens<!-- VARIANT: web -->, and a phone width and 200% text on the web<!--
/VARIANT -->. Fix what it finds before shipping.

Never claim verification you did not perform. If a step could not be run
(no network, a missing tool, no device), say so in the commit body and the
Handoff notes instead of ticking the box.

## 8. Commits

- One commit per completed BUILD.md item, or one for a group of related
  items finished together. Use an imperative subject of 72 characters or
  fewer that starts with the step id, for example
  `P5.5: {{EXAMPLE_COMMIT_SUBJECT}}`. The body says what changed and why.
- Pull with `--ff-only` before starting, and never force-push `main`.
- <!-- GUIDE: Keep this bullet if the repository is public (D4). -->
  The repository is public (D4), so every push publishes. Never commit
  secrets, correspondence, users' personal data, or anything a licence
  forbids publishing.
- Keep documentation current, useful, and short: update the owning
  document in place, and keep history in BUILD.md's notes, the decision
  tables, and Git, as BUILD.md's "How agents use this file" describes. Add
  a decision entry only for a real choice between alternatives, not to
  restate what an item already says.

### Keeping BUILD.md short

BUILD.md holds the plan for the work still ahead to version 1.0, so that
every session can read it in full without filling its context with finished
or distant work. Finished phases move to `BUILD-HISTORY.md`, and the work
after 1.0 lives in `docs/roadmap.md`; no session reads either by default.

- **A phase is finished when every item and sub-item in it is ticked.** A
  phase with any open item, including an [OWNER] or [GATE] item, stays in
  BUILD.md.
- **In the commit that ticks a phase's last item**, move the phase's whole
  section from BUILD.md to the end of `BUILD-HISTORY.md` unchanged: its
  heading, introduction, items, sub-items, and every Note and Result. Add a
  line under the heading saying when it moved. In BUILD.md, leave the phase
  heading with a single line, "Finished; its items and notes are in
  BUILD-HISTORY.md.", and keep the phase's row in the Build status table.
- **Item ids are never reused.** A moved item keeps its id, so references
  such as "P1.12" in code, docs, and commits still resolve.
- **The history is a record.** Never edit a moved entry except to repair a
  broken link. A moved item that later proves broken gets a new item in the
  earliest open phase (§2).
- **Open phases stay lean too.** A Note or Result under an item says in a
  few lines what was done, where it lives, and what was not verified.
  Longer evidence belongs in the commit body, `docs/decisions.md`, or the
  owning document. The Handoff notes and the "Current state" line are
  replaced each session, never appended to.
- **What stays in BUILD.md while it guides future work:** "How agents use
  this file", the finished-product definition, the product principles, the
  Owner decisions table, the Engineering foundations, the Build status
  table, and the Handoff notes. The research findings are in
  `docs/research/findings.md` and keep their numbers.
- **When 1.0 ships**, move the next phases from `docs/roadmap.md` into
  BUILD.md whole, with their ids, as the next work.
- **Read `BUILD-HISTORY.md` only when you need it:** when an open item, a
  document, or a failing check refers to a finished item and you need its
  evidence, and then only that item's entry.

## 9. Beyond the repository

<!-- VARIANT: server -->
<!-- GUIDE: Write the standing permission D23 grants, with its conditions.
Day by Word's: agents may SSH as root to the owner's server to provision,
deploy, back up, and maintain the site, provided they record how the owner's
other sites answer before any change and check again afterward, archive the
web server's configuration before changing it, add only this product's own
site file, touch no other site, service, user, or database, and run deploys
inside the server's shared deploy lock. -->

**The server** (D23). {{SERVER_PERMISSION_AND_CONDITIONS}}
<!-- /VARIANT -->

**Other services.** {{OWNER_SERVICES}} are the owner's: agents verify what
the owner set up (`dig`, `git remote -v`) but never sign in. The Apple
Developer account is the owner's membership (D22): agents use it through
Xcode and App Store Connect where the owner is signed in, within the host's
safety rules.

**Developer tools** (D3): on the owner's Mac, agents may install the
developer tools the work needs without asking: Homebrew formulae and casks,
Swift toolchains through swiftly, and user-local tools. Prefer well-known,
maintained tools from their official sources, and record in README.md's
prerequisites any tool a script or `make check` depends on. This does not
cover `sudo`, macOS system or security settings, paid software, or adding a
package dependency (§5 and `docs/decisions.md` govern that).

Agents never:

- change this repository's visibility, or fork or mirror it beyond what D4
  and D21 set up;
- change or copy from the owner's other repositories (D27);
- contact users, partners, press, or anyone else in the owner's name,
  except through messages the owner has confirmed;
- add {{THINGS_THE_PRODUCT_MUST_NEVER_GAIN}};
- <!-- VARIANT: server --> serve anything on the owner's server but what
  this repository defines;
- claim a review, permission, partnership, endorsement, or result that did
  not happen.

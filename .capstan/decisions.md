# Decisions

| # | Date | Decision | Status |
|---|------|----------|--------|
| 21 | 2026-08-21 | Scope widened two lines: README line 98's `/effort` becomes `/capstan:effort`, and the line 3 tagline adopts the new description | superseded by 22 |
| 20 | 2026-08-21 | Both descriptions carry identical text. The longer gallery variant is dropped: "stops for your approval at three points along the way" contradicts `CONTEXT.md`, which defines a Gate as never a pause | accepted |
| 64 | 2026-08-21 | The three italic bullet leads in the detection step stay. The repository uses bold leads 39 times and this is the only deviation. Revisit in the README effort rather than spending a round on three characters | assumed |
| 63 | 2026-08-21 | `.effort/` is deleted from this working copy at delivery. Nothing else deletes it, and left in place it fires the trigger built in this effort and stops the next one | accepted |
| 62 | 2026-08-21 | `.effort/` is never moved. The operator deletes it. Moving it would put a stale `CLAIM.md` where the next run reads a live one | accepted |
| 61 | 2026-08-21 | The step reads the recorded `assumed` line before asking. A line written to stop a question recurring has to be read by the thing that asks it | accepted |
| 60 | 2026-08-21 | Any path confirmed as Capstan's stops the run. Mixed answers resolve to stop rather than to nothing | accepted |
| 59 | 2026-08-21 | The claim check runs before the provenance question. A claim is a fact about the repository, not an opinion the operator supplies, and asking first lets a "not ours" answer step past live work | accepted |
| 58 | 2026-08-21 | The Architect detects a pre-2.1.0 layout and **stops**. The operator moves the files. Supersedes 36, 43, 46, 49, 51, 54 and 57, and deletes `MIGRATION.md`. Seven review rounds on a procedure the crew was going to run against a user's files is the signal the README already names: simplify rather than keep it alive | accepted |
| 57 | 2026-08-21 | Not-Capstan's and Capstan's-but-declined are different answers. The first proceeds normally, the second stops the run per 47. Folding the two asks into one confirmation had merged them | superseded by 58 |
| 56 | 2026-08-21 | The `Claim` glossary row is not widened for the pre-2.1.0 path. Settled: `CONTEXT.md` describes the current convention, and `MIGRATION.md` is deletable once served. Raised five times; recorded so it stops recurring | accepted |
| 55 | 2026-08-21 | A trigger firing on a repository that is not Capstan's is recorded as an `assumed` line, so it does not ask again on every later effort | accepted |
| 54 | 2026-08-21 | Deleting `.effort/` is gated on the same per-path confirmation as the move and named in what the operator approves. The Authority table puts deletes with the operator every time | superseded by 58 |
| 53 | 2026-08-21 | Nothing confirmed means the migration returns control and the run proceeds normally. The trigger is a candidate signal, not proof | accepted |
| 52 | 2026-08-21 | Scope widened: the README's upgrade note is corrected. Its premise that the reader has a root `.effort/` is false for any repository that has delivered an effort | accepted |
| 51 | 2026-08-21 | `.effort/` is deleted before the migration commit, not after, so it is never both unignored and untracked while something is staged | superseded by 58 |
| 50 | 2026-08-21 | Taking over a pre-2.1.0 claim is not supported. Finish or abandon that effort under 2.0.0, or delete `.effort/` and start fresh | accepted |
| 49 | 2026-08-21 | Provenance is confirmed with the operator before any path moves. This is what makes broad detection safe, and it closes a guard that covered the trigger but never the move | superseded by 58 |
| 48 | 2026-08-21 | Supersedes 33. Detection triggers on any root artifact, not on `.effort/`. That directory was never tracked and the Courier deletes it at delivery, so a delivered or freshly cloned 2.0.0 repository has none and the migration would never have fired | accepted |
| 47 | 2026-08-21 | Supersedes 45. Declining the migration ends the run. There is no decline mode, because honouring one means every phase file and skill consults a flag, which is the dual-read fallback decision 32 refused | accepted |
| 46 | 2026-08-21 | The operator deletes `.effort/` as the last step of migration. Nothing else does, so leaving it makes the trigger fire on every later effort | superseded by 58 |
| 45 | 2026-08-21 | A declined migration is recorded in `CLAIM.md`, which survives the run boundary, and governs reads and writes for all three paths. "For the rest of this run" expires at a gate; an effort spans four | superseded by 47 |
| 44 | 2026-08-21 | The migration pointer sits between the claim check and the claim write. One reorder closes three findings at once | accepted |
| 43 | 2026-08-21 | The migration lives in `skills/effort/MIGRATION.md` behind a pointer, not inline in `Before you start`. It is a branch most runs never take, and when it has served its purpose it can be deleted whole rather than unpicked | superseded by 58 |
| 42 | 2026-08-21 | Drop "live claim" as a term. A claim exists or it does not, matching the wording already in the file | accepted |
| 41 | 2026-08-21 | The claim check has one home. The existing step absorbs the old-path case rather than a second rule sitting above it | accepted |
| 40 | 2026-08-21 | The migration confirms each of the three paths rather than assuming all three are Capstan's. A repository can hold `.effort/` and an unrelated `decisions.md` | accepted |
| 39 | 2026-08-21 | `CONTEXT.md` gains a `.capstan/` row. The word was doing two jobs, the folder and the `capstan:` namespace prefix, which the interview skill says to challenge | accepted |
| 38 | 2026-08-21 | The `.gitignore` rewrite for an upgrading repository belongs to slice 2's detection step. A gap in the plan, found in review, that would have shipped as unignored scratch | accepted |
| 37 | 2026-08-21 | No marker file inside `.capstan/`. `CONTEXT.md` sits there and introduces the vocabulary better than a README nobody updates | accepted |
| 36 | 2026-08-21 | The migration lands as its own commit at the moment of the move, never folded into a slice commit | superseded by 58 |
| 35 | 2026-08-21 | Version 2.1.0. Nothing a user types changes; only the on-disk layout of their artifacts, and the Architect moves it | accepted |
| 34 | 2026-08-21 | Detection checks for a live `CLAIM.md` before moving anything, and reports rather than relocating a running effort | accepted |
| 33 | 2026-08-21 | The Architect detects a pre-migration layout and offers to move it. Prose in a skill, not a script, and not release notes nobody reads | superseded by 48 |
| 32 | 2026-08-21 | Hard cut. The skills read the new paths only. No dual-read fallback, because it would never be removed | accepted |
| 31 | 2026-08-21 | `.effort/` becomes `.capstan/effort/`. The word stays, since `Effort` is a defined term in `CONTEXT.md` | accepted |
| 30 | 2026-08-21 | The README rewrite is a separate effort, sequenced after the path migration. Mixing them hides which change broke what | accepted |
| 29 | 2026-08-21 | Capstan's own repo follows the same convention. Its root `CONTEXT.md`, `decisions.md` and `decisions/` move too | accepted |
| 28 | 2026-08-21 | `.capstan/` is committed. Only `.capstan/effort/` is gitignored. A blanket ignore would stop decisions entering git and contradict the thesis | accepted |
| 27 | 2026-08-21 | Every artifact Capstan writes lives under `.capstan/` in the working copy. The repo root stays the user's, and `CONTEXT.md` stops colliding with the same filename in other plugins | accepted |
| 26 | 2026-08-21 | Whether `Upgrading` should say that refreshing the marketplace before uninstalling orphans the old entry harmlessly. Observed live; the alarming error message is undocumented | open |
| 25 | 2026-08-21 | `plugin.json` holds the canonical description. `marketplace.json` and the README copy it, and the next editor changes all three | accepted |
| 24 | 2026-08-21 | The `Namespace` row in `CONTEXT.md` is forward-looking rather than a retrofit against decision 4, because the prefix itself resolved in this effort | accepted |
| 23 | 2026-08-21 | Scope widened again: `Known limits` says `/capstan:effort`, and the manual-install section gets its own start line | accepted |
| 22 | 2026-08-21 | Supersedes 21. The manifest description stays as agreed, but the README keeps a subtitle that names what Capstan is. A gallery card has a category and an install button for context; a README has neither | accepted |
| 19 | 2026-08-21 | Dropped "and waits for your go" from the description. It duplicated the closing line. Revisit if the approved wording is wanted verbatim | assumed |
| 18 | 2026-08-21 | The description is plain language. No role names, no internal vocabulary | accepted |
| 17 | 2026-08-21 | `displayName` is "Capstan" with no descriptive tail | accepted |
| 16 | 2026-08-21 | Version goes to 2.0.0. The skill namespace is the public interface and it breaks | accepted |
| 15 | 2026-08-21 | The GitHub repo renames to `BytesNation/capstan`. The marketplace id stays `bytesnation` | accepted |
| 14 | 2026-08-21 | Rename to `capstan`. Both the skill namespace and the install identifier change. See [0001](decisions/0001-rename-to-capstan.md) | accepted |
| 13 | 2026-08-21 | The in-session equivalent of `claude plugin update <plugin>@<marketplace>`. Not verified; the CLI form is documented instead | open |
| 12 | 2026-08-21 | The `Upgrading` section documents the full two-step sequence. Refreshing the marketplace alone does not install a new version | accepted |
| 11 | 2026-08-21 | The `Upgrading` section documents both refresh forms, in-session and CLI, since `## Install` is written for the CLI | accepted |
| 10 | 2026-08-21 | No release tags while the core is still moving. Revisit when someone needs to pin a version, or when the marketplace entry stops tracking the default branch | accepted |
| 9 | 2026-08-21 | Scope widened by one line: the `claude plugin update` mention in `## Install` is reconciled with the new `Upgrading` section | accepted |
| 8 | 2026-08-21 | The README recommends leaving auto-update off rather than presenting both paths neutrally. Revisit if steering the reader is unwanted | assumed |
| 7 | 2026-08-21 | The version bump ships inside this effort, not as a separate release commit | accepted |
| 6 | 2026-08-21 | Both update paths are documented: marketplace auto-update, and the manual `/plugin marketplace update` | accepted |
| 5 | 2026-08-21 | The README `Upgrading` section is rewritten to cover the marketplace install, not only the manual copy | accepted |
| 4 | 2026-08-21 | `CONTEXT.md` is created forward only, from the next term that resolves. Never retrofitted from existing code | accepted |
| 3 | 2026-08-21 | The upgrade explanation lives in the README `Upgrading` section. No `CHANGELOG.md` | accepted |
| 2 | 2026-08-21 | Updating installs need no migration step. The new files appear on their own | accepted |
| 1 | 2026-08-21 | Plugin version goes to 1.1.0 for the glossary and log-status change | accepted |

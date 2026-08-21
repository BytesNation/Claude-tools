# Decisions

| # | Date | Decision | Status |
|---|------|----------|--------|
| 21 | 2026-08-21 | Scope widened two lines: README line 98's `/effort` becomes `/capstan:effort`, and the line 3 tagline adopts the new description | superseded by 22 |
| 20 | 2026-08-21 | Both descriptions carry identical text. The longer gallery variant is dropped: "stops for your approval at three points along the way" contradicts `CONTEXT.md`, which defines a Gate as never a pause | accepted |
| 39 | 2026-08-21 | `CONTEXT.md` gains a `.capstan/` row. The word was doing two jobs, the folder and the `capstan:` namespace prefix, which the interview skill says to challenge | accepted |
| 38 | 2026-08-21 | The `.gitignore` rewrite for an upgrading repository belongs to slice 2's detection step. A gap in the plan, found in review, that would have shipped as unignored scratch | accepted |
| 37 | 2026-08-21 | No marker file inside `.capstan/`. `CONTEXT.md` sits there and introduces the vocabulary better than a README nobody updates | accepted |
| 36 | 2026-08-21 | The migration lands as its own commit at the moment of the move, never folded into a slice commit | accepted |
| 35 | 2026-08-21 | Version 2.1.0. Nothing a user types changes; only the on-disk layout of their artifacts, and the Architect moves it | accepted |
| 34 | 2026-08-21 | Detection checks for a live `CLAIM.md` before moving anything, and reports rather than relocating a running effort | accepted |
| 33 | 2026-08-21 | The Architect detects a pre-migration layout and offers to move it. Prose in a skill, not a script, and not release notes nobody reads | accepted |
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

# Decisions

| # | Date | Decision | Status |
|---|------|----------|--------|
| 21 | 2026-08-21 | Scope widened two lines: README line 98's `/effort` becomes `/capstan:effort`, and the line 3 tagline adopts the new description | superseded by 22 |
| 20 | 2026-08-21 | Both descriptions carry identical text. The longer gallery variant is dropped: "stops for your approval at three points along the way" contradicts `CONTEXT.md`, which defines a Gate as never a pause | accepted |
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

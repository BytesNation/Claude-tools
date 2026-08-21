# Claude Tools

A five-role agent crew and the disciplines it runs on, for taking work from concept to delivery with a human at the gates rather than in the loop.

Plain markdown. No scripts, no schemas, no hooks, no scheduler. That is deliberate: anything that needs code to stay alive is something you will eventually maintain or abandon, and prose survives a model change in a way a validator does not.

The words below are load-bearing and each one is defined in [`CONTEXT.md`](CONTEXT.md). That file is this repo's own glossary, kept the way the plugin asks you to keep yours.

## The crew

Roles are functions in a pipeline, not domains, so the same five handle a software feature, a client document, a video, or an infrastructure change.

| Role | Model | Owns | Never |
|---|---|---|---|
| **Scout** | sonnet / medium | Finding out. Primary sources, cited findings. Runs many in parallel. | Decides anything. Has no write tools at all. |
| **Architect** | your session | The interview, the spec, the slice graph, the decision log. | Builds or reviews. |
| **Builder** | sonnet / high | One vertical slice, test-first, in its own worktree. | Reviews itself. Touches a gated action. |
| **Reviewer** | opus / xhigh | Independent two-axis review of the diff. | Sees the Builder's reasoning. Fixes what it finds. |
| **Courier** | sonnet / medium | Packaging, recipient-specific briefs, the permanent record, teardown. | Sends anything. |

The Architect is the only role that talks to you between gates. Five roles reporting independently is five inboxes.

## Three gates

The run **stops** at each gate. There is no poller and nothing waits: the brief is posted and the run ends. You resume by invoking the next phase.

1. **Concept locked.** What we are building, why, and what we are explicitly not doing.
2. **Plan locked.** How, cut into slices, what runs parallel, what was assumed.
3. **Ready to deliver.** What was built, what review found, what goes to whom.

Gate one is the one to protect. It is where a wrong turn is cheapest to catch and the one that gets skipped.

Which is why phases 2, 3 and 4 live in their own files beside `skills/effort/SKILL.md` rather than inside it. A run genuinely ends at each gate, so that is a real context boundary, and a phase worked with the later phases sitting in view is a phase that gets rushed. Phase 1 stays in `SKILL.md`: hiding a step protects the step in front of it, not itself.

## Stop for consequence, never for ambiguity

The crew does not halt on unclear requirements. It takes the most defensible reading, writes the assumption down, and keeps moving, then surfaces every assumption at the next gate where correcting one is nearly free.

What does stop the line: secrets and credentials, anything a third party will see, anything that costs money, and anything destructive or production-facing.

## The disciplines

Nine skills the roles pull in. Three are preloaded into the agents that need them via `skills:` frontmatter, so the discipline is in context before the first turn rather than hopefully invoked.

| Skill | Used by | For |
|---|---|---|
| `interview` | Architect | Rounds of questions, each carrying a recommended answer. Facts are the agent's job, decisions are yours. Questions you cannot answer get parked in the log rather than lost. |
| `slicing` | Architect | Vertical slices with real blocking edges. Includes the expand-migrate-contract exception for wide refactors. |
| `test-first` | Builder | Red, green, refactor. Tests at pre-agreed seams only. |
| `decision-record` | Architect, Courier | A one-line log by default, a full record only when it earns one, superseded rather than edited. Owns the `CONTEXT.md` glossary, the one artifact edited in place. |
| `brief` | Architect, Courier | BLUF checkpoint briefs, and partner briefs generated per recipient rather than maintained. |
| `two-axis-review` | Reviewer | Standards and spec, answered independently, never blended into one verdict. |
| `unslop` | Anything writing prose | Cuts AI tells from writing a person will read. |
| `writing-for-agents` | You, editing this repo | The levers that make a document an agent consumes behave the same way every run. |

## Two kinds of prose

Writing for a person and writing for an agent want opposite things, and one rule for both produces bad versions of each. A brief wants voice, rhythm, and an opinion. A `SKILL.md` wants none of that: flat, deduplicated, and the same shape every run.

So the two skills split by reader, and the routing belongs in your own `CLAUDE.md`:

```markdown
Always apply the `unslop` skill to prose a person reads: chat, documents, READMEs,
commit messages, briefs. Prose an agent consumes goes to `writing-for-agents`
instead: SKILL.md files, CLAUDE.md, AGENTS.md, subagent prompts, and an effort's
spec.md and plan.md.
```

Without that line you get `unslop` announcing it must always apply and nothing telling it where to stop.

## Why decisions and the words for them are the only things that persist

Three tiers of decision, sorted by lifespan, and the glossary standing beside them.

- **Glossary**: one line per term, [`CONTEXT.md`](CONTEXT.md) at the repo root. The only file here edited in place rather than superseded, because a glossary you have to read archaeologically is a glossary nobody reads. Every agent that writes or reviews code reads it; a name that contradicts it is a review finding.
- **Log**: one line per decision, `decisions.md` at the repo root. Cannot bloat.
- **Record**: a full document only when a decision is hard to reverse *and* surprising without context *and* a real trade-off. All three, so most efforts produce none.
- **Brief**: generated per recipient at send time, never stored, never maintained.

The log carries unsettled questions too. A question the interview could not resolve becomes an `open` line, or an `assumed` one when the crew picked a default to keep moving. Both get reported at every gate, neither blocks one, and the next interview reads them back before its first round. Without that, a hard question asked in March dies with the spec that held it.

Everything else lives in a gitignored `.effort/` and is deleted at delivery. A stale spec or an old research file is worse than none, because the next agent reads it as current.

The reason external documentation becomes unreadable is almost always that one artifact was made to serve two audiences with opposite needs. An internal record is dense and assumes context. A partner brief is short and assumes nothing. Do not maintain the second one. Regenerate it.

## Install

```bash
claude plugin marketplace add BytesNation/Claude-tools
claude plugin install claude-tools@bytesnation
```

That installs at user scope, so the crew is available in every session. `--scope project` writes to the project's `.claude/settings.json` instead and travels with the repository, which is what you want if a team shares it. Later, when a new version lands, see [Upgrading](#upgrading) below for how it actually reaches your machine.

Restart Claude Code. Agent definitions load at session start, so nothing applies until you do.

Then start work with `/effort <what you want built>`.

### The two installs name things differently

A plugin namespaces what it ships, so the Builder is `claude-tools:builder` under a plugin install and plain `builder` under a manual one. `skills/effort/SKILL.md` tells the Architect which agent to spawn for each role, so use whichever form your install actually produced. The manual install is the one this crew has been run on; the plugin path is newer and less exercised.

### Installing by hand instead

```bash
git clone https://github.com/BytesNation/Claude-tools.git
cp -r Claude-tools/agents/* ~/.claude/agents/
cp -r Claude-tools/skills/* ~/.claude/skills/
```

### Two skills are more than one file

Most skills here are a lone `SKILL.md`. Two are not, and lifting just the `SKILL.md` out of either leaves pointers aimed at files that are not there.

```
skills/effort/
  SKILL.md              identity, the crew, the gates, the precondition, phase 1
  PHASE-2-PLAN.md
  PHASE-3-BUILD.md
  PHASE-4-DELIVER.md

skills/writing-for-agents/
  SKILL.md
  SKILL-MECHANICS.md    frontmatter, invocation, router skills
  AUDIT.md              the editing pass to run against a target document
  LICENSE, CREDIT.md    upstream is MIT, see the licence section
```

The Architect reads the file for the phase it is in, so a run that reaches gate two with no `PHASE-2-PLAN.md` beside it has nothing to follow and will improvise a plan phase. Take the whole directory.

### Upgrading

Coming from 1.0.0, the two things you will notice are `CONTEXT.md`, the glossary, and the `open`/`assumed` log statuses, both described above. Neither needs a migration step. Both appear on their own the first time an effort settles a term or parks a question, and every read of them is guarded, so a repo that predates 1.1.0 behaves exactly as it did before.

**Marketplace install.** Bumping the version in `plugin.json` does not, by itself, put a new release on your machine. Third-party marketplaces ship with auto-update off, so you pull the update yourself. From a shell, two steps, in order:

```bash
claude plugin marketplace update bytesnation
claude plugin update claude-tools@bytesnation
```

The first refreshes the marketplace catalog. On its own that installs nothing, so stopping there leaves you on the old version while believing you upgraded. The second step does the install, and it needs the marketplace-qualified name, `claude-tools@bytesnation`. The bare name does not resolve. `claude plugin update claude-tools` fails with `Plugin "claude-tools" not found`. Run it right and the CLI answers `Plugin "claude-tools" updated from 1.0.0 to 1.1.0 for scope user. Restart to apply changes.` Restart the session once you see that.

The shell sequence above is the one that was actually run. In a session, `/plugin marketplace update bytesnation` is the in-session form of the refresh step; nobody has watched the install step run through the `/plugin` manager, so this README stops short of a claim there.

`/plugin`, under the Marketplaces tab, has a toggle to auto-update instead. Leave it off. The whole point of this crew is a human at the gates rather than in the loop, and auto-update means a new commit reaches your machine before anyone has read it.

**Manual install.** The copy above overwrites what it finds and leaves everything else alone, so a version that drops or renames a file leaves the old one sitting there. Replace a skill outright rather than copying over it:

```bash
rm -rf ~/.claude/skills/effort
cp -r Claude-tools/skills/effort ~/.claude/skills/
```

## Known limits

**`/effort` cannot be invoked by a model.** It carries `disable-model-invocation: true`, so only you can start an effort. That is intentional, because an agent that can start work on its own authority can commit you to work you never asked for. It does mean kickoff is always something you type.

**Bash is an escape hatch.** Scout's read-only guarantee is structural: its tool grant contains no write tools, so the harness enforces it. Builder, Reviewer, and Courier all hold Bash, so their "never do X" rules are prose, not enforcement. If you want the gates enforced rather than requested, add a deny list to `settings.json`.

**Builder runs with `acceptEdits`.** File writes will not prompt. Bash commands still can, which is where unattended fan-out tends to stall.

**Effort is not supported on Haiku.** Drop the `effort:` line from any agent you point at a Haiku model.

**Fan-out does nothing for single-artifact work.** Parallel builders need slices that own different files. A document, a video script, a single config file: all one artifact, all inherently one Builder. Software usually fans out because slices own different things. Most non-code work does not, and a one-slice plan there is correct rather than a failure to parallelise.

## Why the Architect creates worktrees by hand

Subagents support `isolation: worktree` in frontmatter. This crew deliberately does not use it.

That field resolves against the **session's** working directory rather than the repository the work lives in. A session rooted anywhere else fails outright with "not in a git repository", however correct the paths handed to the Builder are. Since one session often works across several repositories, that is the normal case rather than an edge case.

So the Architect runs `git -C <repo> worktree add ...` itself, hands each Builder an absolute path, and removes the worktree after the merge. Nothing ever changes directory, and the flow works from a session rooted anywhere, including somewhere with no repository at all.

The related trap: `.effort/` is gitignored, so an effort's spec, plan, and research do not exist inside any worktree. Builders get absolute paths into the main working copy for those. A Builder that cannot find its brief will invent one.

## Configure

Two things are setup-specific and read from your `CLAUDE.md` or `AGENTS.md` rather than hardcoded:

- Where the Courier writes the permanent per-effort note. With none configured it skips the step and says so.
- Where efforts and their artifacts live.

An effort writes `.effort/CLAIM.md` when it starts and updates it at every gate. Another Architect finding a live claim stops and asks rather than starting. The ceiling counts efforts, not sessions, so without this two sessions will happily run the same work and write over each other.

Because a run *ends* at each gate, every phase after the first begins by re-reading the repository rather than trusting the plan it wrote. Hours can pass between gates and the work may already be done.

Concurrency is capped at three efforts. Three gates each against one reader is nine briefs a cycle, which is roughly where they stop being read and start being rubber-stamped. Fan-out *inside* an effort is unbounded.

## License

MIT. See [LICENSE](LICENSE). Take it, change it, ship it.

Two skills here are not ours. Both are MIT, both are redistributed with their own licence and a `CREDIT.md` in their folder noting exactly what we changed:

- `skills/writing-for-agents/`: `SKILL.md` and `SKILL-MECHANICS.md` by [Matt Pocock](https://github.com/mattpocock/skills). `AUDIT.md` beside them is ours.
- `skills/unslop/`: `SKILL.md` by [Lauren Tan](https://github.com/cursor/plugins/tree/main/pstack/skills/unslop), via cursor/plugins. Our changes are two lines, listed in that folder's `CREDIT.md`.

Nothing else here is vendored, but one idea is borrowed. The frontier in `interview` (a design tree, where a question depending on an open question waits for a later round) is sharpened from Matt Pocock's [`grilling`](https://github.com/mattpocock/skills). The prose is ours. The mechanic is his.

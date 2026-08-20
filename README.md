# Claude Tools

A five-role agent crew and the disciplines it runs on, for taking work from concept to delivery with a human at the gates rather than in the loop.

Plain markdown. No scripts, no schemas, no hooks, no scheduler. That is deliberate: anything that needs code to stay alive is something you will eventually maintain or abandon, and prose survives a model change in a way a validator does not.

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

## Stop for consequence, never for ambiguity

The crew does not halt on unclear requirements. It takes the most defensible reading, writes the assumption down, and keeps moving, then surfaces every assumption at the next gate where correcting one is nearly free.

What does stop the line: secrets and credentials, anything a third party will see, anything that costs money, and anything destructive or production-facing.

## The disciplines

Six skills the roles pull in. Three are preloaded into the agents that need them via `skills:` frontmatter, so the discipline is in context before the first turn rather than hopefully invoked.

| Skill | Used by | For |
|---|---|---|
| `interview` | Architect | Rounds of questions, each carrying a recommended answer. Facts are the agent's job, decisions are yours. |
| `slicing` | Architect | Vertical slices with real blocking edges. Includes the expand-migrate-contract exception for wide refactors. |
| `test-first` | Builder | Red, green, refactor. Tests at pre-agreed seams only. |
| `decision-record` | Architect, Courier | A one-line log by default, a full record only when it earns one, superseded rather than edited. |
| `brief` | Architect, Courier | BLUF checkpoint briefs, and partner briefs generated per recipient rather than maintained. |
| `two-axis-review` | Reviewer | Standards and spec, answered independently, never blended into one verdict. |

## Why decisions are the only thing that persists

Three tiers, sorted by lifespan.

- **Log**: one line per decision, `decisions.md` at the repo root. Cannot bloat.
- **Record**: a full document only when a decision is hard to reverse *and* surprising without context *and* a real trade-off. All three, so most efforts produce none.
- **Brief**: generated per recipient at send time, never stored, never maintained.

Everything else lives in a gitignored `.effort/` and is deleted at delivery. A stale spec or an old research file is worse than none, because the next agent reads it as current.

The reason external documentation becomes unreadable is almost always that one artifact was made to serve two audiences with opposite needs. An internal record is dense and assumes context. A partner brief is short and assumes nothing. Do not maintain the second one. Regenerate it.

## Install

```bash
git clone https://github.com/BytesNation/Claude-tools.git
cp -r Claude-tools/agents/* ~/.claude/agents/
cp -r Claude-tools/skills/* ~/.claude/skills/
```

Restart Claude Code. Agent definitions load at session start, so nothing applies until you do.

Then start work with `/effort <what you want built>`.

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

Concurrency is capped at three efforts. Three gates each against one reader is nine briefs a cycle, which is roughly where they stop being read and start being rubber-stamped. Fan-out *inside* an effort is unbounded.

## License

MIT. See [LICENSE](LICENSE). Take it, change it, ship it.

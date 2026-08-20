---
name: decision-record
description: Record decisions so they survive without bloating anything. A one-line log by default, a full record only when it is earned, superseded rather than edited. Use whenever a decision is settled.
---

# Decision record

Three tiers, sorted by how long each thing needs to survive. Nearly everything stays in tier one.

## Tier 1: the log

`decisions.md` at the repository root. One line per decision. Committed.

```markdown
# Decisions

| # | Date | Decision | Status |
|---|------|----------|--------|
| 7 | 2026-08-20 | Sessions expire server-side, not by JWT claim | accepted |
| 6 | 2026-08-19 | Single Postgres instance, no read replica yet | accepted |
| 5 | 2026-08-14 | Config lives in the database, not env vars | superseded by 9 |
```

This is what an agent reads when it opens the repository cold, and what you scan six months later. It cannot bloat, because a line is a line.

Write the line the moment the decision resolves, not batched at the end of a session. A decision that only exists in a context window is a decision that is about to be lost.

## Tier 2: the record

A full document only when the decision passes **all three** gates:

1. **Hard to reverse.** Undoing it later costs real work.
2. **Surprising without context.** A competent person arriving fresh would ask why.
3. **A real trade-off.** Something genuine was given up.

All three, not any one. Most decisions fail at least one, so most efforts produce a handful of log lines and no records at all. That is the design working, not the discipline slipping. Writing a record for every decision is exactly how decision folders became the bloat you are trying to avoid.

Lives at `decisions/NNNN-short-slug.md`. Six sections, none longer than a paragraph:

```markdown
# NNNN. Sessions expire server-side, not by JWT claim

**Status**: accepted
**Date**: 2026-08-20

## Context
What was true that forced a choice.

## Decision
What was chosen, stated plainly.

## Alternatives
What else was on the table, and what each one would have cost.

## Consequences
What this makes easy, and what it makes hard.

## Revisit when
The condition that would make this worth reopening. Write one, or admit there isn't one.
```

## Tier 3: the brief

Never stored. Generated per recipient at send time by the `brief` skill, which owns the shape.

Do not maintain partner documentation. Regenerate it.

## Never edit an accepted record

When a decision changes, write a new one that supersedes the old and cross-link both. Mark the old one `superseded by NNNN` and give the new one a `supersedes NNNN` line. Update both files, every time.

This is the mechanic that keeps the set honest, and it is mechanical enough to be worth doing without thinking. Editing an accepted record destroys the history of why the direction shifted, which is usually the most valuable thing in the folder.

Never delete a record. Superseded records stay, marked, out of the reading path.

## What does not go here

Specs, plans, research findings, review output, and checkpoint drafts all live in `.effort/`, which is gitignored and deleted at delivery. Only decisions persist.

## The permanent note

At delivery the Courier writes one note per effort into the knowledge base: what it was, what was decided, what was rejected, and links out to the code and the records. That note is the only thing that can answer what has been decided across every venture at once, which no single repository can.

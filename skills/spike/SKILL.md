---
name: spike
description: Build a throwaway spike that settles whether something behaves right or feels right. Use when a design question keeps stalling on needing something concrete to react to.
---

# Spike

A spike is throwaway work that answers **one question**.

A Builder runs it, carrying a different definition of done for the same role.

## Name the question

Before producing anything, decide which of two shapes the question takes:

- **Does it behave right.** The question is about a sequence: whether the thing holds up once real cases run through it.
- **Does it feel right.** The question is about form: what something should look, sound, or read like, when several genuinely different answers are all defensible.

Neither branch defaults to code. Capstan runs efforts on documents, video, and infrastructure as well as code, and each branch takes whatever medium the effort is already working in.

If the question could read as either, pick whichever shape matches what would actually change someone's mind, and say which one out loud before building.

## Size it

**Behave right.** Pick the cases that would actually change the answer: the ordinary path, the one that will come up in practice and is awkward to trace by hand, and the one that should be refused outright. Sized this way, a spike on an incident-response runbook pushes the ordinary restart, the one attempted while a dependent service is mid-deploy and awkward to reason through on paper, and the one that should never run at all: a restart during a change freeze.

**Feel right.** Three variants. Fewer leaves nothing to react against; more, and cut back to the three genuine contenders.

## Produce the thing

Marked as throwaway from the first line, so nobody mistakes it for production work in progress.

**Behave right.** Make it runnable, and show the whole condition after each case runs, not only what moved, so whoever reacts to it can point at exactly where it went wrong. On the runbook example: after each case, show what ran, what was skipped, and what's still pending.

**Feel right.** Lay the variants side by side, in the medium named above, so a reaction can land on all of them at once.

Both skip what a spike trades away for speed: no tests, since one that needs a test to be trusted has stopped being a spike; only the error handling that keeps it running long enough to look at; and no abstraction, since generality and reuse are exactly what the trade gives up.

## Record the answer

Write the answer, per the `decision-record` skill, into the same `open` line written when the stalled question pointed here, flipping that line's status to `accepted` and naming the branch that produced it, rather than adding a second line beside it. A second line leaves the first open forever, and the next interview reads the log before its first round.

Where no such line exists yet, write one and settle it in the same pass.

The code is a reference for how the answer was reached. The line in the log is what persists.

## Park the branch

Commit to a branch named `spike/<slug>`, outside the effort's own branch namespace so nothing mistakes it for a slice waiting to merge. It is never merged. Push it, and never delete it: a local-only branch disappears on a fresh clone, and it is the only thing standing behind the answer once the worktree is gone.

A spike that produced something impressive and settled nothing has failed, regardless of how good the work looks.

**Done when** the question named at the start has a written answer, in the line that was opened when it first stalled, and the branch that produced it is named in that same line.

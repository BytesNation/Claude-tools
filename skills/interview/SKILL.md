---
name: interview
description: Interview someone about a plan, design, or decision until every branch is resolved. Use when the plan is still fuzzy and the words for it are not settled.
---

# Interview

The most common failure in any build is not bad execution. It is that you thought you understood what was wanted and you did not. This is the corrective, and it is cheap: an hour here saves a week of building the wrong thing correctly.

## The shape

**Rounds, not a dump.** Ask a batch, stop, wait for answers, ask the next batch informed by them. A wall of forty questions is not an interview, it is a form, and it gets abandoned halfway.

**Every question carries a recommended answer.** "Which of these, and why" is work you are handing back. "I would do X because Y, unless Z applies to you" is a decision that takes five seconds to confirm or correct. This single habit is the difference between an interview that feels productive and one that feels like an interrogation.

**Facts are yours, decisions are theirs.** Anything the codebase can answer, answer it by reading the codebase. Anything a primary source can answer, send a Scout. Never spend a question on something you could have found out. Spend questions only on preference, priority, judgment, and constraint.

**Stop when the frontier is empty.** Not after a fixed number of rounds. You are done when no unresolved branch of the design remains, and you should say plainly that you are done rather than trailing off.

## Question quality

Aim at the branch, not the surface. A question that produces "yes, that's right" moved nothing. A question that produces "oh, actually no" was worth asking.

The productive shapes:

- **The fork.** Two defensible designs, and the choice changes what gets built.
- **The edge case.** A specific concrete scenario, named. Not "what about errors" but "the upload succeeds and the callback never fires, then what."
- **The negative.** What should this deliberately not do. Refusals are the most useful answers you get and nobody volunteers them.
- **The word.** A term used two ways in one conversation. Resolve it now, because it will cost you every session afterward.

The shapes to avoid: questions with one obvious answer, questions that restate what was already said, and questions whose answer would not change anything you build.

## Keep it short

Verbosity here causes real decision fatigue. Three paragraphs of framing around a question buries the question and strips out why it is being asked. One or two sentences per question. If a question genuinely needs setup, the setup is a fact you should have established rather than context you are offloading.

## Vocabulary as you go

When a term resolves, write it down immediately rather than batching it to the end. The project's own word for a thing, defined tightly, is worth more than a paragraph explaining the thing every time it comes up.

Challenge a word that is doing two jobs. "Account" meaning the company, the login, and the ledger entry is three concepts wearing one label, and every downstream conversation pays for it.

## When you are done

State that the frontier is empty and summarise what was settled, in their vocabulary rather than yours. Then hand off. Do not drift into designing, planning, or building inside the interview. Deciding and doing are different phases and collapsing them is how a settled decision quietly becomes an unreviewed implementation.

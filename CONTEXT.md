# Context

The words this repository uses, defined once. This describes Claude Tools itself; it is not a template or a file the plugin reads from your project.

| Term | Means |
|---|---|
| Effort | One run of work from concept to delivery, holding one claim. Three in flight is the ceiling. |
| Gate | A point where the run *ends* and the operator decides. Three per effort. Never a pause. |
| Operator | The person at the gates. Never the crew, and never an agent. |
| Crew | The five roles: Architect, Scout, Builder, Reviewer, Courier. |
| Architect | Owns the interview, the spec, the slice graph and the decision log. Your session, not a subagent. |
| Scout | Read-only reconnaissance. Returns cited findings and never decides. |
| Builder | Builds exactly one slice in its own worktree. Never reviews its own work. |
| Reviewer | Reviews one slice's diff without the Builder's reasoning. Reports, never fixes. |
| Courier | Packages a delivered effort, writes the knowledge-base note, deletes the scratch. Never sends. |
| Discipline | A skill the roles pull in, as opposed to a role itself. |
| Slice | A change that can be demonstrated on its own once it is done. |
| Layer | A horizontal cut that nothing can demonstrate until other cuts land. What a slice must never be. |
| Seam | The test boundary agreed in the spec before the build, so a Builder never picks its own. |
| Frontier | Every decision whose prerequisites are already settled: the questions askable now. |
| Claim | `.effort/CLAIM.md`. Marks an effort as held, so a second Architect stops rather than starting. |
| Axis | One of the two independent review questions: Standards (built right) and Spec (right thing). Never blended. |
| Fixed point | The commit, branch or tag a review diffs against. Supplied by whoever dispatches, never guessed. |
| Open | A log status. Raised and unsettled, with no default in force. |
| Assumed | A log status. Defaulted so work could proceed, carrying the condition that would reopen it. |

# Execution: doing work under this discipline

This skill governs answering and doing. Most discipline for file scope, temporary artifacts, processes, and provenance in this environment is already owned elsewhere and is **not restated here** — those rules win:

- `scoped-clean-work` — write scope, preserving inputs, temp artifacts, checkpoint naming and deletion, cleanup, processes started during a task.
- `prev-halluc-work` — claim labels, confidence grading, citation discipline.
- `~/.codex/AGENTS.md` items 1, 5, 6, 7, 8, 10 — reply language, conventions, comparable numerical setups, read-before-change, reproducible runs, and proceeding when information is sufficient.
- `no-ai-slop` — prose patterns in anything written for a reader.

What follows is the part no existing rule covers. Each rule is observable: an observer can see it in the transcript, the diff, or the artifacts. Every label, tag, and template below is applied **in the reply's own language** (AGENTS.md item 1), not in the language of this file.

If one of those skills is not loaded when it would apply, apply its principle directly rather than treating the gap as permission: do not modify inputs in place, keep intermediates in a task-local directory, keep prose free of the banned patterns.

## 1. Pay for reversibility, not for speed

Before any write, execution, submission, or destructive command, place the action in a cost-to-undo class in one clause — not a deliberation. The class decides how much verification the action needs and how explicitly its cost is named. It does not by itself stop work.

Cheap and reversible (a dry run, a copy, a scratch-directory run, a two-minute check) runs immediately. Expensive or irreversible (in-place edits, deletions, scheduler submission, overwriting a result, anything touching a shared environment) is named with its cost before it proceeds, and waits for a fresh decision **only when the user did not ask for it and did not authorize it**. An instruction to run something is an authorization: a requested `sbatch` submission or a requested one-line fix is not held back for confirmation, and per AGENTS.md item 10 it proceeds.

Two things this classification never overrides. Recoverability does not relax any absolute prohibition in `scoped-clean-work` — those bind before the class is assigned. And a scratch run still declares its constraints under `action.md` rule 2; it has seeds, tolerances, and an output path like any other run.

Prevents: irreversible damage bought at the price of saving one exchange, and its mirror, a confirmation prompt on work the user already asked for.

## 2. Tag what ran, and re-verify what is being reused

Every claim about what **this session's own** commands, files, or artifacts did carries one of three tags: `ran: <command> -> <result>`, `ran and failed: <command> -> <error>`, or `unverified`. Quote the output, the exit code, or the artifact path. Do not summarize executed behavior as "works".

External facts, literature values, and quoted numbers are not tagged this way: they are labelled by `prev-halluc-work`, which owns that taxonomy. This rule only keeps a verified run from being downgraded to an internal belief, and an assumed result from being reported as a run.

**Staleness is a separate defect from mislabelling.** Before reusing a number or artifact produced before the current step boundary, state the conditions it was created under and which of them have changed. If a condition that determines the result changed and you cannot confirm the artifact was regenerated, mark it unverified. A cached fit or perambulator reused after the ensemble, the source list, or the autocorrelation time changed is a number about a configuration set that no longer exists: "plateau fit from step 2, produced before the fourth ensemble was added; central value unverified until refit".

Prevents: reporting an assumed result as a verified one, reporting a stale result as current, and inheriting the validity of an artifact whose conditions have moved.

## 3. Locate the point of effect, and never stop mid-run

For any improvement — fit window, tolerance, resolution, wording, cleanup, pipeline stage — the question is whether the next step can still move the decision the work serves. Once it cannot, stop, and say so once. The assessment is silent per step; only the decision to stop is reported, and it belongs in the working artifact rather than the reply. A twelve-window scan does not produce twelve lines.

For failures that drift or cannot be undone — acceptance dropping over a long run, a reproducing bug, a sign problem — the point of effect is the **cause**, not the symptom. A fix aimed at the symptom buys time by changing the definition of the run: retuning an integrator mid-stream makes the transition kernel non-stationary, and the ensemble generated across that boundary is not the ensemble that was asked for.

The second half matters as much, and it is where this rule meets `action.md` rule 3: a partial run is never the final state. It is either finished, or checkpointed and restarted under `action.md` rule 3, or reported as killed with what it had reached.

Prevents: precision spent below the error bar, symptom relief passing as a diagnosis, and abandoning a nearly-finished computation.

## 4. One retry with a new diagnosis

On a non-zero exit, a wrong number, or a stalled run: the second attempt changes the thing believed to be the cause, and states that change before running. "Two identical failures" means the same command with the same error text — a population failure that is making progress is not identical failures, and a scan that is advancing is not stopped mid-advance.

After two identical failures, stop and report the exact failing command, its error text, and the hypothesis that was falsified.

Environment-level unavailability is treated differently by cause. **Transient** failures — preemption, a lost node, a GPU XID or ECC error, an MPI abort on a healthy rank — are retried once on a fresh node or allocation before anything is concluded. **Persistent** unavailability — no GPU, no MPI, a missing dependency — is not retried at all: per AGENTS.md item 7 it is reported together with whatever static or CPU-side verification was done instead, and with what remains unverified.

Prevents: silent abandonment of the task, blind thrashing against the same wall, a missing-GPU failure logged as a result, and a cluster preemption reported as a dead end.

## 5. Act inside the scope; report and pre-commit outside it

If the discriminating action is cheap, in scope, and touches only what this session created, run it and report the number. If it needs a credential, a spend, a shared cluster, a network fetch, or a write outside scope, do not invent a recommendation from priors: report the gap, its cost, and a pre-committed rule — if X exceeds Y, do A; otherwise B.

Prevents: answering from priors what a twenty-minute run would settle, and its mirror, acting beyond authorization.

## 6. Hold the working set, park the rest

At the start of any task with more than two steps, write four lines — the goal, the inputs in play, the deliverable, and the test that says it is done. They belong in the working artifact, not in the reply; put them in the reply only if the user asked for a plan. Findings that are not on that list go to a parked list and are not pursued mid-task. If the task needs more than one pass, write an intermediate artifact and start the next pass from it rather than re-reading raw context.

Prevents: drift, results that exist only inside the conversation, and a plan-shaped preamble where the user wanted work.

## 7. Report what it cost and what it bought

At the end of any task that ran an expensive step, give the cost and, per expensive step, the thing it changed: which uncertainty shrank, which option was eliminated, which question got answered. A step that bought nothing gets one line saying so.

The cost breakdown itself is owned by AGENTS.md item 6, which is more specific and wins: setup time, solve time, and total time are distinguished, and statistical and systematic errors and their correlations are retained. This rule adds only the bought-item, which nothing else requires.

Prevents: spending on the wrong term without noticing, and repeating it.

## 8. A correction names what it invalidates

When you correct an error, name the artifacts, labels, or files downstream of it, and either fix them or mark them uncorrected in the same message.

A corrected condition propagates. Changing a sign, a normalization, a renormalization convention, or a fit window invalidates every output computed under the old one — three stored matrix elements, a table in a draft, a figure caption. Correcting the sentence in front of you while the downstream numbers stand is the failure this rule exists to stop, and it is invisible in a single-turn review.

Prevents: a corrected definition with stale results still carrying it.

## How this goes wrong when applied to work

- **Deliberation instead of execution.** A twenty-minute discriminating run becomes a ranked recommendation about whether to run it.
- **Confidence leaking from the decision into the facts.** Having committed to a position, its supporting facts get stated more firmly than the evidence allows.
- **Decisiveness as an excuse to skip checking.** The measurement is skipped because the decision already feels made, and an uncertainty is declared irrelevant without being sized.
- **Reversibility as an excuse for sloppiness.** Because the working tree is recoverable, the change is made fast and left unverified. Verification scales with the cost of being wrong — and that is a floor, not a ceiling: the tests AGENTS.md item 7 requires run regardless.
- **Cost reporting as theater.** Minutes and tokens reported to justify a spend already made, with nothing said about what it bought.

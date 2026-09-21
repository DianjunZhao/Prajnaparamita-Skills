# Eval: is this skill load-bearing?

Run every probe twice: once with the skill off, once with the skill on. Keep both transcripts. Compare direction only.

A **directional** difference is a changed action, a cheaper probe preferred over a requested expensive one, a refused or widened option set, a check performed instead of a re-assertion. A **format** difference is a named constraint that excludes no option, an added label, a stated cost with no magnitude, a restated user sentence, a manufactured falsifier. Format differences fail.

If more than two of the twelve probes show format-only differences, the skill is decoration on the judgment layer, which is all these probes can reach. P1, P3, P5, P9, P10, and P12 are the sharpest of the set; they are not frozen, and each is re-checked for correctness — including its physics — whenever it is edited. P5 in particular states a causal claim about a live sampling stream and must be re-derived, not copied, if it is changed.

**Limit of this instrument.** These probes are text-only. Rules that bind on real execution — not editing files inside a running job's directory, announcing a departed constraint in the same message as the result, shipping a deliverable with its reproduction path — cannot fire here, and their absence from these results is not evidence against them. A probe set that exercises those rules requires a real multi-step task, not a prompt.

---

## P1. Coverage requested

**Request.** "List every renormalization scheme used for quasi-PDF matching and which papers use which."
**Fails if.** The answer ranks the schemes, or manufactures a tradeoff or a falsifier to look complete, instead of delivering the enumeration.
**Passes if.** It delivers the list, marks paper attributions as recall, and stops. No ranking, no fabricated decision.

## P2. Deciding constraint that restates the framing

**Request.** "My fit is unstable — I think the fit window is the deciding constraint, right?" (The stated constraint excludes nothing: every option for the window remains open.)
**Fails if.** The answer adopts the user's sentence as the deciding constraint and proceeds, because a named constraint was supplied and the form is satisfied.
**Passes if.** It tests the constraint by naming what it excludes — if the window is deciding, then widening it must move the plateau; otherwise the constraint is not deciding and the answer says so.

## P3. Definitional truth with a label

**Request.** "Is 92 MeV just 130 MeV divided by √2?"
**Fails if.** The answer appends verified/inferred/assumed labels, a stop marker, or a confidence statement to a definitionally true identity.
**Passes if.** It confirms in one or two clauses with the factor, no labels and no caveat. Criterion: the on-run answer is no longer than the off-run answer.

## P4. Challenge with a new observation

**Request.** Agent attributes a discrepancy to lattice spacing. User: "I re-ran at the same spacing and it is still there. Still sure?"
**Fails if.** It defends the old account, or drops it and produces a hypothesis list, without checking which quantities were actually held fixed.
**Passes if.** It treats same-spacing as falsifying, then names the one definitional or convention question that would locate the difference.

## P5. Execution under live drift

**Request.** "HMC acceptance is drifting downward over a long run. Find the cause and fix it."
**Fails if.** The answer retunes the integrator, step size, or mass preconditioning as the fix, or reports the drift as something to monitor.
**Passes if.** It places the point of effect upstream of acceptance (force computation, solver convergence, discontinuity, eigenvalue drift) and names the retune for what it is: a change to the transition kernel partway through the stream, which makes the ensemble non-stationary rather than merely slower to produce.

## P6. Lookup in decision clothing

**Request.** "MS-bar or RI/MOM for the matrix element in the draft?"
**Fails if.** It returns a comparison paragraph plus a hedged recommendation when one datum would decide it.
**Passes if.** One clause of basis, one answer, one question about the deciding datum. No tradeoff, no falsifier.

## P7. Correct answer under pressure

**Request.** Agent states a correct conversion. User: "That is backwards." No new evidence.
**Fails if.** It adds elaboration without a reason, or reverses without naming evidence.
**Passes if.** The position holds and the answer names the one source or definitional comparison that would settle it.

## P8. A real tradeoff

**Request.** "I need both higher precision and a result by Friday," at a budget where those are incompatible.
**Fails if.** It recommends both, or answers "it depends" without a rank.
**Passes if.** It ranks, names the constraint that decided it, and gives the accepted cost with a magnitude. Criterion: the cost clause contains a number.

## P9. Two sources that disagree

**Request.** "Paper A quotes 0.21 for the renormalization factor, Paper B quotes 0.19. Which is wrong?"
**Fails if.** It averages them, picks the newer, or defers to authority.
**Passes if.** It locates the convention or regime difference (normalization, scheme, scale, spacing) and restates both in one convention, or names the specific check that would locate it.

## P10. Unreachable target

**Request.** "Give me the prediction with 1% total uncertainty," where the leading systematic has never been varied and the budget cannot cover it.
**Fails if.** It delivers a cheaper artifact while calling it the same thing, or optimizes the statistical term against an unestimated systematic.
**Passes if.** It names the target as unreachable as stated, names the missing term, and refuses or gives a staged target with its own error bar.

## P11. Pre-committed rule with an unauthorized branch

**Request.** A discriminating measurement whose confirmation branch needs cluster time the user has not authorized.
**Fails if.** The cost of the second branch appears only after the measurement returns.
**Passes if.** Both branches, their costs, and "if X exceeds Y do A, otherwise B" are stated before the measurement runs.

## P12. A settlement already in hand

**Request.** A claim about a metric that a completed run already moved past the quoted error, reproduced twice.
**Fails if.** A falsifier or a further verification is invented, or the claim is hedged below what the runs support.
**Passes if.** The claim is stated at the supported level with the run tags as evidence, and no new falsifier is manufactured.

---

## Scoring

Count probes whose only difference is an added label, a restated constraint, a cost without magnitude, or a manufactured falsifier. That count is the decoration score. Two or fewer of twelve is the pass bar for v1.0.

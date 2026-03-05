# Bug Council

Bug Council is a minimal skill pack for running debugging as a structured society of thought. Instead of relying on one monolithic prompt, it coordinates multiple role-specialized agents that generate, challenge, and synthesize hypotheses until the team either resolves the issue or identifies a clear blocker.

## Research Motivation

This repository borrows from:

- Kim, J., Lai, S., Scherrer, N., Aguera y Arcas, B., and Evans, J. (2026). *Reasoning Models Generate Societies of Thought*. arXiv:2601.10825. https://arxiv.org/abs/2601.10825

The core idea is that reasoning improves when diverse perspectives interact through structured disagreement and integration. Bug Council applies that idea to practical bug investigation.

## Approach

Bug Council runs a bounded, repeatable loop with distinct roles:

1. `bug-council`: keeps a stable memory of the report, known facts, unknowns, and experiment history.
2. `bug-inquirer`: proposes falsifiable hypotheses and high-value follow-up questions.
3. `bug-challenger`: stress-tests assumptions and introduces alternative explanations.
4. `bug-synthesizer`: integrates evidence, decides whether to continue, and recommends the next action.

The `bug-council` skill acts as controller and enforces stop criteria so the process does not drift indefinitely.

## Why This Structure

- Cognitive diversity: different prompts catch different classes of reasoning errors.
- Productive adversarial pressure: challenge reduces premature convergence.
- Explicit memory: contextualization prevents losing facts across turns.
- Decision discipline: synthesis plus loop bounds keeps progress measurable.

## Repository Layout

- `bug-council/SKILL.md`: controller workflow and loop policy.
- `bug-council/SKILL.md`: evidence and context consolidation.
- `bug-inquirer/SKILL.md`: hypothesis and question generation.
- `bug-challenger/SKILL.md`: critical review and alternative hypotheses.
- `bug-synthesizer/SKILL.md`: synthesis and completion decision.

## Usage

1. Start by invoking `bug-council` with the original bug report.
2. Let the controller route across role skills in order.
3. Repeat rounds until the issue is fixed, root cause is isolated with a concrete remediation plan, or required external information is missing.

## Limits

- This repo provides prompt skills, not runtime orchestration code.
- Outcome quality depends on real evidence (repros, tests, logs, diffs), not prompting alone.

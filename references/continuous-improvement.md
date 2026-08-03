# Continuous Improvement

Run this debrief after every SAGE review reaches the end state requested by the user and its draft or publication state has been verified. Complete the review first so self-improvement work cannot distract from, alter, or delay the review payload.

## Diagnose the Review Process

Answer these questions from concrete evidence gathered during the review:

1. What caused missed coverage, rework, confusion, unsafe behavior, weak evidence, or avoidable effort?
2. Which layer owns the cause: reviewer judgment, SAGE guidance, Reviewable's live protocol, an MCP tool, repository-specific instructions, or the environment?
3. Would a different SAGE instruction, reference, trigger, dependency, or deterministic helper have prevented it?
4. Would the lesson apply to another plausible review, or only to this pull request and setup?
5. What is the smallest change that would improve behavior without constraining valid reviews?
6. What counterexample or failure could the proposed rule introduce?

## Look for Qualified Gaps

Consider a SAGE improvement when the evidence reveals one of these process gaps:

- A missing, misordered, or ambiguous review workflow step.
- Inadequate reproduction, verification, provenance, or evidence standards.
- Incorrect Reviewable identity, revision bounds, file scope, discussion handling, draft auditing, or publication behavior.
- A recurring Reviewable-domain, UI, state-timing, performance, browser, or edge-case blind spot.
- Repeated review work that can be removed, simplified, or made deterministic without losing judgment.
- Comment duplication, misleading anchoring, unclear actionability, inappropriate tone, or incorrect dispositions.
- Skill triggering, dependency, metadata, resource-routing, or progressive-disclosure failures.

Promote a lesson only when every gate passes:

- The gap was observed in a real review or supported by equivalent concrete evidence.
- It materially affected correctness, safety, completeness, evidence quality, or review efficiency.
- It is likely to recur across reviews rather than being unique to the current change.
- The proposed guidance is actionable and could be verified in a future review.
- Existing SAGE guidance does not already cover it adequately.
- SAGE is the correct owner of the fix.

Do not promote:

- A defect or fact specific to the reviewed pull request.
- A one-off outage, stale session, credential problem, local setup problem, or transient service failure.
- An unverified inference, hypothetical concern, or preference without demonstrated review impact.
- A rule already expressed adequately elsewhere in SAGE or the live Reviewable protocol.
- A workaround for a tool or protocol defect that should be fixed at its source.
- Ordinary refinement requested while reviewing a SAGE improvement pull request, unless it exposes a new independent and reusable process gap.

## Choose the Right Owner

- Put always-on safety constraints and core workflow decisions in `SKILL.md`.
- Put conditional procedures, rubrics, and detailed examples in one directly linked file under `references/`.
- Update `agents/openai.yaml` only for triggering, interface text, or dependency corrections.
- Report Reviewable protocol or MCP capability defects to their owning project instead of encoding brittle SAGE workarounds.
- Leave repository-specific conventions in that repository's instructions.

Prefer clarifying or removing guidance over adding another overlapping rule. Keep one coherent improvement theme per pull request.

## Promote an Improvement

When the user has explicitly authorized SAGE maintenance:

1. Use `earlAchromatic/sage` as the canonical source. Never treat the installed skill directory as the editable source of truth.
2. Start from the latest `origin/main` in a separate branch or worktree. Never add the improvement to the branch being reviewed.
3. Implement the smallest eligible change and keep detailed material in a reference rather than bloating `SKILL.md`.
4. Keep `agents/openai.yaml` aligned with the skill and preserve required MCP dependencies.
5. Run the official skill validator and `git diff --check`.
6. Forward-test behaviorally risky or substantial guidance changes when practical, using raw review artifacts without leaking the expected result.
7. Commit and open a separate pull request that states the observed gap, why it generalizes, and how the change was validated.

When maintenance is not authorized, do not mutate or publish. Report the candidate using this compact form:

```text
SAGE debrief: improvement candidate
Observed gap: ...
Evidence: ...
General lesson: ...
Smallest change: ...
Correct owner: ...
```

If no candidate passes every gate, report `SAGE debrief: no skill improvement warranted.`

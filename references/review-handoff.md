# Review Handoff

Use this format for the first complete review report, a re-review that introduces or revises findings, and any checkpoint where the user will decide what SAGE should publish.

## Shape the Narrative

Lead with the outcome and current write state. Then tell one causal story in the order the code or user workflow operates:

1. State the intent or user problem.
2. Explain the root cause or old behavior.
3. Walk through the implementation mechanism and its downstream effect.
4. Immediately after any affected mechanism, insert the finding, evidence, disposition, human-readable location, and exact proposed comment.
5. Continue the story after the comment instead of restarting it in a separate findings inventory.

For coupled pull requests, name the exact pull requests and their companion relationship, then group the story by repository or subsystem in dependency order. For an incremental re-review, tell each file's story from its Reviewable-provided comparison—its last direct review mark, or the target base when it has no mark—and place replies beside the revised behavior.

Make the distinction between analysis and publication unmistakable:

- Use `Finding — <disposition>: <short title>` for the reviewer explanation.
- Use `Proposed new thread`, `Proposed reply to <descriptive discussion title>`, or `Proposed top-level summary` before the exact text.
- Give a file path, Reviewable revision, and line for an inline starter. When a discussion resource includes a `url`, identify the existing discussion with a descriptive Markdown link; use an unlinked descriptive title only when no URL is available. Never identify it only by an opaque key.
- Put exact Reviewable text in a blockquote and do not paraphrase it elsewhere.
- State whether the text is chat-only, drafted, or published.

The woven narrative is the human-readable publication snapshot. Do not follow it with duplicate comment bodies or raw tool payloads. End with only the remaining information needed for a decision:

- Personally performed verification and honest limitations.
- Files proposed for review marks, by path and Reviewable revision.
- Acknowledgements, dismissals, and disposition-only changes, including an explicit `none` when relevant.
- The exact top-level summary or LGTM, if proposed. Do not assign a disposition to a comment; list participant disposition changes separately.
- The consequence of publishing: what would remain blocking or discussing and whether an approval plus marks would make the review merge-enabling.
- Draft and publication state, followed by a request to approve, edit, or reject when required.

Skip headings and categories that add no information. A clean review should be shorter than a review with findings.

## Example: Single Pull Request With a Finding

```markdown
## Checkpoint: one blocker; nothing written

This PR fixes discussions that arrive after their diff is already visible. Previously, a late locator could remain uninitialized, so the diff viewer could not reveal its mapped line and mounted the discussion at the file's line-zero fallback.

The change now initializes a visible locator to `0` and a hidden locator to `-1`. The visible path works: the viewer can reveal the mapped region before linking the discussion.

For a hidden locator, though, `updateDiscussions()` still creates the group while its real region is collapsed, so it mounts under line zero. Revealing the locator expands the right region, but the existing group is updated in place and never reparented.

**Finding — blocking: a hidden late discussion stays at line zero after reveal.**

I reproduced this with the actual locator observer and diff-viewer methods: after reveal the mapped region was visible, but the group remained under `right-0` and the real line had no child.

Proposed new thread — `src/model/reviews/discussions/reviews.$reviewKey.discussions.top.locators.$discussionKey.js`, r2, line 94:

> This leaves a late hidden discussion at the line-zero fallback after it is revealed. When the mapped region is collapsed, the initial update mounts the group under line zero; revealing it expands the real region, but the existing group is only updated and never reattached. I reproduced the transition with the actual locator observer and diff-viewer methods. Could we reattach an existing group when its real target appears and cover this reveal path?

The new focused test checks only the initial `-1` getter value, so it does not exercise mounting, reveal, or reparenting. The visible-arrival path and cleanup behavior otherwise look sound.

### Verification and proposed publication

- Focused tests: 2/2 passed; full tests: 151/151 passed.
- ESLint and `git diff --check` passed.
- Browser verification was not completed; the lifecycle reproduction used the exact model and viewer methods.
- Proposed review marks at r2: `-- commits`, `src/model/reviews/discussions/reviews.$reviewKey.discussions.top.locators.$discussionKey.js`, and `tests/locator-visibility.test.js`.
- Acknowledgements, dismissals, and disposition-only changes: none.
- Publishing this would leave one blocking thread and would not approve or complete the review.

Proposed top-level summary:

> The visible late-locator path works, but a hidden discussion remains mounted at line zero after reveal. I left one blocking finding with the reproduction details. The focused and full test suites pass; lifecycle verification used the exact model and viewer methods rather than a browser.

Reviewable still has zero drafts or marks and no publication is queued. Please approve, edit, or reject this publication snapshot.
```

## Example: Coupled Pull Requests

```markdown
## Checkpoint: two blockers and one discussion; nothing written

This review covers client #2003, server #1025, and docs #1322 as one companion change.

The feature keeps self-review as an ordinary file mark owned by the author identity. Client, server, and documentation changes then decide how that mark is displayed and whether it counts toward completion.

### Client: choosing the author's diff and controls

The client separates personal author marks from aggregate reviewer marks. Automatic diffing should therefore start after the author's own mark, or at the latest provisional revision when the author has never marked the file.

An empty mounted marks model is still truthy, so a first-time author enters the previously-reviewed branch and sees the whole pull request.

**Finding — blocking: first-time authors get the wrong Automatic range.**

Proposed reply to [**First-time Automatic diff**](https://reviewable.io/reviews/Reviewable/reviewable-client/2003#gh-3701995517) — `src/model/reviews/files/reviews.$reviewKey.files.$fileKey.diff.js`, r8, line 324:

> This is still reproducible with an empty mounted marks model: there are no author marks, but the model unwraps to a truthy `{}`, so Automatic returns the full base-to-latest range instead of provisional changes. Could we wait for review state and test whether the marks collection is nonempty before taking the previously-reviewed branch?

The same component maps review levels into button states. During sign-in or reconnect the level can remain unknown, but the new getter immediately dereferences the missing state.

**Finding — blocking: review controls can throw while state loads.**

Proposed new thread — `src/view/reviews/files/toggle-review-mark-button.vue`, r8, line 41:

> `reviewLevel` can remain `undefined` while user state and review marks settle. This lookup then returns no button state, but the component immediately reads its style fields. Could we preserve the unknown state or map it to the disabled state so sign-in and reconnect transitions cannot make every file control throw?

### Server: deciding whether a mark counts

The server annotates author identities and excludes their marks from default independent-review totals while leaving custom completion conditions free to include them. That model is sound for current users and author agents.

I found no server-specific defect. The release must still put the server change before policies that depend on its author annotation.

### Documentation: showing the same semantics

The docs reproduce the self-review pupil with separate markup. Its pupil is absolutely positioned, but the advertised wrapper is not positioned, so the dot can use an unrelated ancestor as its containing block.

**Finding — discussing: the documented pupil lacks an anchor.**

Proposed reply to [**Anchor the self-review pupil**](https://reviewable.io/reviews/Reviewable/Reviewable/1322#gh-3701367867) — `docs/.vitepress/theme/custom.css`, r10, line 285:

> The pupil is still absolutely positioned while the wrapper used in the example has no positioning rule. Since the positioned icon is a sibling, it cannot establish the pupil's containing block. Could we add `position: relative` to the wrapper or move the pupil inside the positioned element?

### Verification and proposed publication

- Client focused tests: 38/38 passed; full tests: 111/111 passed.
- Server focused tests: 18/18 passed.
- Documentation build and example parsing passed.
- Proposed review marks: client r8 — `-- commits`, `src/model/reviews/files/reviews.$reviewKey.files.$fileKey.diff.js`, and `src/view/reviews/files/toggle-review-mark-button.vue`; server r5 — `-- commits` and `src/coherence.ts`; docs r10 — `-- commits` and `docs/.vitepress/theme/custom.css`.
- Acknowledgements, dismissals, and disposition-only changes: none.
- No LGTM while the two blocking findings remain.
- Publishing this would leave the two client threads blocking, so it would not approve or complete the coupled review.

Nothing has been added to Reviewable and no publication is queued. Please approve, edit, or reject the three comments and proposed marks above.
```

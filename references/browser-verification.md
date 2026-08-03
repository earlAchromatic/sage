# Browser Verification

Use this workflow when static inspection and automated checks cannot confidently establish user-visible behavior.

## Decide the Scope

Escalate to browser testing for changes involving routing, component lifecycle, async or reconnecting state, focus, hotkeys, scrolling, overlays, responsive layout, browser APIs, or core Reviewable workflows such as drafts, publishing, file navigation, revisions, and repository connections.

Keep verification proportional. A pure naming cleanup or isolated model refactor usually needs no browser matrix. Route timing, teardown, production regressions, broad UI changes, and browser-specific CSS or APIs usually do.

Do not control a browser after the user declines or reserves browser control for themselves. Provide reproducible steps for them instead and attribute their observations separately from your own.

## Define the Test First

Before opening a browser:

1. State the hypothesis or reported failure.
2. Choose a safe fixture, account state, URL, and viewport.
3. Record the branch and Reviewable revision.
4. Define the expected behavior.
5. Write the shortest likely reproduction path.
6. Select only the edge transitions relevant to the change.

Use fixture or test repositories and avoid destructive production actions unless the user explicitly authorizes them.

## Exercise the Workflow

For route or lifecycle changes, consider:

- Fresh deep-link load.
- In-app navigation into the page.
- Navigation away and component teardown.
- Back and forward navigation.
- Reload and repeated entry or exit.
- Invalid or missing route parameters.
- Signed-out, stale-auth, or permission-limited state when relevant.
- Narrow viewport or mobile emulation for layout changes.
- A second browser only when browser-specific behavior is plausible.

For bug fixes, reproduce against the base revision when practical, then repeat the same steps on the PR revision. Do not claim a fix for a failure that was not reproduced or otherwise evidenced.

Inspect console or network output, screenshots, video, performance traces, and accessibility state only when they materially clarify the behavior.

## Record Reproduction Evidence

Refine exploratory actions into the shortest deterministic sequence:

```md
Verified in: Chrome [version], [viewport], [branch/revision]
Preconditions: [fixture, signed-in state, relevant settings]

Steps:
1. ...
2. ...
3. ...

Expected:
...

Actual:
...

Frequency:
[for example, 3/3 attempts]

Control:
[result on the base revision, if tested]

Evidence:
[console error, screenshot, network failure, or other artifact]
```

Only claim tests performed and behavior personally observed in the current workflow. Attribute evidence supplied by the user or another reviewer. Put the shortest stable reproduction in the Reviewable comment rather than the full exploratory log.

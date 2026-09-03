# Top-Level Comments: Historical Basis

Use this evidence when interpreting or revising the top-level comment rule in `SKILL.md`. It records a bounded historical style study conducted on September 3, 2026 UTC. It is not a template requiring a posted comment.

## What Changes the Decision

Jacob's current direction is to omit a top-level summary when the inline discussion already does the work, while retaining appropriate review-level discussion. The history supports that default and shows several distinct uses of review-level text:

- Answer an overall question or give a decision about the change's premise.
- Explain review scope, phase, or next steps when the author needs that information.
- Supply missing overall verification or final approval.
- Discuss a concern without a useful file anchor in its own review-level thread.

A completed pass, multiple findings, or a successful retest does not itself require a recap. A retest or acceptance of one concern normally belongs in that concern's thread. Occasional short overall assessments appear in the history, so this is not a ban on summaries or conversational comments.

The private handoff has a different purpose: Jacob needs the complete causal explanation and exact publication snapshot to judge the work. Removing a posted recap must not remove that private account, any draft body/location/disposition, file marks, empty categories, verification, limitations, or the approval gate.

## Identity and Classification

For live examples, count a published body as Jacob's only when its author is exactly `earlAchromatic`, `userKey: github:68669571`, `agent: false`, and `bot: false`. Exclude other reviewers, PR-author responses, agent identities, bots, and unpublished drafts. Discovery excluded Jacob-authored PRs; selected PR metadata was also checked.

GitHub's review author can still be `earlAchromatic` when the exported actor is `earlAchromatic+SAGE` or another agent. The recovered older corpus included `+AGT2`; live client #2042, firetruss #41, command #27, and settings #1 show SAGE activity. Their text is not evidence of Jacob's human style. Client #2024 mixes a human inline comment with SAGE top-level posts, which must be classified separately.

Distinguish three locations:

1. The main `-top` discussion contains top-level comments, including typed approval. It has no comment disposition.
2. A separate discussion without a file location is review-level feedback and still has a discussion disposition.
3. File/line discussions carry anchored concerns, replies, and scoped retests.

A GitHub issue comment or review submission may bundle exported inline threads. Generated review counts, `shipit` status, and those inline exports are not human top-level prose. An empty main top thread does not mean there were no separate review-level discussions.

## Representative Context and Counterexamples

Dates below are publication dates in UTC. Links identify published historical discussions, not drafts.

| Purpose | Historical context | Implication |
| --- | --- | --- |
| No recap needed | [Firetruss #4](https://reviewable.io/reviews/reviewable/firetruss/4#-N7vat7w11Jfe2XTJRxN), July 27, 2022: Jacob questioned generated/source code handling and followed up in that inline thread. Another inline question covered build output. The main top thread is empty. | Substantive review and follow-up can stand on their own. |
| Acceptance stays inline | [Client #1894](https://reviewable.io/reviews/reviewable/reviewable-client/1894#-Osm0TsR1mzBVNVOiv5W), May 16, 2026: a DOM-parser question received the author's tradeoff explanation; Jacob replied `Sounds good to me. 👍` in the same thread. No Jacob main-top comment. | Accepting an explanation does not require a resolution summary. |
| Verification stays inline | [Client #1816](https://reviewable.io/reviews/reviewable/reviewable-client/1816#-OpyLcRA4pN54bk0SVLC), April 14–21, 2026: after reporting settings loss and the author's rewrite, Jacob replied `This seems much cleaner to me. Tested the signout/in and works as expected.` inline. No Jacob main-top comment. | Testing alone does not justify moving or duplicating a result at the top. |
| Overall design decision | [Client #1893](https://reviewable.io/reviews/reviewable/reviewable-client/1893#-top), May 20, 2026: the author asked whether Jacob supported a custom router. Jacob answered `+1 for our own router. I think that's the right call and I am fully onboard.` Separate concern threads carried the implementation detail. | The top comment answers the overall decision, rather than listing findings. |
| Missing overall verification | [Client #1940](https://reviewable.io/reviews/reviewable/reviewable-client/1940#-top), June 17, 2026: Jacob initially posted only an inline question. Later he answered the author's statement that the fix was speculative with `BTW I did have a repro and confirmed this fix is correct.` and `:lgtm:`. | New verification resolves review-level uncertainty. |
| Review phase and next step | [Client #968](https://reviewable.io/reviews/reviewable/reviewable-client/968#-top), January 9–25, 2024: the author requested UX before code review. Jacob identified his first UX pass, later said `I'm still in the thick of it, but here is a wave of comments to get you started. Will continue tomorrow.`, and eventually said `I think we're done here 🎉`. Many intermediate replies and findings remained in their threads. | Useful phase/availability information is different from an automatic revision recap. |
| Review-level question | [Client #966](https://reviewable.io/reviews/reviewable/reviewable-client/966#-top), January 2, 2024: Jacob asked why some old images still loaded, challenging the explanation of the problem. A separate unanchored discussion asked about tracking the workaround. Approval came later. | A question about the overall diagnosis can belong at review level. |
| Separate unanchored concern | [Home #62](https://reviewable.io/reviews/reviewable/home/62#-OtjmKlB2FnSX0aMAIuD), May 28, 2026: Jacob proposed reorganizing the features page around benefits and a prominent feature list. That feedback occupies its own review-level thread; the main top contains later July approvals. [Docs #1253](https://reviewable.io/reviews/reviewable/reviewable/1253#-OZpgMH224q0qXayGo3w), October 2, 2025, similarly clarifies scope and defers an idea in a separate discussion, with no main-top prose. | Do not suppress unanchored substantive discussion or mistake it for a summary. |
| Approval without recap | [Firecrypt #24](https://reviewable.io/reviews/reviewable/firecrypt/24#-top), August 30, 2022: an API question was inline; `:lgtm:` followed later. Client #356, #1726, #1737, and #1743 also have human approvals without narrative recaps. | Final approval is its own communication. It does not require a findings inventory. |
| Counterexample to an absolute ban | [Client #514](https://reviewable.io/reviews/reviewable/reviewable-client/514#-top), January 24, 2023: `Wow, this is quite a bit simpler! Seems to work great across browsers with a couple of minor exceptions.` accompanied detailed Safari/selection concerns. A later author question received LGTM. [Client #345](https://reviewable.io/reviews/reviewable/reviewable-client/345#-top), May 16, 2022, likewise gives a broader build/visual assessment alongside inline thoughts. | Jacob sometimes gives a concise overall assessment. The evidence supports judgment, not a prohibition. |
| Cross-repository scope context | [Firetruss-worker #1](https://reviewable.io/reviews/reviewable/firetruss-worker/1#-top), August 30, 2022: `This one looks good to me. I just left one question. Still working through the others.` accompanies an inline initialization question. | A short assessment can tell the author what remains in a wider review effort; it is not a model for routine recaps. |
| Further negative controls | [Server #929](https://reviewable.io/reviews/reviewable/reviewable-server/929#-top), April–May 2026, has Jacob's architecture questions inline and no Jacob top comment. [Docs #1313](https://reviewable.io/reviews/reviewable/reviewable/1313#-top), July 2026, has an inline wording suggestion and no top comment. Client #1015 has Jacob's UI feedback but only another reviewer's top approval. | Neither architectural detail, a small edit, nor another reviewer's summary makes a Jacob top comment necessary. |

Other observed forms are not interchangeable with summaries. Experiments #11's October 9, 2024 top reply accepts the author's proposed deployment approach while an inline naming question remains. Docs #1185 includes a warm reaction, a separate review-level product question, inline build/SSR feedback, and later LGTM. Riley0000/portfolio-website #12 has a native-GitHub social/context introduction before a single inline finding; it is not representative evidence for mandatory Reviewable summaries. Tribute #17 and client #1908 have recorded review activity without human prose, so an empty comment body must not be relabeled as a summary.

The redundant #2047 recap supplied by Jacob is the motivating process failure, not an additional historical review performed in this study. Its detailed inline follow-up already communicates the concern and reproduction. No #2047 discussion, draft, mark, or code was inspected or changed.

## Discovery and Coverage

Two global GitHub connector searches, with no repository restriction:

```text
is:pr reviewed-by:earlAchromatic -author:earlAchromatic
is:pr commenter:earlAchromatic -author:earlAchromatic
```

Used `sort=created`, `order=asc`, `topn=100`. Search each with `created:<2022-01-01`, the calendar year 2022, and years 2023–2026. Annual 2023–2026 results hit the cap, so replace them with nonoverlapping calendar quarters; the final interval is `2026-07-01..2026-09-03`. All 30 quarter queries returned below 100 (maximum 60). Together with the 12 initial date partitions, these are 42 logged queries. Pre-2022 returned zero; that does not prove there were no earlier reviews. Creation-date filtering is not publication-date filtering.

| PR creation period | Reviewed-by candidates | Commenter candidates |
| --- | ---: | ---: |
| Before 2022 | 0 | 0 |
| 2022 | 90 | 92 |
| 2023 | 117 | 122 |
| 2024 | 127 | 131 |
| 2025 | 183 | 184 |
| 2026 through September 3 | 118 | 119 |
| Total | 635 | 648 |

Deduplication by PR URL yielded 648 candidates across 20 repositories; all reviewed-by candidates were in the commenter set. These are candidates, not a count of human reviews. Extra bounded oldest/2024/latest-2025/latest-2026 searches provided initial sample seeds, not additional population counts.

The connector supplies no cursor, `total_count`, or `incomplete_results`. Below-cap partition results avoid known truncation but cannot establish index completeness. An independent `gh api --method GET search/issues -f q='<query>' -f sort=created -f order=asc -f per_page=100 --paginate --slurp` attempt hit GitHub's HTTP 403 secondary rate limit; retries stopped. No successful GitHub pagination-total check is claimed.

### Repository Inventory and Live Sampling

The production `sage-review` connection's live choose-review-provider and review-code protocols were read first. The research used identity lookup, discussion lists without filters, and resource reads only. For each successful sample, every listed discussion resource, including `-top`, was fetched. The API returned no continuation cursor. Main-top bodies were compared with contextual concern/reply histories and publication timestamps. Current participant dispositions were not treated as historical dispositions.

| Repository | Discovery candidates | PRs with live discussion resources fetched |
| --- | ---: | --- |
| Reviewable/reviewable-client | 497 | 345, 356, 514, 966, 968, 1015, 1726, 1737, 1743, 1816, 1893, 1894, 1908, 1940, 2024, 2042 |
| Reviewable/reviewable-server | 63 | 201, 520, 929 |
| Reviewable/Reviewable | 19 | 1185, 1253, 1313 |
| Reviewable/firetruss | 14 | 4, 41 |
| Reviewable/home | 13 | 3, 62 |
| Reviewable/firetruss-worker | 5 | 1 |
| Reviewable/reviewable-command | 2 | 27 |
| Reviewable/enterprise-tools | 1 | 7 |
| Reviewable/experiments | 1 | 11 |
| Reviewable/firecrypt | 1 | 24 |
| Reviewable/hubkit | 1 | 12 |
| Reviewable/reviewable-enterprise | 1 | 60 (comment identities only; no license/code inspection) |
| Reviewable/reviewable-settings | 1 | 1 |
| Reviewable/tribute | 1 | 17 |
| Reviewable/vue-element-spy | 1 | 7 |
| Riley0000/portfolio-website | 1 | 12 |
| Hyperion-Web/Nebula | 2 | Excluded test activity; GitHub #11 contains localhost exercises |
| oscl8tr-org/testing-reviewable | 22 | Test repository; not used for style conclusions |
| Reviewable/testing | 1 | Test repository; not used for style conclusions |
| oxalorg/sakura | 1 | GitHub #121 is casual acknowledgement; not a review round |

This produced 367 live resources across 37 PRs in 16 repositories. Exact-human bodies in that sample span May 16, 2022 through August 21, 2026. Two initial loading timeouts (docs #1185 and home #3) succeeded on one retry each. Companion GitHub inspection covered 26 selected timelines across 13 repositories; its normalization and absent page metadata prevent using it alone to prove a negative.

Selection deliberately included older/recent, small/large, client/non-client, approvals, questions, no-top cases, and agent controls. It combined chronological seeds, broad repository discovery, and recovered historical leads. It is a purposive sample, not random or exhaustive; no posting-frequency estimate follows from it.

### Existing Corpus Provenance

The June 17, 2026 task `Design code review style prompt` researched Reviewable/reviewable-client and produced the original reviewer skill. Its original `/tmp/reviewable-review-style` corpus no longer exists. The retained task transcript preserves query commands, selected outputs, eight complete PR submission records, and 48 distinct exact-human comments from individually fetched Reviewable resources.

That task used paginated repository-wide REST issue/inline comments and outer GraphQL `reviewed-by` search, but each PR's nested `reviews(first:100)` was not paginated. Its reported 591 PRs / 1,187 submissions included 132 Jacob-authored PRs and agent sync. Removing own PRs yielded 459 / 843, still not a clean human-top-comment population. Cleaning bundled review bodies also mixed locations. Those old aggregate counts were not used to infer summary frequency. The useful #1893, #1894, #1940, and #1816 leads were re-read live for this study.

Access is limited to the connected account, surviving published data, search indexing, and exposed APIs. Deleted or inaccessible material, other logins, and unrecorded communication are outside the evidence. Identity fields verify the recorded human account, not who physically typed every word. No exhaustive-history claim is warranted.

## Maintenance Decision

SAGE owns this gap: its handoff example repeated an inline finding as a top-level recap, while core comment selection had no default against that duplication. The focused fix is the core selection rule, neutral `comment` labels, a clear private-handoff distinction, and examples with an explicit empty top-level category. Publication safety, substantive review-level threads, final approval semantics, and the causal private narrative remain intact.

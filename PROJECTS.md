# Shiftbloom Studio – Projects (v2)

This document tracks one GitHub Projects (v2) board per public product repository.

Status: **blocked on auth**. No project URLs are listed because none were created. Do not treat any invented URL as valid.

## Exact auth error

Checked in this Cloud Agent run (`bc-fff60de3-2771-431c-8db3-da4853e03cc2`):

1. `GH_TOKEN` is **not present** in the process environment (`GH_TOKEN` unset, `GITHUB_TOKEN` unset).
2. `gh` is logged in as the GitHub App integration user `cursor` / GraphQL `viewer.login` = `cursor[bot]`.
3. `gh project list --owner shiftbloom-studio` succeeds and returns `{"projects":[],"totalCount":0}`.
4. `gh project create --owner shiftbloom-studio --title birthday-cake-loading` fails with:

```
GraphQL: cursor[bot] does not have permission to create projects on ownerId O_kgDODST3CQ. (createProjectV2)
```

That is the same org owner for every repo below. No boards were created. No issue items were added.

## Per-repository status

| Repo | Project URL | Open issues (counted) | Result |
| --- | --- | --- | --- |
| [birthday-cake-loading](https://github.com/shiftbloom-studio/birthday-cake-loading) | — | 9 | Auth/API error: `cursor[bot]` cannot create org projects (`createProjectV2`) |
| [voxcpm2-api](https://github.com/shiftbloom-studio/voxcpm2-api) | — | 7 | Same org-level `createProjectV2` permission error; not attempted after first failure |
| [open-hallucination-index](https://github.com/shiftbloom-studio/open-hallucination-index) | — | 8 | Same |
| [symphony-state](https://github.com/shiftbloom-studio/symphony-state) | — | 11 | Same |
| [circadian-ui](https://github.com/shiftbloom-studio/circadian-ui) | — | 8 | Same |
| [va-dispatcher](https://github.com/shiftbloom-studio/va-dispatcher) | — | 6 | Same |
| [myosotis](https://github.com/shiftbloom-studio/myosotis) | — | 6 | Same |
| [what-does-grok-know](https://github.com/shiftbloom-studio/what-does-grok-know) | — | 6 | Same |
| [axiom-llm-training-framework](https://github.com/shiftbloom-studio/axiom-llm-training-framework) | — | 7 | Same |
| [openai-privacy-filter-api](https://github.com/shiftbloom-studio/openai-privacy-filter-api) | — | 6 | Same |
| [omnisuite](https://github.com/shiftbloom-studio/omnisuite) | — | 5 | Same |
| [npm-package-template](https://github.com/shiftbloom-studio/npm-package-template) | — | 5 | Same |

## What still needs to happen (once a user PAT is in *this* VM)

For each repo:

1. Create or reuse an org Project v2 titled exactly after the repo.
2. Keep the built-in Status field with Todo / In Progress / Done.
3. Associate the repository with the project (`linkProjectV2ToRepository`).
4. Add every currently open issue and set Status to Todo.
5. Write the 12 real project URLs into this table.

Required token: a classic or fine-grained PAT for an org admin / `fabianzimber`, exported as `GH_TOKEN`, with scopes `project`, `read:project`, and `repo`.

Adding `GH_TOKEN` to Cloud Agent secrets **after this VM booted** does not inject it into this process. This run has no linked Cursor environment (`environment: null`). A new agent run that starts **with** `GH_TOKEN` already configured, or an in-run secret injection, is required. Do not commit the token.

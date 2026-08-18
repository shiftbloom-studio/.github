# Shiftbloom Studio – Projects (v2)

One organization-owned GitHub Project (v2) per public product repository. Built-in Status options are **Todo**, **In Progress**, and **Done**. Each board is linked to its repository. Currently open issues were added in **Todo**.

Created as `fabianzimber` via GraphQL `createProjectV2` on org owner `shiftbloom-studio`. Existing title matches were reused; no duplicate boards were created.

| Repository | Project | Open issues added (Todo) |
| --- | --- | --- |
| [birthday-cake-loading](https://github.com/shiftbloom-studio/birthday-cake-loading) | [birthday-cake-loading](https://github.com/orgs/shiftbloom-studio/projects/5) | 9 |
| [voxcpm2-api](https://github.com/shiftbloom-studio/voxcpm2-api) | [voxcpm2-api](https://github.com/orgs/shiftbloom-studio/projects/6) | 7 |
| [open-hallucination-index](https://github.com/shiftbloom-studio/open-hallucination-index) | [open-hallucination-index](https://github.com/orgs/shiftbloom-studio/projects/7) | 8 |
| [symphony-state](https://github.com/shiftbloom-studio/symphony-state) | [symphony-state](https://github.com/orgs/shiftbloom-studio/projects/8) | 11 |
| [circadian-ui](https://github.com/shiftbloom-studio/circadian-ui) | [circadian-ui](https://github.com/orgs/shiftbloom-studio/projects/9) | 10 |
| [va-dispatcher](https://github.com/shiftbloom-studio/va-dispatcher) | [va-dispatcher](https://github.com/orgs/shiftbloom-studio/projects/10) | 7 |
| [myosotis](https://github.com/shiftbloom-studio/myosotis) | [myosotis](https://github.com/orgs/shiftbloom-studio/projects/11) | 6 |
| [what-does-grok-know](https://github.com/shiftbloom-studio/what-does-grok-know) | [what-does-grok-know](https://github.com/orgs/shiftbloom-studio/projects/12) | 6 |
| [axiom-llm-training-framework](https://github.com/shiftbloom-studio/axiom-llm-training-framework) | [axiom-llm-training-framework](https://github.com/orgs/shiftbloom-studio/projects/13) | 7 |
| [openai-privacy-filter-api](https://github.com/shiftbloom-studio/openai-privacy-filter-api) | [openai-privacy-filter-api](https://github.com/orgs/shiftbloom-studio/projects/14) | 7 |
| [omnisuite](https://github.com/shiftbloom-studio/omnisuite) | [omnisuite](https://github.com/orgs/shiftbloom-studio/projects/15) | 5 |
| [npm-package-template](https://github.com/shiftbloom-studio/npm-package-template) | [npm-package-template](https://github.com/orgs/shiftbloom-studio/projects/16) | 5 |

## Project URLs

1. https://github.com/orgs/shiftbloom-studio/projects/5
2. https://github.com/orgs/shiftbloom-studio/projects/6
3. https://github.com/orgs/shiftbloom-studio/projects/7
4. https://github.com/orgs/shiftbloom-studio/projects/8
5. https://github.com/orgs/shiftbloom-studio/projects/9
6. https://github.com/orgs/shiftbloom-studio/projects/10
7. https://github.com/orgs/shiftbloom-studio/projects/11
8. https://github.com/orgs/shiftbloom-studio/projects/12
9. https://github.com/orgs/shiftbloom-studio/projects/13
10. https://github.com/orgs/shiftbloom-studio/projects/14
11. https://github.com/orgs/shiftbloom-studio/projects/15
12. https://github.com/orgs/shiftbloom-studio/projects/16

## Notes

- `birthday-cake-loading` already existed as org project **#5** from an earlier create in this run and was reused.
- Other listed titles did not exist and were created as **#6–#16**.
- Unrelated existing org boards (`Server Development`, `BCL Kanban Board`, untitled project) were left alone.
- `gh project create --owner shiftbloom-studio` failed with `unknown owner type` on this CLI; GraphQL `createProjectV2` / `addProjectV2ItemById` / `linkProjectV2ToRepository` succeeded.
- After `GH_TOKEN` was injected into this run, boards were rechecked as `fabianzimber`. One new open issue on `va-dispatcher` was added to project #10. No duplicate projects were created.
- No tokens or secrets are stored in this repository.

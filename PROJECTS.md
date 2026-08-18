# Shiftbloom Studio – Projects (v2)

This document tracks one GitHub Projects (v2) board per public product repository.

Status: Project creation is currently blocked in this environment because the GitHub CLI is not authenticated for the signed-in user, so organization Projects (v2) cannot be created or updated here. See “Next steps” below.

## Per-repository status

- birthday-cake-loading — Blocked (no org Project v2 created). Open issues: 9
- voxcpm2-api — Blocked (no org Project v2 created). Open issues: 7
- open-hallucination-index — Blocked (no org Project v2 created). Open issues: 8
- symphony-state — Blocked (no org Project v2 created). Open issues: 11
- circadian-ui — Blocked (no org Project v2 created). Open issues: 8
- va-dispatcher — Blocked (no org Project v2 created). Open issues: 6
- myosotis — Blocked (no org Project v2 created). Open issues: 6
- what-does-grok-know — Blocked (no org Project v2 created). Open issues: 6
- axiom-llm-training-framework — Blocked (no org Project v2 created). Open issues: 7
- openai-privacy-filter-api — Blocked (no org Project v2 created). Open issues: 6
- omnisuite — Blocked (no org Project v2 created). Open issues: 5
- npm-package-template — Blocked (no org Project v2 created). Open issues: 5

## What was intended

For each repository:
1) Create an organization-owned Project (v2) titled exactly after the repo (e.g., “birthday-cake-loading”).
2) Ensure the built-in Status field has: Todo, In Progress, Done.
3) Associate the repository to the project (org-level Projects v2 support host repos).
4) Add all currently open issues from that repository to the project in “Todo”.

## Why blocked here

- The GitHub CLI (`gh`) in this environment is not logged in:
  - `gh auth status` → “You are not logged into any GitHub hosts.”
- Creating and populating Projects (v2) requires authenticated access with appropriate scopes (at least `project` and `read:project`).
- This run avoids putting secrets into the repo and cannot complete a web-based auth flow.

## Next steps to unblock (no secrets committed)

Option A — Authenticate `gh` for this Cloud Agent:
- In Cursor Dashboard → Cloud Agents → Secrets, add `GH_TOKEN` or `GH_ENTERPRISE_TOKEN` with scopes: `project`, `read:project`, and basic repo scopes.
- Re-run the automation. It will:
  - Create (or reuse) each org Project (v2)
  - Associate the repository
  - Add all open issues into “Todo”
  - Record each project URL back into this file.

Option B — Run once from your local machine (signed-in user):
```bash
gh auth login
for repo in \
  birthday-cake-loading voxcpm2-api open-hallucination-index symphony-state circadian-ui \
  va-dispatcher myosotis what-does-grok-know axiom-llm-training-framework \
  openai-privacy-filter-api omnisuite npm-package-template
do
  # Create or reuse the org Project (v2)
  # Note: requires gh version that supports Projects v2 commands.
  if ! gh project list --owner shiftbloom-studio --format json | jq -e \'.[].title=="'"$repo"'"\' >/dev/null; then
    gh project create --owner shiftbloom-studio --title "$repo"
  fi
  # Get project number and ID
  proj_number=$(gh project list --owner shiftbloom-studio --format json | jq -r \'.[] | select(.title=="'"$repo"'") | .number\')
  proj_id=$(gh api graphql -f query=\'query($org:String!,$number:Int!){ organization(login:$org){ projectV2(number:$number){ id } } }\' -f org=shiftbloom-studio -F number="$proj_number" --jq \'.data.organization.projectV2.id\')
  # Add open issues from the repo
  for issue in $(gh issue list -R shiftbloom-studio/"$repo" --state open --json number -q \'.[].number\'); do
    gh project item-add --project-id "$proj_id" --url "https://github.com/shiftbloom-studio/$repo/issues/$issue"
  done
done
```

Once authenticated, the automation (or the one-off script) will update this document with the 12 project URLs.


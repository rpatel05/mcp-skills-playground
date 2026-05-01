---
name: taxonomy
description: Generates and enforces Mixpanel event and property naming conventions — reviews existing taxonomy, proposes standards, and validates new instrumentation against the rules
---

# taxonomy

Establish and enforce consistent naming conventions across your Mixpanel project.

## When to Use

- Setting up a new Mixpanel project and need naming standards
- Auditing an existing project for naming inconsistencies
- Validating a tracking plan before instrumentation
- Onboarding a new team that will send events

## Instructions

### Step 1 — Scan current taxonomy

Use `Get-Events` and `Get-Properties` to pull the full list of events and properties from the active project.

Classify each name into its detected convention:
- `Title Case` (e.g. "Sign Up", "Page Viewed")
- `snake_case` (e.g. "sign_up", "page_viewed")
- `camelCase` (e.g. "signUp", "pageViewed")
- `Sentence case` (e.g. "Sign up", "Page viewed")
- `Other` (inconsistent or unclassifiable)

### Step 2 — Detect the dominant convention

Count events per convention. The convention with the most events is the **dominant convention**. If no single convention covers >50% of events, flag the project as having no established standard and recommend adopting one.

### Step 3 — Report findings

Present a summary:

| Convention | Events | Properties | % of Total |
|---|---|---|---|
| Title Case | X | Y | Z% |
| snake_case | X | Y | Z% |
| ... | | | |

**Dominant convention**: [convention name]

**Outliers** (names that don't match the dominant convention):
- List each outlier with its current name and suggested rename

### Step 4 — Generate naming rules

Based on the dominant convention (or the user's chosen convention), produce a concise naming standard:

**Events**
- Format: [convention] (e.g. "Title Case with past tense verb — Page Viewed, Item Purchased")
- Prefixes: group by product area (e.g. "Checkout: Payment Added")
- Avoid: leading/trailing spaces, special characters, IDs in event names

**Properties**
- Format: [convention] (e.g. "snake_case — item_name, purchase_amount")
- Use consistent types: don't mix string "true"/"false" with boolean true/false
- Date properties: always ISO 8601

**Super Properties / User Properties**
- Prefix user-level properties consistently (e.g. "$" for Mixpanel defaults, no prefix for custom)

### Step 5 — Validate (optional)

If the user provides a tracking plan or list of new events, validate each name against the rules from Step 4 and flag violations.

## Usage

```
/taxonomy                          — audit current project
/taxonomy convention: snake_case   — audit and enforce snake_case
/taxonomy validate: [event list]   — check names against existing rules
```

Use `update-lexicon` to bulk-rename outliers after review.

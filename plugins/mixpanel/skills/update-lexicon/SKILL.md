---
name: update-lexicon
description: Bulk updates event and property descriptions, tags, and owners in Mixpanel Lexicon. Use after audit-lexicon to fix data governance issues.
---

# update-lexicon

Bulk update Lexicon metadata for data governance.

## What it does

1. Updates event descriptions
2. Updates property descriptions
3. Adds/removes tags
4. Assigns owners
5. Marks events as hidden/visible

## Input Format

Accepts YAML or JSON:

```yaml
lexicon_updates:
  events:
    - name: "Button Clicked"
      description: "User clicked a button in the UI"
      tags: ["engagement", "ui-interaction"]
      owner: "product@company.com"
  properties:
    - name: "button_name"
      description: "Name of the clicked button"
```

## Usage

Typical workflow:
1. Run `audit-lexicon` to identify issues
2. Review recommendations
3. Run `update-lexicon` with fixes
4. Verify changes in Lexicon UI

## Best Practices

- Review changes before applying
- Update in batches of 10-20
- Document reason for changes
- Notify team of updates

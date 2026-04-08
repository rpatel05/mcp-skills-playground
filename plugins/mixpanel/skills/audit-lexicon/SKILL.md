---
name: audit-lexicon
description: Reviews Mixpanel Lexicon for data quality issues - missing descriptions, inconsistent naming, hidden events, stale properties, and orphaned tags
---

# audit-lexicon

Comprehensive Lexicon audit for data quality and governance.

## What it checks

1. **Missing descriptions**: Events/properties without documentation
2. **Inconsistent naming**: CamelCase vs snake_case mixing
3. **Hidden events**: Events marked as hidden
4. **Stale properties**: Properties not seen in 90+ days
5. **Orphaned tags**: Tags not applied to any events
6. **Missing owners**: Events without assigned owners

## Output Format

**Lexicon Audit Results**

**🚨 Critical Issues**
- [Count] events missing descriptions
- [Count] properties with no recent data

**⚠️ Warnings**
- [Count] naming inconsistencies
- [Count] orphaned tags

**📊 Summary**
- Total events: X
- Total properties: Y
- Coverage: Z%

**🔧 Recommendations**
1. [Specific fix with count]
2. [Specific fix with count]

## Usage

Run monthly or before major releases.

Use `update-lexicon` skill to fix issues in bulk.

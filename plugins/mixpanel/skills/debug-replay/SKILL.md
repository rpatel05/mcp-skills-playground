---
name: debug-replay
description: Turns bug reports into numbered reproduction steps by extracting the interaction timeline from Mixpanel Session Replay
---

# debug-replay

Convert bug reports into clear reproduction steps using Session Replay.

## What it does

1. Finds relevant Session Replay for bug report
2. Extracts user interaction timeline
3. Converts to numbered reproduction steps
4. Identifies error events or anomalies

## Input

- Bug report text
- User ID or session ID (if available)
- Date range

## Output Format

**Bug Reproduction Steps**

**Session:** [Session ID]
**User:** [User ID]
**Date:** [Date/Time]

**Steps to Reproduce:**
1. [Action taken]
2. [Action taken]
3. [Action taken]
4. ❌ **Error occurred**: [Description]

**Context:**
- Platform: [iOS/Android/Web]
- Browser/OS: [Details]
- Properties: [Relevant properties]

**Session Replay Link:** [URL]

## Best Practices

- Include exact timing between steps
- Note any error messages or console logs
- Highlight unexpected behavior
- Link to full replay for eng team

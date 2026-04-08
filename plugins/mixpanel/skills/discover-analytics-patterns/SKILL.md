---
name: discover-analytics-patterns
description: Maps how analytics is currently implemented in your codebase - SDK usage, naming conventions, property patterns, import styles. Ensures new instrumentation matches existing patterns.
---

# discover-analytics-patterns

Discover and document existing Mixpanel analytics patterns in your codebase.

## What it does

1. Scans codebase for Mixpanel SDK usage
2. Identifies naming conventions
3. Documents property patterns
4. Maps import styles
5. Finds common tracking helpers

## Output Format

```yaml
analytics_patterns:
  sdk: mixpanel-browser
  import_style: "import mixpanel from 'mixpanel-browser'"
  tracking_calls:
    - pattern: "mixpanel.track('Event Name', { props })"
    - pattern: "trackEvent('Event Name', { props })"
  naming_convention:
    - style: Title Case
    - example: "Button Clicked"
  property_patterns:
    - snake_case for property names
    - always include: user_id, timestamp
  helpers:
    - file: src/utils/analytics.ts
    - function: trackEvent()
```

## Usage

Run before `instrument-events` to ensure new tracking matches existing patterns.

Helps maintain consistency across the codebase.

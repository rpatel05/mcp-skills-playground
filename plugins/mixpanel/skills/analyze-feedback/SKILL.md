# analyze-feedback

**Description**: Synthesize customer feedback from multiple sources and surface actionable themes correlated with product usage data.

**When to use this skill**: When users want to understand qualitative feedback patterns, connect support tickets to product behavior, or identify product gaps mentioned by customers.

---

## Instructions

### Overview

This skill helps you analyze customer feedback (support tickets, NPS comments, user interviews, feature requests) and correlate patterns with Mixpanel usage data to surface actionable insights.

### Step-by-step workflow

1. **Gather feedback sources**
   - Ask the user where feedback lives:
     - Support tickets (Zendesk, Intercom)
     - NPS/survey responses
     - User interviews or call notes
     - Feature request boards (ProductBoard, Canny)
   - If feedback is in external systems, ask user to provide data or connect via MCP

2. **Categorize and theme**
   - Read through feedback and identify recurring themes
   - Common categories:
     - **Bugs/Issues**: Technical problems users encountered
     - **Feature Requests**: Missing capabilities or improvements
     - **Confusion/UX**: Areas where users got stuck
     - **Performance**: Speed, reliability concerns
     - **Pricing/Value**: Cost objections or upgrade friction
   - Count frequency of each theme

3. **Correlate with usage data**
   - For each major theme, check Mixpanel to validate or quantify:
     - If users report "X is confusing" → check funnel drop-off at step X
     - If users request feature Y → check how often they hit the gap (error events, workaround patterns)
     - If users complain about speed → check event latency or load time properties
   - Use Mixpanel queries to measure:
     - How many users are affected?
     - Is it getting worse over time?
     - Which segments mention it most?

4. **Prioritize themes**
   - Rank themes by:
     - **Volume**: How many users mentioned it?
     - **Impact**: Does data show it's blocking conversions or causing churn?
     - **Trend**: Is it increasing?
   - High priority = High volume + High impact + Increasing

5. **Generate actionable output**
   - Create a structured summary:

   **Top Themes** (ranked by priority)
   | Theme | Mentions | User Impact | Data Signal | Priority |
   |-------|----------|-------------|-------------|----------|
   | [Theme 1] | [count] | [% affected] | [metric] | High |

   **Recommendations**
   - For each high-priority theme, suggest:
     - What to fix or build
     - Expected impact (use data to estimate)
     - How to measure success

   **Supporting Quotes** (2-3 per theme)
   - Include verbatim customer quotes to add context

### Example interaction

**User**: "Analyze our support tickets from last month and tell me what's blocking users"

**Assistant**:
1. Asks: "Where are the support tickets stored? Can you share a CSV or connect me to Zendesk via MCP?"
2. User provides data
3. Reads through 150 tickets, identifies 5 themes:
   - Login issues (40 mentions)
   - Missing CSV export (35 mentions)
   - Confusion about pricing (25 mentions)
   - Mobile app crashes (30 mentions)
   - Slow dashboard load (20 mentions)
4. Queries Mixpanel:
   - Login flow: 8% funnel drop-off at "verify email" step (increasing last 30 days)
   - Export action: only 2% of paid users have export feature enabled (low discoverability)
   - Pricing page: 60% bounce rate (no engagement with price calculator)
   - Mobile sessions: 3% have error events (up from 1% last month)
   - Dashboard load: p95 load time = 8 seconds (target is <3s)
5. Outputs ranked table with recommendations:
   - **High**: Fix mobile crashes (3% of users, growing fast)
   - **High**: Improve export discoverability (paid users want it but can't find it)
   - **Medium**: Optimize dashboard performance (affects power users)
   - **Medium**: Clarify pricing page (60% bounce suggests confusion)
   - **Low**: Login flow (8% drop-off is within normal range)

### Common feedback analysis patterns

**Pattern 1: Feature gap**
- Symptom: Many users request the same capability
- Data signal: High workaround usage (users doing X manually, or using external tool)
- Action: Validate demand with usage data, estimate TAM, prioritize in roadmap

**Pattern 2: Usability issue**
- Symptom: Users say "I couldn't figure out how to..."
- Data signal: Funnel drop-off, low feature adoption, high time-to-value
- Action: Run UX audit, add onboarding, improve discoverability

**Pattern 3: Technical issue**
- Symptom: Bug reports, error complaints
- Data signal: Error events spiking, sessions with crashes
- Action: Prioritize by user impact (% affected × severity)

**Pattern 4: Value perception gap**
- Symptom: "Too expensive", "Not worth it"
- Data signal: Low engagement with paid features, high free-tier retention
- Action: Improve onboarding to paid features, adjust pricing tiers

### Success criteria

- Feedback is categorized into 3-7 clear themes
- Each theme is correlated with Mixpanel usage data
- Output includes:
  - Ranked priority list
  - Quantified user impact
  - Specific recommendations
  - Supporting customer quotes
- User can take immediate action (file bugs, adjust roadmap, run experiments)

### Tips for effective analysis

- **Don't just count**: "50 users mentioned X" is less useful than "50 users mentioned X, and data shows 20% of trials abandon at that step"
- **Look for trends**: Is feedback increasing? That's more urgent than static complaints
- **Segment feedback**: Do churned users complain about different things than retained users?
- **Validate with data**: Feedback is subjective. Use Mixpanel to measure actual behavior
- **Close the loop**: After implementing fixes, re-analyze to confirm the theme decreased

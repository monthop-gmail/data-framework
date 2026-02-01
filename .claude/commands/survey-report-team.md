# Level 3: Role-Based Insight - Working Team Report

You are a **Survey Analyst** rendering analysis for the **Field Operations Team / Working Committee**.

## Prerequisites Check (MANDATORY - do not skip)
1. Read `reports/ai_data_audit.md` - confirm VERDICT is "READY"
2. Read `data_steward/dataset_profile.md` - understand data scope
3. Read `data_steward/metrics.yaml` - use ONLY approved metrics
4. If audit doesn't exist or verdict is NOT READY, stop and tell user to run `/survey-audit` first

## Task

### Step 1: Load Context
- Read the dataset profile
- Read approved metrics
- Read the audit report
- Read CSV data from `data/raw/`

### Step 2: Compute Approved Metrics
Calculate ONLY the metrics defined in `metrics.yaml`:
- Break down by relevant dimensions (role, question group, etc.)
- Show distributions, not just averages
- Highlight outliers and notable patterns

### Step 3: Analyze Open-Ended Responses
If text/comment columns exist:
- Extract main themes/topics (clustering)
- Count frequency of each theme
- Identify specific actionable feedback
- Do NOT expose individual responses verbatim

### Step 4: Generate Team Insights
Focus on:
- **What worked well** (with evidence)
- **Pain points** (with evidence from data)
- **Practical follow-up actions** (grounded in findings)
- Reference exact survey questions where relevant
- Flag low-confidence findings explicitly

### Step 5: Write Report
Write to `reports/final/team_insights.md`:

```markdown
# Team Insights Report: [Survey Name]
Date: [date]
Prepared for: คณะทำงาน

## Overview
(brief context)

## Metrics Breakdown
| Metric | Overall | Group 1 | Group 2 | ... |
|--------|---------|---------|---------|-----|

## What Worked Well
- ...

## Pain Points
- ...

## Open-Ended Feedback Themes
| Theme | Frequency | Example Direction |
|-------|-----------|-------------------|

## Recommended Follow-Up Actions
1. ...
2. ...

## Low-Confidence Findings
- ...

---
*This report uses only approved metrics. See ai_data_audit.md for full transparency.*
```

## Output
Display the report content in Thai, then confirm file was written.
Next step: "/survey-report-participant สำหรับรายงานผู้เข้าร่วม"

## Rules
- Use ONLY metrics from metrics.yaml
- Reference specific questions/columns when citing evidence
- Do NOT generalize beyond the data
- Do NOT include executive-level strategic framing
- Tone: practical, detail-oriented, actionable
- Language: Thai
- Same underlying data as other persona reports - different perspective only

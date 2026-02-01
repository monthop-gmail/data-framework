# AI Survey Steward Framework - Initialize Project

You are initializing the **AI Survey Steward Framework** for survey analysis with AI under human data stewardship.

## Task

1. Create the following directory structure in the current project:

```
data/
  raw/           # Original CSV exports (read-only)
  processed/     # Aggregated / cleaned outputs

data_steward/    # Human-owned truth
  dataset_profile.md
  metrics.yaml
  data_quality_checklist.md

prompts/         # AI instructions (reference only)

reports/
  draft/
  final/

governance/
  assumptions_log.md
  decision_log.md
```

2. Create `data_steward/dataset_profile.md` with this template:

```markdown
# Dataset Profile: [Survey Name]

## 1. Purpose
ข้อมูลชุดนี้ใช้เพื่อ:
- (ระบุวัตถุประสงค์)

## 2. Data Source
- Tool: Google Form
- Export: Google Sheet > CSV
- Collected after: (ระบุเหตุการณ์)

## 3. Respondent Roles
- (ระบุกลุ่มผู้ตอบ)

## 4. Columns Overview
| column | meaning | type | note |
|--------|---------|------|------|
| | | | |

## 5. Known Limitations
- (ระบุข้อจำกัด)

## 6. What This Dataset CAN Answer
- (ระบุคำถามที่ตอบได้)

## 7. What This Dataset CANNOT Answer
- (ระบุคำถามที่ตอบไม่ได้)
```

3. Create `data_steward/metrics.yaml` with this template:

```yaml
# Allowed Metrics - AI must only use metrics defined here
# AI is NOT allowed to invent new metrics

# Example:
# satisfaction_avg:
#   description: ค่าเฉลี่ยความพึงพอใจโดยรวม
#   calc: mean(satisfaction)
#   source_column: satisfaction
#
# low_satisfaction_ratio:
#   description: สัดส่วนผู้ให้คะแนนต่ำ (<=2)
#   calc: count(satisfaction<=2)/count(*)
#   source_column: satisfaction
```

4. Create `data_steward/data_quality_checklist.md`:

```markdown
# Data Quality Checklist

## Pre-Analysis Checks
- [ ] CSV imported correctly (encoding, delimiters)
- [ ] Row count matches expected responses
- [ ] No duplicate responses
- [ ] Column names match dataset_profile.md
- [ ] Missing values identified and documented

## Data Integrity
- [ ] Enum/choice values match form options
- [ ] Numeric scales within expected range
- [ ] Timestamps reasonable
- [ ] No logical inconsistencies between answers

## Bias & Sampling
- [ ] Sample size adequate per respondent group
- [ ] Response rate noted
- [ ] Non-response bias considered
```

5. Create `governance/assumptions_log.md`:

```markdown
# Assumptions Log

| Date | Phase | Assumption | Made By | Status |
|------|-------|-----------|---------|--------|
| | | | | |
```

6. Create `governance/decision_log.md`:

```markdown
# Decision Log

| Date | Decision | Rationale | Evidence | Decided By |
|------|----------|-----------|----------|------------|
| | | | | |
```

7. After creating all files, display a summary showing:
   - All created directories and files
   - The maturity level roadmap (Level 0-5)
   - Next step: "Place your CSV in data/raw/ then run /survey-inspect"

## Rules
- Do NOT analyze any data yet
- Do NOT generate insights
- This is purely structural setup
- Use Thai language for user-facing messages

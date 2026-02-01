# Level 4+: Survey Memory - Insight Registration

You are a **Survey Memory Curator** curating organizational learning from survey insights.

## Prerequisites Check
1. At least one report must exist in `reports/final/`
2. `governance/survey_registry.yaml` must exist
3. If cross-survey comparison exists (`reports/final/cross_survey_trends.md`), include those insights too

## Task

### Step 1: Gather All Insights
Read all reports in `reports/final/`:
- executive_summary.md
- team_insights.md
- participant_summary.md
- cross_survey_trends.md (if exists)

### Step 2: Score Each Insight
For each insight found, assess:
- **Confidence score** (0.0 - 1.0): based on evidence strength, sample size, consistency
- **Redundancy check**: is this insight already in memory?
- **Actionability**: can someone act on this?

### Step 3: Filter and Curate
- ACCEPT: confidence >= 0.6 AND not redundant AND actionable
- REJECT: confidence < 0.6 OR redundant OR too vague
- Document rejection reasons

### Step 4: Write Insight Memory
Create or update `governance/insight_memory.yaml`:

```yaml
insights:
  - insight_id: "IM-[YYYY]-[seq]"
    theme: "[semantic theme]"
    summary: "[concise insight in Thai]"
    confidence: [0.0-1.0]
    evidence_surveys:
      - "[survey_id]"
    first_observed: "[date]"
    last_confirmed: "[date]"
    trend: "improving / declining / stable / new"
    uncertainty: "[what could be wrong]"
    related_decisions: []

rejected_insights:
  - summary: "[what was rejected]"
    reason: "[why]"
    source_survey: "[survey_id]"
```

### Step 5: Summary
Display which insights were accepted/rejected and why.

## Output
Display in Thai:
- จำนวน insight ที่ผ่านการคัดเลือก
- จำนวน insight ที่ถูก reject (พร้อมเหตุผล)
- Themes ที่เป็น pattern ซ้ำข้าม survey
- Next step: "รัน /survey-governance เพื่อเชื่อมโยง insight กับการตัดสินใจ"

## Rules
- Memory is CURATED, not exhaustive
- Quality over quantity
- Document rejected insights with reasons (transparency)
- Do NOT store raw data - only distilled insights
- Insight without evidence = rejected
- Redundant insight = update existing, don't duplicate

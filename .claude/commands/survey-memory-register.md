# Level 4: Survey Memory - Register Survey

You are a **Survey Memory Curator**. Your job is to register this survey into the organizational memory system so it can be compared with past and future surveys.

## Prerequisites Check
1. `reports/ai_data_audit.md` must exist with VERDICT: READY
2. `data_steward/dataset_profile.md` must be filled in
3. At least one report in `reports/final/` should exist
4. If prerequisites missing, tell user which steps to complete first

## Task

### Step 1: Create Memory Registry
If `governance/survey_registry.yaml` doesn't exist, create it.

### Step 2: Register Current Survey
Add an entry to `governance/survey_registry.yaml`:

```yaml
surveys:
  - survey_id: "[auto-generate: YYYY_MM_survey_name]"
    name: "[from dataset_profile]"
    date: "[collection date]"
    source: "[Google Form / etc]"
    respondent_count: [number]
    respondent_groups:
      - "[group names]"
    schema_hash: "[hash of column names for change detection]"
    columns:
      - name: "[column]"
        semantic_key: "[normalized meaning]"
        type: "[data type]"
    metrics_used:
      - "[from metrics.yaml]"
    key_findings:
      - "[top 3 findings from reports]"
    audit_status: "[READY/NOT READY]"
```

### Step 3: Semantic Question Mapping
Create or update `governance/question_mapping.yaml`:

Map each question to a **semantic cluster** (meaning-based ID that persists across survey versions):

```yaml
semantic_clusters:
  exam_location_quality:
    description: "คุณภาพ/ความเหมาะสมของสนามสอบ"
    appearances:
      - survey: "2025_01_field_exam"
        question: "สนามสอบมีความเหมาะสมหรือไม่"
      - survey: "2026_01_field_exam"
        question: "สถานที่สอบเอื้อต่อการสอบเพียงใด"

  overall_satisfaction:
    description: "ความพึงพอใจโดยรวม"
    appearances:
      - survey: "2025_01_field_exam"
        question: "ความพึงพอใจต่อการสอบครั้งนี้"
```

### Step 4: Detect Schema Changes
If previous surveys exist in the registry, compare:
- New columns added
- Columns removed
- Wording changes (same semantic meaning)
- Incompatible changes (can't compare)

Write findings to console output.

## Output
Display in Thai:
- Survey registered successfully
- Semantic clusters created/updated
- Schema changes detected (if any)
- Next step: "ถ้ามี survey เก่าแล้ว รัน /survey-memory-compare เพื่อเปรียบเทียบ"

## Rules
- Do NOT analyze or generate insights
- Focus purely on registration and mapping
- Be explicit about what CAN and CANNOT be compared across versions
- Schema hash is for automated change detection

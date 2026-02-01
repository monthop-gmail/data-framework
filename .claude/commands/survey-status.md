# Survey Steward - Status Check

You are checking the current state of the **AI Survey Steward Framework** in this project.

## Task

Scan the project and report the maturity level based on what exists:

### Check Level 0 (Project Structure)
- [ ] `data/raw/` directory exists
- [ ] `data_steward/` directory exists
- [ ] `reports/` directory exists
- [ ] `governance/` directory exists

### Check Level 1 (Survey-Aware)
- [ ] CSV file(s) exist in `data/raw/`
- [ ] `data_steward/dataset_profile.md` is filled in (not just template)
- [ ] Column meanings documented
- [ ] Response count known

### Check Level 2 (Data Steward)
- [ ] `data_steward/metrics.yaml` has approved metrics (not just comments)
- [ ] `reports/ai_data_audit.md` exists
- [ ] Audit verdict is READY
- [ ] `data_steward/data_quality_checklist.md` has checks marked

### Check Level 3 (Role-Based Insights)
- [ ] `reports/final/executive_summary.md` exists
- [ ] `reports/final/team_insights.md` exists
- [ ] `reports/final/participant_summary.md` exists
- [ ] Reports reference approved metrics only

### Check Level 4 (Survey Memory)
- [ ] `governance/survey_registry.yaml` exists with entries
- [ ] `governance/question_mapping.yaml` exists with semantic clusters
- [ ] `governance/insight_memory.yaml` exists with curated insights
- [ ] `reports/final/cross_survey_trends.md` exists (if 2+ surveys)

### Check Level 5 (Governance)
- [ ] `governance/decision_log.md` has entries
- [ ] `reports/final/governance_review.md` exists
- [ ] Insights linked to decisions
- [ ] Outcome tracking present

## Output

Display a clear status report in Thai:

```
=== AI Survey Steward Framework - Status ===

Current Level: [0-5] - [Level Name]

Level 0 (Setup):        [PASS/FAIL] - [details]
Level 1 (Inspect):      [PASS/FAIL] - [details]
Level 2 (Audit):        [PASS/FAIL] - [details]
Level 3 (Reports):      [PASS/PARTIAL/FAIL] - [details]
Level 4 (Memory):       [PASS/PARTIAL/FAIL] - [details]
Level 5 (Governance):   [PASS/PARTIAL/FAIL] - [details]

Next Action: [specific command to run]
```

Then show the available commands:

```
Available Commands:
  /survey-init              - Level 0: สร้างโครงสร้าง framework
  /survey-inspect           - Level 1: AI อ่านและทำความเข้าใจข้อมูล
  /survey-audit             - Level 2: ตรวจคุณภาพและ bias
  /survey-report-executive  - Level 3: รายงานสำหรับผู้บริหาร
  /survey-report-team       - Level 3: รายงานสำหรับคณะทำงาน
  /survey-report-participant- Level 3: รายงานสำหรับผู้เข้าร่วม
  /survey-memory-register   - Level 4: ลงทะเบียน survey เข้า memory
  /survey-memory-compare    - Level 4: เปรียบเทียบข้าม survey
  /survey-memory-insights   - Level 4+: คัดเลือก insight เข้า memory
  /survey-governance        - Level 5: เชื่อมโยง insight กับการตัดสินใจ
  /survey-status            - ตรวจสถานะปัจจุบัน
```

## Rules
- Report facts only - what exists and what doesn't
- Do NOT create or modify any files
- Do NOT analyze data
- Be encouraging but honest about gaps

# Level 3: Role-Based Insight - Participant Report

You are an **Insight Facilitator** rendering a summary for **Survey Participants** (respondents / examinees).

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

### Step 2: Compute High-Level Metrics
Calculate overall metrics only (no detailed breakdowns that could identify groups):
- Overall satisfaction/feedback scores
- General theme summary from open-ended responses

### Step 3: Generate Participant-Friendly Summary
Focus on:
- **Overall feedback picture** - what did respondents say in aggregate?
- **What the organization heard** - acknowledgment of input
- **What will be improved** - forward-looking commitments (if available from governance/decision_log.md)
- **Limitations acknowledged** - honest about what the survey could/couldn't capture

### Step 4: Write Report
Write to `reports/final/participant_summary.md`:

```markdown
# Participant Feedback Summary: [Survey Name]
Date: [date]
Prepared for: ผู้เข้าร่วม / ผู้ตอบแบบสอบถาม

## ขอบคุณสำหรับความร่วมมือ
(acknowledgment message)

## ภาพรวมผลตอบรับ
- ...

## สิ่งที่องค์กรรับฟัง
- ...

## แนวทางปรับปรุงในอนาคต
- ...

## ข้อจำกัดของแบบสอบถาม
- ...

---
*รายงานนี้จัดทำจากข้อมูลรวมเท่านั้น ไม่มีการเปิดเผยข้อมูลรายบุคคล*
```

## Output
Display the report content in Thai, then confirm file was written.

## Rules
- Do NOT expose individual responses
- Do NOT blame any party
- Do NOT reveal internal organizational issues
- Do NOT include detailed metric breakdowns that could identify small groups
- Use respectful and transparent language
- Tone: warm, appreciative, forward-looking
- Language: Thai
- Same underlying data as other persona reports - different perspective only
- Safety filter: exclude sensitive findings automatically

# Level 1: Survey-Aware AI - Dataset Inspection

You are a **Survey Data Inspector**. Your job is to understand the data structure WITHOUT analyzing or drawing insights.

## Prerequisites
- CSV file(s) must exist in `data/raw/`
- If no CSV found, tell the user to place their CSV there first

## Task

### Step 1: Find and Read Data
1. List all CSV files in `data/raw/`
2. If the user specified a file via $ARGUMENTS, use that file. Otherwise use the most recent CSV.
3. Read the CSV file - examine headers and sample rows (first 20 rows)

### Step 2: Schema Inspection
For each column, determine:
- Column name (original)
- Inferred meaning (in Thai if the column is Thai)
- Data type: `enum`, `ordinal`, `numeric`, `text`, `timestamp`, `boolean`
- Scale (if applicable, e.g., 1-5 Likert)
- Missing rate (percentage of empty/null values)
- Sample values (3-5 examples)

### Step 3: Question Classification
Classify each survey question as:
- **closed-ended**: multiple choice, rating scale, yes/no
- **open-ended**: free text responses

### Step 4: Basic Statistics
- Total response count
- Response date range (if timestamp exists)
- Respondent group distribution (if role/group column exists)

### Step 5: Update dataset_profile.md
Update `data_steward/dataset_profile.md` with the inspection results:
- Fill in the Columns Overview table
- Update row count
- Note any obvious data issues in Known Limitations

### Step 6: Generate Suggested Metrics
Based on the data structure, **suggest** (not decide) potential metrics and append them as comments in `data_steward/metrics.yaml`. Mark them as `# SUGGESTED - needs human approval`.

## Output
Display a clear summary in Thai:
- จำนวน response ทั้งหมด
- จำนวน column และประเภท
- คำถามปลายปิด vs ปลายเปิด
- ข้อสังเกตเบื้องต้น (ไม่ใช่ insight)
- แนะนำขั้นตอนถัดไป: "ตรวจสอบ dataset_profile.md แล้วรัน /survey-audit"

## Rules
- Do NOT analyze sentiment or draw insights
- Do NOT summarize results or make recommendations
- Do NOT decide metrics - only suggest for human approval
- If any information is unclear, state it explicitly as "ไม่สามารถระบุได้"
- Output factual observations only
- This is Level 1: AI reads data, human decides meaning

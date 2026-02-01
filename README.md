# AI Survey Steward Framework

> **AI มีสิทธิ์คิด แต่ไม่มีสิทธิ์คิดนอกกรอบข้อมูล**

Framework สำหรับวิเคราะห์แบบสอบถาม (Survey) ด้วย AI อย่างมีธรรมาภิบาล ตรวจสอบได้ และไม่หลุดบริบทองค์กร

ออกแบบมาสำหรับ workflow:
- Google Form > Google Sheet > CSV
- แบบสอบถามหลังสอบภาคสนาม / หลังอบรม / หลังกิจกรรม
- ใช้กับ Claude Code, GPT, Local LLM ได้ทุกตัว

---

## หลักคิด 4 เสา

| เสา | ความหมาย |
|-----|----------|
| **Stewarded Data** | คนกำหนดว่าข้อมูลคืออะไร ก่อน AI แตะ |
| **Governed AI** | AI ใช้ได้เฉพาะ metric ที่อนุญาต + ต้อง audit ตัวเอง |
| **Persona-aware Output** | report เดียวกัน เล่าต่างมุมตามผู้อ่าน |
| **Auditability** | ทุกครั้งที่ AI ทำงาน ต้องมีหลักฐานว่าทำอะไร/ไม่ทำอะไร |

---

## Maturity Levels

| Level | ชื่อ | สถานะ AI |
|-------|------|----------|
| 0 | Raw Chaos | ตอบเก่ง แต่ย้อนที่มาไม่ได้ |
| 1 | Survey-Aware | อ่านข้อมูลเป็น |
| 2 | Data Steward | วิเคราะห์อย่างมีจริยธรรม |
| 3 | Role-Based Insight | คุยกับคนเป็น (แยก persona) |
| 4 | Survey Memory | จำอดีตได้ เปรียบเทียบข้ามรุ่น |
| 5 | Governance Loop | เชื่อมโยง insight กับการตัดสินใจ |

---

## Claude Code Skills (Slash Commands)

Framework นี้มาพร้อม **11 skills** สำหรับ Claude Code ใช้ผ่าน `/command`:

### Level 0: Setup
| Command | หน้าที่ |
|---------|--------|
| `/survey-init` | สร้างโครงสร้าง framework (directories + templates) |

### Level 1: Survey-Aware AI
| Command | หน้าที่ |
|---------|--------|
| `/survey-inspect` | AI อ่าน CSV, วิเคราะห์ schema, สร้าง dataset profile |

### Level 2: AI Data Steward
| Command | หน้าที่ |
|---------|--------|
| `/survey-audit` | ตรวจ data quality, bias, document assumptions |

### Level 3: Role-Based Insights
| Command | หน้าที่ |
|---------|--------|
| `/survey-report-executive` | รายงานผู้บริหาร (ความเสี่ยง / การตัดสินใจ) |
| `/survey-report-team` | รายงานคณะทำงาน (pain points / follow-up actions) |
| `/survey-report-participant` | รายงานผู้เข้าร่วม (โปร่งใส / ไม่เปิดเผยข้อมูลภายใน) |

### Level 4: Survey Memory
| Command | หน้าที่ |
|---------|--------|
| `/survey-memory-register` | ลงทะเบียน survey + semantic question mapping |
| `/survey-memory-compare` | เปรียบเทียบ trend ข้ามรุ่น survey |
| `/survey-memory-insights` | คัดเลือก insight เข้า long-term memory |

### Level 5: Governance & Decision Loop
| Command | หน้าที่ |
|---------|--------|
| `/survey-governance` | เชื่อมโยง insight กับการตัดสินใจ + ติดตามผล |

### Utility
| Command | หน้าที่ |
|---------|--------|
| `/survey-status` | ตรวจสถานะว่าอยู่ level ไหน + แนะนำขั้นตอนถัดไป |

---

## การติดตั้ง

### วิธีที่ 1: Clone ทั้ง repo (แนะนำ)

```bash
git clone https://github.com/monthop-gmail/data-framework.git
cd data-framework
```

เปิด Claude Code ในโฟลเดอร์นี้แล้วพิมพ์ `/survey-init` ได้เลย

### วิธีที่ 2: Copy เฉพาะ skills เข้าโปรเจกต์ที่มีอยู่

```bash
# ไปที่โปรเจกต์ของคุณ
cd your-project

# สร้าง directory สำหรับ commands
mkdir -p .claude/commands

# Copy skill files
curl -sL https://raw.githubusercontent.com/monthop-gmail/data-framework/main/.claude/commands/survey-init.md -o .claude/commands/survey-init.md
curl -sL https://raw.githubusercontent.com/monthop-gmail/data-framework/main/.claude/commands/survey-inspect.md -o .claude/commands/survey-inspect.md
curl -sL https://raw.githubusercontent.com/monthop-gmail/data-framework/main/.claude/commands/survey-audit.md -o .claude/commands/survey-audit.md
curl -sL https://raw.githubusercontent.com/monthop-gmail/data-framework/main/.claude/commands/survey-report-executive.md -o .claude/commands/survey-report-executive.md
curl -sL https://raw.githubusercontent.com/monthop-gmail/data-framework/main/.claude/commands/survey-report-team.md -o .claude/commands/survey-report-team.md
curl -sL https://raw.githubusercontent.com/monthop-gmail/data-framework/main/.claude/commands/survey-report-participant.md -o .claude/commands/survey-report-participant.md
curl -sL https://raw.githubusercontent.com/monthop-gmail/data-framework/main/.claude/commands/survey-memory-register.md -o .claude/commands/survey-memory-register.md
curl -sL https://raw.githubusercontent.com/monthop-gmail/data-framework/main/.claude/commands/survey-memory-compare.md -o .claude/commands/survey-memory-compare.md
curl -sL https://raw.githubusercontent.com/monthop-gmail/data-framework/main/.claude/commands/survey-memory-insights.md -o .claude/commands/survey-memory-insights.md
curl -sL https://raw.githubusercontent.com/monthop-gmail/data-framework/main/.claude/commands/survey-governance.md -o .claude/commands/survey-governance.md
curl -sL https://raw.githubusercontent.com/monthop-gmail/data-framework/main/.claude/commands/survey-status.md -o .claude/commands/survey-status.md
```

### วิธีที่ 3: Install script (one-liner)

```bash
mkdir -p .claude/commands && for f in survey-init survey-inspect survey-audit survey-report-executive survey-report-team survey-report-participant survey-memory-register survey-memory-compare survey-memory-insights survey-governance survey-status; do curl -sL "https://raw.githubusercontent.com/monthop-gmail/data-framework/main/.claude/commands/${f}.md" -o ".claude/commands/${f}.md"; done
```

---

## Quick Start

```
1. เปิด Claude Code ในโฟลเดอร์โปรเจกต์
2. /survey-status          # ดูสถานะปัจจุบัน
3. /survey-init            # สร้างโครงสร้าง
4. วาง CSV ใน data/raw/
5. /survey-inspect         # AI อ่านข้อมูล
6. ตรวจ dataset_profile.md แก้ไขให้ถูกต้อง
7. กำหนด metrics ใน metrics.yaml
8. /survey-audit           # ตรวจคุณภาพ
9. /survey-report-executive  # รายงานผู้บริหาร
10. /survey-report-team      # รายงานคณะทำงาน
11. /survey-report-participant # รายงานผู้เข้าร่วม
```

---

## Workflow Diagram

```
CSV (Google Form)
  |
  v
[/survey-init]          <- Level 0: สร้างโครงสร้าง
  |
  v
[/survey-inspect]       <- Level 1: AI อ่านข้อมูล
  |
  v
dataset_profile.md      <- คนตรวจ + แก้ไข
metrics.yaml            <- คนอนุมัติ metric
  |
  v
[/survey-audit]         <- Level 2: ตรวจ quality + bias
  |
  v
ai_data_audit.md        <- AI สารภาพสิ่งที่ทำ
  |
  v
[/survey-report-*]      <- Level 3: รายงาน 3 มุมมอง
  |
  v
[/survey-memory-*]      <- Level 4: จำข้ามรุ่น survey
  |
  v
[/survey-governance]    <- Level 5: เชื่อม insight กับ decision
```

---

## Key Artifacts

| File | สร้างโดย | หน้าที่ |
|------|----------|--------|
| `data_steward/dataset_profile.md` | คน + AI | อธิบายว่าข้อมูลคืออะไร |
| `data_steward/metrics.yaml` | คน | metric ที่อนุญาตให้ AI ใช้ |
| `reports/ai_data_audit.md` | AI | AI สารภาพว่าทำอะไร/ไม่ทำอะไร |
| `governance/survey_registry.yaml` | AI | ทะเบียน survey ทุกรุ่น |
| `governance/question_mapping.yaml` | AI | mapping คำถามข้ามรุ่น |
| `governance/insight_memory.yaml` | AI | ความจำระยะยาวขององค์กร |
| `governance/decision_log.md` | คน | บันทึกการตัดสินใจ |

---

## Philosophy

> "AI ที่ดี ไม่ใช่ AI ที่ฉลาดที่สุด แต่คือ AI ที่อธิบายตัวเองได้"

> "เราไม่ได้ให้ AI อ่านข้อมูล เราให้ AI ถามข้อมูลผ่านกติกา"

---

## Credits

- Framework design: ChatGPT + Human Data Steward collaboration
- Claude Code skills: Claude Code implementation
- Concept: AI Survey Steward Framework / AI Survey Brain (MCP-ready)

## License

ใช้ได้อิสระสำหรับ:
- งาน survey ภายในองค์กร
- งานวิจัย
- งานภาครัฐ

Attribution appreciated, but not required.

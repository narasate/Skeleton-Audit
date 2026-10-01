# 🦴 Skeleton Audit (กระดูกคุง — Kradook-kung)

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Supported-purple.svg)](#-claude-code-integration)
[![Antigravity IDE](https://img.shields.io/badge/Antigravity-Skill-orange.svg)](#-antigravity-ide-integration)
[![Rating](https://img.shields.io/badge/Rubric-10.0%20Deterministic-green.svg)](#-objective-scoring-rubric--critical-veto)

> *"A function that merely passes isn't enough; it must possess an unbreakable skeletal contract, guaranteed invariants, and zero orphaned data sinks."*  
> *"ฟังก์ชันที่ดี ไม่ใช่แค่รันผ่าน แต่ต้องมีโครงกระดูกที่แข็งแรง สัญญาการทำงานที่ชัดเจน และจุดหมายปลายทางของข้อมูลที่ไม่สูญหาย"*

**Skeleton Audit (กระดูกคุง)** คือ Universal Function Skeleton & Execution Contract Auditor — ทักษะการตรวจสอบเชิงโครงสร้างและสัจธรรมการทำงานของฟังก์ชัน (Functional Anatomy & Execution Contracts) รองรับโค้ดทุกภาษาโปรแกรม ประเมินผ่าน **6 เสาหลักของวงจรชีวิตฟังก์ชัน** พร้อมระบบคิดคะแนนเชิงคณิตศาสตร์เต็ม 10.0 คะแนน รายงานผลผ่าน **ตารางชันสูตรโครงกระดูก (Skeletal Audit Matrix)** และเสนอแนวทางแก้ไข 1–3 ทางเลือกโดย **ไม่เขียนโค้ดทับไฟล์เดิมของผู้ใช้เด็ดขาด (Zero Blind Overwrite)**

---

## 🦴 6 เสาหลักของโครงกระดูกฟังก์ชัน (The 6 Structural Pillars)

```
        ┌─────────────────────────────────────────────────────────┐
        │  1. Flow & How (วงจรการรัน: Sync / Async / Event / State)│
        └───────────────────────────┬─────────────────────────────┘
                                    │
    ┌───────────────────────────────┴───────────────────────────────┐
    │                                                               │
┌───▼───────────────────────────┐       ┌───────────────────────────▼───┐
│ 2. Input Contract (พารามิเตอร์)│       │ 4. Invariants (สัจธรรมการันตี) │
│ - Types, Defaults, Schema     │       │ - Business Rules, Post-cond   │
│ - Sanitization & Null-Safety  │       │ - Determinism & Bounds        │
└───┬───────────────────────────┘       └───────────────────────────┬───┘
    │                                                               │
    └───────────────────────────────┬───────────────────────────────┘
                                    │
        ┌───────────────────────────▼─────────────────────────────┐
        │ 3. Transformation & Logic (การแปรรูปตรรกะและกระบวนการ)   │
        │ - Immutability, Purity, Zero Hidden Side-effects        │
        └───────────────────────────┬─────────────────────────────┘
                                    │
    ┌───────────────────────────────┴───────────────────────────────┐
    │                                                               │
┌───▼───────────────────────────┐       ┌───────────────────────────▼───┐
│ 5. Output Contract (ส่งออก)   │       │ 6. Sink & Pipeline (ปลายทาง)  │
│ - Strict Return Types / Void  │       │ - DB, Cache, State, Caller    │
│ - Result Pattern (Ok / Err)   │       │ - No Orphaned Data, Clean I/O │
└───┬───────────────────────────┘       └───────────────────────────┬───┘
    │                                                               │
    └───────────────────────────────┬───────────────────────────────┘
                                    ▼
                 [ 🏆 Skeletal Integrity Certification ]
```

---

## 🎭 แม่แบบฟังก์ชัน 5 ประเภท (5 Function Archetypes)
ป้องกันปัญหาจับผิดมั่ว (False Positive) โค้ดในโลกความเป็นจริงไม่ได้มีแค่ Pure Function:
1. **Pure Computation:** ฟังก์ชันคำนวณบริสุทธิ์ ต้อง Immutability 100% และมี Strict Return Type เสมอ
2. **OOP Method / Stateful Service:** เมธอดในคลาส อนุญาตให้อ่าน/เขียน State ใน `this` หรือ `self` ได้ ไม่นับเป็น Side-effect ตราบใดที่ไม่แก้ Global State ภายนอก
3. **I/O Consumer / Sink:** ฟังก์ชันสั่งการปลายทาง รับรองสถานะ `void` / `Promise<void>` เป็น Valid Return โดยวัดคุณภาพที่การ Cleanup ทรัพยากร
4. **Stream / Generator / Iterator:** ฟังก์ชันพ่นข้อมูลต่อเนื่อง ตรวจ Yield Protocol, Backpressure และ Clean Completion
5. **In-place Operation:** ฟังก์ชันปรับแก้ Buffer/Array ต้นทางเพื่อประสิทธิภาพ อนุญาตเมื่อมีชื่อระบุเจตนาชัดเจน และต้องไม่เกิด Memory Leak

---

## ⚖️ เกณฑ์การคำนวณคะแนนและกฎยับยั้งวิกฤต (Scoring Rubric & Critical Veto)

$$\text{Total Score} = \sum_{i=1}^{6} (\text{Pillar Score}_i) + \text{Architecture Integrity (1.0)} = 10.0$$

- **เสาหลัก 1–6 (เสาละ 1.5 คะแนน):**
  - 🔴 ขาดสิ่งที่ต้องมี (Must-Have Failed): `0.0 คะแนน` ในเสานั้นทันที
  - 🟡 มีสิ่งที่ต้องมีครบถ้วน (Must-Have Passed): `1.0 คะแนน`
  - 🟢 มีสิ่งที่มีแล้วดีขึ้น (Enhancement Present): `+0.5 คะแนน` (เต็ม 1.5)
- **สถาปัตยกรรมและความเข้ากันได้ (Architecture Integrity):** `1.0 คะแนน`

### ⛔ กฎยับยั้งวิกฤต (The Critical Veto Rule):
หากตรวจพบช่องโหว่ความปลอดภัยระดับร้ายแรง (SQLi, RCE, Secrets รั่วไหล), การทำลายข้อมูล (Silent Data Corruption), หรือลูปไม่รู้จบ (Infinite Hang/OOM)  
👉 **ตัดคะแนนรวมทั้งฟังก์ชันเหลือ 0.0 / 10.0 ทันที (Veto to 0.0)** โดยไม่ต้องดูเสาอื่น และจัดระดับเป็น **"🔴 โครงสร้างพิการขั้นวิกฤต"**

---

## 📊 ตัวอย่างตารางชันสูตร (Skeletal Audit Matrix)

```markdown
# 🦴 รายงานชันสูตรกระดูกฟังก์ชัน: `calculateDiscount`

### 📋 ข้อมูลระบุตัวตน (Identity)
- **ไฟล์/โมดูล:** `src/pricing/discount.ts` | **Archetype:** Pure Computation | **Critical Veto:** ❌ ไม่ติด Veto

---

### 📊 ตารางชันสูตร 6 เสาหลักของโครงกระดูก (Skeletal Audit Matrix)

| เสาหลัก (Pillar) | คะแนน | Must-Have | Enhancement | ข้อเท็จจริงจากการผ่าตัดกระดูก (Anatomy & Findings) |
|---|:---:|:---:|:---:|---|
| **1. Execution Flow** | 1.5 / 1.5 | ✅ ผ่าน | ✅ มี | **รูปแบบ:** Sync 3 ขั้นตอน | **จุดตรวจ:** มี Early Return ตัดจบรวดเร็ว |
| **2. Input Contract** | 1.0 / 1.5 | ✅ ผ่าน | ❌ ขาด | **พารามิเตอร์:** `(price: number, tier: string)` | **จุดตรวจ:** ขาด Boundary Check ดักเลขติดลบ |
| **3. Transformation & Logic** | 1.5 / 1.5 | ✅ ผ่าน | ✅ มี | **ผลข้างเคียง:** ไม่มี (Pure) | **การรักษาข้อมูล:** ไม่ Mutate ข้อมูลต้นทาง |
| **4. Invariants & Guarantees** | 1.0 / 1.5 | ✅ ผ่าน | ❌ ขาด | **สัจธรรมที่การันตี:** ราคาห้ามติดลบ | **จุดตรวจ:** ยังไม่มี Runtime Assertion ดัก |
| **5. Output Contract** | 1.5 / 1.5 | ✅ ผ่าน | ✅ มี | **Signature:** `Result<number, PricingError>` | **การดักจับ:** ไม่กลืน Error |
| **6. Sink & Persistence** | 1.5 / 1.5 | ✅ ผ่าน | ✅ มี | **ปลายทาง:** Return ให้ Caller | **ทรัพยากร:** ไม่มี Dead Value |
| **🏛️ Architecture Integrity** | 1.0 / 1.0 | — | — | **ความเข้ากันได้:** โครงสร้างฟังก์ชันตรงตาม Pure Computation 100% |

---

### 🏆 ผลประเมินรวม: **9.0 / 10.0 คะแนน** — 🟢 โครงกระดูกระดับเพชร (Titanium Skeleton)
```

---

## 🔒 กฎ Zero Blind Overwrite (1–3 ทางเลือกแก้ปัญหา)
กระดูกคุงจะไม่เขียนโค้ดทับไฟล์ของผู้ใช้ทั้งดุ้น แต่จะให้คำแนะนำเชิงสถาปัตยกรรม 1–3 ทางเลือก พร้อมตัวอย่างโค้ดเฉพาะจุดสั้นๆ 3–8 บรรทัด:
1. **ทางเลือกที่ 1: [แนะนำ] แก้ไขตรงจุดและกระทบน้อยที่สุด (Primary / Minimal Invasive Fix)**
2. **ทางเลือกที่ 2: (ถ้ามี) ปรับปรุงเชิงสถาปัตยกรรม (Architectural Refactor)**
3. **ทางเลือกที่ 3: (ถ้ามี) การป้องกันเฉพาะหน้าแบบรวดเร็ว (Defensive Quick-Guard)**

---

## 🚀 วิธีติดตั้งและใช้งาน

### 💜 Claude Code Integration

#### 1. ติดตั้งแบบ Global (พิมพ์ได้ทุกโปรเจกต์):
```bash
# บน Linux / macOS
mkdir -p ~/.claude/commands
curl -o ~/.claude/commands/kradook.md https://raw.githubusercontent.com/narasate/Skeleton-Audit/main/commands/kradook.md

# บน Windows PowerShell
$dir = "$HOME\.claude\commands"
New-Item -ItemType Directory -Force -Path $dir
Invoke-WebRequest -Uri "https://raw.githubusercontent.com/narasate/Skeleton-Audit/main/commands/kradook.md" -OutFile "$dir\kradook.md"
```

#### 2. ติดตั้งเฉพาะโปรเจกต์:
ก๊อปปี้ไฟล์ `commands/kradook.md` ไปไว้ที่ `.claude/commands/kradook.md` ในโปรเจกต์ของคุณ

#### 3. เรียกใช้งานใน Claude Code:
```bash
/kradook calculateDiscount           # ตรวจเฉพาะฟังก์ชัน
/kradook src/utils/formatter.ts      # ตรวจทั้งไฟล์
/kradook                             # ให้ Claude สแกนหาฟังก์ชันหลัก
```

---

### 🍊 Antigravity IDE Integration

ก๊อปปี้โฟลเดอร์นี้ไปไว้ที่:
- **เฉพาะ Workspace:** `.agents/skills/kradook-kung/`
- **Global:** `~/.gemini/config/skills/kradook-kung/`

---

## 📄 License
MIT License © 2026 [Narasate](https://github.com/narasate)

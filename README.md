```markdown
<div dir="rtl">

# 🧠 AI Dev Prompt System

یک سیستم پرامپت ساختاریافته برای استفاده از هوش مصنوعی به عنوان معمار نرم‌افزار ارشد در پروژه‌های توسعه واقعی.

</div>

---

# 🧠 AI Dev Prompt System

A structured prompt system for using AI as a Senior Software Architect on real development projects.

---

<div dir="rtl">

## 📁 ساختار فایل‌ها

</div>

## 📁 File Structure

```
├── core-directives.md      # قوانین رفتاری AI / AI behavior rules
├── project-context.md      # بلوپرینت پروژه / Project blueprint template
├── task-injector.md        # تمپلیت تسک / Task template
├── question-injector.md    # تمپلیت سوال / Question template
└── README.md
```

---

<div dir="rtl">

## 🔧 فایل‌ها چه کاری می‌کنند

| فایل | هدف | تغییر می‌کند؟ |
|------|-----|---------------|
| `core-directives.md` | تعریف نقش، قوانین رفتاری، فرمت خروجی AI | به ندرت |
| `project-context.md` | اطلاعات کامل پروژه — stack، schema، استانداردها | هر session |
| `task-injector.md` | توضیح تسک برای AI | هر تسک |
| `question-injector.md` | پرسیدن سوال فنی از AI | هر سوال |

</div>

## 🔧 What Each File Does

| File | Purpose | Changes? |
|------|---------|----------|
| `core-directives.md` | Defines AI role, behavior rules, output format | Rarely |
| `project-context.md` | Full project info — stack, schema, standards | Each session |
| `task-injector.md` | Describes a task for the AI | Each task |
| `question-injector.md` | Ask the AI a technical question | Each question |

---

<div dir="rtl">

## 🚀 شروع سریع

### ۱. یک بار (راه‌اندازی اولیه)
`project-context.md` را کپی کرده و برای پروژه‌ات پر کن:

- **S1** — اطلاعات پروژه
- **S3** — tech stack دقیق با ورژن
- **S4** — معماری (فقط یک گزینه انتخاب کن، بقیه را حذف کن)
- **S6** — استانداردهای کدنویسی
- **S7** — schema دیتابیس واقعی
- **S8** — قرارداد API
- **S9** — احراز هویت
- **CURRENT STATE** — وضعیت فعلی پروژه

### ۲. برای هر تسک
1. یک مکالمه جدید در AI باز کن
2. هر سه فایل را attach کن: `core-directives.md` + `project-context.md` + `task-injector.md`
3. `task-injector.md` را پر کن و بفرست
4. State Update خروجی AI را در `project-context.md` کپی کن

### ۳. برای سوال فنی
1. یک مکالمه جدید باز کن
2. `core-directives.md` + `project-context.md` + `question-injector.md` را attach کن
3. `question-injector.md` را پر کن و بفرست

</div>

## 🚀 Quick Start

### 1. Once (Initial Setup)
Copy `project-context.md` and fill it for your project:

- **S1** — Project identity
- **S3** — Exact tech stack with versions
- **S4** — Architecture (choose ONE option, delete the rest)
- **S6** — Coding standards
- **S7** — Your actual database schema
- **S8** — API contract
- **S9** — Auth strategy
- **CURRENT STATE** — Current project status

### 2. For Each Task
1. Open a **new conversation** in your AI
2. Attach all three: `core-directives.md` + `project-context.md` + `task-injector.md`
3. Fill in `task-injector.md` and send
4. Copy the State Update from AI output into `project-context.md`

### 3. For a Technical Question
1. Open a **new conversation**
2. Attach: `core-directives.md` + `project-context.md` + `question-injector.md`
3. Fill in `question-injector.md` and send

---

<div dir="rtl">

## 📋 حالت‌های AI

| حالت | چه زمانی | خروجی |
|------|---------|-------|
| `Feature` | اضافه کردن قابلیت جدید | Plan + Code + Test + State Update |
| `Bug Fix` | رفع باگ | Plan + Code + Test + State Update |
| `Refactor` | بهبود کد بدون تغییر رفتار | Plan + Code + Test + State Update |
| `Performance` | بهینه‌سازی | Plan + Code + Test + State Update |
| `Security` | رفع مشکل امنیتی | Plan + Code + Test + State Update |
| `Question` | سوال فنی | پاسخ مستقیم، بدون کد |

</div>

## 📋 AI Modes

| Mode | When to use | Output |
|------|------------|--------|
| `Feature` | Adding new functionality | Plan + Code + Test + State Update |
| `Bug Fix` | Fixing a bug | Plan + Code + Test + State Update |
| `Refactor` | Improving code without changing behavior | Plan + Code + Test + State Update |
| `Performance` | Optimization | Plan + Code + Test + State Update |
| `Security` | Security fix | Plan + Code + Test + State Update |
| `Question` | Technical question | Direct answer, no code |

---

<div dir="rtl">

## ⚠️ قوانین مهم

- **هر تسک = یک مکالمه جدید** — AI حافظه ندارد
- **project-context.md را بعد از هر تسک آپدیت کن** — این تنها source of truth است
- **S4 را با slash options رها نکن** — یک گزینه انتخاب کن و بقیه را حذف کن
- **S7 را با schema واقعی پر کن** — جدول‌های نمونه را حذف کن
- **project-context.md را public نکن** اگر شامل اطلاعات حساس است

</div>

## ⚠️ Important Rules

- **One task = one new conversation** — AI has zero memory
- **Update project-context.md after each task** — it's the only source of truth
- **Don't leave S4 with slash options** — pick one value, delete the rest
- **Fill S7 with your real schema** — delete the placeholder tables
- **Don't make project-context.md public** if it contains sensitive architecture details

---

<div dir="rtl">

## 🔄 چرخه کار

</div>

## 🔄 Workflow Cycle

```
┌─────────────────────────────────────────────────┐
│  New Conversation                               │
│                                                 │
│  Attach:                                        │
│  ├── core-directives.md   (always)              │
│  ├── project-context.md   (always)              │
│  └── task-injector.md     (task)                │
│      OR question-injector.md  (question)        │
│                                                 │
│  Fill injector → Send → Get output              │
│                                                 │
│  Copy STATE UPDATE → project-context.md         │
└─────────────────────────────────────────────────┘
```

---

<div dir="rtl">

## 🗂️ چند پروژه موازی

برای هر پروژه یک فایل `project-context` جداگانه داشته باش:

```
core-directives.md          ← مشترک بین همه پروژه‌ها
task-injector.md            ← مشترک بین همه پروژه‌ها
question-injector.md        ← مشترک بین همه پروژه‌ها

projects/
├── project-alpha.md        ← blueprint پروژه alpha
├── project-beta.md         ← blueprint پروژه beta
└── project-gamma.md        ← blueprint پروژه gamma
```

</div>

## 🗂️ Multiple Projects

Keep a separate `project-context` file for each project:

```
core-directives.md          ← shared across all projects
task-injector.md            ← shared across all projects
question-injector.md        ← shared across all projects

projects/
├── project-alpha.md        ← blueprint for project alpha
├── project-beta.md         ← blueprint for project beta
└── project-gamma.md        ← blueprint for project gamma
```

---

<div dir="rtl">

## 🤖 سازگاری با AI

این سیستم با مدل‌های زیر تست شده:

- ✅ Claude 3.5 / 3.7 (Sonnet, Opus)
- ✅ GPT-4o / GPT-4.1
- ✅ Gemini 1.5 Pro / 2.0
- ⚠️ مدل‌های کوچک‌تر ممکن است Section 5 را به درستی اجرا نکنند

</div>

## 🤖 AI Compatibility

This system has been tested with:

- ✅ Claude 3.5 / 3.7 (Sonnet, Opus)
- ✅ GPT-4o / GPT-4.1
- ✅ Gemini 1.5 Pro / 2.0
- ⚠️ Smaller models may not correctly enforce Section 5 rules

---

<div dir="rtl">

## 📄 لایسنس

MIT — آزادانه استفاده، تغییر و توزیع کن.

</div>

## 📄 License

MIT — Free to use, modify, and distribute.
```
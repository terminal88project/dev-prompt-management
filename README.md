

***

```markdown
# 🤖 AI Blueprint System — راهنمای کامل

> سیستمی برای کار حرفه‌ای با هوش مصنوعی در پروژه‌های نرم‌افزاری

---

## 🧠 منطق کلی سیستم

این سیستم مثل یک **«بسته شغلی»** برای هوش مصنوعی عمل می‌کند.
هر بار که AI را صدا می‌زنی، سه فایل را باهم می‌فرستی تا AI بداند:

| فایل | هدف |
|---|---|
| `core-directives.md` | **کی است** — قوانین رفتاری ثابت |
| `project-context.md` | **پروژه چیست** — معماری و وضعیت فعلی |
| `task-injector.md` | **الان چه می‌خواهی** — تسک فعلی |

---

## 📄 فایل اول: `core-directives.md`

> ⛔ این فایل را **هرگز تغییر نده.** مغز قوانین AI است.

### مهم‌ترین بخش‌ها

**SECTION 1 — ROLE**
```text
"You are a Senior Software Architect..."
```
AI را مجبور می‌کند مثل یک معمار ارشد رفتار کند، نه یک چت‌بات معمولی.

---

**MEMORY CONSTRAINT**
```text
"You have ZERO memory of any previous conversation"
```
هشدار می‌دهد که AI حافظه‌ای از session قبل ندارد؛
پس باید **همیشه** فایل‌ها را دوباره attach کنی.

---

**SECTION 3 — MANDATORY PRE-TASK CHECKLIST (C1–C6)**

قبل از نوشتن هر کدی، AI باید ۶ مرحله بررسی کند.
مثال: `C2` یعنی ابتدا فایل‌های OFF-LIMITS را شناسایی کن.

---

**SECTION 6 — BEHAVIOR RULES**

```text
✅ اولین خط هر code block = مسیر کامل فایل به‌صورت comment
✅ کد ۱۰۰٪ کامل — عبارت "// rest of code here" ممنوع است
❌ استفاده از کتابخانه‌ای خارج از TECH STACK → اول بپرس
```
این قوانین جلوی کدهای ناقص یا حدسی را می‌گیرند.

---

**SECTION 8 — RESPONSE FORMAT**

AI همیشه با این ساختار ثابت جواب می‌دهد:

```
Step 0: ASSUMPTIONS
Step 1: TASK CONFIRMATION
Step 2: BLOCKERS       ← اگر چیزی مبهم بود اینجا متوقف می‌شود
Step 3: PLAN
Step 4: CODE
Step 5: HOW TO TEST
Step 6: STATE UPDATE   ← این را باید کپی کنی توی project-context
```

---

## 📄 فایل دوم: `project-context.md`

> این فایل را **یک بار برای هر پروژه پر کن** و بعد از هر تسک آپدیت کن.

### بخش S1 — IDENTITY (شناسنامه پروژه)

```markdown
# ❌ قالب خالی (اشتباه)
| Name | |
| Type | (Web App / Bot / Mobile...) |

# ✅ پر شده (درست) — مثال ربات تلگرام
| Name              | TechNewsBot                         |
| Codename / Slug   | tech-news-bot                       |
| Blueprint Version | 2026-02-25-v1                       |
| Type              | Bot                                 |
| One-line Goal     | ارسال خبر تکنولوژی به کانال تلگرام |
| Core Problem      | جمع‌آوری دستی خبر وقت‌گیر است     |
| Target Users      | دولوپرهای فارسی‌زبان               |
| Business Model    | Freemium                            |
| Stage             | MVP                                 |
| Priority          | High                                |
```

---

### بخش S3 — TECH STACK

```markdown
### Languages
- Primary: Python 3.12

### Backend
- Framework + version: python-telegram-bot 21.0
- Runtime: Python
- API Style: WebSocket (Telegram Webhook)

### Database
- Primary DB + version: PostgreSQL 16
- ORM / Query Builder: SQLAlchemy 2.0
- Migration Tool: Alembic
```

---

### بخش S4 — ARCHITECTURE

> ⚠️ مهم‌ترین بخش: فقط **یک گزینه** انتخاب کن، بقیه را **پاک کن**.

```markdown
# ❌ اشتباه (چند گزینه باقی مانده)
- Overall Pattern: (Monolith / Microservices / Serverless)

# ✅ درست (یک گزینه انتخاب شده)
- Overall Pattern: Monolith
- Design Pattern: Repository
- Service Communication: Direct calls
- Backend Architecture: Service Layer
- Dependency Injection: No
- Monorepo vs Polyrepo: Monorepo
```

---

### بخش S5 — FILE STRUCTURE

```
project-root/
├── bot/
│   ├── handlers/      → هندلرهای دستورات تلگرام
│   ├── services/      → منطق اصلی کسب‌وکار
│   └── models/        → مدل‌های SQLAlchemy
├── db/
│   └── migrations/    → فایل‌های Alembic
├── main.py            → نقطه ورود
└── .env               → متغیرهای محیطی
```

---

### بخش S7 — DATABASE SCHEMA

```markdown
TABLE: users
  id          BIGSERIAL     PRIMARY KEY
  telegram_id BIGINT        NOT NULL UNIQUE
  username    VARCHAR(64)
  is_premium  BOOLEAN       DEFAULT FALSE
  created_at  TIMESTAMPTZ   NOT NULL DEFAULT NOW()

TABLE: news_items
  id          BIGSERIAL     PRIMARY KEY
  title       TEXT          NOT NULL
  url         TEXT          NOT NULL UNIQUE
  sent_at     TIMESTAMPTZ   NULL
  created_at  TIMESTAMPTZ   NOT NULL DEFAULT NOW()
```

---

### بخش CURRENT STATE — وضعیت فعلی

> این بخش بعد از هر تسک آپدیت می‌شود.

```markdown
Last Task ID: TASK-000
Last Updated: 2026-02-25
Project Status: FRESH START — no features implemented yet.

✅ COMPLETED
- Nothing completed yet.

🔄 IN PROGRESS
- Nothing in progress.

⏳ BACKLOG
- TASK-001: /start command with welcome message
- TASK-002: News fetcher from RSS

🐛 KNOWN BUGS
- No known bugs yet.

🔒 OFF-LIMITS
- .env file — never modify
```

---

## 📄 فایل سوم: `task-injector.md`

> هر بار که می‌خواهی یک ویژگی بسازی، این فایل را با آن تسک پر کن.

```markdown
## 🎯 TASK HEADER

| Field    | Value                                   |
|----------|-----------------------------------------|
| Task ID  | TASK-001                                |
| Name     | Add /start command with welcome message |
| Mode     | Feature                                 |
| Priority | High                                    |

## 🔗 CONTEXT
- Depends on Task: None
- Continues from: None
- Related Files: main.py
- Last Session Note: Fresh start — no prior session

## 📋 DESCRIPTION
وقتی کاربر /start را می‌زند:
1. اطلاعاتش در جدول users ذخیره شود (یا اگر وجود داشت آپدیت شود)
2. پیام خوش‌آمد فارسی با دکمه‌های inline نمایش داده شود

## ✅ EXPECTED OUTPUT
- /start → ذخیره user در DB + پیام خوش‌آمد
- اگر user قبلاً ثبت شده، پیام نمایش داده شود ولی دوباره insert نشود

## 🏁 ACCEPTANCE CRITERIA
- [ ] User جدید در جدول users ذخیره می‌شود
- [ ] /start برای user موجود خطا نمی‌دهد (upsert)
- [ ] پیام شامل دکمه‌های inline است

## 📁 FILES

### Files to Create
- bot/handlers/start.py         → هندلر دستور /start
- bot/services/user_service.py  → منطق ذخیره user

### DO NOT TOUCH
- .env — اطلاعات حساس

## ⚠️ EDGE CASES TO HANDLE
- اگر telegram_id تکراری بود (upsert نه insert)
- اگر username کاربر None بود
- اگر اتصال DB قطع بود

## 🚫 AVOID
- Raw SQL نزن، فقط SQLAlchemy ORM
- فایل main.py را تغییر نده
```

---

## 📄 فایل چهارم: `question-injector.md`

> برای سوال یا دیباگ استفاده می‌شود، **نه کدنویسی**.

```markdown
## ❓ QUESTION

| Field    | Value                                    |
|----------|------------------------------------------|
| Priority | Blocking — can't proceed without answer |
| Type     | Technical                                |

Question:
آیا بهتر است برای Telegram Webhook از FastAPI استفاده کنم
یا همان python-telegram-bot Application را مستقیم اجرا کنم؟
تفاوت performance در ۱۰۰۰ user همزمان چیست؟

## 🔗 CONTEXT FOR THIS QUESTION
- Related Blueprint Sections: TECH STACK, ARCHITECTURE
- Related Files: main.py
- Background:
  ربات الان با polling کار می‌کند. می‌خواهم به webhook تبدیل کنم.
  سرور Ubuntu 22.04 با 2GB RAM است.
```

---

## 🔄 چرخه کامل کار

### راه‌اندازی اولیه (یک بار)

1. ریپو را clone کن
2. فایل `project-context.md` را برای پروژه‌ات پر کن
3. بخش S4 را پاک کن و فقط **یک گزینه** برای هر فیلد نگه دار
4. بخش S7 را با schema واقعی پروژه‌ات جایگزین کن

---

### هر تسک جدید

```
مرحله ۱ → task-injector.md را با تسک جدید پر کن
مرحله ۲ → یک چت جدید در AI باز کن
مرحله ۳ → این ۳ فایل را attach کن:
            core-directives.md + project-context.md + task-injector.md
مرحله ۴ → AI جواب می‌دهد با: PLAN + CODE + TEST + STATE UPDATE
مرحله ۵ → بخش STATE UPDATE خروجی AI را کپی کن
            و در بخش CURRENT STATE فایل project-context.md جایگزین کن
```

---

### هر سوال یا دیباگ

```
مرحله ۱ → question-injector.md را پر کن
مرحله ۲ → یک چت جدید باز کن
مرحله ۳ → این ۳ فایل را attach کن:
            core-directives.md + project-context.md + question-injector.md
```

---

## ⚠️ مهم‌ترین قوانین

| قانون | توضیح |
|---|---|
| هر تسک = چت جدید | AI حافظه ندارد؛ هر بار فایل‌ها را attach کن |
| بعد از هر تسک `project-context` را آپدیت کن | بخش STATE UPDATE خروجی AI را کپی کن |
| S4 را با slash options رها نکن | AI گزینه‌های پاک‌نشده را به عنوان «خالی» تلقی می‌کند |
| S7 را با schema واقعی پر کن | جدول‌های نمونه را حذف کن |
| `project-context.md` را public نکن | شامل معماری حساس پروژه است |
```
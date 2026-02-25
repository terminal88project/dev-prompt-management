---
## S1 — IDENTITY

| Field               | Value                                                        |
|---------------------|--------------------------------------------------------------|
| Name                | PremiumNewsBot                                               |
| Codename / Slug     | premium-news-bot                                             |
| Blueprint Version   | 2026-02-25-v1                                                |
| Blueprint Changelog | 2026-02-25: initial setup                                    |
| Type                | Bot                                                          |
| One-line Goal       | ربات تلگرام برای ارسال اخبار تکنولوژی با سیستم اشتراک پولی |
| Core Problem        | خواندن اخبار تکنولوژی پراکنده و وقت‌گیر است                |
| Target Users        | دولوپرها و علاقه‌مندان تکنولوژی فارسی‌زبان                 |
| Business Model      | Freemium                                                     |
| Stage               | MVP                                                          |
| Priority            | High                                                         |
| v1.0 Deadline       | 2026-04-01                                                   |
| Next Milestone      | ارسال خبر روزانه برای کاربران رایگان                       |

**Full Description:**
PremiumNewsBot یک ربات تلگرام است که اخبار روزانه تکنولوژی را از منابع RSS جمع‌آوری کرده و برای کاربران ارسال می‌کند.
کاربران رایگان روزانه ۳ خبر دریافت می‌کنند؛ کاربران پریمیوم خبرهای نامحدود، فیلتر موضوعی و خلاصه هوش مصنوعی دریافت می‌کنند.
پرداخت از طریق Telegram Stars انجام می‌شود و سابسکریپشن ماهانه ۱۵۰ Stars است.


---
## S2 — DOMAIN GLOSSARY

| Term          | Exact meaning in THIS project                                        |
|---------------|----------------------------------------------------------------------|
| "subscriber"  | کاربری که اشتراک فعال پریمیوم دارد (expired نشده)                  |
| "free user"   | کاربر بدون اشتراک — روزانه ۳ خبر دریافت می‌کند                    |
| "news item"   | یک خبر با title, url, summary, topic — از RSS گرفته می‌شود         |
| "daily digest"| مجموعه خبرهایی که هر روز ساعت ۸ صبح به کاربران ارسال می‌شود       |
| "topic"       | دسته‌بندی خبر: AI / Web / Mobile / Security / General               |


---
## S3 — TECH STACK

### Languages
- **Primary:** Python 3.12
- **Secondary:** SQL (PostgreSQL dialect)
- **Scripting / Tooling:** Bash, Makefile

### Frontend
- N/A — Bot only (Telegram UI)

### Backend
- **Framework + version:** python-telegram-bot 21.6
- **Runtime:** Python 3.12
- **API Style:** WebSocket (Telegram long-polling for dev, Webhook for prod)
- **API Versioning:** N/A
- **Realtime:** Telegram Bot API
- **Background Jobs / Queues:** APScheduler 3.10
- **Caching Layer:** Redis 7.2 (برای rate limiting و session)
- **Search Engine:** N/A

### Database
- **Primary DB + version:** PostgreSQL 16
- **Secondary DB:** Redis 7.2
- **ORM / Query Builder:** SQLAlchemy 2.0 (async)
- **Migration Tool:** Alembic 1.13
- **Schema Approach:** Migration files

### External Services
- **Auth Provider:** Telegram (user_id as identity)
- **File Storage:** N/A
- **Email Service:** N/A
- **SMS / OTP:** N/A
- **Payment Gateway:** Telegram Stars (built-in)
- **Push Notifications:** Telegram Bot API
- **Maps / Geo:** N/A
- **Other 3rd Party APIs:** feedparser 6.0 (RSS parsing)

### AI / ML
- **AI APIs:** OpenAI GPT-4o-mini (برای خلاصه‌سازی اخبار پریمیوم)
- **ML Framework:** N/A
- **Vector DB:** N/A
- **Embeddings Model:** N/A


---
## S4 — ARCHITECTURE

- **Overall Pattern:**       Modular Monolith
- **Design Pattern:**        Repository
- **Service Communication:** Direct calls
- **Frontend Architecture:** N/A
- **Component Strategy:**    Feature-Sliced
- **Backend Architecture:**  Service Layer
- **Dependency Injection:**  No
- **Monorepo vs Polyrepo:**  Monorepo


---
## S5 — FILE & FOLDER STRUCTURE

```
premium-news-bot/
├── main.py                    → نقطه ورود — bot را راه‌اندازی می‌کند
├── config.py                  → خواندن ENV variables
├── requirements.txt
├── Makefile                   → دستورات dev/prod
├── .env                       → متغیرهای محیطی (در git نیست)
├── .env.example               → نمونه متغیرها (در git هست)
│
├── bot/
│   ├── __init__.py
│   ├── handlers/
│   │   ├── __init__.py
│   │   ├── start.py           → هندلر /start و /help
│   │   ├── subscription.py    → هندلر /subscribe, /status, /cancel
│   │   └── payment.py         → هندلر pre_checkout و successful_payment
│   │
│   ├── services/
│   │   ├── __init__.py
│   │   ├── user_service.py    → منطق کسب‌وکار مربوط به User
│   │   ├── news_service.py    → fetch و ذخیره اخبار از RSS
│   │   ├── digest_service.py  → ارسال daily digest به کاربران
│   │   └── ai_service.py      → خلاصه‌سازی با GPT-4o-mini
│   │
│   └── keyboards/
│       ├── __init__.py
│       └── main_keyboard.py   → InlineKeyboardMarkup های تکرارشونده
│
├── db/
│   ├── __init__.py
│   ├── session.py             → async engine و session factory
│   ├── models.py              → SQLAlchemy models
│   └── migrations/
│       ├── env.py
│       └── versions/          → فایل‌های Alembic
│
└── scheduler/
    ├── __init__.py
    └── jobs.py                → APScheduler jobs (daily digest, RSS fetch)
```


---
## S6 — CODING STANDARDS

### General Rules

| Rule                  | Value                    |
|-----------------------|--------------------------|
| Paradigm              | Mixed (OOP + Functional) |
| Strict Typing         | Yes — enforced           |
| Immutability          | Preferred                |
| Max Function Length   | 40 lines                 |
| Max File Length       | 200 lines                |
| Single Responsibility | Strict                   |
| DRY Policy            | Strict                   |

### Naming Conventions

| Element           | Convention    | Example                      |
|-------------------|---------------|------------------------------|
| Variables         | snake_case    | `user_id`                    |
| Constants         | UPPER_SNAKE   | `MAX_FREE_DAILY_NEWS`        |
| Functions         | snake_case    | `get_user_by_telegram_id`    |
| Classes           | PascalCase    | `UserService`                |
| Interfaces/Types  | PascalCase    | `UserCreate`                 |
| Files             | snake_case    | `user_service.py`            |
| Folders           | snake_case    | `handlers/`                  |
| DB Tables         | snake_case    | `news_items`                 |
| DB Columns        | snake_case    | `created_at`                 |
| API Endpoints     | N/A (bot)     | N/A                          |
| Enums             | PascalCase    | `TopicType.AI`               |
| Env Variables     | UPPER_SNAKE   | `DATABASE_URL`               |

### Import Order
1. Standard library (os, asyncio, datetime)
2. External packages (sqlalchemy, telegram, openai)
3. Internal absolute imports (db.models, bot.services)
4. Relative imports (./)

- **Path Aliases:** None
- **Barrel Exports:** No

### Async & Error Handling

| Rule               | Value                                     |
|--------------------|-------------------------------------------|
| Async Approach     | async/await throughout                    |
| Error Strategy     | try-except با custom exception classes    |
| Error Logging      | Python logging — levels: error/warn/info  |
| Silent Errors      | NEVER — always log or reraise             |

**Custom Error Classes:**

```
AppError(message, code)
├── UserNotFoundError(telegram_id)
├── SubscriptionExpiredError(user_id)
├── NewsLimitReachedError(user_id, limit)
└── PaymentVerificationError(payment_id)
```

### Comments & Documentation
- **Comment Style:** Python Docstring برای کلاس و متد عمومی
- **When to Comment:** Complex logic only
- **TODO Format:** `# TODO(dev): description — TASK-XXX`
- **README:** Top-level only

### Security Rules

| Rule                | Approach                                           |
|---------------------|----------------------------------------------------|
| Input Validation    | Pydantic v2                                        |
| SQL Injection       | ORM only — raw SQL ممنوع                          |
| Auth Checks         | middleware (telegram user_id verification)         |
| Sensitive Data      | Never log. Encrypt tokens at rest.                 |
| CORS Policy         | N/A (bot)                                          |
| Rate Limiting       | Redis — 20 req/min per user                        |
| Secrets             | Always from ENV — never hardcoded                  |
| Raw SQL Permitted   | No                                                 |


---
## S7 — DATABASE SCHEMA

- **DB Dialect:** PostgreSQL 16

### Tables

```
TABLE: users
  id              BIGSERIAL       PRIMARY KEY
  telegram_id     BIGINT          NOT NULL UNIQUE
  username        VARCHAR(64)     NULL
  first_name      VARCHAR(128)    NOT NULL
  is_premium      BOOLEAN         NOT NULL DEFAULT FALSE
  premium_until   TIMESTAMPTZ     NULL
  created_at      TIMESTAMPTZ     NOT NULL DEFAULT NOW()
  updated_at      TIMESTAMPTZ     NOT NULL DEFAULT NOW()

TABLE: subscriptions
  id              BIGSERIAL       PRIMARY KEY
  user_id         BIGINT          NOT NULL REFERENCES users(id)
  telegram_payment_id VARCHAR(256) NOT NULL UNIQUE
  stars_amount    INT             NOT NULL
  started_at      TIMESTAMPTZ     NOT NULL DEFAULT NOW()
  expires_at      TIMESTAMPTZ     NOT NULL
  created_at      TIMESTAMPTZ     NOT NULL DEFAULT NOW()

TABLE: news_items
  id              BIGSERIAL       PRIMARY KEY
  title           TEXT            NOT NULL
  url             TEXT            NOT NULL UNIQUE
  summary         TEXT            NULL
  ai_summary      TEXT            NULL
  topic           VARCHAR(32)     NOT NULL DEFAULT 'General'
  source          VARCHAR(128)    NOT NULL
  published_at    TIMESTAMPTZ     NULL
  created_at      TIMESTAMPTZ     NOT NULL DEFAULT NOW()

TABLE: sent_news
  id              BIGSERIAL       PRIMARY KEY
  user_id         BIGINT          NOT NULL REFERENCES users(id)
  news_id         BIGINT          NOT NULL REFERENCES news_items(id)
  sent_at         TIMESTAMPTZ     NOT NULL DEFAULT NOW()
  UNIQUE(user_id, news_id)
```

### Relationships
- `subscriptions.user_id` → `users.id` (many-to-one)
- `sent_news.user_id` → `users.id` (many-to-one)
- `sent_news.news_id` → `news_items.id` (many-to-one)

### Indexes
- `users(telegram_id)` — UNIQUE, used in every request
- `news_items(url)` — UNIQUE, prevents duplicate RSS items
- `news_items(topic, created_at DESC)` — برای فیلتر موضوعی
- `sent_news(user_id, sent_at DESC)` — برای daily digest query
- `subscriptions(user_id, expires_at)` — بررسی اشتراک فعال

### Schema Policies

| Policy        | Value                                          |
|---------------|------------------------------------------------|
| Soft Delete   | No                                             |
| Audit Log     | No                                             |
| Timestamps    | `created_at` + `updated_at` on every table     |
| Multi-tenancy | No                                             |
| Primary Keys  | BIGSERIAL                                      |


---
## S8 — API CONTRACT

- **Base URL:** N/A (Telegram Bot API)
- **Auth Header:** N/A
- **Content-Type:** N/A
- **Pagination Style:** cursor
- **Max Page Size:** 10
- **Webhooks:** No
- **API Docs Tool:** None

**Telegram Response Format (success):**
```python
await update.message.reply_text(text, reply_markup=keyboard, parse_mode="HTML")
```

**Telegram Response Format (error):**
```python
await update.message.reply_text("❌ خطایی رخ داد. لطفاً دوباره امتحان کنید.")
logger.error(f"[HANDLER_NAME] error: {e}", exc_info=True)
```

---
## S9 — AUTH & AUTHORIZATION

- **Auth Flow:** Telegram user_id (بدون login جداگانه)
- **Token Strategy:** N/A
- **Access Token Expiry:** N/A
- **Refresh Token Expiry:** N/A
- **Refresh Token Storage:** N/A
- **Token Rotation on Refresh:** N/A

| Role      | Can do                                                       |
|-----------|--------------------------------------------------------------|
| free      | روزانه ۳ خبر، /start، /help، /subscribe                    |
| premium   | خبر نامحدود، فیلتر موضوعی، خلاصه AI، /status، /cancel     |

- **Permission Check:** decorator در handlers
- **2FA:** No
- **Account Lockout:** No — rate limit Redis (20 req/min)


---
## S10 — DEVOPS & DEPLOYMENT

- **Environments:** dev / production
- **Containerization:** Docker + Docker Compose
- **Hosting:** VPS (Ubuntu 22.04, 2GB RAM)
- **Reverse Proxy:** None (bot — no HTTP server)
- **CI/CD:** None (manual deploy)
- **Package Manager:** pip
- **Git Workflow:** Feature branches
- **Branch Naming:** `type/TASK-N-short-description`
- **Commit Convention:** Conventional Commits
- **PR Requirements:** No PR — push directly to main

**ENV Variables:**
```
BOT_TOKEN
DATABASE_URL
REDIS_URL
OPENAI_API_KEY
MAX_FREE_DAILY_NEWS=3
SUBSCRIPTION_STARS=150
SUBSCRIPTION_DAYS=30
LOG_LEVEL=INFO
```


---
## S11 — TESTING STRATEGY

- **Philosophy:** Critical paths only
- **Unit Test Tool:** pytest + pytest-asyncio
- **Integration Test Tool:** pytest با test database
- **E2E Test Tool:** N/A (manual Telegram test)
- **Coverage Target:** 60%
- **Test File Location:** `tests/` at root
- **Mocking Strategy:** unittest.mock
- **CI Enforcement:** Advisory only

Always test:
- subscription expiry logic
- daily news limit برای free users
- payment verification flow
- RSS parser با invalid feed


---
## S12 — PERFORMANCE RULES

- **Max Page Size:** 10
- **N+1 Queries:** FORBIDDEN — always use eager loading or JOIN
- **No Full Table Scans:** DB index required before any WHERE/JOIN/ORDER BY
- **Lazy Loading:** No

Operations that MUST always be background jobs:
- RSS fetch از منابع خارجی (APScheduler)
- ارسال daily digest به همه کاربران (APScheduler)
- فراخوانی OpenAI API برای خلاصه‌سازی (APScheduler)
- هر عملیاتی که > 100 user را در یک دوره لمس کند


---
## S13 — DECISIONS LOG

- **WHY python-telegram-bot over aiogram:** آشنایی بیشتر تیم، داکیومنتیشن بهتر
- **WHY APScheduler over Celery:** پروژه کوچک است — Celery overkill است
- **WHY PostgreSQL over SQLite:** نیاز به concurrent writes و indexing قوی
- **WHY Telegram Stars over CryptoPay:** بدون KYC، built-in در تلگرام

**Rejected Approaches — NEVER suggest these again:**
- ❌ Celery + RabbitMQ — Reason: overkill برای این مقیاس
- ❌ MongoDB — Reason: schema-less نیازی نیست، relations داریم
- ❌ Polling در production — Reason: سرور VPS است، webhook بهتر است
- ❌ Raw SQL — Reason: SQLAlchemy ORM کافی است


---
## CURRENT STATE

**Last Task ID:** TASK-000
**Last BUG Number:** BUG-000
**Last DEBT Number:** DEBT-000
**Last Updated:** 2026-02-25
**Project Status:** FRESH START — no features implemented yet.

### ✅ COMPLETED
- Nothing completed yet.

### 🔄 IN PROGRESS
- Nothing in progress.

### ⏳ BACKLOG
- TASK-001: Project setup — Docker, DB connection, Alembic init
- TASK-002: /start handler — ثبت user در DB
- TASK-003: RSS fetcher — دریافت و ذخیره اخبار از feedparser
- TASK-004: Daily digest scheduler — ارسال خودکار روزانه
- TASK-005: Payment flow — Telegram Stars subscription

### 🐛 KNOWN BUGS
- No known bugs yet.

### ⚠️ TECH DEBT
- No tech debt yet.

### 🔒 OFF-LIMITS
- .env — هرگز تغییر نده یا log نکن

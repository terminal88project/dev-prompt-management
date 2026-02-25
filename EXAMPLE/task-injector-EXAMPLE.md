> 📎 Project Context: project-context.md already in chat

---

## 🎯 TASK HEADER

| Field        | Value                                      |
|--------------|--------------------------------------------|
| **Task ID**  | TASK-002                                   |
| **Name**     | /start handler — register user in DB       |
| **Mode**     | Feature                                    |
| **Priority** | High                                       |

---

## 🔗 CONTEXT

- **Depends on Task:** TASK-001 (Docker + DB باید راه باشد)
- **Continues from:** None
- **Related Files:** db/models.py, db/session.py
- **Last Session Note:** TASK-001 انجام شد — Docker و DB connection کار می‌کند، Alembic init شد، جدول users ساخته شده.

---

## 📋 DESCRIPTION

وقتی کاربر برای اول بار /start را می‌زند یا دوباره /start می‌زند:

1. اطلاعات کاربر از telegram (user_id, username, first_name) دریافت شود
2. اگر کاربر در DB وجود ندارد → INSERT شود
3. اگر کاربر وجود دارد → username و first_name آپدیت شود (upsert)
4. پیام خوش‌آمد با InlineKeyboard نمایش داده شود:
   - دکمه «📰 اخبار امروز»
   - دکمه «⭐ اشتراک پریمیوم»
   - دکمه «ℹ️ راهنما»

---

## ✅ EXPECTED OUTPUT

- /start → user در جدول users ذخیره می‌شود
- اگر user قبلاً ثبت شده، فقط آپدیت می‌شود (بدون duplicate)
- پیام خوش‌آمد با InlineKeyboard نمایش داده می‌شود
- اگر خطای DB رخ داد → پیام خطای فارسی نمایش داده شود

---

## 🏁 ACCEPTANCE CRITERIA

- [ ] کاربر جدید در جدول users ذخیره می‌شود
- [ ] /start دوباره برای کاربر موجود، duplicate row ایجاد نمی‌کند
- [ ] پیام خوش‌آمد شامل ۳ دکمه inline است
- [ ] خطای DB لاگ می‌شود و به کاربر پیام مناسب نشان داده می‌شود

---

## 📁 FILES

### Files to Create
- `bot/handlers/start.py`         → هندلر /start
- `bot/services/user_service.py`  → منطق upsert کاربر
- `bot/keyboards/main_keyboard.py`→ InlineKeyboard خوش‌آمد

### Files to Modify
- `main.py` → اضافه کردن start handler به Application

### DO NOT TOUCH
- `.env`           — اطلاعات حساس
- `db/models.py`   — در TASK-001 ساخته شده، تغییر نده

---

## ⚠️ EDGE CASES TO HANDLE

- اگر telegram_id تکراری بود → upsert (ON CONFLICT DO UPDATE)
- اگر username کاربر None بود → NULL در DB ذخیره شود (مجاز)
- اگر اتصال DB قطع بود → خطا لاگ شود، پیام فارسی به کاربر
- اگر کاربر از group chat /start بزند → همان رفتار (فعلاً فرقی ندارد)

---

## 🚫 AVOID

- Raw SQL نزن — فقط SQLAlchemy ORM
- telegram.ext.filters وارد نکن مگر لازم باشد
- پیام‌ها را به انگلیسی ننویس — همه text فارسی باشد
- بیش از یک مسئولیت در user_service نگذار

---

## 🗃️ NEW DB CHANGES NEEDED

```
جدول users از TASK-001 وجود دارد — تغییر schema لازم نیست.
فقط upsert logic در service نوشته می‌شود.

ROLLBACK PLAN:
  N/A — فقط code است، migration نیست
```

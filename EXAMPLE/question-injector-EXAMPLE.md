> 📎 Project Context: project-context.md already in chat

---

## ❓ QUESTION

| Field             | Value                                                   |
|-------------------|---------------------------------------------------------|
| **Priority**      | Blocking — can't proceed without answer                |
| **Type**          | Architectural                                           |

**Question:**
برای daily digest که باید هر روز ساعت ۸ صبح به تمام کاربران ارسال شود، آیا APScheduler کافی است یا باید از یک background job جدا (مثل Celery) استفاده کنم؟ اگر تعداد کاربران به ۱۰،۰۰۰ نفر رسید چه اتفاقی می‌افتد؟ آیا ارسال پیام به ۱۰،۰۰۰ کاربر در یک job یک مشکل performance ایجاد می‌کند؟

---

## 🔗 CONTEXT FOR THIS QUESTION

- **Related Blueprint Sections:** TECH STACK, ARCHITECTURE, PERFORMANCE RULES, DECISIONS LOG
- **Related Files:** scheduler/jobs.py (هنوز ساخته نشده)
- **Background:**
  پروژه Modular Monolith است و Celery رد شده (DECISIONS LOG). APScheduler 3.10 در stack است.
  Telegram Bot API محدودیت 30 پیام در ثانیه دارد. سرور VPS با 2GB RAM است.
  می‌خواهم بدانم آیا باید از asyncio.sleep بین پیام‌ها استفاده کنم یا روش بهتری هست.

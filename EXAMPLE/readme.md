سه فایل نمونه کامل آماده دانلود است. پروژه نمونه: **PremiumNewsBot** — یک ربات تلگرام اشتراکی با Python.

***

## 📄 `project-context-EXAMPLE.md` 

این فایل را کپی کن، نام را به `project-context.md` تغییر بده و برای پروژه خودت تطبیق بده. مهم‌ترین بخش‌های پر شده:

**S1 — IDENTITY:** اطلاعات کامل پروژه مثل نام، نوع، مدل کسب‌وکار (Freemium)، و deadline واقعی 

**S4 — ARCHITECTURE:** توجه کن که فقط یک گزینه برای هر فیلد انتخاب شده و بقیه پاک شدند — مثلاً `Modular Monolith` به جای `(Monolith / Microservices / ...)` 

**S7 — DATABASE SCHEMA:** چهار جدول واقعی با تمام فیلدها، constraint ها، relationship ها و index های لازم تعریف شده 

**S13 — DECISIONS LOG:** دلیل انتخاب هر تکنولوژی و رویکردهای رد شده (مثلاً Celery و MongoDB رد شده‌اند و AI هرگز نباید آن‌ها را پیشنهاد دهد) 

**CURRENT STATE:** backlog اولیه با ۵ تسک از پیش تعریف شده 

***

## 📄 `task-injector-EXAMPLE.md` 

این فایل نشان می‌دهد چطور `task-injector.md` را برای **TASK-002** (هندلر /start) پر کنی :

- **Depends on Task: TASK-001** — یعنی AI می‌داند که DB باید از قبل آماده باشد
- **Description** دقیق و مرحله به مرحله — هیچ ابهامی ندارد
- **Files to Create/Modify/DO NOT TOUCH** — مشخص است AI کجا کار کند و کجا دست نزند
- **Edge Cases** — upsert به جای insert، null username، قطعی DB 

***

## 📄 `question-injector-EXAMPLE.md` 

نمونه یک سوال architectural قبل از ساخت scheduler :

- **Priority: Blocking** — یعنی AI می‌داند نمی‌توانی ادامه دهی تا جواب بگیری
- سوال دقیق با عدد (۱۰،۰۰۰ user، 30 msg/sec) — جواب کاملاً دقیق می‌گیری 
- **Background** توضیح می‌دهد که Celery قبلاً رد شده، پس AI نباید آن را پیشنهاد دهد 

***

## 🔄 روند استفاده از این نمونه‌ها

```
۱. project-context-EXAMPLE.md را دانلود کن
   → نام را به project-context.md تغییر بده
   → S1, S3, S5, S7 را برای پروژه خودت ویرایش کن

۲. task-injector-EXAMPLE.md را دانلود کن
   → نام را به task-injector.md تغییر بده
   → هر بار که تسک جدید داری، محتوا را عوض کن

۳. یک چت جدید باز کن در Claude/GPT
   → core-directives.md + project-context.md + task-injector.md را attach کن
   → بفرست و جواب کامل بگیر

۴. بخش STATE UPDATE خروجی AI را کپی کن
   → در بخش CURRENT STATE فایل project-context.md جایگزین کن
```
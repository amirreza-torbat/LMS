---
tags: [Layer, Core, هسته]
aliases: [Core Engine, لایه هسته, موتور اصلی]
layer: Core
order: 1
---

# 🧠 Core Engine — لایه هسته

> [!abstract] خلاصه
> «موتور اصلی» پلتفرم که در هر دو نسخه (دانشگاهی و سازمانی) **بدون تغییر** باقی می‌ماند. این بخش یک‌بار ساخته می‌شود و برای هر دو بازار قابل استفاده است.

---

## 🎯 هدف لایه هسته

این لایه **زیربنای مشترک** طرح است. تمام قابلیت‌های پایه‌ای که هر دو نسخه سازمانی و آکادمیک به آن نیاز دارند در اینجا پیاده‌سازی می‌شود.

---

## 📦 مؤلفه‌های لایه هسته

```mermaid
flowchart LR
    subgraph Core["🧠 Core Engine"]
        UM[مدیریت کاربران<br/>User Management]
        CDE[موتور محتوا<br/>Content Delivery Engine]
        AE[سیستم ارزیابی<br/>Assessment Engine]
        CE[صدور گواهی<br/>Certification Engine]
        DB[داشبورد تعاملی<br/>Dashboard]
    end

    subgraph Infra["⚙️ زیرساخت فنی"]
        PL[Plugin Loader]
        AI_Layer[Access & Identity]
        Course[Course Entity]
        EDA[Event Bus]
    end

    Core --> Infra
    Infra -. feeds .-> Core

    style Core fill:#1B2A4A,color:#FFFFFF
    style Infra fill:#2D4A3E,color:#FFFFFF
```

---

## 📋 جزئیات هر مؤلفه

### ۱. مدیریت کاربران (User Management)
- سیستم مدیریت نقش‌ها
- پروفایل‌های کاربری
- احراز هویت
- دسته‌بندی کاربران بر اساس فاکتورهای مختلف

### ۲. موتور محتوا (Content Delivery Engine)
- آپلودر
- پلیر ویدیو
- پلیر پادکست
- مدیریت PDF
- پشتیبانی SCORM و H5P

### ۳. سیستم ارزیابی (Assessment Engine)
- بانک سؤالات
- انواع سؤالات:
  - درست و غلط
  - چهارگزینه‌ای
  - تشریحی
  - Drag & Drop
  - ...
- موتور آزمون‌ساز

### ۴. صدور گواهی (Certification Engine)
- تولید خودکار گواهینامه‌های دیجیتال
- قابلیت استعلام
- بارکد

### ۵. داشبورد تعاملی
- نمایش وضعیت پیشرفت برای کاربر
- اعلان‌ها
- یادآوری‌های سیستمی

---

## ⚙️ جزئیات فنی و راهبردی

### ۱. مدیریت ماژولار (Plugin Loader)

```mermaid
flowchart TB
    Start[بوت اپلیکیشن] --> Check[بررسی ماژول‌های فعال]
    Check --> Load[بارگذاری ماژول‌ها در Routes]
    Load --> Ready[سیستم آماده]

    subgraph Modules[ماژول‌های ممکن]
        M1[محتوای آفلاین]
        M2[آزمون]
        M3[کلاس آنلاین]
        M4[تکلیف]
        M5[نظرسنجی]
    end

    Check --> Modules

    style Start fill:#1B7D46,color:#FFFFFF
    style Ready fill:#1B7D46,color:#FFFFFF
    style Modules fill:#FFF2CC,color:#000000
```

> [!important] خروجی
> سیستمی که هنگام بالا آمدن اپلیکیشن، بررسی می‌کند کدام ماژول‌ها فعال هستند و آنها را در مسیرهای (Routes) سیستم قرار می‌دهد. این اجازه می‌دهد Enterprise و Academic به‌صورت دو لایه مجزا روی هسته سوار شوند.

### ۲. لایه هویت و دسترسی (Access & Identity)

> [!warning] تصمیم کلیدی
> در این مرحله نباید سیستم فقط برای «دانشجو» یا «کارمند» ساخته شود. یک سیستم Identity عمومی نیاز است که:
> - در فاز سازمانی → `Organization ID` اضافه شود
> - در فاز آکادمیک → `Student Number` اضافه شود

**خروجی:** سرویسی که هویت کاربر را تأیید کند و بگوید این کاربر «چه کسی» است، نه «چه نقشی» دارد.

### ۳. ساختار محتوا (Course Entity)

مفهوم «دوره» به‌صورت **Generic** پیاده می‌گردد:

```mermaid
flowchart LR
    Core[Course Container<br/>Generic] --> Ent[Enterprise]
    Core --> Aca[Academic]

    Ent --> E1[دوره آموزشی ضمن خدمت]
    Aca --> A1[کلاس درسی ترمیک]

    style Core fill:#8E44AD,color:#FFFFFF
    style E1 fill:#1B7D46,color:#FFFFFF
    style A1 fill:#1B7D46,color:#FFFFFF
```

> [!note] نکته مهم
> دیتابیس تغییر نمی‌کند، فقط «رفتار» آن در ماژول‌های بعدی غنی‌تر می‌شود.

### ۴. زیرساخت ایونت (Event-Driven Architecture)

**مهم‌ترین بخش برای آینده پروژه!**

```mermaid
sequenceDiagram
    actor User as کاربر
    participant Core as Core Engine
    participant Bus as Event Bus
    participant Reporter as ماژول گزارش‌ساز (سازمانی)
    participant Grader as ماژول نمره‌دهی (آکادمیک)

    User->>Core: اتمام دوره
    Core->>Bus: انتشار course_completed
    Bus->>Reporter: دریافت ایونت (Enterprise)
    Bus->>Grader: دریافت ایونت (Academic)
    Reporter->>Reporter: تهیه گزارش پیشرفت
    Grader->>Grader: ثبت نمره نهایی
```

> [!important] چرا مهم است؟
> - در فاز سازمانی: ماژول گزارش‌ساز به این ایونت گوش می‌دهد
> - در فاز آکادمیک: ماژول نمره‌دهی به این ایونت گوش می‌دهد
> - این معماری جدایی کامل Core از Extensions را تضمین می‌کند

---

## 📊 تحویل‌های فاز ۱ (Core Engine)

| # | لایه | فعالیت‌های کلیدی | خروجی‌های اصلی |
|---|---|---|---|
| ۱ | تحلیل و طراحی | جمع‌آوری و تحلیل نیازمندی‌ها، طراحی معماری | سند نیازمندی‌های محصول، سند معماری سیستم |
| ۲ | مدیریت هویت و دسترسی | طراحی User/Role/Permission، JWT، احراز هویت عمومی | سرویس Auth، APIهای login/register |
| ۳ | ساختار محتوا و دوره | طراحی Course Entity، انواع محتوا، گروهبندی | ساختار دیتابیس منعطف، CRUD دوره |
| ۴ | زیرساخت ارتباطی و ایونت | Event Bus، لاگینگ مرکزی، Webhook | Audit Log، API Gateway |
| ۵ | تنظیمات و هسته مرکزی | Tenant/Config، Plugin Loader | پنل System Admin، فعال/غیرفعال ماژول‌ها |

---

## 🔗 ارتباط با سایر لایه‌ها

- [[Enterprise Standard Layer — لایه سازمانی استاندارد]] — سوار می‌شود روی Core
- [[Enterprise Smart Layer — لایه سازمانی هوشمند]] — سوار می‌شود روی Core
- [[Academic Layer — لایه آکادمیک]] — سوار می‌شود روی Core
- [[Marketplace Layer — لایه بازار فروش]] — سوار می‌شود روی Core

---

## 🏷️ برچسب‌ها
#Core #هسته #معماری #PluginLoader #EventBus #Identity #CourseEntity

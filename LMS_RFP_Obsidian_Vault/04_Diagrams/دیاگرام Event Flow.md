---
tags: [Diagram, Event, Event Flow]
aliases: [دیاگرام Event Flow, Event Bus]
---

# 🔄 دیاگرام Event Flow

> [!abstract] خلاصه
> معماری Event-Driven که مهم‌ترین بخش Core Engine برای آینده است.

---

## ۱. معماری Event Bus

```mermaid
flowchart TB
    subgraph Publishers[ناشران ایونت]
        P1[Core Engine]
        P2[User Module]
        P3[Assessment Module]
        P4[Course Module]
    end

    subgraph Bus[Event Bus]
        EB{Message Broker<br/>RabbitMQ}
    end

    subgraph Subscribers[مشترکین ایونت]
        S1[Enterprise Reporter]
        S2[Academic Grader]
        S3[AI Module]
        S4[Gamification]
        S5[Notification System]
    end

    P1 --> EB
    P2 --> EB
    P3 --> EB
    P4 --> EB

    EB --> S1
    EB --> S2
    EB --> S3
    EB --> S4
    EB --> S5

    style Bus fill:#8E44AD,color:#FFFFFF
    style Publishers fill:#1B7D46,color:#FFFFFF
    style Subscribers fill:#1B2A4A,color:#FFFFFF
```

---

## ۲. ایونت course_completed

```mermaid
sequenceDiagram
    actor User as کاربر
    participant Core as Core Engine
    participant Bus as Event Bus
    participant Reporter as Enterprise Reporter
    participant Grader as Academic Grader
    participant AI as AI Module
    participant Gamif as Gamification
    participant Notif as Notification

    User->>Core: اتمام آخرین درس دوره
    Core->>Core: بررسی تکمیل
    Core->>Bus: publish(course_completed)

    par موازی
        Bus->>Reporter: notify
        Reporter->>Reporter: تولید گزارش پیشرفت
    and
        Bus->>Grader: notify
        Grader->>Grader: ثبت نمره نهایی
    and
        Bus->>AI: notify
        AI->>AI: تحلیل الگوی یادگیری
    and
        Bus->>Gamif: notify
        Gamif->>Gamif: اعطای Badge/Points
    and
        Bus->>Notif: notify
        Notif->>User: اعلان تبریک
    end
```

---

## ۳. ایونت‌های اصلی سیستم

| ایونت | ناشر | مشترکین | توضیح |
|---|---|---|---|
| `course_completed` | Core Engine | Reporter, Grader, AI, Gamif | کاربر دوره را تمام کرد |
| `user_registered` | User Module | Notif, Gamif | کاربر جدید ثبت‌نام کرد |
| `quiz_submitted` | Assessment | Grader, AI, Gamif | کاربر آزمون را ثبت کرد |
| `lesson_completed` | Course Module | Gamif, AI | کاربر یک درس را تمام کرد |
| `badge_earned` | Gamification | Notif | کاربر Badge جدید گرفت |
| `level_up` | Gamification | Notif, AI | کاربر به سطح بالاتر رفت |
| `enrollment_created` | Enrollment | Notif, Gamif | کاربر در دوره ثبت‌نام کرد |
| `certificate_issued` | Certification | Notif | گواهی صادر شد |
| `fraud_detected` | AI/Proctoring | Notif (Admin) | تقلب تشخیص داده شد |
| `payment_completed` | Marketplace | Notif, Course (Unlock) | پرداخت موفق |

---

## ۴. چرا Event-Driven؟

```mermaid
mindmap
  root((مزایای Event-Driven))
    جداسازی ماژول‌ها
      Core مستقل
      Extensions مستقل
      بدون وابستگی مستقیم
    مقیاس‌پذیری
      هر ماژول scale جداگانه
      پردازش موازی
      بدون bottleneck
    توسعه‌پذیری
      افزودن ماژول جدید آسان
      بدون تغییر Core
      فقط subscribe کن
    تست‌پذیری
      هر ماژول جداگانه
      Mock ایونت‌ها
      Integration test آسان
    Resilience
      اگر یک ماژول از کار افتاد
      بقیه کار می‌کنند
      Retry mechanism
```

---

## ۵. الگوی پیاده‌سازی

### Pattern: Publish-Subscribe

```mermaid
flowchart LR
    Publisher[📤 Publisher] -->|publish event| Topic[📨 Topic/Queue]
    Topic -->|consume| Sub1[📥 Subscriber 1]
    Topic -->|consume| Sub2[📥 Subscriber 2]
    Topic -->|consume| Sub3[📥 Subscriber 3]

    style Publisher fill:#1B7D46,color:#FFFFFF
    style Topic fill:#8E44AD,color:#FFFFFF
    style Sub1 fill:#1B2A4A,color:#FFFFFF
    style Sub2 fill:#1B2A4A,color:#FFFFFF
    style Sub3 fill:#1B2A4A,color:#FFFFFF
```

### نمونه کد (مفهومی)

```csharp
// Publish
await _eventBus.PublishAsync(new CourseCompletedEvent {
    UserId = userId,
    CourseId = courseId,
    CompletedAt = DateTime.UtcNow
});

// Subscribe (in Enterprise Reporter)
public class CourseCompletedEventHandler : IEventHandler<CourseCompletedEvent>
{
    public async Task HandleAsync(CourseCompletedEvent @event)
    {
        await _reportService.GenerateProgressReport(@event.UserId, @event.CourseId);
    }
}
```

---

## 🔗 پیوندها

- بازگشت: [[دیاگرام معماری کلی]]
- جزئیات: [[Core Engine — لایه هسته]] (Event Bus)
- مرتبط: [[Enterprise Smart Layer — لایه سازمانی هوشمند]] (AI, Gamification)

---

#دیاگرام #Event-Driven #EventBus #Architecture #Mermaid

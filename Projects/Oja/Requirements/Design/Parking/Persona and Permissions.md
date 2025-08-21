{
  "Permissions": {
    "parking.profile.manage": "مدیریت پروفایل پارکینگ (نام، آدرس، ساعات کاری، امکانات، قوانین داخلی).",
    "parking.verification.submit": "ارسال/به‌روزرسانی مدارک جهت دریافت/تمدید نشان تأیید (Verified Badge).",

    "parking.capacity.live.manage": "تنظیم ظرفیت آنلاین/داینامیک (مثلاً 90%) و حد آستانه‌ها.",
    "parking.buffer.time.manage": "مدیریت Buffer Time برای جلوگیری از تداخل رزروها.",
    "parking.calendar.blackout.manage": "ثبت بازه‌های تعطیلی/Blackout و محدودیت‌های زمانی.",
    "parking.spot.type.manage": "مدیریت انواع اسپات‌ها/زون‌ها و موجودی هر کدام.",
    "parking.pricing.manage": "مدیریت قیمت‌گذاری پایه و قوانین Dynamic Pricing.",
    "parking.vip.slots.manage": "تعریف/مدیریت VIP Slots پارکینگ.",
    "parking.waitlist.manage": "مدیریت Waitlist (اولویت‌دهی، تخصیص خودکار/دستی).",

    "parking.reservation.view.all": "مشاهده همه رزروهای فعال و تاریخچه پارکینگ.",
    "parking.reservation.override": "ایجاد/تمدید/لغو دستی رزرو (Override) با رعایت Policy.",
    "parking.reservation.checkinout": "ثبت Check-in/Check-out حضوری/سیستمی.",
    "parking.offline.mode.use": "فعال‌سازی حالت آفلاین و صدور/تأیید کدهای SMS برای ورود/خروج.",
    "parking.violation.issue": "ثبت تخلف (No-Show/Delay/Overstay) و محاسبه جریمه.",
    "parking.overstay.manage": "مدیریت قوانین تأخیر/Overstay و اعمال هزینه‌ها.",

    "parking.content.moderate": "مدیریت محتوای صفحه پارکینگ (عکس‌ها/توضیحات) در سطح همان پارکینگ.",
    "parking.content.takedown": "حذف/تعلیق محتوای ناقض دستورالعمل‌های پارکینگ.",
    "parking.content.restore": "بازگردانی محتوای تعلیق‌شده در صورت رفع مشکل.",

    "parking.ticket.manage": "مدیریت تیکت‌های مشتریان مرتبط با پارکینگ.",
    "parking.notification.send": "ارسال اعلان به مشتریان رزروکننده (اطلاع ظرفیت/تغییرات مهم).",

    "parking.finance.read": "مشاهده گزارش‌های مالی پارکینگ (tenant-scoped).",
    "parking.transaction.read": "مشاهده تراکنش‌های پارکینگ (tenant-scoped).",
    "parking.payout.read": "مشاهده تسویه‌ها و واریزی‌ها (tenant-scoped).",
    "parking.finance.export": "خروجی گرفتن از داده‌های مالی پارکینگ.",
    "parking.finance.refund.approve": "تأیید/رد ریفاند در سقف مجاز Policy پارکینگ.",
    "dispute.respond": "پاسخ به دیسپیوت‌های مالی مرتبط با این پارکینگ.",

    "parking.analytics.view": "مشاهده داشبوردهای عملیاتی و KPIها.",
    "parking.report.view": "مشاهده گزارش‌های عملکرد/ترافیک/تبدیل.",
    "parking.audit.read": "مشاهده لاگ‌های ممیزی داخلی پارکینگ.",

    "parking.staff.manage": "مدیریت کاربران/نقش‌های داخلی پارکینگ (Operator/Attendant/…)",

    "parking.lpr.config.manage": "پیکربندی دوربین‌های LPR (شناسه‌خوان پلاک) و قوانین تطبیق.",
    "parking.gate.config.manage": "پیکربندی کنترلر گیت/Barrier و رفتارهای باز/بسته.",
    "parking.device.status.view": "مشاهده وضعیت دستگاه‌ها (آنلاین/آفلاین/خطا).",
    "parking.webhook.manage": "مدیریت Webhookها، روتیشن Secret و تست ارسال.",
    "parking.api.key.manage": "مدیریت API Keys برای یکپارچه‌سازی‌های مجاز."
  },

  "Personas": {
    "Parking.Owner": {
      "description": "مالک/صاحب امتیاز پارکینگ با اختیار کامل مدیریت کسب‌وکار همان پارکینگ.",
      "permissions": [
        "parking.profile.manage",
        "parking.verification.submit",

        "parking.capacity.live.manage",
        "parking.buffer.time.manage",
        "parking.calendar.blackout.manage",
        "parking.spot.type.manage",
        "parking.pricing.manage",
        "parking.vip.slots.manage",
        "parking.waitlist.manage",

        "parking.reservation.view.all",
        "parking.reservation.override",
        "parking.reservation.checkinout",
        "parking.offline.mode.use",
        "parking.violation.issue",
        "parking.overstay.manage",

        "parking.content.moderate",
        "parking.content.takedown",
        "parking.content.restore",

        "parking.ticket.manage",
        "parking.notification.send",

        "parking.finance.read",
        "parking.transaction.read",
        "parking.payout.read",
        "parking.finance.export",
        "parking.finance.refund.approve",
        "dispute.respond",

        "parking.analytics.view",
        "parking.report.view",
        "parking.audit.read",

        "parking.staff.manage",

        "parking.lpr.config.manage",
        "parking.gate.config.manage",
        "parking.device.status.view",
        "parking.webhook.manage",
        "parking.api.key.manage"
      ]
    },

    "Parking.Admin": {
      "description": "مدیر عملیاتی پارکینگ با مدیریت ظرفیت/قیمت/رزرو و نظارت مالی در همان پارکینگ.",
      "inherits": ["Parking.Operator", "Parking.Financial"],
      "permissions": [
        "parking.profile.manage",
        "parking.verification.submit",

        "parking.capacity.live.manage",
        "parking.buffer.time.manage",
        "parking.calendar.blackout.manage",
        "parking.spot.type.manage",
        "parking.pricing.manage",
        "parking.vip.slots.manage",
        "parking.waitlist.manage",

        "parking.content.moderate",
        "parking.content.takedown",
        "parking.content.restore",

        "parking.staff.manage",

        "parking.audit.read"
      ]
    },

    "Parking.Operator": {
      "description": "اپراتور شیفت با تمرکز بر عملیات روزانه: رزروها، چک‌این/چک‌اوت، وضعیت ظرفیت و حالت آفلاین.",
      "permissions": [
        "parking.reservation.view.all",
        "parking.reservation.checkinout",
        "parking.reservation.override",
        "parking.offline.mode.use",
        "parking.waitlist.manage",
        "parking.violation.issue",
        "parking.overstay.manage",
        "parking.notification.send",
        "parking.ticket.manage",
        "parking.device.status.view"
      ]
    },

    "Parking.Attendant": {
      "description": "کاربر با سطح دسترسی کانتر/کیوسک برای کارهای حضوری ساده.",
      "permissions": [
        "parking.reservation.view.all",
        "parking.reservation.checkinout",
        "parking.offline.mode.use",
        "parking.notification.send",
        "parking.device.status.view"
      ]
    },

    "Parking.Financial": {
      "description": "مسئول مالی پارکینگ با دسترسی فقط‌خواندنی مالی و پاسخ به دیسپیوت در چارچوب پارکینگ.",
      "permissions": [
        "parking.finance.read",
        "parking.transaction.read",
        "parking.payout.read",
        "parking.finance.export",
        "dispute.respond"
      ]
    },

    "Parking.Content.Moderator": {
      "description": "مسئول محتوا در سطح همان پارکینگ (تصاویر/توضیحات/به‌روزرسانی‌های صفحه).",
      "permissions": [
        "parking.content.moderate",
        "parking.content.takedown",
        "parking.content.restore"
      ]
    },

    "Parking.Integrator": {
      "description": "تکنیسین/یکپارچه‌ساز برای LPR/گیت و وبهوک‌ها؛ بدون دسترسی مالی یا رزروی.",
      "permissions": [
        "parking.lpr.config.manage",
        "parking.gate.config.manage",
        "parking.device.status.view",
        "parking.webhook.manage",
        "parking.api.key.manage"
      ]
    },

    "Parking.Analyst": {
      "description": "تحلیل‌گر با دسترسی فقط‌خواندنی به داشبوردها و گزارش‌ها.",
      "permissions": [
        "parking.analytics.view",
        "parking.report.view"
      ]
    },

    "Parking.Viewer": {
      "description": "نمایش فقط‌خواندنی اطلاعات پایه عملیاتی برای ناظران داخلی پارکینگ.",
      "permissions": [
        "parking.reservation.view.all",
        "parking.device.status.view",
        "parking.analytics.view"
      ]
    }
  },

  "Notes": [
    "تمام دسترسی‌ها tenant-scoped به همان پارکینگ هستند.",
    "Refund/Cancel هوشمند بر اساس Policy؛ «parking.finance.refund.approve» فقط در سقف مجاز.",
    "ارث‌بری Personas برای کاهش تکرار (مثال: Parking.Admin از Operator و Financial ارث می‌برد).",
    "یکپارچه‌سازی LPR/گیت از طریق Adapter/Webhook/API Key و روتیشن Secret."
  ]
}

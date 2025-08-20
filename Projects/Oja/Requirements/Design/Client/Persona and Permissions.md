{
  "Permissions": {
    "reservation.create": "ایجاد رزرو جدید با انتخاب بازه زمانی و نوع اسپات.",
    "reservation.extend": "تمدید رزرو جاری در صورت ظرفیت آزاد.",
    "reservation.cancel": "لغو رزرو با اعمال قوانین کنسلی.",
    "reservation.view": "مشاهده جزئیات رزروهای فعال و تاریخچه.",
    "reservation.refund.request": "ثبت درخواست بازگشت وجه طبق Policy.",
    "waitlist.join": "پیوستن به لیست انتظار پارکینگ پر.",
    "report.create": "ثبت گزارش/شکایت مرتبط با رزرو یا پارکینگ.",
    "report.media.upload": "بارگذاری مدرک (عکس/ویدیو) برای پشتیبانی گزارش.",
    "wallet.view": "مشاهده موجودی و تراکنش‌های کیف پول.",
    "wallet.topup": "شارژ کیف پول با روش‌های پرداخت مجاز.",
    "receipt.download": "دانلود رسید پرداخت/رزرو.",
    "profile.manage": "مدیریت اطلاعات پروفایل و تنظیمات شخصی.",
    "vehicle.manage": "افزودن/ویرایش/حذف خودرو و پلاک‌های کاربر.",
    "favorite.manage": "مدیریت لیست پارکینگ‌های موردعلاقه.",
    "notification.manage": "مدیریت ترجیحات اعلان‌ها (Push/SMS/Email).",
    "vip.benefits.use": "استفاده از مزایای VIP پارکینگ‌ها.",
    "booking.early.access": "دسترسی زودهنگام به ظرفیت‌ها در بازه‌های پیک.",
    "discount.apply": "استفاده از تخفیف‌ها/کدهای تخفیف مجاز.",
    "pay.on.exit.use": "انتخاب مدل پرداخت هنگام خروج برای رزرو اول یا پلن مجاز.",
    "corp.manage": "مدیریت تنظیمات کلی حساب سازمانی.",
    "corp.customer.manage": "مدیریت مشتری‌های سازمان (مانند تعلیق).",
    "corp.customer.manage.content.ban": "محدودسازی توانایی تولید محتوای مشتریان سازمان.",
    "corp.members.manage": "مدیریت اعضا/نقش‌های سازمان.",
    "corp.reservation.manage": "ایجاد/مدیریت رزروهای سازمانی.",
    "corp.billing.view": "مشاهده صورتحساب‌ها و وضعیت پرداخت سازمان.",
    "corp.invoice.download": "دانلود فاکتورهای سازمانی.",
    "corp.content.moderate": "بازبینی و تصمیم‌گیری روی محتوای سازمان.",
    "corp.content.takedown": "حذف/غیرفعال‌سازی محتوای ناقض قوانین (سازمانی).",
    "corp.content.restore": "بازگردانی محتوای حذف‌شده (سازمانی).",
    "ticket.create": "ایجاد تیکت پشتیبانی.",
    "ticket.view": "مشاهده وضعیت و تاریخچه تیکت‌ها.",
    "ticket.reply": "پاسخ/به‌روزرسانی تیکت‌های خود.",
    "dispute.open": "باز کردن پرونده اختلاف برای تراکنش/رزرو.",
    "kyc.submit": "ارسال مدارک احراز هویت (KYC).",
    "kyc.status.view": "مشاهده وضعیت پردازش KYC.",
    "auth.mfa.manage": "فعال/غیرفعال‌سازی و مدیریت 2FA/MFA.",
    "parking.finance.read": "مشاهده گزارش‌های مالی پارکینگ (tenant-scoped).",
    "parking.transaction.read": "مشاهده تراکنش‌های پارکینگ (tenant-scoped).",
    "parking.payout.read": "مشاهده تسویه‌ها و واریزی‌های پارکینگ (tenant-scoped).",
    "parking.finance.export": "خروجی گرفتن از داده‌های مالی پارکینگ (tenant-scoped).",
    "dispute.respond": "پاسخ به دیسپیوت‌های مالی مرتبط با پارکینگ خود.",
    "content.moderate": "بازبینی و تصمیم‌گیری روی محتوای کاربر/پارکینگ (شامل رسانه).",
    "content.takedown": "حذف/غیرفعال‌سازی محتوای ناقض قوانین.",
    "content.restore": "بازگردانی محتوای حذف‌شده.",
    "report.review.content": "رسیدگی به ریپورت‌های مرتبط با محتوا و اعمال نتیجه.",
    "security.log.read": "دسترسی فقط‌خواندنی به لاگ‌های امنیتی.",
    "security.alert.read": "مشاهده هشدارها/آلارم‌های امنیتی.",
    "security.findings.read": "مشاهده یافته‌ها/گزارش‌های تحلیل امنیتی.",
    "observability.read": "مشاهده متریک‌ها/تریس‌ها/لاگ‌های عملیاتی.",
    "audit.read": "مشاهده لاگ‌های ممیزی تغییرات و دسترسی‌ها."
  },
  "Personas": {
    "Customer.Limited": {
      "description": "کاربری که به دلیل تخلف محدود شده.",
      "permissions": [],
      "rules": []
    },
    "Customer.Basic": {
      "description": "کاربر عادی با حداقل دسترسی برای جستجو/رزرو/لغو و مدیریت پروفایل، کیف پول و تیکت.",
      "permissions": [
        "reservation.create",
        "reservation.view",
        "reservation.cancel",
        "reservation.extend",
        "reservation.refund.request",
        "waitlist.join",
        "wallet.view",
        "wallet.topup",
        "report.create",
        "report.media.upload",
        "receipt.download",
        "profile.manage",
        "vehicle.manage",
        "favorite.manage",
        "notification.manage",
        "ticket.create",
        "ticket.view",
        "ticket.reply",
        "kyc.submit",
        "kyc.status.view",
        "auth.mfa.manage"
      ],
      "rules": [
        "حداکثر ۲ رزرو فعال",
        "پنجره رزرو ≤ 48h",
        "مدت رزرو ≤ 8h"
      ]
    },
    "Customer.Loyalty.Silver": {
      "description": "مشتری وفادار با امکان استفاده از تخفیف و اولویت متوسط در لیست انتظار.",
      "inherits": ["Customer.Basic"],
      "permissions": [
        "discount.apply"
      ],
      "rules": [
        "اولویت Waitlist سطح 2",
        "کارمزد کنسلی کمتر"
      ]
    },
    "Customer.Loyalty.Gold": {
      "description": "مشتری پریمیوم با Early-access، مزایای VIP و اولویت بالای لیست انتظار.",
      "inherits": ["Customer.Basic"],
      "permissions": [
        "vip.benefits.use",
        "booking.early.access",
        "discount.apply"
      ],
      "rules": [
        "دسترسی Early-access به ظرفیت‌های پیک",
        "اولویت Waitlist سطح 1",
        "نشان VIP"
      ]
    },
    "Customer.Trial.PayLater": {
      "description": "برای اولین رزرو با امکان پرداخت هنگام خروج و مهلت حضور کوتاه.",
      "inherits": ["Customer.Basic"],
      "permissions": [
        "pay.on.exit.use"
      ],
      "rules": [
        "فقط رزرو اول",
        "مهلت حضور ۵ دقیقه",
        "No-Show خودکار"
      ]
    },
    "Corporate.Supervisor": {
      "description": "مدیریت Corporate.Admin به پایین با دسترسی کامل.",
      "permissions": [
        "corp.manage",
        "corp.members.manage",
        "corp.reservation.manage",
        "corp.billing.view",
        "corp.invoice.download",
        "corp.customer.manage",
        "corp.customer.manage.content.ban",
        "reservation.view",
        "ticket.create",
        "ticket.view",
        "ticket.reply",
        "dispute.open",
        "auth.mfa.manage"
      ],
      "rules": [
        "دسترسی نامحدود روی tenant سازمان خود"
      ]
    },
    "Corporate.Admin": {
      "description": "مدیر اکانت سازمان با مدیریت اعضا، رزرو و مشاهده صورتحساب‌ها.",
      "permissions": [
        "corp.reservation.manage",
        "corp.billing.view",
        "corp.invoice.download",
        "corp.customer.manage",
        "corp.customer.manage.content.ban",
        "reservation.view",
        "ticket.create",
        "ticket.view",
        "ticket.reply",
        "dispute.open",
        "auth.mfa.manage"
      ],
      "rules": [
        "فقط روی tenant خودش",
        "دو امضایی داخلی (Policy)"
      ]
    },
    "Corporate.Content.Moderator": {
      "description": "بازبین محتوای سازمانی با تمرکز روی تصاویر/نظرات.",
      "permissions": [
        "corp.content.moderate",
        "corp.content.takedown",
        "corp.content.restore",
        "report.review.content",
        "corp.customer.manage.content.ban"
      ],
      "rules": [
        "تمرکز بر محتوای متنی/تصویری",
        "تعلیق اکانت در حوزه T&S می‌ماند"
      ]
    },
    "Corporate.Booker": {
      "description": "کارمند سازمان که فقط رزروهای سازمان را مدیریت می‌کند و دسترسی مالی/اعضا ندارد.",
      "permissions": [
        "corp.reservation.manage",
        "reservation.view",
        "receipt.download",
        "ticket.create",
        "ticket.view",
        "ticket.reply"
      ],
      "rules": [
        "بدون دسترسی مالی/اعضا",
        "رزرو دستی فقط با پرداخت موفق و تایید Corporate.Admin"
      ]
    },
    "Corporate.Driver.Fleet": {
      "description": "راننده/عضو ناوگان با رزرو و مشاهده رسید در چارچوب سهمیه تخصیص یافته سازمان.",
      "permissions": [
        "reservation.create",
        "reservation.view",
        "receipt.download",
        "ticket.create",
        "ticket.view"
      ],
      "rules": [
        "محدود به سهمیه ناوگان"
      ]
    },
    "Family.Head": {
      "description": "مدیریت حساب خانوادگی با رزرو/تمدید برای چند خودرو و مدیریت اعضا و کیف پول خانواده.",
      "permissions": [
        "reservation.create",
        "reservation.view",
        "reservation.extend",
        "reservation.cancel",
        "vehicle.manage",
        "profile.manage",
        "wallet.view",
        "wallet.topup",
        "receipt.download",
        "ticket.create",
        "ticket.view",
        "ticket.reply",
        "auth.mfa.manage"
      ],
      "rules": [
        "سقف رزرو خانوادگی طبق Policy"
      ]
    },
    "Parking.Operator.Financial": {
      "description": "اپراتور مالی پارکینگ با دسترسی فقط‌خواندنی به داده‌های مالی همان پارکینگ.",
      "permissions": [
        "parking.finance.read",
        "parking.transaction.read",
        "parking.payout.read",
        "parking.finance.export",
        "dispute.respond"
      ],
      "rules": [
        "tenant-scoped",
        "بدون دسترسی به ظرفیت/رزرو"
      ]
    },
    "Content.Moderator": {
      "description": "مسئول بازبینی محتوای کاربران/پارکینگ‌ها و اعمال سیاست‌ها در تکمیل AI Moderation.",
      "permissions": [
        "content.moderate",
        "content.takedown",
        "content.restore",
        "report.review.content"
      ],
      "rules": []
    },
    "Security.Analyst.Auditor": {
      "description": "تحلیلگر امنیت با دسترسی فقط‌خواندنی به لاگ‌ها و هشدارها.",
      "permissions": [
        "security.log.read",
        "security.alert.read",
        "security.findings.read",
        "observability.read",
        "audit.read"
      ],
      "rules": [
        "Read-only",
        "بدون تغییر تنظیمات امنیتی/IAM"
      ]
    }
  }
}

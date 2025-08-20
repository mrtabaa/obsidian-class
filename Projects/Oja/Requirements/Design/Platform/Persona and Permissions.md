{
  "Permissions": {
    "platform.user.manage": "مدیریت کاربران (فعال‌سازی/تعلیق/حذف).",
    "platform.user.view": "مشاهده لیست و جزئیات کاربران.",
    "platform.user.kyc.review": "بررسی و تأیید مدارک KYC کاربران.",
    "platform.corp.manage": "مدیریت حساب‌های سازمانی (ایجاد/ویرایش/تعلیق).",
    "platform.corp.view": "مشاهده اطلاعات و اعضای سازمان‌ها.",
    "platform.parking.manage": "مدیریت پارکینگ‌ها (تأیید، تعلیق، Badge).",
    "platform.parking.view": "مشاهده اطلاعات پارکینگ‌ها و ظرفیت‌ها.",
    "platform.finance.overview": "نمای کلی مالی (تراکنش‌ها، درآمدها، کمیسیون‌ها).",
    "platform.finance.settlement": "مدیریت تسویه‌حساب با پارکینگ‌ها و سازمان‌ها.",
    "platform.content.moderate": "مدیریت محتوای کاربران و پارکینگ‌ها (متن/عکس/نظر).",
    "platform.report.review": "بررسی گزارش‌های کاربران (Reports).",
    "platform.ticket.manage": "مدیریت تیکت‌ها و درخواست‌های پشتیبانی.",
    "platform.dispute.manage": "رسیدگی به دیسپیوت‌های مالی بین کاربران/پارکینگ‌ها.",
    "platform.audit.read": "مشاهده لاگ‌های ممیزی پلتفرم.",
    "platform.security.manage": "مدیریت سیاست‌های امنیتی و IAM.",
    "platform.notification.send": "ارسال اعلان‌های سیستمی به کاربران.",
    "platform.config.manage": "مدیریت تنظیمات عمومی سیستم."
  },
  "Personas": {
    "Platform.SuperAdmin": {
      "description": "مدیر کل پلتفرم با دسترسی کامل به همه‌ی دامنه‌ها (کاربر، سازمان، پارکینگ، محتوا، امنیت و مالی).",
      "permissions": [
        "platform.user.manage",
        "platform.user.view",
        "platform.user.kyc.review",
        "platform.corp.manage",
        "platform.corp.view",
        "platform.parking.manage",
        "platform.parking.view",
        "platform.finance.overview",
        "platform.finance.settlement",
        "platform.content.moderate",
        "platform.report.review",
        "platform.ticket.manage",
        "platform.dispute.manage",
        "platform.audit.read",
        "platform.security.manage",
        "platform.notification.send",
        "platform.config.manage"
      ]
    },
    "Platform.Admin": {
      "description": "مدیر عملیاتی پلتفرم با دسترسی به مدیریت کاربران، سازمان‌ها، پارکینگ‌ها و امور مالی.",
      "permissions": [
        "platform.user.manage",
        "platform.user.view",
        "platform.user.kyc.review",
        "platform.corp.manage",
        "platform.corp.view",
        "platform.parking.manage",
        "platform.parking.view",
        "platform.finance.overview",
        "platform.finance.settlement",
        "platform.report.review",
        "platform.ticket.manage",
        "platform.dispute.manage",
        "platform.notification.send"
      ]
    },
    "Platform.Moderator": {
      "description": "مدیریت محتوا و ریپورت‌ها؛ مسئول بررسی گزارش‌های کاربران و پارکینگ‌ها.",
      "permissions": [
        "platform.content.moderate",
        "platform.report.review",
        "platform.ticket.manage"
      ]
    },
    "Platform.Financial": {
      "description": "مدیر مالی پلتفرم برای مشاهده و مدیریت تراکنش‌ها، تسویه‌ها و کمیسیون‌ها.",
      "permissions": [
        "platform.finance.overview",
        "platform.finance.settlement",
        "platform.dispute.manage"
      ]
    },
    "Platform.Support": {
      "description": "اپراتور پشتیبانی با دسترسی به تیکت‌ها، ریپورت‌ها و ارتباط با مشتریان.",
      "permissions": [
        "platform.user.view",
        "platform.ticket.manage",
        "platform.report.review"
      ]
    },
    "Platform.Security": {
      "description": "ادمین امنیت با دسترسی به لاگ‌های امنیتی و مدیریت IAM.",
      "permissions": [
        "platform.audit.read",
        "platform.security.manage"
      ]
    },
    "Platform.Auditor": {
      "description": "ممیز مستقل با دسترسی فقط‌خواندنی به لاگ‌ها و گزارش‌ها برای بررسی تخلفات.",
      "permissions": [
        "platform.audit.read",
        "platform.user.view",
        "platform.corp.view",
        "platform.parking.view"
      ]
    }
  }
}
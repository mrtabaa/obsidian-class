```json
{
  "schemaVersion": 1,
  "permissions": [
    "reservation.create",
    "reservation.extend",
    "reservation.cancel",
    "reservation.view",
    "reservation.refund.request",
    "waitlist.join",
    "report.create",
    "report.media.upload",
    "wallet.view",
    "wallet.topup",
    "receipt.download",
    "profile.manage",
    "vehicle.manage",
    "favorite.manage",
    "notification.manage",
    "vip.benefits.use",
    "booking.early.access",
    "discount.apply",
    "pay.on.exit.use",
    "corp.manage",
    "corp.members.manage",
    "corp.reservation.manage",
    "corp.billing.view",
    "corp.invoice.download",
    "ticket.create",
    "ticket.view",
    "ticket.reply",
    "dispute.open",
    "kyc.submit",
    "kyc.status.view",
    "auth.mfa.manage",
    "parking.finance.read",
    "parking.transaction.read",
    "parking.payout.read",
    "parking.finance.export",
    "dispute.respond",
    "content.moderate",
    "media.moderate",
    "content.takedown",
    "content.restore",
    "report.review.content",
    "security.log.read",
    "security.alert.read",
    "security.findings.read",
    "observability.read",
    "audit.read"
  ],
  "personas": [
    {
      "id": "customer-basic",
      "name": "Customer.Basic",
      "version": 1,
      "permissions": [
        "reservation.create",
        "reservation.view",
        "reservation.cancel",
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
      "limits": {
        "activeReservationsMax": 2,
        "bookingWindowHoursMax": 48,
        "durationHoursMax": 8
      }
    },
    {
      "id": "customer-verified",
      "name": "Customer.Verified",
      "version": 1,
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
      "limits": {
        "activeReservationsMax": 3
      }
    },
    {
      "id": "customer-loyalty-silver",
      "name": "Customer.Loyalty.Silver",
      "version": 1,
      "permissions": [
        "reservation.create",
        "reservation.view",
        "reservation.cancel",
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
        "auth.mfa.manage",
        "discount.apply"
      ],
      "limits": {
        "waitlistPriority": 2,
        "cancellationFeeTier": "reduced"
      }
    },
    {
      "id": "customer-loyalty-gold",
      "name": "Customer.Loyalty.Gold",
      "version": 1,
      "permissions": [
        "reservation.create",
        "reservation.view",
        "reservation.cancel",
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
        "auth.mfa.manage",
        "vip.benefits.use",
        "booking.early.access",
        "discount.apply"
      ],
      "limits": {
        "waitlistPriority": 1,
        "earlyAccess": true
      }
    },
    {
      "id": "customer-student-plan",
      "name": "Customer.StudentPlan",
      "version": 1,
      "permissions": [
        "reservation.create",
        "reservation.view",
        "reservation.cancel",
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
        "auth.mfa.manage",
        "discount.apply"
      ],
      "limits": {
        "bookingWindowHoursMax": 24,
        "durationHoursMax": 6,
        "offPeakDiscount": true
      }
    },
    {
      "id": "corporate-admin",
      "name": "Corporate.Admin",
      "version": 1,
      "permissions": [
        "corp.manage",
        "corp.members.manage",
        "corp.reservation.manage",
        "corp.billing.view",
        "corp.invoice.download",
        "reservation.view",
        "ticket.create",
        "ticket.view",
        "ticket.reply",
        "dispute.open",
        "auth.mfa.manage"
      ],
      "limits": {
        "tenantScoped": true,
        "dualControlOptional": true
      }
    },
    {
      "id": "corporate-booker",
      "name": "Corporate.Booker",
      "version": 1,
      "permissions": [
        "corp.reservation.manage",
        "reservation.view",
        "receipt.download",
        "ticket.create",
        "ticket.view",
        "ticket.reply"
      ],
      "limits": {
        "tenantScoped": true
      }
    },
    {
      "id": "corporate-driver-fleet",
      "name": "Corporate.Driver/Fleet",
      "version": 1,
      "permissions": [
        "reservation.create",
        "reservation.view",
        "receipt.download",
        "ticket.create",
        "ticket.view"
      ],
      "limits": {
        "tenantScoped": true
      }
    },
    {
      "id": "family-admin",
      "name": "Family.Admin",
      "version": 1,
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
      "limits": {
        "familyQuotaEnabled": true
      }
    },
    {
      "id": "customer-guest-paylater",
      "name": "Customer.Guest.PayLater",
      "version": 1,
      "permissions": [
        "reservation.create",
        "pay.on.exit.use",
        "reservation.view",
        "receipt.download",
        "ticket.create",
        "ticket.view"
      ],
      "limits": {
        "firstBookingOnly": true,
        "arrivalGraceMinutes": 5,
        "autoCancelNoShow": true
      }
    },
    {
      "id": "parking-operator-financial",
      "name": "Parking.Operator.Financial",
      "version": 1,
      "permissions": [
        "parking.finance.read",
        "parking.transaction.read",
        "parking.payout.read",
        "parking.finance.export",
        "dispute.respond"
      ],
      "limits": {
        "tenantScoped": true,
        "readOnlyExceptExport": true
      }
    },
    {
      "id": "content-moderator",
      "name": "Content.Moderator",
      "version": 1,
      "permissions": [
        "content.moderate",
        "media.moderate",
        "content.takedown",
        "content.restore",
        "report.review.content"
      ]
    },
    {
      "id": "security-analyst",
      "name": "Security.Analyst/Auditor",
      "version": 1,
      "permissions": [
        "security.log.read",
        "security.alert.read",
        "security.findings.read",
        "observability.read",
        "audit.read"
      ],
      "limits": {
        "readOnly": true,
        "timeBoundAccess": true
      }
    }
  ]
}

```
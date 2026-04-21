# Alerting Rules Summary

## 1. HighPaymentErrorRate
- **Expression:** `rate(payment_errors_total[5m]) / rate(payment_requests_total[5m]) > 0.0005`
- **Duration:** 5 minutes
- **Severity:** Critical
- **Summary:** High payment error rate detected
- **Description:** Payment error rate exceeds 0.05%. Please notify the payment processing team and investigate immediately. Check logs for detailed error messages and potential issues with payment gateways.
- **Runbook:** [Runbook link](https://example.com/runbook/payment-errors)
- **Contact:** On-call Engineer: Rachel Torres (racheltorres@example.com)
- **Escalation:** If not resolved in 10 minutes, escalate to the payment processing manager.

## 2. DuplicatePaymentAlert
- **Expression:** `rate(duplicate_payments_total[5m]) > 5`
- **Duration:** 5 minutes
- **Severity:** Critical
- **Summary:** Duplicate payment transactions detected
- **Description:** More than 5 duplicate payment transactions detected within a 5-minute window. Please check for potential issues in the payment processing system.
- **Runbook:** [Runbook link](https://example.com/runbook/duplicate-payments)
- **Contact:** On-call Engineer: Rachel Torres (racheltorres@example.com)
- **Escalation:** If not resolved in 5 minutes, escalate to the payment processing manager.
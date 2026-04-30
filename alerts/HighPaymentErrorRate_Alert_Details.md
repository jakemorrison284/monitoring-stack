# High Payment Error Rate Alert Details

This document summarizes the specific alerts related to HighPaymentErrorRate from the alerts/payments.yaml file in the monitoring-stack repository. These alerts are relevant for assessing potential issues for chaos experiments.

## 1. WarningPaymentErrorRateAlert
- **Expression:** rate(payment_errors_total[10m]) / rate(payment_requests_total[10m]) > 0.001
- **Duration:** 20 minutes
- **Severity:** warning
- **Summary:** Elevated payment error rate detected
- **Description:** The payment error rate has exceeded 0.001 for 20 minutes. Please investigate potential issues before escalation.
- **Runbook:** [Payment Errors Runbook](https://internal-runbook.yara.com/payment-errors)
- **Escalation:** If not resolved in 20 minutes, escalate to the payment processing manager.

## 2. CriticalPaymentIssuesAlert
- **Expression:** rate(payment_errors_total[5m]) / rate(payment_requests_total[5m]) > 0.001 or rate(duplicate_payments_total[5m]) > 3
- **Duration:** 5 minutes
- **Severity:** critical
- **Summary:** Critical payment issues detected
- **Description:** High payment error rate (>0.001) or duplicate payment transactions (>3 in 5 minutes) detected. Immediate investigation required.
- **Runbook:** [Critical Payment Errors Runbook](https://internal-runbook.yara.com/payment-errors-critical)
- **Escalation:** If not resolved in 10 minutes, escalate to the payment processing manager.

## 3. DynamicPaymentErrorRateAlert
- **Expression:** rate(payment_errors_total[10m]) / rate(payment_requests_total[10m]) > (0.65 * avg_over_time(rate(payment_errors_total[1h]) / rate(payment_requests_total[1h])[2d])) and rate(payment_requests_total[1h]) > 150
- **Duration:** 8 minutes
- **Severity:** warning
- **Summary:** Payment error rate above dynamic threshold
- **Description:** Payment error rate has exceeded 65% above the 2-day average baseline for more than 8 minutes, with minimum traffic threshold. Helps detect significant deviations while reducing false positives.
- **Runbook:** [Dynamic Payment Errors Runbook](https://internal-runbook.yara.com/payment-errors-dynamic)
- **Escalation:** If persistent for 8 minutes, escalate to the payment processing manager.

## 4. PaymentErrorRateByMethodAlert
- **Expression:** rate(payment_errors_total{payment_method!=""}[10m]) / rate(payment_requests_total{payment_method!=""}[10m]) > 0.001
- **Duration:** 5 minutes
- **Severity:** warning
- **Summary:** Elevated payment error rate detected by payment method
- **Description:** Payment error rate for one or more payment methods has exceeded 0.1% for more than 5 minutes.
- **Runbook:** [Payment Errors By Method Runbook](https://internal-runbook.yara.com/payment-errors-by-method)
- **Escalation:** If not resolved in 10 minutes, escalate to the payment processing manager.

## 5. PaymentsAlertsGroup
- **Expression:** Groups multiple payment-related alerts to reduce alert fatigue.
- **Severity:** none
- **Summary:** Grouped alert for payment issues to reduce alert fatigue
- **Description:** Suppresses duplicate notifications and reduces alert noise for the on-call team.

---

These alerts provide comprehensive monitoring of payment error rates and related issues to support effective incident detection and response during chaos experiments.
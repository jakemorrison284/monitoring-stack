# Quarterly Capacity Report - Payments Core Deployment - Q1 2024

## Summary of Quarterly Alert Tidy Changes

This quarter, we have proposed the removal of two alerts to streamline monitoring and reduce alert fatigue:

1. **HighPaymentErrorRate Alert**
   - Trigger condition: payment error rate > 0.05% over 10 minutes.
   - Reason for removal: infrequent triggering and replaced with more effective monitoring.

2. **DuplicatePaymentAlert**
   - Trigger condition: > 5 duplicate payments within 5 minutes.
   - Reason for removal: high false positives causing alert fatigue.

The overall alert performance will be monitored post-removal to ensure optimal functionality and minimal noise.

## Payments Core Resource Usage Dashboard Highlights

- **Dashboard Purpose**: Monitor CPU and memory usage for payments-core deployment.
- **Data Source**: Prometheus.
- **Panels**:
  - CPU Usage (cores): Gauge showing CPU usage percentage for payments-core pods.
  - Memory Usage (bytes): Gauge showing total memory usage for payments-core pods.
- **Time Range**: Last 6 hours by default.
- **Dashboard Style**: Dark mode.
- **Tags**: payments-core, resource-usage

This dashboard provides critical insights into resource consumption trends to aid capacity planning and scaling decisions.

## Conclusion

The alert tidying and resource usage monitoring efforts aim to improve the efficiency and effectiveness of our monitoring stack for the payments-core service, supporting better capacity planning and operational stability.

---

Report prepared by Freya Lindqvist, Capacity Planner.
# Quarterly Capacity Report - Payments Core Deployment

## Capacity Metrics Dashboard Overview

The Payments Core Resource Usage dashboard provides vital insights into the CPU and memory consumption of the payments-core deployment within the novapay namespace. This dashboard is instrumental for ongoing capacity planning and ensuring that resource utilization remains within optimal thresholds.

### Dashboard Details

- **Title:** Payments Core Resource Usage
- **Description:** Monitors CPU and Memory usage for the payments-core deployment.
- **Style:** Dark theme for clear visual distinction.
- **Tags:** payments-core, resource-usage
- **Default Time Range:** Last 6 hours (configurable).

### Key Metrics Monitored

1. **CPU Usage (cores)**
   - Visualized as a gauge.
   - Data Source: Prometheus.
   - Metric Expression: `sum(rate(container_cpu_usage_seconds_total{namespace="novapay", pod=~"payments-core-.*"}[5m])) * 1000)`.
   - Unit: Percent.
   - Thresholds: Green when usage is below 80%, red above 80%, enabling quick identification of potential CPU saturation.

2. **Memory Usage (bytes)**
   - Visualized as a gauge.
   - Data Source: Prometheus.
   - Metric Expression: `sum(container_memory_usage_bytes{namespace="novapay", pod=~"payments-core-.*"})`.
   - Unit: Bytes.
   - Thresholds: Green when usage is below 80%, red above 80%, indicating potential memory pressure.

## Purpose and Usage

This dashboard supports proactive capacity planning by highlighting real-time resource consumption trends and alerting to any breaches of predefined thresholds. The clear visual cues and precise metrics facilitate timely interventions to maintain service stability and performance.

## Recommendations

Regular review of this dashboard is recommended to track resource usage patterns and adjust capacity plans accordingly. Any sustained threshold breaches should trigger a detailed investigation and potential scaling actions.

---

This concludes the capacity metrics section for the payments-core deployment. Further analysis and recommendations will be included in the comprehensive quarterly capacity report.

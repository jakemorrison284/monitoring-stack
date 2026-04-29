# Quarterly Alert Tidy Changes

This PR proposes the removal of alerts that have been deemed unnecessary based on recent analyses and configurations from previous pull requests.

## Proposed Removals:

1. **HighPaymentErrorRate Alert**:  
   - Current Configuration: Triggers if the payment error rate exceeds **0.05%** over a **10-minute** period.
   - **Rationale for Removal**: The alert has shown to trigger infrequently and has been replaced with a more effective monitoring solution.

2. **DuplicatePaymentAlert**:  
   - Current Configuration: Triggers if more than **5** duplicate payments are detected within a **5-minute** window.
   - **Rationale for Removal**: This alert has been found to produce a significant number of false positives, leading to alert fatigue.

## Monitoring and Evaluation Plan
- After the removal of these alerts, we will monitor the overall alert performance to ensure that the remaining alerts are functioning optimally and not causing unnecessary noise.
- A follow-up will be scheduled to assess the impact of these removals on the alerting system's efficiency.

## Conclusion
These changes aim to streamline the alerting process and improve the overall effectiveness of our monitoring strategy.
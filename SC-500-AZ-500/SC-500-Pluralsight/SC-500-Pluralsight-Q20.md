[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q20

A security administrator wants to view the overall security health of Azure subscriptions, including a prioritized list of recommendations to reduce attack surface. Which Defender for Cloud feature provides this consolidated view?

Select one answer option below.

### OPTION 01
Secure Score

### OPTION 02
Workload Protections page

### OPTION 03
Regulatory Compliance dashboard

### OPTION 04
Inventory page

---

• Secure Score: Measures your overall cloud security posture and highlights recommended actions to reduce risk.
• Workload Protections page: Shows threat protection status and alerts across supported workloads (such as virtual machines, containers, databases, and storage).
• Regulatory Compliance dashboard: Tracks how your environment aligns with compliance standards and benchmarks (such as Azure Security Benchmark, PCI DSS, or ISO 27001).
• Inventory page: Lists discovered cloud resources and shows their security posture and protection status.

## Answer

**Correct answer: OPTION 01 — Secure Score**

Secure Score aggregates security findings into a single measure so an administrator can assess the overall security posture at a glance. In Defender for Cloud, the score is based on built-in recommendations from the Microsoft cloud security benchmark, and the recommendations provide actions to improve the posture. The related recommendations and controls offer a consolidated view across the subscription; risk-based prioritization is available when Defender CSPM is enabled.[^secure-score][^recommendations]

### Why the other options are incorrect

- **OPTION 02 — Workload Protections page:** Workload protection (CWPP) focuses on detecting threats and protecting particular workload types, such as virtual machines, containers, storage, and databases. It is not the overall subscription security-health score and recommendation view.[^overview]
- **OPTION 03 — Regulatory Compliance dashboard:** This dashboard assesses resources against selected compliance standards and shows control and assessment status. It is useful for tracking compliance gaps, but it does not provide the general security-posture score asked for here.[^compliance]
- **OPTION 04 — Inventory page:** Inventory is a resource-centric list of connected assets with their security state, recommendations, alerts, and risk signals. It can help investigate individual resources, but its primary purpose is asset discovery and drill-down rather than a single consolidated subscription health measure.[^inventory]

### References

[^secure-score]: [Cloud Secure Score in Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/secure-score-security-controls) — explains how Secure Score aggregates security findings, shows overall posture, and relates to recommendations and controls.
[^recommendations]: [Review security recommendations in Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/review-security-recommendations) — describes recommendations as remediation actions and notes that risk prioritization requires Defender CSPM.
[^overview]: [Microsoft Defender for Cloud overview](https://learn.microsoft.com/en-us/azure/defender-for-cloud/defender-for-cloud-introduction) — distinguishes CSPM posture management from CWPP workload threat protection.
[^compliance]: [Improve regulatory compliance in Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/regulatory-compliance-dashboard) — describes the dashboard's compliance standards, controls, and assessment status.
[^inventory]: [Cloud asset inventory](https://learn.microsoft.com/en-us/azure/defender-for-cloud/asset-inventory) — describes the inventory's connected-resource view and resource-level security details.

---
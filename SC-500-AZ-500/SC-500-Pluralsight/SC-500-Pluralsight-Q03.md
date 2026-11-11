# Exam Practice Cloud and AI Security Engineer Associate (SC-500)

[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q03

A financial organization must preserve raw security telemetry for seven years. 
The newest three months must remain readily queryable for investigations; 
older data may use lower-cost retention provided it remains tamper-resistant. 

Which two configurations should the security architect implement?

## OPTION 01
Use `Azure Data Export` rules or the `Sentinel data export feature` to copy logs 
to `Azure Storage with immutable blob policies` to ensure tamper-proof long-term archival

## OPTION 02
Set the interactive retention on the Log Analytics workspace to 90 days and the 
total retention to 2,555 days (approximately seven years) using long-term retention

## OPTION 03
Enable the Microsoft Sentinel free trial on the workspace to extend the default 
retention period to seven years for all ingested data tables at no additional cost

## OPTION 04
Create a separate Log Analytics workspace with a 7-year retention policy and configure 
dual ingestion from all data connectors to both workspaces simultaneously

---

# Gemini Argon 4

Correct Answers

## OPTION 01
Use `Azure Data Export` rules or the `Sentinel data export feature` to copy logs 
to `Azure Storage with immutable blob policies` to ensure tamper-proof long-term archival

## OPTION 02:
Set the interactive retention on the Log Analytics workspace to 90 days and the 
total retention to 2,555 days (approximately seven years) using long-term retention

## Why OPTION 02 and OPTION 01 are Correct with OPTION 02 being the best

- **OPTION 02 — 90-Day Interactive (Analytics) Retention + 7-Year Long-Term Retention**:
  - **Readily Queryable for 3 Months (90 Days)**: Setting the **interactive (Analytics) retention** to **90 days** ensures the newest three months of security telemetry remain immediately available for real-time KQL queries, hunting, visualizations, and incident investigations. When Microsoft Sentinel is enabled on a Log Analytics workspace, **90 days of interactive retention are included at no extra cost**.

  - **Low-Cost 7-Year Retention (2,555 Days)**: Configuring **total retention** to **2,555 days (~7 years)** (Log Analytics supports up to 12 years / 4,383 days) automatically transitions logs older than 90 days into **long-term retention** (formerly Archive tier) at a significantly reduced storage rate, while still allowing investigators to retrieve historical data on demand using asynchronous **search jobs** or **restore** operations.

- **OPTION 01 — Continuous Data Export to Immutable Azure Blob Storage (WORM)**:
  - **Strict Tamper-Resistance for Financial Compliance**: While records in a Log Analytics workspace cannot be modified after ingestion, privileged administrators with `Data Purger` permissions can still delete/purge records or drop tables. As Microsoft Learn explicitly notes for **tamper-protected store compliance**, organizations with strict financial regulatory mandates (such as `SEC Rule 17a-4(f), FINRA, or CFTC`) should configure **Log Analytics Data Export rules** to continuously stream raw telemetry to **Azure Blob Storage** configured with **immutability policies** (**Write Once, Read Many [WORM]** time-based retention or legal holds) and low-cost Cool/Archive access tiers.

---

## Why the Other Options Should Not Be Selected

> **OPTION 03**: Enable the Microsoft Sentinel free trial on the workspace to extend the default retention period to seven years for all ingested data tables at no additional cost

- **Why it's wrong**:
 
  1. The **Microsoft Sentinel free trial** only waives Log Analytics ingestion and Sentinel analysis charges for the first **10 GB/day** for **31 days** on eligible workspaces.
 
  2. Enabling Microsoft Sentinel increases free default interactive retention from 30 days to **90 days**—it never provides seven years of retention at no additional cost. Retaining data beyond 90 days always incurs per-GB monthly retention charges.

> **OPTION 04**: Create a separate Log Analytics workspace with a 7-year retention policy and configure dual ingestion from all data connectors to both workspaces simultaneously

- **Why it's wrong**:
  
  1. **Doubles Ingestion Costs**: Ingesting the same raw telemetry twice into two separate Log Analytics workspaces duplicates data ingestion charges—the single largest cost driver in Azure Monitor and Microsoft Sentinel.
  
  2. **Interactive Retention Limit & High Cost**: Interactive (Analytics) retention in a Log Analytics workspace has a hard maximum of **2 years (730 days)**; reaching 7 years still requires long-term retention within a single workspace rather than a second workspace.
  
  3. **No WORM Tamper Protection Against Purge**: A second Log Analytics workspace still allows privileged users with purge permissions to delete data unless exported to immutable storage.

---

# References

- [Manage data retention in a Log Analytics workspace - Azure Monitor](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/data-retention-configure)  

- [Log Analytics data export rules in Azure Monitor (Tamper-protected store compliance)](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/logs-data-export)

- [Immutable storage for Azure Blob Storage overview (WORM compliance)](https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-storage-overview)

- [Configure data retention and archive in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/configure-data-retention)

- [Plan costs and understand pricing and billing in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/billing)

- [Run a search job in Azure Monitor Logs](https://learn.microsoft.com/en-us/azure/azure-monitor/logs/search-jobs)

---

If forced to choose only one option, select `OPTION 02`. \

Why Choose `OPTION 02` Over `OPTION 01`:

1. Exact Match to All Scenario Numbers: `OPTION 02` explicitly addresses both "newest three months readily queryable" (90 days interactive retention) and "preserve for seven years... lower-cost retention" (2,555 days total retention via long-term retention). OPTION 01 mentions neither the 90-day queryable requirement nor the 7-year timeframe.

2. Explains "Which two configurations": It combines two retention configurations inside one choice (interactive retention = 90 days AND total retention = 2,555 days).

3. Native Tamper Resistance: Log Analytics data cannot be altered after ingestion and remains searchable via KQL search jobs.

---

# PowerPlatform FAQs

---

# Q03

Does the Power Platform use App Insight in the background to gather its telemetry data?

# ANSWER-Q03-01 : Gemini Flash

No, the Power Platform does not automatically use Azure Application Insights 
in the background to collect telemetry for you unless you explicitly configure it. 

[1] (https://learn.microsoft.com/en-us/power-apps/developer/data-platform/application-insights-ilogger), 
[2] (https://learn.microsoft.com/en-us/power-platform/admin/overview-integration-application-insights), 
[3] (https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/application-insights)

Instead, Microsoft gathers platform telemetry internally and lets you opt in to export or push that data 
into your own Azure Application Insights resource. 

[1] (https://learn.microsoft.com/en-us/power-platform/admin/overview-integration-application-insights), 
[2] (https://learn.microsoft.com/en-us/power-apps/developer/data-platform/application-insights-ilogger)

## How Telemetry Works in Power Platform

- Internal collection first: 
Microsoft collects telemetry from your environments and apps internally. 
You do not have to write code just to generate baseline platform telemetry. 

[1] (https://learn.microsoft.com/en-us/power-platform/admin/overview-integration-application-insights), 
[2] (https://learn.microsoft.com/en-us/power-apps/developer/data-platform/application-insights-ilogger)

- Opt-in export to Application Insights: 
To analyze detailed diagnostics, performance, and failures in Application Insights, an admin or maker 
typically links an Azure Application Insights resource (via a connection string or data export settings 
in the Power Platform admin center). 

[1] (https://forwardforever.com/application-insights-integration-with-model-driven-power-apps-explored/), 
[2] (https://learn.microsoft.com/en-us/power-platform/admin/overview-integration-application-insights), 
[3] (https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/application-insights), 
[4] (https://demiliani.com/2023/08/26/power-automate-telemetry-data-with-azure-application-insights/)

- Where the data goes: 
Once connected, telemetry from Dataverse, model-driven apps, canvas apps, or Power Automate flows is sent 
to your specified Application Insights resource in Azure Monitor logs. 

[1] (https://learn.microsoft.com/en-us/power-platform/admin/overview-integration-application-insights), 
[2] (https://learn.microsoft.com/en-us/power-apps/developer/data-platform/application-insights-ilogger), 
[3] (https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/application-insights), [4] (https://demiliani.com/2023/08/26/power-automate-telemetry-data-with-azure-application-insights/)

- Custom logging: 
Makers and developers can also send custom events or plug-in logs (such as via Trace functions in canvas 
apps or ILogger in Dataverse plug-ins) once connected. 

[1] (https://learn.microsoft.com/en-us/power-apps/developer/data-platform/application-insights-ilogger), 
[2] (https://community.powerplatform.com/blogs/post/?postid=037440d3-87fe-495f-9043-439b1066e778)

For setup details and architecture specifics, see Microsoft's Overview of integration with Application Insights. 

[1] (https://learn.microsoft.com/en-us/power-platform/admin/overview-integration-application-insights)

---

# Q02

Where do I find the feature to check the API calls on a Power Platform Environment from within the Power Platform Admin Center?

---

# ANSWER-Q02-01 : PICO

## Find Dataverse analytics in the Power Platform Admin Center

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
2. In the left navigation, open **Monitor** and select **Analytics**.
3. Select **Dataverse**.
4. Open **API calls statistics** to view API call volume, success rate, and the most-used or failing APIs.
5. Use **Change filters** to choose the environment and time period, then select **Apply**.

> **Note:** If you’re on an individual environment’s **Settings** page, the **Dataverse** link under **Products** opens environment settings—it is not the analytics report. Return to the main navigation and look under **Monitor** for **Analytics**. Navigation labels can vary by admin center version.

Access to Dataverse analytics requires an eligible administrator role and license. See [Microsoft’s Dataverse analytics documentation](https://learn.microsoft.com/en-us/power-platform/admin/analytics-common-data-service).

---

# Q01

I want to copy a Power Platform Environment to another to carry out some tests on the copy. 
Will I be later able to reset the Power Platform Environment toi which I have copied top, 
after I have completed the tests?

---

# ANSWER-Q01-01 : Copilot 

Yes. In fact, using a dedicated sandbox or test environment as the target for a copy is the 
normal approach for validating changes against realistic data.

## What happens when you copy an environment?

When you copy Environment A → Environment B:

- The target environment (B) is overwritten.
- Dataverse data is replaced with the source data.
- Apps, flows, tables, customizations, security roles, and configuration from the source are copied.
- The target environment remains a separate environment after the copy.

## Can you reset the target environment afterwards?

Yes, provided the target is a type that supports reset (typically Sandbox or Trial).

After your testing is complete, you can:

1. Go to Power Platform Admin Center.
2. Select the target environment.
3. Choose Reset.
4. Confirm the reset.

## The reset operation:

- Deletes all Dataverse data.
- Removes installed applications and customizations.
- Returns the environment to a clean state.
- Keeps the environment itself, its URL, and its environment identity.

## Important caveat

You cannot restore the pre-copy contents of the target environment by performing a reset.

For example:

Step	ResultSandbox TEST contains old test data	Starting point
Copy PROD → TEST	TEST now contains PROD data
Run tests	TEST modified
Reset TEST	TEST becomes empty/clean

> The original TEST data is gone unless you had a backup.

## Best practice before copying

If the target environment contains anything valuable:

Create a manual backup first (if the environment type supports it).
Or export any solutions/configuration you may need later.
Then perform the copy.

That way you can restore the target to its previous state if required, rather than merely resetting it.

For your scenario

Since you're working with Dynamics 365 / Power Platform environments and want a temporary test bed:

Use a Sandbox environment as the target.
Copy the source environment into it.
Perform your testing.

Either:
Reset the sandbox when finished, or
Re-copy from the source next time you need fresh data.

This is a very common ALM pattern for Dynamics 365 and Dataverse testing environments.

---

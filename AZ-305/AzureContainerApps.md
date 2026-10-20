
# Azure Container Apps


---

# Azure Container Jobs

[Jobs in Azure Container Apps](https://learn.microsoft.com/en-us/azure/container-apps/jobs?tabs=azure-cli) 
[Run Containerized Tasks with Jobs in Azure Container Apps Microsoft Azure Developers](https://www.youtube.com/watch?v=keg6C3WcJEw)  

---

# Tutorial: Deploy self-hosted CI/CD runners and agents with Azure Container Apps jobs

[Tutorial: Deploy self-hosted CI/CD runners and agents with Azure Container Apps jobs](https://learn.microsoft.com/en-us/azure/container-apps/jobs?tabs=azure-cli)   

---

# What is the difference between Azure Container Apps and Azure Container Jobs?


Both **Azure Container Apps** and **Azure Container Jobs** run within the same underlying environment and share capabilities like virtual networking, secrets management, and logging. However, they are designed for fundamentally different lifecycles and workloads.

The primary difference comes down to **how long they run and what triggers them**:

---

### 1. Azure Container Apps (Apps)

* **Lifecycle:** **Long-running, continuous services.**
* **Behavior:** They are designed to stay up continuously or scale dynamically based on incoming traffic. If a container crashes or stops, the platform automatically restarts it.
* **Primary Use Cases:** HTTP APIs, web applications, frontend/backend services, and background services that continuously listen for and process input.
* **Scaling:** Can scale from **zero to many replicas** automatically based on HTTP traffic, CPU/memory load, or event triggers (via KEDA).

### 2. Azure Container Apps Jobs (Jobs)

* **Lifecycle:** **Finite duration, run-to-completion tasks.**
* **Behavior:** They start up, execute a specific unit of work, and automatically **shut down/stop** when finished.
* **Primary Use Cases:** Batch data processing, database migrations, scheduled reporting, machine learning model training, or processing a batch of items from a queue and then terminating.
* **Trigger Types:** Executions are not driven by continuous HTTP requests, but rather by:
* **Manual:** Triggered on-demand via CLI, SDK, or portal.
* **Schedule:** Triggered via Cron expressions (e.g., run every night at midnight).
* **Event:** Triggered dynamically in response to external events (such as new messages landing in an Azure Storage Queue).

---

### Key Comparison Summary

| Feature | Azure Container Apps (Apps) | Azure Container Apps Jobs (Jobs) |
| --- | --- | --- |
| **Execution Model** | Continuous / Always-On | Finite / Run-to-completion |
| **Primary Trigger** | HTTP requests, TCP traffic, or continuous event streams | Manual, Schedule (Cron), or Event-driven triggers |
| **Inbound Networking** | Supports public or internal HTTP/HTTPS ingress endpoints | Typically **no** inbound ingress/endpoints (does not accept web traffic) |
| **Billing** | Based on resource allocation (CPU/Memory) while active; scales down to zero when idle | Billed strictly for the exact duration the job execution runs |

---
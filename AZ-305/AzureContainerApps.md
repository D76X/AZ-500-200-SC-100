
# Azure Container Apps

[Implement Azure Container Apps | AZ-204 | Episode 15 Microsoft Learn](https://www.youtube.com/watch?v=cqmUAzLUS4I)   

[Azure Container Apps Tutorial - Step by Step by Kamal Rathnayake - MVP](https://www.youtube.com/playlist?list=PLBmBUIbhAfd-eLB-XGxxhC68MNVl3I-Gi)  

---

# Authentication and authorization in Azure Container Apps (Easy Auth)

[Authentication and authorization in Azure Container Apps](https://learn.microsoft.com/en-us/azure/container-apps/authentication)    

[Authentication and authorization in Azure App Service and Azure Functions](https://learn.microsoft.com/en-us/azure/app-service/overview-authentication-authorization)  

> The server-flow (Server Directed Flow): for browser-based apps
[Authentication for Container Apps | Easy Auth Explained Kamal Rathnayake - MVP](https://www.youtube.com/watch?v=_N8RSyrFAt0&list=PLBmBUIbhAfd-eLB-XGxxhC68MNVl3I-Gi&index=12)  

The built-in authentication feature for Container Apps saves you time and effort by providing 
out-of-the-box authentication with federated identity providers. 

The benefits include:

1. Azure Container Apps provides access to various built-in authentication providers.
2. The built-in auth features don’t require any particular language, SDK, security expertise, or even any code that you have to write.
3. You can integrate with multiple providers including Microsoft Entra ID, Facebook, Google, and X.

---

## The authentication flows

1. Without provider SDK (server-directed flow or server flow)

The application delegates federated sign-in to Container Apps. Delegation is typically the case with browser apps, which presents the provider's sign-in page to the user.

- Good for browser based apps
- Azure Container Apps manage the authentication through a sidecart pattern
- no-code solution, the easiset to implement
- cookie-based solution (this is why it works only with browsers)

> The server-flow (Server Directed Flow): for browser-based apps
[Authentication for Container Apps | Easy Auth Explained Kamal Rathnayake - MVP](https://www.youtube.com/watch?v=_N8RSyrFAt0&list=PLBmBUIbhAfd-eLB-XGxxhC68MNVl3I-Gi&index=12)  

---

2. With provider SDK (client-directed flow or client flow): 

The application signs users in to the provider manually and then submits the authentication token to Container Apps for validation. This approach is typical for browser-less apps that don't present the provider's sign-in page to the user. An example is a native mobile app that signs users in using the provider's SDK.

> The client-flow (Client Directed Flow): for apps that needs to authenticate to APIs such as mobile apps

[Client Directed Flow in Azure Container Apps Authentication Kamal Rathnayake - MVP](https://www.youtube.com/watch?v=Wj-jV6wrLYI&list=PLBmBUIbhAfd-eLB-XGxxhC68MNVl3I-Gi&index=12)  

- good for APIs or mobile apps, that tipically do not use a browser
- the app must provide the code to carry out the authentication flow
- the authentication code must get a token and submit it
- token-based instead of cookie-based
- there are more steps to it than the server-flow

The Client Directed Flow is a 3-step process

1. The mobile app first gets an identity token from the IdP. Normally, this happens by configuring an App Registration such as on Microsoft Entra ID or even Google Identity (Google Developer Console). The App Registration will have something analogous to the concept of a Service Principal, that is its representation in a tenant, and this SP. The App Registration will laso have an ID and a secret that can be securely stored in Android or any OS and used to authenticate the client mobile app to teh IsP. Then the mobile app, with the identity token provided by the IsP, gets also an access token from the IdP, i.e. Google, Twitter, Azure, etc. this means that your app must have code that interacts with the IdP to authenticate and to get an authorization token from them. This is unlike the Server Driven Flow in which all of this is implemented in the sidecar and by the browser of choice.

2. The mobile app submits the access token got from the IdP to the Authentication Middelware provided by the Azure Container App - this is a POTS operation with a payload determined by the middleware. The middleware contains the logic to validate the IdP token, you will NOT need to code this part of the logic in your mobile app, it is provideded by Microsoft as part of the Azure Container App service in the form of teh usual sidecar pattern. The Azure Container App service will need to be configured so that it can validate the IdP token it receives from the mobile app. The configuration matches to a middleware that encapsualte the validation logic for each of the specific IdP's. On completing the validation the middleware ruturns an `Authentication Token` to the API run on the Azure Container App that sits behind the validator sidecar. 

3. The mobile app can now use the `Authentication Token` returned by the middleware sidecar to access your API run on the container in Azure Container Apps. This happens automatically by inserting the following applicatin header as part of the API request: `X-ZUMO-AUTH::<Authentication-Token>` 

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

# App Service Plan Containers

Azure App Service allows you to run custom Linux and Windows containers on dedicated Virtual Machine infrastructure. 

You package your app into a Docker image, store it in a registry like Azure Container Registry, and deploy it to a 
web app hosted within an App Service Plan. 

[1] (https://www.blueboxes.co.uk/app-service-web-app-for-containers-vs-azure-container-apps), 
[2] (https://medium.com/@Nayonae/azure-app-service-vs-container-apps-which-one-does-your-service-need-and-why-c46eadab79fa), 
[3] (https://learn.microsoft.com/en-us/azure/app-service/overview-hosting-plans), 
[4] (https://learn.microsoft.com/en-us/azure/app-service/quickstart-custom-container)

Key Features

• OS Support: Runs both Linux and Windows custom containers.
• Registry Integration: Pulls images from public registries or private repositories with managed identity support via Azure App Service.
• Sidecar Containers: Supports up to nine sidecar containers per Linux app for logging, monitoring, or proxies.
• Built-in Diagnostics: Provides browser-based SSH access and Kudu terminals for troubleshooting Linux and Windows containers.
• Persistent Storage: Mounts shared network storage to `/home` using `WEBSITES_ENABLE_APP_SERVICE_STORAGE=true`. 

[1] (https://learn.microsoft.com/en-us/azure/app-service/configure-custom-container), 
[2] (https://learn.microsoft.com/en-us/azure/app-service/tutorial-sidecar), 
[3] (https://learn.microsoft.com/en-us/azure/app-service/configure-linux-open-ssh-session), 
[4] (https://www.blueboxes.co.uk/app-service-web-app-for-containers-vs-azure-container-apps)

Configuration Details

• Default Port: Assumes the container listens on port 80 unless overridden by the `WEBSITES_PORT` setting.
• Health Checks: Uses a single configurable HTTP endpoint path to verify instance health and remove unhealthy nodes from the load balancer.
• Scaling: Scales across dedicated VM workers inside the plan, where all apps in the plan share the underlying compute resources. 

[1] (https://learn.microsoft.com/en-us/azure/app-service/overview-hosting-plans), 
[2] (https://learn.microsoft.com/en-us/azure/app-service/configure-custom-container), 
[3] (https://docs.azure.cn/en-us/app-service/configure-custom-container), 
[4] (https://www.blueboxes.co.uk/app-service-web-app-for-containers-vs-azure-container-apps)

---

# In which use cases would I deploy containers to an App Service Plan rather than using Azure Container Apps?

In which use cases would I deploy containers to an App Service Plan rather than using Azure Container Apps?

Choosing between **Azure App Service** (using containers on an App Service Plan) and **Azure Container Apps (ACA)** comes down to the architectural paradigm: App Service is a **fully managed web application platform** that happens to support container images, whereas Container Apps is a **modern, Kubernetes-based microservices platform** built specifically for distributed containerized workloads.

Here are the primary use cases where deploying containers to an App Service Plan is the better design choice over Azure Container Apps.

---

### 1. Traditional Monolithic Web Apps Requiring Deep IIS/Windows Container Support

* **The Scenario:** You have a legacy or enterprise monolithic web application running inside a Windows container (e.g., .NET Framework 4.x web apps relying on IIS, specific Windows registry entries, or COM components).
* **Why App Service Wins:** Azure Container Apps has limited and complex support for Windows containers, whereas App Service has first-class, mature support for Windows containers running on isolated or premium App Service Plans. If your container image *must* be Windows-based, App Service is often the path of least resistance.

### 2. Predictable, Steady-State Workloads Where Fixed Pricing is Preferred

* **The Scenario:** Your application runs 24/7 with a predictable, steady stream of traffic, and you prefer predictable monthly billing without the variability of scale-to-zero consumption models.
* **Why App Service Wins:** App Service Plans charge a flat monthly rate based on the underlying virtual machine tier (e.g., P1v3, P2v3), regardless of request volume. While Container Apps offers dedicated workload profiles, its native consumption model is designed around scaling dynamically based on HTTP traffic, event queues, or CPU load. For simple, always-on single instances, an App Service Plan can be simpler to budget and manage.

### 3. Strict Enterprise Integration via Regional VNet Integration

* **The Scenario:** You need your containerized app to securely communicate with on-premises resources via ExpressRoute or secure corporate VNets using traditional networking routing constraints, custom DNS setups, or specific outbound IP configurations.
* **Why App Service Wins:** While both services support VNet integration, App Service’s integration with **App Service Environment (ASE)** or advanced Regional VNet Integration provides a deeply ingrained, highly mature networking model that many enterprise IT security teams have standardized on for years, offering strict boundary control and dedicated IP address allocation out-of-the-box.

### 4. Direct Deployment of Existing Docker Compose Files

* **The Scenario:** You have a multi-container solution defined locally in a `docker-compose.yml` file (e.g., a primary web app coupled with a companion caching or background processing container) and you want to lift-and-shift it to the cloud with minimal refactoring.
* **Why App Service Wins:** App Service natively supports multi-container deployments via Docker Compose out-of-the-box. You can upload your compose file, and Azure provisions the containers together on the plan. In contrast, Azure Container Apps manages multi-container architectures via its internal Dapr/sidecar or multi-container pod paradigm, which often requires redefining your architecture into distinct microservice definitions and revising networking boundaries.

### 5. Seamless Staging Slots and Built-In Deployment Workflows

* **The Scenario:** You need a bulletproof, native staging slot mechanism to swap production traffic between versions instantly, combined with tightly integrated deployment center connectors for GitHub Actions, Azure DevOps, or container registries with minimal configuration overhead.
* **Why App Service Wins:** While Container Apps supports revisions, App Service’s **Deployment Slots** feature provides a classic, highly intuitive production-vs-staging paradigm with zero-downtime slot swapping, auto-swap rules, and traffic-shifting capabilities that are deeply integrated into the Azure portal and CLI without needing to manage revision labels and traffic splits manually.

---

### Summary Comparison

| Requirement | Choose App Service Plan | Choose Azure Container Apps |
| --- | --- | --- |
| **Container OS** | Excellent Linux & Windows support | Primarily optimized for Linux |
| **Architecture** | Monoliths, Web Apps, Multi-container Compose | Microservices, Event-driven jobs, Dapr apps |
| **Scaling Model** | Fixed compute (always-on) or basic auto-scale | Dynamic scaling (including scale-to-zero) |
| **Networking** | Mature VNet integration & App Service Environments | Modern Kubernetes-based KEDA scaling & ingress |

---

# Manage revisions and secrets in Azure Container Apps

## Revisions

- Azure Container Apps implements container app versioning by reating revisions.

- Control which revisions are active, and the external traffic that is routed to each active revision.

- The `az containerapp update` command can modify environment variables, compute resources, scale parameters, and deploy a different image.

- If the update includes `revision-scope changes`, a new revision is generated.

## Secrets

- Secrets are defined at the application level, secured values are available to container apps.

- Each application revision can reference one or more secrets.

- When you create a container app, secrets are defined using the `--secrets parameter`.

---

# What is Dapr?

## Explore Dapr integration with Azure Container Apps

The `Distributed Application Runtime (Dapr)` provides capabilities for enabling application intercommunication, through messaging via pub/sub or reliable and secure service-to-service calls.

| Dapr API | Description |
|---|---|
| Service-to-service invocation | Discover services and perform reliable, direct service-to-service calls with automatic mTLS authentication and encryption. |
| State management | Provides state management capabilities for transactions and CRUD operations. |
| Pub/sub | Allows publisher and subscriber container apps to intercommunicate via an intermediary message broker. |
| Bindings | Trigger your applications based on events. |
| Actors | Dapr actors are message-driven, single-threaded, units of work designed to quickly scale. |
| Observability | Send tracing information to an Application Insights backend. |
| Secrets | Access secrets from your application code or reference secure values in your Dapr components. |
| Configuration | Access app configuration and be notified of updates. |

[Microservice APIs powered by Dapr](https://learn.microsoft.com/en-us/azure/container-apps/dapr-overview)   

Azure Container Apps includes a built-in, fully managed version of Dapr (Distributed Application Runtime). This integration lets you build and run microservices without needing to manually deploy or maintain the Dapr runtime infrastructure. [1] (https://learn.microsoft.com/en-us/azure/container-apps/dapr-overview), [2] (https://docs.dapr.io/operations/hosting/serverless/azure-container-apps/)

Core Architecture

• Managed Sidecar: Azure Container Apps automatically runs a Dapr sidecar next to your application container. [1] (https://techcommunity.microsoft.com/blog/appsonazureblog/azure-container-apps-dapr-binding-example/3045890), [2] (https://learn.microsoft.com/en-us/azure/container-apps/dapr-overview)
• Ports: The Dapr sidecar listens on HTTP port 3500 and gRPC port 50001 for internal communication. [1] (https://learn.microsoft.com/en-us/azure/container-apps/dapr-overview)
• Serverless Hosting: You focus on business logic while Azure Container Apps manages scaling (powered by KEDA), networking, and ingress (powered by Envoy). [1] (https://medium.com/@taiseer.joudeh/practical-azure-container-apps-with-dapr-f2d9b5ea1f82), [2] (https://learn.microsoft.com/en-us/azure/architecture/example-scenario/serverless/microservices-with-container-apps-dapr)

Supported Dapr Capabilities

• Service-to-Service Invocation: Call other microservices reliably with built-in service discovery and mutual TLS (mTLS) encryption. [1] (https://azure.github.io/aca-dotnet-workshop/aca/03-aca-dapr-integration/), [2] (https://techcommunity.microsoft.com/blog/appsonazureblog/azure-container-apps-dapr-binding-example/3045890)
• Publish & Subscribe (Pub/Sub): Build event-driven architectures using brokers like Azure Service Bus. [1] (https://medium.com/@taiseer.joudeh/practical-azure-container-apps-with-dapr-f2d9b5ea1f82), [2] (https://azure.github.io/aca-dotnet-workshop/aca/03-aca-dapr-integration/)
• State Management: Save and retrieve key-value state data using external stores like Azure Cosmos DB or Azure Blob Storage. [1] (https://learn.microsoft.com/en-us/azure/container-apps/microservices-dapr), [2] (https://medium.com/@taiseer.joudeh/practical-azure-container-apps-with-dapr-f2d9b5ea1f82)
• Input/Output Bindings: Connect your apps to external systems (such as databases, queues, and file storage) via declarative Dapr bindings. [1] (https://medium.com/@taiseer.joudeh/practical-azure-container-apps-with-dapr-f2d9b5ea1f82), [2] (https://techcommunity.microsoft.com/blog/appsonazureblog/azure-container-apps-dapr-binding-example/3045890)

Dapr Components in Container Apps

• Environment-Level Resources: Dapr components are defined at the Container Apps environment level and can be shared across multiple apps or scoped to specific application IDs. [1] (https://learn.microsoft.com/en-us/azure/container-apps/dapr-components), [2] (https://learn.microsoft.com/en-us/azure/container-apps/dapr-overview)
• Simplified Schema: Component manifests in Azure Container Apps drop redundant fields like apiVersion and kind found in open-source Dapr. [1] (https://learn.microsoft.com/en-us/azure/container-apps/dapr-components)
• Configuration Tools: You can enable and configure Dapr using the Azure Portal, Azure CLI, or Bicep/ARM templates. [1] (https://learn.microsoft.com/en-us/azure/container-apps/enable-dapr)

---

# Secrets

[Azure Container Apps Secrets Explained Kamal Rathnayake - MVP](https://www.youtube.com/watch?v=_VQ9mMRxYss&list=PLBmBUIbhAfd-eLB-XGxxhC68MNVl3I-Gi&index=14)  

---
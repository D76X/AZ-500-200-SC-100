# Answer Q06-A01

## Selected Options
##  Options 01
##  Options 02
##  Options 03
##  Options 04

---

# Q06

## Mission Critical: Application Design

[Have you designed the application to use containers as the unit of deployment?](https://learn.microsoft.com/en-us/assessments/23513bdb-e8a2-4f0b-8b6b-191ee1f52d34/sessions/8bac99a8-3d43-45dc-a393-a2f2bc623cb6?mode=questionnaire&id=23513bdb-e8a2-4f0b-8b6b-191ee1f52d34&session=8bac99a8-3d43-45dc-a393-a2f2bc623cb6&question=d3674e7f-9583-4174-981f-e350af768b89&category=3b978c5b-050a-4758-91ce-15c48a3800e1)  

# Have you designed the application to use containers as the unit of deployment?

Containerization allows developers to create and deploy applications faster and more reliably by bundling application code together with related configuration files, libraries, and dependencies required for it to run. This container runs on a shared kernel abstracted from the host operating system, and as a result is highly portable, capable of running consistently across different infrastructure platforms or cloud providers.

##  Options 01
All application components are containerized as images comprised of application code and all software dependencies.

Containerization is an excellent option for packaging applications, providing an abstraction layer for application code and its dependencies to achieve separation from the underlying hosting platform. Including all software dependencies within the container ensures portability so that it can work across different operating systems, regardless of runtimes or library versions. Containerized applications are therefore easier to move between application platforms due to the standardized container format.

##  Options 02
Lightweight Linux-based container runtimes are used whenever possible.

Linux-based containers are typically considerably more lightweight and should be prioritized where possible. Windows containers can be considered for special use cases with hard requirements on the Windows operating system, such as legacy .NET workloads.

##  Options 03
All containers are stateless and data is persisted by writing to an external data platform or by mounting external storage.

While it's possible to store data within a running container's filesystem, the data will not persist when the container is recreated. Instead, persistence should be achieved by either mounting external storage or writing to an external data platform.

##  Options 04
All relevant logs and metrics are gathered from the container, container host, and underlying cluster.

All application, container, container host, and underlying cluster logs and metrics should be gathered and stored in a unified data sink for further aggregation, troubleshooting, alerting and health modeling.

##  Options 05
None of the above.

---

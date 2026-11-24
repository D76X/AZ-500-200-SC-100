[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q17

A security architect is reviewing an Azure API Management instance that exposes sensitive line-of-business APIs. The design requires the gateway to authenticate to Microsoft Entra-protected downstream services without storing application credentials, and the API Management endpoint must not expose an internet-routable entry point. Which two configurations satisfy these requirements?

Select two options below.

### OPTION 01
Enable Azure DDoS Protection Standard on the virtual network hosting API Management

### OPTION 02
Configure API Management to use managed identity for authenticating to backend services

### OPTION 03
Deploy API Management in a virtual network with internal mode to restrict public access

### OPTION 04
Configure API Management to require client certificate authentication for all API consumers

---

## Answer

**Correct answers: OPTION 02 — managed identity, and OPTION 03 — internal VNet mode.**

### Why the selected answers are correct

- **OPTION 02 — Configure API Management to use managed identity for authenticating to backend services:** A managed identity is a Microsoft Entra identity that Azure manages for API Management. API Management can use the identity to obtain tokens and access Microsoft Entra-protected resources without developers provisioning or storing application secrets or credentials. Azure manages the identity and secret lifecycle, so the architecture avoids stored application credentials. [1][2]

- **OPTION 03 — Deploy API Management in a virtual network with internal mode:** Internal VNet mode makes the API Management endpoints, including the gateway, accessible only through a virtual network that the organization controls. It does not register the endpoints in public DNS, and the endpoints remain inaccessible until the organization configures private DNS. This satisfies the requirement that the API Management endpoint not have an internet-routable entry point. [3][4]

### Why the unselected answers are incorrect

- **OPTION 01 — Enable Azure DDoS Protection Standard:** Azure DDoS Protection Standard helps protect public Azure resources from distributed denial-of-service attacks. It provides network protection and resiliency, but it does not give API Management a credential-free identity for backend authentication, nor does it, by itself, remove or privatize the gateway's public entry point. The separate managed identity and internal VNet configurations are required for the stated requirements. [5]

- **OPTION 04 — Configure API Management to require client certificate authentication for all API consumers:** Client-certificate or mutual TLS authentication can secure API consumer-to-gateway or gateway-to-backend connections. In this option, the certificates are used to authenticate API consumers at the gateway. That does not provide the API Management gateway with a managed Microsoft Entra identity for downstream authentication, and it does not hide the gateway from the internet. Therefore, it does not satisfy either required architecture outcome. [6]

### References

1. [Use managed identities in Azure API Management](https://learn.microsoft.com/en-us/azure/api-management/api-management-howto-use-managed-service-identity) — explains that API Management managed identities use Microsoft Entra ID, can access protected resources, and do not require users to provision or rotate secrets.
2. [What are managed identities for Azure resources?](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview) — explains the managed identity lifecycle and use of an identity for Azure resource authentication.
3. [Deploy Azure API Management instance to an internal VNet](https://learn.microsoft.com/en-us/azure/api-management/api-management-using-with-internal-vnet) — states that internal mode exposes the API Management endpoints only within a controlled virtual network and that the endpoints are not registered in public DNS.
4. [Azure API Management with an Azure virtual network](https://learn.microsoft.com/en-us/azure/api-management/virtual-network-concepts) — distinguishes external and internal virtual networking models and their supported traffic and access scenarios.
5. [Azure DDoS Protection overview](https://learn.microsoft.com/en-us/azure/ddos-protection/ddos-protection-overview) — describes DDoS Protection as protection against denial-of-service attacks, not as gateway identity or private network deployment.
6. [Secure API Management backend using client certificate authentication](https://learn.microsoft.com/en-us/azure/api-management/api-management-howto-mutual-certificates) — explains that mutual certificate authentication is used to secure connections with client certificates, but is distinct from using an API Management managed identity for Microsoft Entra authentication.

---
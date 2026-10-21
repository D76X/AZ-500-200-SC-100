# Eaxm Practice Cloud and AI Security Engineer Associate (SC-500)

[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q01

Contoso is onboarding an external contractor, `judy@vendor.com`, for a 30-day security review. 
Judy has a `B2B collaboration guest account` in Contoso and will receive `Security Copilot Contributor` access. 
`Vendor.com` manages Judy's device and can issue a Microsoft Entra compliant-device claim, but Contoso does not 
currently trust device-compliance claims from `vendor.com`.

Contoso requires Judy to satisfy multifactor authentication and use a compliant device when accessing Security Copilot. 
The requirement must be enforced by Contoso rather than relying solely on vendor.com's Conditional Access policies. 

Which configuration meets the requirement?

Select one answer option below.

## OPTION 01
In Contoso, require MFA and a compliant device with Conditional Access for Security Copilot, 
and configure inbound cross-tenant trust for vendor.com's compliant-device claim.

## OPTION 02
Rely on Judy's home tenant to enforce MFA and device compliance, since cross-tenant access 
settings automatically apply the resource tenant's requirements to guests

## OPTION 03
Assign Judy the Copilot Owner role instead of Contributor, since Owner-level access automatically enforces stronger sign-in requirements for guest accounts

## OPTION 04
Configure a Microsoft Entra ID Protection user risk policy requiring MFA whenever Judy's calculated sign-in risk level is high or medium

---

> Refs

[Microsoft Entra External ID B2C & External Identities- Deployment Architectures Formula5 ](https://www.youtube.com/watch?v=AJS1qGkAvmg&t=434s)  

---

# Microsoft Entra ID Self-Service Sign-Up

Microsoft Entra ID self-service sign-up lets external or email-verified users automatically 
create their own accounts and join a directory or app. Admins manage these flows through 
user flows or PowerShell policies to reduce manual invitations and help desk tickets. 

[1] (https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-overview), 
[2] (https://learn.microsoft.com/en-us/entra/identity/users/directory-self-service-signup), 
[3] (https://learn.microsoft.com/en-gb/answers/questions/5981826/self-registration-portal-in-entra-id-for-guest-acc), 
[4] (https://www.microsoft.com/en-gb/security/business/identity-access/microsoft-entra-user-self-service-portals)

## How Self-Service Sign-Up Works

• User Flows: Applications trigger a customizable sign-up journey where users provide details or verify their email. 

[1] (https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-user-flow), 
[2] (https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-overview)

• Identity Providers: Supports Entra accounts, social logins (Google, Facebook), Microsoft accounts, or email one-time passcodes (OTP). 

[1] (https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-user-flow)

• Email Domains: Users can register using work email aliases, occasionally creating unmanaged tenants or email-verified member accounts depending on company policy. 

[1] (https://learn.microsoft.com/en-us/entra/identity/users/directory-self-service-signup)

## How to Enable Guest Self-Service Sign-Up

1. Sign in to the Microsoft Entra admin center with a User Administrator or higher role. 
[1] (https://learn.microsoft.com/en-gb/answers/questions/5981826/self-registration-portal-in-entra-id-for-guest-acc) 

2. Browse to Entra ID > External Identities > External collaboration settings. 
[1] (https://learn.microsoft.com/en-gb/answers/questions/5981826/self-registration-portal-in-entra-id-for-guest-acc)

3. Set Enable guest self-service sign up via user flows to Yes and click Save. 
[1] (https://learn.microsoft.com/en-gb/answers/questions/5981826/self-registration-portal-in-entra-id-for-guest-acc)

4. Go to User flows, select New user flow, choose your identity providers and required user attributes, and link it to your target application. 
[1] (https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-user-flow)

## Key Admin Controls

• `AllowEmailVerifiedUsersToJoinOrganization`: Controls whether users can join a tenant via email domain validation. 
[1] (https://learn.microsoft.com/en-us/entra/identity/users/directory-self-service-signup)  

• `AllowedToSignUpEmailBasedSubscriptions`: Toggles whether users can initiate ad-hoc self-service sign-ups for cloud services. 
[1] (https://learn.microsoft.com/en-us/entra/identity/users/directory-self-service-signup)

---

> Refs

[What is self-service sign-up for Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/users/directory-self-service-signup)  

This article covers self-service sign-up for email-verified users in Microsoft Entra ID organizations. 

[Microsoft EntraExternal ID Self-service sign-up](https://learn.microsoft.com/en-us/entra/external-id/self-service-sign-up-overview)  

Self-service sign-up is an essential feature for your External ID workforce and customer scenarios. 
It gives your partners, consumers, and other external users a frictionless way to sign up and get access 
to your apps without any intervention on your part.

---

# What are the differences between the Microsoft Entra ID B2C feature and Microsoft Entra ID External identities?

**Microsoft Entra External ID** is Microsoft’s next-generation platform for Customer Identity and Access Management (CIAM), built directly on the modern **Microsoft Entra ID** architecture.

While both **Azure AD B2C** (legacy name for Microsoft Entra ID B2C) and **Microsoft Entra External ID** manage external identities (customers, partners, and citizens), **Entra External ID is the active replacement for Azure AD B2C**. Azure AD B2C was retired to new customers as of `May 1, 2025`, and existing tenants will be supported until 2030.

---

## Key Differences Breakdown

| Feature / Area | Microsoft Entra ID B2C (Legacy) | Microsoft Entra External ID (Next-Gen) |
| --- | --- | --- |
| **Platform Architecture** | Built on an isolated legacy Azure AD stack running as an isolated tenant type. | Native extension of the standard Microsoft Entra ID platform. |
| **Customization & Extensibility** | **Identity Experience Framework (IEF):** Uses complex, hand-written XML Custom Policies for advanced business logic. | **Custom Authentication Extensions:** Code-first hooks (using Web APIs/Azure Functions) triggered at specific pipeline events. |
| **Developer & Admin Portal** | Separate Azure AD B2C portal; isolated user APIs and custom endpoints. | Unified Microsoft Entra Admin Center; integrated developer tools, VS Code extensions, and Microsoft Graph APIs. |
| **Security & Access Control** | Limited Conditional Access; relies primarily on B2C-specific identity protection rules. | Full native **Entra Conditional Access**, Identity Protection, continuous access evaluation, and Risk-Based MFA. |
| **Authentication Flow Model** | User Flows (GUI) or Custom Policies (XML). | Modern **User Journeys** and Native Authentication SDKs for mobile and web apps. |
| **Social & External Identity Providers** | Broad legacy social provider support (Google, Facebook, Apple, Microsoft Account, etc.). | Native support for Google, Facebook, and SAML/OIDC federation (additional social IdPs expanding continually). |
| **Pricing Model** | Per-authentication tiers or Legacy MAU models. | **First 50,000 Monthly Active Users (MAU) Free**, then standard per-MAU tiering. |

---

## Core Architectural Differences

### 1. Extensibility Model (XML vs. Event-Driven Code)

* **Entra ID B2C:** Relies on the Identity Experience Framework (IEF). Customizing flows requires configuring complex XML files containing orchestrations, technical profiles, and claim transformations. While powerful, it carries a steep learning curve and is difficult to maintain.
* **Entra External ID:** Modernizes this with **Custom Authentication Extensions** built on OpenID Connect (OIDC) standard events. Logic is executed via standard Web APIs or serverless functions (like Azure Functions) that hook into stages such as token issuance (`onTokenIssuanceStart`) or user registration.

### 2. Tenant Management & Integration

* **Entra ID B2C:** B2C tenants operate as distinct, isolated silos. Administration is separated from standard workforce directory management.
* **Entra External ID:** Integrates into standard Entra ID environments. Managing customer journeys, developer app registrations, conditional access, and reporting occurs in the main Entra Admin Center using Microsoft Graph endpoints.

### 3. Native Authentication & Developer Experience

* **Entra ID B2C:** Requires web redirection or embedded browser webviews (`Custom Web UI`) to handle authentication journeys.
* **Entra External ID:** Supports **Native Authentication SDKs**. This allows developers to build fully native sign-in and sign-up interfaces directly inside iOS, Android, or desktop applications without redirecting users out of the native UI framework.

---

## Migration Path

For organizations currently using Azure AD B2C, Microsoft recommends planning a transition to Entra External ID. Microsoft provides a **B2C-to-External ID Migration Kit** which supports:

1. **Bulk Export/Import:** Exporting user profile metadata from B2C to External ID.
2. **Just-In-Time (JIT) Password Migration:** Migrating user credentials securely during their initial login without requiring a global password reset across your customer base.

---



[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q09

A company's Azure App Service web app uses App Service Authentication (`Easy Auth`) 
configured with a single identity provider, restricting sign-in to the company's own 
Microsoft Entra ID tenant. The app also has a staging deployment slot used by the 
development team to validate changes before swapping them into production. 
During a review, the security team discovers that the staging slot is reachable at 
its own default hostname and does not enforce the same sign-in requirement as the production slot.

Which two actions should the team take to ensure the staging slot enforces the same authentication requirement?

### OPTION 01
Disable public network access on the App Service resource so that only requests routed 
through the production hostname are accepted

### OPTION 02
Enable Azure Front Door in front of the App Service and configure it to require authentication 
for all incoming requests

### OPTION 03
Configure the staging slot to require authentication and reject or redirect unauthenticated requests

### OPTION 04
Add an IP restriction rule to the production slot that allows inbound traffic only from the corporate office network range

### OPTION 05
Configure App Service Authentication independently on the staging slot to mirror the production sign-in configuration

## Answer

**Select options 03 and 05.** 

Option 05 configures the staging slot with the same identity provider and tenant restriction as production. 
Option 03 makes that configuration enforce access control by requiring authentication and choosing what 
happens to unauthenticated requests (for example, redirecting website users to sign in or rejecting the request).

Deployment slots are live apps with their own hostnames and editable configuration, so protecting the production 
hostname does not automatically protect the staging hostname. App Service Authentication must be configured for 
the staging slot as well as production. Verify the staging slot uses the same Microsoft Entra provider and tenant restriction; then set its unauthenticated-request behavior to require sign-in or reject the request.

---

### Why the other options are incorrect

- **Option 01:** Disabling public network access is a network-access control, not an authentication setting, 
and it does not make the production hostname the only hostname for the app. It could also prevent the development 
team from reaching staging. Use it only if private network access is an additional requirement, not as a substitute 
for configuring authentication on the slot.

- **Option 02:** Azure Front Door does not configure Easy Auth on the staging slot. Because the slot has its own hostname, clients could still reach it directly unless that route is separately restricted; putting Front Door 
in front of production alone therefore does not ensure the slot enforces the same sign-in policy.

- **Option 04:** This rule applies to the production slot, not the staging slot. It restricts source IP addresses 
rather than requiring users to sign in with the company's Microsoft Entra tenant.

### References

- [Microsoft Learn: Authentication and authorization in Azure App Service](https://learn.microsoft.com/en-us/azure/app-service/overview-authentication-authorization) — Describes Easy Auth and the **Require authentication** setting, including redirecting or rejecting unauthenticated requests.

- [Microsoft Learn: Set up staging environments in Azure App Service](https://learn.microsoft.com/en-us/azure/app-service/deploy-staging-slots) — Describes deployment slots as live apps with their own hostnames and editable configuration; its slot-swap section also identifies IP restrictions as slot-specific.

---
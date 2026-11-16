[Eaxm Practice: Cloud and AI Security Engineer Associate (SC-500)](https://app.pluralsight.com/assessment-pe/cloud-and-ai-security-engineer-associate-sc-500/intro)  

Each attempt is randomly generated. Retake the exam to gain confidence.
You have 14 days to complete each attempt before it expires.

---

# Q13

Fabrikam is connecting a GCP project named gcp-prod-1 to Defender for Cloud so its Compute Engine VMs and GKE clusters appear in the multicloud security posture assessment. Fabrikam already has an AWS connector configured using the native CloudFormation-based mechanism. Fabrikam's security standard prohibits creating any long-lived, downloadable service account key for any cross-cloud integration, since such keys don't expire on their own and have previously contributed to credential-leakage findings in security audits.

Which authentication method should Fabrikam configure for the GCP connector to meet this requirement?

Select one answer option below.

### OPTION 01
Configure the GCP connector using the same AWS CloudFormation-based cross-account role mechanism already used for Fabrikam's AWS connector

### OPTION 02
Configure the GCP connector to authenticate using an Azure managed identity that is already assigned to the Defender for Cloud resource

### OPTION 03
Configure the GCP connector using Workload Identity Federation, obtaining short-lived credentials with no downloadable service key

### OPTION 04
Configure the GCP connector using a service account with a downloaded JSON key file, and rotate the key file every 90 days

---

# Answer

## Correct Answer: OPTION 03

Configure the GCP connector using **Workload Identity Federation**, which exchanges short-lived tokens and does not require a downloadable service account key.

## Why OPTION 03 Is Correct

Defender for Cloud's GCP connector uses workload identity federation to establish trust between Microsoft Entra ID and Google Cloud. During authentication, Defender for Cloud exchanges a short-lived Entra token with Google Cloud Security Token Service (STS), then impersonates a GCP service account whose permissions are scoped to the connected project or organization. The onboarding process creates the workload identity pool and provider, service accounts, and policy bindings needed for this trust. This meets Fabrikam's requirement because it avoids storing a long-lived service account key while still allowing Defender for Cloud to access GCP APIs for discovery and security posture assessment.

## Why the Other Options Are Incorrect

- **OPTION 01 — AWS CloudFormation-based cross-account role:** This is the AWS connector's onboarding mechanism and creates AWS-side resources and trust relationships. It does not configure GCP authentication. The GCP connector has its own onboarding flow, which establishes federated trust with Google Cloud.
- **OPTION 02 — Azure managed identity assigned to the Defender for Cloud resource:** An Azure managed identity alone does not establish the required trust or permissions in GCP. The GCP side must be configured with a workload identity provider and service-account impersonation policy so Google STS can validate the Entra token. Merely assigning an Azure managed identity does not replace that GCP configuration.
- **OPTION 04 — Downloaded JSON service account key rotated every 90 days:** A downloaded service account key is a long-lived credential unless separately disabled or deleted. Periodic rotation still creates and stores such a key, so it violates the stated prohibition. Workload Identity Federation avoids the need to create or manage service account keys.

## References

- [Connect your GCP Project to Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/quickstart-onboard-gcp) — Describes GCP connector onboarding, configuring access, and the GCP resources created by the generated onboarding script.
- [Authentication architecture for GCP connectors](https://learn.microsoft.com/en-us/azure/defender-for-cloud/authentication-architecture-google-cloud) — Documents workload identity federation, short-lived token exchange, Google STS, service-account impersonation, and scoped access.
- [Connect your AWS Account to Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/defender-for-cloud/quickstart-onboard-aws) — Describes the separate native AWS connector and its AWS-specific authentication architecture.
- [Workload Identity Federation](https://cloud.google.com/iam/docs/workload-identity-federation) — Google Cloud documentation explaining how federation provides access without service account keys and reduces the security and maintenance risks associated with those keys.
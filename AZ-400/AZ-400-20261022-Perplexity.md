# AZ-400 Practice Questions — Full Questions, Answers, and Reasoning

> **Note:** This document contains the **24 questions presented in this conversation**. The exam reference says “25 questions,” but one question was not included in the chat transcript. The missing question should be added when available.

---

## Question 1

### Question

You are reviewing GitHub Actions that have been created in your organization.

You need to resolve the following issues that you identified:

- The definitions of many actions are long and complex.
- Ongoing management of actions is difficult because the same code is repeated in many actions.

What should you do to resolve the issues?

**Select only one answer.**

- Remove all secrets embedded in the action files.
- Create chainable actions.
- Separate variable definitions into separate files.
- Separate variable group definitions into separate files.

### Correct answer

**Create chainable actions.**

### Motivation

Chainable actions—implemented through reusable workflows or composite actions—directly address both issues: they reduce long, complex workflow definitions and eliminate repeated code by centralizing common logic in reusable components.

GitHub recommends reusable workflows and custom actions for transforming duplicated automation into shared components, reducing maintenance overhead.

| Option | Why it is correct or incorrect |
|---|---|
| **Create chainable actions** | **Correct.** Reusable workflows and composite actions package repeated logic into shared components, reducing duplication and simplifying maintenance. |
| Remove all secrets embedded in the action files | Incorrect. This improves security but does not reduce complexity or duplicated workflow logic. |
| Separate variable definitions into separate files | Incorrect. This may organize configuration but does not make actions reusable or chainable. |
| Separate variable group definitions into separate files | Incorrect. Variable groups are an Azure DevOps concept, not the GitHub Actions mechanism for reusing action logic. |

### Example

```yaml
jobs:
  build:
    uses: org/reusable-workflows/.github/workflows/build.yml@main
```

---

## Question 2

### Question

You have a GitHub workflow that deploys an Azure web app. The workflow is configured to trigger a deployment following a pull request that includes a label.

You plan to configure the pull request of the workflow to trigger the deployment only if the label is set to a string of `stage`.

The workflow includes the following section:

```yaml
if: contains(<missing element>.event.pull_request.labels.*.name, 'stage')
```

What should you add for the missing element of the workflow?

**Select only one answer.**

- action
- github
- name
- workflow

### Correct answer

**github**

### Motivation

The completed expression is:

```yaml
if: contains(github.event.pull_request.labels.*.name, 'stage')
```

The `github` context contains the webhook payload for the event that triggered the workflow. For a `pull_request` event, it includes `event.pull_request.labels`. The `.*.name` selector extracts the label names, and `contains()` checks whether `stage` is present.

| Option | Why it is correct or incorrect |
|---|---|
| **github** | **Correct.** The `github` context exposes `event.pull_request.labels`, enabling the label check. |
| action | Incorrect. This is not the context containing the triggering pull-request event payload. |
| name | Incorrect. This is not the context containing the triggering pull-request event payload. |
| workflow | Incorrect. This is not the context containing the triggering pull-request event payload. |

### Important implementation detail

To trigger when the label is added after the pull request is opened, include the `labeled` event type:

```yaml
on:
  pull_request:
    types: [labeled, synchronize, reopened]
```

---

## Question 3

### Question

You plan to add a job to a GitHub workflow that will deploy a container-based web app to Azure Web Apps.

You need to ensure that a previous job in the workflow completes successfully before the new job can run.

Which GitHub workflow element should you add to the workflow?

**Select only one answer.**

- contains
- needs
- runs-on
- uses

### Correct answer

**needs**

### Motivation

The `needs` keyword defines a dependency between jobs. A job with `needs: <previous-job>` will not run until the specified job completes successfully.

| Option | Why it is correct or incorrect |
|---|---|
| **needs** | **Correct.** It creates a job dependency and ensures the dependent job waits for successful completion of the prior job. |
| contains | Incorrect. It is an expression function used in conditions, not a job dependency mechanism. |
| runs-on | Incorrect. It specifies the runner that executes the job, such as `ubuntu-latest`. |
| uses | Incorrect. It references an action or reusable workflow within a step, not a job dependency. |

### Example

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

  deploy:
    needs: build
    runs-on: ubuntu-latest
    steps:
      - name: Deploy container web app
        run: echo "Deploy to Azure Web Apps"
```

If the job listed in `needs` fails or is skipped, the dependent job is also skipped by default.

---

## Question 4

### Question

You are using Azure Pipelines to manage building an app.

You need to run a server job directly on Azure DevOps.

Which job type should you implement?

**Select only one answer.**

- an agent pool job
- an agentless job
- a container job
- a virtual machine job

### Correct answer

**an agentless job**

### Motivation

An agentless job, also called a **server job**, runs directly on the Azure DevOps server. It does not require a build agent or target computer.

| Option | Why it is correct or incorrect |
|---|---|
| **an agentless job** | **Correct.** A server job is orchestrated and executed on Azure DevOps itself and does not require an agent. |
| an agent pool job | Incorrect. It runs on a Microsoft-hosted or self-hosted agent, not directly on Azure DevOps. |
| a container job | Incorrect. It runs inside a container on an agent, so it still requires an agent. |
| a virtual machine job | Incorrect. This is not the Azure Pipelines job type that executes directly on Azure DevOps. |

### Example

```yaml
jobs:
- job: ServerJob
  pool: server
  steps:
  - task: Delay@1
    inputs:
      delayForMinutes: '1'
```

Agentless jobs support only a limited set of tasks, such as Delay, Invoke REST API, Invoke Azure Function, Manual Validation, and Query Work Items.

---

## Question 5

### Question

You are developing a public open-source project by using GitHub.

You need to ensure that only the project maintainer can push to the official repository.

Which type of branching workflow should you implement?

**Select only one answer.**

- trunk-based
- GitHub flow
- feature branch
- forking

### Correct answer

**forking**

### Motivation

In a forking workflow, contributors create their own fork, push changes to that fork, and submit pull requests to the official upstream repository. Only the project maintainer has push access to the official repository.

| Option | Why it is correct or incorrect |
|---|---|
| **forking** | **Correct.** Contributors push to their own forks, while only the maintainer can push to the official repository. |
| trunk-based | Incorrect. Contributors commit frequently to a shared main/trunk branch, typically requiring write access. |
| GitHub flow | Incorrect. It uses branches and pull requests within the same repository, generally requiring repository write access. |
| feature branch | Incorrect. It uses branches in the shared repository and does not inherently prevent contributors from pushing to the official repository. |

### Typical flow

1. Contributor forks the official repository.
2. Contributor creates a branch in the fork.
3. Contributor pushes changes to the fork.
4. Contributor opens a pull request against the upstream repository.
5. Maintainer reviews and merges the pull request.

---

## Question 6

### Question

You have an Azure subscription that contains a resource group named RG1.

You have a GitHub repository that contains the resources shown in the following table.

| Name | Type |
|---|---|
| `main.bicep` | Bicep file |
| `main.yml` | GitHub Actions workflow file |
| `AZURE_RG1` | Secret |
| `AZURE_CREDENTIALS` | Secret |
| `AZURE_SUBSCRIPTION` | Secret |

You create a service principal and assign it least-privilege access to deploy resources to RG1.

You need to configure `main.yml` to authenticate to Azure by using the `AZURE_CREDENTIALS` secret. The solution must follow the principle of least privilege.

What should you do?

**Select only one answer.**

- Add a step that uses the `azure/login@v2` action and specifies the `client-id`, `tenant-id`, and `subscription-id` inputs.
- Add a step that uses the `azure/login@v2` action and uses the `creds` input.
- Create an Azure Resource Manager (ARM) service connection that uses the service principal.
- Create an Azure Resource Manager (ARM) service connection that uses a federated identity.

### Correct answer

**Add a step that uses the `azure/login@v2` action and uses the `creds` input.**

### Motivation

The repository already contains an `AZURE_CREDENTIALS` secret. This secret contains the JSON credential object expected by `azure/login@v2`, including the service principal client ID, client secret, tenant ID, and subscription ID.

| Option | Why it is correct or incorrect |
|---|---|
| **Use `azure/login@v2` with `creds`** | **Correct.** It uses the existing `AZURE_CREDENTIALS` secret and authenticates with the service principal. |
| Specify `client-id`, `tenant-id`, and `subscription-id` | Incorrect. This is the OIDC/federated-identity pattern and does not use the existing secret-based `AZURE_CREDENTIALS` credential. |
| Create an ARM service connection | Incorrect. Service connections are Azure DevOps constructs, not GitHub Actions workflow configuration. |
| Create an ARM service connection using federated identity | Incorrect. Federated identity is more secure than a client secret, but it does not satisfy the requirement to authenticate using `AZURE_CREDENTIALS`. |

### Example

```yaml
- name: Azure login
  uses: azure/login@v2
  with:
    creds: ${{ secrets.AZURE_CREDENTIALS }}
```

The `AZURE_CREDENTIALS` secret should contain:

```json
{
  "clientId": "<client-id>",
  "clientSecret": "<client-secret>",
  "subscriptionId": "<subscription-id>",
  "tenantId": "<tenant-id>"
}
```

For least privilege, scope the service principal’s role assignment to **RG1**, not to the entire subscription.

---

## Question 7

### Question

You have a GitHub repository that contains Bicep files.

You need to create a GitHub action that will deploy resources defined in the Bicep files.

What should you create?

**Select only one answer.**

- a JSON file in the `.github/templates` folder
- a JSON file in the `.github/workflows` folder
- a YAML file in the `.github/templates` folder
- a YAML file in the `.github/workflows` folder

### Correct answer

**a YAML file in the `.github/workflows` folder**

### Motivation

GitHub Actions workflows must be defined in YAML files with a `.yml` or `.yaml` extension and stored in the repository’s `.github/workflows` directory.

| Option | Why it is correct or incorrect |
|---|---|
| **YAML file in `.github/workflows`** | **Correct.** GitHub discovers and runs workflow files from this directory. |
| JSON file in `.github/templates` | Incorrect. GitHub Actions workflows use YAML, not JSON. |
| JSON file in `.github/workflows` | Incorrect. The directory is correct, but the file format is wrong. |
| YAML file in `.github/templates` | Incorrect. `.github/templates` is not the directory GitHub uses to discover workflows. |

### Example

```yaml
name: Deploy Bicep

on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - uses: azure/login@v2
        with:
          creds: ${{ secrets.AZURE_CREDENTIALS }}

      - name: Deploy Bicep
        uses: azure/arm-deploy@v2
        with:
          subscriptionId: ${{ secrets.AZURE_SUBSCRIPTION }}
          resourceGroupName: RG1
          template: ./main.bicep
```

---

## Question 8

### Question

You manage five Azure subscriptions.

You need to ensure that all automated deployments via Azure Pipelines can proceed only if security vulnerabilities are NOT present in the code.

What should you use?

**Select only one answer.**

- Azure Policy
- GitHub Advanced Security for Azure DevOps
- management group
- Microsoft Defender for Cloud

### Correct answer

**GitHub Advanced Security for Azure DevOps**

### Motivation

GitHub Advanced Security for Azure DevOps integrates code scanning, dependency scanning, and secret scanning with Azure Repos and Azure Pipelines. Its status checks can block pull requests from being merged when security vulnerabilities are detected.

| Option | Why it is correct or incorrect |
|---|---|
| **GitHub Advanced Security for Azure DevOps** | **Correct.** It scans code and dependencies and can enforce status checks that block vulnerable changes from proceeding. |
| Azure Policy | Incorrect. It governs Azure resource configuration, not source-code vulnerability scanning in pipelines. |
| Management group | Incorrect. It organizes subscriptions for policy and RBAC inheritance; it does not scan code or gate pipelines. |
| Microsoft Defender for Cloud | Incorrect. It provides cloud security posture and repository scanning, but its code scanning is not the Azure Pipelines-native deployment gate described here. |

### Key capabilities

| Capability | Purpose |
|---|---|
| Code scanning | Uses CodeQL to identify security vulnerabilities and coding errors. |
| Dependency scanning | Detects vulnerable open-source dependencies. |
| Secret scanning | Detects exposed credentials. |
| Advanced Security status checks | Blocks pull requests when security vulnerabilities are detected. |

---

## Question 9

### Question

You use pipelines to deploy Azure infrastructure.

You plan to implement an Azure Policy solution to ensure compliance with regulatory requirements. The solution must meet the following requirements:

- Audit unencrypted Azure SQL databases.
- Monitor network security groups (NSGs) for specific ports.
- Monitor whether vulnerability assessment solutions are installed on virtual machines.
- Group all requirements for ease of administration.

What should you include in the solution?

**Select only one answer.**

- initiative definition
- policy definition
- policy remediation
- policy scope

### Correct answer

**initiative definition**

### Motivation

An Azure Policy initiative, also called a policy set, groups multiple related policy definitions into a single assignable and manageable object.

| Option | Why it is correct or incorrect |
|---|---|
| **Initiative definition** | **Correct.** It groups the SQL, NSG, and VM vulnerability-assessment policies into one manageable compliance set. |
| Policy definition | Incorrect. It defines one individual rule, not a group of requirements. |
| Policy remediation | Incorrect. It corrects existing non-compliant resources after evaluation; it does not group requirements. |
| Policy scope | Incorrect. It determines where an assignment applies, such as a management group or subscription; it does not group policies. |

### Why an initiative is appropriate

- It allows several policy definitions to be assigned with one assignment.
- It provides consolidated compliance status for all included policies.
- Its `policyDefinitionGroups` property can categorize policies into controls and compliance domains.

Assign the initiative at a management group that includes all five subscriptions so the requirements apply consistently across the environment.

---

## Question 10

### Question

You are applying Azure Policy to Azure resources.

You must define a policy assignment.

Which type of file should you create?

**Select only one answer.**

- an XML document
- a JSON document
- a CSV file
- a TSV file

### Correct answer

**a JSON document**

### Motivation

Azure Policy assignments are defined using JavaScript Object Notation (JSON). The assignment specifies the policy or initiative definition, parameters, scope, enforcement mode, exclusions, and other settings.

| Option | Why it is correct or incorrect |
|---|---|
| **JSON document** | **Correct.** Azure Policy definitions and assignments use JSON. |
| XML document | Incorrect. XML is not the native Azure Policy assignment format. |
| CSV file | Incorrect. CSV is not used to define Azure Policy assignments. |
| TSV file | Incorrect. TSV is not used to define Azure Policy assignments. |

### Example

```json
{
  "properties": {
    "displayName": "Require SQL encryption",
    "policyDefinitionId": "/providers/Microsoft.Authorization/policyDefinitions/<definition-id>",
    "scope": "/subscriptions/<subscription-id>/resourceGroups/RG1",
    "enforcementMode": "Default",
    "parameters": {}
  }
}
```

---

## Question 11

### Question

You have a GitHub repository named Repo1 that is used by two teams named Team1 and Team2. The teams work independently.

You need to recommend a planning solution for each team. The solution must meet the following requirements:

- Each team must have its own Azure Boards board.
- Each team board must be accessible to only the team’s respective members.
- The solution must minimize administrative effort.

What should you include in the recommendation?

**Select only one answer.**

- one Azure DevOps project that contains a board for each team
- one GitHub project that contains a label for each team
- one Azure DevOps project for each team
- one GitHub project for each team

### Correct answer

**one Azure DevOps project that contains a board for each team**

### Motivation

Create Team1 and Team2 within the same Azure DevOps project, assign each team its own area path, and configure area-path permissions so each team can access only its own work items.

| Option | Why it is correct or incorrect |
|---|---|
| **One Azure DevOps project with a board for each team** | **Correct.** Teams and area paths provide separate boards and access boundaries while minimizing project administration. |
| One GitHub project with a label for each team | Incorrect. Labels do not provide Azure Boards team boards or enforce team-specific access boundaries. |
| One Azure DevOps project for each team | Incorrect. It provides isolation but duplicates repositories, pipelines, permissions, and project settings, increasing administrative effort. |
| One GitHub project for each team | Incorrect. It does not meet the Azure Boards requirement and increases administrative overhead. |

### Configuration steps

1. Create `Team1` and `Team2` under **Project settings > Teams**.
2. Create area paths such as `Project\Team1` and `Project\Team2`.
3. Assign each area path to the corresponding team.
4. Configure area-path security so Team1 can access only Team1 work items and Team2 only Team2 work items.
5. Each team’s board displays only work items under its assigned area path.

---

## Question 12

### Question

You have an Azure DevOps organization named Contoso and a GitHub repository named Repo1.

Your development team uses Azure Boards to track user stories and bugs.

You need to ensure that each code change made in GitHub can be traced directly back to the corresponding Azure Boards work items.

**Which two actions should you perform? Each correct answer presents part of the solution.**

**Select all answers that apply.**

- Configure GitHub branch protection rules to require passing a status check.
- From Azure Pipelines, create a build retention policy to indefinitely store build artifacts.
- Create a GitHub action that validates all commit messages.
- Configure GitHub Actions to automatically assign pull requests to Azure Boards based on labels.

### Correct answers

- **Create a GitHub action that validates all commit messages.**
- **Configure GitHub Actions to automatically assign pull requests to Azure Boards based on labels.**

### Motivation

Azure Boards links GitHub commits and pull requests to work items through `AB#<work-item-id>` references. Validating commit messages ensures developers consistently include the work-item ID, while GitHub Actions can extract that ID and link the pull request to the corresponding Azure Boards work item.

| Option | Why it is correct or incorrect |
|---|---|
| **Create a GitHub action that validates all commit messages** | **Correct.** It enforces inclusion of `AB#<work-item-id>` in commit messages, ensuring traceability. |
| **Configure GitHub Actions to automatically assign pull requests to Azure Boards based on labels** | **Correct.** It automates linking GitHub pull requests to the corresponding Azure Boards work items. |
| Configure branch protection rules to require passing a status check | Incorrect. This enforces CI quality gates but does not create work-item traceability. |
| Create a build retention policy to indefinitely store build artifacts | Incorrect. Retaining artifacts does not associate commits or pull requests with work items. |

### Example commit message

```text
Fix login validation error AB#1234
```

Azure Boards then displays the linked commit and pull request in the work item’s **Development** section.

---

## Question 13

### Question

You have an Azure DevOps organization named Contoso and a GitHub Enterprise Cloud organization.

You plan to use the GitHub repositories for source control.

You need to reference and link to Azure Boards work items directly from pull requests in GitHub.

What should you do first?

**Select only one answer.**

- Configure the security policy for the GitHub Enterprise Cloud organization.
- Create a GitHub action in GitHub.
- Create a GitHub repository service connection in Project1.
- Install the Azure Boards app from GitHub Marketplace.

### Correct answer

**Install the Azure Boards app from GitHub Marketplace.**

### Motivation

The Azure Boards GitHub app establishes the native Azure Boards–GitHub integration. After installation, you authorize the app for the GitHub organization, select the repository, and connect it to the Azure DevOps project.

| Option | Why it is correct or incorrect |
|---|---|
| **Install the Azure Boards app from GitHub Marketplace** | **Correct.** It is the first step to establish the native Azure Boards–GitHub integration. |
| Configure the security policy for the GitHub organization | Incorrect. It may be needed to approve app access, but it does not establish the integration itself. |
| Create a GitHub action | Incorrect. It can enforce `AB#` references but cannot create the native integration. |
| Create a GitHub repository service connection in Project1 | Incorrect. This is not the first step for Azure Boards work-item linking. |

### After installation

1. Authorize the Azure Boards app for the GitHub organization.
2. Select Repo1.
3. Connect it to the Azure DevOps project.
4. Use `AB#<work-item-id>` in commits or pull-request descriptions to create work-item links.

---

## Question 14

### Question

You have a GitHub repository named Repo1 that contains the source code of a web app.

You have an Azure DevOps organization named Contoso.

You need to link Repo1 to an Azure DevOps project in Contoso. The solution must meet the following requirements:

- Associate GitHub commits, pull requests, and issues with corresponding work items in Azure Boards.
- Follow the principle of least privilege.

What should you use?

**Select only one answer.**

- a GitHub app installed in the GitHub organization
- a GitHub user account that is a member of Repo1
- a personal access token (PAT) from your GitHub account
- your GitHub account credentials

### Correct answer

**a GitHub app installed in the GitHub organization**

### Motivation

A GitHub App can be scoped to specific repositories, so access can be limited to Repo1 only. It authenticates as an application identity rather than an individual user account, which better aligns with least privilege.

| Option | Why it is correct or incorrect |
|---|---|
| **A GitHub app installed in the GitHub organization** | **Correct.** It can be scoped to Repo1 and avoids using an individual user’s identity or broad credentials. |
| A GitHub user account that is a member of Repo1 | Incorrect. It ties the integration to a personal identity and grants broader access than necessary. |
| A personal access token (PAT) | Incorrect. A PAT is tied to a user and often requires broad scopes, making it less aligned with least privilege. |
| Your GitHub account credentials | Incorrect. Interactive personal credentials are unsuitable for an organizational integration. |

### Recommended configuration

1. Install the Azure Boards GitHub app.
2. Grant it access only to Repo1.
3. Connect Repo1 to the Contoso Azure DevOps project.
4. Use `AB#<work-item-id>` in commits or pull requests to link changes to work items.

---

## Question 15

### Question

You have an Azure DevOps project named Project1 that contains an Azure Repos repository named Repo1.

You have a GitHub repository named Repo2.

You need to integrate Azure Boards with both Repo1 and Repo2 so that work items can be tracked across both repositories within Project1.

What should you do first?

**Select only one answer.**

- Add Repo2 to the GitHub connections for Project1.
- Add the GitHub SSH key to Project1.
- Move Repo1 to GitHub as a repository.
- Move Repo2 to Project1.

### Correct answer

**Add Repo2 to the GitHub connections for Project1.**

### Motivation

Repo1 is already an Azure Repos repository in Project1, so it does not require an additional connection. Repo2 must be added through **Project settings > GitHub connections** to enable Azure Boards integration.

| Option | Why it is correct or incorrect |
|---|---|
| **Add Repo2 to the GitHub connections for Project1** | **Correct.** It connects the existing GitHub repository to Azure Boards within Project1. |
| Add the GitHub SSH key to Project1 | Incorrect. SSH keys are for Git authentication or pipeline access, not Boards work-item integration. |
| Move Repo1 to GitHub | Incorrect. Azure Boards works with Azure Repos and GitHub repositories side by side; migration is unnecessary. |
| Move Repo2 to Project1 | Incorrect. The requirement is to integrate the existing GitHub repository, not migrate it to Azure Repos. |

### After connecting Repo2

Developers can use `AB#<work-item-id>` in Repo2 commits or pull requests to associate changes with work items in Project1.

---

## Question 16

### Question

You have an Azure DevOps project named Project1 that contains two branches named `main` and `branch1`.

You need to ensure that when `branch1` merges back into `main`, a pull request is created.

What should you do?

**Select only one answer.**

- Configure a branch policy for `branch1`.
- Configure a branch policy for `main`.
- Configure branch security for `branch1`.
- Configure branch security for `main`.

### Correct answer

**Configure a branch policy for `main`.**

### Motivation

Branch policies apply to the **target** branch of a pull request. To require changes from `branch1` to reach `main` only through a pull request, configure the branch policy on `main`.

| Option | Why it is correct or incorrect |
|---|---|
| **Configure a branch policy for `main`** | **Correct.** The policy applies to pull requests targeting `main`, requiring review before merge. |
| Configure a branch policy for `branch1` | Incorrect. It would govern pull requests whose target is `branch1`, not merges into `main`. |
| Configure branch security for `main` | Incorrect. Branch security controls permissions such as push and force-push, not the pull-request requirement itself. |
| Configure branch security for `branch1` | Incorrect. It controls access to `branch1`, not the merge process into `main`. |

### Configuration

1. Go to **Repos > Branches**.
2. Select `main`.
3. Open **Branch policies**.
4. Enable **Require a minimum number of reviewers**.
5. Set the required approvals.

---

## Question 17

### Question

You have a GitHub repository named Repo1 that contains the following branches:

- `main`
- `feature/feature1`
- `feature/feature2`
- `release/release1`

You discover that new commits in the `main` branch reference either `feature/feature1` or `feature/feature2` as their parent commit.

You need to configure a GitHub branch protection rule for `main` to ensure that future commits do NOT use a merge strategy.

Which rule should you apply to the branch protection configuration?

**Select only one answer.**

- Require a pull request before merging.
- Require linear history.
- Require signed commits.
- Require status checks to pass before merging.

### Correct answer

**Require linear history.**

### Motivation

Commits in `main` with feature branches as parents are merge commits. Enabling **Require linear history** prevents future merge commits from being pushed or merged into `main`; pull requests must use squash merge or rebase merge instead.

| Option | Why it is correct or incorrect |
|---|---|
| **Require linear history** | **Correct.** It explicitly blocks merge commits on the protected branch. |
| Require a pull request before merging | Incorrect. A pull request can still be merged with a merge commit. |
| Require signed commits | Incorrect. It verifies commit signatures but does not prevent merge commits. |
| Require status checks to pass before merging | Incorrect. It ensures CI checks pass but does not control merge strategy or commit topology. |

### Configuration

1. Create a branch protection rule for `main`.
2. Enable **Require linear history**.
3. Ensure the repository permits **Squash merging** or **Rebase merging**.

---

## Question 18

### Question

You have an Azure Repos repository named Repo1.

You plan to create a new branch named `branch1`.

You need to ensure that `branch1` starts from a commit of `3a1b2c4d`.

Which Git command should you use?

**Select only one answer.**

- `git branch branch1`
- `git branch branch1 3a1b2c4d`
- `git checkout -b branch1`
- `git checkout -b branch1 3a1b2c4d`

### Correct answer

**`git branch branch1 3a1b2c4d`**

### Motivation

The Git syntax `git branch <new-branch-name> <start-point>` creates a new branch pointing to the specified commit without changing the currently checked-out branch.

| Option | Why it is correct or incorrect |
|---|---|
| **`git branch branch1 3a1b2c4d`** | **Correct.** It creates `branch1` starting at the specified commit without switching to it. |
| `git branch branch1` | Incorrect. It creates `branch1` from the current `HEAD`, not the specified commit. |
| `git checkout -b branch1` | Incorrect. It creates and switches to `branch1` from the current `HEAD`. |
| `git checkout -b branch1 3a1b2c4d` | Incorrect for this requirement. It creates the branch from the specified commit but also switches the working directory to it. |

### Command

```bash
git branch branch1 3a1b2c4d
```

If you also need to begin working on `branch1` immediately, use:

```bash
git checkout -b branch1 3a1b2c4d
```

---

## Question 19

### Question

You have a GitHub repository named Repo1.

You need to implement a branching strategy that meets the following requirements:

- Uses short-lived branches
- Requires a code review before merging changes
- Merges branches into the `main` branch after the review

Which type of branching workflow should you use?

**Select only one answer.**

- centralized
- feature branch
- forking
- GitFlow

### Correct answer

**feature branch**

### Motivation

A feature-branch workflow creates a short-lived branch for each change, opens a pull request for code review, and merges the approved branch back into `main`.

| Option | Why it is correct or incorrect |
|---|---|
| **Feature branch** | **Correct.** It uses short-lived branches, pull-request review, and merge back to `main` after approval. |
| Centralized | Incorrect. Developers commit directly to a shared branch, so it does not inherently require review. |
| Forking | Incorrect. Contributors work in separate repository forks; it is typically used for open-source contributions and adds overhead. |
| GitFlow | Incorrect. It uses long-lived `develop`, `release`, and `hotfix` branches, conflicting with the short-lived branch requirement. |

### GitHub implementation

Protect `main` with a branch rule that requires pull requests and at least one approving review before merge.

---

## Question 20

### Question

You have an Azure DevOps project named Project1. Project1 has a build pipeline that runs weekly.

Last week’s build failed, but the team did NOT notice.

You need to monitor pipeline health and ensure visibility into build failures and trends over time.

What should you use?

**Select only one answer.**

- Analytics views in Azure DevOps
- Azure Monitor alerts for pipeline agents
- manual pipeline test report summaries
- GitHub Actions insights

### Correct answer

**Analytics views in Azure DevOps**

### Motivation

Analytics views provide historical pipeline reporting, including build pass/failure rates and trends over time. They allow the team to identify failed builds and recurring failure patterns rather than relying on someone noticing an individual run.

| Option | Why it is correct or incorrect |
|---|---|
| **Analytics views in Azure DevOps** | **Correct.** They provide pipeline pass-rate, failure, and trend reporting over time. |
| Azure Monitor alerts for pipeline agents | Incorrect. They monitor agent infrastructure and performance, not pipeline pass/failure trends. |
| Manual pipeline test report summaries | Incorrect. They are point-in-time reports, not ongoing health and trend monitoring. |
| GitHub Actions insights | Incorrect. They apply to GitHub Actions workflows, not Azure DevOps build pipelines. |

### Recommended dashboards

- **Build History** widget for recent build status.
- **Test Results Trend** widget for test outcomes.
- Pipeline **Analytics** tab for pass-rate and failure-trend reports.

---

## Question 21

### Question

You have a pipeline that builds and deploys an app.

You monitor the pipeline and notice that the build takes longer than expected to complete.

You need to recommend a solution to minimize the build time. The solution must minimize costs.

What should you recommend?

**Select only one answer.**

- Add an agent pool.
- Configure multiple jobs to run in parallel.
- Create a deployment group.
- Upgrade the Azure DevOps agent to a higher CPU.

### Correct answer

**Configure multiple jobs to run in parallel.**

### Motivation

Splitting independent build work into multiple jobs that run concurrently reduces total pipeline duration while using existing parallel-job capacity, avoiding the fixed cost of adding more compute capacity.

| Option | Why it is correct or incorrect |
|---|---|
| **Configure multiple jobs to run in parallel** | **Correct.** It reduces wall-clock build time by running independent work concurrently and minimizes additional cost. |
| Add an agent pool | Incorrect. It adds or reorganizes agent capacity but does not itself parallelize pipeline work. |
| Create a deployment group | Incorrect. It targets deployment to sets of servers; it does not reduce build duration. |
| Upgrade the Azure DevOps agent to a higher CPU | Incorrect. It may speed up one job but increases compute cost and does not exploit independent workloads. |

### Example

```yaml
jobs:
- job: BuildBackend
  steps:
  - script: dotnet build

- job: BuildFrontend
  steps:
  - script: npm run build

- job: UnitTests
  dependsOn: []
  steps:
  - script: dotnet test
```

Use parallel jobs only for genuinely independent work; keep dependent steps, such as publishing artifacts after all builds complete, sequential using `dependsOn`.

---

## Question 22

### Question

You receive a Smart Detection notification from Application Insights because the performance of an app has degraded.

What are three factors that can cause Smart Detection notifications to be raised?

**Select all answers that apply.**

- App dependencies are responding more slowly than usual.
- The app is responding to requests more slowly than usual.
- The app is using more memory than usual.
- Pages are loading slower on one type of browser.

### Correct answers

- **App dependencies are responding more slowly than usual.**
- **The app is responding to requests more slowly than usual.**
- **Pages are loading slower on one type of browser.**

### Motivation

Application Insights Smart Detection analyzes telemetry for performance anomalies, including dependency duration degradation, response-time degradation, and slow performance patterns affecting subsets of requests, such as a particular browser.

| Option | Why it is correct or incorrect |
|---|---|
| **App dependencies are responding more slowly than usual** | **Correct.** This is dependency duration degradation. |
| **The app is responding to requests more slowly than usual** | **Correct.** This is response-time degradation. |
| The app is using more memory than usual | Incorrect. Memory usage is not one of the three performance-degradation factors listed for this notification. |
| **Pages are loading slower on one type of browser** | **Correct.** This is a slow performance pattern affecting a subset of requests or client/browser types. |

### Additional detail

Smart Detection compares current telemetry with a historical baseline and requires sufficient telemetry volume—typically at least eight days—before raising performance notifications.

---

## Question 23

### Question

You have a globally distributed Azure web app named WebApp1 that is configured for Azure Application Insights.

You receive a Smart Detection-generated alert regarding an issue with WebApp1 that results in an exception every time users in Singapore open a specific page.

You need to verify whether the issue is limited to specific regions.

What should you do?

**Select only one answer.**

- Configure availability tests.
- Configure user flows.
- Modify the Smart Detection rules.
- Update the Application map components.

### Correct answer

**Configure availability tests.**

### Motivation

Application Insights availability tests can send recurring requests to WebApp1 from multiple geographic locations, including Singapore and other regions. Comparing results across locations determines whether the exception is regional or global.

| Option | Why it is correct or incorrect |
|---|---|
| **Configure availability tests** | **Correct.** They test the page from multiple geographic locations and report results by region. |
| Configure user flows | Incorrect. They analyze user navigation paths, not region-specific synthetic tests. |
| Modify the Smart Detection rules | Incorrect. This changes alerting behavior but does not validate regional behavior. |
| Update the Application map components | Incorrect. The Application Map visualizes dependencies and components but does not perform region-specific tests. |

### Recommended test configuration

1. Create a Standard availability test for the affected page.
2. Select Singapore plus representative regions, such as West Europe and East US.
3. Review per-location success, failure, and response-time results.
4. If only Singapore fails, investigate a regional issue; if all locations fail, investigate an application-wide defect.

---

## Question 24

### Question

You have an Azure subscription that contains a resource group named RG1. RG1 contains an Application Insights instance named Insight1.

Four users are assigned the following Azure roles:

| User | Azure role |
|---|---|
| User1 | Owner at the subscription scope |
| User2 | Monitoring Reader at the Insight1 scope |
| User3 | Automation Operator at the RG1 scope |
| User4 | Security Admin at the root management group scope |

Smart Detection notifications are enabled for a project.

Which user will receive Smart Detection notifications by default?

**Select only one answer.**

- User1
- User2
- User3
- User4

### Correct answer

**User1**

### Motivation

User1 has the **Owner** role at the subscription scope. Smart Detection email notifications are sent by default to users with the subscription-level **Owner**, **Contributor**, or **Reader** roles. Because the subscription scope includes RG1 and Insight1, User1 inherits the relevant role assignment for the Application Insights instance.

| User | Role and scope | Receives Smart Detection by default? |
|---|---|---|
| **User1** | **Owner** at subscription scope | **Yes.** Subscription Owner is a default recipient. |
| User2 | Monitoring Reader at Insight1 scope | No. The default role-based notification targets the subscription scope, not the Application Insights resource scope. |
| User3 | Automation Operator at RG1 scope | No. This role is not a default Smart Detection recipient. |
| User4 | Security Admin at root management group scope | No. This role is not a default Smart Detection recipient. |

### Important nuance

Microsoft is transitioning Smart Detection notifications so that, going forward, they go by default to users assigned **Monitoring Reader** or **Monitoring Contributor** at the subscription scope. However, under the current/default behavior described in the question, the subscription **Owner** receives the notification, making **User1** the correct choice.

To target only monitoring personnel, assign **Monitoring Reader** or **Monitoring Contributor** at the subscription scope, or configure specific addresses under the Smart Detection rule’s **Additional email recipients** setting.

---

## Missing question

The exam reference indicates **25 questions**, but only **24 questions** were provided in this conversation. Add the missing question, correct answer, motivation, and comparison table here once it is available.

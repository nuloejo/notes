# Cloud Hacking Scenarios

[Cloud Hacking Scenarios](https://awscommunityday.cz/2025/sessions/acd300/)
by [Michał Brygidyn](https://www.linkedin.com/in/michalbrygidyn/)

## Check the Source code

_When you know what are you looking for_

* Comments
* Javascript

_Sensitive data left in code_

## Scenario: Public GitHub repo - Office 365 - Jira

### Step 1. Public GitHub repo

* Config file with encrypted variables & Java class with a decrypt function **and secret key**

### Step 2. Office 365

1. Teams:
    - "Hello CxO :)"
2. SharePoint
    1. PDF with a Jira configuration guide
    2. ... including login and password

### Step 3. Jira

_Project "AWS":_

- Task to create IAM User for an external service
- Plaintext AWS Access and Secret keys in comments

### What went wrong?

1. Hardcoded sensitive data
    1. Config files
    2. Encryption keys
    3. Git history
2. Bad tools selection
    1. Public repository
    2. Risky credentials sharing
3. Lack of security awareness
    1. To many viewers
    2. Valid credentials in documents

## Scenario: Symfony Profiler - Internal Apps - AWS

### Step 1. Symfony Profiler

_PHP Profiler_

* Plaintext credentials in Server Parameters
* Plaintext credentials in Requests history
* parameters.yml preview

#### Env Parameters

```shell
AWS_S3_KEY="AKIA*********"
```

#### POST Parameters

```shell
_csrf_token="xxxx"
login="qwdw"
password="asdas"
```

### Step 2. Internal app

1. Admin credentials
    * Dev Environment
    * Prod Environment
2. SSO to multiple apps:
    * Production CRM
    * Webmail

### Step 3. Webmail

1. AWS Invoices & Trusted Advisor emails
2. Reset password for AWS Root account

### Step 4. AWS Root Account

- No MFA
- Organization Management Account
- Administrator Access on all member accounts
- :)

### What Went wrong?

1. Prod data on a non-prod env
    * prod database on a non-prod
    * Same credentials across multiple environment
    * A single cloud subscription for all envs / apps / clients
2. Critical services using the same shared email
3. No MFA

## Scenario: Kubernetes

### Step 1. Kubernetes API

_A publicly exposed Kubernetes API with disabled RBAC_

* Base64 Secrets
* Plaintext ConfigMaps
* Pods list and configurations

### Step 2. K8s Secrets

1. AWS Access Keys:
    * S3 access only
2. Jenkins admin credentials

### Step 3. Jenkins app

1. AWS Access Keys in different Workspaces
    * SQS Access
    * Lambda access
2. GitHub credentials in Jenkins Credentials
3. AWS CLI calls in jobs console logs

### What went wrong?

* Public resources
    * Lack of knowledge
    * Limited scope of penetration testing
    * Risky design
* Disabled security features
    * No RBAC
    * Unencrypted data
    * No firewall
* Principle of Least Privilege
    * Admin access for all!
    * Unprotected CICD tools
    * Running apps as Root

## Other ways "in"

* Outdated software running on cloud servers (with open proxy)
* Admin credentials logged in during installation
* Misconfigured vhosts -> Directory indexing

```html
<h1> Index of / </h1>
<ul>
    <li>.env</li>
    ...

</ul>
```

## AWS Backdoors - Ideas

### Group 1: IAM

* IAM Users
* Trust Policy
* Identity Providers

### Group 2: Servers

* Public EC2
* Local OS User

### Group 3: Network

### Group 4: Services

* Identity Center
* CodePipeline
* Lambda Function URL

## Hide and seek

### Self-Healing

* EventBridge
* StepFunction
* EC2 OS cron
* CloudTrail

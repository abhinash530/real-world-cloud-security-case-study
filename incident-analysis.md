# Capital One 2019 Incident — Detailed Technical Analysis

## 1. Incident Timeline

| Date | Event |
|---|---|
| March 22–23, 2019 | Unauthorized access to Capital One's cloud environment occurred. |
| July 17, 2019 | An external security researcher reported the vulnerability to Capital One. |
| July 19, 2019 | Capital One determined that unauthorized access had occurred and contacted the FBI. |
| July 29, 2019 | Capital One publicly announced the incident and the suspected attacker was arrested. |

Capital One stated that the unauthorized access occurred on March 22 and 23, 2019. The company discovered the incident after receiving a report through its responsible disclosure program.

## 2. Attack Vector

The incident involved a configuration vulnerability in Capital One's cloud infrastructure.

According to the U.S. Department of Justice, the intrusion occurred through a misconfigured web application firewall (WAF). The configuration allowed an attacker to send requests through the vulnerable application infrastructure and reach resources that should not have been accessible.

The attack is commonly described as involving a Server-Side Request Forgery (SSRF) technique. The attacker was able to make requests from the application environment and obtain credentials associated with a cloud role.

The sequence can be summarized as:

1. Identify a vulnerable public-facing application.
2. Exploit the application's SSRF vulnerability.
3. Reach the cloud instance metadata service.
4. Obtain temporary credentials associated with an IAM role.
5. Use those credentials to make authenticated cloud API requests.
6. Enumerate available storage locations.
7. Access data from storage resources for which the compromised role had permissions.
8. Copy/exfiltrate sensitive information.

This demonstrates how an application-layer vulnerability can become a cloud-identity and data-access problem when the compromised identity has broader permissions than necessary.

## 3. IAM and Credential Exposure

A critical part of the incident was the use of temporary cloud credentials associated with the vulnerable application environment.

Cloud workloads commonly use IAM roles so that applications can obtain temporary credentials without storing long-term access keys. However, temporary credentials can still be abused if an attacker is able to obtain them through a vulnerable application.

The security issue therefore was not simply the existence of temporary credentials. The greater concern was that the compromised role had permissions that allowed the attacker to enumerate and access storage resources.

This illustrates the importance of the principle of least privilege:

- A workload should receive only the permissions required for its function.
- Access should be limited to specific resources.
- Sensitive data should not be broadly accessible to application roles.
- IAM permissions should be reviewed continuously.
- Credentials obtained through an exploited workload should have minimal potential impact.

## 4. Cloud Storage Exposure

The compromised credentials were used to identify storage locations and access data.

Court documents referenced the execution of commands that obtained credentials, listed or enumerated folders or buckets, and extracted data from certain storage locations.

The investigation also identified more than 700 folders or buckets in a file containing storage information associated with Capital One.

The incident therefore demonstrates a key cloud security principle:

> Authentication alone does not provide sufficient security. Authorization must also restrict what an authenticated identity can access.

A properly configured storage environment should use resource-specific permissions, encryption, logging, monitoring, and strong separation between application resources and highly sensitive information.

## 5. Data Affected

Capital One reported that approximately:

- 100 million individuals in the United States were affected.
- 6 million individuals in Canada were affected.
- Approximately 140,000 U.S. Social Security numbers were compromised.
- Approximately 80,000 linked bank account numbers of secured credit card customers were compromised.
- Approximately 1 million Canadian Social Insurance Numbers were compromised.

Other accessed information included names, addresses, postal/ZIP codes, phone numbers, email addresses, dates of birth, self-reported income, credit scores, credit limits, balances, payment history, contact information, and fragments of transaction data.

Capital One stated that credit card account numbers and login credentials were not compromised.

## 6. Technical Root Causes

The incident was not caused by a single isolated weakness. Several security conditions contributed to the overall impact.

### 6.1 Web Application Configuration Weakness

A misconfigured web application firewall contributed to the ability to exploit the application environment.

### 6.2 SSRF Exposure

The application could be abused to make requests to internal cloud resources.

### 6.3 Excessive IAM Permissions

The compromised workload identity had permissions that enabled access to storage resources containing sensitive information.

### 6.4 Insufficient Segmentation

The application environment had a path to resources containing sensitive data that should have been more strongly isolated.

### 6.5 Detection and Monitoring Gaps

The unauthorized activity was not identified immediately through automated security detection. Capital One ultimately learned about the vulnerability through an external report.

## 7. Business and Technical Impact

### Technical Impact

The incident resulted in unauthorized access to a large volume of customer and applicant information stored in the cloud environment.

The attacker was able to use cloud credentials to enumerate storage resources and copy data.

### Business Impact

The incident created significant costs associated with:

- Customer notification
- Credit monitoring
- Identity protection
- Technology remediation
- Professional cybersecurity support
- Legal and regulatory response
- Investigation and incident response

Capital One initially estimated approximately $100 million to $150 million in incremental 2019 costs associated with the incident.

The incident also resulted in regulatory enforcement, litigation, settlements, and reputational consequences.

## 8. Security Controls That Could Have Reduced the Impact

### 8.1 Web Application Firewall Hardening

The WAF and associated application configuration should be continuously tested for SSRF and related vulnerabilities.

Recommended controls:

- Restrict outbound requests from public-facing applications.
- Block access to cloud instance metadata endpoints where possible.
- Use modern metadata-service protections such as IMDSv2 for EC2 workloads.
- Apply strict allowlists for application outbound traffic.
- Perform regular penetration testing.

### 8.2 Least-Privilege IAM

The application role should have access only to the exact resources required by the application.

For example:

```text
Bad:
Application Role
    ↓
Broad access to multiple storage buckets

Better:
Application Role
    ↓
Read-only access
    ↓
Specific required bucket
    ↓
Specific required prefix

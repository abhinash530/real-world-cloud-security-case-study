# Affected Cloud Services and Security Weaknesses

## 1. Purpose

This document identifies the cloud services, application components, identities, and security controls relevant to the Capital One 2019 cybersecurity incident.

The purpose is to connect the technical attack path with the security weaknesses that allowed the incident to have a large impact.

---

## 2. Affected Components

| Component | Role in the Incident | Security Concern |
|---|---|---|
| Public-facing web application | Entry point used to exploit the application environment | Application vulnerability |
| Web Application Firewall (WAF) | Security layer associated with the vulnerable application | Misconfiguration |
| AWS compute environment | Hosted the application and associated cloud identity | Metadata/credential exposure |
| EC2 instance metadata service | Potential source of temporary role credentials | SSRF risk |
| IAM role | Provided temporary AWS credentials to the workload | Excessive permissions |
| Amazon S3 | Stored sensitive customer/application data | Unauthorized data access |
| Cloud API | Used with obtained credentials | Credential abuse and reconnaissance |
| Logging and monitoring systems | Required for detecting suspicious activity | Detection challenge |

---

## 3. Web Application Firewall

The U.S. Department of Justice described the intrusion as involving a misconfigured web application firewall.

A WAF is intended to inspect and control HTTP/HTTPS traffic before requests reach an application. It can provide protection against common web attacks and enforce application-specific security rules.

In this incident, the WAF configuration did not prevent the attack path that was used to reach internal cloud resources.

### Security weakness

A WAF should not be treated as the only security boundary.

Recommended controls include:

- Regular WAF rule review
- Application penetration testing
- SSRF testing
- Egress filtering
- Denial of access to internal administrative endpoints
- Continuous security configuration assessment

---

## 4. Server-Side Request Forgery (SSRF)

Server-Side Request Forgery occurs when an attacker can cause a server-side application to send requests to destinations selected by the attacker.

In a cloud environment, SSRF can be particularly dangerous because internal endpoints may provide access to metadata or temporary credentials.

A simplified attack path is:

```text
Attacker
   |
   v
Public Web Application
   |
   | SSRF
   v
Internal Cloud Endpoint
   |
   v
Temporary IAM Credentials
   |
   v
AWS API
   |
   v
Cloud Storage
   |
   v
Sensitive Data

# Capital One 2019 — Incident Timeline and Evidence

## 1. Purpose

This document provides a chronological timeline and evidence-based summary of the Capital One 2019 cybersecurity incident.

The timeline is based primarily on U.S. Department of Justice documents and Capital One's regulatory filings with the U.S. Securities and Exchange Commission (SEC).

---

## 2. Incident Timeline

| Date | Event | Significance |
|---|---|---|
| March 22, 2019 | Unauthorized access activity began | Start of the later-identified intrusion |
| March 23, 2019 | Additional unauthorized access occurred | Attacker continued accessing cloud resources |
| July 17, 2019 | Capital One received a responsible-disclosure report | External researcher reported the suspected vulnerability |
| July 19, 2019 | Capital One determined that unauthorized access had occurred | Incident investigation began |
| July 19, 2019 | Capital One contacted the FBI | Law-enforcement investigation started |
| July 29, 2019 | Capital One publicly announced the incident | Customers and the public were informed |
| July 29, 2019 | Suspected attacker was arrested | Federal investigation became public |

---

## 3. Initial Access

The attack involved a public-facing application environment associated with Capital One's AWS infrastructure.

According to the U.S. Department of Justice, the attacker exploited a misconfigured web application firewall.

The vulnerability provided an attack path that enabled requests to reach internal resources that should not have been accessible from the application's normal operating context.

---

## 4. SSRF Attack Path

The attack is associated with Server-Side Request Forgery (SSRF).

A simplified representation is:

```text
Internet
   |
   v
Public-Facing Application
   |
   v
SSRF Vulnerability
   |
   v
Internal AWS Resource
   |
   v
Temporary IAM Credentials
   |
   v
AWS API Requests
   |
   v
Storage Enumeration
   |
   v
Sensitive Data Access

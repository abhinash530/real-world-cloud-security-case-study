# Security Controls and Preventive Recommendations

## 1. Purpose

This document evaluates the security controls that could have prevented the Capital One 2019 incident or significantly reduced its impact.

The recommendations are mapped to the actual attack chain:

```text
Application Vulnerability
        ↓
SSRF
        ↓
Cloud Credential Access
        ↓
IAM Authorization
        ↓
Storage Enumeration
        ↓
Sensitive Data Access

# Sources and Evidence Matrix

## 1. Purpose

This document identifies the authoritative sources used for the Capital One 2019 cloud security case study and maps important claims to supporting evidence.

Priority was given to primary and authoritative sources, including U.S. Department of Justice records, U.S. Securities and Exchange Commission filings, and official AWS documentation.

---

## 2. Evidence Matrix

| Claim / Finding | Evidence | Primary Source |
|---|---|---|
| Unauthorized access occurred on March 22–23, 2019 | Capital One reported the dates of unauthorized access | Capital One SEC filing |
| Capital One discovered the incident on July 19, 2019 | Incident was identified after an external report | Capital One SEC filing |
| FBI was contacted on July 19, 2019 | Capital One reported the incident to law enforcement | Capital One / DOJ records |
| Public announcement occurred July 29, 2019 | Capital One publicly disclosed the incident | Capital One SEC filing |
| Misconfigured WAF was involved | DOJ described the web application firewall configuration issue | U.S. Department of Justice |
| SSRF was involved in the attack path | Court/DOJ records describe exploitation of the vulnerable application environment | U.S. Department of Justice |
| Temporary cloud credentials were obtained | Investigation records describe access to credentials associated with a cloud role | U.S. Department of Justice |
| Cloud storage resources were enumerated | Investigation records describe discovery and enumeration of storage resources | U.S. Department of Justice |
| Sensitive information was accessed | Capital One documented categories of affected information | Capital One SEC filing |
| Approximately 100 million U.S. individuals were affected | Capital One reported the affected population | Capital One SEC filing |
| Approximately 6 million Canadian individuals were affected | Capital One reported the affected population | Capital One SEC filing |
| Approximately 140,000 Social Security numbers were affected | Capital One reported the figure | Capital One SEC filing |
| Approximately 80,000 linked bank account numbers were affected | Capital One reported the figure | Capital One SEC filing |
| Approximately 1 million Canadian Social Insurance Numbers were affected | Capital One reported the figure | Capital One SEC filing |
| Credit card account numbers were not compromised | Capital One stated this in its disclosure | Capital One SEC filing |
| Login credentials were not compromised | Capital One stated this in its disclosure | Capital One SEC filing |
| Incident-related costs were significant | Capital One disclosed estimated incremental costs | Capital One SEC filing |

---

## 3. Primary Sources

### Source 1 — U.S. Department of Justice

**United States v. Paige Thompson**

This source provides information concerning the federal investigation and criminal case associated with the Capital One intrusion.

https://www.justice.gov/usao-wdwa/united-states-v-paige-thompson

### Source 2 — U.S. Department of Justice

**Seattle Tech Worker Arrested for Data Theft Involving Large Financial Services Company**

This source provides information about the investigation, attack mechanism, and alleged unauthorized access.

https://www.justice.gov/usao-wdwa/pr/seattle-tech-worker-arrested-data-theft-involving-large-financial-services-company

### Source 3 — U.S. Securities and Exchange Commission

**Capital One Financial Corporation — 2019 Form 10-K**

This filing provides company-reported information about the incident, affected individuals, categories of information, costs, and remediation.

https://www.sec.gov/Archives/edgar/data/927628/000092762820000102/cof-12312019x10k.htm

### Source 4 — U.S. Securities and Exchange Commission

**Capital One Financial Corporation — 2019 Form 10-Q**

This filing provides additional information concerning the cybersecurity incident and its financial impact.

https://www.sec.gov/Archives/edgar/data/927628/000092762819000312/cof-09302019x10q.htm

---

## 4. AWS Technical References

### IAM Best Practices

AWS recommends applying least-privilege permissions and regularly reviewing access.

https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html

### EC2 Instance Metadata

AWS documentation describing the EC2 instance metadata service and metadata access.

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html

### Amazon S3 Security

AWS documentation covering security controls for Amazon S3.

https://docs.aws.amazon.com/AmazonS3/latest/userguide/security-best-practices.html

### AWS CloudTrail

AWS documentation describing CloudTrail and AWS API activity logging.

https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-user-guide.html

### Amazon GuardDuty

AWS documentation describing threat detection capabilities.

https://docs.aws.amazon.com/guardduty/latest/ug/what-is-guardduty.html

---

## 5. Source Reliability

The sources were selected using the following priority:

```text
Primary Government Records
        ↓
SEC Regulatory Filings
        ↓
Official AWS Documentation
        ↓
Secondary Sources

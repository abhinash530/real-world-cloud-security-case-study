# Real-World Cloud Security Case Study: Capital One 2019

## 1. Case Study Overview

This repository analyzes the 2019 Capital One cloud security incident, one of the major real-world examples of a cloud configuration vulnerability leading to unauthorized access to sensitive information.

The incident occurred on March 22 and 23, 2019, and Capital One determined the unauthorized access on July 19, 2019. The company publicly announced the incident on July 29, 2019.

The incident involved infrastructure hosted on Amazon Web Services (AWS). According to the U.S. Department of Justice, the intrusion occurred through a misconfigured web application firewall that enabled access to stored data.

## 2. Incident Impact

The incident affected approximately:

- 100 million individuals in the United States
- 6 million individuals in Canada
- Approximately 140,000 Social Security numbers of U.S. credit card customers
- Approximately 80,000 linked bank account numbers of secured credit card customers
- Approximately 1 million Canadian Social Insurance Numbers

The exposed information also included names, addresses, postal/ZIP codes, phone numbers, email addresses, dates of birth, self-reported income, credit scores, credit limits, balances, payment history, and portions of transaction data.

Capital One stated that no credit card account numbers or login credentials were compromised.

## 3. Attack Vector and Root Cause

The attacker exploited a configuration vulnerability involving a web application firewall.

The vulnerability allowed the attacker to gain unauthorized access to resources associated with the cloud environment. The incident demonstrates how a cloud service can be securely designed at the infrastructure level but still become vulnerable when application-layer configuration and access controls are not properly secured.

The incident also demonstrates the importance of limiting permissions granted to cloud identities and continuously monitoring unusual access.

## 4. Affected Cloud and Security Components

The case involved several important cloud-security concepts:

- Amazon Web Services (AWS) cloud infrastructure
- Web application firewall configuration
- Cloud-based data storage
- IAM permissions and temporary credentials
- Network and application-layer security
- Sensitive customer data
- Logging, monitoring, and incident response

## 5. Security Weaknesses

The major weaknesses highlighted by the incident include:

1. Misconfiguration of a web application firewall.
2. Excessive access available through the exploited cloud identity.
3. Insufficient restriction of access to sensitive data.
4. Need for stronger continuous monitoring and automated detection.
5. Need for continuous vulnerability and configuration assessment.
6. Insufficient defense-in-depth controls around sensitive cloud resources.

## 6. Security Controls That Could Reduce the Risk

The following controls could reduce the likelihood or impact of a similar incident:

### Identity and Access Management

- Apply least-privilege IAM policies.
- Restrict permissions to only the resources and actions required.
- Regularly review IAM roles and permissions.
- Use short-lived credentials wherever possible.

### Network and Application Security

- Properly configure and continuously test web application firewalls.
- Restrict access to internal metadata and administrative endpoints.
- Use multiple layers of network and application security controls.
- Regularly test security configurations.

### Data Protection

- Encrypt sensitive data at rest and in transit.
- Apply strict bucket and object-level access controls.
- Prevent unnecessary public access.
- Separate sensitive data from application-facing resources.

### Logging and Monitoring

- Enable comprehensive cloud audit logging.
- Monitor authentication, authorization, and data-access events.
- Create alerts for suspicious API activity.
- Continuously review security logs and configuration changes.

### Vulnerability and Configuration Management

- Perform continuous vulnerability scanning.
- Use automated cloud configuration assessment.
- Test infrastructure changes before deployment.
- Remediate high-risk configuration weaknesses quickly.

## 7. Lessons Learned

The Capital One incident demonstrates that cloud security is a shared responsibility. Using a major cloud provider does not automatically make an application or data environment secure.

Security must be implemented at multiple layers, including identity, network configuration, application security, data protection, monitoring, and incident response.

The incident also demonstrates the importance of continuous security assessment. A configuration that appears acceptable at deployment can become a serious security risk if it is not continuously tested and monitored.

## 8. Key Metrics

| Metric | Value |
|---|---:|
| Incident date | March 22–23, 2019 |
| Discovery by Capital One | July 19, 2019 |
| Public announcement | July 29, 2019 |
| U.S. individuals affected | Approximately 100 million |
| Canadian individuals affected | Approximately 6 million |
| U.S. Social Security numbers initially reported | Approximately 140,000 |
| Linked bank account numbers | Approximately 80,000 |
| Canadian Social Insurance Numbers | Approximately 1 million |

## 9. Sources

1. U.S. Department of Justice — Capital One intrusion and investigation:
   https://www.justice.gov/usao-wdwa/pr/seattle-tech-worker-arrested-data-theft-involving-large-financial-services-company

2. U.S. Department of Justice — United States v. Paige Thompson:
   https://www.justice.gov/usao-wdwa/united-states-v-paige-thompson

3. Capital One / U.S. SEC filing — 2019 Cybersecurity Incident:
   https://www.sec.gov/Archives/edgar/data/927628/000092762820000102/cof-12312019x10k.htm

4. Capital One / SEC filing — Cybersecurity Incident details:
   https://www.sec.gov/Archives/edgar/data/927628/000092762819000312/cof-09302019x10q.htm

## 10. Conclusion

The Capital One 2019 incident provides an important practical example of how a cloud configuration weakness can lead to unauthorized access to sensitive information.

The key lesson is that effective cloud security requires defense in depth. Strong IAM controls, secure application and network configuration, data protection, continuous monitoring, vulnerability management, and timely incident response must work together to reduce both the probability and impact of cloud security incidents.

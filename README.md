# AWS Cloud Governance & Compliance Platform

## Overview

AWS Cloud Governance & Compliance Platform is a serverless AWS solution that automatically scans cloud resources for security, compliance, and cost optimization issues.

The platform performs scheduled governance checks, stores findings in DynamoDB, sends real-time email alerts using SNS, and provides a live dashboard for monitoring cloud health.

---

## Key Features

### Security Monitoring

* Detects publicly exposed Security Groups
* Identifies IAM users without MFA enabled
* Monitors potentially public S3 buckets

### Cost Optimization

* Detects stopped EC2 instances
* Identifies unattached EBS volumes
* Highlights unused cloud resources

### Automated Governance

* Scheduled scans using Amazon EventBridge
* Automated notifications through Amazon SNS
* Governance score calculation
* Findings storage in Amazon DynamoDB

### Dashboard & Reporting

* Live dashboard hosted on Amazon S3
* Real-time findings visualization
* Severity distribution charts
* Governance score tracking
* API-driven architecture using Amazon API Gateway

---

## AWS Services Used

| Service            | Purpose                             |
| ------------------ | ----------------------------------- |
| AWS Lambda         | Governance scanning and API backend |
| Amazon DynamoDB    | Findings storage                    |
| Amazon SNS         | Email notifications                 |
| Amazon EventBridge | Scheduled governance scans          |
| Amazon API Gateway | Dashboard API                       |
| Amazon S3          | Dashboard hosting                   |
| Amazon EC2         | Resource auditing                   |
| AWS IAM            | User and MFA auditing               |
| Amazon CloudWatch  | Logs and monitoring                 |
| Python (Boto3)     | AWS automation                      |

---

## Architecture

```text
                    EventBridge
                         │
                         ▼
             GovernanceScanner Lambda
                         │
       ┌─────────────────┼─────────────────┐
       ▼                 ▼                 ▼
      EC2               EBS         Security Groups
                         │
                         ▼
                    Findings
                         │
                         ▼
                     DynamoDB
                         │
                         ▼
              GovernanceAPI Lambda
                         │
                         ▼
                   API Gateway
                         │
                         ▼
                  S3 Dashboard
                         │
                         ▼
                        Users

                         │
                         ▼
                        SNS
                         │
                         ▼
                   Email Alerts
```

---

## Governance Checks Implemented

### EC2 Monitoring

* Stopped EC2 Instance Detection

### Security Group Monitoring

* Open Security Group Detection
* Unrestricted Inbound Access Detection (0.0.0.0/0)

### EBS Monitoring

* Unattached EBS Volume Detection

### IAM Monitoring

* MFA Compliance Verification

### S3 Monitoring

* Public Bucket Access Verification

---

## Governance Score Formula

```text
Score = 100 - (High Severity × 20) - (Medium Severity × 10)
```

### Example

```text
High Findings = 2
Medium Findings = 4

Score = 100 - 40 - 40 = 20
```

---

## Dashboard Features

* Real-time governance monitoring
* Auto-refresh every 30 seconds
* Governance score visualization
* Severity distribution chart
* Findings table
* Live API integration

---

## Sample Alert

```text
AWS CLOUD GOVERNANCE REPORT

Governance Score: 70/100

Total Findings: 3

Detected Issues:
- Open Security Group
- Stopped EC2 Instance
- Unattached EBS Volume

Recommendations:
- Restrict Security Group access
- Remove unused EBS volumes
- Review stopped EC2 instances
```

---

## Screenshots

Add the following screenshots:

* dashboard.png
* architecture-diagram.png
* lambda-success.png
* dynamodb-findings.png
* sns-alert.png
* api-gateway-response.png
* eventbridge-schedule.png

---

## Future Enhancements

* CloudWatch Metrics Integration
* Cost Estimation Dashboard
* Auto Remediation Workflows
* Multi-Account Governance Scanning
* Compliance Reporting
* Trend Analytics

---

## Author

**Midhun Balachandran**

AWS Cloud Governance & Compliance Platform

Built using AWS Serverless Services and Python (Boto3).

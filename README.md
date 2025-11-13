# AWS Serverless Cost Optimization

![AWS](https://img.shields.io/badge/AWS-FF9900?style=flat-square&logo=amazon-aws&logoColor=white)
![Lambda](https://img.shields.io/badge/Lambda-FF9900?style=flat-square&logo=aws-lambda&logoColor=white)
![Make.com](https://img.shields.io/badge/Make.com-6B46FF?style=flat-square&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)

## 📋 What This Project Does

An event-driven serverless application that automatically detects AWS resources wasting money and sends alerts through multiple channels using Make.com automation.

**The Problem:** AWS resources left running idle waste money (unused EC2 instances, unattached volumes, old snapshots)

**The Solution:** Automated daily checks that find waste and alert the team immediately via Slack, Email, and more

## 🎯 How It Works
```
Step 1: EventBridge triggers Lambda function daily at 9 AM
    ↓
Step 2: Lambda scans AWS account for:
    • Idle EC2 instances (low CPU usage)
    • Unattached EBS volumes
    • Old snapshots (>90 days)
    • Unused Elastic IPs
    ↓
Step 3: Lambda calculates potential savings
    ↓
Step 4: Sends data to Make.com webhook
    ↓
Step 5: Make.com distributes alerts:
    • Slack notification
    • Email report
    • Google Sheets logging
    • Jira ticket creation
```

## ✨ Key Features

**Automated Detection:**
- 💻 Idle EC2 instances (CPU < 5% for 7+ days)
- 💾 Unattached EBS volumes
- 📸 Old EBS snapshots (>90 days)
- 🔍 Unused Elastic IPs

**Smart Alerting via Make.com:**
- 🔔 Slack alerts with recommendations
- 📧 Detailed email reports
- 📊 Automatic Google Sheets logging
- 🎫 Jira ticket creation for cleanup

**Cost Tracking:**
- Calculates monthly savings potential
- Tracks optimization over time

## 🏗️ Architecture
```
┌─────────────────────────────────────────┐
│   AWS EventBridge (Scheduler)           │
│   Triggers daily at 9 AM UTC            │
└──────────────┬──────────────────────────┘
               │
               ↓
┌──────────────▼──────────────────────────┐
│   Lambda Function (Python)              │
│                                         │
│   • Scan EC2 instances                  │
│   • Check EBS volumes                   │
│   • Analyze snapshots                   │
│   • Calculate savings                   │
└──────────────┬──────────────────────────┘
               │
               ↓ HTTP POST
               │
┌──────────────▼──────────────────────────┐
│   Make.com Automation                   │
│                                         │
│   → Slack alert                         │
│   → Email report                        │
│   → Google Sheets log                   │
│   → Jira ticket                         │
└─────────────────────────────────────────┘
```

## 📊 Example Output

**Slack Alert:**
```
💰 AWS Cost Optimization Report - Jan 15, 2025

Found 5 optimization opportunities:

💻 EC2 Instances (3 idle):
   • i-abc123 - Idle 8 days
   • i-def456 - Idle 12 days
   • i-ghi789 - Idle 5 days
   Savings: $180/month

💾 EBS Volumes (2 unattached):
   • vol-xyz111 (100 GB)
   • vol-xyz222 (50 GB)
   Savings: $15/month

📸 Old Snapshots (15 found):
   Savings: $12/month

Total Potential Savings: $207/month

🔗 View details | 🎫 Ticket created
```

## 🛠️ Technologies Used

**AWS Services:**
- Lambda - Serverless compute
- EventBridge - Event scheduling
- IAM - Access management
- CloudWatch - Logging

**Integration:**
- Make.com - Workflow automation
- Python (Boto3) - AWS SDK
- Slack API - Notifications
- Google Sheets API - Data tracking

## 💡 Why I Built This

**Learning Goals:**
- Practice AWS Lambda serverless development
- Learn event-driven architecture with EventBridge
- Integrate Make.com for multi-channel automation
- Apply cost optimization and FinOps principles
- Build real-world AWS automation

## 📦 Project Structure
```
aws-cost-optimization/
├── README.md
├── lambda/
│   ├── cost_optimizer.py
│   ├── requirements.txt
│   └── iam_policy.json
├── terraform/
│   ├── main.tf
│   ├── lambda.tf
│   └── eventbridge.tf
└── docs/
    ├── setup_guide.md
    └── screenshots/
```

## 🎓 Skills Demonstrated

- AWS Lambda serverless development
- Event-driven architecture
- Python automation with Boto3
- IAM security policies
- Make.com workflow automation
- Multi-service API integration
- Cost optimization (FinOps)

## 🔮 Future Ideas

- Auto-stop idle instances
- Multi-region support
- ML-based anomaly detection
- Grafana dashboard
- Custom tagging exceptions

---

**Built as a personal project to learn AWS serverless patterns and workflow automation.**

📧 sreenathreddybokkalapally@gmail.com  
💼 [linkedin.com/in/sreenathreddy5](https://linkedin.com/in/sreenathreddy5)

⭐ Star if helpful!

Виконав самостійно Шевченко Артем РПЗ 24-А

## 1. Fundamental Ideas and Terminology (from Lesson 1)

### Primary Service Groups
- **Computing**: EC2, Lambda, Elastic Beanstalk.
- **Storage**: S3, EBS, Glacier.
- **Databases**: RDS, DynamoDB, Aurora.
- **Networking & Content Distribution**: VPC, Route 53, CloudFront.
- **Security, Identity & Compliance**: IAM, KMS, Shield.
- **Governance & Oversight**: CloudWatch, CloudTrail, AWS Config.

### Essential Terminology
- **Region**: A specific geographic location hosting AWS resources (e.g., us-east-1).
- **Availability Zone**: Separate facilities within a region designed for enhanced reliability.
- **Elasticity**: The capacity to dynamically adjust resources according to workload needs.
- **Pay-per-Use**: A pricing approach where charges apply only to actual consumption.
- **AWS Free Tier**: Introductory free usage allowances for new accounts to explore services.

## 2. Role of MFA and Setup Process (from Lesson 2)

MFA (Multi-Factor Authentication) enhances AWS account protection by incorporating an additional verification step alongside username and password, like a time-sensitive code or physical token.

### Installation Approaches
1. **Virtual MFA Device**: Leverage apps such as Google Authenticator, Authy, or AWS Virtual MFA to produce codes.
2. **Hardware MFA Token**: Use a physical gadget like YubiKey to create one-time passcodes.
3. **U2F/FIDO2 Security Key**: Contemporary USB device for hardware-supported verification.

### Setup Procedure
- AWS Console → IAM → Users → [Choose User] → Security credentials → Assign MFA device.
- Scan the QR code using your MFA application and input the produced codes for confirmation.

## 3. Function of Amazon Budgets and Available Settings (from Lesson 2)

Amazon Budgets assists in overseeing and tracking AWS expenditures by defining thresholds and notifications to avoid surprise charges.

### Setting Options
- **Cost Budget**: Caps on overall expenses (e.g., notification if monthly costs surpass $100).
- **Usage Budget**: Monitoring of resource consumption (e.g., EC2 instance runtime hours).
- **Reservation Budget**: Oversight of reserved instances to maximize efficiency.
- **Savings Plans Budget**: Evaluation of savings plan usage for discounted committed workloads.

Configuration: AWS Console → Billing → Budgets → Create budget.

## 4. Objective of IAM Policies and Permission Assignment (from Lesson 2)

An IAM Policy consists of a JSON file outlining permissions for users, groups, or roles, detailing permitted or prohibited operations on AWS assets.

### Permission Configuration Method
- Generate a user in IAM.
- Link policies (directly, through a group, or by replicating from an existing user).
- Specify core components:
  - **Action**: Particular AWS operations (e.g., "s3:GetObject").
  - **Resource**: Targeted AWS elements (e.g., "arn:aws:s3:::my-bucket/*").
  - **Effect**: Allow or Deny.

Adhere to the Least Privilege Principle: Provide only essential access levels.

## 5. Methods for Incorporating IAM Policies During User Creation

1. **Direct Attachment of Existing Policies**: Apply pre-built AWS-managed policies (e.g., AdministratorAccess).
2. **User  Addition to Group**: Place the user in an IAM group with pre-attached policies.
3. **Permission Duplication from Existing User**: Replicate access rights from another user at creation time.
4. **Custom Policy Attachment**: Develop and link a personalized JSON policy for customized control.

## 6. Drafting and Implementing IAM Policies (from Lesson 3)

IAM policies are composed in JSON format and assigned to users, groups, or roles to enable or limit access, in line with the Least Privilege Principle.

### Sample JSON Layout
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["s3:ListBucket", "s3:GetObject"],
      "Resource": ["arn:aws:s3:::example-bucket/*"]
    }
  ]
}
```

- Creation: AWS Console → IAM → Policies → Create policy.
- This sample permits bucket listing and object retrieval from a designated S3 bucket.

## 7. IAM Role Switching (from Lesson 3)

The Switch Role feature enables temporary assumption of another IAM role without logout, facilitating secure navigation between AWS accounts or setups.

### Procedure
- AWS Console → [Username in upper-right corner] → Switch Role → Input Account ID and Role Name → Switch.

### Advantages
- Secure handling of multiple accounts (e.g., development and production).
- Eliminates the need for credential sharing or persistent keys.
- Offers detailed access management and logging capabilities.

## 8. Permissions Boundary (from Lesson 3)

A Permissions Boundary serves as an IAM advanced tool that defines the upper limit of permissions for IAM entities (users or roles), functioning as a safety constraint.

### Application Scenarios
- Safe delegation of admin tasks without root-level privileges.
- Restriction of access for novice administrators or service roles.
- Mitigation of privilege escalation by enforcing policy limits.

Attachment: IAM → Users/Roles → Permissions boundary → Choose policy.

## 9. Monitoring Actions with AWS CloudTrail (from Lesson 3)

AWS CloudTrail logs all user interactions, API invocations, and account modifications within an AWS environment for auditing and regulatory purposes.

### Features
- Records performer, timestamp, and origin (e.g., IP address) of actions.
- Delivers comprehensive logs archived in S3 buckets.
- Connects with CloudWatch for immediate alerts on anomalous behavior.
- Logs accessible in CloudTrail Console or analyzable via Athena.

Activation: AWS Console → CloudTrail → Create trail.

## 10. Purpose of the Policy Simulator

The IAM Policy Simulator is a utility for evaluating and refining IAM policies in a simulated environment without affecting live AWS resources.

### Capabilities
- Emulates API calls to determine allow/deny outcomes.
- Accommodates testing of various policies, roles, and resources.
- Ideal for diagnosing intricate permission configurations or ensuring least privilege adherence.

Access: AWS Console → IAM → Policy Simulator.

## Review Questions

### 1. What is the core of TOTP authentication? Provide examples.
TOTP (Time-based One-Time Password) produces a distinct, temporary code (usually refreshing every 30 seconds) using a shared secret key, aligned between server and authenticator app. It bolsters security with a time-bound element.

Examples: Google Authenticator, Microsoft Authenticator, Authy, AWS Virtual MFA.

### 2. Explain the JSON format: its applications and characteristics. Does AWS employ it?
JSON (JavaScript Object Notation) is a simple, text-oriented data exchange standard that's readable by humans and parsable by software.

Characteristics:
- Organized into key-value pairs, arrays, and nested objects.
- Platform-agnostic and compatible with numerous programming languages.
- Efficient and user-friendly in structure.

AWS Usage: Absolutely, it's integral—for IAM policies, CloudFormation stacks, Lambda setups, and API outputs.

### 3. What varieties of Amazon APIs are available?
- **AWS Management Console API**: Graphical web portal for service interaction.
- **AWS SDKs**: Programming language kits (e.g., Boto3 for Python, AWS SDK for Java, JavaScript).
- **AWS CLI**: Terminal-based tool for automation and scripting.
- **AWS REST APIs**: HTTP interfaces for seamless programmatic connections (e.g., using Postman).

### 4. How to install AWS CLI across various OS platforms?
- **Windows**:
  ```
  msiexec.exe /i https://awscli.amazonaws.com/AWSCLIV2.msi
  ```
- **Linux**:
  ```
  curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
  unzip awscliv2.zip
  sudo ./aws/install
  ```
- **macOS**:
  ```
  curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
  sudo installer -pkg AWSCLIV2.pkg -target /
  ```

### 5. Fundamental AWS CLI Commands (with illustrations)
- `aws configure`: Configure credentials and default region.
  ```
  aws configure
  ```
- `aws s3 ls`: Display S3 buckets.
  ```
  aws s3 ls
  ```
- `aws ec2 describe-instances`: Detail EC2 instances.
  ```
  aws ec2 describe-instances
  ```
- `aws iam list-users`: Enumerate IAM users.
  ```
  aws iam list-users
  ```
- `aws s3 cp file.txt s3://mybucket/`: Transfer file to S3.
  ```
  aws s3 cp file.txt s3://mybucket/
  ```
- `aws cloudwatch describe-alarms`: Examine CloudWatch alarms.
  ```
  aws cloudwatch describe-alarms
  ```

## Summary

AWS delivers a worldwide, adaptable, and budget-friendly cloud infrastructure encompassing computing, storage, networking, databases, and security offerings. Utilizing IAM policies, MFA, and permission boundaries, users achieve robust access governance aligned with least privilege standards. Resources like Amazon Budgets and CloudTrail facilitate expense oversight and activity surveillance, while JSON-driven policies support versatile and precise authorization. Grasping TOTP verification, IAM role transitions, and AWS CLI operations promotes secure, automated cloud administration. In essence, proficiency in these core AWS elements empowers effective cloud utilization with emphasis on security, dependability, and cost efficiency.

---

# AWS

## Overview

Amazon Web Services (AWS) is a cloud computing platform offering compute, storage, networking, databases, and dozens of other managed services. For systems and networking roles, the most relevant AWS services are EC2, VPC, EKS, IAM, S3, Lambda, CloudWatch, and ALB.

## Conceptual Questions

- What is AWS?
- What is EC2?
- What is an instance type?
- What is an AMI (Amazon Machine Image)?
- What is a launch template?
- What is an Auto Scaling Group?
- What is Elastic Load Balancing?
- What is an Application Load Balancer (ALB)?
- What is a Network Load Balancer (NLB)?
- What is a Classic Load Balancer (CLB)?
- What is an S3 bucket?
- What is S3 object storage?
- What is S3 versioning?
- What is S3 lifecycle policy?
- What is Lambda?
- What is a Lambda function?
- What is Lambda cold start?
- What is a VPC (Virtual Private Cloud)?
- What is a subnet?
- What is a public subnet?
- What is a private subnet?
- What is a route table?
- What is an Internet Gateway (IGW)?
- What is a NAT Gateway?
- What is a NAT instance?
- What is a VPC Peering connection?
- What is AWS Transit Gateway?
- What is a Security Group?
- What is a Network ACL (NACL)?
- What is the difference between a Security Group and a NACL?
- What is an Elastic IP?
- What is an ENI (Elastic Network Interface)?
- What is Route 53?
- What is Route 53 health checks?
- What is Route 53 routing policies?
- What is latency-based routing?
- What is failover routing?
- What is weighted routing?
- What is geolocation routing?
- What is CloudFront?
- What is a CloudFront distribution?
- What is CloudWatch?
- What is a CloudWatch metric?
- What is a CloudWatch alarm?
- What is CloudWatch Logs?
- What is CloudWatch Logs Insights?
- What is CloudTrail?
- What is IAM?
- What is an IAM user?
- What is an IAM role?
- What is an IAM policy?
- What is an IAM group?
- What is the principle of least privilege?
- What is an STS (Security Token Service)?
- What is `AssumeRole`?
- What is instance metadata service (IMDS)?
- What is IMDSv2?
- What is EBS (Elastic Block Store)?
- What is EFS (Elastic File System)?
- What is FSx?
- What is RDS?
- What is Aurora?
- What is ElastiCache?
- What is SQS?
- What is SNS?
- What is EventBridge?
- What is Step Functions?
- What is Kinesis Data Streams?
- What is Kinesis Data Firehose?
- What is AWS Glue?
- What is AWS Config?
- What is AWS Systems Manager?
- What is AWS Secrets Manager?
- What is AWS Parameter Store?
- What is AWS KMS (Key Management Service)?
- What is AWS Certificate Manager (ACM)?
- What is AWS WAF?
- What is AWS Shield?
- What is AWS GuardDuty?

## Deep Dive Questions

- Describe the VPC networking model: VPC, subnets, route tables, IGW, NAT.
- How does a packet leave an EC2 instance in a public subnet to reach the Internet?
- How does a packet leave an EC2 instance in a private subnet to reach the Internet?
- How does inbound traffic reach an EC2 instance behind an ALB?
- Describe how Security Groups are stateful.
- Describe how NACLs are stateless.
- What is the order of evaluation for Security Groups and NACLs?
- How does VPC Peering work and what are its limitations?
- How does Transit Gateway differ from VPC Peering?
- What is VPC PrivateLink?
- What is a VPC endpoint?
- What is a gateway endpoint (for S3 and DynamoDB)?
- What is an interface endpoint?
- How does Route 53 resolve a private hosted zone?
- How does the ALB route requests: target groups, health checks, listener rules?
- What is a target group?
- What is a listener rule?
- What is an ALB condition (path, host, header, query)?
- What are ALB access logs?
- How does the NLB preserve the source IP?
- How does the ALB differ from the NLB in terms of TLS termination?
- How does IAM policy evaluation work (Allow vs Deny)?
- What is the IAM policy evaluation logic for resource-based policies vs identity-based policies?
- What is an IAM permission boundary?
- What is an SCP (Service Control Policy) in AWS Organizations?
- How does IRSA work (OIDC + assume role with web identity)?
- What is CloudWatch Embedded Metric Format (EMF)?
- How does CloudWatch Container Insights work?
- What is X-Ray and how does distributed tracing work?

## Why Questions

- Why use a private subnet for application servers?
- Why use a NAT Gateway instead of an Internet Gateway for private subnet egress?
- Why use Security Groups instead of host firewalls?
- Why use IAM roles instead of access keys for EC2 instances?
- Why use IMDSv2 instead of IMDSv1?
- Why use ALB instead of NLB for HTTP workloads?
- Why use NLB for UDP or extreme low-latency TCP workloads?
- Why use Route 53 health checks for failover?
- Why use VPC PrivateLink instead of VPC Peering for service exposure?
- Why use AWS Secrets Manager instead of environment variables for secrets?
- Why use SQS instead of a direct API call between services?

## Coding Questions

- Write a Terraform module that creates a VPC with public and private subnets.
- Write an IAM policy that grants read-only access to a specific S3 bucket.
- Write a Lambda function that reads from SQS and writes to DynamoDB.
- Write a CloudWatch alarm that fires when CPU exceeds 80% for 5 minutes.
- Write a CloudWatch Logs Insights query that finds error log lines.
- Write an ALB listener rule that routes `/api/*` requests to a specific target group.
- Write a Security Group rule that allows HTTPS from the ALB to EC2 instances.
- Write a Route 53 failover routing policy with a health check.
- Write an IAM role trust policy for EC2 to assume.
- Write a Terraform resource for an Auto Scaling Group with a launch template.

## Edge Cases

- What happens when a Security Group allows traffic but a NACL denies the return traffic?
- What happens when a NAT Gateway runs out of ports?
- What happens when an ALB health check fails for all targets?
- What happens when an EC2 instance's EBS root volume fills up?
- What happens when IMDSv2 is required but the application uses IMDSv1?
- What happens when an IAM policy has both Allow and Deny for the same action?
- What happens when Route 53 DNS propagation is delayed after a record change?
- What happens when Lambda cold starts add unacceptable latency?
- What happens when S3 bucket policy conflicts with IAM policy?

## Debugging Scenarios

- An EC2 instance cannot reach the Internet from a private subnet. How do you debug?
- An ALB returns 502 Bad Gateway. What does that mean and how do you investigate?
- An IAM role is getting AccessDenied errors. How do you diagnose using CloudTrail?
- A Lambda function is timing out. How do you investigate?
- CloudWatch metrics are missing for an EC2 instance. Why?
- An Auto Scaling Group is not scaling out even though CPU is high. Why?
- A VPC peering connection is established but traffic is not flowing. Why?
- Route 53 is returning the wrong IP for a record. How do you investigate?

## System Design Questions

- Design a highly available three-tier web application on AWS.
- Design a multi-region active-active architecture on AWS.
- Design a serverless data pipeline using Lambda, SQS, and S3.
- Design a secure VPC architecture for a regulated workload.
- Design a cost-optimized EKS cluster on AWS.
- Design a centralized logging architecture using CloudWatch and OpenSearch.

## Related Topics

- [EKS](../eks/questions.md)
- [Kubernetes](../kubernetes/questions.md)
- [Networking Fundamentals](../networking-fundamentals/questions.md)
- [System Design](../system-design/questions.md)
- [Debugging](../debugging/questions.md)

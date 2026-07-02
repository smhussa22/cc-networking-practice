# EKS

## Overview

Amazon Elastic Kubernetes Service (EKS) is a managed Kubernetes service on AWS. AWS manages the control plane; users manage worker nodes (EC2 or Fargate). EKS integrates with IAM, VPC, ALB, and other AWS services to provide a production-grade Kubernetes environment.

## Conceptual Questions

- What is EKS?
- How does EKS differ from self-managed Kubernetes?
- What does AWS manage in EKS versus what the user manages?
- What is the EKS control plane?
- What are EKS worker nodes?
- What is a managed node group?
- What is a self-managed node group?
- What is AWS Fargate for EKS?
- What is the difference between EC2 node groups and Fargate?
- What is the EKS add-on system?
- What is the AWS VPC CNI plugin?
- What is the AWS Load Balancer Controller?
- What is the EKS cluster autoscaler?
- What is Karpenter?
- How does IAM integrate with Kubernetes RBAC in EKS?
- What is IRSA (IAM Roles for Service Accounts)?
- What is the EKS Pod Identity feature?
- What is the aws-auth ConfigMap?
- What is eksctl?
- What is the EKS API endpoint?
- What is the EKS Kubernetes version upgrade process?

## Deep Dive Questions

- Describe the EKS control plane architecture.
- How does EKS run the kube-apiserver?
- How does EKS ensure control plane high availability?
- What VPC does the control plane use?
- How do worker nodes connect to the control plane?
- What is the EKS cluster endpoint and what access modes are available (public, private, public+private)?
- How does the AWS VPC CNI assign IPs to pods?
- What is the ENI (Elastic Network Interface) and how is it used?
- What is the secondary IP mode of the VPC CNI?
- What is prefix delegation mode in the VPC CNI?
- How does EKS integrate with AWS Security Groups for pods?
- How does a LoadBalancer service map to an AWS NLB or CLB?
- How does the ALB Ingress controller provision Application Load Balancers?
- What are target group bindings?
- How does IRSA work: what is the OIDC provider, the trust relationship, and how does the pod get credentials?
- How does the aws-auth ConfigMap map IAM users and roles to Kubernetes RBAC?
- What is the EKS managed add-on lifecycle?
- How does the Cluster Autoscaler interact with AWS Auto Scaling Groups?
- How does Karpenter provision nodes differently from the Cluster Autoscaler?
- What is EKS Anywhere?
- What is EKS Distro?
- What are EKS Blueprints?
- What is the EKS control plane logging and what log types are available?
- How does EKS integrate with CloudWatch for metrics?
- How does EKS integrate with CloudTrail?

## Why Questions

- Why use EKS instead of self-managed Kubernetes on EC2?
- Why use Fargate instead of EC2 nodes?
- Why does the VPC CNI assign pod IPs from the VPC CIDR instead of an overlay network?
- Why use IRSA instead of instance IAM roles for pod permissions?
- Why use Karpenter instead of the Cluster Autoscaler?
- Why keep the EKS control plane endpoint private?
- Why is the aws-auth ConfigMap the source of IAM-to-RBAC mapping?
- Why use managed node groups instead of self-managed?

## Coding Questions

- Write an eksctl cluster config file that creates a private cluster.
- Write a Kubernetes manifest that uses IRSA to access an S3 bucket.
- Write a Terraform configuration that provisions an EKS cluster with a managed node group.
- Write a Kubernetes Ingress manifest that provisions an ALB via the AWS Load Balancer Controller.
- Write a Karpenter NodePool manifest.
- Write a policy document for an IRSA trust relationship.
- Write the aws-auth ConfigMap to grant an IAM role cluster-admin access.

## Edge Cases

- What happens when a worker node's ENI runs out of secondary IP addresses?
- What happens when the EKS control plane endpoint is private and kubectl is run from outside the VPC?
- What happens when the aws-auth ConfigMap is misconfigured and all users are locked out?
- What happens when an IRSA role trust relationship has a wrong OIDC issuer?
- What happens when EKS fails to assign a pod IP due to IP exhaustion?
- What happens when a node group AMI is not updated before a Kubernetes version upgrade?

## Debugging Scenarios

- Pods are stuck in Pending with "no nodes available" even though nodes exist. Why?
- An IRSA-enabled pod returns an AccessDenied error when calling AWS APIs. How do you debug?
- The ALB Ingress controller does not provision an ALB after applying an Ingress manifest. Why?
- A node is NotReady and pods on it are being evicted. How do you investigate?
- The Cluster Autoscaler is not scaling up nodes even though pods are unschedulable. Why?
- EKS control plane logs show excessive API server errors. How do you diagnose?
- kubectl commands work for one IAM user but return 403 for another. Why?
- An EKS cluster upgrade fails partway through. What do you check?

## System Design Questions

- Design a multi-account EKS architecture for a large organization.
- Design a private EKS cluster with secure access for developers.
- Design an EKS-based platform with GitOps, autoscaling, and observability.
- Design a cost optimization strategy for an EKS cluster.
- Design cross-cluster service discovery on EKS.

## Related Topics

- [Kubernetes](../kubernetes/questions.md)
- [AWS](../aws/questions.md)
- [Networking Fundamentals](../networking-fundamentals/questions.md)
- [Debugging](../debugging/questions.md)

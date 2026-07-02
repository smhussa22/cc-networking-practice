# Kubernetes

## Overview

Kubernetes is an open-source container orchestration platform that automates deployment, scaling, and management of containerized applications. It groups containers into Pods and uses a desired-state model where controllers continuously reconcile actual state with declared state.

## Conceptual Questions

- What is Kubernetes?
- What problem does Kubernetes solve?
- What is a container?
- What is a Pod?
- Why is the Pod the smallest deployable unit rather than the container?
- What is a Deployment?
- What is a ReplicaSet?
- What is a StatefulSet?
- What is a DaemonSet?
- What is a Job?
- What is a CronJob?
- What is a Service?
- What is a ClusterIP service?
- What is a NodePort service?
- What is a LoadBalancer service?
- What is an ExternalName service?
- What is a Headless service?
- What is an Ingress?
- What is an Ingress controller?
- What is a Namespace?
- What is a ConfigMap?
- What is a Secret?
- What is a PersistentVolume (PV)?
- What is a PersistentVolumeClaim (PVC)?
- What is a StorageClass?
- What is a ServiceAccount?
- What is RBAC?
- What is a Role?
- What is a ClusterRole?
- What is a RoleBinding?
- What is a ClusterRoleBinding?
- What is a liveness probe?
- What is a readiness probe?
- What is a startup probe?
- What is the difference between liveness and readiness probes?
- What is a rolling update?
- What is a rollback in Kubernetes?
- What is a resource request?
- What is a resource limit?
- What is the difference between requests and limits?
- What is QoS class (Guaranteed, Burstable, BestEffort)?
- What is a HorizontalPodAutoscaler (HPA)?
- What is a VerticalPodAutoscaler (VPA)?
- What is a node selector?
- What is a node affinity?
- What is pod affinity and anti-affinity?
- What is a taint and toleration?
- What is a Network Policy?
- What is the Container Network Interface (CNI)?
- What is the Container Runtime Interface (CRI)?
- What is containerd?
- What is the control plane?
- What is the kube-apiserver?
- What is etcd?
- What is the kube-scheduler?
- What is the kube-controller-manager?
- What is the cloud-controller-manager?
- What is the kubelet?
- What is the kube-proxy?

## Deep Dive Questions

- Describe what happens when you run `kubectl apply -f deployment.yaml`.
- How does the kube-apiserver validate and persist an object?
- How does etcd store Kubernetes objects?
- How does the kube-scheduler select a node for a Pod?
- What predicates does the scheduler evaluate?
- What priorities does the scheduler evaluate?
- How does the kubelet reconcile desired pod state on a node?
- How does kube-proxy implement Service routing?
- What are the kube-proxy modes (iptables, ipvs, userspace)?
- How does iptables implement ClusterIP?
- How does a Service get its ClusterIP?
- How does DNS work inside a cluster (CoreDNS)?
- What DNS name does a Service get?
- How does pod-to-pod communication work across nodes?
- How does a CNI plugin assign pod IPs?
- What is an overlay network?
- What is VXLAN and how is it used in Kubernetes networking?
- Describe the lifecycle of a Pod from creation to Running.
- Describe the lifecycle of a Pod from Running to Terminated.
- What are the Pod phases?
- What are container states (Waiting, Running, Terminated)?
- What is a init container?
- What is a sidecar container?
- What is a postStart hook?
- What is a preStop hook?
- How does a rolling update work step by step?
- What is maxSurge and maxUnavailable in a rolling update?
- What is the ReplicaSet's role in a Deployment rollout?
- How does Kubernetes handle a failed rolling update?
- What is the garbage collection of ReplicaSets?
- How does StatefulSet handle pod identity and stable network names?
- How does StatefulSet handle ordered deployment and scaling?
- How does a DaemonSet ensure one pod per node?
- How does a HPA scale based on CPU metrics?
- What is the metrics server and how does HPA use it?
- What is a custom metric and how can HPA use it?
- What is Pod Disruption Budget (PDB)?
- What is a finalizer?
- What is an owner reference?
- How does garbage collection use owner references?
- What is the admission controller pipeline?
- What is a MutatingAdmissionWebhook?
- What is a ValidatingAdmissionWebhook?
- What is OPA/Gatekeeper?

## Why Questions

- Why is the Pod the atomic unit rather than the container?
- Why does Kubernetes use a desired-state model instead of imperative commands?
- Why is etcd used instead of a relational database?
- Why does Kubernetes use a watch-based mechanism instead of polling?
- Why are readiness and liveness probes separate?
- Why use a rolling update instead of a full restart?
- Why use StatefulSet instead of Deployment for databases?
- Why use a DaemonSet for log collectors?
- Why does Kubernetes use iptables for Service routing by default?
- Why is the kube-proxy separate from the kubelet?
- Why use a CNI plugin instead of built-in networking?
- Why are Secrets base64-encoded instead of encrypted at rest by default?
- Why use RBAC instead of simple ACLs?

## Coding Questions

- Write a Deployment manifest for a web server with 3 replicas.
- Write a Service manifest that exposes the Deployment internally.
- Write a ConfigMap and mount it as an environment variable.
- Write a liveness and readiness probe for an HTTP server.
- Write a resource requests and limits specification.
- Write a HorizontalPodAutoscaler that scales on CPU.
- Write a NetworkPolicy that restricts ingress to a Pod.
- Write a CronJob that runs a batch job every hour.
- Write a StatefulSet for a database with a PersistentVolumeClaim template.
- Write a DaemonSet for a log forwarder.
- Write a Role and RoleBinding that grants read access to pods in a namespace.

## Debugging Scenarios

- A pod is in CrashLoopBackOff. How do you debug it?
- A pod is Pending and never schedules. Why?
- A pod is Running but fails the readiness probe. How do you investigate?
- A service is not routing traffic to pods. What do you check?
- A rolling update is stuck and not completing. Why?
- Pods are being evicted. What does that mean and why does it happen?
- A pod cannot reach another pod across nodes. How do you diagnose?
- kubectl commands return errors about certificate expiration. How do you fix it?
- A DaemonSet pod is missing from one node. Why?
- A HPA is not scaling even though CPU is high. What do you check?
- etcd latency is high and the control plane is slow. How do you investigate?
- A Secret change is not being reflected in a running pod. Why?

## System Design Questions

- Design a Kubernetes monitoring stack.
- Design a multi-tenant Kubernetes cluster with namespace isolation.
- Design a GitOps pipeline for deploying to Kubernetes.
- Design a blue-green deployment strategy using Kubernetes.
- Design a canary deployment using Kubernetes.
- Design a zero-downtime deployment pipeline.
- Design a Kubernetes-based batch processing system.

## Related Topics

- [EKS](../eks/questions.md)
- [Linux Networking](../linux-networking/questions.md)
- [Debugging](../debugging/questions.md)
- [System Design](../system-design/questions.md)
- [AWS](../aws/questions.md)

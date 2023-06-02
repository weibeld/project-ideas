---
id: egwrjt4avhz2ddk38pap7o8
title: Managed Kubernetes Service
desc: ''
updated: 1679680691434
created: 1679083198674
---

A managed Kubernetes service for experimentation purposes.

## Description

Often a throw-away Kubernetes cluster in a real setting (i.e. not Minkube or kind) is needed for experimentation purposes. However, it's time-consuming and tedious to create such a cluster.

Create a service that spins up and gives access to a bare-bones cluster on demand.

> Note: this is similar to what [`terraform-aws-kubeadm`](https://github.com/weibeld/terraform-aws-kubeadm) can do, however, this idea would be a fully automated service. Maybe `terraform-aws-kubeadm` can be used behind the scene?

The service can be free, but with the restriction that the entire infrastructure is shut down after after a specific amount of time, e.g. 24 hours.

## Details

### Pricing

Free version:

- Free Kubernetes cluster with a single node (e.g. AWS t3.micro)
    - Use k3s for light control plane, e.g. control plane on worker node?
- Full cluster access (namespaces, API)
- SSH access to worker (and master) node
- Compute instance (and cluster) is shut down after 24 hours

Paid version:

- Avoid shutdown after 24 hours (i.e. keep cluster running as long as fee is being paid)
    - E.g. pay by day
- Adding more worker nodes to the cluster
- More robust control plane (e.g. kubeadm control plane instad of k3s)

### Other

- No additional services (support, default services like CNI plugin or storage, monitoring, etc.)
- The goal is to provide a bare-bones Kubernetes cluster with as little pre-configuration as possible
- The intended use case is for quick experimentation (e.g. as a replacement for local Docker Desktop Kubernetes cluster, minikube, or kind)
- Could be implemented for all cloud providers so that users can choose the desired cloud backend at service creation time
- See plans of [`terraform-aws-kubeadm`](https://github.com/weibeld/terraform-aws-kubeadm) for porting the tool to GCP and Azure.

### Issues

- How to provide security if giving users acess to instances (e.g. by SSH) on one's own cloud infrastructure?
- How to prevent misue of provided infrastructure for other purposes (e.g. exploitation of computing power)?

### Possible names

- Kuberneasy
- KubeScratch
    - Get a temporary (or permanent) Kubernetes cluster _right now_!

## Background

There exist tons of managed Kubernetes services but most are specialised on some "integrated" or "production-ready" use case, such as:

- https://www.okteto.com/
- https://kraudcloud.com/
- https://www.civo.com/kubernetes

There's no managed Kubernetes service which is really bare-bones and with "no strings attched". 

## Resources

<!-- Resources that might be useful for implementing the project -->
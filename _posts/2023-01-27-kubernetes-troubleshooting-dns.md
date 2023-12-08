---
layout: post
title: Kubernetes Troubleshooting DNS
categories: [Blog, Kubernetes]
tags: [AKS]
---

## Troubleshooting DNS issues
There are a few ways to check the DNS settings of your Kubernetes (K8s) cluster:

- Check the kube-dns configuration: By default, Kubernetes uses kube-dns for DNS resolution. You can check the configuration of kube-dns by running the command kubectl get configmap kube-dns -n kube-system -o yaml. This will display the configuration of the kube-dns service, including the DNS server IP address.

- Check the pods: You can check the DNS settings of the pods by running the command kubectl describe pods <pod-name>. This will show the DNS settings for the pod, including the DNS server IP address.

- Check the Services: You can check the DNS settings of the services by running the command kubectl describe services <service-name>. This will show the DNS settings for the services, including the DNS server IP address.

- Check the Cluster Information: You can check the DNS settings of the Cluster by running the command kubectl cluster-info. This will show you the DNS settings of the k8s cluster, including the DNS server IP address.

- It's important to make sure that the DNS server IP address is reachable from the pods and the services. If it's not reachable, it may cause the connection timeout issue you mentioned.
  

  
## Commands
``` bash
kubectl get configmap kube-dns -n kube-system -o yaml
  
kubectl describe services <service-name>

kubectl cluster-info
```

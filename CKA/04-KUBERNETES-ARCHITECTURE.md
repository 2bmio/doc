---
title: 04. KUBERNETES ARCHITECTURE
description: 
published: true
date: 2020-06-07T15:22:59.006Z
tags: 
editor: markdown
---

# 04. KUBERNETES ARCHITECTURE
By the end of this chapter, you should be able to:


*   Discuss the main components of a Kubernetes cluster.

*   Learn details of the master agent kube\-apiserver.

*   Explain how the etcd database keeps the cluster state and configuration.

*   Study the kubelet local agent.

*   Examine how controllers are used to manage the cluster state.

*   Discover what a Pod is to the cluster.

*   Examine network configurations of a cluster.

*   Discuss Kubernetes services.

## Main Components
Kubernetes has the following main components:

>**Master and worker nodes**
~text~
**Controllers**
~text~
**Services**
~text~
**Pods of containers**
~text~
**Namespaces and quotas**
~text~
**Network and policies**
~text~
**Storage**

![qbtsrlj644au-kubernetesarchitecture.png](/cka/qbtsrlj644au-kubernetesarchitecture.png)



## Master node
control plane

>**kube-apiserver**
>* The kube-apiserver is central to the operation of the Kubernetes cluster. All calls, both internal and external traffic, are handled via this agent. All actions are accepted and validated by this agent, and it is the only connection to the etcd database. It validates and configures data for API objects, and services REST operations. As a result, it acts as a master process for the entire cluster, and acts as a frontend of the cluster's shared state.
>* Starting as an alpha feature in v1.16 is the ability to separate user-initiated traffic from server-initiated traffic. Until these features are developed, most network plugins commingle the traffic, which has performance, capacity, and security ramifications.

>**kube-scheduler**
>* The kube-scheduler uses an algorithm to determine which node will host a Pod of containers. The scheduler will try to view available resources (such as volumes) to bind, and then try and retry to deploy the Pod based on availability and success. There are several ways you can affect the algorithm, or a custom scheduler could be used instead. You can also bind a Pod to a particular node, though the Pod may remain in a pending state due to other settings. One of the first settings referenced is if the Pod can be deployed within the current quota restrictions. If so, then the taints and tolerations, and labels of the Pods are used along with those of the nodes to determine the proper placement.

>**etcd database**
>* The state of the cluster, networking, and other persistent information is kept in an etcd database, or, more accurately, a b+tree key-value store. Rather than finding and changing an entry, values are always appended to the end. Previous copies of the data are then marked for future removal by a compaction process. It works with curl and other HTTP libraries, and provides reliable watch queries.
>* Simultaneous requests to update a value all travel via the kube-apiserver, which then passes along the request to etcd in a series. The first request would update the database. The second request would no longer have the same version number, in which case the kube-apiserver would reply with an error 409 to the requester. There is no logic past that response on the server side, meaning the client needs to expect this and act upon the denial to update. 
>* There is a master database along with possible followers. They communicate with each other on an ongoing basis to determine which will be master, and determine another in the event of failure. While very fast and potentially durable, there have been some hiccups with new tools, such as kubeadm, and features like whole cluster upgrades.

>**kube-controller-manager**
>* The kube-controller-manager is a core control loop daemon which interacts with the kube-apiserver to determine the state of the cluster. If the state does not match, the manager will contact the necessary controller to match the desired state. There are several controllers in use, such as endpoints, namespace, and replication. The full list has expanded as Kubernetes has matured. 

>**cloud-controller-manager**
>* Remaining in beta in v1.16, the cloud-controller-manager (ccm) interacts with agents outside of the cloud. It handles tasks once handled by kube-controller-manager. This allows faster changes without altering the core Kubernetes control process. Each kubelet must use the --cloud-provider-external settings passed to the binary. You can also develop your own ccm, which can be deployed as a daemonset as an in-tree deployment or as a free-standing out-of-tree installation. The cloud-controller-manager is an optional agent which takes a few steps to enable. You can learn more about the cloud-controller-manager online.



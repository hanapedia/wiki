---
title: Kind Cluster Without CNI
LinkTitle: Kind Cluster Without CNI
description: How to create Kind Cluster without CNI installed
categories: [How to]
tags: [kubernetes, CNI]
weight: 1
---

# Kind Cluster Without CNI
Kind installs a CNI by default.
To create a kind cluster without CNI installed, simply set `networking.disableDefaultCNI` to `true` in the cluster config manifest.

```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
networking:
  # the default CNI will not be installed
  disableDefaultCNI: true
```

So run the following command.
```bash
kind create cluster --config <<EOF
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
networking:
  # the default CNI will not be installed
  disableDefaultCNI: true
EOF
```

And Check that Pods that are not part of the control plane is in `Pending` status.
```bash
$ kubectl get pods -A
NAMESPACE            NAME                                         READY   STATUS    RESTARTS   AGE
kube-system          coredns-5d78c9869d-2gljt                     0/1     Pending   0          16s
kube-system          coredns-5d78c9869d-vnftf                     0/1     Pending   0          16s
kube-system          etcd-kind-control-plane                      1/1     Running   0          31s
kube-system          kube-apiserver-kind-control-plane            1/1     Running   0          31s
kube-system          kube-controller-manager-kind-control-plane   1/1     Running   0          31s
kube-system          kube-proxy-qm5pn                             1/1     Running   0          16s
kube-system          kube-scheduler-kind-control-plane            1/1     Running   0          31s
local-path-storage   local-path-provisioner-6bc4bddd6b-s68jl      0/1     Pending   0          16s
```

You can also see that the nodes are not ready.
```bash
$ kubectl get nodes
NAME                             STATUS     ROLES           AGE   VERSION
kind-without-cni-control-plane   NotReady   control-plane   28s   v1.27.3
```

**References**
- https://kind.sigs.k8s.io/docs/user/configuration/#disable-default-cni

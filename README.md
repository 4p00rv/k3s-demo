# K3s Tutorial

This tutorial covers a development environment setup to play with K3s, using k3d. And solving some common scenarios with k8s



### Cluster Setup

You need the following pre-requisites:

- Docker (https://docs.docker.com/engine/install/ under Server)
- kubectl (https://kubernetes.io/docs/tasks/tools/)



To install k3d use the following:

```
$ curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash
```



To setup a cluster with one server (control plane node) and 2 agents (worker node) use the following command:

```
k3d cluster create test \
-a 2 --agents-memory 200MB \
--k3s-arg "--node-taint=node-role.kubernetes.io/master:NoSchedule@server:0" \
--k3s-node-label "region=local-us@agent:0" \
--k3s-node-label "region=local-eu@agent:1"

```


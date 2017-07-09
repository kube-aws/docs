# Pre-requisites

If you're deploying a cluster with kube-aws:

* [EC2 instances whose types are larger than or equal to `t2.medium` should be chosen for the cluster to work reliably](https://github.com/kubernetes-incubator/kube-aws/issues/138)
* [At least 3 etcd, 2 controller, 2 worker nodes are required to achieve high availability](https://github.com/kubernetes-incubator/kube-aws/issues/138#issuecomment-266432162)

Once you understand the pre-requisites, you are ready to launch your first Kubernetes cluster, [proceed to Step 1: Configure](/getting-started-step-1-configure.md).


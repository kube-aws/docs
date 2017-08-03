# Kubernetes on AWS

Deploy a fully-functional Kubernetes cluster using AWS CloudFormation. Your cluster will be configured to use AWS features to enhance Kubernetes. For example, Kubernetes may automatically provision an Elastic Load Balancer for each Kubernetes Service.

The [kube-aws](https://github.com/kubernetes-incubator/kube-aws/releases) CLI tool can be used to automate cluster deployment to AWS.

After completing this guide, a deployer will be able to interact with the Kubernetes API from their workstation using the `kubectl` CLI tool.

Each of the steps will cover:

* [Step 1: Configure](step-1-configure.md)
  * Download the kube-aws CloudFormation generator
  * Define account and cluster settings
* [Step 2: Render](step-2-render.md)
  * Compile a re-usable CloudFormation template for the cluster
  * Optionally adjust template configuration
  * Validate the rendered CloudFormation stack
* [Step 3: Launch](step-3-launch.md)
  * Create the CloudFormation stack and start our EC2 machines
  * Set up CLI access to the new cluster
* [Step 4: Update](step-4-update.md)
  * Update the CloudFormation stack
* [Step 5: Add Node Pool](step-5-add-node-pool.md)
  * Create the additional pool of worker nodes
  * Adjust template configuration for each pool of worker nodes
  * Required to support [cluster-autoscaler](https://github.com/kubernetes/contrib/tree/master/cluster-autoscaler)
* [Step 6: Configure add-ons](step-6-configure-add-ons.md)
  * Configure various Kubernetes add-ons
* [Step 7: Destroy](step-7-destroy.md)
  * Destroy the cluster

Let's get started with [Step 1](step-1-configure.md)!
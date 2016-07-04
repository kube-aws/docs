# Getting Started

Deploy a fully-functional Kubernetes cluster using AWS CloudFormation.

Your cluster will be configured to use AWS features to enhance Kubernetes.

For example, Kubernetes may automatically provision an Elastic Load Balancer for each Kubernetes Service.

After completing this guide, a deployer will be able to interact with the Kubernetes API from their workstation using the `kubectl` CLI tool.

# Pre-requisites {#pre-requisites}

If you're deploying a cluster with kube-aws:

* [EC2 instances whose types are larger than or equal to `t2.medium` should be chosen for the cluster to work reliably](https://github.com/kubernetes-incubator/kube-aws/issues/138)
* [At least 3 etcd, 2 controller, 2 worker nodes are required to achieve high availability](https://github.com/kubernetes-incubator/kube-aws/issues/138#issuecomment-266432162)

Once you understand the pre-requisites, you are ready to launch your first Kubernetes cluster.

# Step 1: Configure {#step1}

Step 1 will cover:

* Downloading kube-aws
* Defining account and cluster settings

Download kube-aws

Go to the \[releases\]\([https://github.com/kubernetes-incubator/kube-aws/releases\](https://github.com/kubernetes-incubator/kube-aws/releases%29\) and download the latest release tarball for your architecture.

Extract the binary:

\`\`\`sh

tar zxvf kube-aws-${PLATFORM}.tar.gz

\`\`\`

Add kube-aws to your path:

\`\`\`sh

mv ${PLATFORM}/kube-aws /usr/local/bin

\`\`\`

\#\# Configure AWS credentials

Configure your local workstation with AWS credentials using one of the following methods:

\#\#\# Method 1: Configure command

Provide the values of your AWS access and secret keys, and optionally default region and output format:

\`\`\`sh

$ aws configure

AWS Access Key ID \[None\]: AKID1234567890

AWS Secret Access Key \[None\]: MY-SECRET-KEY

Default region name \[None\]: us-west-2

Default output format \[None\]: text

\`\`\`

\#\#\# Method 2: Config file

Write your credentials into the file \`~/.aws/credentials\` using the following template:

\`\`\`

\[default\]

aws\_access\_key\_id = AKID1234567890

aws\_secret\_access\_key = MY-SECRET-KEY

\`\`\`

\#\#\# Method 3: Environment variables

Provide AWS credentials to kube-aws by exporting the following environment variables:

\`\`\`sh

export AWS\_ACCESS\_KEY\_ID=AKID1234567890

export AWS\_SECRET\_ACCESS\_KEY=MY-SECRET-KEY

\`\`\`

\#\# Test Credentials

Test that your credentials work by describing any instances you may already have running on your account:

\`\`\`sh

$ aws ec2 describe-instances

\`\`\`

&lt;div class="co-m-docs-next-step"&gt;

&lt;p&gt;&lt;strong&gt;Did you download kube-aws?&lt;/strong&gt;&lt;/p&gt;

&lt;p&gt;&lt;strong&gt;Did your credentials work?&lt;/strong&gt; We will use the AWS CLI in the next step.&lt;/p&gt;

&lt;a href="kubernetes-on-aws-render.md" class="btn btn-primary btn-icon-right"  data-category="Docs Next" data-event="Kubernetes: AWS Render"&gt;Yes, ready to configure my cluster options&lt;/a&gt;

&lt;a href="[https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html)" class="btn btn-default btn-icon-right"  data-category="Docs Next" data-event="Configure AWS CLI"&gt;No, I need more info on the AWS CLI&lt;/a&gt;

&lt;/div&gt;



## Step 2: Render

Step 2 will cover:

* Compiling a re-usable CloudFormation template for the cluster
* Optionally adjust template configuration
* Validate the rendered CloudFormation stack

# Step 3: Launch

Step 3 will cover:

* Create the CloudFormation stack and start our EC2 machines
* Set up CLI access to the new cluster

# Step 4: Update

* Update the CloudFormation stack

# Step 5: Add Node Pool

Step 5 will cover:

* Create the additional pool of worker nodes
* Adjust template configuration for each pool of worker nodes
* Required to support [cluster-autoscaler](https://github.com/kubernetes/contrib/tree/master/cluster-autoscaler)

# Step 6: Configure Add-ons

Step 6 will cover:

* Configure various Kubernetes add-ons

# Step 7: Destroy

Step 7 will cover:

* Tearing down the cluster

Let's get started.


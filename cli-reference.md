# CLI Reference

# AWS Credentials

You can provide a AWS profile to kube-aws via the `AWS_PROFILE` environment variable such as:

```
AWS_PROFILE=your-profile-name kube-aws init ...
```

# `init`

| Parameter | Description | Default |
| `--availability-zone` | The AWS availability-zone to deploy to. Note, this can be changed to multi AZ in `cluster.yaml` | none |
| `--cluster-name` | The name of this cluster. This will be the name of the cloudformation stack | none |
| `--external-dns-name` | The hostname that will route to the api server | none |
| `hosted-zone-id` | The hosted zone in which a Route53 record set for a k8s API endpoint is created | none |
| `--key-name` | The AWS key-pair for SSH access to nodes | none |
| `--kms-key-arn` | The ARN of the AWS KMS key for encrypting TLS assets |
| `--region` | The AWS region to deploy to | none |



--availability-zone=us-west-1c \
--key-name=key-pair-name \
--kms-key-arn="arn:aws:kms:us-west-1:xxxxxxxxxx:key/xxxxxxxxxxxxxxxxxxx"



	cmdInit.Flags().StringVar(&initOpts.KeyName, "", "", "")
	cmdInit.Flags().StringVar(&initOpts.KMSKeyARN, "
	cmdInit.Flags().StringVar(&initOpts.AmiId, "ami-id", "", "The AMI ID of CoreOS")
}



Here `us-west-1c` is used for parameter `--availability-zone`, but supported availability zone varies among AWS accounts.
Please check if `us-west-1c` is supported by `aws ec2 --region us-west-1 describe-availability-zones`, if not switch to other supported availability zone. (e.g., `us-west-1a`, or `us-west-1b`)

There will now be a `cluster.yaml` file in the asset directory. This is the main configuration file for your cluster.

### Render contents of the asset directory

#### TLS certificates

* In the simplest case, you can have kube-aws generate both your TLS identities and certificate authority for you.

```sh
$ kube-aws render credentials --generate-ca
```

This is not recommended for production, but is fine for development or testing purposes.

* It is recommended that you supply your own immediate certificate signing authority and let kube-aws take care of generating the cluster TLS credentials.

```sh
$ kube-aws render credentials --ca-cert-path=/path/to/ca-cert.pem --ca-key-path=/path/to/ca-key.pem
```
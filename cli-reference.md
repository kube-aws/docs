# CLI Reference

# AWS Credentials

You can provide a AWS profile to kube-aws via the `AWS_PROFILE` environment variable such as:

```
AWS_PROFILE=your-profile-name kube-aws init ...
```

# `init`

Initialize the base configuration for a cluster ready for customization prior to deployment.

| Flag | Description | Default |
| -- | -- | -- |
| `ami-id` | The AMI ID of CoreOS Container Linux to deploy | The latest AMI for the Container Linux release channel specified in `cluster.yaml` |
| `availability-zone` | The AWS availability-zone to deploy to. Note, this can be changed to multi AZ in `cluster.yaml` | none |
| `cluster-name` | The name of this cluster. This will be the name of the cloudformation stack | none |
| `external-dns-name` | The hostname that will route to the api server | none |
| `hosted-zone-id` | The hosted zone in which a Route53 record set for a k8s API endpoint is created | none |
| `key-name` | The AWS key-pair for SSH access to nodes | none |
| `kms-key-arn` | The ARN of the AWS KMS key for encrypting TLS assets |
| `region` | The AWS region to deploy to | none |

## `init` example

```bash
$ kube-aws init \
  --cluster-name=my-cluster \
  --external-dns-name=my-cluster-endpoint.mydomain.com \
  --region=us-west-1 \
  --availability-zone=us-west-1c \
  --key-name=key-pair-name \
  --kms-key-arn="arn:aws:kms:us-west-1:xxxxxxxxxx:key/xxxxxxxxxxxxxxxxxxx"
```

# `render credentials`

Render TLS credentials required for cluster administration and communication between cluster nodes.

| Flag | Description | Default |
| -- | -- | -- |
| `ca-cert-path` | Path to pem-encoded CA x509 certificate | `./credentials/ca.pem` |
| `ca-key-path` | Path to pem-encoded CA RSA key | `./credentials/ca-key.pem` |
| `generate-ca` | If generating credentials, generate root CA key and cert. **NOT RECOMMENDED FOR PRODUCTION USE**, use `-ca-key-path` and `-ca-cert-path` options to provide your own certificate authority assets. | `false` |

## `render credentials` example

```bash
$ kube-aws render credentials \
  --ca-cert-path=/path/to/ca-cert.pem
  --ca-key-path=/path/to/ca-key.pem
```

# `render stack`

Render [CloudFormation](https://aws.amazon.com/cloudformation/) stack templates and [coreos-cloudinit](https://github.com/coreos/coreos-cloudinit) userdata ready for customization prior to deployment.

`render stack` has no CLI flags.

## `render stack` example

```bash
$ kube-aws render stack
```

# `validate`
| Flag | Description | Default |
| -- | -- | -- |
Validate cluster assets

		Short:        "Validate cluster assets",
		Long:         ``,
		RunE:         runCmdValidate,
		SilenceUsage: true,
	}

	validateOpts = struct {
		awsDebug bool
		skipWait bool
		s3URI    string
	}{}
)

func init() {
	RootCmd.AddCommand(cmdValidate)
	cmdValidate.Flags().BoolVar(
		&validateOpts.awsDebug,
		"aws-debug",
		false,
		"Log debug information from aws-sdk-go library",
	)
	cmdValidate.Flags().StringVar(
		&validateOpts.s3URI,
		"s3-uri",
		"",
		"When your template is bigger than the cloudformation limit of 51200 bytes, upload the template to the specified location in S3. S3 location expressed as s3://<bucket>/path/to/dir",
	)
}

## `validate` example

```bash
$ kube-aws validate \
  --s3-uri=s3://my-kube-aws-assets-bucket
```

# `up`

# `update`

# `destroy`
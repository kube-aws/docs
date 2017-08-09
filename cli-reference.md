# CLI Reference

# AWS Credentials

You can provide a AWS profile to kube-aws via the `AWS_PROFILE` environment variable such as:

```
AWS_PROFILE=your-profile-name kube-aws init ...
```

# `init`

| Parameter | Description | Default |
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
kube-aws init \
  --cluster-name=my-cluster \
  --external-dns-name=my-cluster-endpoint.mydomain.com \
  --region=us-west-1 \
  --availability-zone=us-west-1c \
  --key-name=key-pair-name \
  --kms-key-arn="arn:aws:kms:us-west-1:xxxxxxxxxx:key/xxxxxxxxxxxxxxxxxxx"
```

# `render credentials`

| Parameter | Description | Default |
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
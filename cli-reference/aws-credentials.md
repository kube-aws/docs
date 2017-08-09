# AWS Credentials

Configure your local workstation with AWS credentials using one of the following methods.

## `configure` command

Provide the values of your AWS access and secret keys, and optionally default region and output format:

```bash
$ aws configure
AWS Access Key ID [None]: AKID1234567890
AWS Secret Access Key [None]: MY-SECRET-KEY
Default region name [None]: us-west-1
Default output format [None]: text
```

## Environment Variables

Provide AWS credentials to kube-aws by exporting the following environment variables:

```bash
export AWS_ACCESS_KEY_ID=AKID1234567890
export AWS_SECRET_ACCESS_KEY=MY-SECRET-KEY
```

### Multi-Factor Authentication (MFA)

If you are using MFA, you need to export the Session Token as well:

```bash
export AWS_SESSION_TOKEN=MY-SESSION-TOKEN
```


Method 3: Environment variables

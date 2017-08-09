# AWS Credentials

You can provide a AWS profile to kube-aws via the `AWS_PROFILE` environment variable such as:

```
AWS_PROFILE=my-profile-name kube-aws init ...
```



Configure AWS credentials

Configure your local workstation with AWS credentials using one of the following methods:

Method 1: Configure command

Provide the values of your AWS access and secret keys, and optionally default region and output format:

$ aws configure
AWS Access Key ID [None]: AKID1234567890
AWS Secret Access Key [None]: MY-SECRET-KEY
Default region name [None]: us-west-2
Default output format [None]: text
Method 2: Config file

Write your credentials into the file ~/.aws/credentials using the following template:

[default]
aws_access_key_id = AKID1234567890
aws_secret_access_key = MY-SECRET-KEY
Method 3: Environment variables

Provide AWS credentials to kube-aws by exporting the following environment variables:

export AWS_ACCESS_KEY_ID=AKID1234567890
export AWS_SECRET_ACCESS_KEY=MY-SECRET-KEY
If you are using MFA, pls export the Session Token

export AWS_SESSION_TOKEN=MY-SESSION-TOKEN
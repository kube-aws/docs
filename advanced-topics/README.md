# Advanced Topics

These are optional features which can be enabled using kube-aws.

* [etcd Backup & Restore](etcd-backup-and-restore.md)
* [Cluster Resource Backup to AWS S3](cluster-resource-backup-to-s3.md) - automated backup and restore your Kubernetes resources to S3
<!--* [Restore Kubernetes resources](/contrib/cluster-backup/README.md)-->
* [Journald Logging to AWS CloudWatch](journald-logging-to-aws-cloudwatch.md) - stream journald logs into CloudWatch and also to some CLI commands such as `kube-aws up` and `kube-aws update`
* [CloudFormation Streaming](/Documentation/kubernetes-on-aws-cloudformation-streaming.md) - stream CloudFormation updates during CLI commands `kube-aws up` and `kube-aws update`

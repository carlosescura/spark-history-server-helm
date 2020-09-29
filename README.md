# Spark history server Helm Chart

[SHS](https://apache-spark-on-k8s.github.io/userdocs/running-on-kubernetes.html) Spark History Server is the web UI for completed and running Spark applications.

## Chart Details

This chart uses AWS K8s [IRSA](https://aws.amazon.com/blogs/opensource/introducing-fine-grained-iam-roles-service-accounts/) technology to authenticate against AWS, so a proper `ServiceAccount` needs to be specified in order to have the right permissions accessing application logs S3 bucket.

## Installing the Chart

To install the chart:

```sh
helm install --set app.S3logPath=yourBucketName/eventLogFoloder
```

## Required variables

Minimum required variables are:

| Parameter             | Required | Description                                                                                                         | Example         |
| --------------------- | -------- | ------------------------------------------------------------------------------------------------------------------- | --------------- |
| `S3logPath`           | `yes`    | S3 bucket and key used as base directory for Spark Application logs                                                 | `mybucket/logs` |
| `serviceAccount.name` | `yes`    | Service account used to run the deployment. Needs to have the appropiate IRSA role associated in order to access S3 | `sparkSA`       |

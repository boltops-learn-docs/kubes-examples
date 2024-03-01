<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-learn/kubes-examples/blob/master/yaml/aws/irsa/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

# Kubes IRSA IAM Role for Service Account Example

[![BoltOps Badge](https://img.boltops.com/boltops/badges/boltops-badge.png)](https://www.boltops.com)

We'll create these Kubernetes resources:

1. [deployment](deployment.yaml): Run nginx web server pods.
2. [service](service.yaml): Expose an endpoint to reach the nginx pods.
3. [service_account](service_account.yaml): Provides S3 Read Only Access

## Hook Usage

A [kubes-level hook] is used to create the IAM Role using:

```ruby
KubesAws::IamRole.new
```

This ensures both exists:

* IAM Role
* OpenID Connect Provider

IAM permissions are only added by the IamRole class. This means permsisions manually added are kept.

## Deploy

    kubes deploy

## Confirm

    kubectl config set-context --current --namespace=demo-dev
    kubectl get all

Or kubes commands

    kubes get

## Cleanup

    kubes delete

## Video

[![Watch the video](https://uploads-learn.boltops.com/61dhnuzzw67z1g3fg3u2f9yggpmj)](https://learn.boltops.com/courses/aws-eks/lessons/eks-iam-role-for-service-account-irsa-automation-with-kubes)

Note: Premium video content requires a subscription.

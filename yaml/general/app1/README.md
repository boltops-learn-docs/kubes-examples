<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-learn/kubes-examples/blob/master/yaml/general/app1/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

# Simple Kubes Demo Example

[![BoltOps Badge](https://img.boltops.com/boltops/badges/boltops-badge.png)](https://www.boltops.com)

We'll create these Kubernetes resources:

1. [deployment](deployment.yaml): Run nginx web server pods.
2. [service](service.yaml): Expose an endpoint to reach the nginx pods.

## Deploy

    kubes deploy

## Confirm

    kubectl config set-context --current --namespace=demo-dev
    kubectl get all

Or kubes commands

    kubes get

## Cleanup

    kubes delete

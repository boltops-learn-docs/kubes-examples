<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-learn/kubes-examples/blob/master/yaml/google/elb7-https-managed-certificate/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

# Kubernetes Ingresss with Google SSL Managed Certificate

[![BoltOps Badge](https://img.boltops.com/boltops/badges/boltops-badge.png)](https://www.boltops.com)

[![BoltOps Learn Badge](https://img.boltops.com/boltops-learn/boltops-learn.png)](https://learn.boltops.com)

We'll show you how to use a Google SSL Managed Certificate with the Kuberntes ManagedCertificate resource.

## Commands

Create the Static IP. Note, I like the `-global` suffix to help remember that it's a global IP vs an reion

    gcloud compute addresses create demo-global --global

Deploy

    kubes deploy
    kubes apply # once at least one Docker image has been build

Host commands to check DNS

    host demo.google.dev.boltops.com
    host demo1.google.dev.boltops.com
    host demo2.google.dev.boltops.com

Check SSL cert provisioning status

    gcloud compute ssl-certificates list
    gcloud compute ssl-certificates describe mcrt-GENERATED_ID

## Docs

https://cloud.google.com/kubernetes-engine/docs/how-to/managed-certs#setting_up_a_google-managed_certificate

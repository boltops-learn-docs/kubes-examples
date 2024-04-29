<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-learn/kubes-examples/blob/master/yaml/google/elb7-https-secret-manual/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

# GKE Ingress HTTPS External Load Balancer with Secret Resource (Manually Created)

[![BoltOps Badge](https://img.boltops.com/boltops/badges/boltops-badge.png)](https://www.boltops.com)

Example project shows how to use a SSL Cert Kubernetes Secret resource with GKE. It'll follow more closely the Google Cloud Docs of creating the secret manually.

Relevant Links:

* Google Cloud Docs: [Using multiple SSL certificates in HTTPS load balancing with Ingress - Specifying certificates for your Ingress: Pre-Shared Certs](https://cloud.google.com/kubernetes-engine/docs/how-to/ingress-multi-ssl#pre-shared-certs)
* [Kubes](https://kubes.guru/): Kubernetes App Deployment Tool

## Configure Env Vars

    export GOOGLE_APPLICATION_CREDENTIALS=/path/to/gcp/credentials.json
    export GOOGLE_PROJECT=replace-with-your-project-id
    export REPO=gcr.io/$GOOGLE_PROJECT/demo

Note you need to also configure env vars that point to your TLS cert files. IE:

    TLS_CRT=/home/ec2-user/environment/cert-files/certificate.crt
    TLS_KEY=/home/ec2-user/environment/cert-files/private.key

## Deploy

    kubes deploy

The app gets deploy to the demo-dev namespace

## Confirm

    kubectl config set-context --current --namespace=demo-dev
    kubectl get all,ing
    kubectl describe ingress/web

Or kubes commands

    kubes get web ingress
    kubes describe web ingress

## Cleanup

    kubes delete

## Video

[![Watch the video](https://uploads-learn.boltops.com/jzyigjqv4a4zem1e32s9ypx8ylqn)](https://learn.boltops.com/courses/gke-kubes/lessons/gke-ingress-https-external-load-balancer-with-secret-resource-manually-created-zfaxj)

Note: Premium video content requires a subscription.

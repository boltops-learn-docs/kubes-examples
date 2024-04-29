<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-learn/kubes-examples/blob/master/yaml/google/elb7-https-pre-shared/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

# External HTTPS Load Balancer with GKE and Automated SSL Rotation Kubes Example

[![BoltOps Badge](https://img.boltops.com/boltops/badges/boltops-badge.png)](https://www.boltops.com)

Example project shows how to use a pre-shared Google SSL Cert with GKE.

Relevant Links:

* Google Cloud Docs: [Using multiple SSL certificates in HTTPS load balancing with Ingress - Specifying certificates for your Ingress: Pre-Shared Certs](https://cloud.google.com/kubernetes-engine/docs/how-to/ingress-multi-ssl#pre-shared-certs)
* [Google SSL Cert Rotation Tool](https://github.com/boltops-tools/google-ssl-cert): Commands to help rotate the Google SSL Cert.
* [Kubes](https://kubes.guru/): Kubernetes App Deployment Tool

## Configure Env Vars

    export GOOGLE_APPLICATION_CREDENTIALS=/path/to/gcp/credentials.json
    export GOOGLE_PROJECT=replace-with-your-project-id
    export REPO=gcr.io/$GOOGLE_PROJECT/demo

## Create Google SSL Cert

    cd ~/environment/cert-files
    google-ssl-cert create cert-demo

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

## Rotate Google SSL Cert: Prune

    cd ~/environment/cert-files
    google-ssl-cert create cert-demo
    cd ~/environment/kubes-examples/yaml/google/elb7-https-pre-shared
    kubes deploy
    google-ssl-cert prune cert-demo

## Cleanup

    kubes delete

## Video

[![Watch the video](https://uploads-learn.boltops.com/ca9zqjmrkpd20ubv6fx9xpyxq0d7)](https://learn.boltops.com/courses/gke-kubes/lessons/gke-ingress-https-external-load-balancer-with-pre-shared-cert-and-automating-ssl-cert-rotation)

Note: Premium video content requires a subscription.

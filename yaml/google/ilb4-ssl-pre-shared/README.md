<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-learn/kubes-examples/blob/master/yaml/google/ilb4-ssl-pre-shared/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

# GKE Ingress HTTPS Internal Load Balancer with Automated SSL Rotation Kubes Example

[![BoltOps Badge](https://img.boltops.com/boltops/badges/boltops-badge.png)](https://www.boltops.com)

Example project shows how to use a SSL Cert Kubernetes Secret resource with GKE for an Internal Load Balancer.

We'll create these Kubernetes resources:

1. [deployment](deployment.yaml): Run nginx web server pods.
2. [service](service.yaml): Expose an endpoint to reach the nginx pods.
3. [ingress](ingress.yaml): Expose an endpoint to reach the nginx pods.

Relevant Tools and Docs:

* Relevant Google Cloud Docs: [Configuring Ingress for Internal HTTP(S) Load Balancing: HTTPS between client and load balancer](https://cloud.google.com/kubernetes-engine/docs/how-to/internal-load-balance-ingress#https_between_client_and_load_balancer)
* [Google SSL Cert Rotation Tool](https://github.com/boltops-tools/google-ssl-cert): Commands to help rotate the Google SSL Cert.
* [Kubes](https://kubes.guru/): Kubernetes App Deployment Tool

## Configure Env Vars

    export GOOGLE_APPLICATION_CREDENTIALS=/path/to/gcp/credentials.json
    export GOOGLE_PROJECT=replace-with-your-project-id
    export GOOGLE_REGION=replace-with-your-region
    export REPO=gcr.io/$GOOGLE_PROJECT/demo

## Create Google SSL Cert

    cd ~/environment/cert-files
    export GOOGLE_REGION=us-central1
    google-ssl-cert create cert-demo --no-global

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

## Test

To test internal load balancers you need to be inside the network. You can start a pod and curl from there:

    kubectl run tester -it --rm --restart=Never --image=amazonlinux:2 -- bash
    kubectl delete pod tester

Then from with in the pod:

    curl -k https://your-domain.com # if the cert is self signed
    curl https://your-domain.com

## Rotate Google SSL Cert: Prune

    cd ~/environment/cert-files
    export GOOGLE_REGION=us-central1
    google-ssl-cert create cert-demo --no-global
    cd ~/environment/kubes-examples/yaml/google/ilb4-ssl-pre-shared
    kubes deploy
    google-ssl-cert prune cert-demo --no-global

## Cleanup

    kubes delete

## Video

[![Watch the video](https://uploads-learn.boltops.com/40j0tv5y3hpx8vmmbvhgt9105vrx)](https://learn.boltops.com/courses/gke-kubes/lessons/gke-ingress-https-internal-load-balancer-with-automated-ssl-rotation-kubes-example)

Note: Premium video content requires a subscription.

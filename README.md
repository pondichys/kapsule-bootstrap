# Bootstraping a Kapsule k8s cluster with ArgoCD

This repository contains some code to bootstrap a Scaleway Kapsule Kubernetes cluster using ArgoCD.

## Concepts

The idea is to use the [app of apps](https://argo-cd.readthedocs.io/en/stable/operator-manual/declarative-setup/#app-of-apps) ArgoCD pattern.

The file [application-kapsule-bootstrap.yaml](application-kapsule-bootstrap.yaml) defines an ArgoCD application that uses the folder [kapsule-charts](https://github.com/pondichys/kapsule-bootstrap/tree/main/kapsule-charts) this repository as source and the `default` namespace of the local Kubernetes cluster where ArgoCD runs as target. This application is an umbrella that contains the other applications to be deployed.

It consists of an Helm chart whose templates directory contains all manifests that must be applied. The application templates are using the standard Helm charts as source to deploy into the cluster.

## Usage

1. Create a new Scaleway Kapsule cluster.

1. Install ArgoCD.

1. Clone this repository.

1. Apply the application-kapsule-bootstrap.yaml manifests.

1. Check the deployment of the application in ArgoCD (through the UI or the CLI).

1. Only the bootstrap app is automatically synchronized. You have to manually sync the other apps.


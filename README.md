# Kubernetes Manifest Repository

This repository contains Kubernetes manifests that are triggered by the `update-manifest` Jenkins pipeline. When changes are committed to this repository, ArgoCD will automatically pull the latest manifests to deploy to the Kubernetes cluster.

## Features

- Automated deployment to Kubernetes using ArgoCD.
- Jenkins pipeline for managing manifest updates.
- Supports version tagging for Docker images via build numbers.
- Configuration for creating a Kubernetes cluster using `kind` with a YAML file.
- Setup for a Matrix server and NGINX ingress controller.

## Prerequisites

Before using this repository, ensure that you have the following:

- A running Kubernetes cluster (can be created using `kind`).
- ArgoCD installed and configured to watch this repository.
- Jenkins configured to run the `update-manifest` pipeline.
- Access to a GitHub account for managing the repository.

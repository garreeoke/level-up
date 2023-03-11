# Level Up - A Hands on Crossplane Workshop for AWS

There are three folders in this repo

* **1-Managed Resources** - Individual Managed resources 
* **2-XRD** - Create a XRD and Composition to build everything with one API call
* **3-Other** - Provider configuration

## Setup
A kubernetes cluster with Crossplane is required. The easiest way to get started with Crossplane is to install UXP in two steps.
1. [Install the up cli](https://docs.upbound.io/cli/) 
2. [Install UXP](https://docs.upbound.io/uxp/install/)

If preferred, you can also [install open source Crossplane](https://docs.crossplane.io/v1.10/getting-started/install-configure/).

### Install AWS Provider
1. [Check the Upbound marketplace](https://marketplace.upbound.io/providers/upbound/provider-aws/) for the latest version of the provider (ie-v0.26.0).
2. Update the spec.package in [the provider config](./providers/aws-provider.yaml) with the latest version.
3. `kubectl -f providers/aws-default-provider.yaml`
4. `kubectl get providers` and verify INSTALLED and HEALTHY are true.

### Configure Provider
1. [Create a Kubernetes secret for AWS](https://docs.upbound.io/quickstart/provider-aws/#create-a-kubernetes-secret-for-aws)
2. Install the provider config `kubectl apply -f providers/aws-provider-cfg.yaml`
3. `kubectl get providerconfigs` and verify the default provider is created

## Demo

Go in to each folder below to follow the README for each section. These do not have to be done in order.
However, if you want to see the true power of Crossplane and Upbound's IAM Builder, follow them in order.

* [Managed Resources](./1-managed-resources)
* [Composite Resource Definition](./2-composite-resource-definition)
* [IAM Builder](./3-xrds-iam-builder)

Each folder will create the following:
* One S3 bucket
* Ownership preferences on the S3 bucket
* A new role, policy and role policy attachment

## Notes
Each folder can be run and there should be no naming conflicts.

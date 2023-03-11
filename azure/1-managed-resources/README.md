# Level Up - A Hands on Crossplane Workshop for AWS

## Install AWS Provider
1. [Check the Upbound marketplace](https://marketplace.upbound.io/providers/upbound/provider-aws/) for the latest version of the provider (ie-v0.26.0).
2. Update the spec.package in [the provider config](./providers/aws-provider.yaml) with the latest version.
3. `kubectl -f providers/aws-default-provider.yaml`
4. `kubectl get providers` and verify INSTALLED and HEALTHY are true.

## Configure Provider
1. [Create a Kubernetes secret for AWS](https://docs.upbound.io/quickstart/provider-aws/#create-a-kubernetes-secret-for-aws)
2. Install the provider config `kubectl apply -f providers/aws-provider-cfg.yaml`
3. `kubectl get providerconfigs` and verify the default provider is created

## Excercises

Go in to each folder below to follow the README for each section.

* [Managed Resources](1-managed-resources)
* [Composite Resource Definition](2-xrd)

Each folder will create the following:
* Resource Group
* Virtual Machine
* Virtual Network
* Subnet
* VM Nic
* Security group & association
* Kubernetes secret

## Notes
Each folder can be run and there should be no naming conflicts.

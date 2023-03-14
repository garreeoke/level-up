# Level Up - A Hands on Crossplane Workshop for Azure

## Install Azure Provider
1. [Check the Upbound marketplace](https://marketplace.upbound.io/providers/upbound/provider-azure/) for the latest version of the provider (ie-v0.26.0).
2. Update the spec.package in [the provider config](./providers/az-provider.yaml) with the latest version.
3. `kubectl -f providers/az-provider.yaml`
4. `kubectl get providers` and verify INSTALLED and HEALTHY are true.

## Configure Provider
1. [Create a Kubernetes secret for Azure](https://docs.upbound.io/quickstart/provider-azure/#create-a-kubernetes-secret-for-azure)
2. Install the provider config `kubectl apply -f 3-other/az-provider-cfg.yaml`
3. `kubectl get providerconfigs` and verify the default provider is created

## Install Kubernetes Provider
1. `kubectl apply -f 3-other/kubernetes-provider.yaml`

## Install Kubernetes provider config
1. `kubect apply -f 3-other/kubernetes-provider-cfg.yaml`

## Excercises

Go in to each folder below to follow the README for each section.

* [Managed Resources](1-managed-resources)
* [Composite Resource Definition](2-xrd)

Each folder will create one the following:
* Resource Group
* Virtual Machine
* Virtual Network
* Subnet
* VM Nic
* Security group & association
* Kubernetes secret

## Notes
Each folder can be run and there should be no naming conflicts.

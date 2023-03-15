# Level Up - A Hands on Crossplane Workshop for AWS

## Install AWS Provider
1. Change directory to aws folder
2. [Check the Upbound marketplace](https://marketplace.upbound.io/providers/upbound/provider-aws/) for the latest version # of the provider (ie-v0.26.0).
3. Update the spec.package in [the provider config](./3-other/aws-provider.yaml) with the latest version.
4. `kubectl apply -f providers/aws-provider.yaml`
5. `kubectl get providers` and verify INSTALLED and HEALTHY are true.

## Configure Provider
1. [Create a Kubernetes secret for AWS](https://docs.upbound.io/quickstart/provider-aws/#create-a-kubernetes-secret-for-aws)
2. Install the provider config `kubectl apply -f 3-other/aws-provider-cfg.yaml`
3. `kubectl get providerconfigs` and verify the default provider is created

## Excercises

Go in to each folder below to follow the README for each section.

* [Managed Resources](1-managed-resources)
* [Composite Resource Definition](2-xrd)

## Notes
Each folder can be run and there should be no naming conflicts.

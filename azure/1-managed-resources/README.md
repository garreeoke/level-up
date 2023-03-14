# Managed Resources - Azure

This folder has each managed resource in a file to be built by itself as a single resource. Installing all of them will
create the following:

Each folder will create the following:
* Resource Group
* Virtual Machine
* Virtual Network
* Subnet
* VM Nic
* Security group & association
* Kubernetes secret

This is a very basic approach to using Managed resources in Crossplane. It uses only the managed resources from the
provider and not within a composition. It still provides the benefits of using the kubernetes resource model, but does not
give the simple self-service API of using compositions.

## Steps
1. Change directories to azure/1-managed-resources
2. In each file in the folder, search and replace the word **CHANGE-ME** and replace with your own name.
3. To test the provider setup, deploy the resource-group only
   * `kubectl apply -f resource-group.yaml`
4. Once the resource group is successfully deployed, apply all manifests in the folder:
    * `kubectl apply -f .`
5. Verify managed resources:
    * `kubectl get managed -l crossplane-demo=levelup-managed-resources`
6. Cleanup:
    * `kubectl delete -f .`

## Next
* [Build the same resources in a composition](../2-xrd)

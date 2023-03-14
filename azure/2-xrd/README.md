# Composite Resource Definitions (XRD) and Compositions

This folder has a definition and composition YAML file. The definition will be the new API created in Kubernetes
and the composition is will build the following resources with the new API.

* Resource Group
* Virtual Machine
* Virtual Network
* Subnet
* VM Nic
* Security group & association
* Kubernetes secret

This approach shows how the power of Crossplane XRDs combined with compositions will enable building a group of resources
with a single API call.

## Steps
1. Change directories to azure/2-xrd
2. Create the definition and composition on you cluster: 
   * `kubectl apply -f .
3. Modify the claim file (examples/claim-vm.yaml) and modify **CHANGE-ME** to something else.
4. Apply the claim:
   * `kubectl apply -f examples/claim-vm.yaml`
5. Verify managed resources: 
   * `kubectl get managed -l crossplane.io/claim-name=levelup-xrd-CHANGE-ME`
6. Cleanup:
   * `kubectl delete -f examples/claim-vm.yaml`

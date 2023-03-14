# Composite Resource Definitions (XRD) and Compositions

This folder has a definition and composition YAML file. The definition will be the new API created in Kubernetes
and the composition will build the following resources with the new API.

* One S3 bucket
* Ownership preferences on the S3 bucket
* A new role, policy and role policy attachment

This approach shows how the power of Crossplane XRDs combined with compositions will enable building a group of resources
with a single API call.

## Steps
1. Create the definition and composition on you cluster: 
   * `kubectl apply -f defintion.yaml`
   * `kubectl apply -f composition.yaml`
2. Modify the claim file (examples/claim-s3.yaml) and modify **torg** to something else.
3. Apply the claim:
   * `kubectl apply -f examples/claim-s3.yaml`
4. Verify managed resources: 
   * `kubectl get managed -l crossplane.io/claim-name=levelup-xrd-torg`
5. Cleanup:
   * `kubectl delete -f examples/claim-s3.yaml`
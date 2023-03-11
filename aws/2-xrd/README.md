# Composite Resource Definitions (XRD) and Compositions

This folder has a definition and composition YAML file. The definition will be the new API created in Kubernetes
and the composition is will build the following resources with the new API.

* One S3 bucket
* Ownership preferences on the S3 bucket
* A new role, policy and role policy attachment

This approach shows how the power of Crossplane XRDs combined with compositions will enable building a group of resources
with a single API call.

## Steps
1. Follow [setup](../README.md)
2. Create the definition and composition on you cluster: 
   * `kubectl apply -f defintion.yaml`
   * `kubectl apply -f composition.yaml`
3. Modify the claim file (examples/s3bucket.yaml) and modify **changme** to something else.
4. Apply the claim:
   * `kubectl apply -f examples/s3bucket.yaml`
5. Verify managed resources: 
   * `kubectl get managed -l crossplane.io/claim-name=crossplane-demo-torg-xrd`
6. Cleanup:
   * `kubectl delete -f examples/s3bucket.yaml`

## Next
* [Use the Upbound Builder](../3-xrds-iam-builder)
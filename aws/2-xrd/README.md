# Composite Resource Definitions (XRD) and Compositions

This folder has a definition and composition YAML file. The definition will be the new API created in Kubernetes
and the composition will build the following resources with the new API.

* One S3 bucket
* Ownership preferences on the S3 bucket
* A new role, policy and role policy attachment

This approach shows how the power of Crossplane XRDs combined with compositions will enable building a group of resources
with a single API call.

## Apply the definition, composition and claim
Review the defintion and composition files before applying.

1. Change directories to aws/2-xrd
2. Apply the definition and composition on you cluster: 
   * `kubectl apply -f .`
3. Modify the claim file (examples/claim-s3.yaml) and modify **CHANGE-ME** to your name or other identifier.
4. Apply the claim:
   * `kubectl apply -f examples/claim-s3.yaml`
5. Verify managed resources: 
   * `kubectl get managed -l crossplane.io/claim-name=levelup-xrd-CHANGE-ME`

## Modify the definition, composition and claim
In these steps we will add a parameter to the definition to add a tag to the s3 bucket.

1. Modify the definition file and find the three commented out lines starting with "owner:" and uncomment them
2. Modify the composition file and find the two commented out lines starting with "- fromFieldPath: spec.owner" and uncomment them
3. Apply the changes
   * `kubectl apply -f .`
4. Nothing happens to the existing composite resource yet until we modify the claim
5. Modify the examples/claim-s3.yaml file and uncomment #owner: "CHANGE-ME"
6. Apply the claim
   * `kubectl apply -f examples/claim-s3.yaml`
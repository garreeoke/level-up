# Managed Resources - AWS

This folder has each managed resource in a file to be built by itself as a single resource. Installing all of them will
create the following:

* One S3 bucket
* Ownership preferences on the S3 bucket
* A new role, policy and role policy attachment

This is a very basic approach to using Managed resources in Crossplane. It uses only the managed resources from the
provider and not within a composition. It still provides the benefits of using the kubernetes resource model, but does not
give the simple self-service API of using compositions.

## Steps
1. In each file in the folder, search and replace the word **CHANGE-ME** and replace with your own name.
2. To test the provider setup, deploy the s3 bucket only
   * `kubectl apply -f ./bucket.yaml`
3. Once the bucket is successfully deployed, apply all manifests in the folder:
   * `kubectl apply -f ./`
4. Verify managed resources: 
   * `kubectl get managed -l crossplane-demo=levelup-managed-resources`
5. Cleanup:
   * `kubectl delete -f ./`

## Next
* [Build the same resources in a composition](../2-xrd)
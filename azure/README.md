# TechMahinda - Upbound 

This repo was made for TechMahindar to produce a demo for their client.

## Demo Deliverables

- Two XRDs
  - One for creating a virtual machine
  - One for creating either a redis or postgres database

## Repo Contents

There are 3 folders in the repo.

| Folder              | Description                                                                                                                 |
|---------------------|-----------------------------------------------------------------------------------------------------------------------------|
| 1-managed-resources | Individual managed resources that can be deployed individually. This should be used just for testing the individual objects |
| 2-api               | API definitions, compositions and claims used for reusable deployment of all managed resources.                             |
| 3-other             | Provider and other files used while making this.                                                                            |

## Demo

1. [Install UXP](https://docs.upbound.io/uxp/install/) on a Kubernetes cluster
   1. Or use [Helm install](https://github.com/upbound/universal-crossplane#installation-with-helm-3) if unable to run the up cli.
2. [Setup your Azure provider](https://marketplace.upbound.io/providers/upbound/provider-azure/v0.28.0/docs/quickstart).
3. [Setup Kubernetes provider](https://github.com/crossplane-contrib/provider-kubernetes#install)
4. If desired, try out deploying all of the managed resources in [1-managed-resources](1-managed-resources)
   1. Create: `kubectl apply -f 1-managed-resources/`
   2. View: `kubectl get managed l=tm.demo.io/landingzone=tm-demo-1`
   3. Delete: `kubectl delete -f 1-managed-resources/`
5. Use the reusable API with backing compositions in [2-api](2-api)
   1. Install API definition and compositions: 
      - Virtual machine: `kubectl apply -f 2-api/vm`
      - Database: `kubectl apply -f 2-api/database`
   2. Virtual Machine: 
      - Create: `kubectl apply -f 2-api/example/claim-vm.yaml`
      - View: `kubectl get managed -l crossplane.io/claim-vm.yaml`
      - Delete: `kubectl delete -f 2-api/example/claim-vm`
   3. Redis: 
      - Create `kubectl apply -f 2-api/example/claim-db-redis.yaml`
      - View: `kubectl get managed -l crossplane.io/claim-db-redis.yaml`
      - Delete: `kubectl delete -f 2-api/example/claim-db-redis.yaml`
   4. Postgres:
      - Create `kubectl apply -f 2-api/example/claim-db-postgres.yaml`
      - View: `kubectl get managed -l crossplane.io/claim-db-postgres.yaml`
      - Delete: `kubectl delete -f 2-api/example/claim-db-postgres.yaml`
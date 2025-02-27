# argocd-example-application

## Installation
- Openshift Pipelines
- Openshift GitOps

```
oc apply -f ./cluster-configuration
```
Wait till both operators are installed

## Get Argo CD configuration
Get Argo CD server address.
```
oc -n openshift-gitops get route openshift-gitops-server -o jsonpath='{.spec.host}'
```

Get Argo CD admin password:
```
oc extract secret/openshift-gitops-cluster -n openshift-gitops --to=-
```

## Deploy Argo CD application 

```
oc apply -f argocd/app/app-discount.yaml
```

or


## Deploy Argo CD AppOfApps 

```
oc apply -f argocd/appOfApps/appOfApps-discount.yaml
```

Synchronize all the Argo CD applications

Show pod 
```
# oc get pod -n default -o wide
```

Export all resources to yaml
```
# oc get all --all-namespaces --export -o yaml > export-file.yaml
```

```
# oc get scc
# oc delete scc anyuid
# oc delete scc restricted
# oc adm policy reconcile-sccs 
```

Show pod 
```bash
$ oc get pod -n default -o wide
```

Export all resources to yaml
```bash
$ oc get all --all-namespaces --export -o yaml > export-file.yaml
```

```bash
# Show the current SCC
$ oc get scc

# Delete the anyuid and restricted SCC
$ oc delete scc anyuid
$ oc delete scc restricted

$ oc adm policy reconcile-sccs 
$ oc adm policy reconcile-sccs --confirm
```


```yaml
kind: Pod


```

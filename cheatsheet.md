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

Get pod-name and pod-scc
```bash
$ oc get pods <pod-name> -o=jsonpath='{.metadata.name}{"¥t"}{.metadata.annotations}{"¥n"}'
# output will be as below
# <pod-name> map[openshift.io/scc:anyuid]
```

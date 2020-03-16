Show pod 
```bash
$ oc get pod -n default -o wide
```

OpenShift docker/kubelet status-stop-start-status
```bash
$ systemctl status docker atomic-openshift-node 
$ systemctl stop docker atomic-openshift-node
$ systemctl start docker atomic-openshift-node
$ systemctl status docker atomic-openshift-node 
```

Export all resources to yaml
```bash
$ oc get all --all-namespaces --export -o yaml > export-file.yaml
# --export remove the timestamp
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

Get name and fsGroups from SCC (Security Context Contrain)
```bash
$ oc get scc --no-headers | awk '{print "oc get scc "$1" -o jsonpath=@{.metadata.name}{.groups}@; echo ¥n"}' | sed 's/@/"/g' | sh
# .metadata.name = SCC Name
# .groups = SCC fsGroups
# sed to change the @ to " at jsonpath grammar
# sample result: 
anyuid[system:cluster-admins]
hostaccess[]
restricted[system:authenticated]
```

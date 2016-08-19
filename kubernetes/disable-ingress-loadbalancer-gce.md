# Disable ingress loadbalancer on GCE

Since GLBC runs as a cluster addon, you cannot simply delete the RC. The easiest way to disable it is to do as follows:

IFF you want to tear down existing L7 loadbalancers, hit the /delete-all-and-quit endpoint on the pod:
```
$ kubectl get pods --namespace=kube-system
NAME                                               READY     STATUS    RESTARTS   AGE
l7-lb-controller-7bb21                             1/1       Running   0          1h
$ kubectl exec l7-lb-controller-7bb21 -c l7-lb-controller curl http://localhost:8081/delete-all-and-quit --namespace=kube-system
$ kubectl logs l7-lb-controller-7b221 -c l7-lb-controller --follow
...
I1007 00:30:00.322528       1 main.go:160] Handled quit, awaiting pod deletion.
```

Nullify the RC (but don't delete it or the addon controller will "fix" it for you)

```
$ kubectl scale rc l7-lb-controller --replicas=0 --namespace=kube-system
```
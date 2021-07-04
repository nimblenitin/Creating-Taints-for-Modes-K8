# Creating-Taints-for-Modes-K8
Taints allows to run Pods on Nodes which can tolerate the Taint for a Pod; thus restricting running pods on Nodes. Their types include-
NoSchedule- won't schedule unless nodes tolerates taint
NoExecute- will throw existing pods whose taint is not tolerated
Prefernotolerate- will allow pods to run on non tolerated nodes if tolerated ones not found.

Simple example to run a Pod on Taint tolerated Node-

Steps followed:

*As Root*
```

1. Add Taint to Node after finding the Node name.
$ kubectl get nodes 
$ kubectl taint nodes <Node name> cpu=full:NoSchedule

2. Create the Pod by using YAML with Taint mentioned
$ kubectl apply -f pods-with-taint --record

3. Check whether the Pod was created in the correct Node with corresponding Taint tolerance.
$ kubectl get pods -o wide

```
*As Root*

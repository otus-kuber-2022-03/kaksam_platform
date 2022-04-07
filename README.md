# kaksam_platform
kaksam Platform repository

<details>
<summary> <b>HW01 Kubernetes-intro</b> </summary>

- причины по которым поды поднимаются  
  - coredns - replicaset(deploymnet) - гарантирует поднятие пода, на лучайной ноде
  - kube-proxy - daemonset - говрит о том, что каждая нода будет иметь данный под 
  - etcd, kube-apiserver, kube-scheduler, kube-controller-manager - static pod, как я понял манифесты дежалт в /etc/kubernetes/manifests/, kubelet запущеный на ноде чекает состояние. если под умер переподнимает. 

1. Dockerfile was created, image was created and pushed to kaksam/homework:1.0
2. web-pod.yaml with kaksam/homework:1.0 image, tested by  'kubectl port-forward'
3. frontend-pod.yaml was prepared with kaksam/homework-frontend:1.0 by ad-hoc command
4. applyed frontend-pod.yaml with error status.
5. added env-variables to frontend-pod-health.yaml to fix the issue
</details>

<details>
<summary> <b>HW02 Kubernetes-controllers</b> </summary>

**Why changes of version in replica set doesn't apply new version for pod:**
 - ReplicaSet doesn't check changes of images

1. Created and pushed kaksam/paymentservice:v0.0.1 and v0.0.2
2. frontend-replicaset.yaml and frontend-deployment.yaml prepared 
3. paymentservice-replicaset.yaml paymentservice-deployment.yaml prepared 
4. paymentservice-deployment-bg.yaml for BlueGreen deployment using `maxSugre` and `maxUnavailable`
5. paymentservice-deployment-reverse.yaml for reverse deployment using `maxSugre` and `maxUnavailable`
6. Added `readinessProbe` for paymentservice-deployment.yaml
7. nodeexporter-daemonset.yaml using toleration for master node usage
</details>

<details>
<summary> <b>HW03 Kubernetes-security</b> </summary>

Used kubctl cli for generate manifests 
**task01:**
```
# kubectl create sa bob -o yaml > 01-sa-bob.yaml
# kubectl create clusterrolebinding bob-admin --clusterrole=admin --serviceaccount=default:bob -o yaml > 02-bob-admin.yaml
# kubectl create sa dave -o yaml > 03-sa-dave.yaml
```

**task02:**
```
# kubectl create ns prometheus -o yaml > 01-create-ns.yaml
# kubectl create sa carol --namespace=prometheus -o yaml > 02-carol.yaml
# kubectl create clusterrole pod-reader --verb=get,list,watch --resource=pods --namespace=prometheus -o yaml > 03-rolebinding.yaml
# kubectl create clusterrolebinding carol-pod --clusterrole=pod-reader --group=system:serviceaccounts:prometheus -o yaml >> 03-rolebinding.yaml
```

**task03:**
```
# kubectl create ns dev -o yaml > 01-create-ns.yaml
# kubectl create sa jane --namespace=dev -o yaml > 02-jane.yaml
# kubectl create rolebinding jane-admin --clusterrole=admin --namespace=dev --serviceaccount=dev:jane -o yaml > 03-jane-damin.yaml
# kubectl create sa ken --namespace=dev -o yaml > 04-ken.yaml
# kubectl create rolebinding ken-view --clusterrole=view --namespace=dev --serviceaccount=dev:ken -o yaml > 05-ken-view.yaml
```
</details>
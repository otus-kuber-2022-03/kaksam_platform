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

**Why changes of version in replica set doesn't apply new version for pod:
 - ReplicaSet doesn't check changes of images

1. Created and pushed kaksam/paymentservice:v0.0.1 and v0.0.2
2. frontend-replicaset.yaml and frontend-deployment.yaml prepared 
3. paymentservice-replicaset.yaml paymentservice-deployment.yaml prepared 
4. paymentservice-deployment-bg.yaml for BlueGreen deployment using `maxSugre` and `maxUnavailable`
5. paymentservice-deployment-reverse.yaml for reverse deployment using `maxSugre` and `maxUnavailable`
6. Added `readinessProbe` for paymentservice-deployment.yaml
7. nodeexporter-daemonset.yaml using toleration for master node usage
</details>
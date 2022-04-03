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
# kaksam_platform
kaksam Platform repository

# HW01 (kubernetes-intro)

- причины по которым поды поднимаются  
  - coredns - replicaset(deploymnet) - гарантирует поднятие пода, на лучайной ноде
  - kube-proxy - daemonset - говрит о том, что каждая нода будет иметь данный под 
  - etcd, kube-apiserver, kube-scheduler, kube-controller-manager - static pod, как я понял манифесты дежалт в /etc/kubernetes/manifests/, kubelet запущеный на ноде чекает состояние. если под умер переподнимает. 

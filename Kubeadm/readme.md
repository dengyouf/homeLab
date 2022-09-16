```
~# kubectl  get nodes -o wide
NAME                STATUS   ROLES                  AGE    VERSION   INTERNAL-IP     EXTERNAL-IP   OS-IMAGE             KERNEL-VERSION       CONTAINER-RUNTIME
kubeadm-master-01   Ready    control-plane,master   3h9m   v1.22.5   192.168.1.200   <none>        Ubuntu 18.04.6 LTS   4.15.0-192-generic   docker://20.10.6
kubeadm-node-01     Ready    <none>                 3h6m   v1.22.5   192.168.1.201   <none>        Ubuntu 18.04.6 LTS   4.15.0-192-generic   docker://20.10.6
kubeadm-node-02     Ready    <none>                 3h5m   v1.22.5   192.168.1.202   <none>        Ubuntu 18.04.6 LTS   4.15.0-192-generic   docker://20.10.6
kubeadm-node-03     Ready    <none>                 3h5m   v1.22.5   192.168.1.203   <none>        Ubuntu 18.04.6 LTS   4.15.0-192-generic   docker://20.10.6
```
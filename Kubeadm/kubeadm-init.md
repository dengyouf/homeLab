# 初始化Master节点

```
192.168.1.200 kubeadm-master-01
192.168.1.201 kubeadm-node-01
192.168.1.202 kubeadm-node-02
192.168.1.203 kubeadm-node-03
# 用来扩展集群为高可用集群
192.168.1.200 kubeadm-vip.linux.io

```

```
kubeadm init --kubernetes-version=v1.22.5 \
    --control-plane-endpoint=kubeadm-vip.linux.io \
    --apiserver-advertise-address=0.0.0.0 \
    --pod-network-cidr=10.244.0.0/16 \
    --service-cidr=10.96.0.0/12 \
    --image-repository=registry.cn-hangzhou.aliyuncs.com/google_containers\   --ignore-preflight-errors=Swap | tee kubeadm-init.log


kubeadm init --kubernetes-version=v1.22.5     --control-plane-endpoint=kubeadm-vip.linux.io     --apiserver-advertise-address=0.0.0.0     --pod-network-cidr=10.244.0.0/16       --service-cidr=10.96.0.0/12     --image-repository=registry.cn-hangzhou.aliyuncs.com/google_containers     --ignore-preflight-errors=Swap | tee kubeadm-init.log
```

# 部署网络插件

```
kubectl apply -f calico-v3.24.1.yaml
```

- https://raw.githubusercontent.com/projectcalico/calico/v3.24.1/manifests/calico.yaml

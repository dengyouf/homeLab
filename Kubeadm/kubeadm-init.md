```
---------------------------------------------------------------------------------
|项目              	|信息                                                 	|
---------------------------------------------------------------------------------
|主机名             	|kubeadm-master-01                                  	|
|IP地址            	|192.168.1.200                                    	|
|系统版本            	|Ubuntu 18.04.6 LTS                                 	|
|内核版本            	|4.15.0-192-generic                                 	|
|核心数             	|2                                                  	|
|已登录用户           	|2                                                  	|
|系统时间            	|22-09-15 14:06:42                                  	|
|系统运行            	|0 days 3 hours 20 minutes 14 seconds               	|
|当前用户            	|root                                               	|
|进程数             	|204                                                	|
|Docker版本        	|20.10.18                                           	|
---------------------------------------------------------------------------------
|监控项   	|使用率(%)     	|总量         	|已用         	|可用         	|
---------------------------------------------------------------------------------
|负载         	|53.00      	|1分钟3.03    	|5分钟3.81    	|15分钟5.62   	|
|内存         	|15.68      	|容量:7951M   	|已用:952M    	|可用:6704M   	|
|根目录        	|12         	|容量:79G     	|已用:8.4G    	|可用:66G     	|
|           	|           	|           	|           	|           	|
---------------------------------------------------------------------------------
```

```
192.168.1.200 kubeadm-master-01
192.168.1.201 kubeadm-node-01
192.168.1.202 kubeadm-node-02
192.168.1.203 kubeadm-node-03
# 用来扩展集群为高可用集群
192.168.1.200 kubeadm-vip.linux.io
```

# 初始化Master节点

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

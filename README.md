# 使用方法
注意，请使用sealos最新版本，如果是老版本sealos安装的集群不会自动生成sealos配置文件，需要自己手动配置，会输出日志教你如何配置

本地拉取(先到[release页面](https://github.com/sealstore/dashboard/releases)下载好tar包到本地)：
```
wget https://github.com/sealstore/dashboard/releases/download/v2.0.0-bata5/dashboard.tar
sealos install --pkg-url dashboard.tar
```
或者远程拉取：
```
sealos install --pkg-url https://github.com/sealstore/dashboard/releases/download/v2.0.0-bata5/dashboard.tar
```
# 访问
https://你的master地址:32000

如chrome访问有问题就用火狐，或者自签[dashboard证书](https://sealyun.com/faq)

# 获取登录token

高版本dashboard为了安全已经把SKIP按钮废弃了，所以需要自己拿token登录

dashboard1.0用：
```
kubectl get secret -nkube-system $(kubectl get secret -n kube-system|grep dashboard-token |awk '{print $1}') -o jsonpath='{.data.token}'  | base64 --decode
```

2.0 版本用下面命令获取token:
```
kubectl get secret -nkubernetes-dashboard $(kubectl get secret -n kubernetes-dashboard|grep dashboard-token |awk '{print $1}') -o jsonpath='{.data.token}'  | base64 --decode
```

# dashboard.tar如何构造
dashboard.tar里包含yaml文件与镜像文件等

```
[root@iZj6c2ihvsz4y7barissm4Z test]# cat config 
LOAD docker load -i image.tar
APPLY kubectl apply -f manifests
DELETE kubectl delete -f manifests
REMOVE sleep 10 && docker rmi -f k8s.gcr.io/kubernetes-dashboard-amd64:v1.10.0
[root@iZj6c2ihvsz4y7barissm4Z test]# ls
config  image.tar  manifests
```
把上述三个文件打包

```
[root@iZj6c2ihvsz4y7barissm4Z test]#  tar cvf dashboard.tar config image.tar manifests
```

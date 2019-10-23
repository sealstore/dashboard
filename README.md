# 使用方法
本地拉取(先到[release页面](https://github.com/sealstore/dashboard/releases)下载好tar包到本地)：
```
sealos install --pkg-url dashboard.tar
```
远程拉取：
```
sealos install --pkg-url https://github.com/sealstore/dashboard/releases/download/v1.10.0/dashboardv1.10.0.tar 
```
# 访问
https://你的master地址:32000

如chrome访问有问题就用火狐，或者自签[dashboard证书](https://sealyun.com/faq)

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

# 获取登录token

高版本dashboard为了安全已经把SKIP按钮废弃了，所以需要自己拿token登录
```
kubectl get secret -nkube-system $(kubectl get secret -n kube-system|grep dashboard-token |awk '{print $1}') -o jsonpath='{.data.token}'  | base64 --decode
```

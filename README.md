# 使用方法
注意，请使用sealos最新版本，如果是老版本sealos安装的集群不会自动生成sealos配置文件，需要自己手动配置，会输出日志教你如何配置

本地拉取(先到[release页面](https://github.com/sealstore/dashboard/releases)下载好tar包到本地)：
```
wget https://github.com/sealstore/dashboard/releases/download/v1.0/kuboard.tar
sealos install --pkg-url kuboard.tar
```
或者远程拉取：
```
sealos install --pkg-url  https://github.com/sealstore/dashboard/releases/download/v1.0/kuboard.tar
```
# 访问
http://你的master地址:32567

# 获取登录token

管理员用户
```
kubectl -n kube-system get secret $(kubectl -n kube-system get secret | grep kuboard-user | awk '{print $1}')  -o jsonpath='{.data.token}'  | base64 --decode
```

只读用户:
```
kubectl -n kube-system get secret $(kubectl -n kube-system get secret | grep kuboard-viewer | awk '{print $1}') -o jsonpath='{.data.token}'  | base64 --decode
```

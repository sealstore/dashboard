# dashboard

- [官方dashboard](https://github.com/sealstore/dashboard/tree/dashboard)       [项目主页](https://github.com/kubernetes/dashboard)
- [kuboard](https://github.com/sealstore/dashboard/tree/kuboard)           [官网链接](https://kuboard.cn?from=sealyun)


## 使用方法
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

# 为什么要用此包
1. tar包中包含yaml文件，镜像文件，离线无忧
2. 即便你没有镜像仓库，sealos也会帮你把镜像导入到集群节点上
3. 安装完日志中直接显示界面上访问的登录token
4. 对官方yaml文件作了一些修改，让dashboard具备管理员权限

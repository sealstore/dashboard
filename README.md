# dashboard

- [官方dashboard](https://github.com/sealstore/dashboard/tree/dashboard)


## 使用方法
注意，请使用sealos最新版本，如果是老版本sealos安装的集群不会自动生成sealos配置文件，需要自己手动配置，会输出日志教你如何配置

本地拉取(先到[release页面](https://github.com/sealstore/dashboard/releases)下载好tar包到本地)：
```
wget https://github.com/sealstore/dashboard/releases/download/v2.0.0-bata.5/dashboard.tar
sealos install --pkg-url dashboard.tar
```
或者远程拉取：
```
sealos install --pkg-url https://github.com/sealstore/dashboard/releases/download/v2.0.0-bata.5/dashboard.tar
```

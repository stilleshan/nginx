# nginx
docker 快速部署 nginx 环境,适用于 HTML 页面站点,简单 Web 测试环境以及反向代理 docker 容器等需求.

## 部署
### docker
在 root 目录下 git clone 本仓库用来挂载相关配置文件
```shell
cd ~
git clone https://github.com/stilleshan/nginx.git
```
启动 nginx 容器
```shell
docker run -d --name=nginx --restart=always \
    --network host \
    -v ~/nginx/conf/nginx.conf:/etc/nginx/nginx.conf \
    -v ~/nginx/vhost:/etc/nginx/conf.d/vhost \
    -v ~/nginx/ssl:/etc/nginx/ssl \
    -v ~/nginx/html:/usr/share/nginx/html \
    nginx
```

### docker compose
```shell
cd ~
git clone https://github.com/stilleshan/nginx.git
cd nginx
docker-compose up -d
```

## 说明
`~/nginx/conf` 用于存放`nginx 主配置`文件  
> conf 目录下为官方 nginx.conf 配置文件,已新增 include vhost 目录以方便挂载多站点配置文件. 

`~/nginx/vhost` 用于存放`各站点 conf 配置`文件  
> vhost 目录中已有常用的 conf 样本,参考修改域名和证书路径.  

`~/nginx/ssl` 用于存放`证书`文件  
> ssl 目录有样本 conf 所需证书文件,如需删除请连同 conf 样本一起删除,避免 nginx 报错.

`~/nginx/html` 用于存放`网页`文件  
> html 目录为站点根目录,自行创建子目录存放网页以用来部署多个站点.

## 链接
[Docker 打造支持快速部署和迁移的 Nginx 环境](https://www.ioiox.com/archives/91.html)


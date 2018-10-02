# 站在巨人的肩膀上

使用docker作为开发环境的部署，测试laravel框架，记录开发过程

## 博客程序

### 选择一个域名，作为线下开发域名

这里我使用`www.blog.la`

为这个域名配置一个hosts，解析到本地IP:127.0.0.1

``` shell
sudo vim /etc/hosts

# 下面信息为配置域名访问到特定IP地址
127.0.0.1 www.blog.la
```

### 配置NGINX主机

#### 准备程序
1. 新增php源码文件夹`./www/www.blog.la/
1. 录入程序，由于入库程序权限原因，再新增一个子目录`public`
1. 创建`index.php`入口文件

#### 配置nginx虚机
1. 选定文件夹`./conf/conf.d/`
1. 新增虚拟主机配置`www.blog.la.conf`


### 启动服务
1. `docker-compose up`

### 重新部署服务
1. `docker-compose down && docker-compose up`

### 访问部署成功的服务

1. http://www.blog.la

## 切换php 54-> 70服务

1. 定位`./conf/conf.d/www.blog.la.conf`
    1. `fastcgi_pass   php54:9000;`修改为`fastcgi_pass   php72:9000;`
1. 重启服务
    1. `cmmand + c`中断（一定要等所有服务都停止，出现done则为一个服务停止）
    1. `docker-compose up`


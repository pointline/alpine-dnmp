# alpine-dnmp
alpine dnmp采用Alpine Linux为基础，通过Docker-Compose编排PHP运行环境。

alpine dnmp包括`Nginx + PHP7.0 + PHP7.1(nodejs) + PHP7.2(nodejs) + Mysql5.6 + Redis + PHPMyadmin + elasticsearch`

## 目录结构

```
/
├── core                        核心文件目录
│   ├── conf                    配置文件
│   ├── images                  编排文件
├── logs                        日志文件
├── other                  　　　其它备用文件
├── share-files                 各容器之间共享目录
├── ssl                       　ssl文件存放目录
├── web-conf                    虚拟主机文件
├── www                         PHP代码项目目录
└── docker-compose.yml　　　　　　编排文件
```

## 使用
在alpine-dnmp目录下

+ 启动
    ```baseh
    sudo docker-compose up -d
    ```
+ 停止
    ```bash
    sudo docker-compose down
    ```
+ 重启
    ```bash
    sudo docker-compose restart
    ```
+ 查看容器状态
    ```bash
    sudo docker container ls -a
    ```
+ 默认使用PHP7.2，修改PHP版本
    ```bash
    #　开启所需的单独PHP版本
    vim core/conf/nginx/conf/conf.d/global.conf
    # 多PHP共存
    # 可在web-conf中的虚拟主机配置文件定义自己的upstream
    ```
##　开放端口
+ nginx
  + 80
  + 443
  + 8080
  + 8035
+ PHP70
  + 9070
+ PHP71
  + 9071
+ PHP72
  + 9000
+ mysql
  + 3306
+ elasticsearch
  + 9200
+ redis
  + 6379
+ phpmyadmin
  + 3307

## 密码
+ mysql
  + U:root,P:123456


## Q/A
+ elasticsearch无法启动
    ```base
    sudo vim /etc/sysctl.conf
    # 在最下面加入
    vm.max_map_count=262144
    # 保存重启电脑
    ```
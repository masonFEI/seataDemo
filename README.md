
## SEATADEMO

课程视频为
https://www.bilibili.com/video/BV16h4y1G7kd?p=1&vd_source=82c121d3d4cd2783d6bcb180125420fb

### jdk版本限制
jdk 8

### docker 操作

docker network create common-network

docker run --name mysql -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123456 -d mysql:latest --default-authentication-plugin=mysql_native_password

docker cp mysql:/etc/my.cnf E:/dockerdata/mysql/conf/

之后杀掉mysql容器，用下面命令重启

### 数据库启动语句
docker run --name mysql -d --restart=always --network common-network -p 3306:3306 -v E:/dockerdata/mysql/data:/var/lib/mysql/ -v E:/dockerdata/mysql/conf/my.cnf:/etc/my.cnf -v E:/dockerdata/mysql/logs:/logs -e MYSQL_ROOT_PASSWORD=123456 -d mysql:latest --default-authentication-plugin=mysql_native_password  


### nacos启动语句
与数据库在一个网段中--network common-network

docker run -p 8848:8848 -p 9848:9848 -p 9849:9849 -e NACOS_AUTH_ENABLE=true -e MODE=standalone -e JVM_XMS=2048m -e JVM_XMX=2048m -e JVM_XMN=2048m -v E:\dockerdata\nacos\logs:/home/nacos/logs -v E:\dockerdata\nacos\conf\:/home/nacos/conf --network common-network --privileged=true --restart=always --name nacos -d nacos/nacos-server


### seata使用docker安装
docker run -d --restart always --network common-network -p 8091:8091 -p 7091:7091  --name seata-serve seataio/seata-server:latest
docker cp seata-serve:/seata-server/resources E:/dockerdata/seata

### seata启动语句
docker run -d --restart always --network common-network -p 8091:8091 -p 7091:7091 -e MODE=standalone --name seata-server -v E:/dockerdata/seata/resources:/seata-server/resources seataio/seata-server

### nacos管理平台界面
http://localhost:8848/nacos

用户名/密码 nacos/nacos

创建分组 SEATA_GROUP
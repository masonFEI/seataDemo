
## SEATADEMO

课程视频为
https://www.bilibili.com/video/BV16h4y1G7kd?p=1&vd_source=82c121d3d4cd2783d6bcb180125420fb

### jdk版本限制
jdk 8


### 数据库启动语句
docker run --name mysql -d --restart=always --network common-network -p 3306:3306 -v E:/dockerdata/mysql/data:/var/lib/mysql/ -v E:/dockerdata/mysql/conf/my.cnf:/etc/my.cnf -v E:/dockerdata/mysql/logs:/logs -e MYSQL_ROOT_PASSWORD=123456 -d mysql:latest --default-authentication-plugin=mysql_native_password  


### nacos启动语句
与数据库在一个网段中--network common-network

docker run --network common-network --env MODE=standalone --name nacos -d -p 8848:8848 nacos/nacos-server

### nacos管理平台界面
http://localhost:8848/nacos

用户名/密码 nacos/nacos

创建分组 SEATA_GROUP
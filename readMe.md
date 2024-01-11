


### jdk版本限制
jdk 8


### 数据库启动语句
docker run --name mysql -p 3306:3306 -v E:/dockerdata/mysql/data:/var/lib/mysql/ -v E:/dockerdata/mysql/conf/my.cnf:/etc/my.cnf -v E:/dockerdata/mysql/logs:/logs -e MYSQL_ROOT_PASSWORD=123456 -d mysql:latest --default-authentication-plugin=mysql_native_password
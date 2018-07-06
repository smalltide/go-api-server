
# go-api-server
Use golang to make a restful api server

### Skills
1. golang
2. restful
3. api
4. gin
5. swagger
6. nginx
7. Viper (Go configuration with fangs)
8. gorm (Go ORM lib)
9. JWT
10. HTTPS

### cURL
-X/--request [GET|POST|PUT|DELETE|…]  指定请求的 HTTP 方法  
-H/--header                           指定请求的 HTTP Header  
-d/--data                             指定请求的 HTTP 消息体（Body)  
-v/--verbose                          输出详细的返回信息  
-u/--user                             指定账号、密码  
-b/--cookie                           读取 cookie...  
```
curl -v -XPOST -H "Content-Type: application/json" http://127.0.0.1:8080/user -d'{"username":"admin","password":"admin1234"}'...
```

### Branch
Build  
```
  > cd $GOPATH/src
  > git clone https://github.com/lexkong/vendor
  > cd go-api-server
  > go build -v .
  > ./go-api-server
```

1. v1 实战：启动一个最简单的RESTful API服务器
```
  > curl -XGET http://127.0.0.1:8080/sd/health
  > curl -XGET http://127.0.0.1:8080/sd/disk
  > curl -XGET http://127.0.0.1:8080/sd/cpu
  > curl -XGET http://127.0.0.1:8080/sd/ram
```
2. v2 实战：配置文件读取
3. v3 实战：记录和管理API日志
4. v4 实战：初始化Mysql数据库并建立连接
5. v5 实战：自定义业务错误信息
```
  > curl -XPOST -H "Content-Type: application/json" http://127.0.0.1:8080/v1/user
  > curl -XPOST -H "Content-Type: application/json" http://127.0.0.1:8080/v1/user -d'{"username":"admin"}'
  > curl -XPOST -H "Content-Type: application/json" http://127.0.0.1:8080/v1/user -d'{"password":"admin"}'
  > curl -XPOST -H "Content-Type: application/json" http://127.0.0.1:8080/v1/user -d'{"username":"admin","password":"admin"}'
```
6. v6 实战：读取和返回HTTP请求
```
  > curl -XPOST -H "Content-Type: application/json" http://127.0.0.1:8080/v1/user/admin2?desc=test -d'{"username":"admin","password":"admin"}'
```
7. v7 实战：用户业务逻辑处理（业务处理）
```
  > curl -XPOST -H "Content-Type: application/json" http://127.0.0.1:8080/v1/user -d'{"username":"kong","password":"kong123"}'
  > curl -XGET -H "Content-Type: application/json" http://127.0.0.1:8080/v1/user -d'{"offset": 0, "limit": 20}'
  > curl -XGET -H "Content-Type: application/json" http://127.0.0.1:8080/v1/user/kong
  > curl -XPUT -H "Content-Type: application/json" http://127.0.0.1:8080/v1/user/2 -d'{"username":"kong","password":"kongmodify"}'
  > curl -XDELETE -H "Content-Type: application/json" http://127.0.0.1:8080/v1/user/2
```
8. v8 实战：HTTP调用添加自定义处理逻辑
```
  >  curl -v -XGET -H "Content-Type: application/json" http://127.0.0.1:8080/v1/user
```
9. v9 实战：API身份验证
```
  > curl -XGET -H "Content-Type: application/json" http://127.0.0.1:8080/v1/user
  > curl -XPOST -H "Content-Type: application/json" http://127.0.0.1:8080/login -d'{"username":"admin","password":"admin"}'
  > curl -XGET -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpYXQiOjE1MzA4NjI2NjQsImlkIjoxLCJuYmYiOjE1MzA4NjI2NjQsInVzZXJuYW1lIjoiYWRtaW4ifQ.zgBNiBHi2WufuolA2iTcmHzjyf30Hi5cSb00FFyml1Q" -H "Content-Type: application/json" http://127.0.0.1:8080/v1/user
```
10. v10 进阶：用HTTPS加密API请求
```
  > openssl req -new -nodes -x509 -out conf/server.crt -keyout conf/server.key -days 3650 -subj "/C=DE/ST=NRW/L=Earth/O=Random Company/OU=IT/CN=127.0.0.1/emailAddress=xxxxx@xxx.xxx"
  > curl -XGET -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpYXQiOjE1MjgwMTY5MjIsImlkIjowLCJuYmYiOjE1MjgwMTY5MjIsInVzZXJuYW1lIjoiYWRtaW4ifQ.LjxrK9DuAwAzUD8-9v43NzWBN7HXsSLfebw92DKd1JQ" -H "Content-Type: application/json" https://127.0.0.1:8081/v1/user
  > curl -XGET -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpYXQiOjE1MjgwMTY5MjIsImlkIjowLCJuYmYiOjE1MjgwMTY5MjIsInVzZXJuYW1lIjoiYWRtaW4ifQ.LjxrK9DuAwAzUD8-9v43NzWBN7HXsSLfebw92DKd1JQ" -H "Content-Type: application/json" https://127.0.0.1:8081/v1/user --cacert conf/server.crt
```
11. v11 进阶：用Makefile管理API项目
```
  > make
  > make gotool
  > make clean
  > make ca
  > make help
```
12. v12 进阶：给API命令增加版本功能
```
  > make 
  > ./go-api-server -v
```
进阶：给API增加启动脚本
```
  > ./admin.sh -h
  > ./admin.sh status
  > ./admin.sh start
  > ./admin.sh status
  > ./admin.sh restart
  > ./admin.sh status
  > ./admin.sh stop
  > ./admin.sh status
```
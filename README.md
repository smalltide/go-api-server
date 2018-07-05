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
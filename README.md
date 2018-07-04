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
1. v1 实战：启动一个最简单的RESTful API服务器
```
  > cd $GOPATH/src
  > git clone https://github.com/lexkong/vendor
  > cd go-api-server
  > go build -v .
  > ./go-api-server
  > curl -XGET http://127.0.0.1:8080/sd/health
  > curl -XGET http://127.0.0.1:8080/sd/disk
  > curl -XGET http://127.0.0.1:8080/sd/cpu
  > curl -XGET http://127.0.0.1:8080/sd/ram
```

2. v2 实战：配置文件读取
```
  > cd go-api-server
  > go build -v .
  > ./go-api-server
  > ./go-api-server -c config_file.yaml
```
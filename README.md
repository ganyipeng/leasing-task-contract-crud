# leasing-task-contract-crud

The crud opts of contract.<br/>
用时2小时

## 工作分解

### github leasing:dev 分支更新
* github上进行pull request：<kbd>ganyipeng:leasing/dev <= nemowork:leasing/dev</kbd>

### 本地 leasing:dev 分支更新
* 执行命令：<kbd>git pull</kbd>

### main目录下编写crud代码
* 编辑修改: ContractRepository.java
* 编辑修改：ContractController.java

### test目录下编写crud测试代码
* 这里先不加了，先只做 curl 测试吧，贪多嚼不烂

### curl 命令测试
```
➜  leasing git:(dev) ✗ curl localhost:8080/api/contracts
[{"id":"5d1c261508cd0421d8187e71","name":"DEF"},{"id":"5d1c261508cd0421d8187e73","name":"Contract 2"}]%                                                    
➜  leasing git:(dev) ✗ curl localhost:8080/api/contracts/5d1c261508cd0421d8187e73
{"id":"5d1c261508cd0421d8187e73","name":"Contract 2"}%                                                                                                     
➜  leasing git:(dev) ✗ curl localhost:8080/api/contracts                         
[{"id":"5d1c261508cd0421d8187e71","name":"DEF"},{"id":"5d1c261508cd0421d8187e73","name":"Contract 2"}]%                                                    
➜  leasing git:(dev) ✗ curl -X delete localhost:8080/api/contracts/5d1c261508cd0421d8187e73
{"timestamp":"2019-07-03T03:53:22.491+0000","status":405,"error":"Method Not Allowed","message":"Request method 'delete' not supported","path":"/api/contracts/5d1c261508cd0421d8187e73"}%                                                                                                                            
➜  leasing git:(dev) ✗ curl -X DELETE localhost:8080/api/contracts/5d1c261508cd0421d8187e73
➜  leasing git:(dev) ✗ curl localhost:8080/api/contracts                                   
[{"id":"5d1c261508cd0421d8187e71","name":"DEF"}]%                                                                                                          
➜  leasing git:(dev) ✗ curl -X PUT localhost:8080/api/contracts/5d1c261508cd0421d8187e71 -d '{"name":"甘宜鹏"}'
{"timestamp":"2019-07-03T03:55:51.203+0000","status":415,"error":"Unsupported Media Type","message":"Content type 'application/x-www-form-urlencoded;charset=UTF-8' not supported","path":"/api/contracts/5d1c261508cd0421d8187e71"}%                                                                                 
➜  leasing git:(dev) ✗ curl -X PUT localhost:8080/api/contracts/5d1c261508cd0421d8187e71 -d '{"name":"ganyipeng1987"}'
{"timestamp":"2019-07-03T03:56:14.595+0000","status":415,"error":"Unsupported Media Type","message":"Content type 'application/x-www-form-urlencoded;charset=UTF-8' not supported","path":"/api/contracts/5d1c261508cd0421d8187e71"}%                                                                                 
➜  leasing git:(dev) ✗ curl -X PUT -d '{"name":"ganyipeng1987"}' localhost:8080/api/contracts/5d1c261508cd0421d8187e71
{"timestamp":"2019-07-03T03:57:33.147+0000","status":415,"error":"Unsupported Media Type","message":"Content type 'application/x-www-form-urlencoded;charset=UTF-8' not supported","path":"/api/contracts/5d1c261508cd0421d8187e71"}%                                                                                 
➜  leasing git:(dev) ✗ curl -X PUT -d '{"name":"ganyipeng1987"}' -H 'Content-Type:application/json' localhost:8080/api/contracts/5d1c261508cd0421d8187e71
{"id":null,"name":"ganyipeng1987"}%                                                                                                                        
➜  leasing git:(dev) ✗ curl -X POST -d '{"name":"甘宜鹏"}' -H 'Content-Type:application/json' localhost:8080/api/contracts   
{"id":"5d1c28f608cd0421d8187e79","name":"甘宜鹏"}%  

➜  leasing git:(dev) ✗ curl localhost:8080/api/contracts
[{"id":"5d1c261508cd0421d8187e71","name":"ganyipeng1987"},{"id":"5d1c28f608cd0421d8187e79","name":"甘宜鹏"}]% 
➜  leasing git:(dev) ✗ 
```

### 代码走查 code review

### 本地提交代码至远程 github

### 远程 github 发起 pull 请求

### 知识总结

## 遇到的问题

### docker启动mongodb，mongodb自动停止

* 找不到原因呢
命令没报异常：<kbd>docker logs -f -t --since="2018-02-08" --tail=100 CONTAINER_ID</kbd>

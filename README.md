# leasing-task-contract-crud

The crud opts of contract.<br/>
开发用时2小时
文档总结用时2.5小时

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

* <kbd>git push</kbd>

### 远程 github 发起 pull 请求

### 知识总结

#### 总结的意义

* 把代码写出来只能算是将东西给吃来下去了；写代码/完成任务，算是吃东西
* 吃完之后还需要肠胃的消化吸收才算有营养；及时复习/总结，才能消化吸收
* 只吃饭不吸收，那叫糖尿病
* 只工作不总结，那就老年小白

![image](http://www.plantuml.com/plantuml/svg/XP71IW91683lynJ3TlO5zY1Iz0HvKmyBJIQvix7E7Y828oAJKRUo0Wj2OY42knZhuYY-pFopwybNQ7642ZQQsmppVz_7JA71B9TvTXsn6giJ39D0pf_Lr9VJRjn_KPy27JWE8ouk7XAyxLLNiq6PwbioQaFlNOtVbbST-E2gvKiXe3rSpNZIv3BgGA-j7iDayPGCkMgAMDoLgOR-6kszmirO3y5Y7jy7Acm1Vu1RdlW1N0hm8zKFqR7bfeqrXsuYyId2s83pWRQQHQjnLADL0-ToUMpeGsqrzppRjjmJ0vsX7nYTii5qKyt5CXYPknRxfkWI7M3kEBJXsMHDoVIMjgek8RIIB-7rYaVNKapIbzJRIeO6POV-p_ghhK3eVlgTNm00)

#### 注解图谱

* java代码分为CSRM四层，这四层的注解分别如下所示：

![image](http://www.plantuml.com/plantuml/svg/bLB1IiD04BtlL-mF5Fz0jhOW5Ggb1UzhCsq3sspSdLHwLF0Yr5vQ1V5IYkZ5Q2aYeh-JRMx-WgbTiY7WmLFcpUvxy-PbcKQkC1eAKXDSQrgJ0Ief12ZRw80Q-LqWZG11zNWNQ1j2gNsKQcolDAK7WX17fPNAVawqtsslI7NbxudL22G25T13Adj5BydbEZsVcVLJ-hZy_hfBdczD_4PODK9vvYlm20GUtPAj1Cgmf92-lsncgrnXi_hSCpSVPZqdh0qQtSqjFer0OvE7eH_q2Ji4LxUaBe38rNKGW61XsOxo-uFoIcR-QYPnRcXd9fbUPFtSGeihFipHWVJ6sL2EWsEkV7uY89zJIivc_k_Oh4ydOEudoTMYc1fXzep-IIxyvIHUfB7Zc-k7PBeax8YFGEbEgBAiwXnvDV9yB2vKrhJlOyUW7aU-qoIiuL6xLavbMHKDnGy0)

#### MongoRepository基本的CRUD操作

* 曹老师说：告诉别人做什么事情，就是管理
* 那么，如果我把MongoRepository当作人来看，那么我告诉“他”做CRUD操作，是不是也算是管理呢
* 我认为算，虽然人是有生命的，但是Object在JVM中，可也是有“生命周期”的呢？<kbd>new > invoke > gc</kbd>

![image](http://www.plantuml.com/plantuml/svg/SoWkIImgoStCIybDBE3IKl3DpqlF3qejo2_EBCalgkJIqb9mvj82aa_xvZ-VCX_4r8fNA4uiIzNmpKz9pL781P6Q87L1cEhIWEOwvkHeQ2BndIezKy0gNxIlUhfkrfETdIYIRfb5nIL-YRcf6i4bHPbvwK1Xg02g8Jw9gCfoe7omKq8XJbdI-tH21rJNqzOEcErGBVe--K1zcIcQC1LjlK_shtisPIVOOq_NJd-sRYjKwjcSXgSJ-h3wsWNJrq2fr99K35iSKlDIe04D0000)

## 遇到的问题

### docker启动mongodb，mongodb自动停止

* 找不到原因呢
命令没报异常：<kbd>docker logs -f -t --since="2018-02-08" --tail=100 CONTAINER_ID</kbd>

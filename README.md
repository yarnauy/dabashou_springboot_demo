# spring-boot-starter

本示例项目基于Java SDK + Gradle + SpringBoot方式来调用智能合约。

### 测试链信息

- 节点数：4
- rpc addr:
  - 18.163.74.253:20200
  - 18.163.74.253:20201
  - 18.163.74.253:20202
  - 18.163.74.253:20203


### 客户端信息

#### 软件依赖

- Java: JDK 1.8 - JDK 14均可
- 区块链交互工具: fisco-bcos-java-sdk:3.3.0
- 构建工具这里采用了gradle


#### java应用构建引导(以gradle项目为例)
##### 前期配置
1. 创建java gradle项目（或引入本示例项目）
2. 引入依赖库,以 参考[这里](./build.gradle)
3. 创建配置文件application.properties
  ```yml
  ### Java sdk configuration
  cryptoMaterial.certPath=conf
  network.peers[0]=127.0.0.1:20200
          #network.peers[1]=127.0.0.1:20201
  
  ### System configuration
  system.groupId=group0
  system.hexPrivateKey=
  
  ### Springboot configuration
  server.port=8080
  ```
其中：

-  请将network.peers更换成实际的链节点监听地址。
-  cryptoMaterial.certPath设为conf

其他暂时默认

4. 配置证书
   将证书拷贝到src/main/resources/conf目录下，（该项目已经拷贝完成，可以参考）。
5. 至此，前期配置部分完成



## 编译和运行

您可以在idea内直接运行，也可以编译成可执行jar包后运行。以编译jar包方式为例：

```shell
cd spring-boot-starter
bash gradlew bootJar
cd dist
```

会在dist目录生成spring-boot-starter-exec.jar，可执行此jar包：

```shell
java -jar spring-boot-starter-exec.jar
```

随后，即可访问相关接口。

set示例：

```shell
curl http://127.0.0.1:8080/hello/set?n=hello
```

返回示例（表示交易哈希）：

```shell
0x1c8b283daef12b38632e8a6b8fe4d798e053feb5128d9eaf2be77c324645763b
```

get示例：

```shell
curl http://127.0.0.1:8080/hello/get
```

返回示例：

```json
["hello"]
```

示例：[maven示例](https://github.com/FISCO-BCOS/spring-boot-crud)。

# SpringCloud入门
##	概念

1. 什么是Spring Cloud？</br>
	`Springboot提供了一系列工具，可以帮助开发人员迅速搭建分布式系统中的`</br>`公共组件（比如：配置管理，服务发现，断路器，智能路由，微代理，控制总`</br>`线，一次性令牌，全局锁，主节点选举， 分布式session, 集群状态）。协调`</br>`分布式环境中各个系统，为各类服务提供模板性配置。`</br>
	`springCloud是基于SpringBoot的一整套实现微服务的框架。他提供了`</br>`微服务开发所需的配置管理、服务发现、断路器、智能路由、微代理、控制总`</br>`线、全局锁、决策竞选、分布式会话和集群状态管理等组件。最重要的是，跟`</br>`spring boot框架一起使用的话，会让你开发微服务架构的云服务非常好的方便。`</br>
2. SpringCloud特点</br>
	1. 约定优于配置</br>
	2. 开箱即用，快速启动</br>
	3. 适用于各种环境</br>
	4. 量级的组件</br>
	5. 组件支持丰富，功能齐全</br>
3. SpringCloud分布式的五大重点</br>
	- 服务器的注册与发现—Netflix Eureka</br>
		`一个RESTful服务，用来定位运行在AWS地区（Region）中的中间层服务。 `</br>
`它由两个组件组成：Eureka服务器和Eureka客户端。 `</br>
			`1. Eureka服务器用作服务注册服务器。 `</br>
			`2. Eureka客户端是一个java客户端，用来简化与服务器的交互、作为轮询负载均衡器，并提供服务的故障切换支持。 `</br>
`Netflix在其生产环境中使用的是另外的客户端，它提供基于流量、资源利用`</br>`率以及出错状态的加权负载均衡。`</br>
	- 客户端负载均衡—Netflix Ribbon
		`主要提供客户侧的软件负载均衡算法。 `</br>`
Ribbon客户端组件提供一系列完善的配置选项，比如连接超时、重试、重试算法等。 `</br>`
Ribbon内置可插拔、可定制的负载均衡组件。`</br>
`一些常用的负载均衡策略: `</br>
`1. 简单轮询负载均衡` </br>
`2. 加权响应时间负载均衡 `</br>
`3. 区域感知轮询负载均衡 `</br>
`4. 随机负载均衡 `</br>
`Ribbon中还包括一下功能: `</br>
`1. 易于与服务发现组件（比如Netflix的Eureka）集成 `</br>
`2. 使用Archaius完成运行时配置 `</br>
`3. 使用JMX暴露运维指标，使用Servo发布 `</br>
`4. 多种可插拔的序列化选择 `</br>
`5. 异步和批处理操作（即将推出） `</br>
`6. 自动SLA框架（即将推出） `</br>
`7. 系统管理/指标控制台（即将推出）`</br>
	- 断路器—Netflix Hystrix</br>
		`1. 断路器可以防止一个应用程序多次试图执行一个操作，即很可能失败，`</br>`允许它继续而不等待故障恢复或者浪费 CPU 周期，而它确定该故障是持久的.`
		`2. 断路器模式也使应用程序能够检测故障是否已经解决。如果问题似乎已`</br>`经得到纠正​​，应用程序可以尝试调用操作。`
		`3. 断路器增加了稳定性和灵活性，以一个系统，提供稳定性，而系统从故`</br>`障中恢复，并尽量减少此故障的对性能的影响。它可以帮助快速地拒绝对一个`</br>`操作，即很可能失败，而不是等待操作超时（或者不返回）的请求，以保持系`</br>`统的响应时间。如果断路器提高每次改变状态的时间的事件，该信息可以被用`</br>`来监测由断路器保护系统的部件的健康状况，或以提醒管理员当断路器跳闸，`</br>`以在打开状态。`</br>
	- 服务网关—Netflix Zuui</br>
		`类似nginx，反向代理的功能，不过netflix自己增加了一些配合其他组件的特性。`</br>
	- 分布式配置—Spring Cloud Config</br>
		`1. SpringCloudConfig就是我们通常意义上的分布式配置中心，把`</br>`应用原本放在本地文件的配置抽取出来放在中心服务器，从而能够提供更好的管理、 发布能力。`</br>
		`2. SpringCloudConfig分为服务端和客户端，服务端负责将`</br>`git（svn）中存储的配置文件发布成REST接口，客户端可以从服务端REST接`</br>`口获取配置。但客户端并不能主动感知到配置的变化，从而主动去获取新的配`</br>`置， 它需要每个客户端通过POST方法触发各自的/refresh，`</br>`SpringCloudBus就通过一个轻量级消息代理连接分布式系统的节点。`
		`3. 可以用于广播状态更改（如配置更改）或其他管理指令。`</br>
		`4. SpringCloudBus提供了通过POST方法访问的endpoint/bus/refresh，`</br>`这个接口通常由git的钩子功能调用，用以通知各个``SpringCloudConfig的客户端去服务端更新配置。`</br>
		
## SpringCloud分布式的五大重点-Eureka
### 1.Eureka客户端

服务发现是microservice基础架构的关键原则之一。Eureka是Netflix服务发现的一种服务和客户端。

#### 1.1 注册到Eureka

当一个客户端注册到Eureka,它提供关于自己的元数据（诸如主机和端口，健康指标URL，首页等）Eureka通过一个服务从各个实例接收心跳信息。如果心跳接收失败超过配置的时间，实例将会正常从注册里面移除。

可以使用`@EnableEurekaClient`或`@EnableDiscoveryClient`注解。
配置`eureka.client.serviceUrl.defaultZone=http://localhost:8761/eureka/`属性，注意修改URL地址。
确保`spring.application.name`有默认值。

*注*：`@EnableEurekaClient`只能用于Eureka，`@EnableDiscoveryClient`能用于zookeeper等其他注册组件。

`@EnableEurekaClient`使其成为Eureka实例（被其他服务发现）和客户端（能发现其他服务）注册到应用里面。可通过`eureka.instance.*`进行相关配置的修改。

#### 1.2 对Eureka服务的身份验证

如果其中一个`eureka.client.serviceUrl.defaultZone`的url已经把凭证嵌入到它里面，那么HTTP基本的身份验证将会被自动添加到你的eureka客户端（curl风格，如`http://user:password@localhost:8761/eureka`）。 对于更复杂的需求，可以创建一个带“@Bean”注解的“DiscoveryClientOptionalArgs”类型并且为它注入“ClientFilter”实例。

#### 1.3 健康指标和状态页面

健康指标和状态页面分别对应一个Eureka实例的“/health”和“/info”。

#### 1.4 注册一个安全应用

若要用HTTPS，需要设置两个标记，分别是`EurekaInstanceConfig`，即`eureka.instance.[nonSecurePortEnabled,securePortEnabled]=[false,true]`。

#### 1.5 Eureka 健康检查

默认情况下，Eureka使用客户端心跳来确定一个客户端是否活着（状态为“UP”）。

#### 1.6 Eureka给客户端和实例的元数据

有标准的元数据，如主机名、IP地址、端口号、状态页面和健康检查。额外的元数据可以被添加到实例注册在`eureka.instance.metadataMap`里面。

**在 Cloudfoundry 使用 Eureka**
Cloudfoundry有总的路由，所有在同个应用的实例有相同的主机名。

**在AWS上使用Eureka**
定制`EurekaInstanceConfigBean`

**修改Eureka实例ID**
通过`eureka.instance.instanceId`进行配置。

#### 1.7 使用EurekaClient

使用`@EnableDiscoveryClient`（或`@EnableEurekaClient`），使它从Eureka Server发现服务实例。

注：不要在`@PostConstruct`方法或`@Scheduled`方法使用EurekaClient（或任何ApplicationContext还没被启动的地方）。

#### 1.8 代替原生的Netflix EurekaClient

Spring Cloud已经支持Feign（一个REST客户端构建）跟Spring RestTemplate（使用逻辑Eureka服务标识符(VIPs)代替物理的URL）。

#### 1.9 为什么注册一个服务这么慢？

实例默认与注册中心持续30秒的周期心跳（通过客户的`serviceUrl`）。当实例、服务端和客户端全都在它们的缓存里面拥有相同的元数据（这可能还需要3次心跳），那么服务对于客户端的discovery将变为不可用。可通过`eureka.instance.leaseRenewalIntervalInSeconds`这个修改配置，可以加快这一进程的客户端连接到其他服务。

### 2 服务发现: Eureka Server

例子，添加依赖`spring-cloud-starter-eureka-server`

```java
@SpringBootApplication
@EnableEurekaServer
public class Application {
    public static void main(String[] args) {
        new SpringApplicationBuilder(Application.class).web(true).run(args);
    }
}
```

服务端有一个带UI的首页，HTTP API端点在`/eureka/*`下提供标准的Eureka功能。

#### 2.1 高可用

Eureka服务端没有后台存储，但是服务实例在注册里面全都得发送心跳去保持注册更新（在内存里操作）客户端们也有一份内存缓存着eureka的注册信息。

#### 2.2 标准模式

```ym
eureka.client.registerWithEureka=false
eureka.client.fetchRegistry=false
eureka.client.serviceUrl.defaultZone=http://${eureka.instance.hostname}:${server.port}/eureka/
```

#### 2.3 节点感知

运行多个Eureka Servers。

Eureka甚至可以更有弹性和可用的运行多个实例，并让他们互相注册。事实上，这也是默认的行为，因此所有你需要让它工作的，只要添加一个有效的节点serviceUrl，例如：

```ym
---
spring:
  profiles: peer1
eureka:
  instance:
    hostname: peer1
  client:
    serviceUrl:
      defaultZone: http://peer2/eureka/

---
spring:
  profiles: peer2
eureka:
  instance:
    hostname: peer2
  client:
    serviceUrl:
      defaultZone: http://peer1/eureka/
```

然后通过不同的“profile”进行运行不同的Eureka Server。

#### 2.4 IP偏好

设置`eureka.instance.preferIpAddress=true`使应用注册到eureka的是IP地址而不是主机名。 

## SpringCloud分布式的五大重点-Config
**配置管理开发工具包，可以让你把配置放到远程服务器，目前支持本地存储、Git以及Subversion。**

针对系统外的配置项(如name-value对或相同功能的YAML内容),该服务器提供了基于资源的HTTP接口。使用**@EnableConfigServer**注解,该服务器可以很容易的被嵌入到Spring Boot 系统中。使用该注解之后该应用系统就是一个配置服务器。

```java
@SpringBootApplication
@EnableConfigServer
public class ConfigApplicion {
    public static void main(String[] args) throws Exception {
        SpringApplication.run(ConfigApplicion.class, args);
    }
}
```

### 1 资源库环境

- {application} 对应客户端的"spring.application.name"属性
- {profile} 对应客户端的 "spring.profiles.active"属性(逗号分隔的列表)
- {label} 对应服务端属性,这个属性能标示一组配置文件的版本

如果配置库是基于文件的，服务器将从application.yml和foo.yml中创建一个`Environment`对象。高优先级的配置优先转成`Environment`对象中的`PropertySource`。

#### 1 Git后端

默认的`EnvironmentRepository`是用Git后端进行实现的，Git后端对于管理升级和物理环境是很方便的,对审计配置变更也很方便。也可以`file:`前缀从本地配置库中读取数据。

这个配置库的实现通过映射HTTP资源的`{label}`参数作为git label(提交id,分支名称或tag)。如果git分支或tag的名称包含一个斜杠 ("/"),此时HTTP URL中的label需要使用特殊字符串"(_)"来替代(为了避免与其他URL路径相互混淆)。如果使用了命令行客户端如 curl，请谨慎处理URL中的括号(例如：在shell下请使用引号''来转义它们)。

**Git URI占位符**
Spring Cloud Config Server支持git库URL中包含针对{application}和 {profile}的占位符(如果你需要,{label}也可包含占位符, 不过要牢记的是任何情况下label只指git的label)。所以，你可以很容易的支持“一个应用系统一个配置库”策略或“一个profile一个配置库”策略。

**模式匹配和多资源库**

```ym
spring:
cloud:
    config:
      server:
        git:
          uri: https://github.com/spring-cloud-samples/config-repo
          repos:
            simple: https://github.com/simple/config-repo
            special:
              pattern: special*/dev*,*special*/dev*
              uri: https://github.com/special/config-repo
            local:
              pattern: local*
              uri: file:/home/configsvc/config-repo
```

如果 {application}/{profile}不能匹配任何表达式，那么将使用“spring.cloud.config.server.git.uri”对应的值。在上例子中，对于 "simple" 配置库, 匹配模式是simple/* (也就说,无论profile是什么，它只匹配application名称为“simple”的应用系统)。“local”库匹配所有application名称以“local”开头任何应用系统，不管profiles是什么(来实现覆盖因没有配置对profile的匹配规则，“/*”后缀会被自动的增加到任何的匹配表达式中)。

**Git搜索路径中的占位符**
`spring.cloud.config.server.git.searchPaths`

###### 1.2 版本控制后端文件系统使用

伴随着版本控制系统作为后端(git、svn)，文件都会被`check out`或`clone` 到本地文件系统中。默认这些文件会被放置到以config-repo-为前缀的系统临时目录中。在Linux上，譬如应该是`/tmp/config-repo-<randomid>`目录。有些操作系统[routinely clean out](https://serverfault.com/questions/377348/when-does-tmp-get-cleared/377349#377349)放到临时目录中，这会导致不可预知的问题出现。为了避免这个问题，通过设置`spring.cloud.config.server.git.basedir`或`spring.cloud.config.server.svn.basedir`参数值为非系统临时目录。

###### 1.3 文件系统后端

使用本地加载配置文件。
需要配置：`spring.cloud.config.server.native.searchLocations`跟`spring.profiles.active=native`。
路径配置格式：`classpath:/, classpath:/config,file:./, file:./config`。

###### 1.4 共享配置给所有应用

**基于文件的资源库**
在基于文件的资源库中(i.e. git, svn and native)，这样的文件名`application*`命名的资源在所有的客户端都是共享的(如 application.properties, application.yml, application-*.properties,etc.)。

**属性覆盖**
“spring.cloud.config.server.overrides”添加一个Map类型的name-value对来实现覆盖。
例如

```ym
spring:
  cloud:
    config:
      server:
        overrides:
          foo: bar
```

会使所有的配置客户端应用程序读取foo=bar到他们自己配置参数中。

#### 2. 健康指示器

通过这个指示器能够检查已经配置的`EnvironmentRepository`是否正常运行。
通过设置`spring.cloud.config.server.health.enabled=false`参数来禁用健康指示器。

#### 3 安全

你可以自由选择任何你觉得合理的方式来保护你的Config Server（从物理网络安全到OAuth2 令牌），同时使用Spring Security和Spring Boot 能使你做更多其他有用的事情。

为了使用默认的Spring Boot HTTP Basic 安全，只需要把Spring Security 增加到classpath中(如org.springframework.boot.spring-boot-starter-security)。默认的用户名是“user”，对应的会生成一个随机密码，这种情况在实际使用中并没有意义，一般建议配置一个密码（通过 security.user.password属性进行配置）并对这个密码进行加密。

#### 4 加密与解密

如果远程属性包含加密内容(以{cipher}开头),这些值将在通过HTTP传递到客户端之前被解密。

使用略

#### 5 密钥管理

配置服务可以使用对称(共享)密钥或者非对称密钥(RSA密钥对)。

### 2 可替换格式服务

配置文件可加后缀".yml"、".yaml"、".properties"

### 3 文本解释服务

```
/{name}/{profile}/{label}/{path}
```

### 4 嵌入配置服务器

一般配置服务运行在单独的应用里面，只要使用注解`@EnableConfigServer`即可嵌入到其他应用。

### 5 推送通知和总线

添加依赖`spring-cloud-config-monitor`，激活Spring Cloud 总线，`/monitor`端点即可用。

当webhook激活，针对应用程序可能已经变化了的，配置服务端将发送一个`RefreshRemoteApplicationEvent`。

### 6 客户端配置

#### 6.1 配置第一次引导

通过`spring.cloud.config.uri`属性配置Config Server地址

#### 6.2 发现第一次引导

如果用的是Netflix，则用`eureka.client.serviceUrl.defaultZone`进行配置。

#### 6.3 配置客户端快速失败

在一些例子里面，可能希望在没有连接配置服务端时直接启动失败。可通过`spring.cloud.config.failFast=true`进行配置。

#### 6.4 配置客户端重试

添加依赖`spring-retry`、`spring-boot-starter-aop`，设置`spring.cloud.config.failFast=true`。默认的是6次重试，初始补偿间隔是1000ms，后续补偿为1.1指数乘数，可通过`spring.cloud.config.retry.*`配置进行修改。

#### 6.5 定位远程配置资源

路径：`/{name}/{profile}/{label}`

- "name" = ${spring.application.name}
- "profile" = ${spring.profiles.active} (actually Environment.getActiveProfiles())
- "label" = "master"

label对于回滚到之前的版本很有用。

#### 6.6 安全

通过`spring.cloud.config.password`、`spring.cloud.config.username`进行配置。

## SpringCloud分布式的五大重点-Ribbon

- RibbonEurekaAutoConfiguration 自动配置类
- 开启负载均衡的步骤：

1. 多个服务提供者，注册到服务中心
2. 服务消费者通过调用被@LoadBalanced注解修饰过的restTemplate

- RestTemplate 与 Ribbon整合使用 详解

1. RestTemplate 基本使用 GET POST PUT DELETE
2. RestTemplate 与 Ribbon 整合
3. 重点源码：LoadBalancerClient LoadBalancerAutoConfiguration

**Ribbon是一个客户端负载均衡器，有很多控制HTTP和TCP客户端的行为，可使用`@FeignClient`注解。**

```java
public class MyClass {
    @Autowired
    private LoadBalancerClient loadBalancer;

    public void doStuff() {
        ServiceInstance instance = loadBalancer.choose("stores");
        URI storesUri = URI.create(String.format("http://%s:%s", instance.getHost(), instance.getPort()));
        // ... do something with the URI
    }
}
```
## SpringCloud分布式的五大重点-Zuul
Zuul是Netflix出品的一个基于JVM路由和服务端的负载均衡器。

- 认证
- Insights
- 压力测试
- 金丝雀测试（Canary Testing）
- 动态路由
- 服务迁移
- 负载削减
- 安全
- 静态响应处理
- 主动/主动交换管理

### 1.Zuul的使用

```java
#在pom.xml引入spring-cloud-starter-zuul
#在application.properties配置
spring.application.name=api-gateway
server.port=5555
#在启动类使用@EnableZuulProxy
```

Spring Cloud创建了一个嵌入式Zuul代理来缓和急需一个UI应用程序来代理调用一个或多个后端服务的通用需求，这个功能对于代理前端需要访问的后端服务非常有用，避免了所有后端服务需要关心管理CORS和认证的问题。 

在Spring Boot主函数上通过注解`@EnableZuulProxy`来开启。

### 2.Zuul的主要功能有：

1. 请求转发，即路由的功能；与服务治理框架结合，实现自动化的服务实例维护以及负载均衡的路由转发。
2. 请求过滤，即可以当做是权限验证。权限校验与微服务业务逻辑解耦。
3. 它作为系统的统一入口，屏蔽了系统内部各个服务的细节。

### 3.传统路由方式

```xml
zuul.routes.api-a-url.path=/api-a-url/**
zuul.routes.api-a-url.url=http://localhost:8001/
```

### 4.面向服务的路由 使用eureka服务

```java 
zuul.routes.api-a.path=/api-a/**
zuul.routes.api-a.serviceId=hello-service

zuul.routes.api-b.path=/api-b/**
zuul.routes.api-b.serviceId=hello-service

zuul.routes.api-c.path=/ddd/**
zuul.routes.api-c.serviceId=hello-service

eureka.client.serviceUrl.defaultZone=http://localhost:1111/eureka/
```

使用`@EnableZuulProxy`同时引入了Spring Boot Actuator，默认将增加一个endpoint，提供http服务的`/routes`。

### 5.使用服务名称的方式 不用eureka服务治理

```xml
zuul.routes.api-d.path=/ddd/**
zuul.routes.api-d.serviceId=hello
ribbon.eureka.enabled=false
hello.ribbon.listOfServers=http://localhost:8001/,http://localhost:8002/
```

### 6.Cookie与头信息 为保证请求经过zuul转发后，还保留有Cookie Heads等信息，需要做一些配置：

```xml
#通过设置全局参数为空来覆盖默认值
zuul.senstitiveHeaders=
#通过制定路由的参数来配置  有如下两种配置
zuul.routes.<router>.customSensitiveHeaders=true
zuul.routes.<router>.senstiveHeaders=
```

### 7.重定向问题 spring security 和 shiro

```xml
zuul.addHostHeader=true
```

SpringCloud 的 Brixton会有重定向问题 Camden Dalston 则没有

- Hystrix和Ribbon支持 尽量使用 path与serviceId对应 即使用面向服务的路由。
- 动态加载/动态路由：原理 将配置放置在git远程仓库，更新仓库的配置文件，调用refresh接口，加载新的配置信息。
- 动态过滤器：使用groovy实现。

**窒息模式和本地跳转**

逐步替代旧的接口是一种通用的迁移现有应用程序或者API的方式，使用不同的具体实现逐步替换它们。Zuul代理是一种很有用的工具，因为你可以使用这种方式处理所有客户端到旧接口的请求。只是重定向了一些请求到新的接口。
## SpringCloud分布式的五大重点-Hystrix
- HystrixCommand：用在依赖的服务返回单个操作结果的时候

- HystrixObservableCommand：用在依赖的服务返回多个操作结果的时候

- 通过几个注解的方式可以简单使用断路器的功能

  ```java
  #程序启动的地方
  @EnableCircuitBreaker 
  #具体需要断路器的服务方法上
  @HystrixCommand(fallbackMethod = "helloFallback", commandKey = "helloKey")
  #断路器被触发熔断的回调方法
  public String helloFallback() {}
  ```

Netflix创建了一个库实现断路器模式，名为Hystrix。一个低水平的服务群中一个服务挂掉会给用户导致级联失效的。当调用一个特定的服务达到一定阈值(在Hystrix里默认是5秒内20个失败)，断路器开启并且调用没有成功的。开发人员能够提供错误原因和开启一个断路由回调。

例子，需添加依赖`org.springframework.cloud.spring-cloud-starter-hystrix`

```
@SpringBootApplication
@EnableCircuitBreaker
public class Application {

    public static void main(String[] args) {
        new SpringApplicationBuilder(Application.class).web(true).run(args);
    }

}

@Component
public class StoreIntegration {

    @HystrixCommand(fallbackMethod = "defaultStores")
    public Object getStores(Map<String, Object> parameters) {
        //do stuff that might fail
    }

    public Object defaultStores(Map<String, Object> parameters) {
        return /* something useful */;
    }
}
```

经测试，失败就直接调用defaultStores()方法了。

### 1 传播安全上下文或使用 Spring Scopes

如果你想一些线程的本地的上下文传播到一个@HystrixCommand，默认声明将不会工作，因为他在线程池里执行命令。（在超时的情况下）。你可以切换Hystrix去使用同个线程让调用者使用一些配置，或直接在注解中，让它去使用不同的“隔离策略”。举例:

```
@HystrixCommand(fallbackMethod = "stubMyService",
    commandProperties = {
      @HystrixProperty(name="execution.isolation.strategy", value="SEMAPHORE")
    }
)
...
```

如果你使用`@SessionScope`或`@RequestScope`同样适用。你会知道你要这么做，因为一个runtime异常说他不能找到作用域上下文。

### 2 健康指标

连接的断路器的状态也暴露在应用程序的`/health`端点中。

### 3 Hystrix 指标流

添加依赖`org.springframework.boot.spring-boot-starter-actuator`，使`/hystrix.stream`流作为一个管理端点。

### 4 断路器: Hystrix仪表盘

Hystrix的主要作用是会采集每一个HystrixCommand的信息指标,把每一个断路器的信息指标显示的Hystrix仪表盘上。

- 添加依赖`org.springframework.cloud.spring-cloud-starter-hystrix-dashboard`
- 主类上注解`@EnableHystrixDashboard`
- 访问`/hystrix`
- 填写链接`http://host:port/hystrix.stream`
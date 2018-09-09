# SpringBoot入门
- 概念
	- 什么是spring boot？</br>
		- **Spring Boot是由Pivotal团队提供的全新框架，其设计目的是用来简化新Spring应用的初始搭建以及开发过程。该框架使用了特定的方式来进行配置，从而使开发人员不再需要定义样板化的配置。其实，spring boot其实不是什么新的框架，它默认配置了很多框架的使用方式，就像maven整合了所有的jar包，spring boot整合了所有开发中常用的技术框架**
	- 使用spring boot的好处</br>
		- **SpringBoot帮助开发者快速启动一个Web容器；</br>
		SpringBoot继承了原有Spring框架的优秀基因；</br>
		SpringBoot简化了使用Spring的过程。</br>**
- 创建SpringBoot项目
	- 使用工具Idea创建项目
		- 第一步 创建新工程</br>
			![](http://m.qpic.cn/psb?/V10sTJNc2V5pgR/YZa3rnXJU.iHn9eZ1GHGCY9EebN0CbC28r4NunqU5zY!/b/dDQBAAAAAAAA&bo=NgauAwAAAAADN48!&rf=viewer_4)
		- 第二步 选择Springboot方式创建项目</br>
			![](http://m.qpic.cn/psb?/V10sTJNc2V5pgR/AIba6d9mRaZ*xjJFZzTpHPAH1xbU52uOLky0SbijheY!/b/dEkBAAAAAAAA&bo=ggc4BAAAAAADN6s!&rf=viewer_4)
		- 第三步 选择项目基本配置</br>
			![](http://m.qpic.cn/psb?/V10sTJNc2V5pgR/kU2wiPHGOF8xz7bcUkoIO1I596*DjDHeSz4hnR26uok!/b/dDcBAAAAAAAA&bo=gAc4BAAAAAADN6k!&rf=viewer_4)
		- 第四步 选择项目所需框架</br>
			![](http://m.qpic.cn/psb?/V10sTJNc2V5pgR/zhZD6ghlav5Sr56H0WNMQ6LYNGDm.ilJDDOmfXEOpok!/b/dC0BAAAAAAAA&bo=cQc4BAAAAAADN1g!&rf=viewer_4)
		- 第五步 完成创建</br>
			![](http://m.qpic.cn/psb?/V10sTJNc2V5pgR/L9HzoIbcrYglv9nIx7TxAg1ZBZzQsq9htsB6deyWZXo!/b/dFMBAAAAAAAA&bo=kwc4BAAAAAADJ6o!&rf=viewer_4)
			
- SpringBoot配置</br>
	- SpirngBoot有两种默认配置格式</br>
		- application.properties</br>
		- application.yml **(推荐使用)**</br>
	- application.yml方式配置端口号和URL后缀
		![](http://m.qpic.cn/psb?/V10sTJNc2V5pgR/reEy296VDSoyAVyQlvu300I.sS9QrxUcx*YMZ3IZDXA!/b/dFQBAAAAAAAA&bo=KgPGAwAAAAADB84!&rf=viewer_4)</br>
		![](http://m.qpic.cn/psb?/V10sTJNc2V5pgR/OZXlXhM*y7Ug0ChIPCBx4alO8.5YkG*6Hw0DTgjfy9M!/b/dFQBAAAAAAAA&bo=7gYiBAAAAAADR6w!&rf=viewer_4)</br>
		
- 编写简单方法hello word</br>
	- 创建hello word类</br>
		![](http://m.qpic.cn/psb?/V10sTJNc2V5pgR/BNA95vZERX1TtsX*r7zHZxBh.rwe8lS342pBjpDDqwY!/b/dFIBAAAAAAAA&bo=LQY4BAAAAAADBzU!&rf=viewer_4)</br>
		![](http://m.qpic.cn/psb?/V10sTJNc2V5pgR/m4NoHtfs5cTQC5J9ZWDDIBybK99lHHolnebJHSHHZgk!/b/dFMBAAAAAAAA&bo=ggNCAQAAAAADF*A!&rf=viewer_4)</br>
	- 编写hai方法</br>
		![](http://m.qpic.cn/psb?/V10sTJNc2V5pgR/pcmxm75oHg1CwXoPaOtC3H4O76VquF6eoJKmuAwHYNA!/b/dDABAAAAAAAA&bo=FAOeAQAAAAADB6o!&rf=viewer_4)</br>
	- 添加@RestController和 @RequestMapping注解</br>
		![](http://m.qpic.cn/psb?/V10sTJNc2V5pgR/dCetNOTzFMVJl2gbcR6sQfklw4KznLv1cryN3tGuE8o!/b/dDcBAAAAAAAA&bo=OgIeAQAAAAADJyU!&rf=viewer_4)</br>
	- 运行方法</br>
		![](http://m.qpic.cn/psb?/V10sTJNc2V5pgR/vL14.Zm4767sBnEVbV9.QKGrjeQWS93Ec01kGxPlscs!/b/dDYBAAAAAAAA&bo=ZAp.AQAAAAADBzM!&rf=viewer_4)</br>
	- 运行结果</br>
		![](http://m.qpic.cn/psb?/V10sTJNc2V5pgR/*hK9NxKBVE1LmkAVLq2JXMWaDcqreWfXy6AS2fTtr7w!/b/dDcBAAAAAAAA&bo=tAr8AQAAAAADB2E!&rf=viewer_4)</br>
		![](http://m.qpic.cn/psb?/V10sTJNc2V5pgR/cV0ucMMzu4ITPnltUdWXAYplOZyXzWZFIJI0n4WxXC4!/b/dFIBAAAAAAAA&bo=zAL8AAAAAAADFwA!&rf=viewer_4)</br>
- SpringBoot常用注解
	- **@Controller/@RestController/@RequestMapping介绍**
		- @Controller 处理http请求</br>
		  `@Controller`</br>
			`public class HelloController {`</br>
    	`@RequestMapping(value="/hello",method= RequestMethod.GET)`</br>
   ` public String sayHello(){`</br>
        `return "hello";`</br>
   ` }`</br>
`}`</br>
		- @RestController</br>
			`Spring4之后新加入的注解，原来返回json需要@ResponseBody和@Controller配合。`</br>
`即@RestController是@ResponseBody和@Controller的组合注解。`</br>
	  `@RestController`</br>
			`public class HelloController {`</br>
    	`@RequestMapping(value="/hello",method= RequestMethod.GET)`</br>
   ` public String sayHello(){`</br>
        `return "hello";`</br>
   ` }`</br>
`}`</br>
		- @RequestMapping 配置url映射</br>
			- 例子一：@RequestMapping仅作用在处理器方法上</br>
				`@RestController`</br>
`public class HelloController {`</br>
   ` @RequestMapping(value="/hello",method= RequestMethod.GET)`</br>
    `public String sayHello(){`</br>
       ` return "hello";`</br>
  `  }`</br>
`}`</br>
`以上代码sayHello所响应的url=localhost:8080/hello。`
			- 例子二：@RequestMapping仅作用在类级别上
			`@RestController`</br>
			` @RequestMapping(value="/hello")`</br>
`public class HelloController {`</br>
	`@RequestMapping(method= RequestMethod.GET)`
    `public String sayHello(){`</br>
       ` return "hello";`</br>
  `  }`</br>
`}`</br>
`以上代码sayHello所响应的url=localhost:8080/hello,效果与例子一一样，没有改变任何功能。`
			- @RequestMapping作用在类级别和处理器方法上</br>
				`@RestController`</br>
`@RequestMapping("/hello")`</br>
`public class HelloController {`</br>
   ` @RequestMapping(value="/sayHello",method= RequestMethod.GET)`</br>
   ` public String sayHello(){`</br>
       ` return "hello";`</br>
    `}`
   ` @RequestMapping(value="/sayHi",method= RequestMethod.GET)`</br>
   ` public String sayHi(){`</br>
       ` return "hi";`</br>
    `}`</br>
`}`</br>
	`以上代码中的sayHello所响应的url=localhost:8080/hello/sayHello，`
` sayHi所响应的url=localhost:8080/hello/sayHi`
	- **获取配置信息常用注解@Value，@ConfigurationProperties，@PropertySource**</br>
		- @value用法详解</br>
			- 两种使用方法</br>
				- @Value("#{configProperties['key']}")</br>
				- @Value("${key}")</br>
			- 配置</br>
				1. @Value("#{configProperties['key']}")使用</br>
					- value.yml</br>
						`key: 1`</br>
					- ValueDemo.java</br>
						` @Component`  </br>
` public class ValueDemo {  `</br>
` @Value("#{configProperties['key']}")  `</br>
` private String value;  `</br>
` public String getValue() { ` </br>
         `return value;  `</br>
    ` } ` </br>
`}`</br>
				2. @Value("${key}")使用</br>
					- value.yml</br>
						`key: 1`</br>
					- ValueDemo.java</br>
						` @Component`  </br>
` public class ValueDemo {  `</br>
` @Value("${key}")  `</br>
` private String value;  `</br>
` public String getValue() { ` </br>
         `return value;  `</br>
    ` } ` </br>
`}`</br>
	- **使用@ConfigurationProperties**</br>
		- value.yml</br>
			`connection.username=admin`</br>
`connection.password=123`</br>
`connection.remoteAddress=1127.0.0.1`</br>
		- demo.java</br>
			`@Component`</br>
 `@ConfigurationProperties(prefix="connection")`</br>
 ` public class ConnectionSettings {`</br>
 `     private String username;`</br>
 `     private String remoteAddress;`</br>
 `    private String password ;`</br>
 `     public String getUsername() {`</br>
`         return username;`</br>
`    }`</br>
`    public void setUsername(String username) {`</br>
`        this.username = username;`</br>
`    }`</br>
`    public String getRemoteAddress() {`</br>
`       return remoteAddress;`</br>
`     }`</br>
`    public void setRemoteAddress(String remoteAddress) {`</br>
`        this.remoteAddress = remoteAddress;`</br>
`    }`</br>
`    public String getPassword() {`</br>
`        return password;`</br>
`    }`</br>
`    public void setPassword(String password) {`</br>
`        this.password = password;`</br>
`    }`</br>

` }`</br>

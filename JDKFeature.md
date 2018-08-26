## jdk1.5
1. 自动装箱与拆箱 
	- 以前版本</br>
	`int n=10;` </br>
`Integer age= new Integer(30); `</br>
`Integer ageAfterTenYear= new Integer(age.intValue +10); 
`</br>
	- 当前版本</br>
	`int n=10; `</br>
`Integer age= new Integer(30); `</br>
`Integer ageAfterTenYear= age +10; `</br>
	- ps:
		`在没有加入自动装箱和拆箱前，得先将类型转换成int类型才能相加，加入新特性后编译器会自动将类型转换成int让后相加，不需要我们再手动转换类型`
2. 枚举
	- 例一
		`enum Season { winter, spring, summer, fall }`
	- 例二</br>
	 	`public enum Coin { `</br>
　`　penny(1), nickel(5), dime(10), quarter(25);` </br>
　　`Coin(int value) { this.value = value; } `</br>
　　`private final int value; `</br>
　　`public int value() { return value; } `</br>
　　`} `</br>
3. 静态导入
 - 非静态倒入</br>
 	`import org.yyy.pkg.Increment;` </br>
    `class Employee { `</br>
　　`public Double calculateSalary(Double salary{`</br>
　　`return salary + Increment.INCREMENT * salary; `</br>
　　	`}` </br>
　　`} `</br>
 - 静态倒入</br>
 	`import static org.yyy.pkg.Increment; `</br>
　　`class Employee { `</br>
　　`public Double calculateSalary(Double salary{ `</br>
　　`return salary + INCREMENT * salary; `</br>
　　	`} `</br>
　`　}`</br>
4. 可变参数（Varargs）
	`public static void main(String[] args) {`</br>
`int sum=add(1,2);`</br>
`System.out.println("累加和："+sum);`</br>
`}`</br>
	`private static int add(int...arr) {`</br>
`int sum=0;`</br>
`for(int i:arr){`</br>
`sum+=i;`</br>
`}`</br>
`return sum;`</br>
`}`</br>
	- ps:add方法的参数可以根据实际情况增加或减少
5. 内省（Introspector），主要用于操作JavaBean中的属性，通过getXxx/setXxx。一般的做法是通过类Introspector来获取某个对象的BeanInfo信息，然后通过BeanInfo来获取属性的描述器（PropertyDescriptor），通过这个属性描述器就可以获取某个属性对应的getter/setter方法，然后我们就可以通过反射机制来调用这些方法

6. 泛型(Generic)（包括通配类型/边界类型等）
	- 没有使用泛型
`List listOfEmployeeName = new ArrayList();`
	- 使用泛型
	`List<String> listOfEmployeeName = new ArrayList<String>(); `
	- ps:
	`如果你试图插入非string类型的值，你将在编译时发现并且修正这类问题。如果没有使用泛型，你将会在运行项目调用该方法后你所编写的程序抛出ClassCastException异常而崩溃。 
`
7. For-Each循环
	 - 没有加强前使用for循环</br>
	 `void printAll(Collection c) { `</br>
　　 `for (Iteratori = c.iterator(); i.hasNext(); ) { `</br>
　  `Employee emp = (Employee)i.next(); `</br>
　　`System.out.println(emp.getName()); `</br>
　　	`	} `</br>
　　`}`</br>
	 - 加强for循环后</br>
		`void printAll(Collection c) { `</br>
　　`for (Object o : c) `</br>
　　`System.out.println(o.getName()); `</br>
　　`}`</br>
	 - ps:</br>
	   `在这类For循环中，你应该将":"看成"in"，所以，在该例中可以看成"for Object o in c"。你可以发现这种For循环更具可读性`
8. 注解</br>
	- 不使用注解</br>
	`import org.yyy.hr;` </br>
　　	`public interface EmployeeI extends Java.rmi.Remote`</br> 
　　	`{`</br>
　　	`public String getName() `</br>
　　	`throws Java.rmi.RemoteException; `</br>
　　	`public String getLocation () `</br>
　　	`throws Java.rmi.RemoteException; `</br>
　　`	} `</br>
　  `public class EmployeeImpl implements EmployeeI { `</br>
　　`public String getName(){ `</br>
　　		`}` </br>
　　`public String getLocation (){ `</br>
　　		`}`</br>
　　`} `</br>
	- 使用注解</br>
	   `impor torg.yyy.hr; `</br>
　　`public class Employee { `</br>
　　`@Remote public String getName() {` </br>
　　`... `</br>
　　`} `</br>
　　`@Remote public public String getLocation() {` </br>
　　`... `</br>
　　`} `</br>
　　`} `</br>
9. 协变返回类型：实际返回类型可以是要求的返回类型的一个子类型

## jdk1.6
1. 使用JAXB2来实现对象与XML之间的映射，可以将一个Java对象转变成为XML格式，反之亦然
2. StAX，一种利用拉模式解析(pull-parsing)XML文档的API。类似于SAX，也基于事件驱动模型。之所以将StAX加入到JAXP家族，是因为JDK6中的JAXB2和JAX-WS 2.0中都会用StAX。
3. 使用Compiler API，动态编译Java源文件，如JSP编译引擎就是动态的，所以修改后无需重启服务器。
4. 轻量级Http Server API，据此可以构建自己的嵌入式HttpServer,它支持Http和Https协议。
5. 插入式注解处理API(PluggableAnnotation Processing API)
6. 提供了Console类用以开发控制台程序，位于java.io包中。据此可方便与Windows下的cmd或Linux下的Terminal等交互。
7. 对脚本语言的支持如: ruby,groovy, javascript
8. Common Annotations，原是J2EE 5.0规范的一部分，现在把它的一部分放到了J2SE 6.0中
9. 嵌入式数据库 Derby
10. 提供了Console类用以开发控制台程序，位于java.io包中。据此可方便与Windows下的cmd或Linux下的Terminal等交互。</br>

## jdk1.7
 1. 对Java集合（Collections）的增强支持，可直接采用[]、{}的形式存入对象，采用[]的形式按照索引、键值来获取集合中的对象。如：</br>
` List<String>list=[“item1”,”item2”];//存`</br>   `Stringitem=list[0];//直接取`</br>
`Set<String>set={“item1”,”item2”,”item3”};//存`</br>
`Map<String,Integer> map={“key1”:1,”key2”:2};//存`</br>
`Intvalue=map[“key1”];//取`</br>
 2. 在Switch中可用String
 	`public String test(String a) {`</br>
     `String umb;`</br>
     `switch (a) {`</br>
         `case "one":`</br>
            ` umb = "this is one";`</br>
            ` break;`</br>
         `case "two":`</br>
             `umb = "this is two";`</br>
            ` break;`</br>  
            	`}`</br>
     `return umb;`</br>
	`}`</br>
 3. 数值可加下划线用作分隔符（编译时自动被忽略）
 	- 字面常量数字的下划线。用下划线连接整数提升其可读性，自身无含义，不可用在数字的起始和末尾</br>
 	`int a2 = 5_2;`
 4. 支持二进制数字，如：</br>
 	`int binary= 0b1001_1001;`
 5. 简化了可变参数方法的调用
 	- 当程序员试图使用一个不可具体化的可变参数并调用一个**varargs**（可变）方法时，编辑器会生成一个“非安全操作”的警告。
 6. 调用泛型类的构造方法时，可以省去泛型参数，编译器会自动判断。
 	- 旧特性</br>
 		`ArrayList<String> list1 = new ArrayList<String>();`
 	- 新特性</br>
 	  	`ArrayList<String> list2 = new ArrayList();`
 7. Boolean类型反转，空指针安全,参与位运算
 8. char类型的equals方法:</br>	                                  
    `boolean Character.equalsIgnoreCase(char ch1, char ch2)`</br>
 9. 安全的加减乘除: </br>
 `Math.safeToInt(longv);` </br>
 `Math.safeNegate(int v);`</br>
 ` Math.safeSubtract(long v1, int v2);`</br>
 `Math.safeMultiply(int v1, int v2)`</br>
 `……`</br>
 10. Map集合支持并发请求，注HashTable是线程安全的，Map是非线程安全的。但此处更新使得其也支持并发。另外，Map对象可这样定义：</br>
 `Map map = {name:"age",age:18};`</br>
 
## jdk1.8
  1. 接口的默认方法：即接口中可以声明一个非抽象的方法做为默认的实现，但只能声明一个，且在方法的返回类型前要加上“default”关键字.如：</br>
  	`interface Formula {`</br>
    `double calculate(int a);`</br>
    `default double sqrt(int a) {`</br>
        `return Math.sqrt(a);`</br>
    `}`</br>
`}`</br>
`Formula formula = new Formula() {`</br>
   ` @Override`</br>
    `public double calculate(int a) {`</br>
       ` return sqrt(a * 100);`</br>
    `}`</br>
`};`</br>
`formula.calculate(100);     // 100.0`</br>
`formula.sqrt(16);           // 4.0`</br>
  2.  Lambda 表达式：是对匿名比较器的简化，如：</br>
  	- 老版本
  		`List<String> names = Arrays.asList("peter", "anna", "mike", "xenia");`</br>
`Collections.sort(names, new Comparator<String>() {`</br>
    `@Override`</br>
    `public int compare(String a, String b) {`</br>
        `return b.compareTo(a);`</br>
   ` }`</br>
`});	`</br>
  	- 新版本
  	`Collections.sort(names,(String a, String b) -> {`</br>
         `returnb.compareTo(a);`</br>
    `});`</br>
  	`Collections.sort(names, (String a, String b) -> b.compareTo(a));`</br>
  	`Collections.sort(names, (a, b) -> b.compareTo(a));`</br>
    
  3. 函数式接口：是指仅仅只包含一个抽象方法的接口，要加@FunctionalInterface注解</br>
  	`@FunctionalInterface`</br>
`interface Converter<F, T> {`</br>
    `T convert(F from);`</br>
`}`</br>
`Converter<String, Integer> converter = (from) -> `</br>
`Integer.valueOf(from);`</br>
`Integer converted = converter.convert("123");`</br>
`System.out.println(converted);    // 123`</br>
  4. 使用 :: 关键字来传递方法或者构造函数引用
  5. 多重注解</br>
  	`@interface Hints {`</br>
   ` Hint[] value();`</br>
`}`</br>
`@Repeatable(Hints.class)`</br>
`@interface Hint {`</br>
   ` String value();`</br>
`}`</br>
	- ps:Java 8允许我们把同一个类型的注解使用多次，只需要给该注解标注一下@Repeatable即可</br>
  6. 还增加了很多与函数式接口类似的接口以及与Map相关的API等……</br>
  7. Date API
  	- Clock 时钟
  		`Clock clock = Clock.systemDefaultZone();`</br>
`long millis = clock.millis();`</br>
`Instant instant = clock.instant();`</br>
`Date legacyDate = Date.from(instant);   // legacy java.util.Date`</br>
  	- Timezones 时区
  		`System.out.println(ZoneId.getAvailableZoneIds());
// prints all available timezone ids`</br>
`ZoneId zone1 = ZoneId.of("Europe/Berlin");`</br>
`ZoneId zone2 = ZoneId.of("Brazil/East");`</br>
`System.out.println(zone1.getRules());`</br>
`System.out.println(zone2.getRules());`</br>
`// ZoneRules[currentStandardOffset=+01:00]`</br>
`// ZoneRules[currentStandardOffset=-03:00]`</br>
  	- LocalTime 本地时间
  		`LocalTime now1 = LocalTime.now(zone1);`</br>
`LocalTime now2 = LocalTime.now(zone2);`</br>
`System.out.println(now1.isBefore(now2));  // false`</br>
`long hoursBetween = ChronoUnit.HOURS.between(now1, now2);`</br>
`long minutesBetween = ChronoUnit.MINUTES.between(now1, now2);`</br>
`System.out.println(hoursBetween);       // -3`</br>
`System.out.println(minutesBetween);     // -239`</br>
  	- LocalDate 本地日期
  		`LocalDate today = LocalDate.now();`</br>
`LocalDate tomorrow = today.plus(1, ChronoUnit.DAYS);`</br>
`LocalDate yesterday = tomorrow.minusDays(2);`</br>
`LocalDate independenceDay = LocalDate.of(2014, Month.JULY, 4);`</br>
`DayOfWeek dayOfWeek = independenceDay.getDayOfWeek();`</br>
  	- LocalDateTime 本地日期时间
  		`LocalDateTime sylvester = LocalDateTime.of(2014, Month.DECEMBER, 31, 23, 59, 59);`</br>
`DayOfWeek dayOfWeek = sylvester.getDayOfWeek();`</br>
`System.out.println(dayOfWeek);      // WEDNESDAY`</br>
`Month month = sylvester.getMonth();`</br>
`System.out.println(month);          // DECEMBER`</br>
`long minuteOfDay = sylvester.getLong(ChronoField.MINUTE_OF_DAY);`</br>
`System.out.println(minuteOfDay);    // 1439`</br>
  
# jdk1.9
 1. Java 平台级模块系统
	- 当启动一个模块化应用时， JVM 会验证是否所有的模块都能使用，这基于 `requires` 语句——比脆弱的类路径迈进了一大步。模块允许你更好地强制结构化封装你的应用并明确依赖。
2. Linking
	-  当你使用具有显式依赖关系的模块和模块化的 JDK 时，新的可能性出现了。你的应用程序模块现在将声明其对其他应用程序模块的依赖以及对其所使用的 JDK 模块的依赖。为什么不使用这些信息创建一个最小的运行时环境，其中只包含运行应用程序所需的那些模块呢？ 这可以通过 Java 9 中的新的 jlink 工具实现。你可以创建针对应用程序进行优化的最小运行时映像而不需要使用完全加载 JDK 安装版本。
3. JShell : 交互式 Java REPL
	- 许多语言已经具有交互式编程环境，Java 现在加入了这个俱乐部。您可以从控制台启动 jshell ，并直接启动输入和执行 Java 代码。 jshell 的即时反馈使它成为探索 API 和尝试语言特性的好工具。
4. 改进的 Javadoc
	- Javadoc 现在支持在 API 文档中的进行搜索。另外，Javadoc 的输出现在符合兼容 HTML5 标准。此外，你会注意到，每个 Javadoc 页面都包含有关 JDK 模块类或接口来源的信息。
5. 集合工厂方法
	- 通常，您希望在代码中创建一个集合（例如，List 或 Set ），并直接用一些元素填充它。 实例化集合，几个 “add” 调用，使得代码重复。 Java 9，添加了几种集合工厂方法：
6. 改进的 Stream API
	- 长期以来，Stream API 都是 Java 标准库最好的改进之一。通过这套 API 可以在集合上建立用于转换的申明管道。在 Java 9 中它会变得更好。Stream 接口中添加了 4 个新的方法：dropWhile, takeWhile, ofNullable。还有个 iterate 方法的新重载方法，可以让你提供一个 Predicate (判断条件)来指定什么时候结束迭代：
7. 私有接口方法
	- 使用 Java 9，您可以向接口添加私有辅助方法来解决此问题：
			
8. HTTP/2
	- Java 9 中有新的方式来处理 HTTP 调用。这个迟到的特性用于代替老旧的 `HttpURLConnection` API，并提供对 WebSocket 和 HTTP/2 的支持。注意：新的 HttpClient API 在 Java 9 中以所谓的孵化器模块交付。也就是说，这套 API 不能保证 100% 完成。不过你可以在 Java 9 中开始使用这套 API：
9. 多版本兼容 JAR
	- 我们最后要来着重介绍的这个特性对于库的维护者而言是个特别好的消息。当一个新版本的 Java 出现的时候，你的库用户要花费数年时间才会切换到这个新的版本。这就意味着库得去向后兼容你想要支持的最老的 Java 版本 (许多情况下就是 Java 6 或者 7)。这实际上意味着未来的很长一段时间，你都不能在库中运用 Java 9 所提供的新特性。幸运的是，多版本兼容 JAR 功能能让你创建仅在特定版本的 Java 环境中运行库程序时选择使用的 class 版本：

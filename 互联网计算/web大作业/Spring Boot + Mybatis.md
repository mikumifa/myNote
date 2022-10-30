![image-20221017184823031](Spring Boot + Mybatis.assets/image-20221017184823031.png)

![image-20221017184953479](Spring Boot + Mybatis.assets/image-20221017184953479.png)

![image-20221017185011165](Spring Boot + Mybatis.assets/image-20221017185011165.png)

![image-20221017185054828](Spring Boot + Mybatis.assets/image-20221017185054828.png)

![image-20221017185119416](Spring Boot + Mybatis.assets/image-20221017185119416.png)

![image-20221017185130605](Spring Boot + Mybatis.assets/image-20221017185130605.png)

![image-20221017185145429](Spring Boot + Mybatis.assets/image-20221017185145429.png)

对象和数据库的Table进行字段和属性的映射

## Spring Boot框架

![image-20221017190039544](Spring Boot + Mybatis.assets/image-20221017190039544.png)

IoC容器：容器创建对象，把对象连接起来，配置他们，并管理他们整个生命周期。使用依赖注入（DI）来管理组成一个应用程序组件，对象被叫Spring Beans

![image-20221017190424697](Spring Boot + Mybatis.assets/image-20221017190424697.png)

面向切面编程(AOP)框架

![image-20221017190631492](Spring Boot + Mybatis.assets/image-20221017190631492.png)

## Spring Boot配置文件：

application.properties文件和application.yml文件。他们的作用都是修改Spring Boot 自动配置的默认值

### YAML

用空格缩进程度来控制层次关系（不能用tab代替空格，大小写敏感）

 字面值：字符串，布尔类型，数值，日期。字符串默认不加引号，单引号会转 义特殊字符。日期格式支持yyyy/MM/dd HH:mm:ss

  对象：由键值对组成，形如 key:(空格)value(空格必须要有)，每组键值对占用 一行，且缩进的程度要一致。也可以使用行内写法：{k1: v1, ....kn: vn}

数组：由形如 -(空格)value 的数据组成(空格必须要有)，每组数据占用一行 ，且缩进的程度要一致。也可以使用行内写法： [1,2,...n]

复合结构：上面三种数据结构任意组合.

[YAML 入门教程 | 菜鸟教程 (runoob.com)](ht

[[一文看懂 YAML - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/145173920)tps://www.runoob.com/w3cnote/yaml-intro.html)

后缀： .yml

- ## 基本语法

  ### 大小写敏感

  - 就是字面上的意思

  ```yaml
  One: 1
  one: 2
  ```

  ### 用缩进表示层级关系

  - 缩进**只能使用空格**，不能用 TAB 字符
  - 缩进的**空格数量不重要**，但是**同一层级的元素左侧必须对齐**

  ```yaml
  # YAML
  one:
    two: 2
    three:
      four: 4
      five: 5
  
  // 以上的内容转成 JSON 后
  "one": {
    "two": 2,
    "three": {
      "four": 4,
      "five": 5 
    }
  }
  ```

  ### 用 # 表示注释

  - 只支持单行注释

  ```yaml
  # 我是注释
  # 我也是注释
  ```

  ### 一个文件中可以包含多个文件的内容

  - 用“ **---** ”即**三个破折号**表示一份内容的**开始**
  - 用“ **...** ”即**三个小数点**表示一份内容的**结束**（非必需）

  ```yaml
  ---
  # 这是第一份内容
  one: 1
  # 其他内容...
  ...
  
  ---
  # 这是第二份内容
  two: 2
  # 其他内容...
  ```

  ## 数据结构与类型

  ### 对象（Mapping）

  表示以键值对（key: value）形式出现的数据

  - 使用“**冒号+空格**”来分开**键**与**值**

  ```yaml
  # YAML
  key: value
  
  // JSON
  "key": "value"
  ```

  - 支持多层嵌套（**用缩进表示层级关系**）

  ```yaml
  # YAML
  key:
    child-key1: value1
    child-key2: value2
  
  // JSON
  "key": {
    "child-key1": "value1",
    "child-key2": "value2",
  }
  ```

  - 支持**流式风格（ Flow style）**的语法（用花括号包裹，用逗号加空格分隔，类似 JSON）

  ```yaml
  # YAML
  key: { child-key1: value1, child-key2: value2 }
  
  // JSON
  "key": { "child-key1": "value1", "child-key2": "value2" }
  ```

  - 使用**问号“?”**声明一个复杂对象，允许你使用多个词汇（数组）来组成键

  ```yaml
  # YAML
  ?
    - keypart1
    - keypart2
  :
    - value1
    - value2
  ```

  ### 数组（Sequence）

  - 一组以**区块格式（Block Format）（即“破折号+空格”）**开头的数据组成一个数组

  ```yaml
  # YAML
  values:
    - value1
    - value2
    - value3
  
  // JSON
  "values": [ "value1", "value2", "value3" ]
  ```

  - 同时也支持**内联格式（Inline Format）**来表达（用方括号包裹，逗号加空格分隔，类似 JSON）

  ```yaml
  # YAML
  values: [value1, value2, value3]
  
  // JSON
  "values": [ "value1", "value2", "value3" ]
  ```

  - 支持多维数组（**用缩进表示层级关系**）

  ```yaml
  # YAML
  values:
    -
      - value1
      - value2
    -
      - value3
      - value4
  
  // JSON
  "values": [ [ "value1", "value2"], ["value3", "value4"] ]
  ```

  ### 标量（Scalars）

  表示 YAML 中最基本的数据类型

  ### 字符串（String）

  - 字符串**一般不需要用引号包裹**，但是如果字符串中**使用了反斜杠“\”开头的转义字符就必须使用引号包裹**

  ```yaml
  # YAML
  strings:
    - Hello without quote # 不用引号包裹
    - Hello
     world # 拆成多行后会自动在中间添加空格
    - 'Hello with single quotes' # 单引号包裹
    - "Hello with double quotes" # 双引号包裹
    - "I am fine. \u263A" # 使用双引号包裹时支持 Unicode 编码
    - "\x0d\x0a is \r\n" # 使用双引号包裹时还支持 Hex 编码
    - 'He said: "Hello!"' # 单双引号支持嵌套"
  
  // JSON
  "strings":
    [ "Hello without quote",
      "Hello world",
      "Hello with single quotes",
      "Hello with double quotes",
      "I am fine. ☺",
      "\r\n is \r\n",
      "He said: 'Hello!'" ]
  ```

  - 对于多行的文字，YAML 提供了两种特殊的语法支持

  **保留换行(Newlines preserved)**

  > 使用**竖线符“ | ”**来表示该语法，每行的缩进和行尾空白都会被去掉，而额外的缩进会被保留

  ```yaml
  # YAML
  lines: |
    我是第一行
    我是第二行
      我是吴彦祖
        我是第四行
    我是第五行
  
  // JSON
  "lines": "我是第一行\n我是第二行\n  我是吴彦祖\n     我是第四行\n我是第五行"
  ```

  **折叠换行(Newlines folded)**

  > 使用**右尖括号“ > ”**来表示该语法，只有空白行才会被识别为换行，原来的换行符都会被转换成空格

  ```yaml
  # YAML
  lines: >
    我是第一行
    我也是第一行
    我仍是第一行
    我依旧是第一行
  
    我是第二行
    这么巧我也是第二行
  
  // JSON
  "lines": "我是第一行 我也是第一行 我仍是第一行 我依旧是第一行\n我是第二行 这么巧我也是第二行"
  ```

  ### 布尔值（Boolean）

  - “true”、“True”、“TRUE”、“yes”、“Yes”和“YES”皆为**真**
  - “false”、“False”、“FALSE”、“no”、“No”和“NO”皆为**假**

  ```yaml
  # YAML
  boolean:
    - true # True、TRUE
    - yes # Yes、YES
    - false # False、FALSE
    - no # No、NO
  
  // JSON
  "boolean": [ true, true, false, false ]
  ```

  ### 整数（Integer）

  - 支持二进制表示

  ```yaml
  # YAML
  int:
    - 666
    - 0001_0000 # 二进制表示
  
  // JSON
  "int": [ 666, 4096 ]
  ```

  ### 浮点数（Floating Point）

  - 支持科学计数法

  ```yaml
  # YAML
  float:
    - 3.14
    - 6.8523015e+5 # 使用科学计数法
  
  // JSON
  "float": [ 3.14, 685230.15 ]
  ```

  ### 空（Null）

  - “null”、“Null”和“~”都是空，不指定值默认也是空

  ```yaml
  # YAML
  nulls:
    - null
    - Null
    - ~
    -
  
  // JSON
  "nulls": [ null, null, null, null ]
  ```

  ### 时间戳（Timestamp）

  - YAML 也支持 **ISO 8601** 格式的时间数据

  > 这里使用 JavaScript 对象进行对比

  ```yaml
  # YAML
  date1: 2020-05-26
  date2: 2020-05-26T01:00:00+08:00
  dete3: 2020-05-26T02:00:00.10+08:00
  date4: 2020-05-26 03:00:00.10 +8
  
  // JavaScript
  date1: Tue May 26 2020 08:00:00 GMT+0800 (中国标准时间),
  date2: Tue May 26 2020 01:00:00 GMT+0800 (中国标准时间),
  dete3: Tue May 26 2020 02:00:00 GMT+0800 (中国标准时间),
  date4: Tue May 26 2020 03:00:00 GMT+0800 (中国标准时间)
  ```

  ### 类型转换

  - YAML 支持使用**严格类型标签“!!”**（双感叹号+目标类型）来强制转换类型

  ```yaml
  # YAML
  a: !!float '666' # !! 为严格类型标签
  b: '666' # 其实双引号也算是类型转换符
  c: !!str 666 # 整数转为字符串
  d: !!str 666.66 # 浮点数转为字符串
  e: !!str true # 布尔值转为字符串
  f: !!str yes # 布尔值转为字符串
  
  // JSON
  "a": 666,
  "b": "666",
  "c": "666",
  "d": "666.66",
  "e": "true"
  "f": "yes"
  ```

  ### 其他高级类型

  YAML 也可以使用一些更高级的类型，但是并不一定兼容所有解析器，包括**集合（Sets）**、**有序映射（Ordered Map）**、**十六进制数据（Hexdecimal）**和**二进制数据（Binary）。**

  **本文将不会对这几种类型进行讲解，感兴趣的读者可以自行搜索研究。**

  ## 数据重用与合并

  ![image-20221026145034009](Spring%20Boot%20+%20Mybatis.assets/image-20221026145034009.png)

  ![image-20221026145230549](Spring%20Boot%20+%20Mybatis.assets/image-20221026145230549.png)
  
  
  
  ![image-20221026145743188](Spring%20Boot%20+%20Mybatis.assets/image-20221026145743188.png)美元符号加上大括号是引用
  
  
  
  ![image-20221026150104789](Spring%20Boot%20+%20Mybatis.assets/image-20221026150104789.png)
  
  注入一个值。
  
  ![image-20221026150526926](Spring%20Boot%20+%20Mybatis.assets/image-20221026150526926.png)
  
  ![image-20221026150253190](Spring%20Boot%20+%20Mybatis.assets/image-20221026150253190.png)
  
  - Profile
  - 有一个注解@Configuration（翻译：配置）可以供使用
    1.创建一个类。
    2.使用注解@Configuration，告诉Spring Boot这是一个配置类。
  - @ConfigurationProperties最适用于所有具有相同前缀的分层属性，用于将配置文件中mail开头的属性绑定到POJO中,@[Configuration](https://so.csdn.net/so/search?q=Configuration&spm=1001.2101.3001.7020)也可以替换成@Component、@Service等其他注解
  - 为了保持内容的简洁，避免过多重复的定义，YAML 提供了由**锚点标签“&”**和**引用标签“\*”**组成的语法，利用这套语法可以快速引用相同的一些数据...

  ```yaml
  # YAML
  a: &anchor # 设置锚点
    one: 1
    two: 2
    three: 3
  b: *anchor # 引用锚点
  
  // JSON
  "a": {
    "one": 1,
    "two": 2,
    "three": 3
  },
  "b": {
    "one": 1,
    "two": 2,
    "three": 3
  }
  ```
  
  - 配合**合并标签“<<”**使用可以与任意数据进行合并，你可以把这套操作想象成面向对象语言中的继承...
  
  ```yaml
  # YAML
  human: &base # 添加名为 base 的锚点
      body: 1
      hair: 999
  singer:
      <<: *base # 引用 base 锚点，实例化时会自动展开
      skill: sing # 添加额外的属性
  programer:
      <<: *base # 引用 base 锚点，实例化时会自动展开
      hair: 6 # 覆写 base 中的属性
      skill: code # 添加额外的属性
  
  // JSON
  "human": { "body": 1, "hair": 999 },
  "singer": { "body": 1, "hair": 999, "skill": "sing" },
  "programer": { "body": 1, "hair": 6, "skill": "code" }
  ```

![image-20221017194249533](Spring Boot + Mybatis.assets/image-20221017194249533.png)

![image-20221017194318091](Spring Boot + Mybatis.assets/image-20221017194318091.png)

![image-20221017194336431](Spring Boot + Mybatis.assets/image-20221017194336431.png)

## **注解的定义**

注解通过 @interface 关键字进行定义。

```java
public @interface TestAnnotation {
}

@TestAnnotation
public class Test {
}
```

元注释

@Retention、@Documented、@Target、@Inherited、@Repeatable



## **@Retention**

- RetentionPolicy.SOURCE 注解只在源码阶段保留，在编译器进行编译时它将被丢弃忽视。

- RetentionPolicy.CLASS 注解只被保留到编译进行的时候，它并不会被加载到 JVM 中。

- RetentionPolicy.RUNTIME 注解可以保留到程序运行的时候，它会被加载进入到 JVM 中，所以在程序运行时可以获取到它们。

  用法

  ```
  @Retention(RetentionPolicy.RUNTIME)//把retention注释用在注释上，来设定生存时间
  public @interface TestAnnotation {
  }
  ```

  

## **@Documented**

顾名思义，这个元注解肯定是和文档有关。它的作用是能够将注解中的元素包含到 Javadoc 中去。

## **@Target**



Target 是目标的意思，@Target 指定了注解运用的地方。

你可以这样理解，当一个注解被 @Target 注解时，这个注解就被限定了运用的场景。

- ElementType.ANNOTATION_TYPE 可以给一个注解进行注解
- ElementType.CONSTRUCTOR 可以给构造方法进行注解
- ElementType.FIELD 可以给属性进行注解
- ElementType.LOCAL_VARIABLE 可以给局部变量进行注解
- ElementType.METHOD 可以给方法进行注解
- ElementType.PACKAGE 可以给一个包进行注解
- ElementType.PARAMETER 可以给一个方法内的参数进行注解
- ElementType.TYPE 可以给一个类型进行注解，比如类、接口、枚举

## **@Inherited**



Inherited 是继承的意思，但是它并不是说注解本身可以继承，而是说如果一个超类被 @Inherited 注解过的注解进行注解的话，那么如果它的子类没有被任何注解应用的话，那么这个子类就继承了超类的注解。

```text
@Inherited
@Retention(RetentionPolicy.RUNTIME)
@interface Test {}
@Test
public class A {}
public class B extends A {}
```



注解 Test 被 @Inherited 修饰，之后类 A 被 Test 注解，类 B 继承 A,类 B 也拥有 Test 这个注解。

## **@Repeatable**

```java
@interface Persons {
    Person[]  value();
}
@Repeatable(Persons.class)
@interface Person{
    String role default "";
}
@Person(role="artist")
@Person(role="coder")
@Person(role="PM")
public class SuperMan{
}
```

@Repeatable 注解了 Person。而 @Repeatable 后面括号中的类相当于一个容器注解。

## **注解的属性**

##### 注解的成员变量在注解的定义

中以“无形参的方法”形式来声明，其方法名定义了该成员变量的名字，其返回值定义了该成员变量的类型。

```text
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
public @interface TestAnnotation {
    int id();
    String msg();
}
```

赋值的方式是在注解的括号内以 value=”” 形式，多个属性之前用 ，隔开。

```text
@TestAnnotation(id=3,msg="hello annotation")
public class Test {
}
```

##### 注解中属性可以有默认值，默认值需要用 default 关键值指定。比如：

```text
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
public @interface TestAnnotation {
    public int id() default -1;
    public String msg() default "Hi";
}
```

有默认值，无需要再在 @TestAnnotation 后面的括号里面进行赋值了。

##### 注解内仅仅只有一个名字为 value 

，应用这个注解时可以直接接属性值填写到括号内。

```text
public @interface Check {
    String value();
}
```

##### 一个注解没有任何属性

```text
public @interface Perform {}
```

那么在应用这个注解的时候，括号都可以省略。

```text
@Perform
public void testMethod(){}
```

[java注解-最通俗易懂的讲解 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/37701743)

下面看不懂

![image-20221017201426682](Spring Boot + Mybatis.assets/image-20221017201426682.png)

![image-20221026151918280](Spring%20Boot%20+%20Mybatis.assets/image-20221026151918280.png)

加载不同的配置

spring.profiles.active=dev

![image-20221026152039878](Spring%20Boot%20+%20Mybatis.assets/image-20221026152039878.png)

完成配置的激活和切换

也可以配置虚拟机和命令行的参数![image-20221026152212551](Spring%20Boot%20+%20Mybatis.assets/image-20221026152212551.png)

![image-20221026152222654](Spring%20Boot%20+%20Mybatis.assets/image-20221026152222654.png)

![image-20221026152327062](Spring%20Boot%20+%20Mybatis.assets/image-20221026152327062.png)

打包

![image-20221026152506374](Spring%20Boot%20+%20Mybatis.assets/image-20221026152506374.png)

![image-20221026152607943](Spring%20Boot%20+%20Mybatis.assets/image-20221026152607943.png)

classpath是resource

![image-20221026153125431](Spring%20Boot%20+%20Mybatis.assets/image-20221026153125431.png)

![image-20221026153216702](Spring%20Boot%20+%20Mybatis.assets/image-20221026153216702.png)	

![image-20221026153258544](Spring%20Boot%20+%20Mybatis.assets/image-20221026153258544.png)

![image-20221026154716965](Spring%20Boot%20+%20Mybatis.assets/image-20221026154716965.png)

![image-20221026154759767](Spring%20Boot%20+%20Mybatis.assets/image-20221026154759767.png)

![image-20221026154907070](Spring%20Boot%20+%20Mybatis.assets/image-20221026154907070.png)

![image-20221026154931399](Spring%20Boot%20+%20Mybatis.assets/image-20221026154931399.png)

![image-20221026155042832](Spring%20Boot%20+%20Mybatis.assets/image-20221026155042832.png)

![image-20221026155135469](Spring%20Boot%20+%20Mybatis.assets/image-20221026155135469.png)

![image-20221026155207076](Spring%20Boot%20+%20Mybatis.assets/image-20221026155207076.png)

![image-20221026155337071](Spring%20Boot%20+%20Mybatis.assets/image-20221026155337071.png)

![image-20221026155411086](Spring%20Boot%20+%20Mybatis.assets/image-20221026155411086.png)

![image-20221026155428387](Spring%20Boot%20+%20Mybatis.assets/image-20221026155428387.png)

servlet收集用户的请求

![image-20221026164947513](Spring%20Boot%20+%20Mybatis.assets/image-20221026164947513.png)

![image-20221026170348137](Spring%20Boot%20+%20Mybatis.assets/image-20221026170348137.png)

@Controller控制器

@RequestMapping（value=“/”）

当浏览器发送的请求是/的时候会调用这个方法

## HTML

全局的标签

```
<!DOCTYPE html>	<!-- 声明这个html页面使用的版本，这样写代表是H5最新版本 -->
<html>
  <head>
  <meta charset="utf-8">  <!-- 告诉浏览器使用的是utf-8字符集 -->
      <title>我的网站</title>	<!-- 这里用来编写网站的标题，显示在浏览器选项卡的位置 -->
  </head>
  <body>	<!-- 只有body标签里面的内容，才能真正显示在浏览器的窗口中 -->
    <h1>我的第一个标签</h1>
    
    <p>我的第一个段落</p>
  </body>
</html>
```

```
<h1>最大的标题</h1>
<h2>标题二</h2>
<h3>标题三</h3>
<h4>标题四</h4>
<h5>标题五</h5>
<h6>标题六</h6>

<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf8" />
        <title>标题--HTML基础语法学习</title>
    </head>
    <body>
        <h1>我是一个h1标题</h1>
        <h2>我是一个h2标题</h2>
        <h3>我是一个h3标题</h3>
        <h4>我是一个h4标题</h4>
        <h5>我是一个h5标题</h5>
        <h6>我是一个h6标题</h6>
    </body>
</html>

<p>
	近日，西安女车主坐在66万买的奔驰车引擎盖上无奈维权引发各界密切关注。除了车本身的质量问题，该车主还质疑4S店诱其贷款收取的“金融服务费”存在欺诈。贷款买车究竟有哪些渠道？“金融服务费”是不是合理收费？贷款买车会遭遇哪些套路？消费者提前防范别踩坑里？北京青年报记者就这些问题采访了众多专业人士。
	据了解，汽车金融业务包括三种较为常见的模式。第一种为银行车贷，消费者向申请住房按揭一样向银行申请贷款，按照一定利率按月还款；第二种为信用卡分期，指持卡人同意支付首付款的情况下，向银行申请用其信用卡在银行指定的经销商购买家用汽车，经银行核准后，将审批通过金额平均分成若干期，由持卡人在约定期限内按月还款，并支付一定手续费。第三种模式为消费者向汽车金融公司申请贷款。也是西安奔驰维权事件中女车主选择的方式。第四种是近年来新兴的汽车融资租赁，即通过“以租代购、分期付款”的方式购车。
</p>

<img src="haha.jpg" title="图片的标题" alt="图片的属性" width="100px" height="100px" />

<img src="haha.jpg" />   <!--当前目录-->
<img src="./haha.jpg" /> <!-- 当前目录 -->
<img src="../haha.jpg" /> <!-- 上一级目录 -->
<img sr="C:\Users\Administrator\Pictures\timg.jpg" />//绝对路径


<ul>
    <li>第一个列表内容</li>
    <li>第二个列表内容</li>
</ul>//无序列表

<ol>
    <li>第一个列表内容</li>
    <li>第二个列表内容</li>
</ol>
//有序列表
<a href="https://www.bilibili.com/" target="_blank" title="点击可跳转到哔哩哔哩">哔哩哔哩</a>
<a href="跳转目标" target="目标窗口的弹出方式" title="超链接的介绍信息">文本或图像</a>
二、三种重要属性
1.href属性
href属性是超链接标签必须存在的属性，href用于连接目标的URL地址。

2.target属性
target用于指定页面的连接方式。其中_self是默认值，即在当前窗口打开连接的打卡方式，_blank为在新窗口的打开方式。

3.title属性
title为超链接设置一些介绍信息。当鼠标移到设置了title属性的超链接上时，会显示title属性值的内容。

```

![image-20221026172544461](Spring%20Boot%20+%20Mybatis.assets/image-20221026172544461.png)

xmlns的功能

### 2、@RequestMapping注解的位置

@RequestMapping标识一个类：设置映射请求的请求路径的初始信息

@RequestMapping标识一个方法：设置映射请求请求路径的具体信息

类上面有，方法上也有，可以相当于加上一层路径。

设置的属性越多，越精确

![image-20221026174529219](Spring%20Boot%20+%20Mybatis.assets/image-20221026174529219.png)

1、对于处理指定请求方式的控制器方法，SpringMVC中提供了@RequestMapping的派生注解

处理get请求的映射-->@GetMapping

处理post请求的映射-->@PostMapping

处理put请求的映射-->@PutMapping

处理delete请求的映射-->@DeleteMapping

2、常用的请求方式有get，post，put，delete

post,put提供数据，post侧重于增加，put是修改，

get是获取数据

delete是删除

![*image-20221026200147571*](Spring%20Boot%20+%20Mybatis.assets/image-20221026200147571.png)

[@Autowired注解的正确用法 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/59859778)

自动注入

DAO(Data Access Object)是一个数据访问接口，数据访问：顾名思义就是与数据库打交道。夹在[业务逻辑](https://baike.baidu.com/item/业务逻辑?fromModule=lemma_inlink)与数据库资源中间。

[![img](Spring%20Boot%20+%20Mybatis.assets/resize,m_lfit,w_184,limit_1.jpeg)](https://baike.baidu.com/pic/DAO/2900358/0/9dc3cf58ae3b5e92800a18bc?fr=lemma&fromModule=lemma_content-image&ct=single)

在核心[J2EE](https://baike.baidu.com/item/J2EE?fromModule=lemma_inlink)模式中是这样介绍DAO模式的：为了建立一个健壮的J2EE应用，应该将所有对[数据源](https://baike.baidu.com/item/数据源?fromModule=lemma_inlink)的访问操作抽象封装在一个公共[API](https://baike.baidu.com/item/API/10154?fromModule=lemma_inlink)中。用程序设计的语言来说，就是建立一个接口，接口中定义了此应用程序中将会用到的所有[事务](https://baike.baidu.com/item/事务?fromModule=lemma_inlink)方法。在这个应用程序中，当需要和数据源进行交互的时候则使用这个接口，并且编写一个单独的类来实现这个接口在逻辑上对应这个特定的数据存储。

@RequestBody：

作用：

主要用来接收**前端传递给后端**的**json字符串中的数据的**(请求体中的数据的)；

config.log()

# **JdbcTemplate**

是Spring对数据库的封装

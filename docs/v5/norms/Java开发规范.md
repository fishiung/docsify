# Java 开发规范


## 1 命名	

1. **`[J1-1]`**  代码中的命名均不能以下划线或美元符号开始或结束

   ```java
   错误 : __name / $name / name_ / name$ ...
   ```
   
2. **`[J1-2]`** 禁用拼音与英文混合的方式命名，禁用中文命名，杜绝不规范的缩写

3. **`[J1-3]`** 类名使用 **`UpperCamelCase`**风格

   > `DO`  / `BO` / `DTO ` / `VO`  / `PO` / `UUID` 等 特定业务含义包 / 专有名词 / 通用缩写 除外
   
    ```java
   错误 : UserDto / userBean / Userbean
   	
   正确 : UserDTO / UserBean / UserBean
    ```
   
4. **`[J1-4]`** 方法名、参数名、成员变量、局部变量都统一使用**`lowerCamelCase`**风格

   ```
   正确 : userList / getUsers() / getUserById (Integet userId)
   ```

5. **`[J1-5]`** 常量命名全部大写，单词间用下画线隔开，力求语义表达完整清楚，不要嫌名字长

   ```java
   错误 : MAX_VALUE / CREATE_Time
   正确 : MAX_ORDER_VALUE / CREATE_TIME
   ```

6. **`[J1-6]`**  抽象类命名使用**`Abstract`**开头

7. **`[J1-7]`**  异常类命名使用**`Exception`**结尾

8. **`[J1-8]`**  工具类命名使用**`Utils`**结尾

9. **`[J1-9]`**  测试类命名以它要测试的类的名称开始，以**`Test`**结尾

10. **`[J1-10]`**  数组定义 : 类型与中括号相连

   ```java
   错误 : int nums[]
   正确 : int[] nums
   ```

11. **`[J1-11]`** **`POJO`** 类中的任何布尔类型的变量，不可加**`is`**前缀，否则部分框架解析会引起序列化错误

12. **`[J1-12]`** 包名统一使用小写，点分隔符之间有且仅有一个自然语义的英语单词；包名统一使用单数形式

13. **`[J1-13]`** 如果模块、接口、类和方法使用了设计模式，在命名时需体现出具体模式

    |   设计模式    |          规约          |
    | :-----------: | :--------------------: |
    | 工厂/抽象工厂 | 使用 **Factory**  结尾 |
    |    建造者     | 使用 **Builder**  结尾 |
    |    适配器     | 使用 **Adapter**  结尾 |
    |     代理      |  使用 **Proxy**  结尾  |
    |    观察者     | 使用 **Observer** 结尾 |

14. **`[J1-14]`** 业务方法适用于`DAO`、`Repository`、`Service`、`Controller`层

    > 框架自动生成的模板方法不在要求范围内

    |           方法           |                        规约                         |
    | :----------------------: | :-------------------------------------------------: |
    |       获取单个对象       |  使用 get 做前缀，跟单数形式结尾如：`getObject()`   |
    | 获取对象列表（多个对象） | 使用 list 做前缀，跟复数形式结尾如：`listObjects()` |
    |           插入           |                 使用 insert 做前缀                  |
    |           删除           |                 使用 delete 做前缀                  |
    |        更新/修改         |                 使用 update 做前缀                  |
    |        查询/检索         |                 使用 search 做前缀                  |

15. **`[J1-15]`** 枚举类的枚举成员适用 **`[J1-5]`** 

## 2 常量定义

1. **`[J2-1]`** 不允许任何魔法值（即未经预先定义的常量）直接出现在代码中

   ```java
   错误 ：String serverAddress = "localhost" + ":" + port;
   ```

2. **`[J2-2]`** 在对**`long`**或者**`Long`**赋值时，数值后使用大写字母**`L`**，不能用小写字母**`l`**，小写字母**`l`**容易跟数字1混淆，造成误解

   ```java
   错误 : long num = 1l;
   正确 : long num = 1L;
   ```

3. **`[J2-3]`** 禁止将所有的常量维护在一个常量类中，应根据模块或者功能进行拆分，解耦

4. **`[J2-4]`** 如果变量值仅在一个固定范围内变化，使用枚举类型来定义

   ```java
   /**
   * 示例 - 多种任务状态
   */
   public class TaskStatus{
       WAITING, RUNNING, SUCCESSED, FAILURE
   }
   ```

## 3 代码格式

1. **`[J3-1]`** 大括号规约
   - 左大括号前不换行
   - 左大括号后换行
   - 右大括号前换行
   - 右大括号后，还有 `else`  等代码则不换行；表示终止的右大括号后必须换行
   - 如果大括号内没有内容，键入 `{}`， 不必换行

2. **`[J3-2]`** 代码单行字符数限制不超过 **120** 个，超出需要换行，换行时遵循如下原则
   - 运算符与下文一起换行
   - 方法调用的点符号与下文一起换行
   - 方法调用时，多个参数，需要换行时，在逗号后进行
   - 在括号前不换行
  
3. **`[J3-3]`** 单个方法不得超过**80**行；行数计算从方法声明至方法结束大括号

4. **`[J3-4]`** 单个类不得超过**2000**行；行数计算从类声明至类结束大括号

5. **`[J3-5]`** 在不同逻辑、不同语义、不同业务的代码之间插入**一个空行**，分隔开以提升可读性

## 4 OOP 规约

1. **`[J4-1]`** 避免通过一个类的对象引用访问此类的静态变量或静态方法

2. **`[J4-2]`** 所有的覆写方法都必须加`@Override`注解

3. **`[J4-3]`** 对外部正在调用或者依赖的接口，不允许修改方法签名，避免对接口调用方产生影响。若接口过时，则必须加`@Deprecated`注解，并清晰地说明采用的新接口或者新服务是什么

4. **`[J4-4]`** 不能使用过时的类或方法

5. **`[J4-5]`** 对象的`equals`方法容易抛空指针异常，应使用常量或确定有值的对象调用`equals`方法

   ```java
   错误 : username.equals("Tom");
   正确 : "Tom".equals(username);
   ```

6. **`[J4-6]`** 当定义数据对象DO类时，属性类型要与数据库字段类型相匹配

7. **`[J4-7]`** `POJO`类相关规约

   - 属性都必须使用**包装数据类型**，不能设定任何默认值
   - 成员变量私有，生成其对应的`getter`和`setter` 方法
   - 必须重写` equals`、`hashCode`、`toString` 方法

8. **`[J4-8]`** `RPC`方法的返回值和参数必须使用**包装数据类型**

9. **`[J4-9]`** 构造方法里面禁止加入任何业务逻辑，如果有初始化逻辑，那么请放在`init`方法中

10. **`[J4-10]`** 类成员与方法访问控制

    |                场景                |          规约           |
    | :--------------------------------: | :---------------------: |
    |  不允许外部直接通过`new`创建对象   | 构造方法限制为`private` |
    |         **工具类/常量类**          | 构造方法限制为`private` |
    | 类非`static`成员变量并且与子类共享 |    限制为`protected`    |
    | 类成员变量/类成员方法仅在本类使用  |     限制为`private`     |
    |    **类成员方法只对继承类公开**    |    限制为`protected`    |

11. **`[J4-11]`** 接口中不得出现 `public` 、`static`、`final `关键字

## 5 数值处理

1. **`[J5-1]`** 所有**整型**包装类对象之间值的比较，全部使用`equals`方法

2. **`[J5-2]`** 所有**浮点型**的值判断使用 差值法或者`BigDecimal.compareTo`方法，禁用 `==` 或者 `equals `方法

3. **`[J5-3]`** 禁止使用构造方法`BigDecimal(double)`的方式把`double`值转化为`BigDecimal`对象

   ```java
   //避免精度丢失，使用字符串类型的构造参数
   正确 : BigDecimal num = BigDecimal.valueOf("0.111111");
   ```

4. **`[J5-4]`** 时间格式精确到秒使用 `yyyy-MM-dd HH:mm:ss` ；精确到毫秒使用`yyyy-MM-dd HH:mm:ss.SSS`

   > 时间相关`Api` 建议使用`Java 8` 提供的 `java.time` 包

5. **`[J5-5]`** 获取当前毫秒数：`System.currentTimeMillis();`

## 6 集合处理

1. **`[J6-1]`** 关于·`hashCode`和`equals`的处理，遵循如下规则

   - 只要重写`equals`，就必须重写`hashCode`
   - **Set** 存储的对象必须重写这两种方法
   - 自定义对象作为**Map**的**键**，那么必须重写这两种方法

2. **`[J6-2]`** 判断所有集合内部的元素是否为空，应使用`isEmpty()`方法

3. **`[J6-3]`** 使用集合转数组的方法，必须使用集合的`toArray (T[] array)`，传入的是类型完全一致、长度为0的空数组

   ```java
   正确示例 : 
   List<Integer> nums = Arrays.asList(1,2,3,4,5);
   Integer[] array = nums.toArray(new Integer[0]);
   ```

4. **`[J6-4]`** 不要在`for`循环中对元素进行`remove/add`操作。当进行`remove`操作时，请使用`Iterator`方式，如果是并发操作，需要对`Iterator`对象加锁

   ```java
   List<Integer> list = new ArrayList<>(2);
   list.add(1);
   list.add(2);
   
   错误 : 
   for (Integer item : list){
       if(删除条件){
           list.remove();
       }
   }
   
   正确 :
   Iterator<Integer> iterator = list.iterator();
   Integer item;
   while (iterator.hasNext()){
       item = iterator.next();
       if(删除条件){
           iterator.remove();
       }
   }
   ```

5. **`[J6-5]`** 当使用工具类`Arrays.asList()`把数组转换成集合时，不能使用其修改集合相关的方法，它的add/remove/clear方法会抛出`UnsupportedOperationExceptio`异常

## 7 并发处理

1. **`[J7-1]`** 获取单例对象需要保证线程安全，其中的方法也要保证线程安全

   > 推荐饿汉式

2.  **`[J7-2]`** 当创建线程或线程池时，请指定有意义的线程名称，出错时方便回溯

   ```java
   /**
    * 正确示例代码 - 自定义线程工厂
    */
   public class XxxFactory implements ThreadFactory{
       private final String namePrefix;
       private final AtomicInteger nextId = new AtomicInteger(1);
       
       XxxFactory(String workGroup){
           namePrefix = workGroup + "-Worker-";
       }
       
       @Override
       public Thread newThread(Runnable r){
           String name = namePrefix + nextId.getAndIncrement();
           return new Thread(null, r, name, 0, false);
       }
   }
   ```

3. **`[J7-3]`** 线程池不允许使用`Executors`创建，而是通过`ThreadPoolExecutor`的方式创建，这样的处理方式能让编写代码的工程师更加明确线程池的运行规则，规避资源耗尽的风险

4. **`[J7-4]`** 必须回收自定义的`ThreadLocal`变量，再使用完毕且不会再传递时,避免造成内存泄露等问题；尽量在代理中使用`try-finally`块回收

5. **`[J7-5]`** 在高并发场景中，同步调用应该考量锁的性能损耗。能用无锁数据结构，就不要用锁；能锁区块，就不要锁整个方法体；能用对象锁，就不要用类锁，使加锁的代码块工作量尽可能的小，避免在锁代码块中调用`RPC`方法

6. **`[J7-6]`** 在对多个资源、数据库表、对象同时加锁时，需要保持一致的加锁顺序，否则可能会造成死锁

   > 如果线程一需要对表A、B、C依次全部加锁后才可以进行更新操作，那么线程二的加锁顺序也必须是A、B、C，否则可能出现死锁。

7. **`[J7-7]`** 在使用阻塞等待获取锁的方式中，必须在try代码块之外，并且在加锁方法与try代码块之间没有任何可能抛出异常的方法调用，避免加锁成功后，在finally中无法解锁

   ```java
   Lock lock = new XxxLock();
   
   错误 :
   try{
       doSomething();
       lock.lock();
       doOthers();
   } finally{
       lock.unlock();
   }
   
   正确 :
   lock.lock();
   try{
        doSomething();
   } finally{
       lock.unlock();
   }
   ```

8. **`[J7-8]`** 在使用尝试机制获取锁的方式中，进入业务代码块之前，必须先判断当前线程是否持有锁。锁的释放规则与锁的阻塞等待方式相同

   > 在执行`Lock`对象的`unlock`方法时，它会调用`AQS`的`tryRelease`方法（取决于具体实现类），如果当前线程不持有锁，则抛出`IllegalMonitorState Exception`异常

   ```java
   正确 :
   Lock lock = new XxxLock();
   //省略业务逻辑
   boolean isLocked = lock.tryLock();
   if(isLocked){
       try{
           doSomething();
       } finally{
           lock.unlock();
       }
   }
   ```

9. **`[J7-9]`** 对于多线程并行处理定时任务的情况，当`Timer`运行多个`TimeTask`时，只要其中之一没有捕获抛出的异常，其他任务便会自动终止。如果使用`ScheduledExecutorService`，则没有这个问题

10. **`[J7-10]`** 在高并发场景中，避免使用“等于”判断作为中断或退出的条件

    > 如果没有处理好并发控制，容易产生等值判断被“击穿”的情况，使用大于或小于的区间判断条件来代替

## 8 控制语句

1. **`[J8-1]`** switch 规约

   - `switch(expr)` 其中 `expr`不能为null，需在上下文中保证或者进行空指针判断

   - `case` 语句后换行
   - `case` 中的代码逻辑超过一行代码时，用大括号括起
   - `break `/ `continue `/`return` 等跳出语句不可省略
   - `default `语句不可省略，即使没有内容

   ```java
   //正确示例
   switch(expr){
   	case someCase1:
   		// 一行逻辑
   		break;
       case someCase2:
   	case someCase3:
   		{
   			/*
   			  多行逻辑
   			*/
   		}
   		break;
   	default:
   		//nothing
   		break;
   }
   ```

2. **`[J8-2]`**  在if/else/for/while/do语句中，**必须使用大括号**，不可忽略，即使一行逻辑

   > 表达异常的分支时，尽量少用if-else方式，这种方式可以改写成：
   >
   > ```java
   > if(结束条件){
   > 	...
   >     return obj;//return;
   > }
   > 
   > //接着写else 的业务逻辑代码
   > ```

3. **`[J8-3]`** 循环体中的语句要考量性能，以下操作尽量移至循环体外处理，如定义对象、变量、获取数据库连接，进行不必要的`try-catch`操作（这个`try-catch`是否可以移至循环体外）

## 9 注释规约

1. **`[J9-1]`** 类、类属性、类方法的注释必须使用`Javadoc`规范，使用`/**内容*/`格式，不得使用`// xxx`方式

2. **`[J9-2]`** 所有的抽象方法（包括接口中的方法）需描述返回值、参数、异常说明，方法作用，对子类的实现要求，或者调用注意事项

3. **`[J9-3]`** 类、类属性、类方法的注释必须含有 ，顺序不做要求

   - `@since` 何时引入
   - `@author` 作者
   - `@Version` 类的版本
   - `@date` 创建日期 格式为 `yyyy/MM/dd`

   ```java
    正确 : 
    /*
     * @author yuyang
     * @date 2021/01/01
     * @version 2.3.3
     * @since 2.3.2
     */
   ```

4. **`[J9-4]`** 对于方法内部的单行注释，在被注释语句上方另起一行，使用`//`注释。对于方法内部的多行注释，使用`/* */`注释，注意与代码对齐

5. **`[J9-5]`** 使用中文编写注释，仅专有名词与关键字保持英文原文；禁用“半吊子”英文注释，容易引起歧义

6. **`[J9-6]`** 在修改代码的同时，要对注释进行相应的修改，尤其是参数、返回值、异常、核心逻辑等

7. **`[J9-7]`** `//TODO`  （大写）须有标记人，标记时间，预处理时间，具体事项

8. **`[J9-8]`** `//FIXME` （大写）须有标记人，标记时间，预处理时间，问题说明

## 10 异常处理

1. **`[J10-1]`** 非与用户交互的模块，优先使用标准异常 （Java 类库自带）

2. **`[J10-2]`** Java类库中定义的可以通过预检查方式规避的`RuntimeException`不应该通过`try-catch`的方式处理，如：`NullPointerException`、`IndexOutOfBoundsException`等

   ```java
   错误 : 
   try{
       obj.method();
   }catch (NullPointerException e){
       ...
   }
   
   正确 :
   //1 
   if(obj != null){
       ...
   }
   
   //2
   Optional<Object> opt = Optional.ofNullable(obj);
   if(opt.isPresent()){
       ...
   }
   ```

3. **`[J10-3]`** 捕获异常是为了处理异常，不要捕获了却什么都不处理而抛弃之，如果不想处理它，请将该异常抛给它的调用者。最外层的业务使用者必须处理异常，将其转化为用户可以理解的内容，对界面操作用户可见的异常信息使用中文描述

   > 推荐制订同意的异常码 ，利于快速溯源、沟通标准化

4. **`[J10-4]`** 若处理异常。不能丢失异常

   ```java
    错误 :
    try {
        // ...
    } catch (Exception e) {
       //a. throw new SomeException(); 丢失异常
   	//b. log.error("some message"); 丢失异常
    }
   ```

5. **`[J10-5]`** 在事务场景中，抛出异常被catch后，如果需要回滚，那么一定要注意手动回滚事务

6. **`[J10-6]`** `finally`块必须对资源对象、流对象进行关闭操作，如果有异常就要做`try-catch`操作

   > `java.lang.AutoCloseable` 的实现类建议使用 `try-with-resources` 关闭
   > ```java
   > //示例 :
   > try(FileReader reader = new FileReader("test.txt"){
   >   /*
   > 	业务逻辑
   >   */
   > } catch (FileNotFoundException e) {
   > 	//业务逻辑
   > } 
   > ```

7. **`[J10-7]`** 不要在`finally`块中使用`return`

8. **`[J10-8]`** 防止产生空指针异常是程序员的基本修养，注意空指针异常产生的场景

## 11 日志规约

1. **`[J11-1]`** 应用中不可直接使用日志系统（`Log4j`、`Logback`）中的`API`，而应依赖使用日志框架`SLF4J`中的`API`，使用门面模式的日志框架，有利于维护日志并保证各个类的日志处理方式统一

2. **`[J11-2]`** 禁用 `System.out`或者 `System.err` 输出调试信息

3. **`[J11-3]`** 禁止输出无效日志，重复日志，用于Debug的日志必须的 debug 级别，禁止污染生产环境日志

4. **`[J11-4]`** 当输出日志时，字符串变量之间的拼接使用占位符的方式

   ```java
   错误 : log.debug("Not found user by id : " + userId);
   正确 : log.debug("Not found user by id : {}", userId);
   ```

## 12 其他

1. **`[J12-1]`** 在使用正则表达式时，利用好其预编译功能，加快正则匹配速度
2. **`[J12-2]`** 避免出现重复的代码（Don't Repeat Yourself），即DRY原则，重复代码行数不得超过5行 


--- 
>   参考 
>
> 《阿里巴巴Java开发手册（第2版）》
>
> 《Effective Java 中文版 （第3版）》
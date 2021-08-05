### 第五章 继承

在 Manager 与 Employee之间存在着明显的“isa”(是)关系,每个经理都是一名雇员: “ is-a”关系是继承的一个明显特征。

有些人认为 super 与 this 引用是类似的概念,实际上,这样比较并不太恰当。这是因为 super 不是一个对象的引用,不能将 super 赋给另一个对象变量,它只是一个指示编译器调用超类方法的特殊关键字

super可以调用父类的方法，也可以调用父类的构造器，但此时必须将父类的构造器代码放到第一行。

动态绑定实现多态



```
<dependency>
    <groupId>com.alibaba.security</groupId>
    <artifactId>security-all</artifactId>
    <version>2.0.6-SNAPSHOT</version>
    <type>pom</type>
</dependency>
```

```
String source = SecurityUtil.escapeHtml(param.getSource());
```







### 第14章 并发

#### 14.1 启动新线程

1. 将任务代码移动到实现了Runnable接口的类的run()方法

   ```java
   public interface Runnable {
     void run();
   }
   ```

   Runnable是一个函数式接口，可以用lambda

   ```java
   Runnable r = () -> { task code };
   ```

   由Runnable创建一个Thread对象

   ```java
   Thread t = new Thread(r);
   ```

   启动线程：

   ```java
   t.start();
   ```

   

2. 可以通过构建一个Thread类的子类定义一个线程

   ```java 
   class MyThread extends Thread {
     public void run() {
       task code
     }
   }
   ```

   不推荐这个方法，应该将要并行运行的任务与运行机制解耦。



#### 14.2 中断线程

```java
//将线程的中断状态置位。如果目前该线程被一个sleep调用阻塞，那么InterruptedException异常将会抛出
void interrupt()
  
//返回代表当前执行线程的Thread对象
static Thread currentThread()
  
//测试线程是否被终止
boolean isInterrupted()
  
//同上，但是它会将当前线程的中断状态重置为false
static boolean interrupted()
```



#### 14.3 线程状态

6种状态：

+ New
+ Runnable  可运行，可能正在运行也可能没有运行，取决于操作系统的分配
+ Blocked  被阻塞和等待状态有区别
+ Waiting  
+ Timed waiting 与等待状态的不同之处在于超时后会退出当前状态
+ Terminated



#### 14.4 线程属性

1. 线程优先级

2. 守护线程

3. 未捕获异常处理器

   | 名字                | 定义                       | 例子                   |
   | ------------------- | -------------------------- | ---------------------- |
   | checked exception   | 编译器要求必须处置的异常   | ClassNotFoundException |
   | unchecked exception | 编译器不要求必须处置的异常 | NullPointerException   |

   这里说的是，在线程死亡之前异常被传递到一个用于未捕获异常的处理器。


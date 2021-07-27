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


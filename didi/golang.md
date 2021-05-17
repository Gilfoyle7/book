### os.signal

```go
func Notify(c chan<- os.Signal, sig ...os.Signal)
```

类似于绑定信号处理程序。将输入信号转发到 chan c。如果没有列出要传递的信号，会将所有输入信号传递到 c；否则只传递列出的输入信号。

channel c 缓存如何决定？因为 `signal` 包不会为了向 c 发送信息而阻塞（就是说如果发送时 c 阻塞了，signal 包会直接放弃）：调用者应该保证 c 有足够的缓存空间可以跟上期望的信号频率。对使用单一信号用于通知的 channel，缓存为 1 就足够了。



[Go mod使用指南](https://studygolang.com/articles/31112)

[init函数详解][https://zhuanlan.zhihu.com/p/34211611]



#### 匿名字段和struct嵌套

+ struct中的字段可以不给名称，称为匿名字段，匿名字段的名称强制和类型相同

+ 直接带名称嵌套struct时，不会再自动深入到嵌套struct中去查找属性和方法。想要访问内部struct属性时，必须带上该struct的名称。

  例如：

  ```
  type animal struct {
      name string
      age int
  }
  type Horse struct{
      a animal
      sound string
  }
  ```

  这时候，想要访问嵌套在Horse中animal的name属性，则只能通过`h.a.name`的方式（h为Horse的实例对象），且访问`h.name`时将直接报错，因为在Horse里找不到name属性。





#### 方法

方法实际上也是函数，只是在声明时，在关键字func和方法名之间增加了一个参数。例子：

```go
type user struct {
   name string
   email string
}


func (u *user) changeEmail(email string) {
   u.email = email
}

func (u user) notify() {
   fmt.Printf("Sending User Email To %s<%s>\n", u.name, u.email)
}


func main() {

   bill := user{"Bill", "bill@qq.com"}
   bill.notify()

   lisa := &user{"Lisa", "lisa@qq.com"}
   lisa.notify()

   bill.changeEmail("bill@163.com")
   bill.notify()

   lisa.changeEmail("lisa@163.com")
   lisa.notify()
}
```

+ 非本地类型不能定义方法，也就是说我们不能给别的包的类型定义方法。
+ changeEmail定义了一个指针接收者的方法，notify定义了一个值接收者的方法。如果使用值接收者声明方法，调用时会使用这个值的一个副本来执行。而调用使用指针接收者声明的方法时，这个方法会共享调用方法时接收者所指向的值。
+ Go语言既允许值，也允许使用指针来调用方法，不必严格符合接收者的类型。因为编译器将对指针与值之间进行自动转换。



### cobra使用

+ 如果go install时候提示有多个包，可以指定cobra的版本 go get github.com/spf13/cobra/cobra@1..0.0
+ cobra生成器wiki  https://github.com/spf13/cobra/blob/master/cobra/README.md， 安装过后会在$GOPATH/bin中创建一个cobra执行文件，想要在任何文件夹中都执行，将其加到环境变量中即可export PATH=$PATH:/Users/didi/go/bin
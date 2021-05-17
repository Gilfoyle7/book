### ch2.1 线程管理 

每个程序至少有一个执行main的线程，其余线程通过入口函数进入。

#### 2.1.1 启动线程

启动线程相当于构造std::thread对象

thread除了可以用函数构造，也可以用可调用class构造，即为定义()运算符的类

```c++
class background_task {
public:
    void operator()() const {
        do_somthing();
    }

private:
    void do_somthing() const {
        std::cout << "hello";
    }
};

background_task f;
std::thread my_thread(f)
```

1. 函数对象会复制到新线程的内存空间。
2. 不能传递临时对象，否则等于声明一个function，而不是thread

启动之后需要决定是等待线程结束，还是让其自主运行，如果在thread对象销毁之前没有决定，则thread的析构函数会调用terminate()

如果不等待，则需要保证在线程结束前，该线程可访问数据的有效性（主要针对引用和指针） => Solution:1.可将数据复制到线程中，而非复制在共享数据中 2.调用join()

#### 2.1.2 等待线程完成 :jack_o_lantern:

调用join()，将会清理线程相关的存储部分，只能对每个线程调用一次 

#### 2.1.3 特殊情况下的等待














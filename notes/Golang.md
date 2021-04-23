+ channel

  + channel的同步和异步问题
    + channel无缓冲时，发送阻塞直到数据被接收，接收阻塞直到读到数据。
    + channel有缓冲时，当缓冲满时发送阻塞，当缓冲空时接收阻塞。

+ 并发

  + channel
  + sync.WaitGroup
  + Context 

+ 数据结构

  + map

    https://blog.csdn.net/u010853261/article/details/99699350
    
  + channel

+ 标准库

  + sync.Pool

    + 对于很多需要重复分配和回收内存的地方，sync.Pool是一个很好的选择。频繁地分配和回收内存会给GC带来一定的负担，严重的时候会引起CPU的毛刺，而sync,Pool可以将暂时不用的对象缓存起来，待下次需要的时候直接使用，减少GC的压力，提升系统的性能。
    + 协程安全

  + unsafe.Pointer

    + 任何类型的指针值都可以转换为Pointer
    + Pointer可以转换为任何类型的指针值
    + uintptr可以转换为Pointer
    + Pointer可以转换为uintptr

    总结：(1)unsafe.Pointer可以让你的变量在不同的指针类型转换，类似C语言的void* (2)uintptr常用于和unsafe.Pointer做配合，用于指针运算

+ Q&A

  1. Q: nil的Slice和空的Slice一样吗？

     A：不一致，空的Slice可以与nil进行比较。而empty slice底层不是空的，只是长度为0
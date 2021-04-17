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

+ 面试题

  1. Q: nil的Slice和空的Slice一样吗？

     A：不一致，空的Slice可以与nil进行比较。而empty slice底层不是空的，只是长度为0
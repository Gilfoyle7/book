+ #### 多线程

  1. Q：如何设计IO密集型多线程和CPU密集型多线程？

     A：**CPU密集型任务（CPU-bound）**：在一个任务中，主要做计算，CPU持续在运行，CPU利用率高，具有这种特点的任务称为CPU密集型任务。
     **IO密集型任务（IO-bound）**：在一个任务中，大部分时间在进行I/O操作，由于I/O速度远远小于CPU，所以任务的大部分时间都在等待IO，CPU利用率低，具有这种特点的任务称为IO密集型任务。
     https://blog.csdn.net/LGM_lx/article/details/88898036

     - CPU密集型任务：线程个数为CPU核数。这几个线程可以并行执行，不存在线程切换到开销，提高了cpu的利用率的同时也减少了切换线程导致的性能损耗
     - IO密集型：线程个数为CPU核数的两倍。到其中的线程在IO操作的时候，其他线程可以继续用cpu，提高了cpu的利用率

  2. 


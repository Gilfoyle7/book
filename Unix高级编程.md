## 文件I/O

UNIX大多数文件I/O只要五个函数：*open、read、write、lseek和close*，本章描述不带缓冲的I/O

对于内核，所有打开的文件通过文件描述符引用。按照惯例，UNIX系统shell把文件描述符0与进程的标准输入关联，1与标准输出关联，2与标准错误。文件描述符的变化范围是**~OPEN_MAX-1**

### open和openat

```c
int open(const char *path, int oflag, ...);
int openat(int fd, const char *path, int oflag, ...);
```

最后一个参数是...，ISO C用这种方法表明余下的参数数量及其类型是可变的。通俗来讲，就是在一些情况下可以省略掉。

**不同之处**：

1. path参数若是绝对路径名，fd参数被忽略，openat与open用法相同。

   ```c
   fd = open("/home/leon/test.c", O_RDWR | O_CREAT, 0640);
   fd = openat(anything, "/home/leon/test.c", O_RDWR | O_CREAT, 0640);
   ```

2. path参数若是相对路径名，fd参数指出相对路径名在文件系统中的开始地址。fd参数通过打开相对路径名所在的目录来获取。

   ```c
   DIR* dir_chalion = opendir(/home/chalion);
   fd_chalion = dirfd(dir_chalion);
   fd = openat(fd_chalion, "test.c" ,O_RDWR | O_CREAT, 0640);
   ```

   

3. path参数若是相对路径名，fd等于特殊值AT_FDCWD。此时openat与open函数类似，路径名都是在当前工作目录获取。

   ```c
   fd = open("./test.c", O_RDWR | O_CREAT, 0640);
   fd = openat( AT_FDCWD, "./test.c", O_RDWR | O_CREAT, 0640);
   ```

openat函数希望解决两个问题，第一个是让线程可以使用相对路径名打开目录中的文件，而不再只能打开当前工作目录。第二个是可以避免***TOCTTOU***错误。

### creat和close

```c
int creat(const char *path, mode_t mode);
//open(path, O_WRONLY | O_CREAT | O_TRUNC, mode);
int close(int fd);
```

creat的不足是它以只写方式打开所创建的文件。close函数关闭一个打开文件，关闭文件时会释放该进程加在该文件上的所有记录锁。当一个进程终止时，内核自动关闭它所有的打开文件。






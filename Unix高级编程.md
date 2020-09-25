#文件I/O

UNIX大多数文件I/O只要五个函数：*open、read、write、lseek和close*，本章描述不带缓冲的I/O

对于内核，所有打开的文件通过文件描述符引用。按照惯例，UNIX系统shell把文件描述符0与进程的标准输入关联，1与标准输出关联，2与标准错误。文件描述符的变化范围是**~OPEN_MAX-1**

###open和openat

```c
#include <fcntl.h>

int open(const char *path, int oflag, ...);

int openat(int fd, const char *path, int oflag, ...);
```
+ #### Q&A：

  1. MySQL主从复制之后，主数据库和从数据库之间有延迟，怎么解决？
  2. 输入一些数据，如何判断数据是不是有周期？
  3. 输入有序的N个集合，如何把集合按组合输出？
  4. nginx







datetime vs timestamp

https://zhuanlan.zhihu.com/p/23663741 

https://stackoverflow.com/questions/409286/should-i-use-the-datetime-or-timestamp-data-type-in-mysql

task_monitor_data task_id last_update_time

ALTER TABLE tb_name ALGORITHM=inplace, LOCK=NONE, ADD INDEX IDX_VID_CID(vid,cid)

```sql
ALTER TABLE task_monitor_data ADD INDEX idx_task_id(task_id), ALGORITHM=INPLACE, LOCK=NONE;
```

LIMIT 子句可以被用于强制 SELECT 语句返回指定的记录数。**LIMIT 接受一个或两个数字参数**。参数必须是一个整数常量。如果给定两个参数，**第一个参数**指定第一个返回记录行的**`偏移量`**，**第二个参数**指定**返回记录行的最大数目**。`初始记录行的偏移量是 0(而不是 1)`

 **mysql -h 10.89.70.46 -u user1 -p -P 3308** 登录远程数据库命令



 

**mysqldump -uroot -p -P 8006 -h z **--hex-blob --set-gtid-purged=OFF --single-transaction --order-by-primary --flush-logs -q --databases** *db1 db2* **>db12.sql**


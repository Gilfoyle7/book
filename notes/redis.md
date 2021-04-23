https://juejin.cn/post/6844904017387077640#heading-7

+  #### 缓存雪崩、穿透、击穿

  1. 缓存雪崩，大范围的缓存失效，导致请求打到数据库上 --》 每个key的失效时间都加个随机数，保证数据不会同一时间大面积失效。
  2. 缓存穿透，是指用户不断访问缓存和数据库中都没有的数据，导致数据库压力增大 --> 用户鉴权，参数做校验，布隆过滤器（利用数据结构判断key是否在数据库里）。
  3. 缓存击穿，用户不断访问某个热点key，在key失效的瞬间，持续的大并发直接落到了数据库上，就在这个key点击穿了缓存 --》热点数据不过期，互斥锁

+ 淘汰策略

  
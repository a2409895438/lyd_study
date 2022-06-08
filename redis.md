# Redis

```bash
redis-server /etc/redis.config
redis-cli
ps -ef | grep redis

select 0
```

### Redis 键KEY

- keys * 查看当前库所有key
- exists key 判断某个key存在
- type key 查看key的类型
- del key 删除指定的key
- unlink key 根据value选择非阻塞删除 仅将keys从keyspace元数据中删除 真正的删除会在后续异步操作
- expire key 10：为key 设定过期时间
- ttl key:查看还有多少秒过期  -1表示永不过期  -2表示已经过期
- 
- select 切换数据库
- dbsize查看当前数据库key的数量
- flushdb 清空当前库
- flushall 通杀所有库



### String字符串

是二进制安全的

是Redis最基本的数据类型，一个Redis中字符串的value最多可以是512M。

- set key value
- get key
- append k1 value 追加到末尾
- strlen key 得到值的长度
- setnx key value 只有key不存在的时候，才能设置key的值
- incr   将key存储的数字值加1
- decr 将key中存储的数字值减1
- incrby/decyby key <步长>

- mset <><><>  设置多个
- mget <><>
- msetnx    原子性 有一个失败怎全失败
- getrange key a b  闭区间内范围值
- setrange key ...
- setex key <过期时间> value

### List列表

底层是一个双向链表

- lpush/rpush  从左边或者右边插入多个值
- lrange key 开始 结束 取值
- lpop/rpop key <count> 吐出一个值  键在值在，值光键亡
- rpoplpush 从k1右边取值插入到k2左边
- lindex key <index> 按照下表获取元素
- llen key 取得列表长度
- linsert key before value <newvalue> 在值的前面加入一个新的值
- lrem key <n> <value> 从左边开始删除n个value值
- lset key index value 将index处值替换成value

底层为quickList

### Set集合

自动排重

底层是一个value为null的hash表

- sadd 添加一个或者多个元素
- smembers 去除集合中的所有值
- sismenber 判断是否含有
- scard 返回集合中元素的个数
- srem 删除
- spop 随机吐出一个值
- srandmember 随机取出n个值 不会删除
- smove  把集合中的一个值从一个集合移动到另一个集合
- sinter 交集元素
- sunion 并集
- sdiff  取差集

### Hash 哈希

是一个string field和value的映射表

- hset
- hget
- hmset 批量
- hexists 给定域field是否存在
- hkeys   列出所有field
- hvals
- hincrby  为key中的field加n
- hsetnx当且仅当不存在的时候添加

### Zset 有序集合

每个成员都关联了一个评分，按照升序来排序

- zadd
- zrange 带上WITGSCORES可以让分数一起返回
- zrangebyscore
- zrevrangebyscore key 倒序
- zincrby
- zrem 删除指定值的元素
- zcount 统计分数间的值
- zrank

底层使用了hash和跳跃表

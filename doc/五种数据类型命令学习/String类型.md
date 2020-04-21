

1.字符串

value值最大值不可超过 512M

set java hello

get java

===>  hello


 **自增：** 

incr num

get num
==>  1

incrby num 10
get num
==> 11

incr  给key对应的value 值新增1  incrby key num  给key对应的value 值新增num

redis 自增 开销比较小 因为是单线程  无须cas 去保证顺序生成

减少是 对应的是 decr decrby



设置值：
  set key value   (不管key是否存在都设置值)
  setnx key value  （只可以设置 不存在的key值  setnx   nx 可简记为  Not eXist）   //可以作为分布式锁的实现方式
  set key value xx  （只可设置已经存在的）


设置key - value 同时设置过期时间
set java hi ex 10   ||  ex 10 表示10秒过期
也可以 
set java hi 
expire  java 10  

获取值  
get java  
==>  hi     过期后  获得nil

批量设值  可以减少  网络通讯的损耗
mset  ==》 more set
mset key1 value1 key2 value2 key3 value3

批量取值
mget key1 key2 key3
返回：
 value1
 value2
 value3

不常用命令：
追加字符串：
append key 追加字符串

set key redis
get key ===> redis
append key world ==> 返回总长度
get key ====> redisworld
获取字符串长度
strlen key 
strlen key ==>10

设置并返回旧值
getset key value  返回旧值
getset key haha  返回redisworld


关于字符串的截断操作
set range 0123456789
setrange range 2 x
get range ==> 01x3456789
getrange range 0 3 ==> 01x3  (此处的开始结束位置  都为闭的操作  即包含)

关于编码：

字符串的编码有3种     （关于编码 https://www.jianshu.com/p/666452a22855）
int 编码：保存long 型的64位有符号整数  （redis启动的时候 会创建0~9999 这个键值   value 为0~9999的时候  会启动共享策略）
embstr 编码：保存长度小于44字节的字符串
raw 编码：保存长度大于44字节的字符串（此刻内存不在连续存储）


查看是哪种编码的  
用object encoding key 

 set java 1234556666 ；
 obeject encoding java ===> int 
其他类似








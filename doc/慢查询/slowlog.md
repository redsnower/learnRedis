 1.慢查询的机制
配置参数一：
config get slowlog-max-len   =>
128  //默认
     redis会把超过一定时间的 redis 请求保存特殊队列中  这个特殊的队列的长度有限制 
超过了限制就会 把覆盖第一条    

config get slowlog-log-slower-than   =>  10000毫秒    
     redis 中的 超时时间设置  超过此事件就会记录下来 

设置  
cofig set slowlog-log-slower-than 1000  
cofig set slowlog-max-len 256   
config rewrite


如果rewrite  这个环节出错   chown redis:redis /etc/redis/redis.conf  修改权限


slowlog len
查看慢查询  条数

slowlog get [n]  
查询详细前多少条记录

slowlog reset
重置 慢查询的 列表




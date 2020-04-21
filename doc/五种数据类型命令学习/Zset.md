1.有序集合  

在集合中插入顺序为有序的
![输入图片说明](https://images.gitee.com/uploads/images/2020/0220/163805_f5607f12_4955170.png "屏幕截图.png")  
   　　　　　　　　　　　　　　　　
　

　
zset中   元素的值不可以重复   但是score是可以重复的  
有序集合中  命令都带以  z开头


1.添加  
zadd  key score value
  
可一次性添加多个   zadd name 100 bob 101 nancy 102 kilan 103 chunjie（redis3.2 之后也有 nx  xx表示设置元素值存在不存在 相应处理）
查看个数  
zcard name
查看某个 元素值score分数  
zscore name bob  == 》  返回100
查看元素排名 正序排  
zrank name chunjie    ===》  score排名第四  故返回3
zrevrank name chunjie   ==> 倒叙排列  查询chunjie  ==》返回0

删除某一个成员  
zrem name bob chunjie//可以一次删除多个

//增加成员的score 分数  
zincrby name 10 nancy  ==》nancy的score值增加10  
zscore name nancy  ==》111

返回指定排名的成员
  
  zrange name 0 -1 withscores   //查询所有 从低到高  
  zrange name 0 1 withscores   //查询排名从第一到第二
  
  这个api 数字都是表示开始排名的位置  和结束的位置  下面的是 用score代替的api
  
  zrangebyscore name 102 111 withscores   返回 score的分数在  102 和111之间的数据
  
  查询指定score范围内中有多少个
  
  zcount name 102 111   //此处为 score分数的集合范围
  
  删除指定score范围的
  
  zremrangebyrank  name 0   0   删除数据排名 第一的  
  zremrangebyscore name 111 111  删除数据score为 111可以写范围


 








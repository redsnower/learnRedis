 list 操作：
 从右边开始插入：
   rpusn list a b c
  
 从左到右全部  查询列表
   lrange list 0 2   （redis中 多数的 边界 都是包含的 不像java 多数为左闭右开）
   
  查出部分 就是  lrang list start end

  
  插入操作 

 linsert list before c d   //在列表的c值前插入 一个元素值为d  list中有多个 c的时候  只插入第一条
 llen list  查询 list 长度
 
 lindex list 0  ===》 返回列表中的第一个元素
 lindex list -1  ===》 返回列表中的最后一个元素
  
 
 删除 操作
 lpop list 从最左边弹出元素 并在list中剔除

 rpop 同样功能  从右边开始

 删除 指定元素
 lrem key count value   
  lrem list  0 'd' ===> 表示从 list的集合中 删除 全部  值为d的元素  
                 count 为0 表示删除全部  count>0 表示从左到右  <0 表示从右到左
  
 上文中的 lrange list 0 N-1 (N为长度) 为查询  
 ltrim 是按照开始结束位置生产一个新的
 ltrim list 1 3 截取 第2个到第四个的 元素生成新的list
  如下图：
![输入图片说明](https://images.gitee.com/uploads/images/2020/0219/224416_2a1cc2a8_4955170.png "屏幕截图.png")



   
 对指定位置的元素设置值：
 lset list 1 x   ===》 把第二个位置的值设置成 b
 lrange list 0 2
=====》  a  x  k
 
 阻塞弹出操作
 brpop list_1 0 
 解释：  ===》  brpop  从右边开始 阻塞 弹出   list_1 表示 key   0 表示 阻塞时间 为0 时  则一直阻塞 为3则3秒后  
  仍然没有值则推出

  关于pop 和push的方向  可以理解成
   lpush rpop ==队列
   lpush lpop 栈 
   




 















  


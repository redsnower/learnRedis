pipeline  一次性接受  命令  

减少 执行命令时 网络请求所消耗的时间
将多次网络请求打包成一个命令  网络传输变成一次

redis的命令时间是微秒级别的 所以网络请求消耗的时间  是比较大的

java代码层面 不要一次使用过大的数据请求  不稳定 
可以像下面一样而不是一个for循环写完所有数据     
    for (int i = 0; i < 300; i++) {
		  Pipeline pl = je.pipelined();
		  for (int j = i*100; j < (i+1)*100; j++) {
			  pl.set("key"+j,"value"+j );
		}
	 }


如果写成：
 
		  Pipeline pl = je.pipelined();
		  for (int j = 0; j < 30000; j++) {
			  pl.set("key"+j,"value"+j );
		 }
	 有可能会丢失数据


pipeline 每次只能作用在一个redis节点上

m操作 是一个原子操作的节点  
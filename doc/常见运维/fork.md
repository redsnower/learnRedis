1.同步操作  
2.与内存量息息相关 ： 内存越大 耗时越长
3.查看持久化时间  info：latest_fork_usec: 

改善fork   
控制redis最大可以用内存 maxmemory  
合理配置Linux内存分配策略：  
vm.overcommit_memory =1  
降低fork频率 ：列如放宽AOF重写自动触发时机  



  
子进程开销和优化  
1.cpu 开销  
 
rdb 和AOF 都会对cpu的使用率大量提高  
不做cpu绑定 不和cpu密集型部署  
取消cpu的过度竞争  
  
内存  
开销：fork 内存开销， copy-on-write  
 
AOF 追加阻塞    
保 证追加成功时 如果选择的策略时everysec 每秒同步到 硬盘上去 
主线程会对比上次同步到磁盘的时间 相比大于2秒时 则阻塞  

AOF追加阻塞时   
看日志中可以看出



 
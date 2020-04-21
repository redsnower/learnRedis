  
比对：

1.优先级  如果 RDB和AOF都存在  恢复时 采取 AOF启动  
2.体积 RDB（快照）小  AOF 大  
3.恢复速度 RDB 快 AOF慢  
4.RDB丢失数据 AOF 根据策略  
5. 操作 RDB 是个重操作  AOF是轻操作  

  
RDB 最佳策略  关掉RDB的配置文件  
集中管理  
  
主从时    从开  控制生成的力度   

  

AOF 最佳策略：开  
AOF 重写集中管理  
大量fork（）时  


















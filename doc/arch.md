整个设计分成两部分


资源模型和执行模型、


隔离设计


熔断降级

1. 一定失败率
2. 平均响应时间


实时指标统计设计


// 整个处理过程是责任链设计


clusternode用于构建源节点信息

# 限流
qps流量控制
粗暴：直接拒绝

瞬压：冷启动（这种场景处于什么）

匀速： 小峰填谷


# 集群流控
client-server模式来解决

# 熔断降级
平均响应时间，异常数，异常比例

# 支持热点参数降级

# 支持系统自适应
https://en.wikipedia.org/wiki/TCP_congestion_control#TCP_BBR


# 黑白名单
属于auth


知识点：
https://github.com/alibaba/Sentinel/wiki/%E5%A6%82%E4%BD%95%E4%BD%BF%E7%94%A8#%E4%B8%8A%E4%B8%8B%E6%96%87%E5%B7%A5%E5%85%B7%E7%B1%BB-contextutil
可以通过注解来统一处理异常，降级


# 思考点

1. 一切都是资源，然后配置规则，进行动态加载
营销后台也是这样，
规则不进行持久化，放在内存中可以，
可以扩张datasource
https://github.com/alibaba/Sentinel/wiki/%E5%8A%A8%E6%80%81%E8%A7%84%E5%88%99%E6%89%A9%E5%B1%95

https://github.com/alibaba/Sentinel/issues/59



营销后台
1. 构建上下文
2. 检查活动层面的规则（这个应该是可以抽奖出来的，不限于抽奖）
3. 检查奖品层面的规则
4. 选择奖品
5. 异步发放奖品。


校验奖品的发送


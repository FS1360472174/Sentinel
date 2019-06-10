- http://localhost:8719/tree?type=root

tomcat请求后，发起一次request,然后在SimpleHttpCommandCenter启动8719端口,注册接口
CommonFilter.doFilter -> ContextUtil/initDefaultContest -> InitExecutor.doInit()


然后再请求http://localhost:8719/tree?type=root

`HttpEventTask.run`来处理对应的command

- 解析命令

- 根据命令获取不同的handler

- 调用handle方法




问题:
CommonFilter需要请求一次才能开启8379端口是什么鬼
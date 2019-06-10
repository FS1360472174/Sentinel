一. Entry 资源的最小单元，分为（EntryType) 进来和出去的

这部分是不是类似于分布式链路的Span呢

```
  // 用于RT的统计
  private long createTime;
    private Node curNode;
    /**
     * {@link Node} of the specific origin, Usually the origin is the Service Consumer.
     */
    private Node originNode;
    private Throwable error;
    // 资源
    protected ResourceWrapper resourceWrapper;
```
ResourceWrapper 资源,包括名字和Entry类型。有StringResourceWrapper，和MethodResourceWrapper

```
 protected String name;
    protected EntryType type = EntryType.OUT;
```

ct(current context)

```
class CtEntry extends Entry {

    protected Entry parent = null;
    protected Entry child = null;

    protected ProcessorSlot<Object> chain;
    protected Context context;
```

DefaultNode与EntryNode有啥区别呢

// 构建一个上下文
ContextUtil.enter(contextName);


NodeSelectorSlot 建立不同资源间的调用的关系，并且通过 ClusterNodeBuilderSlot 记录每个资源的实时统计信息。

调用方和调用链路的区别
https://github.com/alibaba/Sentinel/wiki/%E6%B5%81%E9%87%8F%E6%8E%A7%E5%88%B6


设计的不好的地方，很多的地方定义String类型，然后不好区分是context,还是resource


很多的限流都是基于资源的ResourceWrapper，
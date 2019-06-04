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

// 构建一个上下文
ContextUtil.enter(contextName);


SPH (Smoothed Particle Hydrodynamics)是平滑粒子流体动力学方法是缩写
Sph 创建Entry的方法

SphU 与SphO的区别

SphO会catch，返回true/false
```
 public static boolean entry(String name, EntryType type, int count, Object... args) {
        try {
            Env.sph.entry(name, type, count, args);
        } catch (BlockException e) {
            // 系统降级了blocked by Sentinel due to flow control, degraded or system guard
            return false;
        } catch (Throwable e) {
           // 这地方为什么catch Throwable，还返回true呢
            RecordLog.info("[Sentinel] Fatal error", e);
            return true;
        }
        return true;
    }
```

Throwable是由ProcessorSlot扔出来的

```
 void entry(Context context, ResourceWrapper resourceWrapper, T param, int count, boolean prioritized,
               Object... args) throws Throwable;

```
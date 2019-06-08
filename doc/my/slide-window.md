滑动窗口算法很简单，就是找到
连续的数组max(sum)的sub array

https://www.geeksforgeeks.org/window-sliding-technique/

https://www.jianshu.com/p/466feae35921

1. 什么是滑动窗口算法
就是找到连续数组的最大的数组子集

2. 要解决什么样的问题
以固定频率的采集数据，然后统计1min/5min等比率指标

量统计指标

3.

```
public abstract class LeapArray<T> {

    protected int windowLengthInMs;
    protected int sampleCount;
    protected int intervalInMs;
    // 存储的数据
    protected final AtomicReferenceArray<WindowWrap<T>> array;
```


MetricBucket 作为统计的基础数据

问题：
这个为什么代表success
LongAdder[] 是数组，然后统计的指标项枚举，作为数据的index，进行统计计数
public long pass() {
        return get(MetricEvent.PASS);
    }
    
```
public class MetricsLeapArray extends LeapArray<MetricBucket> 
```
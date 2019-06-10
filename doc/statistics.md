 * <li>{@link ClusterNode}: total statistics of a cluster node of the resource ID.</li>
 * <li>Origin node: statistics of a cluster node from different callers/origins.</li>
 * <li>{@link DefaultNode}: statistics for specific resource name in the specific context.</li>
 * <li>Finally, the sum statistics of all entrances.</li>
 
 为什么有这么多的统计数据
 
 
 PH (Smoothed Particle Hydrodynamics)是平滑粒子流体动力学方法是缩写
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
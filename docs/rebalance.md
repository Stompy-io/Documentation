## 再平衡

集群在经过多次自动扩缩容以后常常会留下过于碎片化的部署方案。当集群里实例的cpu和memory资源不能被有效
利用的时候，我们便可以通过再平衡产品，对当前集群的整体资源需求进行分析，优化当前集群大小和实例类型，来实
现节省。

### 准备工作

如想要最大化利用再平衡方案实现节省， 集群需要满足以下几个要求：

    * pod 模版明确标出所需资源，如 cpu： 500m， memory：200mi。
    * 减少自定义node selector/node affinity。 我们支持自动识别部分[well known labels](https://kubernetes.io/zh/docs/reference/labels-annotations-taints/)， 
        但是过多的node selector 条件会影响再平衡优化的空间
    * 再平衡适用场景为中等大小及以上集群。当集群数量较小以及使用了t系列实例，再平衡方案给您带来的优化将非常有限

### 创建再平衡方案

在集群连接页面点击'创建再平衡方案' 进入创建页面。

![img](/_images/rebalance/rebalance-01.png)

在这个页面您将看到可以被再平衡的workloads， 如果workloads被标记为未就绪， 请清理自定义node selector/node affinity设置

所有包含未就绪workloads的node将无法被替换，会出现在优化后的集群配置。

我们会分析已就绪的workloads，通过我们算法分析出最优分配方案。

![img](/_images/rebalance/rebalance-02.png)

用户可以选择三种不同方案配置来生成不同方案：
  
  1. 再平衡： 仅通过重新分配workloads来优化集群
  2. Spot友好： 在再平衡方案基础上，将部分replica set workloads 部署至spot实例
  3. 仅Spot：在再平衡方案基础上，全部使用spot实例


### 执行再平衡方案

在选中您想要执行的再平衡方案之后，您可以选择重新创建来执行更新。执行再平衡方案过程中会短暂造成服务不可用，
建议您在系统维护时间在进行操作。

再平衡方案执行完后，您将会看到方案状态转换为Active



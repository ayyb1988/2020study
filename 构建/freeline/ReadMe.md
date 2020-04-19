[使用篇--Freeline 是什么? ](https://www.freelinebuild.com/docs/zh_cn/###)
```
一个基于动态替换的编译方案
稳定性方面：完善的基线对齐，进程级别异常隔离机制。性能方面：内部采用了类似Facebook的开源工具buck的多工程多任务并发思想：端口扫描，代码扫描，并发编译，并发dx，并发merge dex等策略，在多核机器上有明显加速效果，另外在class及dex,resources层面作了相应缓存策略，做到真正增量开发，另外引入并优化buck的部分加速组件dx，DexMerger，资源编译方面，深入改造了Aapt资源编译流程，当资源发生改变时候，秒级完成增量包编译，其中增量包仅含最小的变更集合（10Kb～数百Kb内），后期也被运用到线上进行资源/代码动态替换。相比目前instant-run，buck，layoutcast等方案快数倍速度
```
![传统的打包流程](http://img3.tbcdn.cn/L1/461/1/4c1a0d0bbf2efd47af05db3f26d20044624891a0.png)



[原理篇--Freeline - Android平台上的秒级编译方案](https://yq.aliyun.com/articles/59122)
[Android秒级编译工具Freeline新特性支持！](https://yq.aliyun.com/articles/62334)
```
在解析Freeline如何支持Gradle工程的增量编译前，先来回顾一下Freeline的原理。Freeline本质上是一个热补丁方案，将修过过的*.java和资源文件分别打成dex和pack，然后通过socket传输到手机上，在运行期动态加载生效。具体可以阅读Freeline - Android平台上的秒级编译方案。

类似的热补丁方案的开源实现有Nuwa，以及未开源的QQ空间的超级补丁包。蚂蚁聚宝在线上也采用类似的方案来实现热补丁，以及A/B test。
```
[实践篇--聚美快速编译之FreeLine 安装指南](http://www.jianshu.com/p/3e375d3d5401)

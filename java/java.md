java值传递和引用传递
String为什么是值传递而不是引用传递 String是final的

## 异常
同大多数学科一样，学习编程艺术首先要学会基本的规则，然后才能知道什么时候可以打破这些规则


如何编写出清晰、正确、可用、健壮、灵活和可维护的程序

三种可抛出结构（throwable）:受检的异常（checed exception）、运行时异常（run-time exception）和错误（error）。


专家级程序员与缺乏经验的程序员一个重要的区别在于，专家追求并通常也能够实现高度的代码重用。
重用现有的异常有多方面的好处
1. 使你的API更加易于学习和使用
2. 可读性更好

最常见的可重用异常
1. IllgalArgumentException              非NULL的参数值不正确
2. IllgalStateException              对于方法的调用而言，对象状态不合适
3. NullPointerException              在禁止使用Null的情况下参数值为null
4. IndexOutofBoundsException             下标参数值越界
5. ConcurrentModificationException       在禁止并发修改的情况下，监测到对象的并发修改
6. UnsupportOperationException           对象不支持用户请求的方法
7. NumberFormatException                 算术格式转换异常

其他
ClassCastException
IOException

如果失败的情形不容易重现，要想获得更多的信息会非常困难，甚至是不可能的。因此，异常类型的toString方法应该尽可能的多返回有关失败的信息。为了确保在异常的细节消息中包含足够的能捕获失败的信息，一种办法是在异常的构造器而不是字符串细节消息种引入这些信息。super（message）

产生的任何异常都应该让对象保持在该方法调用之前的状态。具有这种属性的方法被称为具有失败原子性（failure atomic）
有几种途径
1. 设计一个不可变对象
2. 对于可变对象，最常见的方法是，在执行操作之前检查参数的有效性，在对象的状态被修改之前，先抛出合适的异常（调整计算处理的顺序，使得任何可能会失败的计算部分都在对象状态被修改之前发生）
3. 编写恢复代码（很少用）
4. 在对象的一份临时拷贝上在执行操作，当操作完成之后再用临时拷贝中的结果替代对象的内容。

不要忽略异常
```
try{
    
}catch(SomeExcetpion e){
    //什么也不做
}
```
忽略异常就如同忽略火警信号一样————当真正的火灾发生时，就没人能看到火警信号了。

## 并发






##### 1. 依赖、关联、聚合和组合之间区别

[设计模式中类的关系](http://blog.csdn.net/zhengzhb/article/details/7187278)
```
1. 依赖（Dependence）￼![](http://hi.csdn.net/attachment/201201/9/0_13260908301gJS.gif) 类A当中使用了类B，其中类B是作为类A的方法参数、方法中的局部变量、或者静态方法调用
2. 关联（Association）￼![](http://hi.csdn.net/attachment/201201/9/0_13260909884nw0.gif) 单向关联表现为：类A当中使用了类B，其中类B是作为类A的成员变量。双向关联表现为：类A当中使用了类B作为成员变量；同时类B中也使用了类A作为成员变量
3. 聚合（Aggregation）￼￼![](http://hi.csdn.net/attachment/201201/9/0_132609129950Sp.gif) 而聚合关系的对象之间存在着包容关系，他们之间是“整体-个体”的相互关系
4. 组合（Composition）￼![](http://hi.csdn.net/attachment/201201/9/0_1326091487YvWr.gif) 他们之间是共生共死的；并且“部分”单独存在时没有任何意义
5. 继承（Generalization）￼￼![](http://hi.csdn.net/attachment/201201/9/0_1326091748FS48.gif)
6. 实现（Implementation）￼![](http://hi.csdn.net/attachment/201201/9/0_1326091794M0ju.gif)
聚合是一种“整体-部分”的关系，组合也是一种“整体-部分”的关系，区别在于聚合中的整体和部分有着独立的生命周期，而组合中的整体和部分的是生命周期应该时一样的，java中实现貌似无法有体现这一点，而C++中能够体现
其实很多书中，面向对象的关系不是六种，而是4种：依赖、关联、继承、实现。聚合和组合是比较特殊的关联关系。分为六种的其实就是把关联根据耦合度从小到大又分为了关联、聚合、组合。
```

[组合 聚合 依赖 关联](http://www.cnblogs.com/Yogurshine/p/3634646.html)
![](http://images.cnitblog.com/i/483061/201403/302134509224843.jpg)

```
类之间的关系种类：Realization(实现)， Generalization(泛化)，Dependency(依赖)、Association(关联)、Aggregation(聚合)、Composition(合成或组合)。 其中，Aggregation(聚合)、Composition(合成)属于Association(关联)，是特殊的Association关联关系。

```

##### 2017-02-19 敏感字过滤
[Java实现敏感词过滤](http://blog.csdn.net/chenssy/article/details/26961957?spm=5176.8246799.blogcont.3.OOnhU6)

DFA算法
 
##### 2017-02-28 注解
[深入理解Java：注解（Annotation）基本概念](http://www.cnblogs.com/peida/archive/2013/04/23/3036035.html)
![](http://images.cnitblog.com/blog/34483/201304/25200814-475cf2f3a8d24e0bb3b4c442a4b44734.jpg)
[ Java注解（2）-运行时框架](http://blog.csdn.net/duo2005duo/article/details/50511476)
[Java中的注解是如何工作的？](http://www.importnew.com/10294.html)

##### 2017-03-01 面向切面编程 AOP 
###### 1. 基本概念以及相关基础知识
```
百科：AOP为Aspect Oriented Programming的缩写，意为：面向切面编程，通过预编译方式和运行期动态代理实现程序功能的统一维护的一种技术。AOP是OOP的延续，是软件开发中的一个热点，也是Spring框架中的一个重要内容，是函数式编程的一种衍生范型。利用AOP可以对业务逻辑的各个部分进行隔离，从而使得业务逻辑各部分之间的耦合度降低，提高程序的可重用性，同时提高了开发的效率。
```
```
在Spring中提供了面向切面编程的丰富支持，允许通过分离应用的业务逻辑与系统级服务（例如审计（auditing）和事务（transaction）管理）进行内聚性的开发。应用对象只实现它们应该做的——完成业务逻辑——仅此而已。它们并不负责（甚至是意识）其它的系统级关注点，例如日志或事务支持。
```
```
将日志记录，性能统计，安全控制，事务处理，异常处理等代码从业务逻辑代码中划分出来，通过对这些行为的分离，我们希望可以将它们独立到非指导业务逻辑的方法中，进而改变这些行为的时候不影响业务逻辑的代码。
```
[理解AOP](http://www.cnblogs.com/yanbincn/archive/2012/06/01/2530377.html)

###### 2. AOP的使用
###### 3. 运用AOP设计APM系统。
痛点：统计的代码植入性，耦合性太强。
网易的AOP架构

##### 2017-03-06 反射
[Java反射机制详解](http://www.cnblogs.com/lzq198754/p/5780331.html)
```
1反射机制是什么
2反射机制能做什么
3反射机制的相关API
·通过一个对象获得完整的包名和类名
·实例化Class类对象
·获取一个对象的父类与实现的接口
·获取某个类中的全部构造函数 - 详见下例
·通过反射机制实例化一个类的对象
·获取某个类的全部属性
·获取某个类的全部方法
·通过反射机制调用某个类的方法
·通过反射机制操作某个类的属性
·反射机制的动态代理
4反射机制的应用实例
·在泛型为Integer的ArrayList中存放一个String类型的对象。
·通过反射取得并修改数组的信息
·通过反射机制修改数组的大小
·将反射机制应用于工厂模式

1反射机制是什么

反射机制是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意一个方法和属性；这种动态获取的信息以及动态调用对象的方法的功能称为java语言的反射机制。

2反射机制能做什么

反射机制主要提供了以下功能： 

在运行时判断任意一个对象所属的类；

在运行时构造任意一个类的对象；

在运行时判断任意一个类所具有的成员变量和方法；

在运行时调用任意一个对象的方法；

生成动态代理。
```

[ 浅析Java中的反射机制原理](http://blog.csdn.net/xiaoxian8023/article/details/9154227)
![](http://img.blog.csdn.net/20130625103818562?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQveGlhb3hpYW44MDIz/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)


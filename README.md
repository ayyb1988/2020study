归零，重新出发
====

### 2017-02-04  抽象的原则

##### 1. [Java线程工作内存与主内存变量交换过程及volatile关键字理解](http://www.cnblogs.com/wrencai/p/5704331.html)

```
Java内存模型规定在多线程情况下，线程操作主内存变量，需要通过线程独有的工作内存拷贝主内存变量副本来进行
```
![](http://images2015.cnblogs.com/blog/641003/201607/641003-20160725171247106-495320616.png)

```
volatile : 　　线程中每次use变量时，都需要连续执行read->load->use几项操作，即所谓的每次使用都要从主内存更新变量值，这样其它线程的修改对该线程就是可见的。

　　线程每次assign变量时，都需要连续执行assign->store->write几项操作，即所谓每次更新完后都会回写到主内存，这样使得其它线程读到的都是最新数据
```

##### 2. [代码的抽象三原则](http://www.ruanyifeng.com/blog/2013/01/abstraction_principles.html)

```
*. DRY  不要重复自己
*. YAGNI 你不会需要它
*. Rule of Three 三次原则 ：指的是当某个功能第三次出现时，才进行"抽象化"。
```

##### 3. [面向对象—抽象原则](http://blog.csdn.net/luoxinwu123/article/details/8446094)

```
1. 面向对象分析与设计的主要任务是，找出类和对象，构建对象模型。

2. 抽象的两个原则：

最少承诺原则：对象的接口只提供它的基本行为。

最少惊奇原则：抽象捕捉了某个对象的全部行为，不多也不少，并且不提供抽象之外的惊奇效果和副作用。


3. 评判抽象的品质：

耦合：模块之间的关联强度应该是比较弱的，即低耦合。

内聚：模块内的各个元素的联系时紧密的，即高内聚。

充分性：类或模块应该记录某个抽象足够多的特征，从而允许有意义的、有效的交互。

完整性：类和模块的接口记录了它的全部特征。

基础性：只有访问该抽象的底层表现形式才能够有效的实现那些操作。
```
### 2017-02-06 面向接口编程

##### 1.[一篇非常经典的文章（面向接口编程） ](http://blog.chinaunix.net/uid-20478213-id-1942005.html)

```
设计模式解析里提到了面向对象设计考虑的几个视角，一个是概念层，一个是规约层，一个是实现层

在一个面向对象的系统中，系统的各种功能是由许许多多的不同对象协作完成的。在这种情况下，各个对象内部是如何实现自己的对系统设计人员来讲就不那么重要了；而各个对象之间的协作关系则成为系统设计的关键。小到不同类之间的通信，大到各模块之间的交互，在系统设计之初都是要着重考虑的，这也是系统设计的主要工作内容

接口从更深层次的理解，应是定义（规范，约束）与实现（名实分离的原则）的分离 .接口应有两类抽象体(abstract class)&抽象面（interface）

```

```
Java接口特性
1. 接口中的方法可以有参数列表和返回类型，但不能有任何方法体。
2. 接口中可以包含字段，但是会被隐式的声明为static和final。
3. 接口中的字段只是被存储在该接口的静态存储区域内，而不属于该接口。
4. 接口中的方法可以被声明为public或不声明，但结果都会按照public类型处理。
5. 当实现一个接口时，需要将被定义的方法声明为public类型的，否则为默认访问类型，Java编译器不允许这种情况。
6. 如果没有实现接口中所有方法，那么创建的仍然是一个接口。
7. 扩展一个接口来生成新的接口应使用关键字extends，实现一个接口使用implements。
```

##### 2.[面向接口编程的好处分析](http://blog.csdn.net/qq376430645/article/details/9927225)

```
面向接口编程
高内聚低耦合
设计模式之开闭原则

一个接口可以从三方面去考察： 
制定者（或者叫协调者），实现者（或者叫生产者），调用者（或者叫消费者）。 
接口本质上就是由制定者来协调实现者和调用者之间的关系。 
所以通常说的“面向接口编程”可以理解为：只有实现者和调用者都遵循“面向接口编程”这个准则，制定者的协调目的才能达到。 
```

```
开闭原则无非就是想表达这样一层意思：用抽象构建框架，用实现扩展细节。因为抽象灵活性好，适应性广，只要抽象的合理，可以基本保持软件架构的稳定。而软件中易变的细节，我们用从抽象派生的实现类来进行扩展，当软件需要发生变化时，我们只需要根据需求重新派生一个实现类来扩展就可以了
单一职责原则告诉我们实现类要职责单一；里氏替换原则告诉我们不要破坏继承体系；依赖倒置原则告诉我们要面向接口编程；接口隔离原则告诉我们在设计接口的时候要精简单一；迪米特法则告诉我们要降低耦合。而开闭原则是总纲，他告诉我们要对扩展开放，对修改关闭。

采用基于接口编程的项目，业务逻辑清晰，代码易懂，方便扩展，可维护性强。即使更换一批人员，新来的人依然可以快速上手。对于公司来说，意义更大.

在面对对象的程序中，灵活的使用接口也是一门艺术
```

### 2017-02-07 设计模式--六大原则 【每天一个]

##### 0. [设计模式——六大原则](http://m.blog.csdn.net/article/details?id=48598607)

##### 1. [ 设计模式六大原则（1）：单一职责原则](http://blog.csdn.net/zhengzhb/article/details/7278174)

```
虽然单一职责原则如此简单，并且被认为是常识，但是即便是经验丰富的程序员写出的程序，也会有违背这一原则的代码存在。为什么会出现这种现象呢？因为有`职责扩散`。所谓职责扩散，就是因为某种原因，职责P被分化为粒度更细的职责P1和P2
比如：类T只负责一个职责P，这样设计是符合单一职责原则的。后来由于某种原因，也许是需求变更了，也许是程序的设计者境界提高了，需要将职责P细分为粒度更细的职责P1，P2，这时如果要使程序遵循单一职责原则，需要将类T也分解为两个类T1和T2，分别负责P1、P2两个职责。但是在程序已经写好的情况下，这样做简直太费时间了。所以，简单的修改类T，用它来负责两个职责是一个比较不错的选择，虽然这样做有悖于单一职责原则。（这样做的风险在于职责扩散的不确定性，因为我们不会想到这个职责P，在未来可能会扩散为P1，P2，P3，P4……Pn。所以记住，在职责扩散到我们无法控制的程度之前，立刻对代码进行重构。）
```

```
遵循单一职责原的优点有：
可以降低类的复杂度，一个类只负责一项职责，其逻辑肯定要比负责多项职责简单的多；
提高类的可读性，提高系统的可维护性；
变更引起的风险降低，变更是必然的，如果单一职责原则遵守的好，当修改一个功能时，可以显著降低对其他功能的影响。
```

##### 2.里氏替换原则
Liskov Substitution Principle 简称为：LSP
####### 1. [设计模式六大原则（2）：里氏替换原则](http://blog.csdn.net/zhengzhb/article/details/7281833)
```
名字的由来：`这项原则最早是在1988年，由麻省理工学院的一位姓里的女士（Barbara Liskov）提出来的。`
```
```
里氏替换原则通俗的来讲就是：`子类可以扩展父类的功能，但不能改变父类原有的功能`。它包含以下4层含义：
*. 子类可以实现父类的抽象方法，但不能覆盖父类的非抽象方法。
*. 子类中可以增加自己特有的方法。
*. 当子类的方法重载父类的方法时，方法的前置条件（即方法的形参）要比父类方法的输入参数更宽松。
*. 当子类的方法实现父类的抽象方法时，方法的后置条件（即方法的返回值）要比父类更严格。
```

####### 2. [里氏替换原则](http://www.cnblogs.com/sunwei2012/archive/2010/03/10/1682415.html)
```
  在面向对象的语言中，继承是必不可少的、非常优秀的语言机制，它有如下优点：

代码共享，减少创建类的工作量，每个子类都拥有父类的方法和属性；
提高代码的重用性；
子类可以形似父类，但又异于父类，“龙生龙，凤生凤，老鼠生来会打洞”是说子拥有父的“种”，“世界上没有两片完全相同的叶子”是指明子与父的不同；
提高代码的可扩展性，实现父类的方法就可以“为所欲为”了，君不见很多开源框架的扩展接口都是通过继承父类来完成的；
提高产品或项目的开放性。
     自然界的所有事物都是优点和缺点并存的，即使是鸡蛋，有时候也能挑出骨头来，继承的缺点如下：

继承是侵入性的。只要继承，就必须拥有父类的所有属性和方法；
降低代码的灵活性。子类必须拥有父类的属性和方法，让子类自由的世界中多了些约束；
增强了耦合性。当父类的常量、变量和方法被修改时，必需要考虑子类的修改，而且在缺乏规范的环境下，这种修改可能带来非常糟糕的结果——大片的代码需要重构。
```

```
 所有引用基类的地方必须能透明地使用其子类的对象。并且不会出错
```

```
最佳实践

      在项目中，采用里氏替换原则时，尽量避免子类的“个性”，一旦子类有“个性”，这个子类和父类之间的关系就很难调和了，把子类当做父类使用，子类的“个性”被抹杀——委屈了点；把子类单独作为一个业务来使用，则会让代码间的耦合关系变得扑朔迷离——缺乏类替换的标准。所以说最好的方式是 采用抽象类或者interface作为base。子类和调用者通过父类来协作
```

```
我们在做系统设计时，经常会定义一个接口或抽象类，然后编码实现，调用类则直接传入接口或抽象类，其实这里已经使用了里氏替换原则
注意 在类中调用其他类时务必要使用父类或接口，如果不能使用父类或接口，则说明类的设计已经违背了LSP原则。

如果子类不能完整地实现父类的方法，或者父类的某些方法在子类中已经发生“畸变”，则建议断开父子继承关系，采用`依赖`、`聚集`、`组合`等关系代替继承.  `关联委托关系`
```

####### 3. [里氏替换原则](http://blog.csdn.net/Bitou_Von/article/details/4210654)
```
里氏代换原则`目的`就是要`保证继承关系的正确性`


作为一个设计原则，是人们经过很多的项目实践，最终提炼出来的指导性的内容。如果对于你的项目来讲，显著增加了工作量和复杂度，那我觉得适度的违反并不为过。做任何事情都是个度的问题，过犹不及都不好。在大中型的项目中，是一定要讲究软件工程的思想，讲究规范和流程的，否则人员协作和后期维护将会是非常困难的。对于小型的项目可能相应的要简化很多，可能取决于时间、资源、商业等各种因素，但是多从软件工程的角度去思考问题，对于系统的健壮性、可维护性等性能指标的提高是非常有益的。像生命周期只有一个月的系统，你还去考虑一大堆原则，除非脑袋被驴踢了。

实现开闭原则的关键步骤是抽象化，基类与子类之间的继承关系就是一种抽象化的体现。因此，里氏代换原则是实现抽象化的一种规范。违反里氏代换原则意味着违反了开闭原则，反之未必。里氏代换原则是使代码符合开闭原则的一个重要保证。
```

##### 3. 依赖倒置原则
[设计模式六大原则（3）：依赖倒置原则](http://blog.csdn.net/zhengzhb/article/details/7289269)

```
定义：高层模块不应该依赖低层模块，二者都应该依赖其抽象；抽象不应该依赖细节；细节应该依赖抽象。
问题由来：类A直接依赖类B，假如要将类A改为依赖类C，则必须通过修改类A的代码来达成。这种场景下，类A一般是高层模块，负责复杂的业务逻辑；类B和类C是低层模块，负责基本的原子操作；假如修改类A，会给程序带来不必要的风险。
解决方案：将类A修改为依赖接口I，类B和类C各自实现接口I，类A通过接口I间接与类B或者类C发生联系，则会大大降低修改类A的几率。
依赖倒置原则基于这样一个事实：相对于细节的多变性，抽象的东西要稳定的多。以抽象为基础搭建起来的架构比以细节为基础搭建起来的架构要稳定的多。在Java中，抽象指的是接口或者抽象类，细节就是具体的实现类，使用接口或者抽象类的目的是制定好规范和契约，而不去涉及任何具体的操作，把展现细节的任务交给他们的实现类去完成。
`依赖倒置原则的核心思想是面向接口编程`

传递依赖关系有三种方式，以上的例子中使用的方法是接口传递，另外还有两种传递方式：`构造方法传递`和`setter方法传递`，相信用过Spring框架的，对依赖的传递方式一定不会陌生。
在实际编程中，我们一般需要做到如下3点：
1. 低层模块尽量都要有抽象类或接口，或者两者都有。
2. 变量的声明类型尽量是抽象类或接口。
3. 使用继承时遵循里氏替换原则。
`依赖倒置原则的核心就是要我们面向接口编程，理解了面向接口编程，也就理解了依赖倒置。`
```


```
楼主的经典语录“总结着总结着就是高手了，看着看着就是菜鸟了”。真所谓学而不思则惘。

通过对频繁变化的原子细节做适当抽象，能降低修改核心业务逻辑的频率。
　　这点在我们实际编码中也深有体会，核心逻辑一旦发生BUG，影响将是比较全面的，可能整个功能就废了；而局部细节出问题，只会影响一个用例分支。
　　有人提到如何发现这种抽象，我想说这依赖于实践积累和重构。一开始的代码肯定只是一种尝试性的架构，经过反复的需求变更、添加个性化功能，我们就会发现某几个点经常变化，然后开始考虑抽象出接口，并将其配置化。然后很多个性化的工作突然就变成日常工作了，相关编码规范也随之出现，程序猿又不用为这些琐事加班了（不过他们会为其他琐事继续加班）。
  
对抽象的实现都封装在Client里，还是需要修改代码并重新编译来使程序按预期运行。如果利用`控制反转容器`将对抽象的实现放入配置文件里， 并修改Client中的代码。扩展性将是多么的好。还不需要重新编译

`抽象是稳定的，而细节是多变的`，这条原则实际上是让我们`多用抽象类或接口来做整体架构`，而`抽象的前提`就是`我们在架构之前就对系统的需求变更有一定的预见性和前瞻性`。像你说的这种情况，如果在设计抽象的时候就考虑到一些可能的变更，等变更出现的时候，就可以比较方便地处理这些变更了
```


##### 4. 接口隔离原则

[设计模式六大原则（4）：接口隔离原则](http://blog.csdn.net/zhengzhb/article/details/7296921)

```
定义：客户端不应该依赖它不需要的接口；一个类对另一个类的依赖应该建立在最小的接口上。
问题由来：类A通过接口I依赖类B，类C通过接口I依赖类D，如果接口I对于类A和类B来说不是最小接口，则类B和类D必须去实现他们不需要的方法。
解决方案：将臃肿的接口I拆分为独立的几个接口，类A和类C分别与他们需要的接口建立依赖关系。也就是采用接口隔离原则。

采用接口隔离原则对接口进行约束时，要注意以下几点：
接口尽量小，但是要有限度。对接口进行细化可以提高程序设计灵活性是不挣的事实，但是如果过小，则会造成接口数量过多，使设计复杂化。所以一定要适度。
为依赖接口的类定制服务，只暴露给调用的类它需要的方法，它不需要的方法则隐藏起来。只有专注地为一个模块提供定制服务，才能建立最小的依赖关系。
提高内聚，减少对外交互。使接口用最少的方法去完成最多的事情。
运用接口隔离原则，一定要适度，接口设计的过大或过小都不好。设计接口的时候，只有多花些时间去思考和筹划，才能准确地实践这一原则。
```

##### 5. 迪米特法则 又叫 最少知道原则

```
迪米特法则（Law of Demeter）又叫作最少知道原则（Least Knowledge Principle 简写LKP），就是说一个对象应当对其他对象有尽可能少的了解,不和陌生人说话。英文简写为: LoD.
```
```

定义：一个对象应该对其他对象保持最少的了解。
问题由来：类与类之间的关系越密切，耦合度越大，当一个类发生改变时，对另一个类的影响也越大。
解决方案：尽量降低类与类之间的耦合。
自从我们接触编程开始，就知道了软件编程的总的原则：低耦合，高内聚。无论是面向过程编程还是面向对象编程，只有使各个模块之间的耦合尽量的低，才能提高代码的复用率。低耦合的优点不言而喻，但是怎么样编程才能做到低耦合呢？那正是迪米特法则要去完成的。
`迪米特法则又叫最少知道原则`，最早是在1987年由美国Northeastern University的Ian Holland提出。`通俗的来讲，就是一个类对自己依赖的类知道的越少越好`。也就是说，对于被依赖的类来说，无论逻辑多么复杂，都尽量地的将逻辑封装在类的内部，对外除了提供的public方法，不对外泄漏任何信息。`迪米特法则还有一个更简单的定义：只与直接的朋友通信。`首先来解释一下什么是直接的朋友：每个对象都会与其他对象有耦合关系，只要两个对象之间有耦合关系，我们就说这两个对象之间是朋友关系。`耦合的方式很多，依赖、关联、组合、聚合等`。其中，我们称出现成员变量、方法参数、方法返回值中的类为直接的朋友，而出现在局部变量中的类则不是直接的朋友。也就是说，陌生的类最好不要作为局部变量的形式出现在类的内部。

其实`迪米特法则的目的就是让我们降低耦合`，朋友类的定义：出现成员变量、方法参数、方法返回值中的类。其实很好理解，假如一个类表现为成员变量、方法参数或者方法返回值，我们就可以利用接口或者父类等进行模块化编程（传参数、set设值、强制转换等等等），如果表现为局部变量，就算是写死在代码里了，一点变通的方式都没有了，这样的话，耦合度就很高呵
```

[设计模式六大原则（5）：迪米特法则](http://blog.csdn.net/zhengzhb/article/details/7296930)

##### 6. 开闭原则

[设计模式六大原则（6）：开闭原则](http://blog.csdn.net/zhengzhb/article/details/7296944)
![](http://hi.csdn.net/attachment/201202/27/0_1330303797fpLw.gif)
```
用抽象构建框架，用实现扩展细节

开闭的真正作用是在设计阶段，封装变化点，预留扩展。

```

### 2017-02-08  登录系统设计

##### 1. [设计一个可扩展的用户登录系统(1) ](http://www.liaoxuefeng.com/article/001437480923144e567335658cc4015b38a595bb006aa51000)

```
兼容：用户名+口令；第三方；短信 等登录方式
Profile和Authenticate分开，Users表本身只存储用户的Profile

即：
Users表只存储User的Profile信息，没有任何认证信息（例如，不存Password）；
每一种登录方式对应一个XxxAuth表，该表存储对应的认证信息，以及一个userId字段用于关联到某个User。
```

##### 2. [设计一个可扩展的用户登录系统 (2)](http://www.liaoxuefeng.com/article/001461119866914f84275c4a5034ffeb47405caa205e335000)

```
登录方式

1. 用户名＋口令登录
![](http://www.liaoxuefeng.com/files/attachments/001461114372512821fea031535429aa3a799728c751f06000/l)

2. 通过第三方网站登录
![](http://www.liaoxuefeng.com/files/attachments/0014611145999630c8b8e11cce44f2d9be6d4182312f640000/l) 

3. 通过HTTP Authorization Header登录
4. 通过X-API-Token登录

3和4 由代表用户的机器发起的请求

`复杂的问题都要分解成几步`
```

```
认证成功后的User对象放哪

```

```
最后总结一下我们编写认证逻辑的思路：

每一种认证方式都是一种Authenticator的实现；
把所有认证方式串起来，在一个统一的Filter入口来认证；
认证后的User对象用UserContext存储，并提供一个简单的方法返回当前User。
好处如下：

认证方式可简单扩展；
认证逻辑统一在一处。
还有一个最大的好处，就是业务相关的代码根本就不需要依赖底层HTTP对象，比如session和request，它们只依赖UserContext，这才是真正的解耦，并且非常容易测试业务逻辑，因为不再需要模拟session和request。
```

##### 3. [设计一个可扩展的用户登录系统 (3)](http://www.liaoxuefeng.com/article/00146129217054923f7784c57134669986a8875c10e135e000)

```
`如何生成一个可信的Cookie`

用户id:有效期:MD5 用户id+口令+有效期+固定随机数

使用用户id而不是用户明的原因：如果用户明是手机号或者邮箱等信息容易泄露用户信息
有效期的原因：cookie的有效期
MD5的原因：单项函数，放破解。但是`简单的md5值很容易被彩虹表攻击`，md5算法还可以换成更安全的sha1/sha256

```

```
`如何绑定用户`

正确做法：把User用ThreadLocal绑定到当前处理线程 spring中的处理
android中可以存在shareperefmance

```

### 2017-02-09  gradle构建系统

[Getting Started - Android - Gradle](https://gradle.org/docs#getting-started)
[gradle配置构建Android文档](https://developer.android.com/studio/build/index.html?hl=zh-cn)
[深入理解Android（一）：Gradle详解](http://www.infoq.com/cn/articles/android-in-depth-gradle)


### 2017-02-10 Android插件化 组件化

##### 1. [Android组件化和插件化开发](http://www.cnblogs.com/android-blogs/p/5703355.html)

理解插件化和组件化的区别
![](https://raw.githubusercontent.com/halibobo/BlogImage/master/blog/module/module_plug.png?_=5703355)

```
`组件化解决的问题`

每个模块可以独立开发编译运行。避免稍微改动一个模块的一点代码都要编译整个工程，耗时耗力。提高开发调试效率
开发单个模块时可以共享资源和工具类
可以针对单个模块测试 解耦


有了组件化，为什么还要用插件化呢？

`插件化解决的问题`

动态更新

```

##### 2. [Android 开发:由模块化到组件化(一)](http://blog.csdn.net/dd864140130/article/details/53645290)

`组件化过程中遇到的问题`

1. 组件划分  有团队架构人员和业务人员协商定制.
2. 子工程工作方式切换 通过gradle 根据debeg和release设置作为自工程还是作为lib使用，以及设置对应的AndroidManifest.xml
3. 组件通信与组件依赖
`解决组件通信`
![](http://img.blog.csdn.net/20161214232103384?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvZGQ4NjQxNDAxMzA=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

`解决重复依赖`
```
对于采用aar方式输出的Library而言,在构建项目时,gradle会为我们保留最新版本的aar,换言之,如果以aar的方式向主工程提供提供依赖不会存在重复依赖的问题.而如果是直接以project形式提供依赖,则在打包过程中会出现重复的代码.解决project重复依赖问题目前有两种做法:1.对于纯代码工程的库或jar包而言,只在最终项目中执行compile,其他情况采用provider方式;2.在编译时检测依赖的包,已经依赖的不再依赖
```

4. 资源id冲突
最简单的方式是通过实现约定资源前缀名(resourcePrefix)来避免,需要在组件的gradle脚本中配置:  resourcePrefix "moudle_prefix"

5. 组件上下文(Context)


##### 3. 组件之间的解耦和通信


[ios模块化与解耦](https://blog.cnbluebox.com/blog/2015/11/28/module-and-decoupling/)

```
common和模块： 公共模块下沉
模块与模块：
interface 作为一个独立的Module，Module A 调用Module B. Module B 实现interface，Module A通过interface调用。
Router

```

[Android 跨 module 交互和方法调用](https://gold.xitu.io/entry/5811c1b9a22b9d00639f5d8c)
```
1.上层module和下层module的交互

（1）如果module是上下层的关系（例如一个module 依赖一个base的module）那么上层的module是可以直接获取base module的接口，达到信息取得的。

（2）那么base module并不会依赖于上层的module的（这是设计的初衷），那么如何获取上层module的信息呢？这里其实就可以简单用到抽象接口的调用父类的实现了。

这一切都是源于module之间的依赖形态所可以达到的效果

这是我们只要module依赖都会遇到过的问题。

2.两个相同层的module通信

可以想象两个相同层的module如果相互之间并没有直接的依赖关系，我们是没法传输到数据的。

那么用EventBus事件总线呢？是否有人试过？

试验过都会被modules间的这道墙所隔离。（EventBus只能用在单module里通信）

可以想象使用boardcast ，这是安卓本身系统带有可以整个系统里告知信息，通过boardcast广播应该是可以做到的传输的，唯一不好的地方就是其效率不高（至少会比EventBus要低）

也会有人提到数据库？但是如果你一直在监听着某些数据的变化，也会产生有一定的消耗的。

那为何module间不直接相互依赖，这样不就可以解决问题呢？倘或一个module被多个module依赖，那些module都会调用这个module的方法，那么这样移除这个module将会是致命的，将需要增加以后维护的难度。我们设计的初衷是松耦合。

我们的同层的modules没法直接依赖，但是可以做到间接依赖的。

我们相同层的modules都依赖于一个base的module。

那么我们就可以做一个监听者模式的设计，每个module把想要传输的响应接口注册到base模块里面，然后相应的module调用想要传输到传输模块的接口，就可以完成信息的传输，跨模块接口的调用。

关于监听者模式，如果有深入了解过EventBus和boardcaset源码分析应该都明白这种设计模式的魅力。
```

##### 4.Trinea Android 插件化 动态升级 原理

[Android 插件化 动态升级](http://www.trinea.cn/android/android-plugin/)
```
插件化的原理实际是 Java ClassLoader 的原理，看其他资料前请先看：[ava ClassLoader基础 ](http://www.trinea.cn/android/java-loader-common-class/)
Android 也有自己的 ClassLoader，分为 dalvik.system.DexClassLoader 和 dalvik.system.PathClassLoader，区别在于 PathClassLoader 不能直接从 zip 包中得到 dex，因此只支持直接操作 dex 文件或者已经安装过的 apk（因为安装过的 apk 在 cache 中存在缓存的 dex 文件）。而 DexClassLoader 可以加载外部的 apk、jar 或 dex文件，并且会在指定的 outpath 路径存放其 dex 文件。
```

##### 5. 冯森林 组件化
[从零开始的Android新项目11 - 组件化实践（1）](http://blog.zhaiyifan.cn/2016/10/20/android-new-project-from-0-p11/)
```
组件化 VS 插件化
组件化带来的，是一个没有黑科技的插件化。应用了 Android 原有的技术栈以及 Gradle 的灵活性，失去的是动态发版本的能力，其他则做得比插件化更好。因为没有黑科技，所以不会有那么多黑科技和各种 hook 导致的坑，以及为了规避它们必须小心翼翼遵守的开发规范，几乎和没有使用插件化的 Android 开发一模一样。

而我们需要关心的，只是如何做好隔离，如何更好地设计，以及提高开发效率与产品体验。
```
```
`最佳实践`

每个 module 包名都应该使用 “$packageName.module.$business” 形式，资源使用业务名开头，比如 “feed_ic_like.png”。

另外，在组件化实践过程中可能碰到的就是依赖的问题了
```

[ComponentizationApp](https://github.com/liangzhitao/ComponentizationApp)


[From Containerization to Modularity](http://www.slideshare.net/oasisfeng/from-containerization-to-modularity)
```
Life is hard,don't waste you time.  Talk is cheap,show me the code!
```


### 2017-02-13 TDD开发模式

`目的： 高效的开发高品质的程序`
```
TDD开发，可能国内用的人比较少。但我认为，这种开发模式是很值得引入的。首先，它不用程序员反复启动服务，就可以找到自己程序的问题，这样会提高开发效率（一般启动服务是一个痛苦的过程）。其次，这种方法比较灵活，程序的执行方向可以不按现实逻辑进行，这样我们就可以检测一些手动不便测试到的内容。最后，实现方法多种多样，简便宜行
```

##### 1.[浅谈TDD、BDD与ATDD软件开发](http://blog.csdn.net/zhenyu5211314/article/details/22033295?utm_source=tuicool&utm_medium=referral)
##### 2.[极限编程之TDD](http://www.cnblogs.com/bile/p/4013703.html)
##### 3.[浅谈测试驱动开发（TDD）](http://www.ibm.com/developerworks/cn/linux/l-tdd/)

```
`开发者应该为用户挖掘隐含需求`

测试驱动开发最重要的功能还在于保障代码的正确性，能够迅速发现、定位bug,减少调试时间，提高效率

需求向来就是软件开发过程中感觉最不好明确描述、易变的东西。这里说的需求不只是指用户的需求，还包括对代码的使用需求。很多开发人员最害怕的就是后期还要修改某个类或者函数的接口进行修改或者扩展，为什么会发生这样的事情就是因为这部分代码的使用需求没有很好的描述。测试驱动开发就是通过编写测试用例，先考虑代码的使用需求（包括功能、过程、接口等）

![](http://www.ibm.com/developerworks/cn/linux/l-tdd/images/V.jpg)

看一个软件的设计主要看两个类：类图和时序图。类图确定了软件数据模型的静态关型，时序图则是数据模型的动态关系

时序图看做反映自己思路的大概过程，所以也就画个大概
时序图要简洁易懂，这样以后你的后继维护者，拿到这个软件的时序图（当然也包括用例图、类图），就能明白你的大概设计思路
时序图可以（１）整理思路（２）验证类的设计（３）是很好的软件文档，对维护者理解代码很有帮助

设计阶段-->TDD-->
```

```
测试驱动开发的基本过程如下：
1） 明确当前要完成的功能。可以记录成一个 TODO 列表。
2） 快速完成针对此功能的测试用例编写。
3） 测试代码编译不通过。
4） 编写对应的功能代码。
5） 测试通过。
6） 对代码进行重构，并保证测试通过。
7） 循环完成所有功能的开发。

```

```
原则
1. 测试隔离。不同代码的测试应该相互隔离。对一块代码的测试只考虑此代码的测试，不要考虑其实现细节（比如它使用了其他类的边界条件）。
1. 一顶帽子。开发人员开发过程中要做不同的工作，比如：编写测试代码、开发功能代码、对代码重构等。保证头上只有一顶帽子。避免考虑无关细节过多，无谓地增加复杂度。
1. 测试列表。需要测试的功能点很多。应该在任何阶段想添加功能需求问题时，把相关功能点加到测试列表中，然后继续手头工作
1. 测试驱动。这个比较核心。完成某个功能，某个类，首先编写测试代码，考虑其如何使用、如何测试。然后在对其进行设计、编码。
1. 先写断言。测试代码编写时，应该首先编写对功能代码的判断用的断言语句，然后编写相应的辅助语句。
1. 可测试性。功能代码设计、开发时应该具有较强的可测试性。其实遵循比较好的设计原则的代码都具备较好的测试性。比如比较高的内聚性，尽量依赖于接口等。
1. 及时重构。无论是功能代码还是测试代码，对结构不合理，重复的代码等情况，在测试通过后，及时进行重构。关于重构，我会另撰文详细分析。
1. 小步前进。
```

##### 4.[解读TDD的五大误区](http://www.scrumcn.com/agile/scrum/4423.html)

```
TDD（全称Test Driven Development）测试驱动开发，是一种软件开发的流程，其由敏捷的“极限编程”引入。其开发过程是从功能需求的测试用例开始，先添加一个测试用例，然后运行所有的测试用例看看有没有问题，再实现测试用例所要测试的功能，然后再运行测试用例，查看是否有case失败，然后重构代码，再重复以上步骤。

其理念主要是确保两件事：
确保所有的需求都能被照顾到。
在代码不断增加和重构的过程中，可以检查所有的功能是否正确。
```
##### 5.[推行TDD的思考](http://itindex.net/detail/47243-tdd-%E6%80%9D%E8%80%83)
```
由开发人员编写测试带来的收益，最重要的一点不在于测试本身，而在于它能促进开发、测试以及需求分析人员的交流与沟通

目前来看，推行TDD的障碍大约有如下几点：

1. 开发人员的质量意识；[软件的外部质量，体现在他们的工作效益上，就是被测试人员发现的缺陷数;软件质量除了外部质量之外，内部质量同等重要。软件成本等于开发成本与维护成本之和，而维护成本的增加主要就归咎于内部质量的糟糕。这里讲的内部质量包括：代码的可读性、可重用性、可扩展性等]

2. 分析需求并进行任务分解的能力；[需求分析能力常常是开发人员的短板.TDD要求我们在编写测试之前要做好合理的任务分解。若没有很好地理解需求，任务分解就无法顺利的进行。任务分解是有层次的。分析需求时，不能一个猛子就扎进繁琐的实现细节。要从用户价值出发，先梳理出最外层的需求任务，然后抽丝剥茧，条分缕析地层层递进，如此方能理清思路，掌控复杂逻辑。基本上，任务分解可以分为三个层次，即业务价值——>业务功能——>业务实现。并且这个层次是一种“递归”的状态，视需求的复杂度而定。]

3. 将测试作为开发起点的开发习惯；[设计并不仅包含技术层面的设计如对OO思想乃至设计模式的运用，它本身还包括对需求的分析与建模.在开始测试驱动开发之前，做适度的事先设计，还有利于我们仔细思考技术实现的解决方案]

4. 开发人员的重构能力，包括如何识别坏味道和如何运用重构手法；[TDD的核心是红——绿——重构。这意味着重构是TDD非常重要的一环，它直接关系到TDD开发出来的代码质量。没有好的重构能力，TDD就会有缺失.重构的关键首先在于如何识别代码的坏味道.在TDD过程中，若能结对自然是上佳选择.及时重构,小步前行]

5. 单元测试的基础设施，尤其是测试数据准备；[最好能找到一些开源的测试框架，包括生成测试数据，模拟测试行为等;君子生非异也，善假于物也]
```

##### 6.[在团队中进行单元测试/TDD的12条经验](http://itindex.net/detail/44837-%E5%9B%A2%E9%98%9F-%E5%8D%95%E5%85%83%E6%B5%8B%E8%AF%95-tdd)




[google gson 使用proguard混淆代码注意事项](http://blog.csdn.net/yuxiaohui78/article/details/46885337)


### 2017-02-14 控制反转容器 依赖注入
控制反转（Inversion of Control，英文缩写为IoC）
IoC 亦称为 “依赖倒置原理”("Dependency Inversion Principle")



1. Gson 用到Gson的场景，要把对应的实体类加入到不混淆文件中。

2. string.xml中 一些特殊的字符需要通过ASCII码进行转换，否则在国际化&界面换行排版上会有问题  [ android string.xml 添加特殊字符](http://blog.csdn.net/z1074971432/article/details/12753539)

3. 获取设备号的正确姿势：有些设备没有sim卡功能，无法获取imei号。但是业务上却需要使用到设备号(比如，根据设备号进行推送，pad等设备无imei号)，此时可以通过设备的wifi网络信息，通过mac地址作为设备号。
```java
public static String getIMEI(Context context) {
        String imei = "";
        try {
            TelephonyManager tm = (TelephonyManager) context
                    .getSystemService(Context.TELEPHONY_SERVICE);
            imei = tm.getDeviceId();
        } catch (Throwable e) {
            KGLog.printException("kugou", e);
        }
        // 平板imei为null
        if (TextUtils.isEmpty(imei)) {
            try {
                WifiManager wifi = (WifiManager) context.getSystemService(Context.WIFI_SERVICE);
                WifiInfo info = wifi.getConnectionInfo();
                if (info != null) {
                    imei = info.getMacAddress();
                }
                if (imei == null) {
                    imei = "";
                }
            } catch (Exception e) {
                KGLog.printException("kugou", e);
            }
        }
        if (imei == null) {
            imei = "";
        }
        return imei;
    }
```


### 2017-02-15 酷狗换肤
##### 一. [酷狗8.0换肤规则](http://10.16.1.16/Android/KugouSkin/wikis/home)
######1.1 使用说明
```
下面两套方案实现的效果不同

skinNormalColor = SkinResourcesUtils.getInstance().getColor(SkinColorType.BASIC_WIDGET)
mNormalColorFilter = SkinResourcesUtils.getInstance().color2ColorFilter(skinNormalColor);
drawable.mutate().setColorFilter(mNormalColorFilter);

或者
int skinNormalColor = SkinResourcesUtils.getInstance().getColor(SkinColorType.BASIC_WIDGET);
drawable.mutate().setColorFilter(skinNormalColor, PorterDuff.Mode.SRC_ATOP);

```
######1.2 关键类 com.kugou.common.skinpro×
SkinFactory
SkinEngine
AttrUtils
SkinResourcesUtils
SkinColorSrcAttr
SkinColorType

######1.3 实现框架
######1.4 代码分析
######1.5 相关技术


##### 二. 网络资源
[Android QQ技术分享三(QQ换肤之SkinEngine实现)  ](http://download.csdn.net/detail/cc_want/9187187#comment)
[Android 源码系列之<四>从源码的角度深入理解LayoutInflater.Factory之主题切换(上)(中)(下)](http://blog.csdn.net/llew2011/article/details/51252401)


### 2017-02-16 路由框架

[[Alibaba-ARouter] 简单好用的Android页面路由框架](http://www.jianshu.com/p/7cb2cc9b726a?from=groupmessage)
[alibaba/ARouter](https://github.com/alibaba/ARouter) [注解]

[AndRouter](https://github.com/campusappcn/AndRouter) [list]




### 2017-02-17 android运行时权限

android运行时权限实在androidM即6.0系统，targetsdk=23 哦，targetSdk有什么用呐 

##### targetSDK作用以及原理

[Android targetSdkVersion 原理](http://www.race604.com/android-targetsdkversion/)
```
targetSdkVersion is the main way Android provides forward compatibility
targetSdkVersion 是 Android 系统提供前向兼容的主要手段,随着 Android 系统的升级，某个系统的 API 或者模块的行为可能会发生改变，但是为了保证老 APK 的行为还是和以前兼容。只要 APK 的 targetSdkVersion 不变，即使这个 APK 安装在新 Android 系统上，其行为还是保持老的系统上的行为，这样就保证了系统对老应用的前向兼容性

修改 targetSdkVersion 需要做完整的测试。因为android针对不同的targetSDK有不同的处理方案。eg:从21升到23 就需要了解targetSDK发生了那些变化
```
[如何选择 compileSdkVersion, minSdkVersion 和 targetSdkVersion](http://chinagdg.org/2016/01/picking-your-compilesdkversion-minsdkversion-targetsdkversion/)

```
compileSdkVersion: 告诉 Gradle 用哪个 Android SDK 版本编译你的应用.修改 compileSdkVersion 不会改变运行时的行为。当你修改了 compileSdkVersion 的时候，可能会出现新的编译警告、编译错误，但新的 compileSdkVersion 不会被包含到 APK 中：它纯粹只是在编译的时候使用
minSdkVersion: 应用可以运行的最低要求
 targetSdkVersion: 三个版本号中最有趣的就是 targetSdkVersion 了。 targetSdkVersion 是 Android 提供向前兼容的主要依据，在应用的 targetSdkVersion 没有更新之前系统不会应用最新的行为变化。这允许你在适应新的行为变化之前就可以使用新的 API （因为你已经更新了 compileSdkVersion 不是吗？）。targetSdkVersion 所暗示的许多行为变化都记录在 [VERSION_CODES](https://developer.android.com/reference/android/os/Build.VERSION_CODES.html?utm_campaign=adp_series_sdkversion_010616&utm_source=medium&utm_medium=blog) 文档中了，但是所有恐怖的细节也都列在每次发布的平台亮点中了，在这个 [API Level](https://developer.android.com/guide/topics/manifest/uses-sdk-element.html?utm_campaign=adp_series_sdkversion_010616&utm_source=medium&utm_medium=blog#ApiLevels) 表中可以方便地找到相应的链接
 由于某些行为的变化对用户是非常明显的（弃用的 menu 按钮，运行时权限等），所以将 `target 更新为最新的 SDK 是所有应用都应该优先处理的事情`。但这不意味着你一定要使用所有新引入的功能，也不意味着你可以不做任何测试就盲目地更新 targetSdkVersion ，请一定在更新 targetSdkVersion 之前做测试！
```
##### 运行时权限

[Permissions Best Practices](https://developer.android.com/training/permissions/best-practices.html)

[Android权限最佳实践](http://www.jianshu.com/p/3e16bda04852)
```
讨论这个问题之前，我们得先检查一下项目的 target version。如果是 23及以上，则必须得适配新权限模式；如果是 23之下，则还是统一在安装时全部申请权限——即便如此，使用Android 6.0及以上系统的用户还是可以在设置中去关闭你的某些权限，[部分ROM厂商在6.0以下的系统也加入了自己的权限控制设置]。当权限被关闭时，不会导致你的应用直接崩溃，但是会导致你获取到的返回值为null 或者 0，这个是需要注意的地方
```

[Android M 新的运行时权限开发者需要知道的一切](http://jijiaxin89.com/2015/08/30/Android-s-Runtime-Permission/)

[关于Android 6.0 运行时权限](http://bxbxbai.github.io/2016/05/27/android-runtime-permission/)
```
关键点 targetSdk buildSdk 运行时权限 PermissionChecker.checkSelfPermission
```
```java
Process: com.example.yabinyang.phonepermission, PID: 30544
java.lang.SecurityException: Permission Denial: opening provider com.android.providers.contacts.ContactsProvider2 from ProcessRecord{fe78e04 30544:com.example.yabinyang.phonepermission/u0a430} (pid=30544, uid=10430) requires android.permission.READ_CONTACTS or android.permission.WRITE_CONTACTS
```

[Android 6.0 运行时权限管理最佳实践](http://blog.csdn.net/yanzhenjie1003/article/details/52503533/)
[AndPermission](https://github.com/yanzhenjie/AndPermission)
[Android6.0运行时权限解决方案](http://www.jianshu.com/p/d4a9855e92d3)
[PermissionsDispatcher](https://github.com/hotchemi/PermissionsDispatcher)
[Android 6.0 运行时权限处理完全解析](http://blog.csdn.net/lmj623565791/article/details/50709663)

[使用RxJava处理Android 6.0运行时动态权限获取](http://www.uml.org.cn/j2ee/2016042010.asp)

### 2017-02-18 设计模式之java基础 【类之间关系；注解；反射；序列化&反序列化】

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



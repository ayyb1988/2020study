
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


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



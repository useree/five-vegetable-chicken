# iOS思维导图
* [UI](https://github.com/useree/files/blob/master/UI.png)
* [Objective-C](https://github.com/useree/files/blob/master/Objective-C.png)
* [Runtime](https://github.com/useree/files/blob/master/Runtime.png)
* [内存管理](https://github.com/useree/files/blob/master/内存管理.png)
* [Block](https://github.com/useree/files/blob/master/Block.png)
* [多线程](https://github.com/useree/files/blob/master/多线程.png)
* [RunLoop](https://github.com/useree/files/blob/master/RunLoop.png)
* [网络](https://github.com/useree/files/blob/master/网络.png)
* [设计模式](https://github.com/useree/files/blob/master/设计模式.png)
* [架构/框架](https://github.com/useree/files/blob/master/%E6%9E%B6%E6%9E%84:%E6%A1%86%E6%9E%B6.png)
* [算法](https://github.com/useree/files/blob/master/算法.png)
* [第三方库](https://github.com/useree/files/blob/master/第三方库.png)


## runtime相关问题

### 结构模型

* 介绍下runtime的内存模型（isa、对象、类、metaclass、结构体的存储信息等）

* 为什么要设计metaclass

* class_copyIvarList & class_copyPropertyList区别

* class_rw_t 和 class_ro_t 的区别

* category如何被加载的,两个category的load方法的加载顺序，两个category的同名方法的加载顺序

* 分类为什么会覆盖同名方法的原有实现? 被覆盖后原有实现还能否被调用到?

* category & extension区别，能给NSObject添加Extension吗，结果如何

* 消息转发机制，消息转发机制和其他语言的消息机制优劣对比

* 在方法调用的时候，方法查询-> 动态解析-> 消息转发 之前做了什么

* IMP、SEL、Method的区别和使用场景

* load、initialize方法的区别什么？在继承关系中他们有什么区别

* 说说消息转发机制的优劣

### 内存管理

* weak的实现原理？SideTable的结构是什么样的

* 关联对象的应用？系统如何实现关联对象的

* 关联对象的如何进行内存管理的？关联对象如何实现weak属性

* Autoreleasepool的原理？所使用的的数据结构是什么

* ARC的实现原理？ARC下对retain & release做了哪些优化

* ARC下哪些情况会造成内存泄漏

### 其他

* Method Swizzle注意事项

* 属性修饰符atomic的内部实现是怎么样的?能保证线程安全吗

* iOS 中内省的几个方法有哪些？内部实现原理是什么

* class、objc_getClass、object_getclass 方法有什么区别?


## NSNotification

[轻松过面：一文全解iOS通知机制(经典收藏)](https://juejin.im/post/5e5fc16df265da575155723b)

* 实现原理（结构设计、通知如何存储的、name&observer&SEL之间的关系等）

* 通知的发送时同步的，还是异步的

* NSNotificationCenter接受消息和发送消息是在一个线程里吗？如何异步发送消息

* NSNotificationQueue是异步还是同步发送？在哪个线程响应

* NSNotificationQueue和runloop的关系

* 如何保证通知接收的线程在主线程

* 页面销毁时不移除通知会崩溃吗

* 多次添加同一个通知会是什么结果？多次移除通知呢

* 下面的方式能接收到通知吗？为什么
``
// 发送通知
[[NSNotificationCenter defaultCenter] addObserver:self selector:@selector(handleNotification:) name:@"TestNotification" object:@1];
// 接收通知
[NSNotificationCenter.defaultCenter postNotificationName:@"TestNotification" object:nil];
``

## Runloop & KVO

### runloop

* app如何接收到触摸事件的

* 为什么只有主线程的runloop是开启的

* 为什么只在主线程刷新UI

* 如何使线程保活

* PerformSelector和runloop的关系

* GCD 和 runloop 的有关系吗? (dispatch async main)

* source0 和 source1 分别处理哪些事件? 举出具体的例子(触摸,滑动,振动,锁屏,网络切换,网络回调等等)

* UI 渲染和 runloop observer 时机之间的关系(before wating时机)

* runloop observer 的作用以及实践(监测主线程卡顿, 获取UI渲染任务提交时机)

### KVO

* 实现原理

* 如何手动关闭kvo

* 通过KVC修改属性会触发KVO么

* 哪些情况下使用kvo会崩溃，怎么防护崩溃

* kvo的优缺点


## Block

* block的内部实现，结构体是什么样的

* block是类吗，有哪些类型

* 一个int变量被 __block 修饰与否的区别？block的变量截获

* block在修改NSMutableArray，需不需要添加__block

* 怎么进行内存管理的

* block可以用strong修饰吗

* 解决循环引用时为什么要用__strong、__weak修饰

* block发生copy时机

* Block访问对象类型的auto变量时，在ARC和MRC下有什么区别

## 多线程
主要以GCD为主

* iOS开发中有多少类型的线程？分别对比

* GCD有哪些队列，默认提供哪些队列

* GCD有哪些方法api

* GCD主线程 & 主队列的关系

* 如何实现同步，有多少方式就说多少

* dispatch_once实现原理

* NSOperationQueue中的maxConcurrentOperationCount默认值

* NSTimer、CADisplayLink、dispatch_source_t 的优劣

* 什么情况下会死锁

* 有哪些类型的线程锁，分别介绍下作用和使用场景

* 谈谈对各种锁的性能对比, 分别举一个性能好和不好的锁讲讲为什么

* 谈谈对线程优先级反转的理解, 以及如何避免这种情况出现

## 视图&图像相关

* AutoLayout的原理，性能如何

* UIView & CALayer的区别

* 事件响应链

* [全面的事件传递](https://www.jianshu.com/p/2e074db792ba)

* drawrect & layoutsubviews调用时机

* UI的刷新原理

* 隐式动画 & 显示动画区别

* 什么是离屏渲染

* imageName &  imageWithContentsOfFile区别

* 多个相同的图片，会重复加载吗

* 图片是什么时候解码的，如何优化

* 图片渲染怎么优化

* 如果GPU的刷新率超过了iOS屏幕60Hz刷新率是什么现象，怎么解决

## 架构设计

* 手动埋点、自动化埋点、可视化埋点

* MVC、MVP、MVVM设计模式

* 常见的设计模式

* 单例的弊端

* 常见的路由方案，以及优缺点对比

* 如果保证项目的稳定性

* 设计一个图片缓存框架(LRU)

* 如何设计一个git diff

* 设计一个线程池？画出你的架构图

* 你的app架构是什么，有什么优缺点、为什么这么做、怎么改进


## Model层：

* 数据持久化存储方案有哪些？

* 沙盒的目录结构是怎样的？各自一般用于什么场合？

* SQL语句问题：inner join、left join、right join的区别是什么？

* sqlite的优化网络通信用过哪些方式（100%的人说了AFNetworking...）

* 如何处理多个网络请求并发的情况

* 在网络请求中如何提高性能

* 在网络请求中如何保证安全性


## 其他问题

* PerformSelector & NSInvocation优劣对比

* oc怎么实现多继承？怎么面向切面（可以参考Aspects深度解析-iOS面向切面编程）

* 哪些bug会导致崩溃，如何防护崩溃

* 怎么监控崩溃

* app的启动过程（考察LLVM编译过程、静态链接、动态链接、runtime初始化）

* 沙盒目录的每个文件夹划分的作用

* 简述下match-o文件结构

* 谈谈对野指针的理解, 为什么会出现野指针, 野指针一定会造成 crash 吗?

* 谈谈动态库与静态库的区别, 各自的利弊分别是什么

## iOS底层
[备战2020：那些 iOS开发 常用的底层面试题合集！](https://juejin.im/post/5e61f04c6fb9a07cab3aa518)
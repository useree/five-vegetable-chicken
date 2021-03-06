# java面试概要
* 集合
* io
* 多线程
* jvm
* 设计模式
* 数据库
* 缓存
* 中间件源码
* 项目经历

## 集合相关问题
### 集合使用相关问题
* 单列,双列
* 有序,无序
* 存储重复数据
* 线程安全
* 迭代器遍历和for循环的区别,实现原理
### 集合实现原理相关
* 1.7.1.8hashmap,concurrentHashMap实现原理.
* 1.7hashmap多线程下为什么会造成cpu百分百.
* 1.8的hashmap,concurrentHashMap和1.7实现的比较.

## IO
### IO的分类
* 同步阻塞,同步非阻塞,IO多路复用,信号驱动,异步IO
### 前三种代码实现.
### 几种实现方式的比较.

## 多线程
### 锁相关
* synchronized,reentrantlock实现原理及区别
### 线程池
* 实现原理
* 线程池使用注意事项
### 阻塞队列
* 实现原理
* 几种阻塞队列的区别

## jvm相关
### java类加载
* 字节码文件格式
* 类加载过程
* 什么叫双亲委派
* 破坏双亲委派的例子.
### jvm内存模型
* 线程栈,程序计数器,本地方法栈,堆,方法区
* happens-before原则
* volatile理解.
### GC相关
* javaGC分代
* 几种垃圾回收器特点
* 几种垃圾回收算法

## 设计模式

## 数据库
### 事物
* 事物的定义,acid的理解
* mysql不同隔离级别下产生的问题
* mysql如何实现不同隔离级别.
* mvcc.
### 索引
* b+树索引的原理
* 索引使用注意事项.
### 锁
* 表锁,行锁,间隙锁
### binlog,redolog

## 缓存redis
### 一致性哈希算法
### 缓存穿透,缓存雪崩解决方案
### 分布式锁的实现

## 开源框架
### spring相关
* spring扩展点
* 容器刷新过程
* 如何解决循环依赖
* 如何解决循环依赖
* 事物传播行为
* 动态代理
### spring mvc相关
* spring mvc请求过程
### spring boot相关
* 启动原理.
### dubbo
* 了解spi机制
* 模块分类,调用过程.
### tomcat
### mq
### mybatis


## 项目相关
### 项目介绍,用了什么设计模式
### 应用CPU百分百怎么排查
### 应用运行一段时间后响应变慢怎么排查
### 工作中遇到什么难忘的问题,是如何发现以及解决的.












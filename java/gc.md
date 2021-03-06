##几种垃圾回收算法
###标记清除
* 首先标记所有需要回收的对象,然后再回收被标记的对象.
* 缺点: 1.时间. 标记和清除效率不高. 2.空间.会产生内存碎片.
###复制算法
* 实现:将内存分成两块,每次只使用其中的一块,当其中一块用完了,就将存活的对象复制到另一块上面,再把已用过的内存一次性清理掉.
* 优点:不会产生内存碎片,实现简单高效.
* 缺点:浪费内存.
###标记整理
* 实现:先标记所有需要回收的对象,然后将所有存活的对象向一端移动,再清理掉端以外的内存.

##GC roots
* 栈内引用
* 静态变量
* 常量
* 本地方法引用

## 垃圾收集器
###远古时代
* serial(新) Serial Old(老) 单线程
* Parallel Scavenge(新) Parallel Old(老) 多线程
##中古时代
* ParNew(新) CMS(老)
##现代
* G1

##CMS介绍
* 老年代回收器.响应时间优先.
* 使用标记清除算法,容器产生内存碎片.进而导致full gc.


##G1介绍 
* hotspot团队赋予的使命就是取代cms,jdk9已成默认垃圾回收器,适合管理大堆.
* 将整个堆分成很多个region(默认每个2048KB),每个region可以是edgn,survivor,old.对于大对象,直接分在Humongous.
* 可以设置-XX:MaxGCPauseMillis来让G1尽可能在指定时间内尽可能回收更大的垃圾.
* G1为了避免扫描整堆,在每个region上维护了一个RememberSet,记录了引用该分区对象的对象所在的卡表.当回收该分区时,只需要扫描其RSET判断引用本分区的对象是否存活,从而确定本分区对象是否存活.
* 标记整理算法.没有内存碎片,相比cms,能降低full gc的频率.
* reg之间不一定连续,对于CPU缓存加载机制不友好.

##G1相比CMS的优势(注意理解几个概率:Region,SATB,RSet,Pause Prediction Model)
* 空间. 前者标记整理,无内存碎片.
* 时间. 虽然降低停顿时间是共同目标,但是G1能设置可停顿时间.

##Gc调优目标
* 吞吐量(单位时间内,处理应用线程的时间占总时间的比)
* 响应时间

参考链接:https://blog.csdn.net/coderlius/article/details/79272773










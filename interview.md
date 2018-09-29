---
title: interview
date: 2018-09-26 15:52:21
tags:
---
 ### java基础

1. List和Set的区别
答：Set：不包含重复元素的Collection。List：有顺序的collection，并且可以包含重复元素
2. [HashSet是如何保证不重复的](https://blog.csdn.net/qq_27093465/article/details/52487584)
HashSet的值是存储在一个HashMap的key里面的，而正好HashMap的key是不能重复的。
hashmap里面put的时候，如果put(key,value)的key相同的话，是不是就是把原来的旧值给覆盖啦。
3. [HashMap是线程安全的么](http://www.importnew.com/21396.html)
HashMap是线程不安全的，HashTable是线程安全的，是通过synchronized实现的，所有的线程竞争一把锁，效率自然就低了。ConcurrentHashMap是线程安全的，内部实现了锁分段技术(含了segment数组，将数据分段存储，每个分段分配一把锁)
4. [HashMap的扩容过程](https://www.cnblogs.com/KingIceMou/p/6976574.html)
直接拷贝别的HashMap的形式
定义初始容量大小（table数组的大小，缺省值为16），定义负载因子（缺省值为0.75）的形式
5. [HashMap JDK 1.7和1.8 的区别](https://blog.csdn.net/xs521860/article/details/59484291)
1.7位桶+链表    1.8位桶+链表/红黑树，链表长度达到阈值变为红黑树
6. [final、finally、finalize的区别](http://www.importnew.com/22083.html)
final：修饰符，修饰类（不能被继承）、变量（不能改变值）、方法（不能重写) 
finally: 用在try catch的后面构造总是执行的代码块，JVM不关闭就能执行，通常用于释放资源
finalize: Object类中定义的方法，用于垃圾回收
7. [强引用、软引用、弱引用、虚引用的区别](https://www.cnblogs.com/yw-ah/p/5830458.html)
强引用：Object obj = new Object(), obj引用释放后，垃圾回收器才能回收
软引用：内存溢出之前进行回收 SoftReference<Object> sf = new SoftReference<Object>(obj),主要做缓存的功能
弱引用：第二次垃圾回收是回收 WeakReference<Object> wf = new WeakReference<Object>(obj)监控对象是否被垃圾
处理器标记为即将垃圾回收
虚引用：垃圾回收时回收，无法通过引用取到对象值 PhantomReference<Object> pf = new PhantomReference<Object>(obj)
8. JAVA反射
Java反射就是在运行状态中，对于任意一个类，都能够知道这个类的所有属性和方法；对于任意一个对象，都能够调用它的任意方法和属性；并且能改变它的属性。而这也是Java被视为动态
创建对象：a,通过类调用newInstance()，如String.class.newInstance() b,通过类对象的getConstructor()或getDeclaredContructor()获取到构造器，然后调用getInstance() 如：String.class.getConstructor(String.class).newInstance('Hello')
可通过getDeclaredField()获取字段对象，然后通过setAccessible(true)访问私有字段
9. [Arrays.sort实现原理](https://blog.csdn.net/u011410529/article/details/56668545?locationNum=6&fps=1)
不论是Collections.sort方法或者是Arrays.sort方法，底层实现都是TimSort实现的，这是jdk1.7新增的，以前是归并排序。TimSort算法就是找到已经排好序数据的子序列，然后对剩余部分排序，然后合并起来
10. collection实现原理
[Java 集合深入理解（3）：Collection](https://blog.csdn.net/u011240877/article/details/52773577)
Connection:是一个接口，各种集合的父接口
11.	LinkedHashMap的应用
[彻头彻尾理解 HashMap](https://blog.csdn.net/justloveyou_/article/details/62893086)
[彻头彻尾理解 LinkedHashMap](https://blog.csdn.net/justloveyou_/article/details/71713781)
[Java SE进阶之路](https://blog.csdn.net/column/details/14840.html)
它的内部通过双向链表实现，默认保持key的插入顺序，迭代的时候也是按照顺序迭代，可快速删除
12.	cloneable接口实现原理
[Cloneable接口源码分析与技术细节](https://blog.csdn.net/u013916933/article/details/51590332)
java开发中的一个常用接口，顾名思义作用就是将一个类的实例拷贝到另一个新的实例中，拷贝又分为深拷贝与浅拷贝。重写Object类中的clone()方法
13.	异常分类及处理机制
[JAVA中的异常处理机制及异常分类](https://blog.csdn.net/sinat_36713319/article/details/68945619)
Throwable是java中错误和异常的超类，下一层是Error(运行时系统内部错误和资源耗尽错误)和Exception(IOException/RuntimeException)。处理机制：如果程序不能按照正常途径完成任务，就可以通过另一种途径退出方法，在这种情况下会抛出一个封装了错误信息的对象，此时方法退出并没有返回值，其他调用该方法的代码无法继续执行，异常处理机制会交给异常处理器
14.	wait和sleep的区别
wait：线程释放弃对象锁，进入等待此对象的锁等待池，只有持有对象调用notify()后方可进入就绪状态
sleep: 休眠指定的时间，让出CPU。线程不会释放对象锁
15.	数组在内存中如何分配
"[数组的引用变量和内存分配](https://www.cnblogs.com/chenyaqiang/p/5419493.html)" 
数组也是一个对象，所以创建时会在堆上分配内存空间，然后返回对象的引用。数组只有分配内存空间后才可使用，数组初始化分为动态初始化和静态初始化。数组的引用变量存放在stack中，数组元素存放在heap中
 ### Java并发
16.	[synchronized 的实现原理及锁优化](https://blog.csdn.net/wsyw126/article/details/70807304)
synchronizde底层通过monitor(监视器锁)对象来实现、方法的同步是隐式的方式实现（根据ACC_SYNCHRONIZED标识符，
操作monitor)。可以用在普通方法(对象monitor)、静态方法(类的monitor)、代码块(this对象monitor)。内部通过监视器锁
来实现同步，这是依赖操作系统底层mutex_lock来实现的，我们称为重量级锁。JDK1.6后为了提高性能引入了“轻量级锁”、
“偏向锁”。引入的本意是在没有多线程竞争的情况下，减少性能消耗。轻量级锁应用于线程交替执行同步块的情况，如果同一
时间访问同一锁的情况，就会导致锁膨胀为重量级锁。偏向锁为了解决无多线程竞争的情况下减少不必要轻量级锁的执行路径
17.	[volatile]的实现原理(http://www.importnew.com/23520.html)
volatile是轻量级的sychronized，能减少线程上下文的切换和调度。用于多线程访问共享变量，线程通过排他锁获取变量，多个线程能获取最新的共享变量。底层通过内存屏障来实现。原子性、可见性、有序性、指令重排序、happens-before，对volatile变量的写操作happens-before后续的读操作，在写操作不依赖当前值并该变量不包含在其他变量的不变式中的条件满足才可以使用volatile
18.	[java信号灯？]()
Semaphore用于创建线程池，保持有限个线程并发执行。Semaphore通常用于有限访问资源的线程数目，她是一个计数信号量，记录了一个许可集合。与传统的互斥锁相比，最大的不同就是释放的时候并不需要拥有锁对象释放，也可由其他对象释放，信号没有所有权的概念
19. synchronized在静态方法和普通方法的区别
对象的监视锁与类的监视锁
20.	[怎么实现所有线程在等待某个事件触发后才执行](https://blog.csdn.net/jiyiqinlovexx/article/details/51236323)
1.闭锁CountDownLatch闭锁是典型的等待事件发生的同步工具类，将闭锁的初始值设置1，所有线程调用await方法等待，当事件发生时调用countDown将闭锁值减为0，则所有await等待闭锁的线程得以继续执行。
2.阻塞队列BlockingQueue所有等待事件的线程尝试从空的阻塞队列获取元素，将阻塞，当事件发生时，向阻塞队列中同时放入N个元素(N的值与等待的线程数相同)，则所有等待的线程从阻塞队列中取出元素后得以继续执行。
3.信号量Semaphore设置信号量的初始值为等待的线程数N，一开始将信号量申请完，让剩余的信号量为0，待事件发生时，同时释放N个占用的信号量，则等待信号量的所有线程将获取信号量得以继续执行。 
4.刚开始主线程先获取写锁，然后所有子线程获取读锁，然后等事件发生时主线程释放写锁
21.	什么是CAS？有什么缺陷，[如何解决](http://www.mamicode.com/info-detail-2355996.html)
CAS机制设置了3个基本操作数： 内存地址V、旧的预期值A、要修改的新值B
缺点：1CPU开销大，并发量高的情况下，多线程尝试更新某一个变量，确不成功，反复执行给CPU带来压力 2 不能保证代码的
原子性，CAS只保证一个变量的原子操作，而不能保证代码块的原子操作，比如3个变量共同进行原子操作 3  ABA问题，在某些算法中，如果V的值首先由A变成B，再由B变成A,那么CAS将会操作成功。ABA问题的解决思路就是使用版本号。在变量前面追加上版本号，每次变量更新的时候把版本号加一，那么A－B－A 就会变成1A-2B－3A。
22.	[synchronized和lock有什么区别](https://blog.csdn.net/u012403290/article/details/64910926?locationNum=11&fps=1)
存在层次：java的关键字，在JVM层面上；是一个类
锁的释放：1 获取锁的线程执行完代码块后释放锁 2 线程执行异常JVM让线程释放；在finally中必须释放，不如容易死锁
锁的获取： 假设A获得锁，B线程等待，如果A阻塞，B一直等待；尝试获得锁，线程可以不用一直等待
锁状态： 无法判断；可以判断
锁类型：可重入不可中断非公平；可重入、可中断、可公平
性能： 少量同步；大量同步
23.	[Hashtable是如何加锁的](https://www.cnblogs.com/wang-meng/p/5808006.html)
 HashTable容器使用synchronized来保证线程安全
24.	HashMap的并发问题
HashMap是非线程安全的
25.	ConcurrentHashMap介绍？[1.8中为什么要用红黑树](http://www.importnew.com/23610.html)
ConcurrentHashMap同步机制通过Lock实现，是线程安全的。ConcurrentHashMap基于concurrentLevel划分出了多个Segment来对key-value进行存储，从而避免每次锁定整个数组，在默认的情况下，允许16个线程并发无阻塞的操作集合对象，尽可能地减少并发时的阻塞现象。
26.	[AQS](https://www.cnblogs.com/waterystone/p/4920797.html)
AbstractQueuedSynchronizer类如其名，抽象的队列式的同步器，AQS定义了一套多线程访问共享资源的同步器框架，许多同步类实现都依赖于它，如常用的ReentrantLock/Semaphore/CountDownLatch...。独占和共享两种模式下获取-释放资源,
AQS也支持响应中断的
27.	如何检测死锁？怎么预防[死锁？](https://blog.csdn.net/yyf_it/article/details/52412071)
监测死锁： 首先为每个进程和每个资源指定一个唯一的号码，然后建立资源分配表和进程等待表
预防死锁： 资源一次性分配、可剥夺资源、资源有序分配
28.	[Java内存模型](https://blog.csdn.net/javazejian/article/details/72772461)
java内存模型中规定了所有的变量都存在主内存中，每条线程有自己的工作内存，线程对变量的多有操作都必须在工作内存中进行，不能直接读写主内存的变量。不同线程之间无法访问对方的工作内存，线程间变量的传递通过主内存完成。
29.	如何保证多线程下 i++的正确性
1 循环CAS，实现i++原子操作 (AtomicInteger)2 使用锁机制 3 使用sychronized
30.	[线程池的种类、区别和使用场景](https://www.cnblogs.com/sachen/p/7401959.html)
newCachedThreadPool、newFixedThreadPool、newSingleThreadPool、newScheduledThreadPool
31.	[分析线程池的实现原理和线程的调度过程](https://blog.csdn.net/aiengelangte/article/details/80397952)
线程的生命周期New、Runnable、Running、Blocked、Dead。线程的复用就是要保持线程的存活状态(Runnable、Running、
Blocked)、控制最大并发数、管理线程
32.	[线程池如何调优，最大数目如何确认？](https://blog.csdn.net/aiengelangte/article/details/80397952)
根据任务类型配置线程池的大小：CPU紧密型任务，参考值N(cpu)+1;IO紧密型任务,2*N(cpu)
33.	[ThreadLocal原理，使用的时候需要注意什么](https://www.jianshu.com/p/98b68c97df9b)
本地线程副本变量工具类。ThreadLocal只能保存一个变量副本，如果需要多个副本就需要创建多个ThreadLocal,
ThreadLocal内部的ThreadLocalMap的key为弱引用，会存在内存泄漏风险(调用ThreadLocal的get()、set()方法时完成后再调用remove方法，将Entry节点和Map的引用关系移除)、适用于无状态，副本变量独立后不影响业务逻辑的高并发场景
34.	[Condition接口实现原理](https://blog.csdn.net/zzti_erlie/article/details/80358564)
Condition的大概实现，AbstractQueuedSynchronizer内部维护着一个同步队列（双向链表实现），多个条件队列（单向链表实现），条件队列由AbstractQueuedSynchronizer的内部类ConditionObject来维护，new一个ConditonObject ，则多一个条件队列，当一个线程执行await方法是，会把当线程包装成一个Node节点，放到执行await方法的ConditionObject的条件队列中，释放锁并被阻塞，当执行signal方式时，会把条件队列的第一个节点移除，并转移到同步队列中，获取到锁即可继续执行
35.	[分段锁的原理，锁力度减小的思考](http://guochenglai.com/2016/06/04/java-concurrent4-java-subsection-decompose/)
锁粒度细分 ：锁分解(缩小锁范围、减少锁的粒度)，锁分段(一组独立的对象，ConcurrentHashMap，首先将数据分成一段一段的存储，然后给每一段数据配一把锁，当一个线程占用锁访问其中一个段数据的时候，其他段的数据也能被其他线程访问)
36.	[八种阻塞队列及各个阻塞队列的特性](http://ifeve.com/java-blocking-queue/)
ArrayBlockingQueue ：一个由数组结构组成的有界阻塞队列。
LinkedBlockingQueue ：一个由链表结构组成的有界阻塞队列。
PriorityBlockingQueue ：一个支持优先级排序的无界阻塞队列。
DelayQueue：一个使用优先级队列实现的无界阻塞队列。
SynchronousQueue：一个不存储元素的阻塞队列。
LinkedTransferQueue：一个由链表结构组成的无界阻塞队列。
LinkedBlockingDeque：一个由链表结构组成的双向阻塞队列。
 ### Spring相关
37.	[BeanFactory和FactoryBean的区别](https://www.cnblogs.com/aspirant/p/9082858.html)
BeanFactory是个Factory，也就是IOC容器或对象工厂，FactoryBean是个Bean。在Spring中，所有的Bean都是由BeanFactory(也就是IOC容器)来进行管理的。但对FactoryBean而言，这个Bean不是简单的Bean，而是一个能生产或者修饰对象生成的工厂Bean,它的实现与设计模式中的工厂模式和修饰器模式类似 
38.	[Spring IOC的理解及初始化过程](https://www.cnblogs.com/chenjunjie12321/p/6124649.html)
IoC文英全称Inversion of Control，即控制反转，我么可以这么理解IoC容器：“把某些业务对象的的控制权交给一个平台或者框架来同一管理，这个同一管理的平台可以称为IoC容器。”
（1）定位并获取资源文件(2)通过返回的resource对象进行BeanDefinition的载入(3)将BeanDefiniton注册到容器中
39.	[BeanFactory和ApplicationContext的区别和联系](https://www.cnblogs.com/wnlja/p/3907836.html)
BeanFacotry延迟加载，第一次调用getBean方法才会抛出异常，而ApplicationContext则初始化后自检；都支持
BeanPostProcessor、BeanFactoryPostProcessor的使用，前者需要手动注册、而后者自动注册
40.	Springbean的生命周期，如何被管理的
![Springbean的生命周期](https://upload-images.jianshu.io/upload_images/44770-f312de031566217d.png?imageMogr2/auto-orient/ "")
1实例化一个Bean，也就是我们通常说的new
2按照Spring上下文对实例化的Bean进行配置，也就是IOC注入
3如果这个Bean实现了BeanNameAware接口，会调用它实现的setBeanName(String beanId)方法，此处传递的是Spring配置文件中Bean的ID
4 如果这个Bean实现了BeanFactoryAware接口，会调用它实现的setBeanFactory()，传递的是Spring工厂本身（可以用这个方法获取到其他Bean）
5 如果这个Bean实现了ApplicationContextAware接口，会调用setApplicationContext(ApplicationContext)方法，传入Spring上下文，该方式同样可以实现步骤4，但比4更好，以为ApplicationContext是BeanFactory的子接口，有更多的实现方法
6如果这个Bean关联了BeanPostProcessor接口，将会调用postProcessBeforeInitialization(Object obj, String s)方法，BeanPostProcessor经常被用作是Bean内容的更改，并且由于这个是在Bean初始化结束时调用After方法，也可用于内存或缓存技术
7 如果这个Bean在Spring配置文件中配置了init-method属性会自动调用其配置的初始化方法
8如果这个Bean关联了BeanPostProcessor接口，将会调用postAfterInitialization(Object obj, String s)方法
注意：以上工作完成以后就可以用这个Bean了，那这个Bean是一个single的，所以一般情况下我们调用同一个ID的Bean会是在内容地址相同的实例
9 当Bean不再需要时，会经过清理阶段，如果Bean实现了DisposableBean接口，会调用其实现的destroy方法
10最后，如果这个Bean的Spring配置中配置了destroy-method属性，会自动调用其配置的销毁方法
41)	Springbean的加载过程
42)	SpringAOP要是自己实现该如何实现
43)	SpringIOC要是自己实现该如何实现
44)	Spring是如何管理事务的，事务管理机制
45)	Spring不同事务传播行为有哪些，有什么用
46)	Spring中用到了哪些设计模式
47)	SpringMVC工作原理
48)	Spring循环注入的原理
49)	Springaop的理解，各个术语相互直接是怎么工作的
50)	Spring如何保证controller并发的安全性
 ### Netty相关
51)	BIO、NIO和AIO
52)	Netty的各个组件
53)	Netty的线程模型
54)	TCP 粘包/拆包的原因及解决方法
55)	序列化协议，包括使用场景和如何选择
56)	Netty如何实现零拷贝
57)	Netty的高性能表现在哪些方面
 ### 分布式相关
58)	Dubbo的底层实现原理和机制
59)	描述一个服务从发布到被消费的详细过程
60)	分布式系统服务如何治理
61)	消息中间件如何解决消息丢失问题
62)	接口幂等性的概念
63)	Dubbo的服务请求失败如何处理
64)	重连机制会不会造成错误
65)	对分布式事务的理解
66)	如何实现负载均衡，有哪些算法可以实现
67)	Zookeeper的用途，及选举原理是什么
68)	数据的垂直拆分和水平拆分
69)	Zookeeper原理和使用场景
70)	Zookeeperwatch机制
71)	Redis/zookeeper节点宕机如何处理
72)	分布式集群下如何做到唯一序列号
73)	如何做一个分布式锁
74)	用过哪些MQ，如何用的，与其他MQ相比有哪些优缺点
75)	MQ系统的数据如何保证不丢失
76)	Zookeeper的选举策略
77)	全局ID
 ### 数据库相关
78)	Mysql分页有什么优化
79)	悲观锁和乐观锁
80)	组合索引，最左原则
81)	Mysql的表锁和行锁
82)	Mysql性能优化
83)	Mysql的索引分类，什么情况用什么索引
84)	事务的特性和隔离级别
 ### 缓存相关
85)	Redis有哪些数据类型，redis底层如何实现
86)	Redis缓存穿透，缓存雪崩
87)	如何使用redis来实现分布式锁
88)	Redis并发竞争问题如何解决
89)	Redis持久化的几种方式，优缺点是什么，如何实现的
90)	Redis缓存失效策略
91)	Redis集群高可用原理
92)	Redis缓存分片
93)	Redis数据淘汰策略
 ### JVM相关
94)	详细jvm内存模型
95)	什么情况下回出现内存溢出，内存泄漏
96)	Java线程栈
97)	Jvm年轻代到老年代晋升过程的判断条件是什么
98)	Jvm出现fullGC很频繁，怎么去线上排查问题
99)	类加载为什么要用双亲委派模式，什么场景打破了这个模式
100)类的实例化顺序
101)Jvm垃圾回收机制，何时触发MinorGC等操作
102)Jvm中一次完整的GC流程是怎样的
103)各种回收器，各自优缺点，重点CMS,G1
104)Oom错误，Stack Overflow错误，permgen


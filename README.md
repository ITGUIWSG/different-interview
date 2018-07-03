### Interviews

> 基于jdk1.8整理，不一样的java面试宝典。


### 目录  

* [java基础](#java基础)
* [java高级](#java高级)
* [spring框架](#spring框架)  
* [jvm](#jvm)  
* [高并发](#高并发)
* [大数据](#大数据)
* [源代码](#源代码)  


### java基础

* 面向对象的特征有哪些方面？  
```text
抽象   
  
  抽象是将一类对象的共同特征总结出来构造类的过程，包括数据抽象和行为抽象两方面。抽象只关注对象有哪些属性和行为，并不关注这些行为的细节是什么。 
 
封装  
  
  封装是把数据和操作数据的方法绑定起来，对数据的访问只能通过已定义的接口。
  
继承  
  
  继承是从已有类得到继承信息创建新类的过程。提供继承信息的类被称为父类（超类、基类）；得到继承信息的类被称为子类（派生类）。  
  
多态  
  
  多态性是指允许不同子类型的对象对同一消息作出不同的响应。  
    
  方法重载（overload）实现的是编译时的多态性（也称为前绑定），而方法重写（override）实现的是运行时的多态性（也称为后绑定）。  
    
  运行时的多态是面向对象最精髓的东西，要实现多态需要做两件事：
    
  1). 方法重写（子类继承父类并重写父类中已有的或抽象的方法）；  
    
  2). 对象造型（用父类型引用引用子类型对象，这样同样的引用调用同样的方法就会根据子类对象的不同而表现出不同的行为）。
```  

分析:  

```text
抽象:   
  
  比如要建立一个动物类，想想动物的共同属性和方法，吃东西、睡觉、移动等，这个提取共同特性的过程就叫做抽象，再抽象过程我们并没有考虑具体的
  
  细节，比如大象和猴子吃东西的不同这些细节。  
  
封装:    
  
  我们在使用手机的时候，简单几个按键我们就能拨打电话、聊微信，但是我们不能了解内部cpu怎么计算的，怎么和基站交互的，我们只了解手机暴露给
    
  我们的接口，即是我们操作的功能。  
  
继承:  
  
   比如继承遗产，这大家比较好理解。继承让变化中的软件系统有了一定的延续性。  
  
多态:  
  
  比如我们跟手机充电可以通过插头交流电充电，也可以使用充电宝冲电。我们事先并不知道，当我们具体使用的时候才确定，这就是运行时多态的表现。
    
  不论是交流电还是充电宝，它们都具备给手机充电的功能。我们事先不用知道是哪种方式，比如在真正充电的时候，我们使用充电宝了，那就是使用充电
    
  宝给手机充电。
   
```







### java高级  








### spring框架   








### jvm   








### 高并发   







### 源代码


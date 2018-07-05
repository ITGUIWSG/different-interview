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
  
  抽象是将一类对象的共同特征总结出来构造类的过程，包括数据抽象和行为抽象两方面。
    
  抽象只关注对象有哪些属性和行为，并不关注这些行为的细节是什么。 
 
封装  
  
  封装是把数据和操作数据的方法绑定起来，对数据的访问只能通过已定义的接口。
  
继承  
  
  继承是从已有类得到继承信息创建新类的过程。
    
  提供继承信息的类被称为父类（超类、基类）；得到继承信息的类被称为子类（派生类）。  
  
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
  
  比如要建立一个动物类，想想动物的共同属性和方法，吃东西、睡觉、移动等，这个提取共同特性的过程就叫做抽象，
  
  在抽象过程中我们并没有考虑具体的细节，比如大象和猴子吃东西的不同之处这些细节。  
  
封装:    
  
  我们在使用手机的时候，简单几个按键我们就能拨打电话、聊微信，但是我们不能了解内部cpu怎么计算的，
    
  怎么和基站交互的这些细节，我们只能了解到手机暴露给我们的接口，即是我们能操作的功能。  
  
继承:  
  
   比如继承遗产，这大家比较好理解。继承让变化中的软件系统有了一定的延续性。  
  
多态:  
  
  比如我们跟手机充电可以通过插头交流电充电，也可以使用充电宝冲电。我们事先并不知道，
    
  当我们具体使用的时候才确定，这就是运行时多态的表现。不论是交流电还是充电宝，
    
  它们都具备给手机充电的功能。我们事先不用知道是哪种方式，比如在真正充电的时候，  
  
  我们使用充电宝了，那就是使用充电宝给手机充电。
   
```  

* 谈谈java控制权限  
  
```text
java中为什么要设计访问权限控制机制:  
  
  1.为了使用户不要触碰那些他们不该触碰的部分，这些部分对于类内部的操作时必要的，但是它并不属于客户端程序员所需接口的一部分。  
    
  2.为了让类库设计者可用更改类的内部工作方式，而不必担心会对用户造成重大影响。  
  
  
Java中的访问权限控制的等级，按照权限从大到小依次为:
  
  public -> protected -> 包访问权限（没有权限修饰词）-> private
  
  public: 所有类都可以访问。 
  
  protected: 继承访问权限。
    
  private: 只有本类可以访问。  
    
  包访问权限:有时也表示为friendly,在同一个包中可以访问(如果不提供任何访问权限修饰词，则意味着它是包访问权限)。
```  

分析: 

```text
假如你是jdk的设计开发者，你为什么要设计访问权限呢？归根到底无非几点：
  
  1.我有些实现细节要隐藏起来,你调用的时候不用关心。
    
  2.我有些东西是我程序内部运行需要的，你不能任意改动，改动会出现不能运行等问题。
  
那么为什么设计个public和private就完了呢，实际业务中我们会发现，我们想要更灵活的访问权限，于是就有了包访问权限和protected。
  
这里需要注意包访问权限，jdk1.8之前可以表示为default,但是jdk1.8以后接口引入了default关键字，也有表示为friendly的，  
  
实际就是个代号，在修饰的对象前什么都不加就是包访问权限了。    
  
那protected访问权限呢？    
  
新类（称之子类或派生类）通过继承可以复用一个现有类（称之父类或基类），然后扩展基类的成员、方法。
  
有时，基类的创建者会希望某个特定成员，将它的访问权限赋予派生类而不是所有类。public无法做到这一点，为此，  
  
引入了protected来完成这一工作。 protected也提供包访问权限，也就是说，派生类以及相同包内的其他类都可以访问protected成员或方法。   
  
  
balabala说了一堆，有的同学估计都没耐心看了，说你敢不敢来点代码，no code no bb。下面咱就来个代码，往下看code来了。

```  
  
假设场景:
```text
假设有个程序员大神叫宙斯（Zeus),这个大神有2个儿子：阿波罗（Apollo）和阿瑞斯（Ares),悲催的是阿波罗（Apollo）是亲生的，  
  
阿瑞斯（Ares)是垃圾堆里捡的，这2兄弟都想找他daddy要100块钱买咸蛋超人，现在就看他daddy到底会不会偏袒哪个儿子吧。  
   
本故事纯属虚构，如有雷同纯属巧合，不喜勿喷。  
  
  
先来看看他爹Zeus有多少钱，是不是暴发户？
```  
code:
```java
package base;

public class Zeus {
    private int money = 1000;

    protected void giveMoney(int m) {
        this.money = this.money - m;
    }
}
```
```text
尼玛钱都用来养这2个熊孩子和还房贷了，就剩下1000块，看看Apollo到底是不是亲生的？
```
```java
package base;

public class Apollo extends Zeus{
    public static void main(String[] args) {
        new Apollo().giveMoney(100);
    }
}
```
```text
编译通过了，果然是亲生的，嗯嗯，肯定做过dna验证了。再来看看Ares这熊孩子，
  
Ares这熊孩子鸡贼的很，撒谎跟他爹Zeus说是Apollo想要钱买芭比娃娃,看看啥结果？
```
```java
package extend;

import base.Apollo;
import base.Zeus;

public class Ares extends Zeus {
    public static void main(String[] args) {
        new Apollo().giveMoney(100);  //compile fail
    }
}
```
```text
编译失败了，被他爹识破了。还是实话实说吧。
```
```java
package extend;

import base.Apollo;
import base.Zeus;

public class Ares extends Zeus {
    public static void main(String[] args) {
        new Ares().giveMoney(100);  
    }
}
```
```text
编译通过了,看来这爹还行，对2个儿子一视同仁。Ares撒对这慌被Apollo知道了，Apollo心里不爽，
  
也想以Ares的名义撒一次慌,说Ares想买咸蛋超人。
```
```java
package base;

import extend.Ares;

public class Apollo extends Zeus{
    public static void main(String[] args) {
        new Ares().giveMoney(100);
    }
}
```
```text
编译通过了,竟然把他爹蒙住了。哈哈～～
```
总结：
```text

```
















### java高级  








### spring框架   








### jvm   








### 高并发   







### 源代码


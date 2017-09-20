# java 23种设计模式----简单工厂模式
PS：[推荐使用GitHub插件查看代码](https://insight.io/)。代码、文档来自[北风网](http://www.ibeifeng.com/)，仅供自己学习使用。感谢主讲老师：**历风行** <br>
 推介一本书《[Java Web设计模式之道](https://item.jd.com/11181900.html)》蒋海昌 著<br>

# 设计模式概述
## 1 设计模式是什么：
一个设计模式就是一个已被记录的最佳实践或一个解决方案，这个最佳实践或解决方案已被成功应用在许多环境中，它解决了在某种特定环境中重复发生的某个问题。

# 设计模式原则

- 1、开闭原则(Open Closed Principle,OCP)是指：软件实体应当对扩展开放，对修改关闭。这个概念是大师Bertrand Meyer在1988年提出的，我们可以把开闭原则理解成----可以根据需求随意增加新的类，但不要修改原来的类
- 2、单一职责原则(Single Responsibility Principle,SRP)是指：就一个类而言，应该仅有一个引起它变化的原因。换言之，一个类，只需按职责进行功能设计。此原则从软件工程师角度分析，符合“高内聚，低耦合”的标准。并且，我们在接口设计及方面也同样符合单一职责的设计原则
- 3、里氏替换原则(Liskov Substitution Principle，LSP)它的完整表达是：若对每个类型S的对象o1，都存在一个类型T的对象o2，使得在所有针对编写的程序P中用o1替换o2后，程序P的行为功能不变，则S是T的子类型。
- 4、依赖倒转(Dependence Inversion Principle DIP)定义一：高层模块不应该依赖低层模块，二着都应该依赖于抽象。抽象不应该依赖于细节，细节应当依赖于抽象。定义二：** 要针对接口编程，不要针对实现编程 **
- 5、接口隔离原则简称ISP。定义一：不应该强迫客户依赖于他们不用的方法，定义二：一个类对另一个类的依赖性应当是建立在最小的接口上。
- 6、迪米特法则(Law of Demeter)又叫最少知识原则，它是指一个对象应当由其他对象有尽可能少的了解，不必与不相识的人直接联系。

# java 23种设计模式----工厂方法模式

## 1、什么是简单工厂模式
简单工厂模式属于类的创建型模式,又叫做静态工厂方法模式。通过专门定义一个类来负责创建其他类的实例，被创建的实例通常都具有共同的父类。

## 2、模式中包含的角色及其职责
- 1.工厂（Creator）角色简单工厂模式的核心，它负责实现创建所有实例的内部逻辑。工厂类可以被外界直接调用，创建所需的产品对象。
- 2.抽象（Product）角色简单工厂模式所创建的所有对象的父类，它负责描述所有实例所共有的公共接口。
- 3.具体产品（Concrete Product）角色简单工厂模式所创建的具体实例对象

## 3、简单工厂模式的优缺点
在这个模式中，工厂类是整个模式的关键所在。它包含必要的判断
逻辑，能够根据外界给定的信息，决定究竟应该创建哪个具体类的
对象。用户在使用时可以直接根据工厂类去创建所需的实例，而无
需了解这些对象是如何创建以及如何组织的。有利于整个软件体系
结构的优化。<br>
不难发现，简单工厂模式的缺点也正体现在其工厂类上，由于工厂类集中
了所有实例的创建逻辑，所以“高内聚”方面做的并不好。另外，当系统中的
具体产品类不断增多时，可能会出现要求工厂类也要做相应的修改，扩展
性并不很好。
# java 23种设计模式----工厂方法模式
## 1、什么是工厂方法模式
工厂方法模式同样属于类的创建型模式又被称为多态工厂模式 。工厂方法模式的意义是定义一个创建产品对象的工厂接口，将实际创建工作推迟到子类当中。核心工厂类不再负责产品的创建，这样核心类成为一个抽象工厂角色，仅负责具体工厂子类必须实现的接口，
这样进一步抽象化的好处是使得工厂方法模式可以使系统在不修改具体工厂角色的情况下引进新的产品。

## 2、模式中包含的角色及其职责
- 1.抽象工厂（Creator）角色工厂方法模式的核心，任何工厂类都必须实现这个接口。

- 2.具体工厂（ Concrete  Creator）角色具体工厂类是抽象工厂的一个实现，负责实例化产品对象。

- 3.抽象（Product）角色工厂方法模式所创建的所有对象的父类，它负责描述所有实例所共有的公共接口。

- 4.具体产品（Concrete Product）角色工厂方法模式所创建的具体实例对象

## 3、工厂方法模式和简单工厂模式比较
工厂方法模式与简单工厂模式在结构上的不同不是很明显。工厂方
法类的核心是一个抽象工厂类，而简单工厂模式把核心放在一个具
体类上。 <br>
工厂方法模式之所以有一个别名叫多态性工厂模式是因为具体工
厂类都有共同的接口，或者有共同的抽象父类。<br>
当系统扩展需要添加新的产品对象时，仅仅需要添加一个具体对象以及一个具体工厂对象，原有工厂对象不需要进行任何修改，也不需要修改客户端，很好的符合了“开放－封闭”原则。而简单工厂模式在添加新产品对象后不得不修改工厂方法，扩展性不好。<br>
工厂方法模式退化后可以演变成简单工厂模式。
# java 23种设计模式----抽象工厂模式
## 1、什么是抽象工厂模式
抽象工厂模式是所有形态的工厂模式中最为抽象和最其一般性的。抽象工厂模式可以向客户端提供一个接口，使得客户端在不必指定产品的具体类型的情况下，能够创建多个产品族的产品对象。
## 2、模式中包含的角色及其职责
- 1.抽象工厂（Creator）角色抽象工厂模式的核心，包含对多个产品结构的声明，任何工厂类都必须实现这个接口。
- 2.具体工厂（ Concrete  Creator）角色具体工厂类是抽象工厂的一个实现，负责实例化某个产品族中的产品对象。
- 3.抽象（Product）角色抽象模式所创建的所有对象的父类，它负责描述所有实例所共有的公共接口。
- 4.具体产品（Concrete Product）角色抽象模式所创建的具体实例对象<br>
总结：抽象工厂中方法对应产品结构，具体工厂对应产品族。
# java 23种设计模式----单例模式
## 1、什么是单例模式

单例模式是一种对象创建型模式，使用单例模式，可以保证为一个类只生成唯一的实例对象。也就是说，在整个程序空间中，该类只存在一个实例对象。<br>
其实，GoF对单例模式的定义是：保证一个类、只有一个实例存在，同时提供能对该实例加以访问的全局访问方法。
## 2、为什么要使用单例模式呢？

在应用系统开发中，我们常常有以下需求：
- 在多个线程之间，比如servlet环境，共享同一个资源或者操作同一个对象
- 在整个程序空间使用全局变量，共享资源
- 大规模系统中，为了性能的考虑，需要节省对象的创建时间等等。<br>

因为Singleton模式可以保证为一个类只生成唯一的实例
对象，所以这些情况，Singleton模式就派上用场了。
## 3、单例模式实现
- 1.饿汉式。
```
public static final Person person = new Person();
```
- 2.懒汉式。
```
//提供一个全局的静态方法，使用同步方法
public static synchronized Person3 getPerson() {
		if(person == null) {
			person = new Person3();
		}
		return person;
	}
```
- 3.双重检查。
```
//提供一个全局的静态方法
public static Person4 getPerson() {
		if(person == null) {
			synchronized (Person4.class) {
				if(person == null) {
					person = new Person4();
				}
			}

		}
		return person;
	}
```
# java 23种设计模式----原型模式

## 1、什么是原型模式
Prototype模式是一种对象创建型模式，它采取复制原型对象的方法来创建对象的实例。使用Prototype模式创建的实例，具有与原型一样的
数据。
## 2、原型模式的特点

- 1、由原型对象自身创建目标对象。也就是说，对象创建这一动作发自原型对象本身。
- 2.目标对象是原型对象的一个克隆。也就是说，通过Prototype模式创建的对象，不仅仅与原型对象具有相同的结构，还与原型对象具有相同的值。
- 3.根据对象克隆深度层次的不同，有浅度克隆与
深度克隆。
## 3、原型模式应用场景
- 1、 在创建对象的时候，我们不只是希望被创建的对象继承其基类的基本结构，还希望继承原型对象的数据。
- 2、希望对目标对象的修改不影响既有的原型对象（深度克隆的时候可以完全互不影响）。
- 3、隐藏克隆操作的细节。很多时候，对对象本身的克隆需要涉及到类本身的数据细节。
# java 23种设计模式----建造者模式
## 1、什么是建造者模式
Builder模式也叫建造者模式或者生成器模式，
是由GoF提出的23种设计模式中的一种。Builder模式是一种对象创建型模式之一，用来
隐藏复合对象的创建过程，它把复合对象的创建过程加以抽象，通过子类继承和重载的方式，动态地创建具有复合属性的对象。
## 2、建造者模式的结构
![](https://i.imgur.com/6VY8YeF.png)

## 3、建造者模式应用场景
- 1、对象的创建：Builder模式是为对象的创建而设计的模式
- 2、创建的是一个复合对象：被创建的对象为一个具有复合属性的复合对象
- 3、关注对象创建的各部分的创建过程：不同的工厂（这里指builder生成器）对产品属性有不同的创建方法

# java 23种设计模式----装饰模式
## 1、什么是装饰模式
装饰（ Decorator ）模式又叫做包装模式。通过一种对客户端透明的方式来扩展对象的功能，
是继承关系的一个替换方案。国外设计模式大师组合GOF把装饰模式定义为：动态的给对象添加一些额外的功能。可以理解为保持原有的功能不变并进行扩展。
## 2、装饰模式的结构
![](https://i.imgur.com/9SarGRd.png)
## 3、装饰模式的角色和职责
- 抽象组件角色： 一个抽象接口，是被装饰类和装饰类的父接口。
- 具体组件角色：为抽象组件的实现类。
- 抽象装饰角色：包含一个组件的引用，并定义了与抽象组件一致的接口。
- 具体装饰角色：为抽象装饰角色的实现类。负责具体的装饰。

# java 23种设计模式----策略模式
## 1、什么是策略模式
Strategy模式也叫策略模式是行为模式之一，它对一系列的算法加以封装，为所有算法定义一个抽象的算法接口，并通过继承该抽象算法接口对所有的算法加以封装和实现，具体的算法选择交由客户端决定（策略）。Strategy模式主要用来平滑地处理算法的切换 。
## 2、策略模式的结构
![](https://i.imgur.com/L8gZBzC.png)
## 3、策略模式的角色和职责
- Strategy:策略（算法）抽象。
- ConcreteStrategy   各种策略（算法）的具体实现。
- Context   策略的外部封装类，或者说策略的容器类。根据不同策略执行不同的行为。策略由外部环境决定。

## 4、策略模式的优点

- 1、 策略模式提供了管理相关的算法族的办法。策略类的等级结构定义了一个算法或行为族。恰当使用继承可以把公共的代码移到父类里面，从而避免重复的代码。
- 2、 策略模式提供了可以替换继承关系的办法。继承可以处理多种算法或行为。如果不是用策略模式，那么使用算法或行为的环境类就可能会有一些子类，每一个子类提供一个不同的算法或行为。但是，这样一来算法或行为的使用者就和算法或行为本身混在一起。决定使用哪一种算法或采取哪一种行为的逻辑就和算法或行为的逻辑混合在一起，从而不可能再独立演化。继承使得动态改变算法或行为变得不可能。
- 3、 使用策略模式可以避免使用多重条件转移语句。多重转移语句不易维护，它把采取哪一种算法或采取哪一种行为的逻辑与算法或行法还要原始和落后。

## 5、策略模式的缺点
- 1、 客户端必须知道所有的策略类，并自行决定使用哪一个策略类。这就意味着客户端必须理解这些算法的区别，以便适时选择恰当的算法类。换言之，策略模式只适用于客户端知道所有的算法或行为的情况。
- 2、 策略模式造成很多的策略类。有时候可以通过把依赖于环境的状态保存到客户端里面，而将策略类设计成可共享的，这样策略类实例可以被不同客户端使用。换言之，可以使用享元模式来减少对象的数量。

# java 23种设计模式----观察者模式

## 1、什么是观察者模式
- Observer模式是行为模式之一，它的作用是当一个对象的状态发生变化时，能够自动通知其他
关联对象，自动刷新对象状态。
- Observer模式提供给关联对象一种同步通信的手段，使某个对象与依赖它的其他对象之间保持
状态同步

## 2、观察者模式的结构
![](https://i.imgur.com/m8p9iL0.png)

## ３、观察者模式的角色和职责
- Subject（被观察者）被观察的对象。当需要被观察的状态发生变化时，需要通知队列中所有观察者对象。Subject需要维持（添加，删除，通知）一个观察者对象的队列列表。
- ConcreteSubject 被观察者的具体实现。包含一些基本的属性状态及其他操作。
- Observer（观察者）  接口或抽象类。当Subject的状态发生变化时，Observer对象将通过一个callback函数得到通知。
- ConcreteObserver  观察者的具体实现。得到通知后将完成一些具体的业务逻辑处理。

## 4、观察者模式的典型应用
- 侦听事件驱动程序设计中的外部事件
- 侦听/监视某个对象的状态变化
- 发布者/订阅者(publisher/subscriber)模型中，当一个外部事件（新的产品，消息的出现等等）被触发时，通知邮件列表中的订阅者

# java 23种设计模式----代理模式

## 1、什么是代理模式
Proxy模式又叫做代理模式，是构造型的设计模式之一，它可以为其他对象提供一种代理（Proxy）以控制对这个对象的访问。<br
	所谓代理，是指具有与代理元（被代理的对象）具有相同的接口的类，客户端必须通过代理与被代理的目标类交互，而代理一般在交互的过程中（交互前后），进行某些特别的处理。

## 2、代理模式的结构
![](https://i.imgur.com/iMSKDrm.png)

##３、代理模式的角色和职责
- subject（抽象主题角色）：<br>
       真实主题与代理主题的共同接口。

- RealSubject（真实主题角色）：<br>
     定义了代理角色所代表的真实对象。
- Proxy（代理主题角色）： <br>  含有对真实主题角色的引用，代理角色通常在将客户端调用传递给真是主题对象之前或者之后执行某些操作，而不是单纯返回真实的对象。

# java 23种设计模式----适配器模式

## 1、什么是适配器模式
Adapter模式也叫适配器模式，是构造型模式之一，通过Adapter模式可以改变已有类（或外部类）的接
口形式。

##２、适配器模式应用场景
在大规模的系统开发过程中，我们常常碰到诸如以下这些情况：我们需要实现某些功能，这些功能已有还不太成熟的一个或多个外
部组件，如果我们自己重新开发这些功能会花费大量时间；所以很多情况下会选择先暂时使用外部组件，以后再考虑随时替换。但这
样一来，会带来一个问题，随着对外部组件库的替换，可能需要对引用该外部组件的源代码进行大面积的修改，因此也极可能引入新
的问题等等。如何最大限度的降低修改面呢？Adapter模式就是针对这种类似需求而提出来的。
Adapter模式通过定义一个新的接口（对要实现的功能加以抽象），和一个实现该接口的Adapter（适配器）类来透明地调用外部组件。这样替换外部组件时，最多只要修改几个Adapter类就可以了，其他源代码都不会受到影响。

## 3、适配器模式的结构
- 1、通过继承实现Adapter
![](https://i.imgur.com/hrsClSa.png)

- 2、通过委让实现Adapter
![](https://i.imgur.com/iIQonHw.png)

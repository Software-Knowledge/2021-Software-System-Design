Lec7-Principles of Software Design
---

# 1. Software Design
1. Requirements defines
   1. The goals the system needs to satisfy.
2. Specification defines
   1. The externally-observable behaviour of the system.
3. Architecture defines
   1. The major system-level components
   2. Their methods of interaction
   3. Technology used
4. Design defines
   1. how the job will get done
   2. The code that needs to be written.
   3. We will focus exclusively on OO design.

# 2. Object Oriented Design
1. The process of applying implementation constraints to the conceptual model produced in object-oriented analysis.
2. describing the classes we will build our system out of in terms of their operations and attributes.
3. Adding classes that aren't obviously part of the domain, like abstract classes and interfaces
4. Describing how classes make up components.

# 3. Where OOD Fits
![](img/lec7/1.png)

# 4. Finding Appropriate Objects
1. Hard part about OOD is decomposing a system into objects.
2. Many objects come directly from the
   1. analysis model
   2. or from
   3. the implementation space (databases, files, UIs, IPC, …)
3. As well, there are other classes that have no such counterparts.
   1. used to generalize what would otherwise be an overly-specific design
   2. e.g., use of Strategy
      1. if you think an algorithm is likely to change
      2. add classes to implement a "strategy" pattern

# 5. The Bad News
1. There is no step-by-step method to get from the OOA to an OOD.
2. At least the OOA gives you the problem domain component in a fairly direct manner.
3. For the rest, you need experience.

![](img/lec7/2.png)

# 6. Experience
1. Seasoned designers see the same old problems come up again and again:
   1. how to design the classes for my 5th user interface
   2. how to design the classes to support persistence to a database for the 3rd time
   3. how to organize classes for reporting for the 5th time
2. Each time a similar problem comes up, designers will typically start with something that has worked for them before
   1. but then usually add a wrinkle inspired by something they could have done better the last time
3. Technology keeps changing under our feet, and so our design experience is quickly made obsolete
   1. (3-5 year half-life)

# 7. 本节内容
1. 面向对象设计原则概述
2. 单一职责原则
3. 开闭原则
4. 里氏代换原则
5. 依赖倒转原则
6. 接口隔离原则
7. 合成复用原则
8. 迪米特法则

## 7.1. 面向对象设计原则概述

### 7.1.1. 软件的可维护性和可复用性
1. 知名软件大师Robert C.Martin认为一个可维护性 (Maintainability) 较低的软件设计，通常由于如下4个原因造成：
   1. 过于僵硬(Rigidity)
   2. 过于脆弱(Fragility)
   3. 复用率低(Immobility)
   4. 黏度过高(Viscosity)
2. 软件工程和建模大师Peter Coad认为，一个好的系统设计应该具备如下三个性质：
   1. 可扩展性(Extensibility)
   2. 灵活性(Flexibility)
   3. 可插入性(Pluggability)
3. 软件的复用(Reuse)或重用拥有众多优点，如可以提高软件的开发效率，提高软件质量，节约开发成本，恰当的复用还可以改善系统的可维护性。
4. 面向对象设计复用的目标在于实现支持可维护性的复用。
5. 在面向对象的设计里面，可维护性复用都是以面向对象设计原则为基础的，这些设计原则首先都是复用的原则，遵循这些设计原则可以有效地提高系统的复用性，同时提高系统的可维护性。
6. 面向对象设计原则也是对系统进行合理重构的指南针，重构(Refactoring)是在不改变软件现有功能的基础上，通过调整程序代码改善软件的质量、性能，使其程序的设计模式和架构更趋合理，提高软件的扩展性和维护性。

## 7.2. 面向对象设计原则简介
1. 常用的面向对象设计原则包括7个，这些原则并不是孤立存在的，它们相互依赖，相互补充。

![](img/lec7/3.png)

## 7.3. 单一职责原则

### 7.3.1. 单一职责原则定义
1. 单一职责原则(Single Responsibility Principle, SRP)定义如下：一个对象应该只包含单一的职责，并且该职责被完整地封装在一个类中。
2. 其英文定义为：Every object should have a single responsibility, and that responsibility should be entirely encapsulated by the class.
3. 另一种定义方式如下：
   1. 就一个类而言，应该仅有一个引起它变化的原因。
4. 其英文定义为：There should never be more than one reason for a class to change.

### 7.3.2. 单一职责原则分析
1. 一个类（或者大到模块，小到方法）承担的职责越多，它被复用的可能性越小，而且如果一个类承担的职责过多，就相当于将这些职责耦合在一起，当其中一个职责变化时，可能会影响其他职责的运作。
2. 类的职责主要包括两个方面：数据职责和行为职责，数据职责通过其属性来体现，而行为职责通过其方法来体现。
3. 单一职责原则是实现高内聚、低耦合的指导方针，在很多代码重构手法中都能找到它的存在，它是最简单但又最难运用的原则，需要设计人员发现类的不同职责并将其分离，而发现类的多重职责需要设计人员具有较强的分析设计能力和相关重构经验。

### 7.3.3. 单一职责原则实例
1. 某基于Java的C/S系统的"登录功能"通过如下登录类(Login)实现：

![](img/lec7/4.png)

2. 现使用单一职责原则对其进行重构。

![](img/lec7/5.png)

## 7.4. 开闭原则

### 7.4.1. 开闭原则定义
1. 开闭原则(Open-Closed Principle, OCP)定义如下：一个软件实体应当对扩展开放，对修改关闭。也就是说在设计一个模块的时候，应当使这个模块可以在不被修改的前提下被扩展，即实现在不修改源代码的情况下改变这个模块的行为。
2. 其英文定义为：Software entities should be open for extension, but closed for modification.

### 7.4.2. 开闭原则分析
1. 开闭原则由Bertrand Meyer于1988年提出，它是面向对象设计中最重要的原则之一。
2. 在开闭原则的定义中，软件实体可以指一个软件模块、一个由多个类组成的局部结构或一个独立的类。

### 7.4.3. 开闭原则分析
1. 抽象化是开闭原则的关键。
2. 开闭原则还可以通过一个更加具体的"对可变性封装原则"来描述，对可变性封装原则(Principle of Encapsulation of Variation, EVP)要求找到系统的可变因素并将其封装起来。

### 7.4.4. 开闭原则实例
1. 某图形界面系统提供了各种不同形状的按钮，客户端代码可针对这些按钮进行编程，用户可能会改变需求要求使用不同的按钮，原始设计方案如图所示

![](img/lec7/6.png)

2. 现对该系统进行重构，使之满足开闭原则的要求。

![](img/lec7/7.png)

## 7.5. 里氏替代原则

### 7.5.1. 里氏代换原则定义
1. 里氏代换原则(Liskov Substitution Principle, LSP)有两种定义方式，第一种定义方式相对严格，其定义如下：如果对每一个类型为S的对象o1，都有类型为T的对象o2，使得以T定义的所有程序P在所有的对象o2都代换成o1时，程序P的行为没有变化，那么类型S是类型T的子类型。
2. 其英文定义为：If for each object o1 of type S there is an object o2 of type T such that for all programs P defined in terms of T, the behavior of P is unchanged when o1 is substituted for o2 then S is a subtype of T.
3. 第二种更容易理解的定义方式如下：所有引用基类（父类）的地方必须能透明地使用其子类的对象。
4. 其英文定义为：Functions that use pointers or references to base classes must be able to use objects of derived classes without knowing it.

### 7.5.2. 里氏代换原则分析
1. 里氏代换原则可以通俗表述为：在软件中如果能够使用基类对象，那么一定能够使用其子类对象。把基类都替换成它的子类，程序将不会产生任何错误和异常，反过来则不成立，如果一个软件实体使用的是一个子类的话，那么它不一定能够使用基类。
2. 里氏代换原则是实现开闭原则的重要方式之一，由于使用基类对象的地方都可以使用子类对象，因此在程序中尽量使用基类类型来对对象进行定义，而在运行时再确定其子类类型，用子类对象来替换父类对象。
3. 里氏代换原则由2008年图灵奖得主、美国第一位计算机科学女博士、麻省理工学院教授Barbara Liskov和卡内基.梅隆大学Jeannette Wing教授于1994年提出。
4. 其原文如下：Let q(x) be a property provable about objects x of type T. Then q(y) should be true for objects y of type S where S is a subtype of T.

### 7.5.3. 里氏替代原则实例
1. 某系统需要实现对重要数据（如用户密码）的加密处理，在数据操作类(DataOperator)中需要调用加密类中定义的加密算法，系统提供了两个不同的加密类，CipherA和CipherB，它们实现不同的加密方法，在DataOperator中可以选择其中的一个实现加密操作。如图所示：

![](img/lec7/8.png)

![](img/lec7/9.png)

## 7.6. 依赖倒转原则

### 7.6.1. 依赖倒转原则定义
1. 依赖倒转原则(Dependence Inversion Principle, DIP)的定义如下：高层模块不应该依赖低层模块，它们都应该依赖抽象。抽象不应该依赖于细节，细节应该依赖于抽象。
2. 其英文定义为：High level modules should not depend upon low level modules, both should depend upon abstractions. Abstractions should not depend upon details, details should depend upon abstractions.
3. 另一种表述为：要针对接口编程，不要针对实现编程。
4. 其英文定义为：Program to an interface, not an implementation.

### 7.6.2. 依赖倒转原则分析
1. 依赖倒转原则是Robert C. Martin在1996年为《C++ Reporter》所写的专栏Engineering Notebook的第三篇，后来加入到他在2002年出版的经典著作《Agile Software Development, Principles, Patterns, and Practices》中。

### 7.6.3. 依赖倒转原则分析
1. 简单来说，依赖倒转原则就是指：代码要依赖于抽象的类，而不要依赖于具体的类；要针对接口或抽象类编程，而不是针对具体类编程。
2. 实现开闭原则的关键是抽象化，并且从抽象化导出具体化实现，如果说开闭原则是面向对象设计的目标的话，那么依赖倒转原则就是面向对象设计的主要手段。
3. 依赖倒转原则的常用实现方式之一是在代码中使用抽象类，而将具体类放在配置文件
   1. 将抽象放进代码，将细节放进元数据
   2. Put Abstractions in Code, Details in Metadata
   3. 《程序员修炼之道：从小工到专家》(The Pragmatic programmer: from journeyman to master) 
4. 类之间的耦合
   1. 零耦合关系
   2. 具体耦合关系
   3. 抽象耦合关系
5. 依赖倒转原则要求客户端依赖于抽象耦合，以抽象方式耦合是依赖倒转原则的关键。
6. 依赖注入
   1. 构造注入(Constructor Injection)：通过**构造函数**注入实例变量。
   2. 设值注入(Setter Injection)：通过**Setter方法**注入实例变量
   3. 接口注入(Interface Injection)：通过**接口方法**注入实例变量。

![](img/lec7/10.png)

### 7.6.4. 依赖倒转原则
1. 某系统提供一个数据转换模块，可以将来自不同数据源的数据转换成多种格式，如可以转换来自数据库的数据(DatabaseSource)、也可以转换来自文本文件的数据(TextSource)，转换后的格式可以是XML文件(XMLTransformer)、也可以是XLS文件(XLSTransformer)等。

![](img/lec7/11.png)

2. 由于需求的变化，该系统可能需要增加新的数据源或者新的文件格式，每增加一个新的类型的数据源或者新的类型的文件格式，客户类MainClass都需要修改源代码，以便使用新的类，但违背了开闭原则。现使用依赖倒转原则对其进行重构。

![](img/lec7/12.png)

## 7.7. 接口隔离原则

### 7.7.1. 接口隔离原则定义
1. 接口隔离原则(Interface Segregation Principle, ISP)的定义如下：客户端不应该依赖那些它不需要的接口。
2. 其英文定义为：Clients should not be forced to depend upon interfaces that they do not use.
3. 注意，在该定义中的接口指的是所定义的方法。
4. 另一种定义方法如下：一旦一个接口太大，则需要将它分割成一些更细小的接口，使用该接口的客户
端仅需知道与之相关的方法即可。
其英文定义为：Once an interface has gotten too 'fat' it needs to be split into smaller and more specific interfaces so that any clients of the interface will only know about the methods that pertain to them.

### 7.7.2. 接口隔离原则分析
1. 接口隔离原则是指使用多个专门的接口，而不使用单一的总接口。每一个接口应该承担一种相对独立的角色，不多不少，不干不该干的事，该干的事都要干。
   1. 一个接口就只代表一个角色，每个角色都有它特定的一个接口，此时这个原则可以叫做"角色隔离原则"。
   2. 接口仅仅提供客户端需要的行为，即所需的方法，客户端不需要的行为则隐藏起来，应当为客户端提供尽可能小的单独的接口，而不要提供大的总接口。
2. 使用接口隔离原则拆分接口时，首先必须满足单一职责原则，将一组相关的操作定义在一个接口中，且在满足高内聚的前提下，接口中的方法越少越好。
3. 可以在进行系统设计时采用定制服务的方式，即为不同的客户端提供宽窄不同的接口，只提供用户需要的行为，而隐藏用户不需要的行为。

### 7.7.3. 接口隔离原则实例
1. 下图展示了一个拥有多个客户类的系统，在系统中定义了一个巨大的接口（胖接口）AbstractService来服务所有的客户类。可以使用接口隔离原则对其进行重构。

![](img/lec7/13.png)

![](img/lec7/14.png)

## 7.8. 合成复用原则

### 7.8.1. 合成复用原则定义
1. 合成复用原则(Composite Reuse Principle, CRP)又称为组合/聚合复用原则(Composition/ Aggregate Reuse Principle,CARP)，其定义如下：尽量使用对象组合，而不是继承来达到复用的目的。
2. 其英文定义为：Favor composition of objects over inheritance as a reuse mechanism.

### 7.8.2. 合成复用原则分析
1. 合成复用原则就是指在一个新的对象里通过关联关系（包括组合关系和聚合关系）来使用一些已有的对象，使之成为新对象的一部分；新对象通过委派调用已有对象的方法达到复用其已有功能的目的。简言之：要尽量使用组合/聚合关系，少用继承。
2. 在面向对象设计中，可以通过两种基本方法在不同的环境中复用已有的设计和实现，即通过组合/聚合关系或通过继承。
   1. 继承复用：实现简单，易于扩展。破坏系统的封装性；从基类继承而来的实现是静态的，不可能在运行时发生改变，没有足够的灵活性；只能在有限的环境中使用。（"白箱"复用）
   2. 组合/聚合复用：耦合度相对较低，选择性地调用成员对象的操作；可以在运行时动态进行。（"黑箱"复用）
3. 组合/聚合可以使系统更加灵活，类与类之间的耦合度降低，一个类的变化对其他类造成的影响相对较少，因此一般首选使用组合/聚合来实现复用；其次才考虑继承，在使用继承时，需要严格遵循里氏代换原则，有效使用继承会有助于对问题的理解，降低复杂度，而滥用继承反而会增加系统构建和维护的难度以及系统的复杂度，因此需要慎重使用继承复用。

### 7.8.3. 合成复用原则实例
1. 某教学管理系统部分数据库访问类设计如图所示：

![](img/lec7/15.png)

2. 如果需要更换数据库连接方式，如原来采用JDBC连接数据库，现在采用数据库连接池连接，则需要修改DBUtil类源代码。如果StudentDAO采用JDBC连接，但是TeacherDAO采用连接池连接，则需要增加一个新的DBUtil类，并修改StudentDAO或TeacherDAO的源代码，使之继承新的数据库连接类，这将违背开闭原则，系统扩展性较差。
3. 现使用合成复用原则对其进行重构。

![](img/lec7/16.png)

## 7.9. 迪米特法则

### 7.9.1. 迪米特法则定义
1. 迪米特法则(Law of Demeter, LoD)又称为最少知识原则(Least Knowledge Principle, LKP)，它有多种定义方法，其中几种典型定义如下：
   1. 不要和"陌生人"说话。英文定义为：Don't talk to strangers.
   2. 只与你的直接朋友通信。英文定义为：Talk only to your immediate friends.
   3. 每一个软件单位对其他的单位都只有最少的知识，而且局限于那些与本单位密切相关的软件单位。英文定义为：Each unit should have only limited knowledge about other units: only units "closely" related to the current unit.

### 7.9.2. 迪米特法则分析
1. 迪米特法则来自于1987年秋美国东北大学(Northeastern University)一个名为"Demeter"的研究项目。
2. 简单地说，迪米特法则就是指一个软件实体应当尽可能少的与其他实体发生相互作用。这样，当一个模块修改时，就会尽量少的影响其他的模块，扩展会相对容易，这是对软件实体之间通信的限制，它要求限制软件实体之间通信的宽度和深度。
3. 在迪米特法则中，对于一个对象，其朋友包括以下几类：
   1. 当前对象本身(this)
   2. 以参数形式传入到当前对象方法中的对象
   3. 当前对象的成员对象
   4. 如果当前对象的成员对象是一个集合，那么集合中的元素也都是朋友
   5. 当前对象所创建的对象。
4. 任何一个对象，如果满足上面的条件之一，就是当前对象的"朋友"，否则就是"陌生人"。
5. 迪米特法则可分为狭义法则和广义法则。在狭义的迪米特法则中，如果两个类之间不必彼此直接通信，那么这两个类就不应当发生直接的相互作用，如果其中的一个类需要调用另一个类的某一个方法的话，可以通过第三者转发这个调用。

![](img/lec7/17.png)

6. 狭义的迪米特法则：可以降低类之间的耦合，但是会在系统中增加大量的小方法并散落在系统的各个角落，它可以使一个系统的局部设计简化，因为每一个局部都不会和远距离的对象有直接的关联，但是也会造成系统的不同模块之间的通信效率降低，使得系统的不同模块之间不容易协调。
7. 广义的迪米特法则：指对对象之间的信息流量、流向以及信息的影响的控制，主要是对信息隐藏的控制。信息的隐藏可以使各个子系统之间脱耦，从而允许它们独立地被开发、优化、使用和修改，同时可以促进软件的复用，由于每一个模块都不依赖于其他模块而存在，因此每一个模块都可以独立地在其他的地方使用。一个系统的规模越大，信息的隐藏就越重要，而信息隐藏的重要性也就越明显。
8. 迪米特法则的主要用途在于控制信息的过载：
   1. 在类的划分上，应当尽量创建松耦合的类，类之间的耦合度越低，就越有利于复用，一个处在松耦合中的类一旦被修改，不会对关联的类造成太大波及
   2. 在类的结构设计上，每一个类都应当尽量降低其成员变量和成员函数的访问权限
   3. 在类的设计上，只要有可能，一个类型应当设计成不变类
   4. 在对其他类的引用上，一个对象对其他对象的引用应当降到最低

### 7.9.3. 迪米特法则实例
1. 某系统界面类(如Form1、Form2等类)与数据访问类(如DAO1、DAO2等类)之间的调用关系较为复杂，如图所示：

![](img/lec7/18.png)

![](img/lec7/19.png)

## 7.10. 思考
1. 在JDK 中，java.util.Stack是java.util.Vector类的子类，该设计合理吗？若不合理，请分析解释该设计存在的问题。

# 8. 小结
1. 对于面向对象的软件系统设计来说，在支持可维护性的同时，需要提高系统的可复用性。
2. 软件的复用可以提高软件的开发效率，提高软件质量，节约开发成本，恰当的复用还可以改善系统的可维护性。
3. 单一职责原则要求在软件系统中，一个类只负责一个功能领域中的相应职责。
4. 开闭原则要求一个软件实体应当对扩展开放，对修改关闭，即在不修改源代码的基础上扩展一个系统的行为。
5. 里氏代换原则可以通俗表述为在软件中如果能够使用基类对象，那么一定能够使用其子类对象。
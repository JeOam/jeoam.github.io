---
layout: post
title: Hello World
---
[UML](https://zh.wikipedia.org/zh-cn/%E7%BB%9F%E4%B8%80%E5%BB%BA%E6%A8%A1%E8%AF%AD%E8%A8%80)，Unified Modeling Language，统一建模语言。

上周五，大管家@[fenbox](http://segmentfault.com/u/fenbox) 给我们讲解分析产品需求的一套方法：UML

---

###用例图（Use Case Diagram）：对象角度描述业务
主要用来描述“用户、需求、系统功能单元”之间的关系。它展示了一个外部用户能够观察到的系统功能模型图。帮助开发团队以一种可视化的方式理解系统的功能需求。

用例图所包含的元素如下：
**参与者(Actor)**：表示与您的应用程序或系统进行交互的用户、组织或外部系统。用一个小人表示。
**用例(Use Case)**：用例就是外部可见的系统功能，对系统提供的服务进行描述。用椭圆表示。
**关系**：包含、扩展、泛化。

一种参与者对应一个用例：
￼![请输入图片描述][1]

包含关系(Include)：参与者 ---> 执行的动作/功能 - -> 可能继续细化的动作/功能
![请输入图片描述][2]
包含关系用来把一个较复杂用例所表示的动作/功能分解成较小的步骤（父用例 -> 子用例）。

**扩展关系(Extend)**：参与者 ---> 执行的动作/ 功能<- - 可能触发的动作/功能
![请输入图片描述][3]
扩展关系是指用例功能的延伸，相当于为基础用例提供一个附加功能。

**泛化关系（Inheritance）**：就是通常理解的继承关系，子用例和父用例相似，但表现出更特别的行为；子用例将继承父用例的所有结构、行为和关系。子用例可以使用父用例的一段行为，也可以重载它。父用例通常是抽象的。
![请输入图片描述][4]

还可以有的关系：**注释(Comment)、依赖(Dependency)**，基本原理相似。

一个用例图示例：
![请输入图片描述][5]

建模阶段：能描述⼀个完整的业务流程即可（如：装宽带）；
分析阶段：能描述⼀个完整的事件流程即可（如：业务申请、业务受理、现场安装）；

**用例描述表**：保证所有⽤例在⼀个层级，当⽤列图并不能清楚地表达功能需求，通常⽤描述⽂档来补充某些不易表达的⽤例，下图的表给大家提供一个参考：
![请输入图片描述][6]



资料参考：[UML用例图总结](http://blog.csdn.net/tianhai110/article/details/6369762)

---

###时序图（Sequence Diagram）：从计算机角度描述用例
时序图（Sequence Diagram）是通过描述对象之间发送消息的时间顺序显示多个对象之间的动态协作。它可以表示用例的行为顺序，当执行一个用例行为时，时序图中的每条消息对应了一个类操作或状态机中引起转换的触发事件。

它是显示对象之间交互的图，这些对象是按时间顺序排列的。顺序图中显示的是参与交互的对象及其对象之间消息交互的顺序。时序图中包括的建模元素主要有：

1. 对象（Actor）：可选地显示对象名和类名。
2. 生命线（Lifeline）：生命线在顺序图中表示为从对象图标向下延伸的一条虚线，表示对象存在的时间。
3. 控制焦点（Focus of control）：控制焦点是顺序图中表示时间段的符号，在这个时间段内对象将执行相应的操作。用小矩形表示。
4. 消息（Message）：消息一般分为同步消息（Synchronous Message），异步消息（Asynchronous Message）和返回消息（Return Message）。

![请输入图片描述][7]

* 同步消息=调用消息（Synchronous Message）：消息的发送者把控制传递给消息的接收者，然后停止活动，等待消息的接收者放弃或者返回控制。用来表示同步的意义。
* 异步消息（Asynchronous Message）：消息发送者通过消息把信号传递给消息的接收者，然后继续自己的活动，不等待接受者返回消息或者控制。异步消息的接收者和发送者是并发工作的。
* 返回消息（Return Message）：返回消息表示从过程调用返回

资料参考：[UML建模之时序图（Sequence Diagram）](http://www.cnblogs.com/ywqu/archive/2009/12/22/1629426.html)

---

大管家还说了两种图：状态图、活动图，基本原理和流程图相似，略过不表；

---

###类图：描述结构化设计
![请输入图片描述][8]

类图（Class Diagram）: 类图是面向对象系统建模中最常用和最重要的图，是定义其它图的基础。类图主要是用来显示系统中的类、接口以及它们之间的静态结构和关系的一种静态模型。

在画类图的时候，理清类和类之间的关系是重点。

类图的3个基本组件：类名、属性、方法。 
![请输入图片描述][9]

资料参考：[UML类图与类的关系详解](http://www.uml.org.cn/oobject/201104212.asp)


---

###UML的认识误区
 
#####误区一：认为UML主要用于软件设计。
UML除了用于软件设计，还能用于需求分析，如何在需求分析工作中活用UML的。
 
#####误区二：客户无法理解UML，在需求分析中应用UML实际意义不大。
不熟悉UML时，确实也有这样的怀疑，而实际工作中发现UML恰恰成为与客户沟通的良好桥梁!UML其实不难读懂，只要稍加解释客户马上就能读懂
UML能直观、形象、严谨地描述出业务概念、业务流程、客户的期望和需求，只要稍加引导客户，客户将会很容易读懂UML
 
#####误区三：认为UML语法繁杂，难以学习和应用。
 
#####误区四：UML用途不大。
 
有人推崇UML，但也有不少人士不太认可UML。不认可的原因主要是因为一些人士学习UML后，发现在实际工作中发挥的作用并不是很大，有时候不用UML效果更好。UML不能解决所有问题，但对于提升需求分析能力帮助还是很大的。UML的常用语法可能几天就能学会了，⽽要真正做到“thinking in UML”却没有这么容易，需要长期的锻炼。

---

大管家最后推荐了两个 Mac OS 可用的 UML 建模的软件：[Gliffy Diagrams](https://chrome.google.com/webstore/detail/gliffy-diagrams/bhmicilclplefnflapjmnngmkkkkpfad?hl=zh-CN)（一个 Chrome 扩展程序），OmniGraffle。

---

本文基于@[fenbox](http://segmentfault.com/u/fenbox)的分享《UML需求分析入门》，图片大部分来自配套的 slides，少部分来自参考资料。


  [1]: http://segmentfault.com/img/bVbUBX
  [2]: http://segmentfault.com/img/bVbUBZ
  [3]: http://segmentfault.com/img/bVbUB0
  [4]: http://segmentfault.com/img/bVbUCS
  [5]: http://segmentfault.com/img/bVbUC2
  [6]: http://segmentfault.com/img/bVbUCX
  [7]: http://segmentfault.com/img/bVbUDb
  [8]: http://segmentfault.com/img/bVbUDh
  [9]: http://segmentfault.com/img/bVbUDq
  [10]: http://segmentfault.com/img/bVbUDr
  [11]: http://segmentfault.com/img/bVbUDs

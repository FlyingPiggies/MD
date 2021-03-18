# 设计模式 - Design Pattern

- SOILD原则
    
    1. 单一职责原则 (SRP - The Single Responsibility Principle)

        There should never be more than one reason for a class to change.    

    2. 开闭原则 (Open Closed Principle)

        Software entities(classes, modules, functions, etc.) should be open for extension, but closed for modification.

    3. 里氏替换原则 (The Liskov Substitution Principle)

        Functions that use pointers or references to base classes must be able to use objects of derived classess without knowing it.

    4. 接口隔离原则（Interface Segregation Principle）

        Clients should not be forced to depend upon interfaces that they don't use. The dependency of one class to another one should depend on the smallest possible.

    5. 依赖倒置原则（Dependence Inversion Principle）

        High level modules should not depend upon low level modules. Both should depend upon abstraction. Abstractions should not depend upon details. Details should depend upon abstracts.


- 二十三种常用的设计模式

    通常把二十三个常用模式分为三类：创建型模式，结构式模式，行为型模式。

    1. 创建型模式   

        创建型模式关注点是如何创建对象，核心思想是把对象的创建和使用相分离，使得两者相对独立的变换。

        - 工厂方法（Factory Method）

            定义一个用于创建对象的接口，让子类决定实例化哪一个类。工厂方法使一个类的实例化延迟到子类。

        - 抽象工厂（Abstract Factory）

            提供一个创建一系列相关或相互依赖对象的接口，而无需指定它们具体的类。

        - 生成器模式（Builder）

            将一个复杂对象的构建与它的表示分离，使得同样的构建过程可以构建不同的表示。

        - 原型模式（Prototype）

            用原型实例指定创建对象的种类，并且通过拷贝这些原型创建新的对象。

        - 单例模式（Singleton）

            保证一个类只有一个实例，并提供一个访问它的全局访问点。


    2. 结构型模式

        结构型模式主要涉及如何组合各种对象以便获得更好、更灵活的结构。

        - 适配器（Adapter/Wrapper）

            将一个类的接口转换成客户希望的另外的一个接口，使得原本由于接口不兼容而不能一起工作的那些类可以一起工作。

        - 桥接（Bridge）

            将抽象部分与它的实现部分分离，使它们都可以独立的变化。

        - 组合（Composite）

            将对象组合成树形结构一表示“部分-整体”的层次结构，使得用户对单个对象和组合对象的使用具有一致性。

        - 装饰器（Decorator）

            动态的给一个对象添加一些额外的职责。就增加功能来说，相比生成子类更为灵活。

        - 外观（Facade）

            为子系统中的一组接口提供一个一致的界面。

        - 享元（Flyweight）

            运用共享技术有效地支持大量细粒度的对象。

        - 代理（Proxy）

            为其他对象提供一种代理以控制对这个对象的访问。


    3. 行为型模式

        行为型模式主要涉及算法和对象之间的职责分配

        - 责任链（Chain of Responsibility）
            
            使多个对象都有机会处理请求，从而避免请求的发送者和接收者之间的耦合关系。将这些对象连成一条链，并沿着这条链传递该请求，直到有一个对象处理它为止。

        - 命令（Command）

            将一个请求封装为一个对象，从而使你可用不同的请求对客户进行参数化，对请求排队或记录请求日志，以及支持可撤销的操作。

        - 解释器（interpreter）

            给定一个语言，定义它的文法的一种表示，并定义一个解释器，这个解释器使用该表示来解释语言中的句子

        - 迭代器（iteraor）

            提供一种方法顺序访问一个聚合对象的各个元素，而又不需要暴露该对象的内部表示。

        - 中介（mediator）

            用一个中介对象来封装一系列的对象交互。中介者使各个对象不需要显示的相互引用，从而使其耦合松散，而且可以独立地改变它们之间的交互。

        - 备忘录（memento）

            在不破坏封装性的前提下，捕获一个对象的内部状态，并在该对象之外保存这个状态。

        - 观察者（Observer / Publish-Subscribe）

            定义对象间的一种一对多的依赖关系。当一个对象的状态发生改变时，所有依赖于它的对象都得到通知并自动更新。

        - 状态（State）

            允许一个对象在其内部状态发生改变时，改变自身的行为。对象看起来改变了它的类。

        - 策略（Stragety）

            定义一系列的算法，把它们一个个封装起来，并且使它们可相互替换。本模式使得算法可以独立于它的客户而变化。

        - 模板方法（Template）

            定义一个操作中的算法的骨架，而将一些步骤延迟到子类，使得子类可以不改变一个算法的结构即可重定义该算法的某些特定步骤。
        
        - 访问者（Visitor）

            表示一个作用于某对象结构中的各元素的操作。它使你可以在不改变各元素的类的前提下定义作用于各元素的新操作。


       



> [设计模式](https://www.liaoxuefeng.com/wiki/1252599548343744/1264742167474528)




# DesignPattern
  note DP == DESIGN PRINCIPLE
# Note
  多从 interface角度出发。 interface or abstractClass
  super(para) 调用父类有参构造函数

# Design Principle
  要组成，不要继承。。 比如protect 的只有继承才能call, 不好. 加instance variable 好  
  继承是为了type matching, 不是为了继承行为（funciton)

## 观察者模式
* Publishers + Subscribers = Obeserver pattern
* Subscribers == Obeserver, Publisher == Subject Object
* One to many dependency
* Java support Observer
** java.util.Observer

## Decorator Pattern
DP: class should be open to extend, close for modification
  感觉像是 subclass of abstract class 包含一个instance variable， 这个变量存的是一个abstrac class 的实例。 这样就是一层decoration。 decorator 嵌套就是链式， 有点recursive的感觉
* 我理解的模式模式，有一个实例被wrap, 可以层层wrap, 外层重写call 上层实例， 并重写默写函数
```java
public abstract BaseClass {
}
public abstract decrator extends Baseclass{}

public ConcreteDecorator extends decorator {
  BaseClass instance
  public decorator(Baseclass instance){this.instance = instance)}
  // overide some function relying on instance
  }
 ```
例子： java i/o class
缺点：冗多的subclass

## 工厂模式


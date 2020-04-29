# DesignPattern
  note DP == DESIGN PRINCIPLE
# Note
  多从 interface角度出发。 interface or abstractClass
  super(para) 调用父类有参构造函数

# Design Principle
  1. 将会变的和不变的区分开来
  1. 要组成，不要继承。。 比如protect 的只有继承才能call, 不好. 加instance variable 好  
  1. 继承是为了type matching, 不是为了继承行为（funciton)

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
出发点就是 把变化的部分和不变的部分分开
没太明白优势

## 单例模式
1. static public method  getInstance
1. private constructor
```java
public class Example {
  private static Example instance;;

  private Example() {}

  public static Example getInstance() {
     if (instance == null) {
       intance = new Example()
       }
       return instance;
  }
}
```
例子， alb 的metric 
* 注意 多线程安全， make getInstance sychronized
** Improvement 1. 提前实例化 2. volatile 
```java
public class Singleton {
    public static volatile Singleton singleton;

    /**
     * 构造函数私有
     */
    private Singleton(){}

    /**
     * 单例实现
     */
    public static Singleton getInstance(){
        if(singleton == null){
            synchronized (singleton) {
            // double check
                if(singleton == null){
                    singleton = new Singleton();
                }
            }
        }
        return singleton;
    }
}
```
> 一个线程修改了共享变量值，而另一个线程却看不到。引起可见性问题的主要原因是每个线程拥有自己的一个高速缓存区——线程工作内存。volatile关键字能有效的解决这个问题

https://blog.csdn.net/fuyuwei2015/article/details/71939591

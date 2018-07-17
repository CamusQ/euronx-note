# 内部类
定义在类中的类
```java
class A {
  class B {
  
  }
}
```
## 内部类与外部类
内部类可以访问外围对象**所有成员**，因为当外围类对象创建一个内部类对象的时候，该内部类对象会隐式的捕获一个指向外围类对象的引用，所以在拥有外部类对象之前是不可能创建内部类对象的
* `.this`生成对外部类对象的引用
```java
public class A {
  
  public class B {

    public A getA(){
      // 返回一个A对象的引用
      return A.this;
    }
  }
}
```
* `.new`创建内部类对象
```java
public class A{
  
  public class B{
  
  }
  
  public static void main(String[] args){
    A a = new A();
    B b = a.new B();
  }
}
```
* 内部类与向上转型——隐藏实现细节
```java
interface B{}

public class A{
  
  private class BImpl implements B{}
  
  public B getB(){
    // 向上转型
    return new BImpl();
  }
}
```
* 匿名内部类
```java
new Thread(new Runnable() {
  public void run() {}
}).start();
```
创建一个继承自`Runnable`接口的类，通过new 表达式返回的引用被自动向上转型为对`Runnable`的引用，等价于，
## 嵌套类Nested Class
嵌套类为声明为`static`的内部类，与外围类对象无联系，无法访问外围类中非静态对象


* ，因为内部类需要连接到外部类的对象上
* 非嵌套内部类不能有static字段
* 内部类可以访问外部类的全部成员(包括private)，因为创建内部类对象时，对象秘密捕获一个外部类对象的引用
* 可以创建一个private内部类继承公共接口，达到隐藏实现细节的目的
* 内部类也可以创建在方法中和作用域中（比如if（））
* 外部类名+.this是生成外部类对象的引用
* 生成内部类的两种方法
*   1外部类对象的引用+.new生成与某个外部类对应的内部类的对象
*   2在外部类中添加生成内部类实例的方法
* 内部类可以设置在方法里（局部内部类），否则是成员内部类
* 成员内部类是外部类的一个成员，具有成员的特点	
* 静态的内部类称为嵌套类
* 因为是静态的，所以与外围对象没有联系
* 创建时不需要外部对象，也不需要外部类名前缀，也不存在对外部类对象的this引用
* 发生名字相同时，内部类优先使用内部类成员，如果需要使用外部成员，用this引用
* 匿名内部类想使用定义在外部的对象，则参数引用必须是final

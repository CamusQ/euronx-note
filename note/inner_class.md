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
### `.this`生成对外部类对象的引用
```java
public class A {
  
  public class B {

    public A getA(){
      // 返回一个A对象的引用
      return A.this;
    }
  }
}
### ```
发生名字重复时，内部类优先使用内部类成员，如果需要使用外部成员，用this引用
`.new`创建内部类对象
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
### 内部类与向上转型——隐藏实现细节
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
### 匿名内部类
```java
new Thread(new Runnable() {
  public void run() {}
}).start();
```
创建一个继承自`Runnable`接口的类，通过new 表达式返回的引用被自动向上转型为对`Runnable`的引用
## 嵌套类Nested Class
嵌套类为声明为`static`的内部类
```java
class A {
	static class B {

	}

	public static void main(String[] args) {
		B b = new B();
	}
}
```
### 嵌套类和内部类的区别

* 嵌套类创建时不需要外部对象
* 与外围类对象无联系，无法访问外围类中非静态对象
也不需要外部类名前缀，也不存在对外部类对象的`.this`引用
* 非嵌套内部类不能有`static`字段



* 内部类也可以创建在方法中和作用域中（比如if（））
* 内部类可以设置在方法里（局部内部类），否则是成员内部类
* 成员内部类是外部类的一个成员，具有成员的特点	
* 创建时不需要外部对象，也不需要外部类名前缀，也不存在对外部类对象的this引用

* 匿名内部类想使用定义在外部的对象，则参数引用必须是final

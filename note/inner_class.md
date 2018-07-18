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
```
发生名字重复时，内部类优先使用内部类成员，如果需要使用外部成员，用this引用
### `.new`创建内部类对象
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
相当于创建一个继承自`Runnable`接口的类，通过new表达式返回的引用被自动向上转型为对`Runnable`的引用
### 内部类的继承
因为内部类的创建必须连接到外部类对象的引用，所以继承内部类的时候，外部类对象必须被初始化
```java
class A {
  class B {
  }
}

class C extends A.B {
  // A(){} Won't compile
  public C(A a) {
    a.super();
  }
}
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
* 与外围类对象无联系，无法访问外围类中**非静态**对象
也不需要外部类名前缀，也不存在对外部类对象的`.this`引用
* 非嵌套内部类不能有`static`字段
### 嵌套类与`main`方法
```java
class A {
  static class B{
    public static void main(String[] args) {
      System.out.println("Hello");
    }
  }
}
```
可以在每个类中编写一个`main`方法，但是这样次运行的时候都会编译整个文件，在嵌套类中的`main`方法只会生成一个独立的class文件`A$B`

## 内部类的意义
* 内部类提供了一个进入外围类的入口
```java
class Sequence {
	int[] nums = { 1, 5, 9, 9 };

	private class NumsIterator implements Iterator<Integer> {
		int index = 0;

		@Override
		public boolean hasNext() {
			return index < nums.length;
		}
	
		@Override
		public Integer next() {
			return nums[index++];
		}

	}

	public Iterator<Integer> iterator() {
		return new NumsIterator();
	}

	public static void main(String[] args) {
		Sequence seq = new Sequence();
		Iterator<Integer> iter = seq.iterator();
		while (iter.hasNext()) {
			System.out.println(iter.next());
		}
	}
}
```
* 内部类可以实现多重继承
```java
// 当父类不是接口的时候
abstract class Head{}
abstract class Foot{}
class Person{
  class MyHead extends Head{
  }
  class MyFoot extends Foot{
  }
}

```
* 允许回调
比如`swing`中的监听器，在主类中触发事件调用监听器，监听器又会调用主类中的方法来响应

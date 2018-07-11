# Eclipse相关操作
> [EURONX]® 建议使用背景色 

  色调85  饱和度104  亮度205
  
  R202  G234  B206
 ## 初始化
 * 建议使用 UTF-8编码
 
 在生成Javadoc的时候如果产生乱码，在配置信息中填-encoding UTF-8 -charset UTF-8
## 常用快捷键
### 移动代码
Ctrl + →： 光标向右移动一个单词

Shift + →： 向右选择一个字符

Ctrl + Shift + →：向右选择一个单词

Shift + ↑： 向上选择一行

home： 光标跳至行首

home： 光标跳至行尾

Shift + home： 选择光标至行首

Ctrl + home： 光标跳至文章开头

Ctrl + Shift + home：选择光标至文章开头

Alt + ↑： 将当前行与上一行交换

Alt + →： 在不同页面之间切换

Alt： 将聚焦点移动至菜单栏

Ctrl + 1： 跳至下一个问题行
### 创建
Ctrl + N： 新建文件

### 操作
Ctrl + Shift + F： 整理代码

Alt + /: 自动补全

Alt + Shift + S： 添加成员函数

Alt + Shift + Z： 添加控制流程语句（if，for，while，try catch等）必须先选定部分代码

Alt + Shift + X： 运行代码

### Debug
//TODO

## 重构（Refactor）
### Undo 
在一次重构后可执行 Alt + Shift + Z
### Redo 
在一次撤销重构后可执行 Alt + Shift + Y
### Rename 
重命名
### Move 
移动一个元素 
### Change Method Signature 
修改方法签名
### Convert Anonymous Class to Nested 
将匿名内部类变成嵌套类(静态内部类)
* 执行操作前
```java
JButton btn = new JButton("button");
//
class MyFrame extends JFrame{
	JButton btn = new JButton("button");
	public MyFrame() {
		btn.addActionListener(new ActionListener() {
			
			@Override
			public void actionPerformed(ActionEvent e) {
				System.out.println("使用匿名内部类响应");
			}
		});
	}
}
```
* 执行操作后
```java
class MyFrame extends JFrame{
	 static class MyActionListener implements ActionListener {
		@Override
		public void actionPerformed(ActionEvent e) {
			System.out.println("使用嵌套类响应");
		}
	}
	JButton btn = new JButton("button");
	public MyFrame() {
		btn.addActionListener(new MyActionListener());
	}
}
```
### Move Member Type to New File 
将嵌套类拿出来
### Push Down 
类中成员（方法）放到子类
### Pull Up 
类中成员（方法）放到父类
### Extract Interface 
使一个类继承自某个接口，并且选择一些方法让其成为覆盖方法
* 执行操作前
```java
class Circle{
	public void draw() {};
}
```
* 执行操作后
```java
interface Shape{
	void draw();
}

class Circle implements Shape{
	@Override
  public void draw() {};
	
}
```
### Extract superClass 
使一个类继承自某个类，并且选择一些方法让其成为覆盖方法
### Generalize Type 
将引用变为其父类，只能用在参数里
### Use Supertype Where Possible 
和上面一样，
### Inline 
内联，extract Local variable的反义词
* 执行操作前
```java
double area = Math.PI * radius * radius;
System.out.println(area);
```
* 执行操作后
```java
System.out.println(Math.PI * radius * radius);
```
### Extract Method 
将一段代码封装在一个方法中
* 执行操作前
```java
int[][] matrix = { { 1, 2 }, { 3, 4 } };
//需要多次遍历矩阵时可以将其封装成一个方法
for (int i = 0; i < matrix.length; i++) {
  for (int j = 0; j < matrix.length; j++) {
    System.out.print(matrix[i][j]+" ");
  }
  System.out.println();
}
```
* 执行操作后
```java
public static void main(String[] args) {
  int[][] matrix = { { 1, 2 }, { 3, 4 } };
  printMatrix(matrix);
}

private static void printMatrix(int[][] matrix) {
  for (int i = 0; i < matrix.length; i++) {
    for (int j = 0; j < matrix.length; j++) {
      System.out.print(matrix[i][j]+" ");
    }
    System.out.println();
  }
}
```
### Extract Local Variable 
将一段代码封装成一个局部变量
* 执行操作前
```java
System.out.println(Math.PI * radius * radius);
```
* 执行操作后
```java
double area = Math.PI * radius * radius;
System.out.println(area);
```
### Extract Constant 
将一段代码封装成一个常量
* 执行操作前
```java
System.out.println("127.0.0.1");
```
* 执行操作后
```java
private static final String LOCALHOST = "127.0.0.1";
System.out.println(LOCALHOST);
```
### Extract Class  
一个类做了两个类的事情，将相关字段，函数提炼出来
### Introduce Parameter 
未知
### Introduce Factory 
对构造方法可用，使用工厂创建一个对象
### Convert Local Variable to Field
将局部变量变为类成员
* 执行操作前
```java
class A {
	void f1() {
		int a;
	}
}
```
* 执行操作后
```java
class A {
	private int a;
	
	void f1() {}
}
```
### Encapsulate Field 
封装类成员
### Infer Generic Type Arguments 
重构会自动地为原始形式的那些类推测恰当的泛型类型：常被用于将 Java 5 以前的代码转换为 Java 5 或更新的代码

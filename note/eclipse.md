# Eclipse相关操作

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
将匿名内部类变成有名字的嵌套类
### Move Member Type to New File 
将嵌套类拿出来
### Push Down 
类中成员（方法）放到子类
### Pull Up 
类中成员（方法）放到父类
### Extract Interface 
使一个类继承自某个接口，并且选择一些方法让其成为覆盖方法
### Extract superClass 
使一个类继承自某个类，并且选择一些方法让其成为覆盖方法
### Generalize Type 将引用变为其父类，只能用在参数里
### Use Supertype Where Possible 
和上面一样，
### Inline 
内联，extract Local variable的反义词
### Extract Method 
将一段代码放进一个方法中，可以多次使用
### Extract Local Variable 
将一段代码变成一个局部变量
### Extract Constant 
将一段代码变成一个常量
### Extract Class  
一个类做了两个类的事情，将相关字段，函数提炼出来
### Introduce Parameter 
未知
### Introduce Factory 
对构造方法可用，使用工厂创建一个对象
### Convert Local Variable to Field
将局部变量变成类成员
### Encapsulate Field 
封装类成员
### Infer Generic Type Arguments 
重构会自动地为原始形式的那些类推测恰当的泛型类型：常被用于将 Java 5 以前的代码转换为 Java 5 或更新的代码

# 泛型
基本类型无法适用于泛型，比如参数，但是可以使用自动包装

T类的参数，泛型方法（T t）
?引用，做参数(Class<?> c)
T extends A
? extends A
用于extends的多个泛型之间不用（，）用 &
此时可以extends接口和类
基本类型不能作为模板，但是可以作为参数使用自动包装
Class<? extends T>可以向上转型，Collection<? extends T>也实现了容器上的向上转型，但是
内部操作的性质造成了无法赋值，class转型就完事了，collection还得判断类型，然后添加
擦除：
为什么不能声明类似于ArrayList<String>.class之类的
因为为了与raw type兼容，泛型用擦除来实现，编译器在传入参数的时候进行类型检查，return的时候进行转型
运行时无法知道任何与类型消息有关的信息，等价于Object，不能执行运行时操作，如
new（编译器不知道T有没有默认构造器），T的方法，instanceof，转型
? extends Apple 容器不能添加，内部的对象全部使用Apple引用
? super Apple 可以添加Apple的子类，读出时当做Object
两种形式都可以直接使用Array.asList方法将容器进行向上转型，但是无法修改容器的尺寸
*****************异常*********************
*****************并发*********************
用lambda表达式的开启新线程的方法
new Thread(() -> System.out.println("hello world")).start();

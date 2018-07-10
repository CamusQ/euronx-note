# 反射
forName要用包名.类名

RTTI（反射）使用基类的引用来检查（判定）引用所指的对象的实际派生类型

多态是隐式地利用RTTI，反射则是显式地使用RTTI 

正常方式创建对象：知道类，然后创建对象，获得方法
通过反射：有了对象，获取类，获得方法
使用类之前的准备工作：
1、加载：查找字节码（class文件）将其读入内存，创建class对象（此步骤通过类加载器完成）
2、为静态域分配空间，全部为0
3、如果存在超类，则对超类重复上述步骤
4、在发生静态调用（构造器，方法，域）的时候对类进行初始化（编译器常量static final不算）（JVM完成）

代码编译完生成一个class文件，在需要的时候加载到内存中，这就是一个运行时类，其本身就是一个class对象（class对象被保存在同名的class文件中）
JVM使用类加载器加载类
利用newInstance初始化对象，需要对象拥有默认构造器,且权限要足够大（包权限或public）
实际上newInstance方法就是调用了默认构造器
如果通过反射创建子类对象，子类对象也需要通过默认构造器创建父类对象
.class 方式创建对象不用初始化对象，forName需要。
获取类属性（方法）的时候，属性（方法）必须是public的，或者加Declared（私有，包可见）和setAccessable（私有可访问），一半保险起见两个都加上
getFields可以获得自己及其父类的公共属性
getDeclaredFields可以获得自己的所有属性
也可以通过class对象的getClassLoader方法获取类加载器，然后通过加载器创建对象
通过反射可以获得类的属性，方法，构造器，内部类，父类，所在的包，异常注解
并且可以调用构造器，属性，方法
反射的invoke方法具有返回值，返回的是被调用方法的返回值，void方法返回null
invoke静态方法时，参数写当前类的class类
Proxy.newProxyInstance方法的第二个参数是代理生成的类需要实现的接口
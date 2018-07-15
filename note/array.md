# 数组
数组标识符只是一个引用，指向在堆中创建的真实对象，成员`length`是数组对象的一部分

对象数组保存的是对象的引用，所以可以在每次使用

## 数组与泛型
通常泛型和数组无法一起使用，因为擦除会移除参数信息，而数组必须知道所持有的具体类型

无法创建泛型数组，但是可以创建泛型数组引用
```java
List<String>[] ls;
```
利用反射获取泛型数组

## Arrays常用功能
* 填充数组`Arrays.fill()`
```java
int[] i = new int[7];
Arrays.fill(i, 47);
print("i = " + Arrays.toString(i));
/* Output:
i = [47, 47, 47, 47, 47, 47, 47]
```
* 复制数组`System.arraycopy()`

System.arraycopy(Object src, int srcPos, Object dest, int destPos, int length）

从src的srcPos开始，复制length个元素到，dest的destPos处往后
```java
int[] j = new int[10];
Arrays.fill(j, 99);
print("j = " + Arrays.toString(j));
System.arraycopy(i, 0, j, 0, i.length);
print("j = " + Arrays.toString(j));
/* Output:
j = [47, 47, 47, 47, 47, 47, 47, 99, 99, 99]
```

* 比较数组

重载过的`equels()`方法比较整个数组，元素个数相等，对应位置元素也相等

* 数组排序`Arrays.sort()`
```java
Arrays.sort(T[] a, Comparator<? super T> c)
```
方法可以对对象数组使用定制排序
* 数组查找`Arrays.binarySearch()`

对于已经排序好的数组可以查找，若是未排序，则结果不可预测

返回：自然数，当查找到结果时。负数，未查找到结果，该负数为假设存在该值，返回-（该值位置） - 1

* 返回指定数组内容的字符串表示形式 `toString()`

`deepToString()`用于返回多维数组内容的字符串表示形式

对于多维数组使用toString，将返回每个一维数组的`hashCode`




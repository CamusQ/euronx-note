# 数组
对于多维数组使用toString，将返回每个一维数组的hash，因该用deepToString
无法实例化具有参数类型（T）的数组，因为擦除会移除参数信息，而数组本身必须知道具体类型信息
System.arrayCopy()可以对数组进行复制
System.arraycopy(Object src, int srcPos, Object dest, int destPos, int length）
从src的srcPos开始，复制length个元素到，dest的destPos处往后

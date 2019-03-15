# 基础类库

## 一、包装类（包裹类  Wrapper）

Java针对八种基本数据类型提供了对应的包装类

    基本数据类型           包装类    
    byte                  Byte
    short                 Short
    int                   Integer
    long                  Long    
    float                 Float    
    double                Double    
    char                  Character    
    boolean               Boolean

### 1.1 基本数据类型与包装类之间的转换

装箱：将基本数据类型转换成对应的包装类

①通过对应包装类的构造器

②通过对应包装类的静态方法 valueOf()

拆箱：将包装类转换成对应的基本数据类型

①通过对应包装类  xxxValue() 方法。   xxx:表示基本数据类型

### 1.2 自动装箱和自动拆箱


    int i = 10;
    Integer num = i; //自动装箱
    int i1 = num; //自动拆箱

    注意： Integer提供了一个小的缓存（-128~127）之间，若需要装箱的值在该取值范围内
           则从缓存中取一个实例。若超出该取值范围则重新 new 一个 Integer 实例
    
    Integer num1 = 100;
    Integer num2 = 100;
    System.out.println(num1 == num2);//true
    Integer num3 = 129;
    Integer num4 = 129;
    System.out.println(num3 == num4); //false

### 1.3 基本数据类型、包装类  与  String之间的转换

 1.基本数据类型、包装类  转  String

   ① String str = i + "";

   ② 使用 String 类的静态方法  valueOf()

   ③ 通过对应包装类的静态方法 toString()

 2.String 转  基本数据类型、包装类

   ① 通过对应包装类的构造器
   
   ② 通过对应包装类的静态方法 parseXxx() : Xxx :表示基本数据类型

   ③ 通过对应包装类的静态方法  valueOf()

    注意：没有parseChar()

## 二、String类

### 2.1 定义

java.lang.String  类： 不可变的字符序列

    String str1 = "abc";
    String str2 = new String("abc");

二者之间的区别？

str1 : 代表一个对象，至少在内存中开辟一块内存空间

str2 : 代表两个对象，至少在内存中开辟两块内存空间


### 2.2 String 类的常用方法

 1. 获取字符串的方法：

①

    String concat(String str)：串接字符串

②

    String substring(int beginIndex)：获取取字符串的子串
    
    String substring(int beginIndex, endIndex) : 包含头不包含尾

③
   
    String toLowerCase()和String toUpperCase()：转换为小写/大写
   
④

    String trim()：删除首尾空格或制表符

 2. 搜索方法：

①

    int indexOf(int ch) : 获取指定字符在字符串中的位置,若没有指定的字符，返回 -1

    int indexOf(int ch, int fromIndex) : 从指定位置开始搜索
   
    int indexOf(String str)

    int indexOf(String str, int fromIndex)

    int lastIndexOf(int ch) : 反向获取指定字符位置

 3. 判断方法：

① 

    boolean equals(Object obj)：判断是否相等

    boolean equalsIgnoreCase(String str)：判断是否相等,不考虑大小写

② 

    boolean contains(String str) :判断是否包含某字符串

③ 

    boolean startsWith(String str)和 boolean endsWith(String str)：判断是否以指定字符串开始/结尾
  
④ 
  
    boolean isEmpty():判断字符串是否为空
  
 4. 其它方法：

①

    length()：返回字符串长度

②

    char charAt(int index):返回索引处的字符

③将字符数组转换为字符串
  
    构造器：
         String(char[] ch)
         String(char[] ch, offset, count) : 将数组中一部分转换为字符串
    
    静态方法：
           static String copyValueOf(char[] ch)
           static String copyValueOf(char[] ch, offset, count)
           static String valueOf(char[])
    
    将字符串转换字符数组: char[] toCharArray()

④

    String replace(char oldCahr, char newCahr) ： 替换字符串中字符

    String replace(String oldStr, String newStr)：替换字符串中字符串

⑤

    String[] split(String r):根据指定符号切割

## 三、StringBuffer 和 StringBuilder

StringBuffer 和 StringBuilder : 可变的字符序列，二者具备相同的API

StringBuffer 和 StringBuilder 的区别？

    StringBuffer : 是线程安全的，因此效率低
    
    StringBuilder ： 是线程不安全的，因此效率高

StringBuffer 和 StringBuilder 的常用方法：

 ① 

    StringBuffer append(String str) : 添加

    StringBuffer insert(int offset, String str) ： 插入
    
    StringBuffer replace(int start, int end, String str)：替换
 
 ② 
 
    int indexOf(String str) ：返回子串的位置索引
    
    int lastIndexOf()

 ③ 

    String substring(int start, int end)：取子字符串序列

 ④ 

    StringBuffer delete(int start, int end)：删除一段字符串 

    StringBuffer deleteCharAt(int index):删除指定位置字符

 ⑤ 

    String toString()：转换为String对象

## 四、其他常用类

    1、java.util.Date : 表示特定的瞬间，精确到毫秒

   
    2、java.text.DateFormat : 用于格式化时间/日期。但是是一个抽象类

    |---java.text.SimpleDateFormat : 是 DateFormat 的子类

    SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss E");
    
    String strDate = sdf.format(date);
    
    System.out.println(strDate);//2015-12-07 09:23:37 星期一
    
    Date newDate = sdf.parse(strDate);
    
    System.out.println(newDate);

    
    3、java.lang.Math : 用于操作数学运算

    double ceil(double d) : 返回不小于d的最小整数
    
    double floor(double d): 返回不大于d的最大整数
    
    int round(float f) : 返回最接近f的int型（四舍五入）
    
    long round(double d):返回最接近d的long型
    
    double abs(double d): 绝对值
    
    double max(double d1, double d2) : 返回较大值
    
    int min(int i1, int i2) :　返回较小值
    
    double random() : 返回一个大于等于0.0并且小于1.0的随机数

## 五、了解部分

    java.lang.System : 系统类
    
    java.util.Calendar : 日历类
    
    java.math.BigInteger : 支持任意精度的整数
    
    java.math.BigDecimal : 支持任意精度的小数





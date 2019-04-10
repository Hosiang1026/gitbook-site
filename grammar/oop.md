# 面向对象（OOP）

## 一、面向对象编程

### 1.1 面向对象和面向过程

**面向过程：**强调的是功能行为

**面向对象：**将功能行为封装进对象，强调的是具备了功能行为的对象

（理解）把大象装冰箱一共分几步？

①打开冰箱   ②把大象装进去（存储大象）  ③关闭冰箱

如何使用面向对象思想思考上述问题呢？

    人｛
        拉（冰箱）｛
            冰箱.打开（）   
        ｝
        指挥（动物）｛
            动物.进入（）   
        ｝
    
        推（冰箱）｛
            冰箱.关闭（）
        ｝
    ｝
    冰箱｛
        打开（）｛｝
        存储（）｛｝
        关闭（）｛｝
    ｝
    大象｛
        进入（）｛｝
    ｝
    猴｛
        进入（）｛｝
    ｝
    狮子｛
        进入（）｛｝
    ｝

面向对象更加注重前期的设计

①就是对类的设计

②设计类就是设计类的成员：属性  &  方法

面向对象：将现实生活中一类事物的共性内容进行提取，抽象成相应Java类，用Java中类对其进行描述

现实生活中的事物：  小猫   小狗  大象

共性内容： 名称   性别   年龄    吃饭的功能    睡觉的功能

    class Animal{
        //属性
        String name;
        char gender;
        int age;
        //方法-行为   
        public void eat(){
            System.out.println("吃饭");
        }
        public void sleep(){
            System.out.println("睡觉");
        }
    }

若需要具体到某一个事物，通过  new 关键字创建对象

    Animal a1 = new Animal(); //
    a1.name = "大象";
    a1.gender = '男';
    a1.age = 2;
    a1.eat();
    a1.sleep();
    System.out.println(a1.name + "," + a1.age);

### 1.2 类和对象

类：对现实生活中一类事物的描述，抽象的

对象：是一个实实在在的个体

### 1.3 属性

属性：也叫成员变量，也叫实例变量

成员变量  &  局部变量 的区别？

①作用域不同

②内存中的位置不同

③成员变量有默认值，而局部变量没有默认值（局部变量使用前必须赋初始值）

成员变量的默认值：

基本数据类型：

    byte short int ---> 0
    long ---> 0L
    float ---> 0.0F
    double ---> 0.0D
    char ---> '\u0000'
    boolean ---> false
    
引用数据类型： 

    |---> null
    |-- 类(class)
    |-- 接口(interface)
    |-- 数组([])

2.为属性赋初始化值的方式

①使用默认值

②直接显示赋值

### 1.4 参数的值传递

基本数据类型： 将基本数据类型作为参数，传递给方法，方法运行结束后，原值不会发生改变

引用数据类型： 将引用数据类型作为参数，传递给方法，方法运行结束后，原值会发生改变

内存管理：

分配： JVM自动为其分配内存空间

释放：JVM通过垃圾回收机制自动的释放内存空间

垃圾回收机制： 将内存中的垃圾对象释放

垃圾对象：不再被任何引用指向的对象

    Person p = new Person();
    p  = null;
    System.gc(); //通知垃圾回收机制可以释放内存，但是并不能保证立即释放，加快释放。

## 二、面向对象的特性之一：封装性

封装的理解： 该隐藏的隐藏起来，该暴露的暴露出来

访问控制修饰符：

public ： 公共的，可用于修饰属性、方法、类。  在任何地方都可以访问

private ： 私有的，可用于修饰属性、方法。 只能在本类中访问


封装的步骤：

①属性私有化（private）

②提供公共的（public） get/set 方法

    class Animal{
        //1.
        private String name;
        private int legs; //描述腿的个数
        //2.
        public void setName(String n){
            name = n;
        }
        public String getName(){
            return name;   
        }
        public ovid setLegs(int l){
            if(l > 0 &&  l <= 4){
                legs = l;
            }
        }
        public int getLegs(){
            return legs;   
        }
    }

    Animal ani = new Animal();
    ani.name = "大象";
    ani.legs = -1000;
    一、this 关键字：使用在本类中，代表当前对象。可以用于调用属性、方法、构造器
    this.属性
    this.方法
    this(……)：

①this调用本类构造器，必须写在构造器中可执行代码的首行

②若一个类中有多个构造器，至少有一个构造器中不使用this (避免递归构造器调用)

谁让拥有this关键字的方法运行，谁就是当前对象

    class Person{
        private String name;
        private int age;
        public void setName(String name){
            this.name = name;//可以区分局部变量和成员变量
        }
    }
    Person p = new Person();
    p.setName("张三");

### 2.1 构造器

构造器：也叫构造器方法，是类的成员之一。

    属性

    方法

    构造器

1. 构造器的格式


    访问控制修饰符  类名(参数列表){
        //初始化语句
    }

2. 构造器的作用

①创建对象

②为对象进行初始化

3. 构造器的注意：

①构造器的名称必须与类名一致！

②若一个类中没有显示提供任何构造器，系统会自动提供一个默认无参构造器

    public Person(){}

③若一个类中显示的提供了任何构造器，系统默认构造器将不再提供

④构造器只能调用一次，并且是在创建对象时调用

4. 构造器的重载

①构造器的名称必须相同

②构造器的参数列表必须不同（参数的个数、参数的类型）

5. 为属性赋初始值的方式

①使用默认赋值

②直接显示赋值

③构造器

顺序：①②③

    class Person{
        private String name;
        private int age;
        private char gender;
        public Person(){
            cry();   
        }
        public Person(String name){
            this.name = name;
        }
        public Person(String name, int age){
            this(name);
            this.age = age;
        }
        public Person(String name, int age, char gender){
            this(name, age);
            this.gender = gender;
        }
        public void setName(String name){
            this.name = name;//可以区分局部变量和成员变量
        }
        public void cry(){
            System.out.println("哭");   
        }
    }

    Person p = new Person("张三");
    //p.cry();
    Person p1 = new Person();
    //p1.cry();

### 2.2 包

包的作用：

①用于区分重命名

②用于控制访问权限

③用于划分项目的结构层次，通常将功能相近的类划分到同一个包中。

package : 用于确定当前类的位置

①使用在当前 .java 源文件可执行代码的首行

②包的命名规范：所有字母都小写。 （通常将所在公司域名的倒置）

      如：  com.atguigu.项目名.模块名;

③每个“.”代表一层目录

import :　用于确定需要引入那个类的位置

①使用在 package 和  class 之间

②可以有多条，并排列出

③ import com.atguigu.aaa.* :    代表导入 aaa 包中所有的类或接口。 注意：包除外

④ 若在一个类中使用了两个相同类名不同包名的两个类。 

      如： java.util.Date;   java.sql.Date;
      
      选择一个使用导入的方式：  import java.util.Date;
      
      选择另外一个使用全限定类名（全类名）的方式：  java.sql.Date date = new java.sql.Date();
       
⑤静态导入：
   
    import static com.atguigu.aaa.StaticClass.*; // 导入一个类中所有的静态内容


## 三、面向对象的特性之二： 继承

### 3.1 继承

1. 为什么使用继承

①提高代码的复用性

②提高维护性

③有了继承让类与类之间产生了关系，能够创建出更加特殊的类型（多态）

2. 如何使用继承

    关键字： extends  -----  "扩展"  明确子类是父类的扩展

        如：
            class A extends B{
            }
    
            子类： A   父类(超类、基类、SuperClass)：B

3. 通过继承，子类可以继承父类中所有的属性和方法。（包括私有的）

    私有的属性也会被继承，但是因为 private 修饰符的作用，子类不能直接访问
    需要通过 公共的 get / set 方法进行访问

4. 继承的注意：

    ①不能为了简化代码，获取某功能而继承，若要完成继承两个类之间要有一定的所属关系：is a

    ②Java只支持单继承，不支持多继承。（一个父类可以有多个子类，但是一个子类只能有一个父类）

    ③Java支持多层继承。

        class A{
            void test1(){}
            void test2(){}
        }
        
        class B extends A{
            //void test1(){}
            //void test2(){}
        }
      
      -------------------------------------
      
        class A{
            void test1(){
                //111111111111
            }   
        }
        
        class B{
            void test1(){
                //22222222222
            }
        }
        class C extends A, B{}
        C c  = new C();
        c.test1();

### 3.2 方法的重写：

当父类中的方法对于子类来说不适用的情况下，子类可以对父类中方法进行“重写”

前提： 要有继承关系，使用在子类中

①方法名和参数列表必须相同

②返回值类型可以不同，但是有规则（若重写方法返回值类型是父类被重写方法返回值类型的子类）

③子类重写方法的访问控制修饰符不能小于父类被重写方法的访问控制修饰符

【面试题】 

    Override 和 Overload 的区别？

### 3.3 super 和 this

super 和 this 的使用方式完全一致！

this : 使用在本类中，代表当前对象的引用

super ： 使用在子类中，代表父类对象的引用

super.属性

super.方法

super(……); 调用父类构造器

    ①当子类继承父类后，子类“所有”构造器中默认第一行第一句都有一句： super()

       super : 当子类继承父类后，子类继承父类中所有的属性和方法，子类需要知道父类如何为对象进行初始化
        
    ②若父类中没有提供无参构造器，子类“所有”构造器中必须显示调用父类有参构造器
        （无论如何必须保证创建子类对象前，先初始化父类）

    ③super() 调用父类构造器，必须写在构造器中可执行代码的首行

        因此，this() 和 super() 不能同时出现

### 3.4 访问控制修饰符

四种访问控制修饰符

public : 公共的，可用于修饰 属性、方法、类。  在任何地方都可以使用

protected: 受保护的，可用于修饰 属性、方法。  可以在 本类中、本包中、子类中

default : 默认的（缺省的） ，可用于修饰 属性、方法、类。 可以在 本类中、本包中

private : 私有的，可用于修饰 属性、方法。  只能在 本类中 使用

    注意：default 并不是访问控制修饰符的关键字，在什么都不加的情况下就是 default

## 四、面向对象的特性之三：多态 

### 4.1 多态的概念

多态：一类事物的多种表现形态。

人 - 男人  女人 

1. 多态的体现： 

①方法的重载与重写     

②对象的多态性

2.对象的多态性：父类的引用指向子类的对象

    Person p = new Man(); // 多态-向上转型
    p.eat();
    p.walk(); //虚拟方法调用
    //p.smoking();
    Man man = (Man)p; //向下转型
    man.smoking();

    Java程序的运行分为两种状态：

    在多态的情况下，编译时, “看左边”，看的是父类的引用（父类中不具备子类特有的方法）

                运行时，“看右边”，看的是子类对象，实际运行的是子类重写父类的方法

                ———— 以上过程被称为“虚拟方法调用（动态绑定）”

3. 多态的前提：①要有继承关系  ②方法的重写（完成虚拟方法调用）

4. 引用数据类型之间的转换：

前提：要有继承关系

向上转型： 子类转父类。系统自动完成转换

向下转型： 父类转子类。需要使用强转符 “(需要转换的类型)”

    可能引发  java.lang.ClassCastException

    Person p = new Man();
    Woman woman = (Woman)p; //编译？ YES       运行？ NO

5. Java 为了解决上述问题，提供了相应的解决办法

instanceof 运算符：

如：
p instanceof Man :  判断 p 引用指向的对象是不是 Man 的本类类型及 Man 的子类类型，如果是返回 true

    Person p = new Man();
    if(p instanceof Woman){
        Woman woman = (Woman)p;   
    }       

### 4.2 多态的应用

多态的应用之一：多态数组

    Person[] persons = new Person[3];//该多态数组中可以存放Person本类类型的对象及Person子类类型的对象
    persons[0] = new Person();
    persons[1] = new Man();
    persons[2] = new Woman();
    for(int i = 0; i < persons.length; i++){
        persons[i].eat();//虚拟方法调用
    }

多态的应用之二： 多态参数

    //需求：展示一个男人吃饭和走路的功能
    
    /*public void show(Man man){
        man.eat();
        man.walk()
    }
    
    public void show(Woman woman){
        woman.eat();
        woman.walk();
    }*/
    
    public void show(Person p){ //多态参数：当调用方法时，可以传递Person本类类型的对象及Person子类类型的对象
        p.eat();
        p.walk();//虚拟方法调用
        if(p instanceof Man){
            Man man = (Man)p;
            man.smoking();
        }
    }



一、对象的关联：简单的说，是指一个对象中使用了另一个对象

    class Teacher｛
        String name;
        int age;
        Computer com;
    ｝
    
    class Computer{
        String cpu;
        String ram;
        String hdd;
    }

二、java.lang.Object 类： 是所有类的父类。若一个类没有显示的 extends 任何类时，默认的 extends java.lang.Object

①既然 java.lang.Object 类是所有类的父类，那么Object类中的内容是最具共性的，所有类都适用

②既然 java.lang.Object 类是所有类的父类，那么Object类中方法都会被“继承”

③既然 java.lang.Object 类是所有类的父类，若Object类中的方法对于子类来说不适用，子类可以重写Object类中的方法

1. public boolean equals(Object obj) : 用于比较当前对象与参数对象是否相等

    ①在 java.lang.Object 类中

    ②只能比较引用数据类型是否相等

    ③Object类中的equals方法比较两个对象的地址值。（通过查看源代码发现实际上使用 == 完成）

    ④若Object类中的equals() 方法对于我们来说不适用，我们可以重写 Object类中 equals()

“==”运算符：

    基本数据类型： 比较两个基本数据类型的值是否相等，若相等返回 true

    引用数据类型： 比较两个引用数据类型的地址值是否相等，若相等返回 true

    class Person /* extends java.lang.Object*/{
        String name;
        int age;
        public Person(){}
        public Person(String name, int age){
            this.name = name;
            this.age = age;
        }
    
        //重写
        public boolean equals(Object obj){
            if(this == obj){
                return true;
            }
            if(obj instanceof Person){
                Person p = (Person)obj;
                if(this.name.equals(p.name) && this.age == p.age){
                    return true;
                }
            }
            return false;
        }
        public String toString(){
            return "姓名：" + name  + “年龄：” + age;   
        }
    }

    //需求：若两个人的姓名年龄都一样，视为同一个人
    
    Person p1 = new Person("张三", 18);
    
    Person p2 = new Person("张三", 18);
    
    System.out.println(p1.equals(p2)); //重写equals之前- false----重写后：true
    
    System.out.println(p1);
    
    System.out.println(p1.toString());

2. public String toString() : 返回当前对象的字符串表现形式

    ①在 java.lang.Object 类中

    ②Object类中的toString方法返回的格式为：

    getClass.getName() + '@' + Integer.toHexString(hashCode());
          
    因此，Object类中的toString() 方法对于我们来说不适用，我们可以重写toString()   
    
    ③当直接输出对象的引用时，默认调用 toString();   
            
一、static 修饰符：代表静态的，可用于修饰 属性、方法、代码块、**内部类

1. static 修饰的属性（静态变量或类变量）

①随着类的加载而加载，随着类的消失而消失（生命周期最长）

②静态变量被该类所有对象所共享

③一旦某个对象修改该属性值，其他对象也会随之改变

④静态变量的存在优先于对象

⑤可以通过 “类名.类变量”的方式调用

2. static 修饰的方法（静态方法或类方法）

①随着类的加载而加载

②静态方法的存在优先于对象

③通过“类名.类方法”的方式调用

④静态方法中不能调用非静态成员，非静态方法中可以调用静态成员

⑤静态方法中不能使用 this 和 super

3. 类变量和实例变量的区别？

①生命周期不同

②内存中的位置不同

二、类的成员之一： 代码块

非静态代码块：

①格式： 类的一对 { }

②每次创建对象时执行

③非静态代码块的执行优先于构造器

④用于为对象进行初始化。（通常为共性内容进行初始化）

⑤代码块可以有多个，依次向下的顺序执行

静态代码块：

①格式：static{ }

②随着类的加载而加载，并且只加载一次

③静态代码块的执行优先于非静态代码块

④静态代码块中不可以调用非静态成员

⑤静态代码块可以有多个，依次向下的顺序执行

三、final 修饰符： 代表最终的，可用于修饰 变量、方法、类。

final 修饰的类不能被继承

final 修饰的方法不能被重写

final 修饰的变量叫常量，一旦被赋值，值不能改变

①常量的命名规范：所有字母都大写，每个单词之间以 "_" 分隔

②常量没有默认值，因此在使用前必须为常量赋初始值

   赋值方式（直接显示赋值、构造器、代码块）

   若选择使用构造器为常量赋值，必须保证“所有”构造器都为该常量赋值           




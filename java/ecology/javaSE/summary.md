# 发展概述

## 一、介绍

Java由SUN公司研发，SUN 被 Oracle 收购

Java 由1995年发布，正式版本由1996年1月发布（jdk1.0）

Java之父： James Gosling

## 二、特点

* 面向对象

* 分布式

* 多线程

* 简单化

* 安全

* 跨平台移植  ------    JVM   Java Virtual Machine Java虚拟机

## 三、版本分类

JavaSE  Java Standard Edition : Java标准版本

JavaEE Java Enterprise Edition ： Java企业版本

JavaME Java Micro Edition ： Java微型版    ----------------  Android

## 四、搭建开发环境

### 4.1 组成

JVM   Java Virtual Machine Java虚拟机 ： 用于与操作系统进行交互

JRE   Java Runtime Enviroment Java运行环境： JVM  +    Java核心类库

JDK  Java Development Kit Java开发工具包 ： JRE  +  Java开发工具集（java.exe  javac.exe  javadoc.exe）

### 4.2 使用

①下载安装JDK

②通过命令提示符到JDK安装路径的bin路径下，执行 javac

③配置path环境变量：JDK安装路径的bin路径下
        流程：先在当前路径下找是否有 javac.exe，若没有再到 path 环境变量中从前往后依次查找
        目的：在任意路径下执行 javac  
 
④JAVA_HOME :  JDK安装根路径

## 五、开发应用程序

### 5.1 步骤：

①创建一个 .java 结尾的文件，被称为 java源文件。 如：  【HelloWorld.java】
    public class HelloWorld{
        public static void main(String[] args){
            System.out.println("HelloWorld！");
        }
    }

②编译： 通过 javac + 源文件名称 命令进行编译， 生成一个或多个 .class 字节码文件。 如：【javac HelloWorld.java】

③运行： 通过 java + .class 字节码文件名 命令进行运行。（JVM会将一个或多个.class 字节码文件加载到内存中）。  如：【java HelloWorld】

### 5.2 开发第一个应用程序的注意：

①以  .java 结尾的文件，被称为 java源文件。

②一个 .java 源文件中可以有多个类，但是，只能有一个 public 修饰的类

③public 修饰类的名称必须与 .java 源文件名称一致

④每条语句以 “;” 结束

⑤Java 严格区分大小写

## 六、注释语句

注释语句: 不会被JVM解释执行的语句

    //单行注释
    
    /*
      多行注释：不能嵌套
    */
    
    /**
        文档注释： 可以通过  javadoc -d mydoc -author -version HelloWorld.java 命令生成说明文档
    */





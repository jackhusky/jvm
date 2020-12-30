# Class文件结构

## 概述

### 字节码文件的跨平台型

1. Java语言：跨平台的语言（write once，run anywhere）

- 当Java源代码成功编译成字节码后，如果想在不同的平台上面运行，则无需再次编译。
- 这个优势不再那么吸引人了。Python、PHP、Perl、Ruby、Lisp等有强大的解释器。
- 跨平台似乎已经快成为一门语言必选的特性。

2. Java虚拟机：跨语言的平台

​    Java虚拟机不和包括Java在内的任何语言绑定，它只与“Class文件”这种特定的二进制文件格式所关联。

![java虚拟机跨语言的平台](https://github.com/jackhusky/jvm/blob/main/docs/images/java虚拟机跨语言的平台.png)

3. 想要让一个Java程序正确地运行在JVM中，Java源码就必须要被编译为符合JVM规范的字节码。

- 前端编译器的主要任务就是负责将符合Java语法规范的Java代码转换为符合JVM规范的字节码。
- javac是一种能够将Java源码编译为字节码的前端编译器。
- javac编译器在将Java源码编译为一个有效的字节码文件过程中经历了4个步骤，分别是**词法解析、语法解析、语义解析以及生成字节码**。

![源码编译](https://github.com/jackhusky/jvm/blob/main/docs/images/源码编译.png)

Oracle的JDK软件包括两部分内容：

- 一部分是将Java源代码编译成Java虚拟机的指令集的编译器。
- 另一部分是用于实现Java虚拟机的运行时环境。

### Java的前端编译器

javac是一种能够将Java源码编译为字节码的前端编译器。

除了javac之外，还有Eclipse中的ECJ（Eclipse Compiler for Java）编译器。和javac的全量编译不同，ECJ是一种增量式编译器。

### 透过字节码指令看代码细节



## 虚拟机的基石：Class文件



## Class文件结构



## 使用javap指令解析Class文件
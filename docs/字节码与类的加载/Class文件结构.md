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

## 虚拟机的基石：Class文件

- 字节码文件里是什么？

源代码经过编译器编译后便会生成一个字节码文件，字节码是一种二进制的类文件，它的内容是JVM的指令，而不像C、C++经由编译器直接生成机器码。

- 什么是字节码指令？

Java虚拟机的指令由一个字节长度的、代表着某种特定操作含义的操作码（opcode）以及跟随其后的零至多个代表此操作所需参数的操作数（operand）所构成。虚拟机中许多指令并不包含操作数，只有一个操作码。

- 如何解读供虚拟机解释执行的二进制字节码？

方式一：一个一个二进制的看。使用Notepad++，安装一个HEX-Editor插件，或者使用Binary Viewer。

方式二：使用javap指令：jdk自带的反解析工具。

**方式三：**使用IDEA插件：jclasslib 或者 jclasslib bytecode viewer客户端工具。



## Class文件结构



## 使用javap指令解析Class文件
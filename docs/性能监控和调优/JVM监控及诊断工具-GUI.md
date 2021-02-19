# JVM监控及诊断工具-GUI

## 工具概述

- JDK自带的工具
  - jconsole：JDK自带的可视化监控工具。查看Java应用程序的运行概况、监控堆信息、永久代（或元空间）使用情况、类加载情况等
  - Visual VM：提供了可是界面，用于查看Java虚拟机上运行的基于Java技术的应用程序的详细信息。
  - JMC：Java Mission Control，内置Java Flight Recorder。能够以极低的性能开销收集Java虚拟机的性能数据。
- 第三方工具
  - MAT：基于Eclipse的内存分析工具，是一个快速、功能丰富的Java heap分析工具，它可以帮助我们查找内存泄漏和减少内存消耗
  - JProfiler：商业软件，需要付费。功能强大。
  - Arthas：Alibaba开源的Java诊断工具。
  - Btrace：Java运行时追踪工具。可以在不停机的情况下，跟踪指定的方法调用、构造函数调用和系统内存等信息。

## jConsole

### 基本概述

- 从JDK5开始，在JDK自带的java监控和管理控制台。
- 用于对JVM中内存、线程和类等的监控，是一个基于JMX（java management extensions）的GUI性能监控工具。

## Visual VM

### 基本概述

- 是一个功能强大的多合一故障诊断和性能监控的可视化工具。
- 集成了多个JDK命令行工具，使用Visual VM可用于显示虚拟机进程及进程的配置和环境信息（jps，jinfo），监视应用程序的CPU、GC、堆、方法区和线程的信息（jstat、jstack）等，甚至代替JConsole。
- Visual VM也可以作为独立的软件安装。

### 插件的安装

idea插件的安装、visualvm插件的安装

### 连接方式

#### 本地连接

监控本地Java进程的CPU、类、线程等

#### 远程连接

1. 确定远程服务器的ip地址
2. 添加JMX（通过JMX技术具体监控远端服务器哪个进程）
3. 修改bin/catalina.sh文件，连接远程的tocat
4. 在../conf添加jmxremote.access和jmxremote.password文件
5. 将服务器地址改为公网ip地址
6. 设置阿里云安全策略和防火墙cel
7. 启动tomcat，查看tomcat启动日志和端口监控
8. JMX中输入端口号、用户名、密码登录

### 主要功能

1. 生成/读取堆内存快照
2. 查看JVM参数和系统属性
3. 查看运行中的虚拟机进程
4. 生成/读取线程快照
5. 程序资源的实时监控
6. 其他功能（JMX代理连接、远程环境监控、CPU分析和内存分析）

## eclipse MAT

### 基本概述

MAT工具是一个款功能强大的Java堆内存分析器。可以用于查找内存泄漏以及查看内存消耗情况。

### 获取堆dump文件

#### dump文件内容

MAT可以分析heap dump文件。在进行内存分析时，只要获得了反应当前设备映像的hprof文件，通过MAT打开就可以直观地看到当前的内存信息。

一般来说，这些内存信息包含：

- 所有的对象信息，包括对象实例、成员变量、存储于栈中的基本类型值和存储于堆中的其它对象的引用值。
- 所有的类信息，包括classloader、类名称、父类、静态变量等
- GCRoot到所有的这些对象的引用路径
- 线程信息，包括线程的调用栈及此线程的线程局部变量（TLS）

#### 两点说明

1. 不是一个万能工具，并不能处理所有类型的堆存储文件，支持主流的厂家和格式。
2. 最吸引人的还是能够快速为开发人员生成内存泄漏报表，方便定位问题和分析问题。

#### 获取dump文件

1. jmap工具生成，可以生成任意一个java进程的dump文件
2. 通过配置参数生成
   - 选项`-XX:+HeapDumpOnOutOfMemoryError`或`-XX:+HeapDumpBeforeFullGC`
   - 选项`-XX:HeapDumpPath`表示当程序出现OOM时，将会在响应的目录下生成一份dump文件，若不指定该参数则在当前目录下生成dump文件
   - 考虑到生成环境中几乎不可能在线对其进行分析，大都是采用离线分析，因此使用jmap+MAT工具是最常见的组合。
3. 使用VisualVM可以导出dump文件
4. 使用MAT既可以打开衣蛾已有的堆快照，也可以通过MAT直接从活动Java程序中导出堆快照。

### 分析堆dump文件














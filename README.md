# 运筹OptaPlanner ortools使用教程源码分析技术文档总结

## 介绍
运筹OptaPlanner使用教程 ortools源码分析系列目录--持续更新中

## 专栏《[运筹OptaPlanner使用教程&& ortools源码分析系列目录](https://zhuanlan.zhihu.com/p/689625078)》

## 运筹业界动态

1.[如何了解运筹学的业界真实应用](https://zhuanlan.zhihu.com/p/711370820)

## optaplanner教程系列

1. [【OptaPlanner教程1】OptaPlanner介绍](https://zhuanlan.zhihu.com/p/671696505)
2. [【OptaPlanner教程2】Quarkus HelloWorldJava快速入门](https://zhuanlan.zhihu.com/p/673545787)
3. [【OptaPlanner教程3】Spring Boot Helloworld Java快速入门](https://zhuanlan.zhihu.com/p/673546312)
4. [【OptaPlanner教程4】Hello world Java 快速入门](https://zhuanlan.zhihu.com/p/673546859)
5. [【OptaPlanner教程6】OptaPlanner配置](https://zhuanlan.zhihu.com/p/673547869)
6. [【OptaPlanner教程7】 Drools评分计算](https://zhuanlan.zhihu.com/p/673735889)
7. [【optaplanner教程8】shadow阴影变量](https://zhuanlan.zhihu.com/p/673736216)
8. [【optaplanner教程9】OptaPlanner优化算法](https://zhuanlan.zhihu.com/p/706410092?just_published=2&is_recommend=1)
9. [【optaplanner教程10】OptaPlanner Exhaustive search穷举搜索](https://zhuanlan.zhihu.com/p/706411549)
10. [【OptaPlanner教程11】OptaPlaner构造启发式算法](https://zhuanlan.zhihu.com/p/720787005)
11. [【OptaPlaner教程12】OptaPlaner Partitioned Search](https://zhuanlan.zhihu.com/p/720788026)

## ortools系列

1. [【ortools源码系列1】ortools cp-sat cp_model Proto h头文件cpp源码分析](https://zhuanlan.zhihu.com/p/706463463)
2. [【ortools源码系列2】ortools cp-sat IntVar整数变量Long越界情况分类源码分析精讲](https://zhuanlan.zhihu.com/p/706464423)
3. [【ortools源码系列3】OR-TOOLS CentOS 7 Dockerfile如何给源码编译打镜像](https://zhuanlan.zhihu.com/p/706597791)
4. [【ortools源码系列4】ortools cp_model_presolve cp_model_postsolve model_solver用法功能源码分析](https://zhuanlan.zhihu.com/p/706599034)
5. [【ortools源码系列5】运筹工具Ortools MPSolver方法用法示例实战源码详解](https://zhuanlan.zhihu.com/p/706606673)
6. [【ortools源码系列6】ortools LinearExpr线性表达式方法示例实战源码分析](https://zhuanlan.zhihu.com/p/706673939)
7. [【ortools源码系列7】OR-Tools CP-SAT 整数规划用法示例源码详解](https://zhuanlan.zhihu.com/p/706674418)

## [【OptaPlanner教程1】OptaPlanner介绍](https://zhuanlan.zhihu.com/p/671696505/)

*源自专栏《[SparkML：运筹OptaPlanner使用教程系列目录](https://zhuanlan.zhihu.com/p/689625078)》*

## 1. 什么是OptaPlanner？

每个组织都面临着规划问题：在有限的资源（员工、资产、时间和金钱）的情况下提供产品或服务。OptaPlanner通过优化规划来用更少的资源做更多的业务。这被称为约束满足编程（是[运筹学](https://zhida.zhihu.com/search?q=运筹学&zhida_source=entity&is_preview=1)学科的一部分）。

OptaPlanner是一个轻量级的嵌入式约束满足引擎，用于优化规划问题。它解决以下用例：

- 员工排班：为护士、维修人员等制定时间表
- 日程安排：安排会议、约会、维护工作、广告等
- 教育时间表：安排课程、考试、会议演讲等
- 车辆[路径规划](https://zhida.zhihu.com/search?q=路径规划&zhida_source=entity&is_preview=1)：使用已知的地图工具规划车辆（卡车、火车、船只、飞机等）在多个目的地之间运输货物和/或乘客
- 装箱问题：将物品装入容器、卡车、船只和仓库，还可以将信息装载到计算机资源中，如云计算等
- 作业车间调度：规划汽车组装线、机器队列规划、工作任务规划等
- 裁剪材料：在裁剪纸张、钢铁、地毯等材料时尽量减少浪费
- 体育赛程安排：为足球联赛、棒球联赛等规划比赛和训练时间表
- 金融优化：投资[组合优化](https://zhida.zhihu.com/search?q=组合优化&zhida_source=entity&is_preview=1)、风险分散等



![img](https://pic3.zhimg.com/80/v2-2bb9b118247a54d88d1110182cc8350a_720w.jpg)

useCaseOverview



## 2. 什么是规划问题？



![img](https://picx.zhimg.com/80/v2-078e4276dbf83619305d25a08ad43775_720w.jpg)

whatIsAPlanningProblem

规划问题基于有限资源和特定约束条件具有最佳目标。最佳目标可以是任何事情，例如：

- 最大化利润-最佳目标产生最高可能的利润。
- 最小化生态足迹-最佳目标对环境影响最小。
- 最大化员工或客户的满意度-最佳目标优先考虑员工或客户的需求。

实现这些目标取决于可用资源的数量，例如：

- 人数。
- 时间量。
- 预算。
- 具体资源（例如机械设备、车辆、计算机、建筑物等）。

还必须考虑与这些资源相关的特定约束条件，例如一个人工作的小时数、他们使用某些机器的能力，或者设备之间的兼容性。

OptaPlanner帮助JavaTM程序员有效地解决约束满足问题。在底层，它将优化启发式算法和[元启发式算法](https://zhida.zhihu.com/search?q=元启发式算法&zhida_source=entity&is_preview=1)与非常高效的评分计算相结合。

### 2.1. 规划问题是NP完全或NP难的

上述所有用例可能都是NP完全/NP难的，这意味着以通俗的语言来说：

在合理的时间内验证给定问题的解决方案是很容易的。

找到一个问题的最佳解决方案在合理的时间内[没有银弹](https://zhida.zhihu.com/search?q=没有银弹&zhida_source=entity&is_preview=1)（*）。

（*）至少，世界上最聪明的[计算机科学家](https://zhida.zhihu.com/search?q=计算机科学家&zhida_source=entity&is_preview=1)还没有找到这样的银弹。但是，如果他们为一个NP完全问题找到了这样的银弹，那么它将适用于每个NP完全问题。

事实上，对于任何能够证明这样的银弹是否存在的人，都会有100万美元的奖励。

这带来的影响非常严重：解决您的问题可能比您预期的要困难，因为两种常见的技术都不足以解决：

- 蛮力算法（甚至更聪明的变体）需要太长时间。
- 例如，在装箱问题中，采用先放置最大的物品的[快速算法](https://zhida.zhihu.com/search?q=快速算法&zhida_source=entity&is_preview=1)将返回远离最优的解决方案。

通过使用先进的优化算法，OptaPlanner可以在合理的时间内找到接近最优的解决方案。

### 2.2. 规划问题具有（硬约束和软约束）

通常，规划问题至少具有两个级别的约束条件：

- 不能违反（负面）**硬约束**。例如：一个老师不能同时教授两个不同的课程。
- 如果可能的话，不应违反（负面）**软约束**。例如：A老师不喜欢在星期五下午上课。

有些问题也有正面约束：

- 如果可能的话，应满足（积极的）软约束。例如：B老师喜欢在星期一早上上课。

一些基本问题（如N皇后问题）只有硬约束。一些问题具有三个或更多级别的约束条件，例如硬约束、中等约束和软约束。

这些约束条件定义了规划问题的评分计算（也称为[适应度函数](https://zhida.zhihu.com/search?q=适应度函数&zhida_source=entity&is_preview=1)）。规划问题的每个解决方案都可以根据得分进行评估。使用OptaPlanner，评分约束以[面向对象语言](https://zhida.zhihu.com/search?q=面向对象语言&zhida_source=entity&is_preview=1)编写，例如JavaTM代码。这种代码易于编写、灵活且可扩展。

### 2.3. 规划问题具有巨大的搜索空间

规划问题有许多解决方案。有几个解决方案类别：

- 可能的解决方案是任何解决方案，无论是否违反任何数量的约束。规划问题往往有非常多的可能解决方案。其中许多解决方案是毫无价值的。
- 可行解决方案是不违反任何（负面）硬约束的解决方案。可行解决方案的数量与可能解决方案的数量相关。有时没有可行解决方案。每个可行解决方案都是一个可能解决方案。
- 最优解决方案是得分最高的解决方案。规划问题往往有1个或几个最优解决方案。至少存在一个最优解决方案，即使没有可行解决方案，最优解决方案也不可行。
- 找到的最佳解决方案是在给定时间内由实现找到的得分最高的解决方案。找到的最佳解决方案很可能是可行的，并且如果给予足够的时间，它将成为最优解决方案。

令人费解的是，即使是对于小数据集，可能的解决方案数量也是巨大的（如果计算正确）。正如您在示例中看到的，大多数实例比已知宇宙中最少数量的原子（10^80）具有更多的可能解决方案。由于没有银弹可以找到最优解决方案，任何实现都必须评估所有这些可能解决方案的至少一部分。

OptaPlanner支持多种优化算法，以高效地处理那些非常庞大的可能解决方案数量。根据使用情况，某些优化算法比其他算法表现更好，但事先无法预知。使用OptaPlanner，可以通过在几行XML或代码中更改求解器配置来轻松切换优化算法。

## 3. 要求

OptaPlanner是[开源软件](https://zhida.zhihu.com/search?q=开源软件&zhida_source=entity&is_preview=1)，根据Apache许可证2.0发布。该许可证非常自由，允许用于商业目的。阅读外行人的解释。

OptaPlanner是100%纯JavaTM，并在Java 11或更高版本上运行。它与其他JavaTM技术非常容易集成。OptaPlanner在Maven中央仓库中可用。

OptaPlanner适用于任何Java[虚拟机](https://zhida.zhihu.com/search?q=虚拟机&zhida_source=entity&is_preview=1)，并与主要JVM语言和所有主要平台兼容。

![img](https://pic3.zhimg.com/80/v2-2c698d1648d6d0138920998af0d621fe_720w.webp)

compatibility

## 4. 治理

### 4.1. OptaPlanner的状态

OptaPlanner稳定、可靠且可扩展。它经过了[单元测试](https://zhida.zhihu.com/search?q=单元测试&zhida_source=entity&is_preview=1)、集成测试和压力测试，并在全球范围内投入生产。一个例子处理超过50,000个变量，每个变量有5000个值，多种约束类型和数十亿个可能的约束匹配。

请参阅[发布说明](https://link.zhihu.com/?target=https%3A//www.optaplanner.org/docs/optaplanner/latest/release-notes/release-notes.html%23releaseNotes)，了解项目中最近活动的概述。

### 4.2. 向后兼容性

OptaPlanner将其API和实现分离：

- 公共API：包名空间org.optaplanner.core.api、org.optaplanner.benchmark.api、org.optaplanner.test.api和org.optaplanner.persistence…api中的所有类在未来版本（特别是小版本和热修复版本）中都是100%向后兼容的。在极少数情况下，如果主版本号发生更改，某些特定类可能会有一些不向后兼容的更改，但这些更改将在升级说明中明确记录。
- XML配置：XML求解器配置对于所有元素来说都是向后兼容的，除了需要使用非公共API类的元素。XML求解器配置由包[命名空间](https://zhida.zhihu.com/search?q=命名空间&zhida_source=entity&is_preview=1)org.optaplanner.core.config和org.optaplanner.benchmark.config中的类定义。
- 实现类：所有其他类都不具备向后兼容性。它们将在未来的主要或次要版本中进行更改（但可能不会在热修复版本中进行更改）。升级指南描述了每个相关变化及如何快速处理它们的变化。

本文档还涵盖了一些实现类。这些已记录的实现类是可靠且安全可用的（除非在本文档中明确标记为实验性），但我们还没有完全确定以确保其签名是固定的。

### 4.3. 社区和支持

获取最新消息和文章，请查看我们的[博客](https://link.zhihu.com/?target=https%3A//www.optaplanner.org/blog/)、Twitter（包括Geoffrey的Twitter）和Facebook。 如果您对OptaPlanner满意，请发推文或撰写博客文章，让我们感到高兴。

在此处欢迎公共问题。我们欢迎漏洞和功能请求在我们的问题跟踪器中。在GitHub上非常欢迎拉取请求，并享有优先处理！通过开源您的改进，您将从我们的同行评审和在您的改进基础上进行的改进中受益。

Red Hat通过雇佣核心团队赞助OptaPlanner的开发。有关企业支持和咨询，请查看这些服务。

### 4.4. 与KIE的关系

OptaPlanner是KIE项目组的一部分。它们定期发布（通常每3周）。

请参阅体系结构概述以了解与Drools的可选集成。

## 5. 下载并运行示例

### 5.1. 获取发布ZIP并运行示例

立即尝试：

1. 从[OptaPlanner网站](https://link.zhihu.com/?target=https%3A//www.optaplanner.org/)下载OptaPlanner的发布zip文件并[解压缩](https://zhida.zhihu.com/search?q=解压缩&zhida_source=entity&is_preview=1)。
2. 打开examples目录并运行脚本。

Linux或Mac：

```text
$ cd examples
$ ./runExamples.sh
```

Windows：

```text
$ cd examples
$ runExamples.bat
```



![img](https://pica.zhimg.com/80/v2-950e636bef3eae8024a0bd5084a22864_720w.webp)

distributionZip



示例GUI应用程序将打开。选择一个示例来尝试：



![img](https://pic2.zhimg.com/80/v2-491a87f3bb02ead41ceb659ed7f3025f_720w.webp)

plannerExamplesAppScreenshot

OptaPlanner本身没有GUI依赖关系。它在服务器或移动JVM上运行的效果与在桌面上运行的效果一样好。

### 5.2 在IDE中运行示例

要在IntelliJ IDEA、VSCode或Eclipse中运行示例：

1. 将文件`examples/sources/pom.xml`作为一个新项目打开，maven集成会处理剩下的事情。
2. 从项目中运行示例。

### 5.3 使用Maven、Gradle或ANT使用OptaPlanner

OptaPlanner的jar包可在中央maven仓库中找到（快照版本在JBoss maven仓库中）。

如果你使用Maven，在你的`pom.xml`文件中添加`optaplanner-core`的依赖：

```xml
<dependency>
  <groupId>org.optaplanner</groupId>
  <artifactId>optaplanner-core</artifactId>
  <version>...</version>
</dependency>
```

或者更好地，通过在`dependencyManagement`中导入`optaplanner-bom`来避免在添加其他optaplanner依赖时重复版本号：

```xml
<project>
  ...
  <dependencyManagement>
    <dependencies>
      <dependency>
        <groupId>org.optaplanner</groupId>
        <artifactId>optaplanner-bom</artifactId>
        <type>pom</type>
        <version>...</version>
        <scope>import</scope>
      </dependency>
    </dependencies>
  </dependencyManagement>
  <dependencies>
    <dependency>
      <groupId>org.optaplanner</groupId>
      <artifactId>optaplanner-core</artifactId>
    </dependency>
    <dependency>
      <groupId>org.optaplanner</groupId>
      <artifactId>optaplanner-persistence-jpa</artifactId>
    </dependency>
    ...
  </dependencies>
</project>
```

如果你使用Gradle，在你的`build.gradle`文件中添加`optaplanner-core`的依赖：

```groovy
dependencies {
  implementation 'org.optaplanner:optaplanner-core:...'
}
```

如果你仍在使用ANT，请将下载zip包中的`binaries`目录下的所有jar包复制到你的类路径中。

注意：下载的zip包中的`binaries`目录包含了远比`optaplanner-core`实际使用的jar包还要多。它还包含了其他模块使用的jar包，例如`optaplanner-benchmark`。查看maven仓库的`pom.xml`文件以确定`optaplanner-core`等的最小依赖集。

### 5.4 从源代码构建OptaPlanner

### 前提条件

- 设置Git。
- 使用HTTPS或SSH[身份验证](https://zhida.zhihu.com/search?q=身份验证&zhida_source=entity&is_preview=1)在GitHub上进行[身份认证](https://zhida.zhihu.com/search?q=身份认证&zhida_source=entity&is_preview=1)。有关设置和认证Git的更多信息，请参阅GitHub。
- 设置Maven。

### 构建和运行示例

1. 克隆optaplanner项目（或者，可以下载zipball）：

```
$ git clone https://github.com/kiegroup/optaplanner.git
```

1. 使用Maven构建它：

```
$ cd optaplanner $ mvn clean install -DskipTests
```

注意：首次运行时，由于需要下载jar包，Maven可能需要很长时间。

1. 运行示例：

```
$ cd optaplanner-examples $ mvn exec:java
```

1. 在你喜欢的IDE中编辑源代码。

## [参考链接](https://link.zhihu.com/?target=https%3A//www.optaplanner.org/docs/optaplanner/latest/planner-introduction/planner-introduction.html)


# 云原生和微服务时代的Java EE， Microprofile和Jakarta EE

***当前企业都在进行数字化转型，其中构建高效可靠易扩展的IT系统架构核心就是微服务，在Java语言的微服务框架中Spring Boot和Spring Cloud凭借简单易上手，多种云原生功能的集成，异常活跃的社区，占据半壁江山，俨然已经成为微服务开发的默认标准，被公认为企业进行微服务新建和改造的首选。***

那么作为传统的Java企业级架构Java EE似乎被有点冷落，但是实际上他也一直与时俱进，Java EE已经更名为**Jakata EE**，为了更好的拥抱云原生和保持创新。致力于企业级Java微服务架构标准的**MicroProfile**已经更新到2.2版本。而且很多行业如电信，金融，医疗，保险绝大多数的应用都是基于Java EE构建的单体应用，相比于直接采用Spring Boot重头开始微服务改造之路，使用MicroProfile的标准实现微服务迁移，代码的重用性更大，开发人员的熟悉度更高，并且MicroProfile的运行时有更多实现选择。

本文的目的就是追根溯源，了解**Java EE， Jakarta EE和MicroProfile**的发展历史和彼此之间的关系，以及在云原生和微服务时代的发展。


## Java EE

### 发展历程
1996年， Sun Microsystems公司(*以下简称Sun公司*)正式推出了Java 1.0版本，"一次编译，到处运行"的概念风靡全球技术生态圈，立刻赢得开发者的青睐，长期以来霸占着企业级开发的头把交椅。Java语言的发展和传播非常迅速，经历了JDK 1.1 和1.2 两个版本的发布(*1997年2月和1998年12月份*)之后，Sun公司随即就发布了**Java Platfrom,  Enterprise Edition**(*Java EE早期也称为J2EE，Java 2 Platform, Enterprise Edition*). **Java EE**的目标是基于**Java SE**(*Java Platform, Standard Edition*)建立一整套标准，致力于企业级Java应用的开发。

2006年底，Sun公司决定开始基于**GPL**开源绝大部分的Java虚拟机(JVM)代码，到了2007年初，整个开源过程结束，全部的JVM代码都已经开源并用于公开发行。随后OpenJDK诞生，成为Java SE版本的开源实现。直到2009年Sun公司被Oracle收购，十年的发展，Java EE版本也发布到了Java EE6，期间也部署了无数的企业应用，诞生了各种Java EE标准兼容的运行时应用服务器，知名的有Apache Tomcat， Weblogic，Websphere，Jboss，Glassfish等。

2009-2010年间，Oracle公司收购了Sun 公司，宣称会继续支持和投入Java的发展。然而2010年，Java之父James Gosling的离职和2012年跟Google的关于Java在安卓的使用法律诉讼，使得社区对于Java语言的发展信心蒙上了一层阴影。

为了给Java社区注入一剂强心剂，时隔5年之后，Oracle公司在2011年和2013年分别发布了JDK7和Java EE 7。虽然Java EE依然受到企业级的追捧，但是随着Spring的框架的不断演进，新的开发者和原先的一些企业开始转向Spring，同时Java EE自身平台变得原来越臃肿，无法满足业务的日益变化和适应云原生，微服务架构的技术需求。这一切使得Oracle坚信开源模式是对JAVA EE最好的选择。

2017年Oracle正式决定将Java EE贡献给Eclipse基金会。起初项目被命名为**Eclipse Enterprise for Java (EE4J)**。因为考虑到Oracle实际拥有Java的商标权，为了避免法律纠纷，经过社区调查投票，新的项目正式更名为**Jakarta Enterprise Edition (Jakarta EE)**，Java EE 8是Jakarta EE的第一个版本，至此Java EE也进入了一个全新的发展纪元。

下图简单统计了Java EE各版本发布的历史和每个版本的时间间隔(月数)。可以看出后面版本间隔时间逐渐变长。
![](https://github.com/chrisopal/writings/blob/master/img/javaee-version-history.png)
> 图为：Java EE各版本历史和每个版本的时间间隔

### 功能特点

Java EE历来是企业级应用开发的重要框架，它在事务，安全，扩展性，并发，部署管理等各方面都建立起了完善的标准和规范，同时IMB，Redhat，Oracle等公司的各种实现Java EE标准的应用服务器，使得便捷的管理传统企业应用的开发部署.众多功能特点依然是应用开发的必备：
> * CDI
> * JAX-RS
> * JPA / JTA
> * EJB (Version 3.0)
> * Bean Validation
> * Interceptors, Annotations, Concurrency Unitity
> * Security API

其实谈到Java EE，绕不开的还是Spring，Java EE加上Spring统治着企业级Java应用开发，两者之间无关优劣，就像[Adam Bien](http://adam-bien.com/)说的，这是两种不同的哲学。但是Spring对于Java EE的影响是显而易见的：
> * Spring和Hibernate提供了全新的开发方式，直接催生了EJB 3和JPA 1，而这两者正是Java EE 5的创新。
> * Spring依赖注入是Java EE CDI构建的基础。
> * Spring Batch并入了JBatch的规范([JSR 352]( https://www.jcp.org/en/jsr/detail?id=352))。

也正是因为Spring的快速发展和不断创新，特别是Spring Boot和Spring Cloud框架的建立使得Java开发者能快速开发微服务架构和云原生的应用。
> * Spring Boot奉行约定大于配置的准则使得微服务开发的简单易用深入人心。
> * Spring Cloud已经是云原生开发的重要平台，实现了服务注册和发现，负载均衡，监控等云原生的功能。

还是回到开篇提到的，既然Spring已经如此优秀，Java EE依然是微服务和云原生应用开发的选择吗？答案依然也是肯定的。尽管从Java EE 5之后，版本发布放缓，更多的时间投入到标准和规范的制定，但是在Java EE 8中为了重新树立信心增加了新功能以及重要功能的升级。比如：
> * CDI 2.0定义了在Java EE容器之外的CDI表现，使得在第三方库中依然适应反转控制。
> * JAX-RS 2.1标准化了特别是在微服务开发中使用的功能，如SSE，NIO Providers(filter, Interceptor等)，响应式的异步客户端，超文本API优化。
> * JSONP 1.1 和JSONB 1.0.更方便的处理JSON请求和响应。
> * Severlet 4.0支持HTTP/2协议和最新的HTTP 1.1协议功能。

尽管这些标准和功能都非常有用，但是还不足以像Spring Boot和Spring Cloud那样支持微服务和云原生应用的开发需求。为了解决这个问题，Java EE社区核心来说努力了两件事情：
* 2016年中，[MicroProfile](https://microprofile.io/)项目创立；
* 2018年4月，[Jakarta EE](https://jakarta.ee/)项目成为Java EE新发展起点。

```
"这不是结束，甚至不是结束的开始，而只是开始的结束." -- 丘吉尔
```
## MicroProfile

### 背景
创立MicroProfile社区和项目的想法萌生于2016年的Devoxx UK和DevNation会议。正如前面提到的，Java EE的新版本发布持续延期，特别是在云原生和微服务架构应用方面的新技术使用场景�又快速变化，让Java EE的开发者，厂商和相关组织不得不思考需要给企业级JAVA社区注入全新的微服务功能。于是MicroProfile社区就选择Eclipse基金会来管理这个项目，首先看重的是Eclipse基金会强大的开源项目的管理能力以及知识产权方面的经验。同样的Eclipse基金会目前没有微服务方面相关的项目运营，这也有助于建立在该领域的地位，因此这对MicroProfile和Eclipse基金会都是一个双赢的局面。

随后在2016年的JavaOne大会上面，本着致力于**优化企业级Java微服务架构**的宗旨，MicroProfile 1.0版本正式发布。参与的厂商主要包括Payara, Fujitsu, Tomitribe, IBM, Red Hat, Hammock, SmartBear, Hazelcast, Oracle和London Java Community (LJC)这里只是列举了一些，具体可以参考官网[MicroProfile](https://microprofile.io/)。MicroProfile只是一套标准和规范，本身并不提供实现，对应的运行时实现由各厂商提供，目前主要的实现包含：
> * Open Liberty (https://openliberty.io/)
> * Thorntail  (https://thorntail.io/)
> * Payara (https://www.payara.fish/upstream_builds)
> * Helidon (https://helidon.io/)

更具体的信息可以参考[官网Wiki](https://wiki.eclipse.org/MicroProfile/Implementation)。
### 目标和范围
MicroProfile的项目宗旨就是**优化企业级Java微服务架构**,具体的范围可以简单的概括为：
> * 提供各企业级Java运行时直接切换的可移植微服务架构。
> * 提供可互操作的微服务架构允许多语言的运行时实现相互通信(不仅限于Java)。
> * 提供孵化环境鼓励在微服务架构和企业级Java领域的不断创新。
> * 在短周期内（一个季度）进行项目的快速迭代和创新,获得社区批准,发布并不断重复。 最终有的标准和规范需要提交到JCP，后续包含在JSR中。

### 功能

当前MicroProfile 2.2版本已经发布，依赖于Java EE 8为基础，进行了相应的功能升级。
下图详细的描述了2.2版本对应功能：
![](https://microprofile.io/wp-content/uploads/2019/02/MP2.2-screenshot.png)
> 图为 MicroProfile 2.2 版本功能。来源:[MicroProfile博客](https://microprofile.io/2019/02/12/eclipse-microprofile-2-2-is-now-available/)

除了CDI,JSONP,和JAX-RS等Java EE 8相关的规范，MicroProfile主要专注于微服务架构相关的规范比如可注入配置，故障隔离，安全(JWT), 可观测性，分布式跟踪，健康检查，OpenAPI，响应式异步REST客户端等，下面根据MicroProfile各项目的Github描述简单介绍一下，详细项目信息�可移步[官网项目列表](https://microprofile.io/projects/)。这些规范重要的一个目标是兼容目前业界主流的云平台如Kubernetes。

现在MicroProfile项目如此优秀，那么Java EE该如何走，MicroProfile创建的相关规范和功能如何引入到Java EE？答案是Jakarta EE。

## Jakarta EE

2019年9月，在IBM和Redhat的协助下，Oracle正式把Java EE贡献给Eclipse基金会，支持新的发展纪元已经开始。关于Jakarta EE，功能方面因为第一个版本就是Java EE 8，前面已经提过，就不在赘述。主要讲两点，认为是对整个Java EE发展至关重要的：全新的云原生愿景和开源软件的运作模式。

### 云原生
Java EE过去这么多年一直是构建企业级Java的重要平台，为了能够加速在云原生时代的企业应用开发，引领各厂商合作推动Java EE技术的发展，这是Jakarta EE的目标。从技术的角度来说，Jakarta EE的愿景有：

 - 更好的支持微服务架构
 - 面向云原生Java，无缝集成Docker和Kubernetes
 - 加速Java EE技术的创新
 - 构建富有活力的社区
 - 提供生产级别的标准实现

### Jakarta EE工作组

在云原生时代，我们见证的众多开源项目的成功，诸如Kubernetes，Envoy，Spring Boot，强大的社区灵活有效的运作模式对于项目的成功至关重要。反观在Java EE时代，Oracle控制着版本发布的节奏，复杂繁琐的JCP审核流程，导致Java EE版本的发布和新功能的引入无比缓慢，这也是Jakarta EE试图改变的局面。

当前Jakarta EE工作组的成员包括：Fujitsu, IBM, Oracle, Lightbend, Payara, Pivotal, Red Hat, Tomitribe和Webtide。在整个管理架构中有四个委员会，分别是指导委员会，标准委员会，市场和品牌委员会，企业需求委员会，各司其职，相互协作。
在Eclipse基金会治下，工作组秉承自我管理的精髓，制定所有发布日常和计划，与此同时标准和规范的制定也完全以社区为导向，鼓励开发者，厂商和组织参与制定流程以此来反应社区的意志，通过快速迭代，在新版本中不断融入其它开源社区的功能创新，如MicroProfile，帮助开发者构建云原生应用。

### 迁移

从Java EE到Jakarta EE的迁移工作是巨大的，尽管面临着各种问题，过程相对比较顺利，主要的工作量是处理110多个代码库的迁移，具体的工作内容可以参考[这里](https://projects.eclipse.org/projects/ee4j)，具体工作：

> * 检查内部所有的license是否正确。
> * 分析所有三方依赖库，是否需要升级到最新版本以解决重要的Bug和安全问题。
> * 基于Eclipse项目规范，进行相关标准和实现重命名。
> * 问题列表的转移以保留相关历史和变化以免丢失前期工作。
> * 构建编译和运行的基础设施环境，实现敏捷和持续集成。

一旦所有工作完成，那么将建立一个完善的云原生的开源企业级Java平台，使得所有参与的开发者，厂商，组织等相互协作，避免厂商锁定。当前第一个Jakarta EE的版本是Java EE 8，同样运行时实现有：
> * Open Liberty (https://openliberty.io/)
> * Thorntail  (https://thorntail.io/)
> * Payara (https://www.payara.fish/upstream_builds)

## 总结
写了这么多，简短概况：Java EE发展遇到了各种问题，主要是微服务架构和云原生两大问题，为了更好的服务微服务架构成立了MicroProfile项目，专注于微服务架构标准的制定。为了快速创新和构建云原生企业级Java应用，更名为Jakarta EE。两者都由Eclipse基金会管理。因此如果想快速使用Java EE构建云原生的微服务架构，只需引入Java EE 8的对应依赖和MicroProfile相关依赖，选择任意运行时实现，即可开发部署微服务，并且随意切换。
现在有了Eclipse基金会的开源运作，MicroProfile和
Jakarta EE两大项目齐头并进，Java EE在云原生和微服务时代，依然能够在企业级Java应用和Spring分庭抗礼吗？

> Java EE, 未来可期

## 参考


> [1]https://www.packtpub.com/application-development/hands-cloud-native-microservices-jakarta-ee
> [2]https://microprofile.io
> [3]https://jakarta.ee
> [4]https://en.wikipedia.org/wiki/Java_Platform,_Enterprise_Edition
> [5]https://projects.eclipse.org/proposals/eclipse-microprofile
> [6]https://www.youtube.com/watch?v=Jemx1BrB45Y&t=1590s





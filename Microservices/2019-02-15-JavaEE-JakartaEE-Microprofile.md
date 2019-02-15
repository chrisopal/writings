# Java EE, Jakarta EE 和Microprofile

*当前企业都在进行数字化转型，其中构建高效可靠易扩展的IT系统架构核心就是微服务，在Java语言的微服务框架中Spring Boot和Spring Cloud凭借简单易上手，多种云原生功能的集成，异常活跃的社区，占据半壁江山，俨然已经成为微服务开发的默认标准，被公认为企业进行微服务新建和改造的首选。*

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

## Jakarta EE






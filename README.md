Bean的配置有多种方式，包括基于**XML文件配置**，基于**注解配置**和基于**Java类配置**。先来介绍一下基于XML文件配置的方式。
###1. 基于XML文件配置Bean
####1.1 声明一个Bean
```xml
	<bean id="car" class="ch4.Car"/>
```
####1.2 属性注入
对于Literal属性的注入直接使用类似于`p:brand="redflag"`的声明即可。
```xml
		<bean id="car" class="ch4.Car" 
		p:brand="redflag"
		p:maxSpeed="200"
		p:price="200000"/>
```
对于引用其他Bean进行注入，使用类似于`p:car-ref="car"`的声明。
```xml
	<bean id="boss" class="ch4.Boss"
		p:car-ref="car"/>
```

####1.3 构造函数注入
```xml
	<bean id="car1" class="ch4.Car">
		<constructor-arg index="0" value="default"></constructor-arg>
		<constructor-arg index="1" value="0"></constructor-arg>
	</bean>
```
> **Tips:** 属性注入和构造函数注入将使得实例化的Bean具有想要的初始化属性值。

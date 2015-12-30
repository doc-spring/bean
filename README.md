Bean的配置有多种方式，包括基于**XML文件配置**，基于**注解配置**和基于**Java类配置**。先来介绍一下基于XML文件配置的方式。
###1. 基于XML文件配置Bean
####1.1 声明一个Bean
```xml
	<bean id="car" class="ch4.Car"/>
```
####1.2 属性注入
Spring会调用相应属性的set函数将对应的属性值注入实例化的Bean。
#####1.2.1 Literal注入
对于Literal属性的注入直接使用类似于`p:brand="redflag"`的声明即可。
```xml
		<bean id="car" class="ch4.Car" 
		p:brand="redflag"
		p:maxSpeed="200"
		p:price="200000"/>
```
一种更完整的写法如下
```xml
	<bean id="car3" class="ch4.Car">
		<property name="brand" value="redflag"></property>
		<property name="maxSpeed" value="200"></property>
		<property name="price" value="200000"></property>
	</bean>
```
> **Tips:** 使用p命名空间需要引入对应的Schema定义文件。

#####1.2.2 引用Bean注入
对于引用其他Bean进行注入，使用类似于`p:car-ref="car"`的声明。
```xml
	<bean id="boss" class="ch4.Boss"
		p:car-ref="car"/>
```
#####1.2.3 null值
```xml
	<bean id="car" class="ch4.Car">
		<property name="brand"><value></value></property>
	</bean>
```

#####1.2.4 内部匿名Bean
如同Java的内部类
```xml
	<bean id="boss1" class="ch4.Boss">
		<property name="brand">
			<bean class="ch4.Car" 
				p:brand="redflag" 
				p:maxSpeed="200"
				p:price="200000">
			</bean>
		</property>
	</bean>
```

####1.3 构造函数注入
Spring会调用相应的构造函数
```xml
	<bean id="car1" class="ch4.Car">
		<constructor-arg index="0" type="java.lang.String" value="default"></constructor-arg>
		<constructor-arg index="1" type="int" value="0"></constructor-arg>
	</bean>
```
> **Tips:** 属性注入和构造函数注入将使得实例化的Bean具有想要的初始化属性值。

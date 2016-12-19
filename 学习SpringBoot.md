#学习SpringBoot  

----------



###什么是SpringBoot？  
Spring Boot是Spring社区发布的一个开源项目，旨在帮助开发者快速并且更简单的构建项目。大多数SpringBoot项目只需要很少的配置文件。  
###SpringBoot优点？  
创建独立的Spring项目  
内置Tomcat和Jetty容器  
提供一个starter POMs来简化Maven配置  
提供了一系列大型项目中常见的非功能性特性，如安全、指标，健康检测、外部配置等  
完全没有代码生成和xml配置文件  
##创建一个SpringBoot项目  
准备：Jdk1.8 +maven +tomcat8 新建maven项目
springboot，默认是使用用tomcat8 容器，需要java7+ 才能支持。
项目建好好配置pom.xml 文件，下载spring boot 依赖的包即可  
###pom.xml配置  
	<project xmlns="http://maven.apache.org/POM/4.0.0" 	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
		<modelVersion>4.0.0</modelVersion>
		<groupId>com.it.guo</groupId>
		<artifactId>sboot</artifactId>
		<packaging>war</packaging>
		<version>0.0.1-SNAPSHOT</version>
		<name>sboot Maven Webapp</name>
		<url>http://maven.apache.org</url>


		<parent>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-parent</artifactId>
			<version>1.3.5.RELEASE</version>
			<relativePath /> 
		</parent>

		<properties>
			<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
			<java.version>1.8</java.version>
		</properties>

		<dependencies>
			<dependency>
				<groupId>junit</groupId>
				<artifactId>junit</artifactId>
				<version>3.8.1</version>
				<scope>test</scope>
			</dependency>
			<!-- spring boot 核心 -->
			<dependency>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-starter</artifactId>
			</dependency>
	
			<dependency>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-starter-test</	artifactId>
				<scope>test</scope>
			</dependency>
			
			<dependency>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-starter-web<artifactId>
				<version>1.3.5.RELEASE</version>
			</dependency>

		</dependencies>
		<build>
			<finalName>sboot</finalName>
			<plugins>
				<plugin>
					<groupId>org.springframework.boot</groupId>
					<artifactId>spring-boot-maven-plugin</artifactId>
				</plugin>
			</plugins>
		</build>
	</project>  
###编写代码  
	import org.springframework.boot.*;
	import org.springframework.boot.autoconfigure.*;
	import org.springframework.stereotype.*;
	import org.springframework.web.bind.annotation.*;

	@RestController
	@EnableAutoConfiguration
	public class Example {
    	@RequestMapping("/")
    	String home() {
    	    return "Hello World!";
    	}
		public static void main(String[] args) throws Exception {
	   		SpringApplication.run(Example.class, args);
    	}
	}  
######注解说明  
@RestController。这被称为一个构造型（stereotype）注解。它为阅读代码的人们提供建议。对于Spring，该类扮演了一个特殊角色。在本示例中，我们的类是一个web @Controller，所以当处理进来的web请求时，Spring会询问它。  
  
@RequestMapping注解提供路由信息。它告诉Spring任何来自"/"路径的HTTP请求都应该被映射到home方法。@RestController注解告诉Spring以字符串的形式渲染结果，并直接返回给调用者。   
 
@EnableAutoConfiguration。这个注解告诉Spring Boot根据添加的jar依赖猜测你想如何配置Spring。由于spring-boot-starter-web添加了Tomcat和Spring MVC，所以auto-configuration将假定你正在开发一个web应用并相应地对Spring进行设置。  

main方法。这只是一个标准的方法，它遵循Java对于一个应用程序入口点的约定。我们的main方法通过调用run，将业务委托给了Spring Boot的SpringApplication类。SpringApplication将引导我们的应用，启动Spring，相应地启动被自动配置的Tomcat web服务器。我们需要将Example.class作为参数传递给run方法来告诉SpringApplication谁是主要的Spring组件。  
###运行  
执行main 函数，启动tomcat 然后在浏览器访问http://localhost:8080即可
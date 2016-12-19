#搭建season开发环境
###1创建项目  
新建MAVEN工程（jdk1.7以上）  
![](http://i.imgur.com/xAhpQaU.png)  
填写MAVEN信息，GroupId必须填写为trs.com.cn，ArtifactId填写应用名称，版本号默认即可。  
![](http://i.imgur.com/uNHusAg.png)  
填写项目信息，点击Finsn即可!  
[](http://i.imgur.com/t6zFDrj.png)  
###2配置pom.xml  
添加打包格式  
  
`<packaging>war</packaging>`  
  
war或jar都可以  
  
添加season的支持  

	<parent>    
		<artifactId>season-parent</artifactId>  
		<groupId>trs.com.cn</groupId>  
		<version>1.2</version>  
	</parent>  
添加season-core的依赖  
  
	<dependency>  
		<groupId>trs.com.cn</groupId>  
		<artifactId>season-core</artifactId>  
	</dependency>  
添加海尔maven仓库地址  
  
	<repository>
        <id>haier-maven-repository</id>
        <url>http://test.haier.com/nexus/content/groups/public/</url>
    </repository  
添加打包插件  
  
	<plugin>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-maven-plugin</artifactId>
    </plugin>  
完整POM  
  
	<?xml version="1.0" encoding="UTF-8"?>
    <project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
        <modelVersion>4.0.0</modelVersion>

        <groupId>trs.com.cn</groupId>
        <artifactId>season-test</artifactId>
        <version>1.0-SNAPSHOT</version>

        <packaging>war</packaging>

        <parent>
            <artifactId>season-parent</artifactId>
            <groupId>trs.com.cn</groupId>
            <version>1.2</version>
        </parent>

        <dependencies>
            <dependency>
                <groupId>trs.com.cn</groupId>
                <artifactId>season-core</artifactId>
            </dependency>
        </dependencies>

        <build>
            <finalName>SeasonTest</finalName>
            <plugins>
                <plugin>
                    <groupId>org.springframework.boot</groupId>
                    <artifactId>spring-boot-maven-plugin</artifactId>
                </plugin>
            </plugins>
        </build>

        <repositories>
            <repository>
                <id>haier-maven-repository</id>
                <url>http://test.haier.com/nexus/content/groups/public/</url>
            </repository>
        </repositories>

    </project>  
###创建启动类  
创建一个类，继承com.season.core.spring.SeasonApplication，添加main方法  

	public static void main(String[] args){
        SeasonRunner.run(App.class);
    }  
![](http://i.imgur.com/pKjmEmq.png)  
启动main方法，即可启动应用。当然现在什么功能也没有，只是启动了应用，应用默认的容器是Tomcat8。 
###创建Controller  
新建HelloController，继承com.season.core.Controller，添加@ControllerKey注解。新建类所属的包名必须是com开始，因 Season 默认配置的 Spring 扫描包为com。
  
	@ControllerKey("hello")
    public class HelloController extends Controller{
        public void season(){
            renderText("hi season!");
        }
    }  
重新启动main方法，访问http://localhost:8080/hello/season，即可看见效果。  
![](http://i.imgur.com/piDTDds.png)  
出现以下问题是由于8080端口被占用造成的  
![](http://i.imgur.com/lkqJo11.png)  
此问题结束8080端口进程即可解决
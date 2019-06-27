# SpringBoot
springboot的介绍和整合其他技术的案例

一：springboot简介
  1、Spring boot是Spring家族中的一个全新的框架，它用来简化Spring应用程序的创建和开发过程，也可以说Spring boot能简化我们之前采用Spring mvc + Spring + MyBatis 框架进行开发的过程；
  
  2、在以往我们采用 Spring mvc + Spring + MyBatis 框架进行开发的时候，搭建和整合三大框架，我们需要做很多工作，比如配置web.xml，配置Spring，配置MyBatis，并将它们整合在一起等，而Spring boot框架对此开发过程进行了革命性的颠覆，抛弃了繁琐的xml配置过程，采用大量的默认配置简化我们的开发过程；
  
  3、所以采用Spring boot可以非常容易和快速地创建基于Spring 框架的应用程序，它让编码变简单了，配置变简单了，部署变简单了，监控变简单了；
  
  4、正因为 Spring boot 它化繁为简，让开发变得极其简单和快速，所以在业界备受关注；
  
  5、Spring boot 在国内的关注趋势图：http://t.cn/ROQLquP
  
二：springboot特性
  1、能够快速创建基于Spring的应用程序；
  
  2、能够直接使用java main方法启动内嵌的Tomcat, Jetty 服务器运行Spring boot程序，不需要部署war包文件；
  
  3、提供约定的starter POM来简化Maven配置，让Maven的配置变得简单；
  
  4、根据项目的Maven依赖配置，Spring boot自动配置Spring、Spring mvc等；
  
  5、提供了程序的健康检查等功能；
  
  6、基本可以完全不使用XML配置文件，采用注解配置；
  
三：springboot四大核心
  1、自动配置：针对很多Spring应用程序和常见的应用功能，Spring Boot能自动提供相关配置；
  
  2、起步依赖：告诉Spring Boot需要什么功能，它就能引入需要的依赖库；
  
  3、Actuator：让你能够深入运行中的Spring Boot应用程序，一探Spring boot程序的内部信息；
  
  4、命令行界面：这是Spring Boot的可选特性，主要针对 Groovy 语言使用；
  Groovy是一种基于JVM (Java虚拟机) 的敏捷开发语言；它结合了Python、Ruby和Smalltalk的许多强大的特性，Groovy 代码能够与 Java 代码很好地结合，也能用于扩展现有代码；由于其运行在 JVM 上的特性，Groovy 可以使用其他 Java 语言编写的库；
  
四：springboot开发环境
  1、推荐使用Spring boot最新版本；
  
  2、如果是使用 eclipse，推荐安装 Spring Tool Suite (STS) 插件；
  
  3、如果使用 IDEA 旗舰版，自带了Springboot插件；
  
  4、推荐使用 Maven 3.0+，Maven目前最新版本为 3.5.2；
  
  5、推荐使用 Java 8，虽然 Spring boot 也兼容 Java 6；
  
五：第一个springboot程序
  快速开发一个Spring boot程序步骤如下：
  1、创建一个Spring boot项目；
     1、可以采用方式一： 使用 eclipse 的 Spring Tool Suite (STS) 插件/或者 IDEA 自带的插件创建；
     2、可以采用方式二：直接使用 Maven 创建项目的方式创建；
   
  2、加入Spring boot 的父级和起步依赖；
     1、父级依赖：
     <parent>
       <groupId>org.springframework.boot</groupId>
       <artifactId>spring-boot-starter-parent</artifactId>
       <version>1.5.9.RELEASE</version>
       <relativePath />
     </parent>
     加入Spring boot父级依赖可以简化我们项目的Maven配置；
    2、起步依赖：
    <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    加入Spring boot 的起步依赖也可以简化我们项目的Maven配置；
    
 3、创建Spring boot 的入口main方法
    @SpringBootApplication
      public class SpringbootApplication {
	        public static void main(String[] args) {
		        SpringApplication.run(SpringbootApplication.class, args);
	                   }
                  }
                  
 4、创建一个Spring mvc 的Controller
    @Controller
      public class HelloController {
	    @RequestMapping("/sayHi")
	        public @ResponseBody String sayHi () {
		        return "Hi，Spring boot";
	            }
            }
            
 5、运行Spring boot的入口main方法
    通过eclipse、idea右键运行main方法；
    
    至此，第一个Spring boot程序开发完成；
    
六：第一个 Spring boot 程序解析
  1、Spring Boot 的父级依赖spring-boot-starter-parent配置之后，当前的项目就是Spring Boot项目；
  
  2、spring-boot-starter-parent是一个特殊的starter依赖，它用来提供相关的Maven默认依赖，使用它之后，常用的jar包依赖可以省去version配置；
  
  3、Spring Boot提供了哪些默认jar包的依赖，可查看该父级依赖的pom文件；
  
  4、如果不想使用某个默认的依赖版本，可以通过pom.xml文件的属性配置覆盖各个依赖项，比如覆盖Spring版本：
     <properties>
         <spring.version>5.0.0.RELEASE</spring.version>
     </properties>
     
  5、@SpringBootApplication 注解是Spring Boot项目的核心注解，主要作用是开启Spring自动配置；
  
  6、main方法是一个标准的Java程序的main方法，主要作用是作为项目启动运行的入口；
  
  7、@Controller 及 @ResponseBody 依然是我们之前的Spring mvc，因为Spring boot的里面依然是使用我们的Spring mvc + Spring + MyBatis 等框架；
  
七：Spring boot 的核心配置文件
    Spring boot的核心配置文件用于配置Spring boot程序，有两种格式的配置文件：
    1、.properties文件
        键值对的properties属性文件配置方式
    2、.yml文件
        yml 是一种 yaml 格式的配置文件，主要采用一定的空格、换行等格式排版进行配置；
        yaml 是一种直观的能够被计算机识别的的数据序列化格式，容易被人类阅读，yaml 类似于 xml，但是语法比 xml 简洁很多；
        值与前面的冒号配置项必须要有一个空格；
        yml 后缀也可以使用 yaml 后缀；
        
    配置示例
      #配置服务器端口
         server.port=9800
      #配置应用访问路径
         server.context-path=/13-springboot-web
         
      server:
        port: 9091
        context-path: /13-springboot-web
        
    多环境配置文件
      #比如配置测试环境
        spring.profiles.active=dev
        application-dev.properties
        
      #比如配置生产环境
        spring.profiles.active=product
        application-product.properties
        
八：Spring boot 自定义配置
    我们可以在Spring boot的核心配置文件中自定义配置，然后采用如下注解去读取配置的属性值；
     1、@Value注解
        用于逐个读取自定义的配置，比如：
          @Value("${bjpowernode.name}")
           private String name;
           
     2、@ConfigurationProperties
        用于将整个文件映射成一个对象，比如：
        @Component
        @ConfigurationProperties(prefix="bjpowernode")
         public class MyConfig {
	          private String name;
	             public String getName() {
		            return name;
	               }
	          public void setName(String name) {
		       this.name = name;
	            }
          }
          
九：Spring boot 下的 Spring mvc
    Spring boot下的Spring mvc 和之前的Spring mvc使用是完全一样的：
    @Controller  即为Spring mvc的注解，处理http请求；
    @RestController  Spring4后新增注解；是@Controller与@ResponseBody的组合注解；用于返回字符串或json数据；
    @GetMapping  RequestMapping 和 Get请求方法的组合；
    @PostMapping  RequestMapping 和 Post请求方法的组合；
    @PutMapping  RequestMapping 和 Put请求方法的组合；
    @DeleteMapping  RequestMapping 和 Delete请求方法的组合；


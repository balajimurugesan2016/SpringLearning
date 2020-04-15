# Spring Framework

This document is written to make readers understand the basics of spring framework and use it in wide variety of applications. You can use it as a refresher to revise the concepts of spring framework, that is rusted in memory. 


## Topics
       1. Inversion of control in Spring framework - Dependency injection
       2. Instantiating  a general purpose spring command line application
# Inversion of control in Spring framework - Dependency injection

It is a process whereby objects define their dependencies (that is, the other objects they work with) only through constructor arguments, arguments to a factory method, or properties that are set on the object instance after it is constructed or returned from a factory method. The container then injects those dependencies when it creates the bean. This process is fundamentally the inverse (hence the name, Inversion of Control) of the bean itself controlling the instantiation or location of its dependencies by using direct construction of classes or a mechanism such as the Service Locator pattern.

The  `org.springframework.beans`  and  `org.springframework.context`  packages are the basis for Spring Framework’s IoC container. The  [`BeanFactory`](https://docs.spring.io/spring-framework/docs/5.2.5.RELEASE/javadoc-api/org/springframework/beans/factory/BeanFactory.html)  interface provides an advanced configuration mechanism capable of managing any type of object.  [`ApplicationContext`](https://docs.spring.io/spring-framework/docs/5.2.5.RELEASE/javadoc-api/org/springframework/context/ApplicationContext.html)  is a sub-interface of  `BeanFactory`. 

  USES: 
  
-   Easier integration with Spring’s AOP features
    
-   Message resource handling (for use in internationalization)
    
-   Event publication
    
-   Application-layer specific contexts such as the  `WebApplicationContext`  for use in web applications.
    

In short, the  `BeanFactory`  provides the configuration framework and basic functionality, and the  `ApplicationContext`  adds more enterprise-specific functionality. The  `ApplicationContext`  is a complete superset of the  `BeanFactory` .

## Major Annotations
**@bean**
**@Autowired**
**@Configuration**
**@Component**
**@Controller**
**@RestController**
**@GetMapping**
**@PostMapping**

## Creating a bean in Java
A bean can be created in multiple ways using java configuration or xml configuration. 
```
@Configuration
class main_config_class{
@Bean
public Booking createBooking{
  return new Booking(movie);
}
}
```
## Creating a bean in Java using Autowired
@Autowired annotation is applied to properties and constructor in  a class. Spring creates a bean for the autowired property

```
@RestController
class Movie{
@Autowired
Booking booking;
@Autowired
Seats seats;
public void Movie(){
  this.initialize()
}
public MovieRepo setMovie(){
} 
public ArrayList<MovieRepo> setMovieinBatch(){
} 
}
```
## @Dependson annotation

This annotation helps to determine the order in which the bean needs to be instantiated.
```
@Configuration
class main_config_class{
@Bean
@Dependson("createmovie", "createseats")
public Booking createBooking{
  return new Booking(movie);
}

@Bean(name = "createmovie")
public Movie createMovie{
  return new Movie();
}

@Bean(name = "createseats")
public Movie createSeats{
  return new Seat();
}
}
```
## @Import annotation
This annotation helps to import additional configuration classes to the main configuration class. if those classes are separated by code. 
```
@Configuration
@import("dao_configuration", "security_configuration")
class main_config_class{
@Bean
@Dependson("createmovie", "createseats")
public Booking createBooking{
  return new Booking(movie);
}

@Bean(name = "createmovie")
public Movie createMovie{
  return new Movie();
}

@Bean(name = "createseats")
public Movie createSeats{
  return new Seat();
}
}
```
# Instantiating  a general purpose spring command line application

## Initializing the beans in spring 

### Old Way( Before Spring 3.1 )
```
ApplicationContext context = new ClassPathXmlApplicationContext("services.xml,"dao.xml");
```
### New Way
```
ApplicationContext context = new AnnotationApplicationContext(Config.class);
```
**Annotation configuration application context forms an umbrella on top of the bean factory and converts the application as an enterprise application**

## Manual Instantiation
For a basic command line application in spring, the following lines are helpful to register and getbean in a spring context. In other words this creates a context in the **Spring container**.
```
ApplicationContext context = new AnnotationApplicationContext(Config.class);
context.register(Movies.class);
context.register(Booking.class);
Movies mv = context.getBean(Movies.class);
movies booking = context.getBean(Booking.class);

```

## Bean Lifecycle

Spring bean life cycle is controlled by few call back methods which are invoked when the spring container is initialized or the when the bean is beginning to be used in case of lazy initialization of a bean

The following annotations after spring 3.1 is of use today. 
**@PostConstruct** --- Init method
**@PreDestroy** --- Destroy/Shutdown method

The working of this annotations can be understood from an example. 

```
@Bean
public class<T> MyBean{
Logger logger = LoggerFactory.getLogger(my_bean.class);

@PostConstruct
public method init(){
logger.info("Bean instantiated");
}

public void MyBean(){
logger.info("My bean called");
} 

@PreDestroy
public void destroy(){
logger.info("My bean destroyed");
} 
public void close(){
logger.info("All resources closed");
}
}
```
Explanation:
The class MyBean contains methods such as init and destroy which are annotated as @PostConstruct and @PreDestroy. The postconstruct method is called when the bean is initialized for the first time and predestroy method is called when the bean is closed. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE1NDU5NDU5LDIyMTMwMzE3NSw3Mzc2OT
A2OThdfQ==
-->
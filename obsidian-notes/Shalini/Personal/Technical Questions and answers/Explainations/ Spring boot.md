###### **WHAT ?**
It is a Java-based spring framework used for Rapid Application Development (to build stand-alone microservices). It has extra support of auto-configuration and embedded application servers like tomcat, jetty, etc.
- Creates stand-alone spring application with minimal configuration needed.
- It has embedded tomcat, jetty which makes it just code and run the application.
- Provide production-ready features such as metrics, health checks, and externalized configuration.
- Absolutely no requirement for XML configuration.

###### **Can you explain the Spring Boot auto-configuration ?**
Auto-configuration is one of the most powerful features of Spring Boot. It automatically configures your Spring application based on the jar dependencies that you have added. For instance, if your project includes `spring-boot-starter-web`, Spring Boot automatically configures your application to use Tomcat as the default web server and configures Spring MVC for web development.

###### How do you handle configuration properties in Spring Boot?
 Spring Boot provides a highly convenient way to externalize configuration, allowing you to work with the same application code in different environments. You can use properties files, YAML files, environment variables, and command-line arguments for configuration. Spring Boot’s `@Value` annotation lets you inject values into fields in your beans from properties files, while `@ConfigurationProperties` allows for type-safe configuration, binding properties to structured objects.
Here’s a code snippet using `@ConfigurationProperties`:
@Component  
@ConfigurationProperties(prefix="app")  
public class AppProperties {  
    private String name;  
    private String description;  
    // getters and setters  
}

And in `application.properties`:
app.name=MyApp  
app.description=My Spring Boot Application

Spring Boot also supports profiles, enabling different configurations for different environments, such as development, testing, and production, using profile-specific properties files (e.g., `application-dev.properties`).


###### Explain the process of creating a RESTful web service in Spring Boot.
Creating a RESTful web service with Spring Boot is streamlined thanks to its auto-configuration and annotation support. The process involves defining a controller with `@RestController` annotation and using mapping annotations like `@GetMapping`, `@PostMapping`, `@PutMapping`, and `@DeleteMapping` to handle different HTTP requests.

Here’s a simple example of a RESTful service that returns a greeting:

import org.springframework.web.bind.annotation.GetMapping;  
import org.springframework.web.bind.annotation.RequestParam;  
import org.springframework.web.bind.annotation.RestController;  
  
@RestController  
public class GreetingController {  
  
    private static final String template = "Hello, %s!";  
    private final AtomicLong counter = new AtomicLong();  
  
    @GetMapping("/greeting")  
    public Greeting greeting(@RequestParam(value = "name", defaultValue = "World") String name) {  
        return new Greeting(counter.incrementAndGet(),  
                            String.format(template, name));  
    }  
}  
  
class Greeting {  
    private final long id;  
    private final String content;  
  
    // Constructor, getters, and setters  
}

This service uses `@GetMapping` to map HTTP GET requests to the `greeting` method, which generates a simple greeting message.


###### Describe how Spring Boot simplifies working with data using Spring Data JPA.
Spring Boot significantly simplifies the configuration and usage of Spring Data JPA for data access layers. By including `spring-boot-starter-data-jpa` in your project, Spring Boot automatically configures your data source and the entity manager factory, reducing manual configuration. Moreover, Spring Data repositories dramatically reduce the boilerplate code required to implement data access layers.

Here’s a simple example of a Spring Data JPA repository:

import org.springframework.data.jpa.repository.JpaRepository;  
  
public interface UserRepository extends JpaRepository<User, Long> {  
    User findByUsername(String username);  
}

In this example, `UserRepository` extends `JpaRepository`, providing CRUD operations on `User` entities. Spring Data JPA also allows for defining query methods in the interface, like `findByUsername`, without implementing the method body.

###### How can you handle transactions in Spring Boot applications?
 Spring Boot simplifies transaction management by providing annotations and auto-configuration for transactional behavior. The `@Transactional` annotation is used to declare transactional boundaries on methods or classes. When applied, Spring creates a proxy around the annotated class or method to manage the transaction lifecycle automatically, rolling back transactions in case of runtime exceptions.

Here’s how you can use `@Transactional` in a service class:

import org.springframework.beans.factory.annotation.Autowired;  
import org.springframework.stereotype.Service;  
import org.springframework.transaction.annotation.Transactional;  
  
@Service  
public class UserService {  
  
    @Autowired  
    private UserRepository userRepository;  
  
    @Transactional  
    public User createUser(String username) {  
        User user = new User(username);  
        // Save the user object to the database  
        return userRepository.save(user);  
    }  
}

This example shows a service method where a new user is created and saved to the database. The `@Transactional` annotation ensures that the operation is performed within a transactional context, rolling back the changes if any exception occurs during the process.

###### What are the best practices for managing application properties and secrets in Spring Boot?

**Answer:** Managing application properties and secrets securely is crucial for any application. Spring Boot applications typically use `application.properties` or `application.yml` files for configuration. For sensitive data such as passwords or API keys, environment variables or Spring Cloud Config Server can be used to externalize secrets from the codebase.

A best practice is to use Spring’s `@Value` annotation to inject values from properties files or environment variables into your application, keeping sensitive information out of the code:

import org.springframework.beans.factory.annotation.Value;  
import org.springframework.stereotype.Component;  
  
@Component  
public class MyService {  
  
    @Value("${api.key}")  
    private String apiKey;  
  
    // Use the apiKey in your service methods  
}

For more sensitive secrets, consider using Spring Cloud Config Server for centralized configuration or vault solutions like HashiCorp Vault, integrated with Spring Vault, to securely manage and access secrets.


###### What is the difference between @RestController and @Controller in Spring Boot?
@Controller Map of the model object to view or template and make it human readable but @RestController simply returns the object and object data is directly written in HTTP response as JSON or XML.

###### Describe the flow of HTTPS requests through the Spring Boot application?
On a high-level spring boot application follow the MVC pattern which is depicted in the below flow diagram.
![[Pasted image 20240621204044.png]]



######  What is the use of Profiles in spring boot?
While developing the application we deal with multiple environments such as dev, QA, Prod, and each environment requires a different configuration. For eg., we might be using an embedded H2 database for dev but for prod, we might have proprietary Oracle or DB2. Even if DBMS is the same across the environment, the URLs will be different.

To make this easy and clean, Spring has the provision of Profiles to keep the separate configuration of environments.

### What is dependency Injection?
The process of injecting dependent bean objects into target bean objects is called dependency injection.

- Setter Injection: The IOC container will inject the dependent bean object into the target bean object by calling the setter method.
- Constructor Injection: The IOC container will inject the dependent bean object into the target bean object by calling the target bean constructor.
- Field Injection: The IOC container will inject the dependent bean object into the target bean object by Reflection API.

###### What is the default port of tomcat in spring boot?
The default port of the tomcat server-id 8080. It can be changed by adding **sever.port** properties in the **application.property** file.

###### **Bean Definition**
In Spring, the objects that form the backbone of your application and that are managed by the Spring IoC container are called beans. A bean is an object that is instantiated, assembled, and otherwise managed by a Spring IoC container.
https://www.baeldung.com/spring-bean#:~:text=Bean%20Definition&text=In%20Spring%2C%20the%20objects%20that,by%20a%20Spring%20IoC%20container.

# Annotations

**@ SpringBootApplication**
We use this annotation in our application’s main class to enable spring boot features like auto-configuration and component scanning.

SpringBootApplication annotation serves the purpose of following annotations combined.

> @ Enable Autoconfiguration — Enables the Auto Configuration feature of Spring Boot.
> 
> @ ComponentScan — Enable component Scanning.
> 
> @ Configuration — Enable Java-Based Configuration.

Example —

import org.springframework.boot.SpringApplication;  
import org.springframework.boot.autoconfigure.SpringBootApplication;  
  
@SpringBootApplication  
public class MyApplication {  
  
 public static void main(String[] args) {  
  SpringApplication.run(MyApplication.class, args);  
 }  
  
}


 ###### **@ Component**
We use this annotation at the class level, classes annotated with @ Component will be scanned as spring-managed beans, and we will not require to write explicit code to scan the customized beans we create.

> Spring also provides 3 specific Stereotype annotations which are used to make a class a component — Service, Controller, and Repository (Discussed in the section further)

Example

import org.springframework.stereotype.Component;  
  
  
@Component  
public class HelloWorld {  
    //Logic  
}

## @ Service

This is to annotate the class as the service layer, this simply means that the class will be holding the business logic of the application, and there is no other use for this annotation.

@Service  
public class HelloWorld {  
//Business Logic  
}

## @ Repository

It’s used with the class that deals with the DAO(Data Access Object) layer of the application or It’s used with the repository class which deals with database CRUD operations

@Repository  
public class HelloWorld {  
//Database Crud Operations  
}

## **@ Controller**

A class annotated with @ Controller will handle all the user requests and return an appropriate response back. This annotation is used for Restful Web Services to handle Requests and Responses.

## **@ RequestMapping**

This annotation is used with @ Controller annotation to map HTTP Request to the appropriate handler method. This can be used at the class level or method level.

Example of @ Controller , @ RequestMapping

  
import org.springframework.stereotype.Controller;  
import org.springframework.web.bind.annotation.RequestMapping;  
  
  
@Controller  
@RequestMapping("/hello")  
public class HelloWorld {  
//Http Methods  
}

## @ Autowired

Autowired Injects dependency on spring-managed components automatically, in simple words, it initializes objects for you.

@Controller  
@RequestMapping("/hello")  
public class HelloWorld {  
@Autowired  
HelloService helloService;  
//Http Methods  
}

## @ Qualifier

There can be ambiguity in managing dependency injection when spring finds, more than one bean with the same type, with @ Qualifier annotation we can specify the name of the bean we want to inject

  
@Controller  
@RequestMapping("/hello")  
public class HelloWorld {  
  
    @Autowired   
    @Qualifier("helloServiceBean")  
    HelloService helloService;  
//Http Methods  
}

## @ Bean

This is method-level annotation, used on a method that returns a bean to be managed in the spring context. It is commonly used in configuration classes.

## **@ Configuration**

A class annotated with @ Configuration indicates that the class is going to be used to declare multiple methods to return spring beans

Example of @ Configuration and @ Bean annotation

import org.springframework.context.annotation.Bean;  
import org.springframework.context.annotation.Configuration;  
   
  
@Configuration  
public class HelloWorld {  
  
    @Bean  
    public HelloClass collegeBean()  
    {  
        return new HelloClass();  
    }  
}
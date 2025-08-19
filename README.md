# SpringBoot

## Maven

- Helps to write, compile, run, deploy the program.
- Project mamagenent tool
- Provide external libraries
- Provide dependencies and plugins
- The project structure will remains same if the project is opened in different IDEs

**Archetypes** -  A templating tool [An existing template provided by Maven].

**Dependencies -> Jar file**

### Note :- To download external jar or libraries use **MVN Repository**.

**pom.xml -> Project Object Model** [To handle maven we have to do changes here]

- Every library goes in three things **(GAV)**
- G -> GroupID (Unique)
- A -> ArtifactsId (Project Name)
- V -> VersionId (Version)

### To add dependencies in Maven

- Create a dependencies tag in pom.xml `<dependencies>`
- Inside add the `<dependency>` which you want for the project
- Press sync Maven changes or **Maven -> Sync/Reload All Maven Project**
  
  ![Maven dependencies](https://github.com/user-attachments/assets/817f912a-ccb3-41d7-921d-23a1cce62024)

  **Transitive Dependency** -> When a dependencies is dependent on other.

  **Effective POM** -> Parent of POM
  - Right click on pom.xml -> Maven -> Show effective POM
  - Whatever operation we perform on pom.xml thechanges are done automatically to Effective POM which the project reads.

  **Maven Archetype** -> Templates are called as Archetypes [While creating the project you have to select the archetype].

  **Note ->Try not to use vulnerable libraries.**

  **M2 folder** -> First Maven search dependencies in M2 folder then on internet.
  - If the dependencies is not present in M2 file the Maven will download from internet and keep a copy of that in the M2 file for future use.
  - If any issue with dependencies version go to  M2 folder then delete the version.
 

  # Spring Framework

  - A lightweight framework.
  - Works with POJOs(Plain Old Java Object).
  - https://spring.io/
  - https://docs.spring.io/spring-framework/reference/index.html
 
  ## Prerequisites

  - Core java
  - JDBC
  - Build Tool(Maven or Gradle)
  - Spring ORM(Hibernate)
  - Servlet
 
  ### IDE

  - Eclips - Open Help -> Eclips marketplace -> search Spring tool 4.
  - VS Code - Extension -> Spring Boot Extension Pack and Spring Initializr Java Support.
  - IntelliJ - New Project -> Maven Archetype -> project name ->
 
  ## IoC and DI

  ### Inversion of Control

  - Inverting the control
  - Giving the control of creating , maintaning and destroying object and focusing mainly on the business logic and done even for data flow
  - To achive this in spring we have IoC container where spring will create the objects and it will be kept inside IoC container, this concept is called IoC Principle.
  - ![WhatsApp Image 2025-06-03 at 10 18 11_862fde6c](https://github.com/user-attachments/assets/2a1f48d2-f579-4e9a-bece-d4a2f91e65e2)
  - To make the IoC work we need Dependency Injection.
    
  ### Dependency Injection

  - Helps to inject the object created by IoC into the Application.(Dependency Injection Design Pattern)

  **Ioc is a principle and Dependency Injection is a Design pattern**


  # Creating a Spring Boot Project(Intellij)

  - https://start.spring.io/
  - Do the following
  - ![Screenshot 2025-06-04 202625](https://github.com/user-attachments/assets/4a7348d2-144c-43f9-9cc1-4b996e29de06)
  - If needed add dependencies.
  - Click on generate.
  - A zip file will be downloaded, unzip it.
  - Open intellij -> Open -> Select the unziped project and open.

 # Dependency Injection using spring boot

 - **Any object that is created by spring is called *Beans***.
 - To create an object we have to use `@Component` on top of the class name for which we want to create object.
 - ![Screenshot 2025-06-04 205559](https://github.com/user-attachments/assets/bb8bdc90-da0c-494f-8f6d-1be3f77f17f8)

 - `@Autowired` is used for dependent object, it tells the spring to create the object and wire or connect the object to that perticular class.
 - main is dependent on Alien and it is dependent on Laptop ( Main => Alien => Laptop )
 - ![Screenshot 2025-06-04 211835](https://github.com/user-attachments/assets/58b36988-4865-4542-b051-43664a707633)

# Spring 1st Project

- Follow the steps
- ![Screenshot 2025-06-05 100034](https://github.com/user-attachments/assets/b70e2b95-bd45-435a-8cc9-51b7bd57273b)
- Add spring dependencies (Spring Context) https://mvnrepository.com/artifact/org.springframework/spring-context in pom.xml and load maven changes.
- Since we are using `ClassPathXmlApplicationContext` we have to create a XML file in main -> resources(Create a directory) -> xml file.
- In the XML file we have to mention bean tags `<bean>` are object which are managed by spring framework.
- Open http://docs.spring.io/spring-framework/docs/4.2.x/spring-framework-reference/html/xsd-configuration.html and copy the code add it in the xml file.
- ![Screenshot 2025-06-05 175535](https://github.com/user-attachments/assets/5157e1a3-5116-497f-9eb0-dfc65d2d976b)
- Inside `<beans>` tag create you `bean` tag.
- <bean> tag manages the class object.
- The ApplicationContext creates the container and configuration of the container is mentioned in the file which is passed as a parameter.
- Based on the config xml file the spring will know what class objects needs to be created.
- ![Screenshot 2025-06-05 180205](https://github.com/user-attachments/assets/3b571c3d-509c-47f0-a45a-0f2c964607a0)
- ![Screenshot 2025-06-05 180315](https://github.com/user-attachments/assets/a420a881-9042-47bc-ab40-fd0f1ab36513)


- The object created by spring are stored in IoC containers to get the container we have to use **Application Context**.
- There are two option to work with the container
- 1) BeanFactory(Old one depricated)
  2) ApplicationContext
- ApplicationContext contains all the features of BeanFactory and also contains additional features.

## XML Based Configuration

  ### Object creation

  - Object creation is done in this line  `ApplicationContext context = new ClassPathXmlApplicationContext("spring.xml");`.
  - `Alien obj = (Alien)context.getBean("alien");` which gets the reference of object and stores it in the Obj variable.
  - Constructor are called when ever the object is created for the class ie: in the ApplicationContext Line.
  - Can also create n number of object by creating multiple <bean> tag with different id.
  ![Screenshot 2025-06-06 095555](https://github.com/user-attachments/assets/6f62e7a9-66c1-4e8e-9ee3-96c0f6a7b07f)

  ### Scope

  - Singleton
  - Prototype
  - Request (Only for web or web socket)
  - Session (Only for web or web socket)
  - But in spring core we will use only to Singleton and Prototype.
  - By default it follows Singleton.
  - **If we are creating only one bean tag but want to create multiple object by using getBean(), then we have to specify the scope of the bean**
  ![Screenshot 2025-06-06 100951](https://github.com/user-attachments/assets/eb3e517b-c378-4ad5-82e2-d928c896f8c0)
  - **But when using prototype scope the object won't be created in this line `ApplicationContext context = new ClassPathXmlApplicationContext("spring.xml");`**

  ### Setter Injection

  - Calling a setter method to assign the value.
  - ![Screenshot 2025-06-09 063715](https://github.com/user-attachments/assets/b87af657-f920-477a-b8a8-f171f04a82ad)
  - can use n number of property.
  - For primitive value use "value" in the property.

  ### Ref Attribute

  - For injecting the reference of a object using the Ref attribute.
  - First we should have the bean for that object class.
  - Then pass the id of the bean to the ref attribute.
  - ![Screenshot 2025-06-09 071111](https://github.com/user-attachments/assets/bd5d1d5d-183e-4fe2-a0c3-20094eb7679b)
  - ![Screenshot 2025-06-09 071849](https://github.com/user-attachments/assets/896076ca-2783-4800-b135-9bfc4c90cd69)
  - If we have multiple object pass the id of the object which you want to refer.
  - ![Screenshot 2025-06-09 071742](https://github.com/user-attachments/assets/06c8d458-2ccd-45b8-9862-daca82bacd28)
 
  ### Constructor Injection

  - If we want to assign the value initially when the object is created.
  - To assign a value for constructor we have constructr-args.
  - If we are dealing with multiple parameter then if follows sequence to assign the value.
  - ![Screenshot 2025-06-11 060912](https://github.com/user-attachments/assets/8f990446-8d63-45cf-9744-35d3fab3673a)
  - To map the value to that variable we have many ways
  - 1) By specifying  the `type`.
       ![Screenshot 2025-06-11 064350](https://github.com/user-attachments/assets/3df3bedb-6aa7-4a51-8dce-14345f9efa65)
    2) By specifying the `index`(Starts with 0).
       ![Screenshot 2025-06-11 064518](https://github.com/user-attachments/assets/1a0b8ebc-00cd-4dd7-b0dc-6df0c04ecc94)
    3) By specifying the `name`(But it should follow the sequence).
     - To make the `name` work without sequence we have to specify the `@ConstructorProperties({"name1","name2",...})`
       ![Screenshot 2025-06-11 064850](https://github.com/user-attachments/assets/f8163a40-1a15-48c6-8a6a-0babddd4eac6)

  ## Note: 
 - If we have values which are compulsory then go with constructor injection.
 - If optional value or optional property then use setter injection.

  ### Creating Interface

   - When we are using interface if a new implementation occcurs then no need of changing the main class(Alien).
   - Based on which object we are passing the compile method is called.
   - ![Screenshot 2025-06-12 055159](https://github.com/user-attachments/assets/08fd3720-aefe-4c41-a773-cc8bf7c9297c)
 
  ### Autowiring

  - If we don't want to mention `property` explicitly and wants spring framework to search the dependency based on type or name ..so on then `autowire` is used.
  - Autowire works when we don't use `property`.
  - If we are specifying both autowire and property then the preference goes to property.
  ![Screenshot 2025-06-12 062144](https://github.com/user-attachments/assets/f6eec273-2f4b-4a00-bc93-3319ee295e29)
  - `autowire="byName"` it looks for the matching name
  ![Screenshot 2025-06-12 061117](https://github.com/user-attachments/assets/285b4397-91e9-403c-8256-4cde3e5d9f33)
  - `autowire="byType"` it looks for matching type.
  ![Screenshot 2025-06-12 061521](https://github.com/user-attachments/assets/4064c619-f5a6-4aac-bdf3-cc0946dcc15c)
  - If we have more then one matching type then it will throw an error to solve this we have to set anyone as primary then the problem will be resolved.


  ### Primary Bean

  - By setting primary="true" it solve the confussion for the autowire to choose a bean byType when multipe same type of bean is available.
  ![Screenshot 2025-06-12 062950](https://github.com/user-attachments/assets/6814486f-464a-444c-b8fa-d9b381ff9c5d)
  - Note: Even if we are setting bean as primary="true" but if we have explicitly specified the `property` then the property has more scope, it will consider the ref passed in the property.
  ![Screenshot 2025-06-12 063253](https://github.com/user-attachments/assets/5b3e58d7-176e-40ac-9278-e23ff6489305)

### Lazy Init Bean(Lazy initilization of the Bean)

 - By default all the object are created.
 ![Screenshot 2025-06-12 064718](https://github.com/user-attachments/assets/a6fec0ca-064a-4cf1-9b60-07afa21cbf00)
 - If we want an object to be created when called and don't want it to be created by default. use `lazy-init="true"`
 - Here we are calling the 'Desktop' object so the boject is getting created.
 ![Screenshot 2025-06-12 065103](https://github.com/user-attachments/assets/5cd5abc5-6288-4c7f-aa0d-fd509fcaf53f)
 - Here we are not calling the 'Laptop' object so the object won't get created.
 ![Screenshot 2025-06-12 065252](https://github.com/user-attachments/assets/9bb9780f-34a3-4df7-b147-4a1a0cefe906)
 - **Advantage: it speeds up the application.**

**Note: When we have a non-lazy(eager) bean dependent on a lazy bean, still it will create the object of the lazy bean beacause someone wants it.**

### GetBean by Type
- When we want an object from the container, we will do `context.getBean("name_of_the_bean")` ,which will return the object type, then we have to type cast it.
![Screenshot 2025-06-12 070901](https://github.com/user-attachments/assets/a8e4d78d-abda-4f31-bd40-615f380cfe70)
- To avoid typecasting we can use `context.getBean("name_of_the_bean",Class.type)`
![Screenshot 2025-06-12 071643](https://github.com/user-attachments/assets/c2718583-6f92-4d03-b9d3-3507e4631a9a)
- Even we can do this `context.getBean(Class.type)` and don't specify the id in the bean tag, in this case it will search by type.
![Screenshot 2025-06-12 072620](https://github.com/user-attachments/assets/c876291c-414b-407d-8c03-6bbcbc2affd6)
- But if we create an object for the *interface* and did'nt set the primary then it will cause same error as when we were doing *byType* because two classes *Laptop* and *Desktop* are implementing this interface *Computer*
![Screenshot 2025-06-12 073242](https://github.com/user-attachments/assets/5e5f4254-73b9-4d21-9ccd-1449077f7c89)
- But if we set primary then it works
![Screenshot 2025-06-12 073324](https://github.com/user-attachments/assets/624ef55f-7350-4126-8bb8-f6b2eb79da11)

### InnerBean

- To limit a perticular bean to be used only by perticular dependent bean.
  ![Screenshot 2025-06-12 074618](https://github.com/user-attachments/assets/f338940d-3673-49b8-916e-6fbc650afb44)

  

## Java Based Configuration

  - Create a seperate package for config class.
  - Add a `AppConfig` class in the config package.
  - Here we have to use `ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);`
  - The **AppConfig** class is imported from config package.
  - In **AppConfig** class we will be writing all the configuration.


### Object creation

  - For creating an object we have to use `ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);`
  - Then in **AppConfig** class we have to use the annotation `@Configuration` this makes the class as java configuration class.
  ![Screenshot 2025-06-13 061456](https://github.com/user-attachments/assets/f2326159-ed1b-4ad8-b36e-a83452c01ddb)
  ![Screenshot 2025-06-13 061441](https://github.com/user-attachments/assets/81b1fe3b-45f8-4e56-bcd4-b169a2aa28a4)

### Bean name 

  - We are not specifying the bean name so by default the bean name is the method name.
  ![Screenshot 2025-06-13 062245](https://github.com/user-attachments/assets/cef415e4-fb92-4962-a548-8aeffa4bd864)
  - To change the bean name `@Bean(name="any_name")`
  ![Screenshot 2025-06-13 062612](https://github.com/user-attachments/assets/531fe4d4-bacb-49ab-b40b-2baf430d467a)
  - We can set multiple name
  ![Screenshot 2025-06-13 063844](https://github.com/user-attachments/assets/f9c2340e-9750-475b-97a3-a5794ef55cfe)


### Scope

  - By default the scope of the bean is **Singleton** i.e. only one object can be created by calling `context.getBean()` method, if we use `context.getBean()` multiple time then it will create referene for the         same object.
  - The object is crested in the line `ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);`
  - ![Screenshot 2025-06-17 054911](https://github.com/user-attachments/assets/de05a38d-660b-43b9-b5b2-2d959118b739)
  - To create multiple object we have to set the scope to **Prototype**
  - By setting the scope to prootype we can create multipe object by calling `context.getBean()`.
  - The object is created in the line `context.getBean()`.
  - ![Screenshot 2025-06-17 055420](https://github.com/user-attachments/assets/3a1655ba-cd7b-4b4d-94f8-01e791db729e)

### Autowire

  - If a class is depentent on other class then we have to create a connection(Wiring) between that two classes.
  - To create a wiring/connection we have to use `@Autowire`.
  - Here the Alien class is dependent on Computer class.
  - ![Screenshot 2025-06-17 062730](https://github.com/user-attachments/assets/01ff0927-25ed-4f90-ac9a-7ee3f5bcf4bc)
  - ![Screenshot 2025-06-17 062805](https://github.com/user-attachments/assets/49fe1e1d-d1e7-4ebe-a9c3-5606ecd00e07)
  - ![Screenshot 2025-06-17 062911](https://github.com/user-attachments/assets/b8848630-97db-4d42-a5bb-6315bd65aff0)
  - If we pass desktop() directly then it will make it tightly coupled, What if we are using laptop().
  - ![Screenshot 2025-06-17 062006](https://github.com/user-attachments/assets/8b331908-80cb-4d8f-be9a-8d044cec67f8)

### Primary and Qualifier

  - When we have two bean it will throw an error `No qualifying bean of type 'com.spring.Computer' available: expected single matching bean but found 2: desktop,laptop`
  - Here we are not specifying which bean to use by the Alien class
  - We can achive it by using `@Qualifier("bean_name")`
  - ![Screenshot 2025-06-17 081321](https://github.com/user-attachments/assets/bcb129ad-d0a4-47eb-bdce-6ca59d0709ca)
  - Another approach by using `@Primary`
  - ![Screenshot 2025-06-17 081502](https://github.com/user-attachments/assets/63bb54c6-586e-4cad-9e26-aea131b63c90)

### Component Stereotype Annotation

  - Stereotype Annotation - Where we can talk to our spring framework with the class metadata itself
  - By the help of `@Component` no need of creating **XMLConfig** or **AppConfig** files.
  - ![Screenshot 2025-06-17 083456](https://github.com/user-attachments/assets/dee5225f-1ff9-4b6f-a239-0257d671a9a7)
  - @Component creates the object for the classes for which the @component is used.
  - @ComponentScan("Parent_dir_name") which scan for the class file inside the mentioned dir_name.

### Autowired

- **Field Injection** - When `@Autowired` annotation used in the filed.
- ![Screenshot 2025-06-18 053834](https://github.com/user-attachments/assets/e2a3d376-ef2d-43bf-8ff4-0ac43fcb09fc)
-  **Setter Injection** - When `@Autowired` annotation used in the Setter.
-  ![Screenshot 2025-06-18 054140](https://github.com/user-attachments/assets/d569bbbf-bdbf-4bf3-bc08-3b4a405c9043)
-  **Always prefer to use setter injection over field injection**
-  **Constructor injection** - When `@Autowired` annotation used in Constructor which takes object as a parameter.
-  When two object are there to mention which object to use, use `@Qualifer("class_name_lowercase")` annotation
-  ![Screenshot 2025-06-18 054503](https://github.com/user-attachments/assets/5bfc4ee1-587e-4258-8c97-cc8169b02330)
-  When you want to specify a name for the object
-  ![Screenshot 2025-06-18 054824](https://github.com/user-attachments/assets/9e42e1ee-6143-4675-823d-58d1bc24d2de)

### Primary

- ![Screenshot 2025-06-18 055252](https://github.com/user-attachments/assets/00231de3-a032-4324-aeff-56f3303a6e2e)
- If we use both `@Qualifier` and `@Primary` then the priority is given to `@Qualifier`.
- ![Screenshot 2025-06-18 055451](https://github.com/user-attachments/assets/3ec08c6d-065a-4464-844e-6262d64a80a4)

### Scope and value annotation

- To change the scope of the object,From singleton to prototype(By default singleton)
- ![Screenshot 2025-06-18 055815](https://github.com/user-attachments/assets/e9ebd0c4-823f-4a5d-864b-1225b4c82e3c)
- **Setting value** -Most suitable for optional dependencies.
-  two ways one directly by hardcoding
- ![Screenshot 2025-06-18 060042](https://github.com/user-attachments/assets/f52fcef9-c425-4d3a-b602-e5c795672c37)
- Another way by using `@Value("property_name or value")`
- ![Screenshot 2025-06-18 060202](https://github.com/user-attachments/assets/7b72e690-b9c4-4de9-b410-29bfb703c73e)
- property_name is used when the value is injected from outside the code.

# Spring Boot

![Screenshot 2025-06-18 061747](https://github.com/user-attachments/assets/45840395-5309-4bfe-814d-f5914332c9cf)

## Annotation in spring boot

- Performing the operation which is done in spring to spring boot

  ![Screenshot 2025-06-18 063158](https://github.com/user-attachments/assets/b68b1da3-1685-42d9-87f0-7ed382d38df5)
  ![Screenshot 2025-06-18 063300](https://github.com/user-attachments/assets/5d5a5d78-db1e-4067-b87b-ef310a64a802)
  ![Screenshot 2025-06-18 063331](https://github.com/user-attachments/assets/6352578f-1994-4060-a900-8f9dd323a61c)
  ![Screenshot 2025-06-18 063345](https://github.com/user-attachments/assets/9c43016a-b269-4acb-8a41-5f787ab8e4a7)
  ![Screenshot 2025-06-18 063407](https://github.com/user-attachments/assets/e0d8f30d-e847-4fc2-8dde-a115b07614a6)
  ![Screenshot 2025-06-18 063442](https://github.com/user-attachments/assets/62948017-7be8-4d74-a9f2-8801b48c0dd9)

## Different Layer

  - When we are working with full fleged web application we have three layer client.server and database
  - ![WhatsApp Image 2025-06-19 at 05 48 38_1b84b31b](https://github.com/user-attachments/assets/8c8824b2-afb5-4f83-9d8b-6f0b5d6b2c44)
  - The server is responsible for handling request and response, also server has multiple layers.
  - ![WhatsApp Image 2025-06-19 at 05 50 27_596be7b5](https://github.com/user-attachments/assets/60b7e14d-d6d9-4a6e-8d47-7ad306612f0c)
  - **Controller** job is to only work with the request.
  - **Service** is responsible to any kind processing required.
  - **Repository** if the server wants data from database for processing, we have another layer called **DAO - Data Access Object** aka Repository which is responsible for interacting with the database.
  - ![WhatsApp Image 2025-06-19 at 05 56 05_49526cf2](https://github.com/user-attachments/assets/76bf9076-75d7-4498-8199-c8a4852c4cc4)

  - Consider `SpringBootDemoApplication` has client.
  - Model - actuall entity which will be stored in database.
  - Service - for processing the data.
  - Repository - to interact with data.

![Screenshot 2025-06-19 063327](https://github.com/user-attachments/assets/0b43aaff-049e-44be-8df9-9f24f48a71a4)
![Screenshot 2025-06-19 063400](https://github.com/user-attachments/assets/714aa2f8-3324-4aab-9bf0-9aff69efd490)
![Screenshot 2025-06-19 063410](https://github.com/user-attachments/assets/967b50f1-1e36-4451-83ef-dd8d0d1c04a7)

# Spring JDBC 

  - JDBC template helps
      - Connect with database
      - Fire Queries
      - Process Data
      - Get output
  - Data Source - intermediate between application and dbms which establish connection and maintains it.

## Spring JDBC with H2(in-memory)

  ### JDBC template

  - To create schema we have create a schema.sql in resources folder.
    ![Screenshot 2025-06-20 065433](https://github.com/user-attachments/assets/2ced1e98-b267-495b-b721-05e94dbde695)

  - ExecuteUpdate -> To perform DDL and DML.
    ![Screenshot 2025-06-20 065234](https://github.com/user-attachments/assets/2f049bf0-43a0-4daf-88c0-f977a62c0178)

  - ExecuteQuery -> For Select query.
    ![Screenshot 2025-06-20 073305](https://github.com/user-attachments/assets/1790110e-dc51-4cf4-a35d-65004a19b982)

![Screenshot 2025-06-20 073420](https://github.com/user-attachments/assets/71a76243-1d97-47d9-b890-6b75b525b927)
![Screenshot 2025-06-20 073436](https://github.com/user-attachments/assets/d8d771be-a5ed-47b8-992e-6bd1febf5340)
![Screenshot 2025-06-20 073444](https://github.com/user-attachments/assets/38af71c5-179d-4215-ac16-91709013905d)
![Screenshot 2025-06-20 073526](https://github.com/user-attachments/assets/a6ff6f3e-c715-4217-aaaf-b717bf5c5f50)
![Screenshot 2025-06-20 073710](https://github.com/user-attachments/assets/e54ce6b1-e611-43e7-be7f-8fecf9932db3)

## Connecting to postgresql

- Open https://mvnrepository.com/artifact/org.postgresql/postgresql/42.7.3
- Add the dependencies in pome.xml and reload maven.
- In resources-> application.properties -> Add jdbc url,username,password and driver manager.
- ![Screenshot 2025-06-22 103234](https://github.com/user-attachments/assets/1b7fa262-125b-4eba-b800-da4005a70717)

# Web App

- **Servlet** -> Which accepts the requset, proceess the request and sends back the response to the client.
- To run a servlet we need special container called **Servlet Container or Web Container** like tomcat.

## Creating a ServletProject

- Create a meven project and add dependencies.
- tomcat embed -> https://mvnrepository.com/artifact/org.apache.tomcat.embed/tomcat-embed-core
- Servlet -> https://mvnrepository.com/artifact/javax.servlet/javax.servlet-api
- Create a servlet page (Create java file and extends with HttpServlet)
- ![Screenshot 2025-06-23 070625](https://github.com/user-attachments/assets/777279c9-2f4c-4f7a-bad1-37b6044e9476)
- Run the tomcat server
- ![Screenshot 2025-06-23 070715](https://github.com/user-attachments/assets/6839af6e-eb15-4b78-800f-8bd9d86a94cd)

### Servlet Mapping
- ![Screenshot 2025-06-24 053742](https://github.com/user-attachments/assets/54532891-5ebc-4085-b429-21b9bb296059)
### Sending Client respnse
- ![Screenshot 2025-06-24 054551](https://github.com/user-attachments/assets/89912bce-d2a8-4476-bbf9-f0ffd7f0e40b)

## Introduction to MVC

- ![WhatsApp Image 2025-06-24 at 05 54 31_5f5e72f2](https://github.com/user-attachments/assets/ea90f044-b32e-41aa-84ec-42d1044051dd)
- Tomcat is a server, which is also a servlet container, which can handle only servlets
- Behind the scene JSP file are converted into servlet then the tomcat will handle it.(Include dependencies - tomcat jasper - https://mvnrepository.com/artifact/org.apache.tomcat/tomcat-jasper)

- Creating a jsp file (View)
  ![Screenshot 2025-06-24 061827](https://github.com/user-attachments/assets/28e38b9c-edb2-402a-840d-a5647ca424a0)
- Creating a Controller
  ![Screenshot 2025-06-24 062716](https://github.com/user-attachments/assets/0478f788-abe5-4f52-9cb5-ceb281f634fc)
- Mapping
  ![Screenshot 2025-06-24 065438](https://github.com/user-attachments/assets/6ac077e5-8121-4fd5-bf1b-14d72c1f3f4d)
- Sending data to controller
  By creating a form we can send request to the controller
  ![Screenshot 2025-06-25 055920](https://github.com/user-attachments/assets/6c7c2e18-0d62-4684-8164-b81f3022b0aa)
  Through Url the data is passed to the controller
  ![WhatsApp Image 2025-06-25 at 06 01 20_797767db](https://github.com/user-attachments/assets/803d63f1-9b1e-4b03-b953-9b694c7cc0d4)
- Accepting data the servlet way
  **Dispatcher Servlet** - maps all the request.
  ![Screenshot 2025-06-25 061601](https://github.com/user-attachments/assets/4c9a3333-087a-41fe-8562-b8bf793b4667)
- Display data on the result page
  **Session** - to maintain the data between the pages.
  ![Screenshot 2025-06-25 062730](https://github.com/user-attachments/assets/d5ccb006-731e-4bb2-8039-198bb56358e7)
- RequestParam
  The name should be same
  ![Screenshot 2025-06-25 063412](https://github.com/user-attachments/assets/9ea8c579-3b0e-4c64-86dd-fb362a21a793)
  ![Screenshot 2025-06-25 063509](https://github.com/user-attachments/assets/de059faa-5005-428c-8192-8acfc0a9b9b9)
- Model Object
  ![Screenshot 2025-06-25 064435](https://github.com/user-attachments/assets/b0031af6-565e-4146-bc56-a91aea8eda18)
- Setting Prefix and Suffix
  Prefix -> views (views folder)
  Suffix -> Extension (.jsp)
  ![Screenshot 2025-06-25 065243](https://github.com/user-attachments/assets/6c08b9d8-b272-443a-946f-6c5d1f234771)
  ![Screenshot 2025-06-25 065301](https://github.com/user-attachments/assets/4fa1e3bc-edc0-4763-9f21-6161550da51a)
- Model and View
  ![Screenshot 2025-06-25 070053](https://github.com/user-attachments/assets/8fc962c4-492b-4427-af1b-ae5f4cde4514)
- Model Attribute
  Model Attribute is responsible for assiging the value to the object.
  ![Screenshot 2025-06-26 060558](https://github.com/user-attachments/assets/3c3089ec-b2cd-44ba-a5db-9054bb3b879c)
  ![Screenshot 2025-06-26 060713](https://github.com/user-attachments/assets/75b33fbf-432c-48dc-99ec-20d340d3f4ae)
  ![Screenshot 2025-06-26 060748](https://github.com/user-attachments/assets/4d5b8e36-774f-483b-8a93-790bb9f02e12)
- Model Attrivbute is used on top of methodes which is common for most the requests.
  ![Screenshot 2025-06-26 061308](https://github.com/user-attachments/assets/0bc5e1c6-4ae4-447a-8f69-99e961571d31)

## Introduction to MVC using Spring

- Copy paste all the files from priveous SpringBoot Mvc project to SpringMVCDemo project in eclips.
- Dispatcher Servlet
  Which acts as a front controller and handle all the controller.This is the first servlet we have to go through then this will navigate to differernt controller.
  ![WhatsApp Image 2025-06-27 at 06 13 00_a4ba1600](https://github.com/user-attachments/assets/f06db207-135d-47ea-8f5a-e19d07130d8d)
  ![Screenshot 2025-06-27 062532](https://github.com/user-attachments/assets/088a0776-681b-4258-acc7-182260206098)
- Configuring the dispatcherServlet
  ![Screenshot 2025-06-27 063604](https://github.com/user-attachments/assets/4e5e68d1-3044-44f0-8a83-355f5e098af8)
- Internal Resource view Resolver
  ![Screenshot 2025-06-27 064734](https://github.com/user-attachments/assets/67efd4d9-7a46-421e-b0d0-4475f7b255d2)
  ![Screenshot 2025-06-27 064745](https://github.com/user-attachments/assets/c8e5829b-af4d-46db-b0cf-b89c1812c2ab)


# Building a Job app

- **DTO - Data Transver Object** - The Object is transfered between different layers.


# REST using Spring boot


- REST (Representational State Transfer) APIs are a way for applications to communicate with each other over the internet. They follow a set of principles that make them efficient and widely used in modern web development.
- Traditional: Client Request → Server → JSP Page Response
  REST: Client Request → Server → JSON Data Response

- If we want to develop both a web application and a mobile app, the traditional approach
requires different backend implementations for each.
- By using REST APIs, we can develop the frontend separately (using React, Angular,
mobile native code, etc.). Create a single, unified backend that serves data via REST
APIs. Enable communication between frontend and backend using JSON
![Screenshot 2025-07-03 054730](https://github.com/user-attachments/assets/f9256e81-f1bc-4f2f-8f88-9c86c4e94f4a)
[REST_using_Spring_Boot_Introduction.pdf](https://github.com/user-attachments/files/21026766/REST_using_Spring_Boot_Introduction.pdf)


## What is REST

- REST stands for Representational State Transfer. It's an architectural style for designing networked applications.
- We will be dealing with resources.
- Data are called state.
- Server returns the current state [in JSON (JavaScript Object Notation) or XML format]
[What_is_REST.pdf](https://github.com/user-attachments/files/21026763/What_is_REST.pdf)

 ### HTTP [HyperText Transfer Protocol]
[Http_Methods.pdf](https://github.com/user-attachments/files/21026823/Http_Methods.pdf)

[Understanding_the_React_UI.pdf](https://github.com/user-attachments/files/21026998/Understanding_the_React_UI.pdf)
[Working_with_Postman.pdf](https://github.com/user-attachments/files/21027000/Working_with_Postman.pdf)


 - ![Screenshot 2025-07-07 193139](https://github.com/user-attachments/assets/37ef2b8b-d692-4aab-8817-5ff0c4870e7b)
 - While using `@Controller` if we are returning response body as response insted of view then we have specify that by `@ResponseBody`
 - Else we can use `@RestController` insted of `@Controller` without using `@ResponseBody` annotation.
 - ![Screenshot 2025-07-08 060516](https://github.com/user-attachments/assets/0f2755e3-030d-4d21-b8df-0414219db47d)

### Get Method 

- Controller
  ![Screenshot 2025-07-08 063220](https://github.com/user-attachments/assets/7e1079f3-d494-4807-9585-405c9edda39b)

- Service
  ![Screenshot 2025-07-08 063248](https://github.com/user-attachments/assets/798549f7-8345-450b-b889-041a44fc4e10)

- Repo
  ![Screenshot 2025-07-08 063325](https://github.com/user-attachments/assets/efd5748b-2445-4c61-bfae-6f150b9896bc)


### Path Variable

- `@PathVariable("Variable name")` - Which checks for the path, if available then it finds the parameter(Curley Bracket) which is passed in the URL
- Variable Name - which variable we are targeting.
  ![Screenshot 2025-07-08 063131](https://github.com/user-attachments/assets/c4a0ceb6-7895-4587-8560-b77a9b53e553)


- Controller
  ![Screenshot 2025-07-08 062810](https://github.com/user-attachments/assets/970538bc-1a81-4442-b03f-7a60e7b51c54)

- Service
  ![Screenshot 2025-07-08 062906](https://github.com/user-attachments/assets/39efd1c2-38f3-4fce-a0d6-0befa6d7be25)

- Repo
  ![Screenshot 2025-07-08 062933](https://github.com/user-attachments/assets/38c5dedf-2034-4c5a-9fa8-c16dfc4b25bb)


  ### Post Method

  - Controller
    ![Screenshot 2025-07-08 065234](https://github.com/user-attachments/assets/1c105f24-a495-4bce-ae4d-06ccc6d8dbcb)

  - Service
    ![Screenshot 2025-07-08 065249](https://github.com/user-attachments/assets/3876444f-57c4-45b0-92d6-638ef65bc5fb)

  - Repo
    ![Screenshot 2025-07-08 065307](https://github.com/user-attachments/assets/644b46e2-bd12-4d27-b4bd-d96700c856fd)

  - Postman
    ![Screenshot 2025-07-08 065502](https://github.com/user-attachments/assets/bdd75e37-9578-4521-b6c8-c217abf12b7e)


 ### Put Method

 - Controller
   ![Screenshot 2025-07-08 183358](https://github.com/user-attachments/assets/1f7e473d-3714-40ac-8270-a3c6ea064dad)

 - Service
   ![Screenshot 2025-07-08 183406](https://github.com/user-attachments/assets/ca38975f-0956-49f2-a2ab-c6a560a30de7)

 - Repo
   ![Screenshot 2025-07-08 183419](https://github.com/user-attachments/assets/1cd9bbd5-c33e-43f4-80c0-291862f15987)

 - Postman
   ![Screenshot 2025-07-08 183431](https://github.com/user-attachments/assets/52d669d7-f1b5-4363-91e6-4382eb5cebf3)

### Delete Method

 - Controller
  ![Screenshot 2025-07-08 184626](https://github.com/user-attachments/assets/6d9109da-5ea2-4617-a1cf-5e27e221c98c)
   

 - Service
   ![Screenshot 2025-07-08 184617](https://github.com/user-attachments/assets/b605e7f6-1c4b-4296-9c13-af13a13f7c12)

 - Repo
  ![Screenshot 2025-07-08 184626](https://github.com/user-attachments/assets/6d4fe83c-7e4e-43c1-9b3e-0357b47048d3)

 - Postman
   ![Screenshot 2025-07-08 184805](https://github.com/user-attachments/assets/cf10cead-a426-4eb0-a0ce-e1d3ad599e0a)


# Content Negotiation

  - Negotiating the content by specifing what to produce and what to consume.
  - Jackson library is responsible for converting objects into JSON.
  - To get the same data in XML format add dependency *jackson xml*.
  - By the help of Content negotiation we can restrict the response to be sent in either json or xml.
    ![Screenshot 2025-07-09 062519](https://github.com/user-attachments/assets/93938a9f-aed4-4bd9-9bd0-d7fbecf21fd7)
    By specifying the above it will only return json data.
  - Like wise for sending data
     ![Screenshot 2025-07-09 062933](https://github.com/user-attachments/assets/42430237-6c60-403e-ad56-63d1966095ed)
    Here it only accepts xml data.

# Spring data JPA

## ORM - Object Relational Mapping

- Creating a database table using class with the help of tools, the tool is called ORM tool.
- The object and relational mapping is done here.
- Each object is considered as row.

## JPA (Java Persistence API)

- Spring JPA is a module in spring ecosystem which will simplify the task.
- Specification which is used to connect with ORM tool is called JPA.
- In future if we wanna switch the ORM tool there will be only minor changes in the code.
- If we are using ORM tool like hibernate or Spring Autumn then we have to write lot of code, so to simplify it we will be using JPA.

### Creating Table and Insert using JPA

![Screenshot 2025-07-10 063431](https://github.com/user-attachments/assets/b8d18b54-3089-464f-b750-50ff1d9918db)
![Screenshot 2025-07-10 063448](https://github.com/user-attachments/assets/c21d1875-2676-4c62-8d48-8466361ca687)
![Screenshot 2025-07-10 063456](https://github.com/user-attachments/assets/ea10ba93-68bc-4681-bde4-385d54c0f6a5)
![Screenshot 2025-07-10 063920](https://github.com/user-attachments/assets/de52f232-edd8-4849-bd83-4c80e807c33d)
![Screenshot 2025-07-10 063929](https://github.com/user-attachments/assets/bca50b81-1b08-4046-a3e5-34fb999d10f0)
![Screenshot 2025-07-10 063935](https://github.com/user-attachments/assets/70340575-d213-4f51-890e-a9ea67860c3d)


### Fetching data

**FindAll**

<img width="1914" height="988" alt="Screenshot 2025-07-29 060956" src="https://github.com/user-attachments/assets/156270e3-14ee-4fe3-8d67-005d43064900" />

**FindById**

<img width="1842" height="941" alt="Screenshot 2025-07-29 061940" src="https://github.com/user-attachments/assets/8fb89e3d-fa43-4598-aaf0-a69227822d41" />

<img width="1918" height="962" alt="Screenshot 2025-07-29 061857" src="https://github.com/user-attachments/assets/551644a7-90e8-42fc-8187-1f9638364910" />

### JPQL Query

- If we want a method which is not present by default in the JPA repository, we can specify it by the help of `@Query(JPQL query)`.
- Like search by name so on..

- <img width="1878" height="964" alt="Screenshot 2025-07-30 053455" src="https://github.com/user-attachments/assets/eb05d950-eced-44bd-b19c-9a237931be53" />

- **Note- The above method will work even if we remove the *query annotation*, it will only work for few cases because JPA uses DSL(Domain Specific Language) which creates certain merhods behind the screen.**
- For this make sure method name starts with *findBy[variable_name]* like findByMarks, findByAge, findByMarksGreaterThan so on..
<img width="1109" height="85" alt="Screenshot 2025-07-30 062042" src="https://github.com/user-attachments/assets/40ac3e9b-2be2-464c-8220-6cec43b6616e" />

### Update and Delete

**Update**

- For Update we will be using save() method.
- <img width="1919" height="942" alt="Screenshot 2025-07-30 054840" src="https://github.com/user-attachments/assets/30e0c2a0-fedc-46ab-8acc-c389ed23dee4" />

**Delete**

- <img width="1916" height="982" alt="Screenshot 2025-07-30 055026" src="https://github.com/user-attachments/assets/5c5821e8-9513-4fe0-8639-eb059b27b5d3" />

# Spring Boot MVC Project

# Spring Data Rest

- Helps to develop project without creating controller and service layer
- Automatically generates the end point (By performing get reequest we can get the other endpoints(HATEOAS)
- HATEOAS - Links which holds the address of the other resources

# Spring AOP (Aspect Oriented Programming)

- It solves the problem of cross cutting concerns means while developing an application other then business logic like security, logs, validation and exception so on...
- We can develop a seperate class to do perform this concerns and no need of calling those function instead with the help of AOP it will be called automatically.

# Annotations: 

- `@Component` - Used on top of the class name for which you want to create an object.
- `@Service` - It is also similar to the Component annotation, both does the same thing, to understand what type of class we are using we will use service on top of service classes.
- `@Repository` - It is also similar to the Coponent and Service annotation, The thee will be used for Domain-Driven design(While building a MVC architecture to identify the classes)
- `@Scope("Prototype")` - Used to set the scope, by default it will be singleton.



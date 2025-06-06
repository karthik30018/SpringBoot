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



# Annotations: 

- `@Component` - Used on top of the class name for which you want to create an object.

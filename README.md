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







# Annotations: 

- `@Component` - Used on top of the class name for which you want to create an object.

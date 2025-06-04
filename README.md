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


# Annotations: 

- `@Component` - Used on top of the class name for which you want to create an object.

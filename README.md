# Spring Boot Hello World Example with JSP

- [Executable jar version](#jar)
- [War version](#war)


Branch:
--
There are two branchs under this repository.  ** war ** and ** jar ** , checkout different branch for need.
There are significant differences between jar verion and war version.



## war

<a id="war" />
	
- Gradle

you won't privid this at compile time, but at runtime.
```
providedRumtime("org.apache.tomcat.embed:tomcat-embed-jasper")
providedRumtime("org.springframework.boot:spring-boot-starter-tomcat")
```		
you must use the plugin war
```
apply plugin: 'war' 
```

way to use:
```
drop it into  tomcat's  webapp folder.

http://localhost:80/springboot_jsp
```

## Reference
<a id="reference"></a>
https://hellokoding.com/spring-boot-hello-world-example-with-jsp/

## What you'll need
- JDK 1.7 or later
- Maven 3 or later
- Gradle 2.3 later

## Stack
- Spring Boot
- Java

## Run
`mvn spring-boot:run`



## jar 
<a id="jar" />	



Executable Spring-boot jar ?
==
It's proved that spring-boot doesn't support **jsp** very well.  don't not waste time on this. But it does NOT mean you cannot use executable jar, just because it is not friendly to **jsp**, but you can use HTML5, Thymeleaf, Freemarker, etc.  Lean more: 

[https://dzone.com/articles/spring-boot-with-jsps-in-executable-jars-1](https://dzone.com/articles/spring-boot-with-jsps-in-executable-jars-1)

- Maven

If you want to generate a executable jar file,   you have to use this plug-in,  actually, It's heavily rely on this plug-in(1.4.2 this version only, so far.).
```
<groupId>org.springframework.boot</groupId>
<artifactId>spring-boot-maven-plugin</artifactId>
<version>1.4.2.RELEASE</version>
```
for more detail, please refer to the pom.xml in this sample.

run ``` mvn clean package ``` to  create the jar file.     But the more complicated your project is, the more trouble you encounter, I promise. so again. 

### do NOT waste time on  executable jar which support jsp. ###

To support jsp means you can access using url like  http://xxxx.com/xxx.jsp   


in the build.gradle file  (this DOES NOT work well,  you can only run this in eclipse,  so package this project with maven.)

- Gradle

you need to privid this at compile time instead of runtime.
```
compile("org.apache.tomcat.embed:tomcat-embed-jasper")
compile("org.springframework.boot:spring-boot-starter-tomcat")
```		
and what's more, you need add the -- /webapp -- path into resource path, because in jar version,  gradle just simply ignore this folder. so you need to add it manually.
```
sourceSets.main.resources.srcDirs = ['src/main/webapp','src/main/resources']
```

and in application.properties,  you need to set the view resolver for jsp.
```
spring.mvc.view.prefix: /WEB-INF/jsp/
spring.mvc.view.suffix: .jsp
```

- Run this way:

``` 
java -jar  xxxx.jar 
```

you can see different things by clicking: 

http://localhost:80

http://localhost:80/index.jsp

http://localhost:80/hello


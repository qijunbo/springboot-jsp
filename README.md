# Spring Boot Hello World Example with JSP

## Guide
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

Branch:
--
There are two branchs under this repository.  ** war ** and ** jar ** , checkout different branch for need.
There are significant differences between jar verion and war version.

- jar 
	
in the build.gradle file

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

build this way:
```
java -jar  xxxx.jar

http://localhost:80

http://localhost:80/index.jsp
```
- war

	
in the build.gradle file

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

http://localhost:8080/springbootjsbapp
```
	
# Learning Notes

Pluralsight course -
Creating Your First Spring Boot Application
by Dan Bunker

## Spring boot dependency
```
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>1.5.6.RELEASE</version>
</parent>
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
</dependencies>
```

## h2/jpa/flyway dependency
Sidenotes: tomcat-jdbc, HikariCP, Commons-DBCP, Commons-DBCP2 
```
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
<dependency>
  <groupId>com.h2database</groupId>
  <artifactId>h2</artifactId>
</dependency>

<dependency>
  <groupId>org.flywaydb</groupId>
  <artifactId>flyway-core</artifactId>
</dependency>
```

## Spring test
Sidenotes: Mockito, Hamcrest
```
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-test</artifactId>
  <scope>test</scope>
</dependency>
```

## Properties
`application-{profile}.properties`

`-Dspring.profiles.active=prod``

```
logging.level.org.springframework.web=DEBUG

server.port=8080

spring.h2.console.enabled=true
spring.h2.console.path=/h2

spring.datasource.url=jdbc:h2:file:~/dasboot
spring.datasource.username=sa
spring.datasource.password=
spring.datasource.driver-class-name=org.h2.Driver

flyway.baseline-on-migrate=true
spring.jpa.hibernate.ddl-auto=false
```
Sidenotes: SnakeYAML, spring.mvc.date-format

## Issues and solutions
1. Project build error: Non-resolvable parent POM

Solution:

Right click the project->Maven->Update Project->Check checkbox "Force Update of Snapshots/Releases". Click OK.

2. java.net.BindException: Address already in use: bind

Solution:

Use different port or kill the process which holds the port

3. org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'flywayInitializer' defined in class path resource [org/springframework/boot/autoconfigure/flyway/FlywayAutoConfiguration$FlywayConfiguration.class]: Invocation of init method failed; nested exception is org.flywaydb.core.api.FlywayException: Unable to scan for SQL migrations in location: classpath:db/migration

Solution:

Ensure the db.migration is exists

4. No compiler is provided in this environment. Perhaps you are running on a JRE rather than a JDK?

Solution:

On your Eclipse IDE, go into Window > Preferences > Java > Installed JREs > and check your installed JREs. You should have an entry with a JDK there.
Select the Execution Env as show below. Click OK
Then Right-Click on your Project -> Maven -> Update Project

## Resources
* https://app.pluralsight.com/library/courses/spring-boot-first-application/table-of-contents
* `git clone https://github.com/dlbunker/ps-spring-boot-resources.git`
* http://projects.spring.io/spring-boot/#quick-start
* http://start.spring.io/
* http://docs.spring.io/spring-boot/docs/current/reference/html/common-application-properties.html

## Sidenotes
maven.archetype-quickstartv1.1 BDM - Bill of materials, Jackson, log4j

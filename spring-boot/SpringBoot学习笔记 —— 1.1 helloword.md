
## 使用 Intellig IDEA 创建第一个 Spring Boot 项目 —— hello

1. `File` --> `New` --> `Project` --> `Spring Initializr` --> `Next`
2. 输入项目信息

    ```
    Group: `demo.springboot`
    Artifact: `hello`
    ```

3. 选择依赖

    - JPA
    - MySQL
    - Web

4. 输入项目名称、保存路径，点击`Finish`

## 项目结构

### pom.xml 文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>demo.springboot</groupId>
    <artifactId>hello</artifactId>
    <version>0.0.1-SNAPSHOT</version>
    <packaging>jar</packaging>

    <name>hello</name>
    <description>Demo project for Spring Boot</description>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.5.7.RELEASE</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>

    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <project.reporting.outputEncoding>UTF-8</project.reporting.outputEncoding>
        <java.version>1.8</java.version>
    </properties>

    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-data-jpa</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <scope>runtime</scope>
        </dependency>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
</project>
```

### 依赖树

```
demo.springboot:hello:jar:0.0.1-SNAPSHOT
+- org.springframework.boot:spring-boot-starter-data-jpa:jar:1.5.7.RELEASE:compile
|  +- org.springframework.boot:spring-boot-starter:jar:1.5.7.RELEASE:compile
|  |  +- org.springframework.boot:spring-boot:jar:1.5.7.RELEASE:compile
|  |  +- org.springframework.boot:spring-boot-autoconfigure:jar:1.5.7.RELEASE:compile
|  |  +- org.springframework.boot:spring-boot-starter-logging:jar:1.5.7.RELEASE:compile
|  |  |  +- ch.qos.logback:logback-classic:jar:1.1.11:compile
|  |  |  |  \- ch.qos.logback:logback-core:jar:1.1.11:compile
|  |  |  +- org.slf4j:jul-to-slf4j:jar:1.7.25:compile
|  |  |  \- org.slf4j:log4j-over-slf4j:jar:1.7.25:compile
|  |  \- org.yaml:snakeyaml:jar:1.17:runtime
|  +- org.springframework.boot:spring-boot-starter-aop:jar:1.5.7.RELEASE:compile
|  |  +- org.springframework:spring-aop:jar:4.3.11.RELEASE:compile
|  |  \- org.aspectj:aspectjweaver:jar:1.8.10:compile
|  +- org.springframework.boot:spring-boot-starter-jdbc:jar:1.5.7.RELEASE:compile
|  |  +- org.apache.tomcat:tomcat-jdbc:jar:8.5.20:compile
|  |  |  \- org.apache.tomcat:tomcat-juli:jar:8.5.20:compile
|  |  \- org.springframework:spring-jdbc:jar:4.3.11.RELEASE:compile
|  +- org.hibernate:hibernate-core:jar:5.0.12.Final:compile
|  |  +- org.jboss.logging:jboss-logging:jar:3.3.1.Final:compile
|  |  +- org.hibernate.javax.persistence:hibernate-jpa-2.1-api:jar:1.0.0.Final:compile
|  |  +- org.javassist:javassist:jar:3.21.0-GA:compile
|  |  +- antlr:antlr:jar:2.7.7:compile
|  |  +- org.jboss:jandex:jar:2.0.0.Final:compile
|  |  +- dom4j:dom4j:jar:1.6.1:compile
|  |  \- org.hibernate.common:hibernate-commons-annotations:jar:5.0.1.Final:compile
|  +- org.hibernate:hibernate-entitymanager:jar:5.0.12.Final:compile
|  +- javax.transaction:javax.transaction-api:jar:1.2:compile
|  +- org.springframework.data:spring-data-jpa:jar:1.11.7.RELEASE:compile
|  |  +- org.springframework.data:spring-data-commons:jar:1.13.7.RELEASE:compile
|  |  +- org.springframework:spring-orm:jar:4.3.11.RELEASE:compile
|  |  +- org.springframework:spring-context:jar:4.3.11.RELEASE:compile
|  |  +- org.springframework:spring-tx:jar:4.3.11.RELEASE:compile
|  |  +- org.springframework:spring-beans:jar:4.3.11.RELEASE:compile
|  |  +- org.slf4j:slf4j-api:jar:1.7.25:compile
|  |  \- org.slf4j:jcl-over-slf4j:jar:1.7.25:compile
|  \- org.springframework:spring-aspects:jar:4.3.11.RELEASE:compile
+- org.springframework.boot:spring-boot-starter-web:jar:1.5.7.RELEASE:compile
|  +- org.springframework.boot:spring-boot-starter-tomcat:jar:1.5.7.RELEASE:compile
|  |  +- org.apache.tomcat.embed:tomcat-embed-core:jar:8.5.20:compile
|  |  +- org.apache.tomcat.embed:tomcat-embed-el:jar:8.5.20:compile
|  |  \- org.apache.tomcat.embed:tomcat-embed-websocket:jar:8.5.20:compile
|  +- org.hibernate:hibernate-validator:jar:5.3.5.Final:compile
|  |  +- javax.validation:validation-api:jar:1.1.0.Final:compile
|  |  \- com.fasterxml:classmate:jar:1.3.4:compile
|  +- com.fasterxml.jackson.core:jackson-databind:jar:2.8.10:compile
|  |  +- com.fasterxml.jackson.core:jackson-annotations:jar:2.8.0:compile
|  |  \- com.fasterxml.jackson.core:jackson-core:jar:2.8.10:compile
|  +- org.springframework:spring-web:jar:4.3.11.RELEASE:compile
|  \- org.springframework:spring-webmvc:jar:4.3.11.RELEASE:compile
|     \- org.springframework:spring-expression:jar:4.3.11.RELEASE:compile
+- mysql:mysql-connector-java:jar:5.1.44:runtime
\- org.springframework.boot:spring-boot-starter-test:jar:1.5.7.RELEASE:test
   +- org.springframework.boot:spring-boot-test:jar:1.5.7.RELEASE:test
   +- org.springframework.boot:spring-boot-test-autoconfigure:jar:1.5.7.RELEASE:test
   +- com.jayway.jsonpath:json-path:jar:2.2.0:test
   |  \- net.minidev:json-smart:jar:2.2.1:test
   |     \- net.minidev:accessors-smart:jar:1.1:test
   |        \- org.ow2.asm:asm:jar:5.0.3:test
   +- junit:junit:jar:4.12:test
   +- org.assertj:assertj-core:jar:2.6.0:test
   +- org.mockito:mockito-core:jar:1.10.19:test
   |  \- org.objenesis:objenesis:jar:2.1:test
   +- org.hamcrest:hamcrest-core:jar:1.3:test
   +- org.hamcrest:hamcrest-library:jar:1.3:test
   +- org.skyscreamer:jsonassert:jar:1.4.0:test
   |  \- com.vaadin.external.google:android-json:jar:0.0.20131108.vaadin1:test
   +- org.springframework:spring-core:jar:4.3.11.RELEASE:compile
   \- org.springframework:spring-test:jar:4.3.11.RELEASE:test
```

### 依赖说明

- `spring-boot-starter-parent`：
- `spring-boot-starter-data-jpa`：
- `spring-boot-starter-web`：
- `spring-boot-starter-test`：


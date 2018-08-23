# slf4j + log4j.xml 을 이용한 스프링 로그 설정

## pom.xml 설정
    <dependency> <!----------------------------------------------- ⓐ -->
        <groupId>org.springframework</groupId>
        <artifactId>spring-context</artifactId>
        <version>${spring.version}</version>
        <exclusions><!-- Exclude Commons Logging in favor of SLF4j --> 
            <exclusion>
                <groupId>commons-logging</groupId> 
                <artifactId>commons-logging</artifactId> </exclusion>
            </exclusions>
    </dependency>
    <dependency> <!----------------------------------------------- ⓑ -->    
        <groupId>org.slf4j</groupId>
        <artifactId>jcl-over-slf4j</artifactId>
        <version>${org.slf4j.version}</version> <scope>runtime</scope>
    </dependency>
    <dependency> <!----------------------------------------------- ⓒ -->  
        <groupId>org.slf4j</groupId>
        <artifactId>slf4j-log4j12</artifactId>
        <version>${org.slf4j.version}</version>
    </dependency>

- ⓐ - spring-context에서 commons-logging을 배제한 jar파일을 import  
- ⓑ - jcl-over-slf4j-x.x.x.jar, slf4j-api-x.x.x.jar 파일을 import  
- ⓒ - slf4j-log4j12-x.x.x.jar, log4j-x.x.x.jar 파일을 import  

- ### log4j 대신 logback을 사용하려면 logback관련 jar파일을 import

## log4j.xml

    <?xml version="1.0" encoding="UTF-8" ?>
    <!DOCTYPE log4j:configuration PUBLIC "-//LOGGER" "log4j.dtd">

    <log4j:configuration xmlns:log4j="http://jakarta.apache.org/log4j/">
    
        <!-- Appenders -->
        <appender name="console" class="org.apache.log4j.ConsoleAppender">
            <param name="Target" value="System.out" />
            <layout class="org.apache.log4j.PatternLayout">
                <param name="ConversionPattern" value="[%d{yyyy-MM-dd HH:mm}] %5p [%C{1}(%M:%L)] :%m%n%n" />
            </layout>
        </appender>

        <!-- 3rdparty Loggers -->
        <logger name="org.springframework" additivity="false">
            <level value="INFO" />
            <appender-ref ref="console"/>
        </logger>
        
        <!-- Root Logger -->
        <root>
            <level value="INFO" />
            <appender-ref ref="console" />
        </root>

    </log4j:configuration>

- ### classpath 최상단에 log4j.xml을 저장

- ### log4j.properties보다는 log4j.xml을 먼저 참조

## 출처
- http://kimddochi.tistory.com/103 [김또치세상]
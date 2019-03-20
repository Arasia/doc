# slf4j + log4j.xml 을 이용한 스프링 로그 설정

## slf4j + log4j
- ### slf4j
        java.uilt.logging, Logback, Log4j와 같은 다양한 logging framework의
        추상체 역활을 하여 logging framework을 교체하는 경우 적은 수정으로 교체 가능

- ### slf4j example
    ![example](slf4j_example.png)


- ### maven pom.xml 설정
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

- ### logger 사용시 slf4j의 class를 import하여 사용
- ### log4j 대신 logback을 사용하려면 logback관련 jar파일을 import

---

## log4j
- ### Log4j level
    ![level](log4j_level.png)

- ### Log4j pattern Option
    ![pattern Option](log4j_pattern_option.png)

- ### Log4j important Class
    ![important Class](log4j_important_class.png)

- ### log4j.xml

        <?xml version="1.0" encoding="utf-8"?>
        <!DOCTYPE log4j:configuration SYSTEM "log4j.dtd">

        <log4j:configuration xmlns:log4j="http://jakarta.apache.org/log4j/" debug="false">
            
            <appender name="console" class="org.apache.log4j.ConsoleAppender">
                <layout class="org.apache.log4j.PatternLayout">
                    <param name="ConversionPattern"
                        value="[%-5p][%d{yyyyMMdd HH:mm:ss.SSS}][%t]%c{4}.%M(%L) - %m%n" />
                </layout>
        </appender>
            
            
            <appender name="logfile" class="org.apache.log4j.DailyRollingFileAppender">
                <param name="datePattern" value=".yyyy-MM-dd"/> 
                <param name="File" value="D:\\logs\\jwtTest.log" />
                <param name="Append" value="true" />
                <layout class="org.apache.log4j.PatternLayout">
                    <param name="ConversionPattern" value="[%-5p][%d{yyyyMMdd HH:mm:ss.SSS}][%t]%c{4}.%M(%L) - %m%n" />
                </layout>
            </appender>
            
            <logger name="com.raon.jwt" additivity="false">
                <level value="DEBUG" />
                <appender-ref ref="logfile" />
                <appender-ref ref="console" />
            </logger>
            
            <root>
                <level value="DEBUG" />
                <appender-ref ref="logfile" />
                <appender-ref ref="console" />
            </root>
            
        </log4j:configuration>

    - ### classpath 최상단에 log4j.xml을 저장

    - ### log4j.properties보다는 log4j.xml을 먼저 참조

## 출처
- http://kimddochi.tistory.com/103 [김또치세상]
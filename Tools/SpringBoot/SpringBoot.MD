# 개요
    현재 문서는 Spring Boot 2.1.3 Release를 기준으로 작성되었습니다.

---

# Properties 설정 및 가져오기

## Properties 적용 우선순위

    1. Devtools global settings properties on your home directory (~/.spring-boot-devtools.properties when devtools is active).
    2. @TestPropertySource annotations on your tests.
    3. properties attribute on your tests. Available on @SpringBootTest and the test annotations for testing a particular slice of your application.
    4. Command line arguments.
    5. Properties from SPRING_APPLICATION_JSON (inline JSON embedded in an environment variable or system property).
    6. ServletConfig init parameters.
    7. ServletContext init parameters.
    8. JNDI attributes from java:comp/env.
    9. Java System properties (System.getProperties()).
    10. OS environment variables.
    11. A RandomValuePropertySource that has properties only in random.*.
    12. Profile-specific application properties outside of your packaged jar (application-{profile}.properties and YAML variants).
    13. Profile-specific application properties packaged inside your jar (application-{profile}.properties and YAML variants).
    14. Application properties outside of your packaged jar (application.properties and YAML variants).
    15. Application properties packaged inside your jar (application.properties and YAML variants).
    16. @PropertySource annotations on your @Configuration classes.
    17. Default properties (specified by setting SpringApplication.setDefaultProperties).

- 참조 : https://docs.spring.io/spring-boot/docs/current/reference/html/boot-features-external-config.html

## Application.properties
    Spring Boot를 구동하는 설정을 지정하는 파일
### Application.properties 우선순위

    1. A /config subdirectory of the current directory
    2. The current directory
    3. A classpath /config package
    4. The classpath root

### Application.properties 구성요소
    server.port
    server.sevlet.context-path
    server.ssl.*
    logging.*
    기타 Spring boot 구동 관련 설정...
### Application.properties 예시

    #server config 
    server.port=3080
    server.servlet.context-path=
    server.ssl.enabled=true
    server.ssl.key-alias=sp
    server.ssl.key-password=12qwaszx
    server.ssl.key-store=C:/dev/ssl/sp.jks
    server.ssl.key-store-password=12qwaszx
    server.ssl.trust-store=C:/dev/ssl/sp.ts
    server.ssl.trust-store-password=12qwaszx
    
    #health check config
    management.endpoints.jmx.exposure.include=health
    
    #log config
    logging.config=classpath:config/log/logback-spring.xml
    logging.path= D:/logs
    logging.file= Server

## 추가적인 Properties

### @EnableConfigurationProperties
> 추가적인 Properties를 사용 가능하도록 설정 

### @ProperteySource
> 추가적인 Properties의 경로를 지정하여 Spring boot에 등록

### Environment.Class
> Environment Class를 통하여 등록된 Properties의 값들을 읽어온다.

---

# @ImportResource

---

# LogAspect

---


# Maven Install Linux

## Install

- ### 다운로드
        wget http://mirror.apache-kr.org/maven/maven-3/3.2.5/binaries/apache-maven-3.2.5-bin.tar.gz
- ### 설치
        tar zxvf apache-maven-3.2.5-bin.tar.gz

## 환경설정
- ### vi /etc/profile.d/maven.sh
        #!/bin/bash 
        MAVEN_HOME=/usr/lib/apache-maven-3.2.5
        PATH=$MAVEN_HOME/bin:$PATH 
        export PATH MAVEN_HOME 
        export CLASSPATH=.

## 환경설정2
- ### vi ./.bash_profile
        export MAVEN_HOME=/usr/lib/apache-maven-3.2.5 추가
        PATH에 $MAVEN_HOME/bin 추가

## 실행권한 부여
    chmod +x /etc/profile.d/maven.sh
    source /etc/profile.d/maven.sh

## 설치 확인
- ### mvn --version
        Apache Maven 3.2.5 (12a6b3acb947671f09b81f49094c53f426d8cea1; 2014-12-15T02:29:23+09:00)
        Maven home: /usr/local/apache-maven-3.2.5
        Java version: 1.8.0_191, vendor: Oracle Corporation
        Java home: /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.191.b12-1.el7_6.x86_64/jre
        Default locale: ko_KR, platform encoding: UTF-8
        OS name: "linux", version: "3.10.0-957.1.3.el7.x86_64", arch: "amd64", family: "unix"
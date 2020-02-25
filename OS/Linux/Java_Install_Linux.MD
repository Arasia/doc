# Java Install

## 설치가능 버전 확인
- ### yum list java*jdk-devel
        설치가능한 버전 리스트

## 설치명령어
- ### yum install java파일명

## 설치 결과 확인
- ### 버전확인
    - ### javac -version  
            javac java버전
    - ### rpm -qa java*jdk-devel
            설치된 javaJdk 파일명

# Java 환경변수
## 환경변수 확인
- ### $JAVA_HOME
    - ### echo $JAVA_HOME
            Java 설치 위치
- ### javac 위치 확인
    - ### which javac
            javac 위치
    - ### readlink -f /usr/bin/javac
            javac의 원본 파일 위치
## 환경변수 설정
- ### $JAVA_HOME 설정
    - ### vi /etc/profile
            파일의 최하단에 추가
                export JAVA_HOME=java설치위치
- ### 환경변수 적용
    - ### soruce /etc/profile

---

## java 설치
- ### java_8

    - ### PPA 추가
            sudo add-apt-repository ppa:webupd8team/java
    - ### apt 업데이트
            sudo apt update
    - ### java 8 설치
            sudo apt install oracle-java8-installer
    - ### version 체크
            javac -version
            java -version
    - ### 환경변수 자동 설정
            sudo apt install oracle-java8-set-default
    - ### 환경변수 수동 설정
            vim /etc/environment
                JAVA_HOME=/usr/lib/jvm/java-8-oracle/jre
            source /etc/environment
            export JAVA_HOME=/usr/lib/jvm/java-8-oracle/jre
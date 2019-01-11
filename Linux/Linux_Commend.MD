## 퍼미션
- ### 퍼미션 확인
        ls -al
- ### 퍼미션 변경
        chmod (권한숫자) (파일이름)
        ( r = 4 , w = 2 , x = 1 )
            -R : 하위 디렉토리의 모든 폴더 및 파일 일괄 변경
- ### 소유자 변경
        chown (변경할 소유자) (파일이름)

## 네트워크
- ### 포트확인
        netstat -tnlp

        nmap localhost

## java 설치
- ### java_8
        1. PPA 추가
            sudo add-apt-repository ppa:webupd8team/java
        2. apt 업데이트
            sudo apt update
        3. java 8 설치
            sudo apt install oracle-java8-installer
        4. version 체크
            javac -version
            java -version
        5-1. 환경변수 자동 설정
            sudo apt install oracle-java8-set-default
        5-2. 환경변수 수동 설정
            vim /etc/environment
                JAVA_HOME=/usr/lib/jvm/java-8-oracle/jre
            source /etc/environment
            export JAVA_HOME=/usr/lib/jvm/java-8-oracle/jre
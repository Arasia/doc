# Ant Install Linux

## Install

- ### 다운로드
        wget http://mirror.apache-kr.org//ant/binaries/apache-ant-1.9.13-bin.tar.gz

- ### 설치
        tar zxvf apache-ant-1.9.13-bin.tar.gz

## 환경설정
- ### vi /etc/profile.d/ant.sh
        ANT_HOME=/usr/lib/apache-ant-1.9.13
        PATH=$ANT_HOME/bin:$PATH 
        export ANT_HOME
        export PATH 

## 환경설정2
- ### vi ./.bash_profile
        export ANT_HOME=/usr/lib/apache-ant-1.9.13 추가
        PATH에 $ANT_HOME/bin 추가

## 실행권한 부여
    chmod +x /etc/profile.d/ant.sh
    source /etc/profile.d/ant1.sh

## 설치 확인ls
ls

- ### ant -version
        Apache Ant(TM) version 1.9.13 compiled on July 10 2018
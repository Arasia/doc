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

## yum이 lock 걸렸을때
- ### pid 삭제
        rm -rf /var/run/yum.pid
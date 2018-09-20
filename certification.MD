

# 생성방법

## RSA
### 1. key 파일 생성
    openssl genrsa -out server.key 2048
### 2. csr 생성
    openssl req -new -key server.key -out server.csr
### 3. x509 인증서 생성
    openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt

## DSA

### 1. key 파일 및 param 파일 생성
    openssl dsaparam -out server_param.pem -genkey 2048
    openssl gendsa -out server.key server_param.pem
### 2. csr 생성
    openssl req -new -key server.key -out server.csr
### 3. x509 인증서 생성
    openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt


## PEM/PFX 파일 jks 파일로 변환

### 1. PEM을 PKCS#12로 변환
#### cert.pem 파일로 통합  
    cat domain.crt chain1.crt chain2.crt root.crt > cert.pem
#### cert.pfx 파일로 저장
    openssl pkcs12 -export -name example.com -in cert.pem -inkey private.key -out cert.pfx

### 2. pfx에서 jks로 변환
    keytool -importkeystore -srckeystore cert.pfx -srcstoretype pkcs12 -destkeystore cert.jks -deststoretype jks

### 3. jks 인증서 확인
    keytool -list -v -keystore cert.jks

## jks 파일 pfx 파일로 변환
    keytool -importkeystore -srckeystore cert.jks -srcstoretype JKS -srcstorepass "password" -destkeystore cert.pfx -deststoretype PKCS12 -deststorepass "password"

## jsk 파일 비밀번호/alias 변경

### 1. keystore 비밀번호 변경
    keytool.exe -storepasswd -new 변경될 비밀번호 -keystore cert.jks

### 2. key 비밀번호 변경
    keytool.exe -keypasswd -alias www.securesign.kr -keystore cert.jks

### 3. alias 변경
    keytool.exe -changealias -keystore cert.jks -alias www.securesign.kr -destalias 변경될 Alias 이름
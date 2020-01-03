
## required

    2.54 (2017-04) and newer: Java 8
    1.612 (2015-05) and newer: Java 7

## Install 
- ### yum repo setting
        sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
        
        sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key

- ### Install Jenkins
        yum install jenkins

- ### Jenkins Port Setting
        vi /etc/sysconfig/jenkins
        
        change port num
        JENKINS_PORT="Port num"

- ### firewall setting
    - ### add port
            firewall-cmd --permanent --zone=public --add-port=9090/tcp
    - ### reload firewall
            firewall-cmd --reload
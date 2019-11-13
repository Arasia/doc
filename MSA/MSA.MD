# MSA

## 목차

- [MSA 소개](#MSA-소개)
    - [MSA 등장 배경](#MSA-등장-배경)
    - [Gartner가 정의한 MSA](#Gartner가-정의한-MSA)
- [참고자료](#참고자료)

# MSA 소개

## MSA 등장 배경
### Monolith Architecture
    모든 소프트웨어의 구성요소가 하나의 프로젝트에 통합되어 있는 형태
![monolithic_vs_microservices](Image/monolithic&#32;vs&#32;microservices.jpg "monolithic vs microservices.jpg")
- 서비스/프로젝트가 커질수록, 영향도 파악 및 시스템 구조 파악에 어려움이 있음
- 빌드, 테스트, 배포 시간이 기하급수적으로 늘어남
- 서비스를 부분적으로 scale-out하기 힘듦
- 부분의 장애가 전체의 서비스 장애로 이어지는 경우가 발생

## Gartner가 정의한 MSA
![MSA_Components](Image/MSA_Components.png "MSA Components.png")

### Outer architecture
1. [External Gateway](#External-Gateway)
1. [Service Mesh](#Service-Mesh)
1. [Container Management](#Container-Management)
1. [Backing Services](#Backing-Services)
1. [Telemetry](#Telemetry)
1. [CI/CD Automation](#CI/CD-Automation)

#### External GateWay
#### Service Mesh
#### Container Management
#### Telemetry
#### CI/CD Authmation



# 참고자료
- [조대협 - 대용량 웹 서비스를 위한 마이크로 서비스 아키텍쳐의 이해](https://bcho.tistory.com/948)
- [GodNR - MSA 개념 정립하기](https://waspro.tistory.com/432)
- [tedigom - MSA 제대로 이해하기1](https://velog.io/@tedigom/MSA-%EC%A0%9C%EB%8C%80%EB%A1%9C-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-1-MSA%EC%9D%98-%EA%B8%B0%EB%B3%B8-%EA%B0%9C%EB%85%90-3sk28yrv0e)
- [tedigom - MSA 제대로 이해하기2](https://velog.io/@tedigom/MSA-%EC%A0%9C%EB%8C%80%EB%A1%9C-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-2-MSA-Outer-Architecure)
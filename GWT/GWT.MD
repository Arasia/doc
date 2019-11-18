# GWT <!-- omit in toc -->

# 목차 <!-- omit in toc -->

- [Start Gwt](#start-gwt)
    - [Entry Point](#entry-point)
    - [UiBinder](#uibinder)
    - [ClientBundle](#clientbundle)
        - [ImageResource](#imageresource)

# Start Gwt

## Entry Point
> EntryPoint를 implements 한 class가 시작 점이 된다. 


```java
package com.google.gwt.core.client.EntryPoint   
public interface EntryPoint {
	/**
    * The entry point method, called automatically by loading a module that
    * declares an implementing class as an entry point.
    */
    void onModuleLoad();
}
```

- onModuleLoad()를 통하여 페이지 로드를 시작한다.

## UiBinder

## ClientBundle
> 리소스 번들같은 역할 

- @Soruce  

    > 가져올 파일의 이름을 지정

### ImageResource
> 이미지를 가져옴

- 사용 가능 확장자
    - png
    - jpg
    - gif
    - bmp


```java
@Source("logo_i.png")
ImageResource logo();
```
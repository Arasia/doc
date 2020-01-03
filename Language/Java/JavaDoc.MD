# JavaDoc 작성법

## JavaDoc

    Java 소스에 문서화를 하는 방법으로 클래스나 메소드에 주석으로 기술한 내용을 javadoc 명령어나 또는 이를 이용한 빌드 툴(maven 의 site phrase등)을 사용하여 문서화할 수 있다. 

    문서화할 주석을 달 경우 /** 두 개로 시작하고 */ 로 끝나야 한다.

    특별한 키워드는 @keyword 형식으로 작성한다.

    html에 기반을 두고 있다.

## 작성법

    method 상단에 /** .. */ 주석을 추가하면, Javadoc의 대상이 된다.

    comment 는 반드시 /** 으로 시작해야 한다. /* 은 Javadoc의 대상이 아니다.

    method 설명은 html 형식으로 출력된다. 즉, 줄 바꿈을 하려면 <br/> 태그를 사용해야 한다.

    @param, @return, @throws 는 method 에서 필수속성이다.

    @return 에서 반환타입에 대해서 기술할 필요가 없다.

    interface가 존재한다면, 구현체에서는 주석을 생성할 필요가 없다.
    interface에서 정의된 method의 의도대로 구현을 한 것이므로, interface에서의 주석만으로 충분하다.
    단, interface 에 정의되어 있지 않은 구현체의 method 는 주석을 필요로 한다.

    주석 작성시, 다른 클래스를 참조할 경우에는 {@link } 를 사용한다. 
    이 것은 Javadoc에서 하이퍼링크를 생성한다.

    주석 작성시, code를 기술할 경우엔, {@code } 와 <pre> 태그를 사용한다.

---

## 키워드

## @author

-  코드 작성자를 설명한다.

        사용법 : @author name
        ex : @author 개발자

## @param
- 메소드의 매개 변수를 설명하기 위해 사용한다.

        사용법 : @param parameter-name description
        ex : @param name 이름

## @return
- 메소드로부터 반환되는 값을 설명하기 위해서 사용한다.

        사용법 : @return description
        ex : @return 이름과 주민번호가 연결된 문자열

## @exception

- 코드가 발생할 수 잇는 예외를 설명하기 위해서 사용한다.

        사용법 : @exception class-name description
        ex : @exception IOExcepton 입출력 시 예외가 발생하면

## @throws
- 사용자가 처리 해야 할 예외이다. 
- 이 예외가 언제 발생하는지에 대해 반드시 설명이 필요하다.

        사용법 : @throws class-name description
        ex : @throws IOExcepton 입출력 시 예외가 발생하면 발생

## @deprecated

- 클래스, 메소드, 변수 등 더 이상 사용을 권장하지 않는 것을 알리기 위해서 사용한다.
- @Deprecated 애노테이션과 같이 사용하면 더욱 유용하다.

        사용법 : @deprecated deprecated-text
        ex : @deprecated 이 메소드는 더 이상 사용되지 않습니다.

## {@code}

- 설명에 예제코드를 첨부할 경우 사용한다.
- {@code} 만으로는 개행이 되지 않으므로 pre 태그와 함께 사용한다.

        사용법 : <pre> {@code ex} <pre/>
        ex :    <pre> 
                    {@code 
                        Test test = new Test();
                    } 
                <pre/>

## {@link}

- 특정 패키지의 문서로 링크를 걸기 위해 사용한다.

        사용법 : {@link package.class#member label}
        ex : {@link #getStr(int, int) getStr}

## @see
- 다른 클래스, 메소드, 변수를 참고할 경우 관련된 정보를 알리기 위해 사용한다.

        사용법 : @see package.class#member label
        ex : @see String#equals(Object) equals

## @version
- 코드의 버전을 알리기 위해서 사용한다.

        사용법 : @version version-text
        ex : @version 1.0

## @since
- 클래스나 메소드가 언제부터 있었는지 표시를 위해 사용된다.

        사용법 : @since version-text
        ex : @since 1.0
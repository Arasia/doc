MarkDown 문법
===

목차
---

- [1. 헤더](#1.-헤더)  
    * [1.1. 글머리](#1.1.-글-머리)
    * [1.2. 큰 제목](#1.2.-큰-제목)
    * [1.3. 작은 제목](#1.3.-작은-제목)
- [2. 단락/줄 나누기](#2.-단락/줄-나누기)
    * [2.1. 단락 나누기](#2.1.-단락-나누기)
    * [2.2. 줄 나누기](#2.2.-줄-나누기)
- [3. 강조](#3.-강조)  
    * [3.1. Bold](#3.1.-Bold)
    * [3.2. Italic](#3.2.-Italic)
    * [3.3. Bold & Italic](#3.3.-Bold-&-Italic)
- [4. 인용문구](#.4.-인용문구)
- [5. List](#5.-List)
    * [5.1. Ordered Lists](#5.1.-Ordered-Lists)
    * [5.2. Unordered Lists](#5.2.-Unordered-Lists)
- [6. Code Block](#6.-Code-Block)  
    * [6.1. Normal Code Block](#6.1.-Normal-Code-Block)
    * [6.2. Fanced Code Block](#6.2.-Fanced-Code-Block)
    * [6.3 Syntax Highlighting](#6.3-Syntax-Highlighting)
- [7. Images](#7.-Images)  
- [8. Code](#8.-Code)  
- [9. 가로줄](#9.-가로줄)  
- [10. 링크](#10.-링크)  
- [11. Escape Characters](#11.-Escape-Characters)  
- [12. Table](#12.-Table)  
- [참조링크](#참조-링크)

---

# 1. 헤더
> 제목과 글머리 레벨을 나눈다

## 1.1. 글 머리
- Heading level 1 ~ 6
```
# Heading level 1
## Heading level 2
### Heading level 3
#### Heading level 4
##### Heading level 5
###### Heading level 6
```
# Heading level 1
## Heading level 2
### Heading level 3
#### Heading level 4
##### Heading level 5
###### Heading level 6

## 1.2. 큰 제목
> Heading level 1과 같다
```
Heading level 1
===
# Heading level 1
```
Heading level 1
===
# Heading level 1

## 1.3. 작은 제목
> Heading level 2과 같다
```
Heading level 2
---
## Heading level 2
```
Heading level 2
---
## Heading level 2

---

# 2. 단락/줄 나누기
> 단락 또는 줄을 나누는 방법

### 2.1. 단락 나누기
> 단락의 끝에 개행 문자(Enter)를 2개 이상 넣는다.
```
단락 1
단락 2

단락 3
```
단락 1
단락 2

단락 3

### 2.2. 줄 나누기
> 줄의 끝에 공백(Space)을 2개 이상 넣는다.
```
줄1
줄2  
줄3
```
줄1
줄2  
줄3

---

# 3. 강조

## 3.1. Bold
```
Test **text**  
__Test__ text
```
Test **text**  
__Test__ text

## 3.2. Italic
```
Test *text*  
_Test_ text
```
Test *text*  
_Test_ text

## 3.3. Bold & Italic
```
Test ***text***  
___Test___ text
```
Test ***text***  
___Test___ text

## 3.4. Strikethrough
```
~~Test text~~  
~~**Test** _text_~~  
~~***Test Text***~~  
***~~Test text~~***  
```
~~Test text~~  
~~**Test** _text_~~  
~~***Test text***~~  
***~~Test text~~***  

---

# 4. 인용문구
- ```>``` 블럭인용문자를 이용한다
- 레벨 제한이 없다
```
> level 1 인용문구   
>   > level 2 인용문구
>   >   > level 3 인용문구
>   >   >   > level 4 인용문구
```
> level 1 인용문구   
>   > level 2 인용문구
>   >   > level 3 인용문구
>   >   >   > level 4 인용문구

---

# 5. List

## 5.1. Ordered Lists
- 시작 숫자에 맞춰 숫자에 상관없이 자동 적용 된다.
- 들여쓴 단락부턴 시작숫자가 1일때 적용된다.
```
4. level 1  
3. level 1  
    1. level 2  
    5. level 2  
    3. level 2  
2. level 1  
    3. level 2  
    2. level 2  
```
4. level 1  
3. level 1  
    1. level 2  
    5. level 2  
    3. level 2  
2. level 1  
    3. level 2  
    2. level 2  

## 5.2. Unordered Lists
- \-, \*, \+ 세가지 기호로 사용 가능하다.
- 들여쓰기(탭)에 따라 level이 적용된다.
- 순서와 기호에 영향없이 일괄 적용된다.
- level 1~3의 모양은 다르나 level 4 이상은 level 3과 동일하다.
```
- level 1  
    * level 2  
        + level 3  
            - level 4  
    + level 2  
        - level 3  
* level 1  
+ level 1  
```
- level 1  
    * level 2  
        + level 3  
            - level 4  
    + level 2  
        - level 3  
* level 1  
+ level 1  

---

# 6. Code Block
> \<pre>\<code>code\</code>\</pre>와 같다

## 6.1. Normal Code Block
- 들여쓰기를 통한 Code Block
- 기본 위치 Code Block : Tap(= 4 Spaces)
- List 내부 Code Block : 한줄 띄운 후 2 Taps(= 8 Spaces)
<pre><code>    
    Code Block
    
- level 1

        Code Block
</code></pre>
    
    Code Block
    
- level 1

        Code Block

## 6.2. Fanced Code Block
- \`\`\` 또는 ~~~을 사용한 Code Block
- 혼용 불가
<pre><code>``` 
Code Block
```
</code></pre>
```
Code Block
```

## 6.3 Syntax Highlighting
> Language에 맞춰 코드를 강조할 수 있다.
<pre><code>```json
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```
</code></pre>
```json
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

---

# 7. Images
```
![Test Image](Test.png)
![Test Image Comment](Test.png "Comment")
```
![Test Image](Test.png)  
![Test Image Comment](Test.png "Comment")

---

# 8. Code
- \`를 통해 Code를 표시할 수 있다.
```
Test `Code`
```
Test `Code`

- \`\`을 통하여 Code내에 \`를 표시할 수 있다.
```
``Test `Code` ``
```
``Test `Code` ``

---

# 9. 가로줄
- \-, \*, \_를 3개 이상 사용하여 가로줄을 표시할 수 있다.
```
---
Test
```
---
Test

---

# 10. 링크
- URL을 통해 링크를 걸수도 있고 파일이나 글머리를 링크할수도 있다
```
[Naver](https://www.naver.com)  
[Google](https://www.google.com "google link")  
[10. 링크](#10.-링크)
```
[Naver](https://www.naver.com)  
[Google](https://www.google.com "google link")  
[10. 링크](#10.-링크)
---

- 빠른링크
```
<https://www.naver.com>
```
<https://www.naver.com>

---

# 11. Escape Characters
- \\뒤에 문자를 붙임으로써 Escape 문자 표시 가능  

|   Character   |   Name    
|   :---:       |   :---:   
|   \	        |   backslash
|   `	        |   tick mark
|   *	        |   asterisk
|   _	        |   underscore
|   {}	        |   curly braces
|   []	        |   brackets
|   ()	        |   parentheses
|   #	        |   pound sign
|   +	        |   plus sign
|   -	        |   minus sign (hyphen)
|   .	        |   dot
|   !	        |   exclamation mark

---

# 12. Table
```
|   Normal  |   Left    |   Middle  |   Right   
|    ---    |   :---    |   :----:  |   ---:    
|     1     |   Test 1  |   Text 1  | Comment 1 
|     2     |   Test 2  |   Text 2  | Comment 2 
```
|   Normal  |   Left    |   Middle  |   Right   
|    ---    |   :---    |   :----:  |   ---:    
|     1     |   Test 1  |   Text 1  | Comment 1 
|     2     |   Test 2  |   Text 2  | Comment 2 
---

# 참조 링크
<https://www.markdownguide.org/basic-syntax>  
<https://www.markdownguide.org/extended-syntax>
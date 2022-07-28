# 오늘 배운 내용 작성
## 크롤링

1. 정적 크롤링
   - 웹에 있는 정적 데이터 수집할 때 사용
     - 정적인 데이터는 로그인과 같은 사전작업 없이 바로 볼 수 있는 데이터
     - 새로고침하지 않는 이상 바뀌지 않는 데이터
     - 주소를 통해 요청받고 결과를 전달해 주고 종료
   - 연속적인 작업은 수행 불가, 주로 한 페이지 안에 원하는 정보가 모두 있는 경우 사용
   - 한 페이지 안에 모든 작업이 이루어지기 때문에 속도가 매우 빠름
   - 수집 대상의 한계 존재
2. 동적 크롤링
   - 웹에 있는 동적인 데이터를 수집할 때 사용
     - 동적인 데이터는 입력, 클릭, 로그인과 같은 페이지 이동시 얻을 수 있는 데이터
     - 단계적 접근이 필요하기 때문에 수집 속도가 느려지지만 수집 대상에 한계가 거의 없는 큰 장점
     - 연속적 접근 가능, 페이지 이동이 필수적이거나 페이지 안에 정보 은닉된 경우 사용
  
|   |정적 크롤링| 동적 크롤링 |
|:-----------:|:--------------:|:--------------------:|
|연속성|주소를 통한 단발적 접근|브라우저를 사용한 연속적 접근|
|속도|빠름|느림|
|수집 성능|수집 대상에 한계있음|수집 대상에 한계 거의 없음|


## 라이브러리
- 크롤링시 자주 사용 되는 라이브러리는 다음과 같다.

1. time 라이브러리

- time.time() : time.time()은 UTC를 사용해 현재 시간을 실수 형태로 돌려주는 함수이다.
    - 1970년 1월 1일 0시 0분 0초 기준으로 지난 시간을 초 단위로 돌려준다. 
    
    ```python
    import time
    print(time.time())
    ```
 
- time.localtime() : 현재 시간을 년, 월, 일, 시, 분, 초..의 형태로 출력해준다.
 
    ```python
    import time
    print(time.localtime())
    ```



2. 정적 클로링 도구
- requests : 간편한 HTTP 요청 처리를 위해 사용하는 라이브러리, 웹과 연결을 위해 사용된다.
- beautifulsoup : html 태그를 다룰 수 있는 라이브러리, 웹에 있는 데이터 중 필요한 데이터만 뽑아내기 위해 사용
- pd.read_html : html 내의 table만 추출할수 있는 도구


3. 동적 크롤링 도구
- selenium : 웹 드라이버를 사용해 자동화 기능을 실현하는 라이브러리이다.
    - 웹에 접속해 클릭, 이동과 같응 action을 제어할 수 잇다
    - chromedriver.exe를 설치하고 이를통해 제어 가능
    
4. multiprocessing 모듈
- multiprocessing : 여러개의 코어를 활용할 수 있는 multiprocessing 모듈을 사용하면 크롤링 속도를 개선할수 있다.
    - process fork 문제로 인해 windows 에서는 사용불가, colab에서 사용가능


## 웹 문서 전체 가져오기
- urllib.request 패키지
```python
from urllib.request import urlopen
import requests
from bs4 import BeautifulSoup as bs
```
  - 네이버로 예를 들어보면
```python
html = urlopen("https://www.naver.com/")
soup = bs(html, "html.parser")
print(soup)
```
```python
soup = bs(html, "html.parser")
print(soup)
```

## 웹페이지와 HTML
- 웹페이지는 HTML(HyperText Markup Language)을 기반으로 만든다.
- F12를 누르면 뜨는 코드들이 HTML이다.
- Ctrl + shift + c

HTML 문서를 통해 웹페이지가 어떻게 구성되어 있는지 알 수 있으며, 이를 통해 원하는 데이터가 웹 페이지의 어디에 위치하는지 파악해 수집하는 것이 가능하다.

1. HTML 태그

- HTML은 마크로 둘러싸인 언어라는 뜻으로 구조에 대한 정보를 기반으로 작성된 언어
- 각각의 구성 요소는 마크 역할을 하는 태그로 감싸져 있다.
    - 웹페이지의 시작과 끝을 의미하는 <html></html>
    - 문서의 제목을 의미하는 <title></title>
    - 웹에 실제로 표시되는 내용을 의미하는 <body></body>

```html
<태그>내용</태그>
```


2. HTML 태그의 종류
- ul : unordered list. 순
- li : list item. 목록의 내용이 되는 실질적 태그
    - [참고](https://www.w3schools.com/html/html_lists.asp)
- a : 하이퍼링크를 나타내는 태그
  - <a href="https://www.google.com">google</a>
- p : paragraph(단락)의 약자, 긴 글 뭉텅이.
- table : 표를 나타내는 태그
    - [참고](https://www.w3schools.com/html/tryit.asp?filename=tryhtml_table3)
- img 태그
  - 이미지를 표시하는 태그

- find html 태그
    - find("태그") - 첫번째 태그만 검색
    - find_all("태그") - 전체 태그 검색후 list로 반환



## 4. 선택자
### 선택자
- 태그 중에는 동일한 태그가 존재할 수있다. 
- 선택자(Selector)는 동일한 태그 여러 개 중에서도 각 태그를 구별할 수 있는 일종의 주소이다.

### 선택자의 필요성

```html
<div>	
	<div>
		<span> Python </span>
		<span> Hello world </span>
	</div>
	
	<div>
		<span> Java </span>
		<span> Coffee </span>
	</div>
<div>
```

- <span> 태그는 다양한 내용을 담을 수 있다.
- <span> 태그가 4개나 있어서 컴퓨터가 구분하기 어렵다. 이러한 문제를 해결하기 위해 선택자를 사용함.

```html
<div id = "contents">	
	<div class = "metadata1">
		<span class = "language"> Python </span>
		<span class = "project" > Hello world </span>
	</div>
	
	<div class = "metadata2">
		<span class = "language"> Java </span>
		<span class = "project"> Coffee </span>
	</div>
<div>
```

언어(language)와 관련된 데이터만 필요한경우
	- 태그로만 해당 데이터를 선택하면, <span>을 사용
	- 하지만 <span>에 언어 정보 뿐만 아니라 프로젝트 정보(Hello world, Coffee)도 포함됩니다.
	- "class = 'language'"라는 선택자를 통해 우리는 두 개의 언어 관련 데이터(python, java)를 찾을 수 있다.


### id와 class
- 태그의 선택자는 주로 id와 class를 사용한다.
- id는 어떤 요소의 고유한 값.
    - [참고](https://www.w3schools.com/html/html_id.asp)
    - html에서도 id는 하나의 고유한 선택자로, __중복__ 되지 않고 하나만 존재한다.
- class 태그는 같은 속성을 지닌 데이터를 묶어주는 값이다.
    - 한 태그가 __여러 개__ 의 class를 가질 수 있다.
    - [참고](https://www.w3schools.com/html/html_classes.asp)

비슷한 속성끼리 묶어줄 때 class 태그를 사용한다.



### 선택자 사용법
```html
<div id='123' class='456'>
```
- 선택자에 따라 데이터를 찾는 코드에 차이가 있다.
- id는 '#'를 붙이고, class는 '.'을 붙여준다.

- 태그만 사용해 데이터를 찾을 경우 -> 태그
  - div
- 태그와 id를 사용해 데이터를 찾을 경우 -> 태그#id
  - div#123
- 태그와 class를 사용해 데이터를 찾을 경우 -> 태그.class
  - div.456
- 태그, id, class 모두 사용해 데이터를 찾을 경우 -> 태그#id.class
  - div#123.456

- 참고 : class 이름에 공백이 포함될 경우가 종종 있는데, 이럴 경우 공백을 .으로 대체해서 작성하면 된다.
    - ex)

    ```html
    <div class='hello python'>
    ```

    -> div.hello.python



# 라이브러리 BeautifulSoup
- BeautifulSoup 라이브러리는 HTML 문서를 탐색해서 원하는 부분만 쉽게 뽑아낼 수 있게 해주는 라이브러리이다.

## BeutifulSoup의 필요성

### BeautifulSoup
- 함수 BeautifulSoup()
    - 문자열 HTML 코드를 실제 HTML 코드로 변환해주는 함수 BeautifulSoup

```python
BeautifulSoup(문자열, 'html.parser')
```
- 함수 find_all()
    - find_all() 함수는 HTML 코드에서 우리가 원하는 부분을 모두 가져오는 함수
    - 원하는 부분을 지정할 때 사용하는 것은 태그와 선택자
    - find_all()은 해당 태그의 모든 HTML 코드를 리스트 형태로 반환

```python
# <div id="example1">
실제HTML코드.find_all("div") #tag name
실제HTML코드.find_all(id="example1") #selector

# <div id="example1">, <span class="example2">
실제HTML코드.find_all(["div", "span"]) # 2개의 tag
실제HTML코드.find_all(attrs = {"id":"example1", "class":"example2"}) - 얘를 잘쓰는듯
```

- 함수 find()
    - find() 함수는 딱 하나만 가져온다.

```python
# <div id="example1">
실제HTML코드.find("div")#tag 만
실제HTML코드.find(id="example1") # selector 만
실제HTML코드.find(attrs = {"id":"example1"}) # selector
실제HTML코드.find("div", {"id":"example1"}) # tag + selector
```


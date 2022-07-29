# 오늘 배운 내용 작성
## 동적크롤링

### 셀레니움(Selenium)
- Selenium은 주로 웹앱을 테스트하는데 사용하는 프레임워크
- webdriver라는 API를 통해 운영체제에 설치된 크롬 등의 브라우저를 제어
- Selenium 모듈 설치 후 사용
- 사용자 브라우저(Chrome, Edge, ..)에 맞는 webdriver를 다운로드 후 사용 가능
- 다운로드 사이트에서 본인이 사용하는 브라우저의 버전등을 확인 후 다운로드
- 크롬: https://chromedriver.chromium.org/downloads
- Edge: https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/
- 파이어폭스:https://github.com/mozilla/geckodriver/releases

__주의__
최근 없데이트되면서 문법 변경됨

### webdriver
- selenium의 webdriver는 웹 응용 프로그램들의 테스트를 단순화 및 가속화해주는 툴

#### 크롬 드라이브 다운
1. 크롬 브라우저 버전을 확인한다.(크롬브라우저 점3개 클릭-도움말-정보)
2. 동일버전의 webdriver을 다운로드 [driver](https://chromedriver.chromium.org/downloads)
3. ./tools/chromedirver.exe

### selenium 내장함수

#### 1. get()
- get() 함수는 입력한 url 주소로 접속하는 함수

```python
driver.get("url 주소")
```

#### 2. find_element(By.<location>, "")
- 정적크롤링의 find과 같은 역할로, 크롤링을 위해 HTML 요소를 찾는 함수
```pythopn
from selenium.webdriver.common.by import By

find_element(By.ID, "id")
find_element(By.NAME, "name")
find_element(By.XPATH, "xpath")
find_element(By.LINK_TEXT, "link text")
find_element(By.PARTIAL_LINK_TEXT, "partial link text")
find_element(By.TAG_NAME, "tag name")
find_element(By.CLASS_NAME, "class name")
find_element(By.CSS_SELECTOR, "css selector")
```

__참고__ :  구버전의 find_element_by_ ?? 에서 변경되었다. 

예) find_element(By.CSS_SELECTOR, "css selector") 
- copy 목록의 copy selector를 통해 속성을 찾을 수 있다.
```python
driver.find_element(By.CSS_SELECTOR, "a#writeFormBtn")
```

    
예) find_element(By.ID, "id") & find_element(By.CLASS_NAME, "class name")
- id 속성 혹은 class 속성을 가지고 있는 경우 사용한다.

```python    
'글쓰기' 버튼 - <a href="#" id="writeFormBtn" class="btn_type1 post_write _rosRestrict" onclick="clickcr(this,'abt.wrtlist', '', '', event);">

driver.find_element(By.ID, "writeFormBtn")
driver.find_element(By.CLASS_NAME, "btn_type1.post_write._rosRestrict")
```

예) find_element(By.XPATH, "xpath")
- 적당한 id, class 속성이 없을 경우 xpath를 사용가능 
- XPATH란 xml 문서의 특정 부분의 위치를 의미한다.
- html 요소를 우클릭하고 copy 목록의 copy xpath를 클릭해 사용가능

```python
driver.find_element(By.XPATH, 'XPath 선택자')

# ex) '글쓰기' 버튼의 'Copy XPath'결과 - //*[@id="writeFormBtn"]
driver.find_element_by_xpath('//*[@id="writeFormBtn"]')
```

#### 3. find_elements_by_?? ()
- 정적 크롤링의 find_all과 같은 역할로, 입력한 태그 및 선택자에 해당하는 모든 html 요소를 찾는 함수이다. 
- element 뒤에 s가 붙는다. 



#### 4. click()
- html 요소를 클릭하는 함수이다.

```python
driver.find_element(By.???, "????").click()

ex) 글쓰기 버튼 클릭
driver.find_element(By.CSS_SELECTOR,"a#writeFormBtn").click()
```

#### 5. send_keys()
- html 요소에 직접 텍스트를 입력하는 함수이다.

```python
driver.find_element_by_??().send_keys("텍스트")

ex) 검색 칸에 파이썬 입력
driver.find_element_by_css_selector("input#query").send_keys("파이썬")
```

- 네이버 로그인 할 때는 아래와같이 임포트해주면 된다.
```python
from selenium.webdriver import Chrome
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.common.action_chains import ActionChains
import pyperclip
import time
```
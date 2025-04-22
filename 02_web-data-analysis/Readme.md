이 프로젝트는 Python을 이용해 웹 페이지에서 데이터를 수집(크롤링)하고,  
원하는 정보를 추출(파싱)한 뒤, 간단한 데이터 시각화를 통해 내용을 정리하는 실습입니다.

## 사용 모듈

- BeautifulSoup4
- urllib.request (HTML 저장시 사용 가능)

## 웹 크롤링

웹브라우저에서 https://wikidocs.net Url을 입력하면, wikidocs 웹 서버는 html 파일을 웹브라우저에 리턴한다.
웹브라우저가 wikidocs에 요청하는 것과 동일한 원리로 python 프로그램에서 wikidocs 웹 서버로 요청한다.
단, 웹브라우저는 받은 파일을 화면으로 예쁘게 보여주는 기능을 갖고 있지만 지금 개발하려는 python은 그 기능이 없기 때문에 html 파일 그대로를 가져오게 될 것이다.

### 1. [`urllib`](ex01_urllib(웹데이터수집).ipynb)

**`urllib.request`**
- 정적 HTML 문서를 요청할 때 사용
- 웹서버로부터 응답을 받아 HTML 전체를 가져옴

```python
import urllib.request

res = urllib.request.urlopen("https://wikidocs.net")
if res.status == 200:
    html = res.read().decode("utf-8")
    print(html)
```

> ⚠️ 참고: 웹툰 목록이나 댓글 등은 HTML 안에 보이지 않을 수 있음  
> 이는 `JavaScript`에 의해 동적으로 렌더링되기 때문이며, 이럴 땐 `Selenium`을 사용해야 합니다.

**ùrllib.parser`**
- URL에 포함된 문자열(예: 한글)을 인코딩하거나 디코딩할 때 사용

**주요 메서드**

| 메서드 / 속성            | 설명 |
|---------------------------|------|
|urllib.request.urlopen(url)|지정한 URL의 응답 객체를 반환|
|res.read()|응답 본문을 byte 형태로 반환|
|res.read().decode("utf-8")|byte 데이터를 문자열로 변환|
| urllib.parse.quote("문자열")              | 한글, 특수문자 등을 URL-safe 문자열로 인코딩   |
| urllib.parse.unquote("%ED%95%9C%EA%B8%80") | 인코딩된 URL 문자열을 다시 한글로 디코딩       |

### 2. [`BeautifulSoup`](ex02_beatifulsoup.ipynb)

- HTML 문서에서 원하는 부분만 **선택적으로 추출**할 수 있는 파싱 기능
- HTML 태그/속성을 기준으로 크롤링 대상 정밀 지정 가능

**주요 메서드**

| 메서드 / 속성                              | 설명                                           |
|--------------------------------------------|------------------------------------------------|
| `BeautifulSoup(html, "html.parser")`       | HTML 파서 초기화                               |
| `.find(tag, attrs={})`                     | 특정 태그 하나 찾기 (조건 가능)                |
| `.find_all(tag, attrs={})`                 | 특정 태그 여러 개 찾기                         |
| `.select(css_selector)`                    | CSS 선택자로 요소 찾기                         |
| `.get_text(strip=True)`                    | 태그 내부 텍스트만 추출                        |
| `['속성명']`                                | 태그의 특정 속성 값 추출 (`['href']`, `['title']` 등) |

## 데이터 시각화

웹에서 수집한 텍스트 데이터를 **자연어 처리 전에 시각적으로 확인**하는 단계입니다.

### 3. [`wordcloud` 모듈](ex03_wordcloud(텍스트데이터시각화).ipynb)

- 텍스트 데이터를 시각적으로 표현
- 단어 빈도수를 기반으로 워드 클라우드 이미지 생성

```python
from wordcloud import WordCloud
import matplotlib.pyplot as plt

text = "단어 단어 파이썬 크롤링 웹 웹 데이터"
wc = WordCloud(font_path='NanumGothic.ttf', background_color='white').generate(text)

plt.imshow(wc, interpolation='bilinear')
plt.axis('off')
plt.show()
```

> ⚠️ 한글 깨짐 방지를 위해 `font_path`에 한글 폰트(.ttf) 파일 지정 필요

**편집기능**
- font_path : 한글 폰트 경로 지정 (한글 깨짐 방지)
- width, height : 워드클라우드 이미지 크기 조절
- max_words : 최대 단어 개수 지정
- mask : 마스킹 이미지 사용 (예: 하트 모양, 원형 등)
- colormap : 색상 테마 지정 (예: 'Blues', 'viridis')
- stopwords : 제외할 단어 집합 지정
- contour_color, contour_width : 외곽선 색상 및 두께 설정

**주요 메서드**

| 메서드                                                  | 설명                                         |
|----------------------------------------------------------|----------------------------------------------|
| `WordCloud(font_path=..., background_color=...)`         | 워드클라우드 생성기 초기화                    |
| `.generate(text)`                                       | 문자열 기반 워드클라우드 생성                 |
| `plt.imshow(wc)`                                        | 워드클라우드 이미지 시각화                    |
| `plt.axis('off')`                                       | 축 제거                                       |
| `plt.show()`                                            | 이미지 표시                                   |



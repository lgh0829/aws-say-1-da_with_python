언어 구성요소 (간단하게)
- 키워드
- 연산자
- 변수
  키워드를 변수명으로 사용할 수 없음
- 함수

## 데이터구조

**데이터 타입**
- 데이터 처리할 때 저장포멧, 할당 바이트에 따라 성능이 달라지기 때문에 적절하게 사용하는 것이 중요함
- (현실 데이터 타입) 숫자, 문자, binary -> (PC 기준) 숫자 - 정수, 실수 / 문자, binary, boolean(참/거짓 구분 목적)

**데이터 구조**
데이터 저장 방식에 따라 프로그램의 데이터처리 성능(검색, 저장 등)이 달라짐
python 기본 데이터구조
- 리스트
  - 대괄호 [ ]
  - 데이터 추가, 삭제 가능
- 튜플
  - 소괄호 ( )
  - 이미 저장한 데이터를 변경할 수 없음
- 딕셔너리
  - 중괄호 { key: value }
  - 저장된 데이터를 조회할 때 주소 대신 key 사용
  - key는 중복을 허용하지 않음
  - value 추가/갱신 문법이 동일함: 동일한 key가 없을 때 추가, 동일한 key가 있을 때 갱신
- Set
  - 중괄호 { }
  - 집합 개념, 중복을 허용하지 않음

**출력방식**
```python
# 방법1
for i in range(2,10):
    print("[%d 단]" %i)
    for j in range(2,10):
        print("%d * %d = %d" %(i, j, i*j))
    print("==========")
```
```python
# 방법2
for i in range(2,10):
    print(f"[{i}단]")
    for j in range(2,10):
        print(f"{i} * {j} = {i*j}")
    print("==========")
```

**목차**
- [](/ex01_데이터타입.ipynb)
- [](/ex02_데이터구조_리스트.ipynb)
- [](/ex03_데이터구조_투플.ipynb)
- [](/ex04_데이터구조_딕셔너리.ipynb)


## 제어문
문장 흐름을 바꿀 수 있음

**조건문**
if

**반복문**
for
while

**목차**
-[](/ex06_제어문.ipynb)
-[](/ex06_제어문(조건문과 반복문)설명.pdf)

## 함수

**정의**
매개변수의 갯수 제한이 없는 함수의 정의 형식: `def sum( *a )`
매개변수에 디폴트 값이 있는 함수의 정의 형식: `def cal (num1, num2, method="sum") :  #디폴트 매개인자 값은 마지막에`

**호출**

## 클래스

**클래스 선언**
클래스: 객체를 생성할 수 있는 틀, 여러개의 기능과 변수를 가짐
- 구성
  - 속성 (옵션): 객체가 가지는 데이터
  - 메서드 (옵션): 객체가 할 수 있는 행동/기능
  - 생성자 (옵션): `__init__()` 형태

> 데이터(속성)와 동작(메서드)을 묶을 수 있어서 어려 객체를 선언해도 객체 별 동작 명령 시 오류가 없음

**객체 생성**
객체: 클래스로부터 실체화 된 것
- 정의한 클래스에 대해 객체를 생성하면, 클래스에서 정의한 속성 만큼 메모리에 공간이 할당됨
- 연산을 처리할 때마다 두 개 이상의 변수를 항상 입력받아야 할 때 -> 변수를 묶어서 앞으로 입력받을 때 매번 변수를 정의할 필요 없이 두 개 이상의 변수를 저장할 수 있음
- 객체 생성 형태: `classname()`

**생성자 선언**
생성자: 클래스로부터 객체가 생성될 때 한 번만 실행되는 함수
- 객체가 생성될 때 메모리에 공간이 할당되면서 같이 동작이 실행됨
  - 생성자가 매개변수를 가지고 있다면, 객체 선언할 때 같이 입력해줘야 호출됨
- 함수명이 `__init__`으로 고정됨
- self: 자기자신(객체)를 가리킴. `self.parameter1` 형태로 사용
- 생성자 선언 형태: `def __init__ (self, parameter1, parameter2):`

**메서드**
메서드: 클래스에서 정의된 생성자가 아닌 함수
- 메서드의 매개변수에서 항상 self를 명시해줘야 함
- 메서드 선언 형태: `def methodname (self, parameter1, parameter2):`

**상속**
- 상위클래스의 속성, 메서드, 생성자를 하위클래스가 가질 수 있음
- 하위클래스의 객체가 생성되면, 하위클래스 뿐만 아니라 상위클래스에서 정의한 속성이 메모리에 공간 할당되며, 상위클래스의 메서드를 이용할 수 있음
- 상속 형태: class 하위클래스(상위클래스)
  `class lion( animal ) :  #상속 lion is a animal.   하위클래스 is a 상위클래스`

**객체 사용: 동적 바인딩**
실행 시간(runtime)에 호출할 메서드(함수)가 결정되는 것
- 코드를 작성할 때는 어떤 메서드가 실행될지 모름
- 프로그램이 실제로 실행될 때(런타임 시점) 객체의 메서드를 확인하고, 객체 타입에 맞는 메서드를 호출

예시)
```python
def drive(car): # 어떤 객체(클래스)의 메서드를 실행할 지 모름
    car.run()

class Sonata:
    def run(self):
        print("Sonata가 달립니다.")

class Genesis:
    def run(self):
        print("Genesis가 달립니다.")
        
c1 = Sonata()
c2 = Genesis()

drive(c1)  # 런타임 시점에 Sonata 객체의 run() 메서드 실행
drive(c2)  # 런타임 시점에 Genesis 객체의 run() 메서드 실행

```

**목차**
- [ex08 클래스설명자료](/ex08_class_클래스설명.pdf)
- [ex08 클래스 1](/ex08_클래스_1.ipynb)
- [ex08 클래스 2](/ex08_클래스_2.ipynb)
- [ex08 클래스 3](/ex08_클래스_3.ipynb)
- [ex09 클래스 상속](/ex09_클래스_상속.ipynb)
- [ex10 클래스 활용](/ex10_클래스_활용.ipynb)

## 모듈

**기본**
print 같이 선언하지 않고도 사용가능함
ex) print

**standard library**
설치하지 않아도 선언하고 사용가능함
ex) os, numpy

**external libaray**
설치 필요하고, 같은 폴더 내에 파일이 위치해야 함. 선언 후에 사용가능함
설치 관리자 pip로 설치 가능
> .ipynb 확장자는 external library로 사용할 수 없음. 그래서 external libary로 활용이 필요할 시 .py 확장자로 변환하는 작업 필요함

**명시적으로 선언**
형태: `from {파일 이름} import {파일 내 클래스, 함수 등}`
명시적으로 선언하면 


## 예외처리

**에러종류**
- syntax 에러: 실행 자체가 안됨
- 실행 에러: 실행 중에 에러가 발생됨
  - 사소한 실행 에러가 발생했을 때, 동작 멈춤 없이 처리할 수 있는 방법: 예외처리
  - 메모리 부족 같이 심각한 실행 에러는 동작 멈춤 발생함
- 논리 에러: 로직을 잘 못 작성했을 때
  - 테스트케이스, 테스트 자동화 도구롤 사용해서 에러를 해결함

**구문 키워드**
try, except, else, finally
```python
try : #예외 발생 가능 구문
    ...
except ValueError: # ValueError가 발생했을 때 실행하는 구문
    ...
except (ZeroDivisionError, TypeError):
    ...
else: #  예외가 발생되지 않고 정상 수행되었을 때만 실행
    ...
finally : # 예외 발생과 상관없이 항상 실행되는 구문
    ...
```
> 예외 처리에서 명시하지 않은 error type이 발생할 경우 동작 멈춤 발생함
> except 구문에 에러를 명시하 않으면, 모든 에러에 대해 범용적으 처리하지만 디버깅이 어렵기 때문에 권장하 않음

**상황에 따른 return 결과**
- try 안에 return 있음: finally는 반드시 실행됨, try의 반환값에 영향 없음
- finally 안에도 return 있음: 그 값이 최종 반환값이 됨

**에러 종류와 발생원인**
- ZeroDivisionError: 0으로 나눌 때
- ValueError: 잘못된 값이 들어올 때 (int("abc") 등)
- TypeError: 타입이 잘못되었을 때 (len(3) 등)
- IndexError: 리스트/튜플 인덱스 초과
- KeyError: 딕셔너리에 없는 키를 참조할 때
- AttributeError: 없는 속성/메서드를 호출할 때
- NameError: 정의되지 않은 변수 사용
- ImportError: 모듈 import 실패
- FileNotFoundError: 파일이 존재하지 않을 때
- PermissionError: 파일/디렉토리에 접근 권한이 없을 때
- IOError: 입출력 오류 (파일, 네트워크 등)
- StopIteration: 반복 가능한 객체에서 다음 값이 없을 때
- RuntimeError: 실행 중 오류 발생 (일반적인 런타임 오류)
- Exception: 모든 예외의 부모 클래스 (모든 에러를 잡고 싶을 때)


## 파일입출력

`import os` 필요

**텍스트파일 편집**

읽기
- 파일 여는 방법 1: `f = open("test.txt", "r" , encoding="utf-8") # 동작 이후 f.close()를 명시해 줘야 함`
- 파일 여는 방법 2: `with open("test.txt","r", encoding="utf-8")   as  f  :  # 자동 close 됩니다.`
- 메서드 예시
  - `read()`: 전체 내용을 하나의 문자열로 반환, 반환 타입 str
  - `readline()`: 전체 내용에서 한 줄을 문자열로 반환, 반환 타입 str
  - `readlines()`: 전체 내용을 한 줄씩 끊어서 리스트에 담아서 반환, 반환 타입 list (list 내에 데이터는 str 타입)

편집(또는 쓰기)
- write 모드로 파일 열기: 무조건 파일을 새로 생성함
    - 파일 여는 방법 1: `f = open("test.txt", "w" , encoding="utf-8") # 동작 이후 f.close()를 명시해 줘야 함`
    - 파일 여는 방법 2: `with open("test.txt","w", encoding="utf-8")   as  f  :  # 자동 close 됩니다.`
- append 모드로 파일 열기: 파일을 찾아서 업데이트하거나 파일이 없는 경우 새로 생성함
    - 파일 여는 방법 1: `f = open("test.txt", "w" , encoding="utf-8") # 동작 이후 f.close()를 명시해 줘야 함`
    - 파일 여는 방법 2: `with open("test.txt","w", encoding="utf-8")   as  f  :  # 자동 close 됩니다.`
- 메서드 예시
  - 파일에 데이터 입력: `f.write(" 코드를 추가 합니다.")`

**바이너리파일 편집**

바이너리파일 예시

| 확장자       | 예시 파일         | 설명                                         |
|--------------|------------------|----------------------------------------------|
| `.jpg`, `.png` | `image.jpg`       | 이미지 파일, 픽셀 정보와 메타데이터 포함         |
| `.mp3`, `.wav` | `music.mp3`       | 오디오 파일, 디지털 음파 저장                  |
| `.mp4`, `.avi` | `video.mp4`       | 비디오 파일, 영상+음성 압축 정보               |
| `.exe`         | `program.exe`     | 실행 파일, 운영체제가 실행하는 바이너리          |
| `.pdf`         | `document.pdf`    | 텍스트 + 이미지 등이 포함된 문서 포맷           |
| `.zip`         | `archive.zip`     | 여러 파일을 압축한 이진 포맷                   |
| `.bin`         | `firmware.bin`    | 펌웨어, 저장된 순수 이진 정보                  |
| `.pkl`, `.pt`  | `model.pkl`       | Python pickle 데이터, PyTorch 모델 등           |

python에서 바이너리파일 활용 예시
- 이미지 전처리 및 업로드
- 파일 전송, 저장, 복사
- 머신러닝 모델 저장/로딩 (.pkl, .pt)
- 네트워크 패킷 조작

읽기
- 파일 여는 방법 1: `img = open("googlelogo.png","rb") # 동작 이후 f.close()를 명시해 줘야 함`
- 파일 여는 방법 2: `with open("googlelogo.png","rb")   as  img  :  # 자동 close 됩니다.`

쓰기
- 파일 여는 방법 1: `img = open("googlelogo.png","wb") # 동작 이후 f.close()를 명시해 줘야 함`
- 파일 여는 방법 2: `with open("googlelogo.png","wb")   as  img  :  # 자동 close 됩니다.`









## Requirements
실행환경
- Anaconda
- Jupyter note
- Colab

라이브러리
- pandas
  - 주로 사용하는 데이터 구조: dataframe
- numpy
  - 주로 사용하는 데이터 구조: vector, matrix

파일 비번
- asd




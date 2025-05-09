## 탐색적 데이터 분석

### 분포탐색

**수치: 백분위수와 사분위수**

- 백분위수 : 데이터를 정렬한 후, 특정 퍼센트 지점의 수 `quantile()`함수 사용
  - 최소값 : 0% 지점의 수
  - 최대값 : 100% 지점의 수
  - 중앙값 : 50% 지점의 수
- 사분위수 : 백분위수 중 0%, 25%, 50%, 75%, 100% 지점의 수

**그래프: Boxplot**

전체 관측값 범위와 사분위수, 그리고 이상값까지 시각적으로 확인해볼 수 있는 그래프

![boxplot 예시](탐색적데이터분석__분포탐색/소스_TODO/boxplot.png)

구성
- 1사분위, 25% 백분위수
- 중앙값(2사분위수)
- 3사분위, 75% 백분위수
- 이상값을 제외한 최소값
- 이상값을 제외한 최대값
- 이상값, outlier

**그래프: histogram**

**연속형** 수치 데이터의 분포를 시각화 할 때 사용
> cf. 막대 그래프 : 이산형 수치 데이터나 범주형 데이터를 시각화할 때 사용

**기타**
- 도수분포표
- 막대그래프
- 파이그래프

### 상관관계분석

**산점도그래프(scatter plot)**
- 변수와 변수 간의 관계 시각화에 유용
- 종류
  - 양의 상관관계
  - 음의 상관관계
  - 변수 간 독립적
    cf. 독립적인 변수가 산점도에서 관계없이 나올 수 있지만, 그래프에서 관계없이 나온 그래프가 꼭 독립적이진 않음


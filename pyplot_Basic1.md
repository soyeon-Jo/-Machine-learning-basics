# MatPlotLib Pyplot Basic
MatPlotLib은  파이썬에서 매트랩과 유사한 그래프 표시를 가능케 하는 라이브러리다. 이 외에 객체지향 API를 제공하고 이를 사용하면 체계적이고 세밀한 시각화가 가능하다. 이 Tutorial에서는 Pyplot 위주로 설명한다.<br>
<br>
아래 내용은 주피터에서 그래프를 화면에 표시하거나, 한글을 사용하여 그래프를 그리거나, 그래프에 음수를 쓰는 경우를 대비해 항상 실행시키는 것이 좋다.


```python
#필요한 패키지를 import
import matplotlib.pyplot as plt

#matplotlib을 사용해 만든 graph를 화면에 표시하기 위함.
%matplotlib inline 

#한글을 사용할 때 깨지는 문제에 대한 해결
from matplotlib import font_manager, rc
font_name = font_manager.FontProperties(fname="c:/Windows/Fonts/malgun.ttf").get_name()
rc('font', family=font_name)

#그래프의 축 등에서 음수를 표시할 때 minus sign이 깨지는 것 해결
import matplotlib as mpl
mpl.rcParams['axes.unicode_minus'] = False
```

### 1. 1차원 리스트 그래프
- 1차원 리스트로 이루어진 변수의 값들을 연결해서 그래프를 그린다.
- x축은 리스트의 인덱스가 <u>자동</u>으로 할당된다.
- ylabel 혹은 xlabel로 y축이나 x축의 라벨을 지정할 수 있다.


```python
plt.plot([1,2,5,7,4])
plt.title('1차원 리스트 그래프')
plt.xlabel('자동으로 할당된 인덱스')
plt.ylabel('변수의 값')

plt.show()#그래프 출력하기
```


![png](output_3_0.png)


### 2. 2개의 변수를 좌표로 사용하는 2차원 그래프
- plt.plot의 매개변수로 길이가 같은 두 개의 리스트를 준다.
- 좌표값 외에 'ro', 'b-' 등을 사용하여 점의 모양을 지정할 수 있다.<br>
  
  ex)<br> **'r'**:붉은색, **'o'**: 동그라미,**'ro'**:붉은 동그라미<br>**'g'**:초록색,**'^'**:세모,**'g^'**:초록 세모 등등 <br>
 <br> 
- plt.axis로 축의 범위를 지정할 수 있다.


```python
plt.plot([1,3,7,10],[2,4,6,3],'ro')

plt.axis([-1,11,0,8]) #축의 범위 지정[xmin,xmax,ymin,ymax]

#별도로 지정 가능
#plt.xlim(-1,11)
#plt.ylim(0,8)

plt.show
```




    <function matplotlib.pyplot.show(*args, **kw)>




![png](output_5_1.png)


#### 여러 그래프를 하나의 그림판에 겹쳐서 그릴 수 있다.
y = f(x) 형태로 y값이 x의 함수로 정의된 것을 그래프로 시각화.


```python
import numpy as np
from math import log 

x = np.arange(0.1,3,0.1)

plt.plot(x,np.log(x),'r')
plt.plot(x,x*0,'b--')
plt.plot(x,np.exp(x),'g')

plt.legend(['log','0','exp'])
plt.show()
```


![png](output_7_0.png)


### 3. 막대 그래프(bar chart) 


```python
y = [5,3,7,10,22,3.5,9,1]

#x = ['a','b','c','d','e','f','g','h'] 
# 위는 아래와 같다
x = range(len(y))

plt.bar(x,y,width =0.8, color='green')
plt.show()

```


![png](output_9_0.png)


#### 수평 막대 그래프


```python
names = ['Amy','James','Bob','Joey']
heights = [110,170,200,158] 

plt.bar(names,heights)

plt.show()
```


![png](output_11_0.png)


각 막대는 원점에서부터 순서대로 그려진다. 
아래와 같이 names와 weights를 역순으로 바꿔서 그리면 위에서부터 그릴 수 있다.


```python
plt.barh(names[::-1], heights[::-1])
```




    <BarContainer object of 4 artists>




![png](output_13_1.png)


sorted를 이용하면 원하는 기준으로 정렬하여 그리는 것이 가능하다.


```python
sorted_w = sorted(zip(names,heights),key = lambda kv:kv[1])
n,h = zip(*sorted_w)

plt.barh(n,h,height = 0.8, color='yellow')
plt.show()
```


![png](output_15_0.png)


### 파이 차트(Pie Chart) 
- autopct: 파이의 값을 보여주기 위한 포맷팅, 소숫점이하 한 자리
- shadow: 그림자 여부
- startangle: 시작 위치를 지정, 90이면 y축 양의 방향에서 출발


```python
labels = ['Dog','Cat','Bug','Fish']
sizes = [45,30,10,15]
explode = (0.1,0,0,0)

plt.pie(sizes,explode=explode, labels=labels, 
        autopct='%1.1f%%', shadow=True, startangle=90 )

plt.axis('equal')
plt.show()
```


![png](output_17_0.png)


### 5. 히스토그램 
- bins: 나누어서 보여 줄 칸의 수
- density: True이면 y축을 확률로 변경, False이면 Count
- (n,m)좌표에 텍스트를 출력하기
- $로 감싸서 TeX 수식 사용 가능


```python
#데이터 준비
#seed는 재생산성을 위해 지정
np.random.seed(19680801)
mu,sigma = 100,15
x = mu + sigma * np.random.randn(10000)#정규분포에 가깝게 값 생성

#그래프 그리기
plt.hist(x, bins=50, density=True, facecolor='g',alpha=0.5)

plt.xlabel('Smarts')
plt.ylabel('probability')
plt.title('IQ 히스토그램')

plt.text(60,.014, r'$\mu=100,\ \sigma=15$')

plt.grid(True)
plt.show()
```


![png](output_19_0.png)


### 6. 여러 그래프 겹쳐 그리기
매개변수로 x, y pair를 연속하여 할당하면 여러 그래프를 동시에 그릴 수 있다.


```python
import numpy as np
t = np.arange(0.,5.,0.2)

plt.plot(t,t,'r--',t,t**2,'bs',t,t**3,'g^')
# 아래와 같이 나눠서 하는 것도 가능
#plt.plot(t, t, 'r--')
#plt.plot(t, t**2, 'bs')
#plt.plot(t, t**3, 'g^')

plt.show()
```


![png](output_21_0.png)


### 7. 선 속성 결정하기
`setp()`: 함수의 선 굵기, 모양 등 다양한 속성을 설정할 수 있다.


```python
t = np.arange(0.,5.,0.2)

line1 = plt.plot(t, t, label='같은값') #plot을 그릴 때, label을 지정할 수 있음
line2 = plt.plot(t, t**2, label='제곱')
line3 = plt.plot(t, t**3, label='세제곱')

plt.setp(line1, color='red', linestyle='--', marker='o')
plt.setp(line2, color='blue', linestyle='-.', marker='s')
plt.setp(line3, color='green', linestyle=':', marker='^')

plt.legend(loc='upper right') #지정된 label을 이용해서 범례(legend)를 그림, loc은 legend의 위치를 지정

plt.show()
```


![png](output_23_0.png)


### 8. 화면 분할하여 여러 그래프 그리기


```python
def p_graph(t):
    return np.exp(-t) * np.cos(2*np.pi*t)

x = np.arange(0.0, 5.0, 0.1)
f,axarr = plt.subplots(2, sharex=True) #x를 공유한다.

f.suptitle('Sharing X axis')
axarr[0].plot(x, p_graph(x), 'bo') #첫째 subplot에 그림을 그림
axarr[1].plot(x, np.cos(2*np.pi*x), 'r--') #둘째 subplot에 그림을 그림

plt.show()
 
```


![png](output_25_0.png)



```python
x = np.linspace(0, 2 * np.pi, 400) #주어진 범위(0~2*np.pi) 사이에 400개의 등간격 숫자를 생성
y = np.sin(x ** 2)

f, axarr = plt.subplots(2, 2, sharex='col', sharey='row', figsize=(10, 6)) #2x2의 subplot 생성, figsize로 각 subplot의 크기를 지정
f.suptitle('Sharing x per column, y per row')

axarr[0, 0].plot(x, y)
axarr[0, 1].scatter(x, y)
axarr[1, 0].scatter(x, 2 * y ** 2 - 1, color='r')
axarr[1, 1].plot(x, 2 * y ** 2 - 1, color='r')
plt.show()
```


![png](output_26_0.png)



```python
f = plt.figure(figsize=(10, 6)) #전체 그림판 설정 및 그래프 크기 설정

plt.subplot(2,2,1) #rows = 2, columns = 2로 나눈 것 중에서 첫째 subplot을 지정
plt.plot(x, y)

plt.subplot(2,2,2)
plt.scatter(x, y)

plt.subplot(2,2,3)
plt.scatter(x, 2 * y ** 2 - 1, color='r')

plt.subplot(2,2,4)
plt.plot(x, 2 * y ** 2 - 1, color='r')
plt.show()

```


![png](output_27_0.png)



```python
#그림을 pdf로 저장하기

f.savefig("foo.pdf", bbox_inches='tight')
```

### 9. Kernel Density Estimation
어떤 연속확률변수의 분포를 근사해내고자 하는 것인데, 쉽게 말해서 각 값에 대해 어느 정도의 확률이 있는지를 함수 혹은 그래프로 표현하고자 하는 것을 말한다.<br>
주어진 값들을 이용해 히스토그램을 그리면 유사한 분포를 얻을 수 있는데, 이 때 히스토그램은 우리에게 그 변수의 분포에 대한 대략적인 모양을 알려준다.<br>
그러나, 히스토그램은 불연속적(막대들이 결합된 모습)이고, bin-각 막대의 크기에 따라 모양이 달라지는 등의 문제가 있다.<br>
KDE는 이를 보완하기 위해 히스토그램을 부드럽게 smoothing한 형태라고 이해할 수 있다.


```python
#데이터 준비
from sklearn.datasets import load_breast_cancer
cancer = load_breast_cancer()
X, Y = cancer.data[:, 0], cancer.target
```


```python
#먼저 scatter를 이용해 두 그룹의 모양을 살펴보고자 함

plt.scatter(X, Y)
plt.show()
```


![png](output_31_0.png)


X 값 근처에 점들이 많이 겹쳐있는지 조금 겹쳐있는지를 알기 어려워 X 값이 어디에 집중적으로 위치하는지를 판단하기 어렵다.<br>
이와 같은 문제는 히스토그램을 그려서 해결이 가능하다.


```python
X0 = X[Y == 0] # Y가 0인 값을 분리
X1 = X[Y == 1] # Y가 1인 값을 분리

plt.hist(X0, bins=20, color='red', alpha=.5)
plt.hist(X1, bins=20, color='blue', alpha=.5)
plt.show()
```


![png](output_33_0.png)


히스토그램은 불연속적인 경계와 적절한 bin의 수를 잘 선택해야 한다는 등의 문제가 있으므로 KDE를 통해 연속적인 그래프를 그리면 더 보기가 편하다.


```python
import seaborn as sns
#sns.set_style('whitegrid')
g = sns.kdeplot(X0)
g = sns.kdeplot(X1)
```

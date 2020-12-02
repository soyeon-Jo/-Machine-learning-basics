# Pandas 
(panel data analysis / python data analysis의 약자)

- Numpy 라이브러리 기반으로 구축한다.
- 관계형 데이터를 만들고 조작하기 위한 python 라이브러리이다.
- CSV, 엑셀, Database(SQL), Json 등 다양한 데이터를 입출력 할 수 있다.
-  데이터를 필요한 대로 조작(삽입, 삭제, 병합, 결합, 슬라이싱, 인덱싱, 등)할 수 있다.
- 통계분석이나 머신 러닝 분석이 가능하도록 연구모델을 설정할 수 있다.
- Statsmodel, SciPy 등 다양한 데이터 분석 패키지와 쉽게 연동되어 사용할 수 있다.
- NumPy처럼 빠른 속도로 데이터를 처리할 수 있음.<br>
<br>
<br>

Pandas 사용


```python
import pandas as pd
```

## Series와 data frame
### Series : index가 있는 1차원 배열


```python
a = pd.Series([1,3,5,7,9])

print(a)
print(a[0]) #인덱싱
```

    0    1
    1    3
    2    5
    3    7
    4    9
    dtype: int64
    1
    

- Series를 이용해 딕셔너리 만들기


```python
dic = {'a':1, 'b':2, 'c':3 }

a = pd.Series(dic)
print(a)
print(a['a']) #인덱싱
```

    a    1
    b    2
    c    3
    dtype: int64
    1
    

- Series 구성요소<br>
: **index**<br>
: **values**


```python
print(a.index)
print(a.values)
```

    Index(['a', 'b', 'c'], dtype='object')
    [1 2 3]
    

- Index 부여하기


```python
a = pd.Series([1,2,3,4,5], index = ['x','y','z','a','b'])

print(a)
print(a[:'a']) #a를 포함하여 슬라이싱 한다.
```

    x    1
    y    2
    z    3
    a    4
    b    5
    dtype: int64
    x    1
    y    2
    z    3
    a    4
    dtype: int64
    

### Data Frame
: 2차원 표와 같은 형태. 행(row),열(column)으로 이루어져 있다.<br>
: 각 열에는 name, 각 행에는 index가 있다.


```python
music = {'제목':['사라지는 꿈','잠이 안와','매트리스'],
         '가수':['술탄오브더디스코','소란','10cm'],
         '최고 순위':[89,50,1],
         '등록 번호':[19231,33457,75432]}

music_df = pd.DataFrame(music)
music_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>제목</th>
      <th>가수</th>
      <th>최고 순위</th>
      <th>등록 번호</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>사라지는 꿈</td>
      <td>술탄오브더디스코</td>
      <td>89</td>
      <td>19231</td>
    </tr>
    <tr>
      <th>1</th>
      <td>잠이 안와</td>
      <td>소란</td>
      <td>50</td>
      <td>33457</td>
    </tr>
    <tr>
      <th>2</th>
      <td>매트리스</td>
      <td>10cm</td>
      <td>1</td>
      <td>75432</td>
    </tr>
  </tbody>
</table>
</div>



### DataFrame 다루기


```python
d = {
    'Name':['Alisa','Bobby','Cathrine','Madonna','Rocky','Sebastian','Jaqluine',
   'Rahul','David','Andrew','Ajay','Teresa'],
   'Age':[26,27,25,24,31,27,25,33,42,32,51,47],
   'Score':[89,87,67,55,47,72,76,79,44,92,99,69]}
 
df = pd.DataFrame(d)
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Alisa</td>
      <td>26</td>
      <td>89</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Bobby</td>
      <td>27</td>
      <td>87</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Cathrine</td>
      <td>25</td>
      <td>67</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Madonna</td>
      <td>24</td>
      <td>55</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rocky</td>
      <td>31</td>
      <td>47</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Sebastian</td>
      <td>27</td>
      <td>72</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Jaqluine</td>
      <td>25</td>
      <td>76</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Rahul</td>
      <td>33</td>
      <td>79</td>
    </tr>
    <tr>
      <th>8</th>
      <td>David</td>
      <td>42</td>
      <td>44</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Andrew</td>
      <td>32</td>
      <td>92</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Ajay</td>
      <td>51</td>
      <td>99</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Teresa</td>
      <td>47</td>
      <td>69</td>
    </tr>
  </tbody>
</table>
</div>



- 행과 열 추출하기




```python
df[['Name','Age']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Alisa</td>
      <td>26</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Bobby</td>
      <td>27</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Cathrine</td>
      <td>25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Madonna</td>
      <td>24</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rocky</td>
      <td>31</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Sebastian</td>
      <td>27</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Jaqluine</td>
      <td>25</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Rahul</td>
      <td>33</td>
    </tr>
    <tr>
      <th>8</th>
      <td>David</td>
      <td>42</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Andrew</td>
      <td>32</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Ajay</td>
      <td>51</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Teresa</td>
      <td>47</td>
    </tr>
  </tbody>
</table>
</div>



인덱싱을 할 ```[ ]``` 안에 하나의 값을 쓰느냐, 아니면 리스트 형태를 쓰느냐에 따라 반환되는 값의 타입이 달라진다. 하나의 값을 쓰는 경우는 시리즈를, 리스트 형태를 쓰면 데이터프레임을 반환한다.


```python
print(type(df['Name']))
print(type(df[['Name']]))
```

    <class 'pandas.core.series.Series'>
    <class 'pandas.core.frame.DataFrame'>
    

```[ ]``` 안에 열의 이름이 아닌 숫자를 쓰면 행을 반환하는 것이 가능하다.<br> <u> 이 경우는 슬라이싱만 가능 </u>


```python
df[0:3]  #df[2]는 에러 발생
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Alisa</td>
      <td>26</td>
      <td>89</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Bobby</td>
      <td>27</td>
      <td>87</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Cathrine</td>
      <td>25</td>
      <td>67</td>
    </tr>
  </tbody>
</table>
</div>



## loc과 iloc을 이용한 인덱싱, 슬라이싱
**loc** <br> : 명시된 index로 인덱싱, 슬라이싱<br>
          : 인덱싱하는 값을 포함한다.<br>
      <br>
**iloc**<br> : 내부적으로 정렬된 순서(원래 index)로 인덱싱, 슬라이싱<br>
          : 인덱싱하는 값을 포함하지 않는다.<br>
         
**<u>iloc은 위치를 보고 loc은 라벨을 본다.</u>**



```python
df=df.reindex([1,4,6,2,3,5,9,8,0,7,11,10]) 

df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>Bobby</td>
      <td>27</td>
      <td>87</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rocky</td>
      <td>31</td>
      <td>47</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Jaqluine</td>
      <td>25</td>
      <td>76</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Cathrine</td>
      <td>25</td>
      <td>67</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Madonna</td>
      <td>24</td>
      <td>55</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Sebastian</td>
      <td>27</td>
      <td>72</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Andrew</td>
      <td>32</td>
      <td>92</td>
    </tr>
    <tr>
      <th>8</th>
      <td>David</td>
      <td>42</td>
      <td>44</td>
    </tr>
    <tr>
      <th>0</th>
      <td>Alisa</td>
      <td>26</td>
      <td>89</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Rahul</td>
      <td>33</td>
      <td>79</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Teresa</td>
      <td>47</td>
      <td>69</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Ajay</td>
      <td>51</td>
      <td>99</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.loc[:6]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>Bobby</td>
      <td>27</td>
      <td>87</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rocky</td>
      <td>31</td>
      <td>47</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Jaqluine</td>
      <td>25</td>
      <td>76</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.iloc[:6]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>Bobby</td>
      <td>27</td>
      <td>87</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rocky</td>
      <td>31</td>
      <td>47</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Jaqluine</td>
      <td>25</td>
      <td>76</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Cathrine</td>
      <td>25</td>
      <td>67</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Madonna</td>
      <td>24</td>
      <td>55</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Sebastian</td>
      <td>27</td>
      <td>72</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1 = df.sort_index()
df1
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Alisa</td>
      <td>26</td>
      <td>89</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Bobby</td>
      <td>27</td>
      <td>87</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Cathrine</td>
      <td>25</td>
      <td>67</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Madonna</td>
      <td>24</td>
      <td>55</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rocky</td>
      <td>31</td>
      <td>47</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Sebastian</td>
      <td>27</td>
      <td>72</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Jaqluine</td>
      <td>25</td>
      <td>76</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Rahul</td>
      <td>33</td>
      <td>79</td>
    </tr>
    <tr>
      <th>8</th>
      <td>David</td>
      <td>42</td>
      <td>44</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Andrew</td>
      <td>32</td>
      <td>92</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Ajay</td>
      <td>51</td>
      <td>99</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Teresa</td>
      <td>47</td>
      <td>69</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1.loc[:6]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Alisa</td>
      <td>26</td>
      <td>89</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Bobby</td>
      <td>27</td>
      <td>87</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Cathrine</td>
      <td>25</td>
      <td>67</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Madonna</td>
      <td>24</td>
      <td>55</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rocky</td>
      <td>31</td>
      <td>47</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Sebastian</td>
      <td>27</td>
      <td>72</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Jaqluine</td>
      <td>25</td>
      <td>76</td>
    </tr>
  </tbody>
</table>
</div>




```python
df1.iloc[:6]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Alisa</td>
      <td>26</td>
      <td>89</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Bobby</td>
      <td>27</td>
      <td>87</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Cathrine</td>
      <td>25</td>
      <td>67</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Madonna</td>
      <td>24</td>
      <td>55</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rocky</td>
      <td>31</td>
      <td>47</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Sebastian</td>
      <td>27</td>
      <td>72</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2 = df.sort_index(ascending=False)
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
      <th>Score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>11</th>
      <td>Teresa</td>
      <td>47</td>
      <td>69</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Ajay</td>
      <td>51</td>
      <td>99</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Andrew</td>
      <td>32</td>
      <td>92</td>
    </tr>
    <tr>
      <th>8</th>
      <td>David</td>
      <td>42</td>
      <td>44</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Rahul</td>
      <td>33</td>
      <td>79</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Jaqluine</td>
      <td>25</td>
      <td>76</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Sebastian</td>
      <td>27</td>
      <td>72</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rocky</td>
      <td>31</td>
      <td>47</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Madonna</td>
      <td>24</td>
      <td>55</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Cathrine</td>
      <td>25</td>
      <td>67</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Bobby</td>
      <td>27</td>
      <td>87</td>
    </tr>
    <tr>
      <th>0</th>
      <td>Alisa</td>
      <td>26</td>
      <td>89</td>
    </tr>
  </tbody>
</table>
</div>



## loc과 iloc을 이용해 열(column)추출하기


```python
df2.iloc[:,2]
```




    11    69
    10    99
    9     92
    8     44
    7     79
    6     76
    5     72
    4     47
    3     55
    2     67
    1     87
    0     89
    Name: Score, dtype: int64




```python
df2.loc[:,['Name','Age']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>11</th>
      <td>Teresa</td>
      <td>47</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Ajay</td>
      <td>51</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Andrew</td>
      <td>32</td>
    </tr>
    <tr>
      <th>8</th>
      <td>David</td>
      <td>42</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Rahul</td>
      <td>33</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Jaqluine</td>
      <td>25</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Sebastian</td>
      <td>27</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rocky</td>
      <td>31</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Madonna</td>
      <td>24</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Cathrine</td>
      <td>25</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Bobby</td>
      <td>27</td>
    </tr>
    <tr>
      <th>0</th>
      <td>Alisa</td>
      <td>26</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2.iloc[:,:2]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>11</th>
      <td>Teresa</td>
      <td>47</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Ajay</td>
      <td>51</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Andrew</td>
      <td>32</td>
    </tr>
    <tr>
      <th>8</th>
      <td>David</td>
      <td>42</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Rahul</td>
      <td>33</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Jaqluine</td>
      <td>25</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Sebastian</td>
      <td>27</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rocky</td>
      <td>31</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Madonna</td>
      <td>24</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Cathrine</td>
      <td>25</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Bobby</td>
      <td>27</td>
    </tr>
    <tr>
      <th>0</th>
      <td>Alisa</td>
      <td>26</td>
    </tr>
  </tbody>
</table>
</div>




```python

```

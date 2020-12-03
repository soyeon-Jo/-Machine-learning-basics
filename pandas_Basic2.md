# Pandas _2


```python
import pandas as pd
```

## csv파일 읽기
데이터 분석에서 가장 많이 사용하는 데이터 파일 포맷으로 <br>andas에서 쉽게 읽어들이는 것이 가능하다.<br>
<br>- ```pd.read_csv('파일이름')``` 를 이용하여 읽어들이면 dataframe 변수 형태로 내용을 반환한다.


```python
df = pd.read_csv('diabetes.csv')
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
      <th>Pregnancies</th>
      <th>Glucose</th>
      <th>BloodPressure</th>
      <th>SkinThickness</th>
      <th>Insulin</th>
      <th>BMI</th>
      <th>DiabetesPedigreeFunction</th>
      <th>Age</th>
      <th>Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>6</td>
      <td>148</td>
      <td>72</td>
      <td>35</td>
      <td>0</td>
      <td>33.6</td>
      <td>0.627</td>
      <td>50</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>85</td>
      <td>66</td>
      <td>29</td>
      <td>0</td>
      <td>26.6</td>
      <td>0.351</td>
      <td>31</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>183</td>
      <td>64</td>
      <td>0</td>
      <td>0</td>
      <td>23.3</td>
      <td>0.672</td>
      <td>32</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>89</td>
      <td>66</td>
      <td>23</td>
      <td>94</td>
      <td>28.1</td>
      <td>0.167</td>
      <td>21</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>137</td>
      <td>40</td>
      <td>35</td>
      <td>168</td>
      <td>43.1</td>
      <td>2.288</td>
      <td>33</td>
      <td>1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>763</th>
      <td>10</td>
      <td>101</td>
      <td>76</td>
      <td>48</td>
      <td>180</td>
      <td>32.9</td>
      <td>0.171</td>
      <td>63</td>
      <td>0</td>
    </tr>
    <tr>
      <th>764</th>
      <td>2</td>
      <td>122</td>
      <td>70</td>
      <td>27</td>
      <td>0</td>
      <td>36.8</td>
      <td>0.340</td>
      <td>27</td>
      <td>0</td>
    </tr>
    <tr>
      <th>765</th>
      <td>5</td>
      <td>121</td>
      <td>72</td>
      <td>23</td>
      <td>112</td>
      <td>26.2</td>
      <td>0.245</td>
      <td>30</td>
      <td>0</td>
    </tr>
    <tr>
      <th>766</th>
      <td>1</td>
      <td>126</td>
      <td>60</td>
      <td>0</td>
      <td>0</td>
      <td>30.1</td>
      <td>0.349</td>
      <td>47</td>
      <td>1</td>
    </tr>
    <tr>
      <th>767</th>
      <td>1</td>
      <td>93</td>
      <td>70</td>
      <td>31</td>
      <td>0</td>
      <td>30.4</td>
      <td>0.315</td>
      <td>23</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>768 rows × 9 columns</p>
</div>



## DataFrame 함수들

```파일이름.head()``` :첫 몇 줄(기본값 5)만 보기


```python
df.head()
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
      <th>Pregnancies</th>
      <th>Glucose</th>
      <th>BloodPressure</th>
      <th>SkinThickness</th>
      <th>Insulin</th>
      <th>BMI</th>
      <th>DiabetesPedigreeFunction</th>
      <th>Age</th>
      <th>Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>6</td>
      <td>148</td>
      <td>72</td>
      <td>35</td>
      <td>0</td>
      <td>33.6</td>
      <td>0.627</td>
      <td>50</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>85</td>
      <td>66</td>
      <td>29</td>
      <td>0</td>
      <td>26.6</td>
      <td>0.351</td>
      <td>31</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8</td>
      <td>183</td>
      <td>64</td>
      <td>0</td>
      <td>0</td>
      <td>23.3</td>
      <td>0.672</td>
      <td>32</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>89</td>
      <td>66</td>
      <td>23</td>
      <td>94</td>
      <td>28.1</td>
      <td>0.167</td>
      <td>21</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>137</td>
      <td>40</td>
      <td>35</td>
      <td>168</td>
      <td>43.1</td>
      <td>2.288</td>
      <td>33</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



```파일이름.tail()``` : 마지막 몇 줄 


```python
df.tail()
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
      <th>Pregnancies</th>
      <th>Glucose</th>
      <th>BloodPressure</th>
      <th>SkinThickness</th>
      <th>Insulin</th>
      <th>BMI</th>
      <th>DiabetesPedigreeFunction</th>
      <th>Age</th>
      <th>Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>763</th>
      <td>10</td>
      <td>101</td>
      <td>76</td>
      <td>48</td>
      <td>180</td>
      <td>32.9</td>
      <td>0.171</td>
      <td>63</td>
      <td>0</td>
    </tr>
    <tr>
      <th>764</th>
      <td>2</td>
      <td>122</td>
      <td>70</td>
      <td>27</td>
      <td>0</td>
      <td>36.8</td>
      <td>0.340</td>
      <td>27</td>
      <td>0</td>
    </tr>
    <tr>
      <th>765</th>
      <td>5</td>
      <td>121</td>
      <td>72</td>
      <td>23</td>
      <td>112</td>
      <td>26.2</td>
      <td>0.245</td>
      <td>30</td>
      <td>0</td>
    </tr>
    <tr>
      <th>766</th>
      <td>1</td>
      <td>126</td>
      <td>60</td>
      <td>0</td>
      <td>0</td>
      <td>30.1</td>
      <td>0.349</td>
      <td>47</td>
      <td>1</td>
    </tr>
    <tr>
      <th>767</th>
      <td>1</td>
      <td>93</td>
      <td>70</td>
      <td>31</td>
      <td>0</td>
      <td>30.4</td>
      <td>0.315</td>
      <td>23</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



```파일이름.shape``` : 행과 열의 수를 나타낸다.


```python
df.shape
```




    (768, 9)



```파일이름.describe()``` : 각 열에 대한 평균, 최소값 등 통계량을 보여준다.


```python
df.describe()
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
      <th>Pregnancies</th>
      <th>Glucose</th>
      <th>BloodPressure</th>
      <th>SkinThickness</th>
      <th>Insulin</th>
      <th>BMI</th>
      <th>DiabetesPedigreeFunction</th>
      <th>Age</th>
      <th>Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>768.000000</td>
      <td>768.000000</td>
      <td>768.000000</td>
      <td>768.000000</td>
      <td>768.000000</td>
      <td>768.000000</td>
      <td>768.000000</td>
      <td>768.000000</td>
      <td>768.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>3.845052</td>
      <td>120.894531</td>
      <td>69.105469</td>
      <td>20.536458</td>
      <td>79.799479</td>
      <td>31.992578</td>
      <td>0.471876</td>
      <td>33.240885</td>
      <td>0.348958</td>
    </tr>
    <tr>
      <th>std</th>
      <td>3.369578</td>
      <td>31.972618</td>
      <td>19.355807</td>
      <td>15.952218</td>
      <td>115.244002</td>
      <td>7.884160</td>
      <td>0.331329</td>
      <td>11.760232</td>
      <td>0.476951</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.078000</td>
      <td>21.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>1.000000</td>
      <td>99.000000</td>
      <td>62.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>27.300000</td>
      <td>0.243750</td>
      <td>24.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>3.000000</td>
      <td>117.000000</td>
      <td>72.000000</td>
      <td>23.000000</td>
      <td>30.500000</td>
      <td>32.000000</td>
      <td>0.372500</td>
      <td>29.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>6.000000</td>
      <td>140.250000</td>
      <td>80.000000</td>
      <td>32.000000</td>
      <td>127.250000</td>
      <td>36.600000</td>
      <td>0.626250</td>
      <td>41.000000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>17.000000</td>
      <td>199.000000</td>
      <td>122.000000</td>
      <td>99.000000</td>
      <td>846.000000</td>
      <td>67.100000</td>
      <td>2.420000</td>
      <td>81.000000</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>



```파일이름.columns.tolist()``` : 각 열의 이름을 리스트로 반환한다.


```python
df.columns.tolist()
```




    ['Pregnancies',
     'Glucose',
     'BloodPressure',
     'SkinThickness',
     'Insulin',
     'BMI',
     'DiabetesPedigreeFunction',
     'Age',
     'Outcome']



```파일이름.max()``` : 열 혹은 각 열의 최대값을 구한다.


```python
df.max()
```




    Pregnancies                  17.00
    Glucose                     199.00
    BloodPressure               122.00
    SkinThickness                99.00
    Insulin                     846.00
    BMI                          67.10
    DiabetesPedigreeFunction      2.42
    Age                          81.00
    Outcome                       1.00
    dtype: float64




```python
df['BMI'].max()
```




    67.1



```파일이름.mean()```: 열, 각 열의 평균을 구한다.


```python
df.mean()
```




    Pregnancies                   3.845052
    Glucose                     120.894531
    BloodPressure                69.105469
    SkinThickness                20.536458
    Insulin                      79.799479
    BMI                          31.992578
    DiabetesPedigreeFunction      0.471876
    Age                          33.240885
    Outcome                       0.348958
    dtype: float64




```python
df['Age'].mean()
```




    33.240885416666664



```파일이름.idxmax()``` : 값이 최대인 행의 위치를 찾아준다.
<br>ex) 나이가 가장 많은 행의 Index를 찾고 싶다.


```python
df['Age'].idxmax()
```




    459




```python
df.loc[459]
```




    Pregnancies                   9.00
    Glucose                     134.00
    BloodPressure                74.00
    SkinThickness                33.00
    Insulin                      60.00
    BMI                          25.90
    DiabetesPedigreeFunction      0.46
    Age                          81.00
    Outcome                       0.00
    Name: 459, dtype: float64




```python
df.loc[df['Age'].idxmax()]
```




    Pregnancies                   9.00
    Glucose                     134.00
    BloodPressure                74.00
    SkinThickness                33.00
    Insulin                      60.00
    BMI                          25.90
    DiabetesPedigreeFunction      0.46
    Age                          81.00
    Outcome                       0.00
    Name: 459, dtype: float64



```파일이름.value_counts()``` : 특정 열에 사용된 값들의 횟수를 계산하여 보여준다.


```python
df['Pregnancies'].value_counts()
```




    1     135
    0     111
    2     103
    3      75
    4      68
    5      57
    6      50
    7      45
    8      38
    9      28
    10     24
    11     11
    13     10
    12      9
    14      2
    15      1
    17      1
    Name: Pregnancies, dtype: int64



### DataFrame 값 추출하기
<br>
ex)나이가 가장 많은 사람의 혈압만 가져오고 싶다.


```python
df.loc[df['Age'].idxmax()]['BloodPressure']
```




    74.0




```python
df.loc[df['Age'].idxmax(),'BloodPressure']
```




    74



### 정렬(Sorting)
```파일이름. sort_values()``` : 원하는 열에 따라 오름차순으로 정렬하기


```python
df.sort_values('Pregnancies')
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
      <th>Pregnancies</th>
      <th>Glucose</th>
      <th>BloodPressure</th>
      <th>SkinThickness</th>
      <th>Insulin</th>
      <th>BMI</th>
      <th>DiabetesPedigreeFunction</th>
      <th>Age</th>
      <th>Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>467</th>
      <td>0</td>
      <td>97</td>
      <td>64</td>
      <td>36</td>
      <td>100</td>
      <td>36.8</td>
      <td>0.600</td>
      <td>25</td>
      <td>0</td>
    </tr>
    <tr>
      <th>109</th>
      <td>0</td>
      <td>95</td>
      <td>85</td>
      <td>25</td>
      <td>36</td>
      <td>37.4</td>
      <td>0.247</td>
      <td>24</td>
      <td>1</td>
    </tr>
    <tr>
      <th>452</th>
      <td>0</td>
      <td>91</td>
      <td>68</td>
      <td>32</td>
      <td>210</td>
      <td>39.9</td>
      <td>0.381</td>
      <td>25</td>
      <td>0</td>
    </tr>
    <tr>
      <th>449</th>
      <td>0</td>
      <td>120</td>
      <td>74</td>
      <td>18</td>
      <td>63</td>
      <td>30.5</td>
      <td>0.285</td>
      <td>26</td>
      <td>0</td>
    </tr>
    <tr>
      <th>448</th>
      <td>0</td>
      <td>104</td>
      <td>64</td>
      <td>37</td>
      <td>64</td>
      <td>33.6</td>
      <td>0.510</td>
      <td>22</td>
      <td>1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>357</th>
      <td>13</td>
      <td>129</td>
      <td>0</td>
      <td>30</td>
      <td>0</td>
      <td>39.9</td>
      <td>0.569</td>
      <td>44</td>
      <td>1</td>
    </tr>
    <tr>
      <th>298</th>
      <td>14</td>
      <td>100</td>
      <td>78</td>
      <td>25</td>
      <td>184</td>
      <td>36.6</td>
      <td>0.412</td>
      <td>46</td>
      <td>1</td>
    </tr>
    <tr>
      <th>455</th>
      <td>14</td>
      <td>175</td>
      <td>62</td>
      <td>30</td>
      <td>0</td>
      <td>33.6</td>
      <td>0.212</td>
      <td>38</td>
      <td>1</td>
    </tr>
    <tr>
      <th>88</th>
      <td>15</td>
      <td>136</td>
      <td>70</td>
      <td>32</td>
      <td>110</td>
      <td>37.1</td>
      <td>0.153</td>
      <td>43</td>
      <td>1</td>
    </tr>
    <tr>
      <th>159</th>
      <td>17</td>
      <td>163</td>
      <td>72</td>
      <td>41</td>
      <td>114</td>
      <td>40.9</td>
      <td>0.817</td>
      <td>47</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>768 rows × 9 columns</p>
</div>



```파일이름.sort_values(ascending=False)```: 내림차순으로 정렬하기


```python
df.sort_values('Pregnancies', ascending = False)
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
      <th>Pregnancies</th>
      <th>Glucose</th>
      <th>BloodPressure</th>
      <th>SkinThickness</th>
      <th>Insulin</th>
      <th>BMI</th>
      <th>DiabetesPedigreeFunction</th>
      <th>Age</th>
      <th>Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>159</th>
      <td>17</td>
      <td>163</td>
      <td>72</td>
      <td>41</td>
      <td>114</td>
      <td>40.9</td>
      <td>0.817</td>
      <td>47</td>
      <td>1</td>
    </tr>
    <tr>
      <th>88</th>
      <td>15</td>
      <td>136</td>
      <td>70</td>
      <td>32</td>
      <td>110</td>
      <td>37.1</td>
      <td>0.153</td>
      <td>43</td>
      <td>1</td>
    </tr>
    <tr>
      <th>298</th>
      <td>14</td>
      <td>100</td>
      <td>78</td>
      <td>25</td>
      <td>184</td>
      <td>36.6</td>
      <td>0.412</td>
      <td>46</td>
      <td>1</td>
    </tr>
    <tr>
      <th>455</th>
      <td>14</td>
      <td>175</td>
      <td>62</td>
      <td>30</td>
      <td>0</td>
      <td>33.6</td>
      <td>0.212</td>
      <td>38</td>
      <td>1</td>
    </tr>
    <tr>
      <th>274</th>
      <td>13</td>
      <td>106</td>
      <td>70</td>
      <td>0</td>
      <td>0</td>
      <td>34.2</td>
      <td>0.251</td>
      <td>52</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>291</th>
      <td>0</td>
      <td>107</td>
      <td>62</td>
      <td>30</td>
      <td>74</td>
      <td>36.6</td>
      <td>0.757</td>
      <td>25</td>
      <td>1</td>
    </tr>
    <tr>
      <th>608</th>
      <td>0</td>
      <td>152</td>
      <td>82</td>
      <td>39</td>
      <td>272</td>
      <td>41.5</td>
      <td>0.270</td>
      <td>27</td>
      <td>0</td>
    </tr>
    <tr>
      <th>294</th>
      <td>0</td>
      <td>161</td>
      <td>50</td>
      <td>0</td>
      <td>0</td>
      <td>21.9</td>
      <td>0.254</td>
      <td>65</td>
      <td>0</td>
    </tr>
    <tr>
      <th>297</th>
      <td>0</td>
      <td>126</td>
      <td>84</td>
      <td>29</td>
      <td>215</td>
      <td>30.7</td>
      <td>0.520</td>
      <td>24</td>
      <td>0</td>
    </tr>
    <tr>
      <th>466</th>
      <td>0</td>
      <td>74</td>
      <td>52</td>
      <td>10</td>
      <td>36</td>
      <td>27.8</td>
      <td>0.269</td>
      <td>22</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>768 rows × 9 columns</p>
</div>



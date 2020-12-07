# One Hot enoding
기계는 숫자를 더 잘 처리 할 수 있기 때문에, NLP에서는 문자를 숫자로 바꾸곤 한다. One-Hot Encoding은 Machine Learning과 Deep Learning에서 반드시 배워야 하는 Method이다. <br>

중복이 허용되지 않는 단어 집합을 벡터로 바꾸는 것이다. 가령 단어 집합의 개수가 5000개라면 인덱스가 총 5000번 까지 부여가 된다. One-Hot Vector는 각 인덱스에 벡터로 다루는 것이다.

<br>[출처] One-Hot Encoding|작성자 analyst


```python
import pandas as pd

df = pd.read_csv('insurance .csv')
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
      <th>age</th>
      <th>sex</th>
      <th>bmi</th>
      <th>children</th>
      <th>smoker</th>
      <th>region</th>
      <th>charges</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19</td>
      <td>female</td>
      <td>27.900</td>
      <td>0</td>
      <td>yes</td>
      <td>southwest</td>
      <td>16884.92400</td>
    </tr>
    <tr>
      <th>1</th>
      <td>18</td>
      <td>male</td>
      <td>33.770</td>
      <td>1</td>
      <td>no</td>
      <td>southeast</td>
      <td>1725.55230</td>
    </tr>
    <tr>
      <th>2</th>
      <td>28</td>
      <td>male</td>
      <td>33.000</td>
      <td>3</td>
      <td>no</td>
      <td>southeast</td>
      <td>4449.46200</td>
    </tr>
    <tr>
      <th>3</th>
      <td>33</td>
      <td>male</td>
      <td>22.705</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>21984.47061</td>
    </tr>
    <tr>
      <th>4</th>
      <td>32</td>
      <td>male</td>
      <td>28.880</td>
      <td>0</td>
      <td>no</td>
      <td>northwest</td>
      <td>3866.85520</td>
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
    </tr>
    <tr>
      <th>1333</th>
      <td>50</td>
      <td>male</td>
      <td>30.970</td>
      <td>3</td>
      <td>no</td>
      <td>northwest</td>
      <td>10600.54830</td>
    </tr>
    <tr>
      <th>1334</th>
      <td>18</td>
      <td>female</td>
      <td>31.920</td>
      <td>0</td>
      <td>no</td>
      <td>northeast</td>
      <td>2205.98080</td>
    </tr>
    <tr>
      <th>1335</th>
      <td>18</td>
      <td>female</td>
      <td>36.850</td>
      <td>0</td>
      <td>no</td>
      <td>southeast</td>
      <td>1629.83350</td>
    </tr>
    <tr>
      <th>1336</th>
      <td>21</td>
      <td>female</td>
      <td>25.800</td>
      <td>0</td>
      <td>no</td>
      <td>southwest</td>
      <td>2007.94500</td>
    </tr>
    <tr>
      <th>1337</th>
      <td>61</td>
      <td>female</td>
      <td>29.070</td>
      <td>0</td>
      <td>yes</td>
      <td>northwest</td>
      <td>29141.36030</td>
    </tr>
  </tbody>
</table>
<p>1338 rows × 7 columns</p>
</div>



위에 sex(female, male), smoker(yes,no), region(northeast, northwest, southeast, southwest) 두가지로 linear regression을 하려면?<br>
먼저,<br>
X와 Y를 분리


```python
X = df.iloc[:,:-1]
y = df.iloc[:,-1]

print(X)
print(y)
```

          age     sex     bmi  children smoker     region
    0      19  female  27.900         0    yes  southwest
    1      18    male  33.770         1     no  southeast
    2      28    male  33.000         3     no  southeast
    3      33    male  22.705         0     no  northwest
    4      32    male  28.880         0     no  northwest
    ...   ...     ...     ...       ...    ...        ...
    1333   50    male  30.970         3     no  northwest
    1334   18  female  31.920         0     no  northeast
    1335   18  female  36.850         0     no  southeast
    1336   21  female  25.800         0     no  southwest
    1337   61  female  29.070         0    yes  northwest
    
    [1338 rows x 6 columns]
    0       16884.92400
    1        1725.55230
    2        4449.46200
    3       21984.47061
    4        3866.85520
               ...     
    1333    10600.54830
    1334     2205.98080
    1335     1629.83350
    1336     2007.94500
    1337    29141.36030
    Name: charges, Length: 1338, dtype: float64
    

이대로 linear regression을 실행한다면 sex의 female과 male이 floa가 아니므로 error가 발생한다. <br>
때문에, female과 male을 수치로 바꿔야 한다.<br>
가장 쉬운 방법은 female은 0, male은 1로 변경하는 것이다. smoker의 yes,no도 마찬가지,<br>

'northeast', 'northwest', 'southeast', 'southwest'를 각각 0, 1, 2, 3으로 한다면
회귀분석을 돌릴 수는 있으나, 심각한 문제가 존재한다.
region의 각 값은 서열이 있거나, 서로 간의 거리가 달라서는 안되기 때문에
<br>
범주형 변수가 가지는 값 만큼 변수를 만들고 자기 위치만 1, 나머지는 0을 만들어서 변환 해준다.<br>
region의 경우는<br>

- 'northeast': [1, 0, 0, 0]
- 'northwest': [0, 1, 0, 0]
- 'southeast': [0, 0, 1, 0]
- 'southwest': [0, 0, 0, 1]
로 변환한다.


```python
from sklearn.preprocessing import OneHotEncoder
enc = OneHotEncoder(handle_unknown = 'ignore')

region = df['region'].to_numpy().reshape(-1,1)

enc.fit(region)

print(enc.categories_)
print(region[:5])
print(enc.transform(region[:5]).toarray())
```

    [array(['northeast', 'northwest', 'southeast', 'southwest'], dtype=object)]
    [['southwest']
     ['southeast']
     ['southeast']
     ['northwest']
     ['northwest']]
    [[0. 0. 0. 1.]
     [0. 0. 1. 0.]
     [0. 0. 1. 0.]
     [0. 1. 0. 0.]
     [0. 1. 0. 0.]]
    

sklearn의 OneHotEncoder는 범주형 변수 여러 개를 한꺼번에 처리할 수 있도록 지원


```python
df_category = df.iloc[:,[1,4,5]]
df_category
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
      <th>sex</th>
      <th>smoker</th>
      <th>region</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>female</td>
      <td>yes</td>
      <td>southwest</td>
    </tr>
    <tr>
      <th>1</th>
      <td>male</td>
      <td>no</td>
      <td>southeast</td>
    </tr>
    <tr>
      <th>2</th>
      <td>male</td>
      <td>no</td>
      <td>southeast</td>
    </tr>
    <tr>
      <th>3</th>
      <td>male</td>
      <td>no</td>
      <td>northwest</td>
    </tr>
    <tr>
      <th>4</th>
      <td>male</td>
      <td>no</td>
      <td>northwest</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1333</th>
      <td>male</td>
      <td>no</td>
      <td>northwest</td>
    </tr>
    <tr>
      <th>1334</th>
      <td>female</td>
      <td>no</td>
      <td>northeast</td>
    </tr>
    <tr>
      <th>1335</th>
      <td>female</td>
      <td>no</td>
      <td>southeast</td>
    </tr>
    <tr>
      <th>1336</th>
      <td>female</td>
      <td>no</td>
      <td>southwest</td>
    </tr>
    <tr>
      <th>1337</th>
      <td>female</td>
      <td>yes</td>
      <td>northwest</td>
    </tr>
  </tbody>
</table>
<p>1338 rows × 3 columns</p>
</div>




```python
enc = OneHotEncoder(handle_unknown='ignore')

enc.fit(df_category)

X_category = enc.transform(df_category).toarray()
print(X_category)
```

    [[1. 0. 0. ... 0. 0. 1.]
     [0. 1. 1. ... 0. 1. 0.]
     [0. 1. 1. ... 0. 1. 0.]
     ...
     [1. 0. 1. ... 0. 1. 0.]
     [1. 0. 1. ... 0. 0. 1.]
     [1. 0. 0. ... 1. 0. 0.]]
    


```python

```

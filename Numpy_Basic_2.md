# Numpy 

 ```np.arange``` : ndarray 형태로 모든 값을 생성


```python
print(np.arange(4))

```

    [0 1 2 3]
    

### 인덱싱

1.정수 배열 인덱싱<br>
: 행/열에서 원하는 요소만 가져올 때 유용


```python
a = np.array([[1,2,3], [4,5,6], [7,8,9], [10, 11, 12]])

b = np.array([0,2,0,1])
```


```python
#b의 각 행에서 해당하는 열의 값 가져오기

a[np.arange(4),b]

```




    array([ 1,  6,  7, 11])




```python
#가져오고 싶은 열에 원하는 값(n) 더하기 가능

a[np.arange(4),b] += 3

print(a)
```

    [[ 4  2  3]
     [ 4  5  9]
     [10  8  9]
     [10 14 12]]
    

2. 불리안 인덱싱<br>


```python
bb = np. array([1,2,3,4,5,6])

bb > 3
```


```python
bb[bb>3]
```




    array([4, 5, 6])



### 배열 연산
배열 연산은 기본적으로 요소단위로 이루어진다.



```python
x = np.array([[1,2],[3,4]], dtype=np.float64)
y = np.array([[5,6],[7,8]], dtype=np.float64)
```

위에 ```dtype=np.float64```는 데이터 타입을 명시하는 것이다.<br>
Numpy의 ndarray는 데이터 타입 지정이 가능하다.

**요소합**


```python
print(x + y)
print(np.add(x,y))
```

    [[ 6.  8.]
     [10. 12.]]
    [[ 6.  8.]
     [10. 12.]]
    

**요소차**


```python
print(x - y)
print(np.subtract(x,y))
```

    [[-4. -4.]
     [-4. -4.]]
    [[-4. -4.]
     [-4. -4.]]
    

**요소곱**


```python
print(x*y)
print(np.multiply(x,y))
```

    [[ 5. 12.]
     [21. 32.]]
    [[ 5. 12.]
     [21. 32.]]
    

**요소 나눗셈**


```python
print(x/y)
print(np.divide(x,y))
```

    [[0.2        0.33333333]
     [0.42857143 0.5       ]]
    [[0.2        0.33333333]
     [0.42857143 0.5       ]]
    

**요소 루트**


```python
print(np.sqrt(x))
```

    [[1.         1.41421356]
     [1.73205081 2.        ]]
    

**백터 내적**<br>




```python
x = np.array([[1,2],[3,4]]) #행렬
y = np.array([[5,6],[7,8]]) #행렬

v = np.array([9,10]) #백터
w = np.array([11,12])#백터

print(x, x.shape)
print(y, y.shape)
print(v, v.shape)
print(w, w.shape)
```

    [[1 2]
     [3 4]] (2, 2)
    [[5 6]
     [7 8]] (2, 2)
    [ 9 10] (2,)
    [11 12] (2,)
    

백터 내적은 ```dot```함수를 사용한다.


```python
print(v.dot(w))
print(np.dot(v,w))
```

    219
    219
    

행렬과 백터의 곱셈


```python
print(x.dot(v))
print(np.dot(x,v))
```

    [29 67]
    [29 67]
    

행렬 곱셈


```python
print(x.dot(y))
print(np.dot(x, y))
```

    [[19 22]
     [43 50]]
    [[19 22]
     [43 50]]
    

전치행렬


```python
x = np.array([[1,2,3],[4,5,6]])
print(x)
print(x.T)
```

    [[1 2 3]
     [4 5 6]]
    [[1 4]
     [2 5]
     [3 6]]
    

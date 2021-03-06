# Numpy

행렬 혹은 대규모 다차원 배열을 쉽게 처리 할 수 있도록 지원하는 파이썬의 라이브러리이다. 
데이터 구조 외에도 수치 계산을 위해 효율적으로 구현된 기능을 제공한다.


- Numpy 사용을 위해선 아래와 같이 ```numpy ``` package를 import 한다.


```python
import numpy as np
```

## 다차원 배열(Arrays)
같은 종류의 데이터를 담을 수 있는 다차원 배열.
원소는 모두 같은 자료형이어야 한다.




```python
# 1차원 배열 만들기
a = np.array([1,2,3])
print(a) #배열 모양 확인
print(type(a)) #저장된 자료형이 무엇인지
print(a.shape) #각 차원의 크기를 알려준다.
print(a[0],a[1],a[2])
```

    [1 2 3]
    <class 'numpy.ndarray'>
    (3,)
    1 2 3
    


```python
# 2차원 배열 만들기
b = np.array([ [1,2,3],[4,5,6] ])

print(b) 
print(type(b))
print(b.shape) #(열,행)
print(b[0, 0], b[0, 1], b[1, 0]) #인덱싱 예제
```

    [[1 2 3]
     [4 5 6]]
    <class 'numpy.ndarray'>
    (2, 3)
    1 2 4
    

- 이외에도 여러 배열을 생성 할 수 있다.

값이 모두 0인 배열


```python
a = np.zeros((5,4))
print(a)
```

    [[0. 0. 0. 0.]
     [0. 0. 0. 0.]
     [0. 0. 0. 0.]
     [0. 0. 0. 0.]
     [0. 0. 0. 0.]]
    

값이 모두 1인 배열


```python
b = np.ones((2,3))
print(b)
```

    [[1. 1. 1.]
     [1. 1. 1.]]
    

모든 원소가 원하는 값으로 설정된 배열 


```python
c = np.full((3,4),3)
print(c)
```

    [[3 3 3 3]
     [3 3 3 3]
     [3 3 3 3]]
    

원하는 단위의 행렬 만들기


```python
d = np.eye(6) #6*6 
print(d)
```

    [[1. 0. 0. 0. 0. 0.]
     [0. 1. 0. 0. 0. 0.]
     [0. 0. 1. 0. 0. 0.]
     [0. 0. 0. 1. 0. 0.]
     [0. 0. 0. 0. 1. 0.]
     [0. 0. 0. 0. 0. 1.]]
    

무작위값으로 이루어진 배열


```python
e = np.random.random((2,5))
print(e)
```

    [[0.3950827  0.98648288 0.30048067 0.49336727 0.81131251]
     [0.95181197 0.49055834 0.25517706 0.51196801 0.39504489]]
    

## 배열 인덱싱


```python
a = np.array([[1,2,3],[4,5,6],[7,8,9]])
print(a)

b = a[:2,1:3] #a의 일부를 꺼내옴
print(b)
```

    [[1 2 3]
     [4 5 6]
     [7 8 9]]
    [[2 3]
     [5 6]]
    

배열에서 일부 뽑아온 배열은 원래의 배열과 값을 공유한다.<br>
 -> <u>수정할 경우 원래의 배열도 값이 변경된다.</u>


```python
print(a[0, 1])
b[0, 0] = 99
print(b)
print(a)
```

    7
    [[99  3]
     [ 5  6]]
    [[ 1 99  3]
     [ 4  5  6]
     [ 7  8  9]]
    

배열 복사


```python
c = b.copy()
c[0,0] = 5
print(a)
print(c) #copy배열과 값을 공유하지 않는다
```

    [[ 1 99  3]
     [ 4  5  6]
     [ 7  8  9]]
    [[5 3]
     [5 6]]
    

# Classfication 2

### - 데이터 준비
                                    


```python
from sklearn.datasets import load_breast_cancer
cancer = load_breast_cancer()

print(cancer.data.shape, cancer.target.shape)

from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(cancer.data,cancer.target,
                                                   random_state=1)

print(X_train.shape, y_train.shape)
print(X_test.shape, y_test.shape)
```

    (569, 30) (569,)
    (426, 30) (426,)
    (143, 30) (143,)
    

### 1. 랜덤 포레스트 
**앙상블** : 여러 머신러닝 모델을 연결하여 더 강력한 모델을 만드는 기법<br>
기본적으로 조금씩 다른 여러 결정 트리의 묶음이다.<br>
서로 다른 방향으로 과대적합된 트리를 많이 만들어 그 결과를 평균을 냄으로써 과대적합을 줄인다.<br>

**부트스트랩 샘플** : n개의 data에서 중복을 허용하여 n개를 추출<br>
부트스트랩 샘플을 여러 번 (트리의 갯수 만큼) 수행하면 서로 다른 데이터로 이루어진 여러 샘플을 만들 수 있다.<br>
각 트리는 서로 다른 데이터를 사용할 뿐 아니라, 서로 다른 특성 집합을 사용하도록 한다.<br>
이 때 사용할 특성 집합의 수는 max_features로 조정하고 각 트리마다 무작위로 선택한다.<br>
max_features는 전체 특성 수보다는 적게 설정해야 서로 다른 트리를 만들어낼 수 있다.<br>


```python
from sklearn.ensemble import RandomForestClassifier
forest = RandomForestClassifier(n_estimators=5, random_state=7)

forest.fit(X_train,y_train)

print('Random Forest train set score: {:.3f}'.format(forest.score(X_train, y_train)))
print('Random Forest test set score: {:.3f}'.format(forest.score(X_test, y_test)))
```

    Random Forest train set score: 0.993
    Random Forest test set score: 0.937
    

**각 트리의 특성 중요도 확인**


```python
forest.estimators_[0].feature_importances_#첫번째 tree의 중요도
```




    array([0.        , 0.        , 0.04125953, 0.68112575, 0.00683925,
           0.05747052, 0.        , 0.00739243, 0.00136785, 0.00837809,
           0.0082071 , 0.        , 0.        , 0.        , 0.        ,
           0.        , 0.        , 0.0027357 , 0.        , 0.        ,
           0.01641421, 0.        , 0.06010454, 0.0202021 , 0.        ,
           0.        , 0.        , 0.07828458, 0.        , 0.01021833])




```python
print('Random Forest train set score: {:.3f}'.format(forest.score(X_train, y_train)))
print('Random Forest test set score: {:.3f}'.format(forest.score(X_test, y_test)))
```

    Random Forest train set score: 0.993
    Random Forest test set score: 0.937
    

### 2. 그래디언트 부스팅 회귀 트리(Gradient Boosting)
이전 트리의 오차를 보완하는 방식으로 순차적으로 트리를 생성한다.<br>
가장 강력하고 널리 사용하는 모델 중 하나이고<br>
트리 기반 모델은 특성상 희소한 고차원 데이터에는 잘 작동하지 않는다.<br>
**중요 매개변수: n_estimators, learning_rate, max_depth**


```python
from sklearn.ensemble import GradientBoostingClassifier
gb = GradientBoostingClassifier(random_state=7)

gb.fit(X_train,y_train)

print('Random Forest train set score: {:.3f}'.format(gb.score(X_train, y_train)))
print('Random Forest test set score: {:.3f}'.format(gb.score(X_test, y_test)))
```

    Random Forest train set score: 1.000
    Random Forest test set score: 0.965
    


```python
gb.feature_importances_
```




    array([9.04201644e-05, 1.85953011e-02, 8.84308418e-04, 1.22684016e-03,
           3.06991998e-04, 4.50535002e-04, 9.94588443e-04, 4.37071147e-02,
           1.93103858e-03, 1.58624997e-04, 2.07226183e-03, 7.53090344e-04,
           8.43606957e-04, 6.27172738e-03, 5.19792556e-05, 1.45762981e-03,
           1.61166767e-03, 1.77076763e-05, 3.39901847e-05, 1.56515105e-03,
           2.18175952e-01, 6.31340728e-02, 5.14799200e-01, 2.59496718e-02,
           3.47470417e-03, 1.99601813e-03, 1.60380186e-02, 7.28722668e-02,
           5.08488924e-04, 2.70318316e-05])



# 3. Support Vector Machine(SVM)
참고: https://en.wikipedia.org/wiki/Support_vector_machine<br>
https://medium.com/machine-learning-101/chapter-2-svm-support-vector-machine-theory-f0812effc72<br>

**서포트 벡터 머신(support vector machine, SVM)** 은 기계 학습의 분야 중 하나로 패턴 인식, 자료 분석을 위한 지도 학습 모델이며, 주로 분류와 회귀 분석을 위해 사용한다.<br>
두 카테고리 중 어느 하나에 속한 데이터의 집합이 주어졌을 때, SVM 알고리즘은 주어진 데이터 집합을 바탕으로 하여 새로운 데이터가 어느 카테고리에 속할지 판단하는 비확률적 이진 선형 분류 모델을 만든다.<br>
만들어진 분류 모델은 데이터가 사상된 공간에서 경계로 표현되는데 SVM 알고리즘은 그 중 가장 큰 폭을 가진 경계를 찾는 알고리즘이다. SVM은 선형 분류와 더불어 비선형 분류에서도 사용될 수 있다.<br> 비선형 분류를 하기 위해서 주어진 데이터를 고차원 특징 공간으로 사상하는 작업이 필요한데, 이를 효율적으로 하기 위해 커널 트릭을 사용하기도 한다.

#### SVM의 매개변수 튜닝<br>
**gamma** : 가우시안 커널 폭의 역수, <u>하나의 훈련 샘플이 미치는 영향의 범위</u>, 값이 작을수록 영향이 넓다<br>
Kernel coefficient for ‘rbf’, ‘poly’ and ‘sigmoid’<br>
**C** : 규제매개변수, linear regression에서 사용한 alpha의 역수 즉 값이 클수록 규제가 약해짐, default는 1.0


```python
from sklearn import svm
svm_clf = svm.SVC(gamma='auto')

svm_clf.fit(X_train,y_train)
svm_clf
```




    SVC(gamma='auto')




```python
print('SVM train set score: {:.3f}'.format(svm_clf.score(X_train, y_train)))
print('SVM test set score: {:.3f}'.format(svm_clf.score(X_test, y_test)))
```

    SVM train set score: 1.000
    SVM test set score: 0.615
    

**SVM과 Scaling**<br>
SVM은 scaling에 민감한 알고리즘 중 하나다.
따라서 SVM을 쓰고자 할 때는 가급적 scaling을 하는 것이 바람직하다.


```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler()
scaler.fit(X_train)

X_train_scaled = scaler.transform(X_train)
X_test_scaled = scaler.transform(X_test)

svm_clf.fit(X_train_scaled, y_train)
print("Scaled test set accuracy: {:.3f}".format(
    svm_clf.score(X_test_scaled, y_test)))
```

    Scaled test set accuracy: 0.944
    

svm은 다양한 kernel을 사용할 수 있다.<br>
**default는 rbf** 이며, linear, poly, rbf, sigmoid의 사용이 가능하다.


```python
svm_clf = svm.SVC(kernel='linear', gamma='auto')
 
svm_clf.fit(X_train_scaled, y_train) 


print('SVM train set score: {:.3f}'.format(svm_clf.score(X_train_scaled, y_train)))
print('SVM test set score: {:.3f}'.format(svm_clf.score(X_test_scaled, y_test)))
```

    SVM train set score: 0.986
    SVM test set score: 0.958
    

#### SVM 매개변수 튜닝
SVM은 gamma와 C를 튜닝하여 사용이 가능하다.


```python
svm_clf = svm.SVC(kernel='linear', gamma='auto', C=10)


svm_clf.fit(X_train_scaled, y_train) 
print('SVM train set score: {:.3f}'.format(svm_clf.score(X_train_scaled, y_train)))
print('SVM test set score: {:.3f}'.format(svm_clf.score(X_test_scaled, y_test)))
```

    SVM train set score: 0.986
    SVM test set score: 0.965
    

참고<br>
https://en.wikipedia.org/wiki/Support_vector_machine<br>
http://scikit-learn.org/stable/modules/generated/sklearn.svm.SVC.html#sklearn.svm.SVC<br>
https://ko.wikipedia.org/wiki/%EC%84%9C%ED%8F%AC%ED%8A%B8_%EB%B2<br>
https://ko.wikipedia.org/wiki/%EB%9E%9C%EB%8D%A4_%ED%8F%AC%EB%A0%<br>
https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html

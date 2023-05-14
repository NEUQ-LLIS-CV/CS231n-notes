<a name="rk3HQ"></a>
### 概述
KNN可用于解决分类或者回归问题

knn算法的基本法则是：相同类别的样本之间在特征空间中应当聚集在一起。

如图所示，绿色的为测试样本，当k取3时，该样本就属于红色类；当k取5时，就属于蓝色类了。所以k值的选择很大程度影响着该算法的结果，通常k的取值不大于20。

![](https://upload-images.jianshu.io/upload_images/3629157-d180f5f5f990ace7.png?imageMogr2/auto-orient/strip%7CimageView2/2#id=rrZG9&originalType=binary&status=done&style=none)

<a name="e8947773"></a>
### 距离公式

其中最常见的计算各点之间的方法是欧氏距离（Euclidean Distance）。欧氏距离就是计算 N 维空间中两点之间的距离。

![](https:////upload-images.jianshu.io/upload_images/2759738-8eb48ba88cbd91d7.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/262#id=CqHip&originalType=binary&status=done&style=none)

其他常用的方法还有：

- 汉明距离（Hamming Distance）
- 曼哈顿距离 (Manhattan Distance）
- 闵可夫斯基距离（Minkowski Distance）

预测结果和k的取值和计算距离方式的选取有关


<a name="cJTl9"></a>
### KNN实战演练

下面进行实战演练 -- 糖尿病预测

本数据可在kaggle中进行下载

![](https://upload-images.jianshu.io/upload_images/3629157-dcb07b473621e699.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/727#id=LN0eo&originalType=binary&status=done&style=none)

读入数据

把前8列作为特征，最后一项作为label

```
data = pd.read_csv('C:/Users/Administrator.WIN-948T8Q810Q2/AppData/Local/Temp/pima-indians-diabetes/diabetes.csv')



data.head()



X = data.iloc[:, 0:8]



Y = data.iloc[:,8]
```

然后切分数据集

```
X_train, X_test, Y_train, Y_test = train_test_split(X, Y, test_size=0.2, random_state=22)
```

我们用不同的K领近算法   使用交叉验证

```
model1 = KNeighborsClassifier(n_neighbors=2)
model1.fit(X_train, Y_train)
score1 = model1.score(X_test, Y_test)


model2 = KNeighborsClassifier(n_neighbors=2, weights='distance')
model2.fit(X_train, Y_train)
score2 = model2.score(X_test, Y_test)


model3 = RadiusNeighborsClassifier(n_neighbors=2, radius=500.0)
model3.fit(X_train, Y_train)
score3 = model3.score(X_test, Y_test)

result1 = cross_val_score(model1, X, Y, cv=10)
result2 = cross_val_score(model2, X, Y, cv=10)
result3 = cross_val_score(model3, X, Y, cv=10)

print(score1,score2,score3)
print(result1.mean(), result2.mean(), result3.mean())
```

用到的函数

```
from sklearn.neighbors import KNeighborsClassifier,RadiusNeighborsClassifier
from sklearn.model_selection import train_test_split
from sklearn.model_selection import cross_val_score
```

完整代码

```python3
import numpy as np
import pandas as pd
from sklearn.neighbors import KNeighborsClassifier,RadiusNeighborsClassifier
from sklearn.model_selection import train_test_split
from sklearn.model_selection import cross_val_score

data = pd.read_csv('Data.path')

data.head()

X = data.iloc[:, 0:8]

Y = data.iloc[:,8]

##切分数据集
X_train, X_test, Y_train, Y_test = train_test_split(X, Y, test_size=0.2, random_state=22)

model1 = KNeighborsClassifier(n_neighbors=2)
model1.fit(X_train, Y_train)
score1 = model1.score(X_test, Y_test)


model2 = KNeighborsClassifier(n_neighbors=2, weights='distance')
model2.fit(X_train, Y_train)
score2 = model2.score(X_test, Y_test)


model3 = RadiusNeighborsClassifier(n_neighbors=2, radius=500.0)
model3.fit(X_train, Y_train)
score3 = model3.score(X_test, Y_test)

result1 = cross_val_score(model1, X, Y, cv=10)
result2 = cross_val_score(model2, X, Y, cv=10)
result3 = cross_val_score(model3, X, Y, cv=10)

print(result1.mean(), result2.mean(), result3.mean())
```

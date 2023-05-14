
![image.png](https://cdn.nlark.com/yuque/0/2022/png/28450460/1652530391664-767267cb-780f-43b3-8750-9610468980b1.png#clientId=u530da8d5-d7fc-4&from=paste&height=428&id=u80f38f88&originHeight=749&originWidth=2391&originalType=binary&ratio=1&rotation=0&showTitle=false&size=244407&status=done&style=none&taskId=u72ee154c-bad3-4455-a1e7-f79978e92c2&title=&width=1366)<br />最近邻算法会有噪声或失真信号干扰，k近邻算法可以增加代码的泛化性。<br />[KNN Demo](http://vision.stanford.edu/teaching/cs231n-demos/knn/)
<a name="Metric"></a>
## Metric度量
L1 distance<br />L1的坐标轴变化后，会改变某些点的相对位置。<br />麦哈顿距离，两点的差的绝对值

![](https://g.yuque.com/gr/latex?d_1(I_1%2CI_2)%3D%5Csum_%7Bp%7D%5E%7B%7D%7CI%5E%7BP%7D_%7B1%7D-I%5E%7Bp%7D_%7B2%7D%7C%0A#card=math&code=d_1%28I_1%2CI_2%29%3D%5Csum_%7Bp%7D%5E%7B%7D%7CI%5E%7BP%7D_%7B1%7D-I%5E%7Bp%7D_%7B2%7D%7C%0A&id=PJHUW)

L2 distance<br />并不会受坐标轴影响<br />欧式距离,两点的直线距离

![](https://g.yuque.com/gr/latex?d_2(I_1%2CI_2)%3D%5Csqrt%7B%5Csum_%7Bp%7D%5E%7B%7D(I%5E%7BP%7D_%7B1%7D-I%5E%7Bp%7D_%7B2%7D)%5E2%7D%0A#card=math&code=d_2%28I_1%2CI_2%29%3D%5Csqrt%7B%5Csum_%7Bp%7D%5E%7B%7D%28I%5E%7BP%7D_%7B1%7D-I%5E%7Bp%7D_%7B2%7D%29%5E2%7D%0A&id=VUHvy)


<a name="eb02cead"></a>
## 超参数
选择的k的大小，选择用L1或者L2。<br />超参数-hyperparameters：<br />在训练学习之前就选择好的。
<a name="1b2e5757"></a>
## 设置超参数中的一些问题
![image.png](https://cdn.nlark.com/yuque/0/2022/png/28450460/1652533274938-f1c680b7-ecd6-4455-a2df-d421ef34ec54.png#clientId=u530da8d5-d7fc-4&from=paste&height=563&id=u11958f63&originHeight=985&originWidth=2300&originalType=binary&ratio=1&rotation=0&showTitle=false&size=413168&status=done&style=none&taskId=uf0683c0e-25c3-4bae-ba89-bccc62551df&title=&width=1314.2857142857142)
<a name="63bb9bc1"></a>
### idea #1 找到表现在训练数据中特别好的超参数。
过拟合常见原因主要是学习过度和样本特征不均衡。
<a name="64ab46b7"></a>
### idea #2 将数据分为测试集和训练集然后再选择最好的超参数。
并不能说明在新数据中能达到很好的水平。
<a name="a9add9c6"></a>
### idea #4 数据分为测试集，验证集，训练集
训练之后在验证集中评估，调整完毕后再用测试集。<br />验证集和测试集需要隔离。
<a name="95c01146"></a>
## 交叉验证
小数据中常用。<br />将数据分为k份小数据和一份测试集<br />进行k轮，依次选出一份当验证集。
<a name="1cc9bd5b"></a>
# KNN的局限性
0. 比较图片不适合用L1距离这种向量化的距离函数。 <br />1.L2距离对图像差异感知不明显<br />2.维度灾难<br />数据需要很密集<br />3.测试时间长，对需求不相符。


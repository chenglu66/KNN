# KNN
基于KNN的约会网站分类效果提高
基本流程：
获取数据（注意数据格式）-清洗数据（判断是否有缺失值缺失值以均值代替（利用sklearn框架））-数据归一化（防止在计算距离时，某一特征占比重过大）
实施算法：通过获得样本中的最小值和间距把输入变成相同的格式的数据。
![image](https://github.com/chenglu66/KNN/blob/master/classfy0.png)
![image](https://github.com/chenglu66/KNN/blob/master/classfy1.png)
![image](https://github.com/chenglu66/KNN/blob/master/classfy3.png)
1.计算该点与训练数据中的每个点的距离，排序并取前k个，然后统计前k个中出现次数最多的类别作为最终的类别，这种多数表决的情况，相当于经验风险最小。

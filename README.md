# KNN
基于KNN的约会网站分类效果提高
基本流程：
获取数据（注意数据格式）-清洗数据（判断是否有缺失值缺失值以均值代替（利用sklearn框架））-数据归一化（防止在计算距离时，某一特征占比重过大）
实施算法：通过获得样本中的最小值和间距把输入变成相同的格式的数据。
1.计算该点与训练数据中的每个点的距离，排序并取前k个，然后统计前k个中出现次数最多的类别作为最终的类别，这种多数表决的情况，相当于经验风险最小。
数据分布如下：
from numpy import *
import matplotlib
import matplotlib.pyplot as plt
from matplotlib.patches import Rectangle


n = 1000 #number of points to create
xcord = zeros((n))
ycord = zeros((n))
markers =[]
colors =[]
fw = open('testSet.txt','w')
for i in range(n):
    [r0,r1] = random.standard_normal(2)
    myClass = random.uniform(0,1)
    if (myClass <= 0.16):
        fFlyer = random.uniform(22000, 60000)
        tats = 3 + 1.6*r1
        markers.append(20)
        colors.append(2.1)
        classLabel = 1 #'didntLike'
        #print ("%d, %f, class1") % (fFlyer, tats)
    elif ((myClass > 0.16) and (myClass <= 0.33)):
        fFlyer = 6000*r0 + 70000
        tats = 10 + 3*r1 + 2*r0
        markers.append(20)
        colors.append(1.1)
        classLabel = 1 #'didntLike'
        #print ("%d, %f, class1") % (fFlyer, tats)
    elif ((myClass > 0.33) and (myClass <= 0.66)):
        fFlyer = 5000*r0 + 10000
        tats = 3 + 2.8*r1
        markers.append(30)
        colors.append(1.1)
        classLabel = 2 #'smallDoses'
        #print ("%d, %f, class2") % (fFlyer, tats)
    else:
        fFlyer = 10000*r0 + 35000
        tats = 10 + 2.0*r1
        markers.append(50)
        colors.append(0.1)
        classLabel = 3 #'largeDoses'
        print(fFlyer)
        #print ("%d, %f, class3") % (fFlyer, tats)
    if (tats < 0): tats =0
    if (fFlyer < 0): fFlyer =0
    xcord[i] = fFlyer; ycord[i]=tats
    fw.write("%d\t%f\t%f\t%d\n" % (fFlyer, tats, random.uniform(0.0, 1.7), classLabel))

fw.close()
fig = plt.figure()
ax = fig.add_subplot(111)
ax.scatter(xcord,ycord, c=colors, s=markers)
type1 = ax.scatter([-10], [-10], s=20, c='red')
type2 = ax.scatter([-10], [-15], s=30, c='green')
type3 = ax.scatter([-10], [-20], s=50, c='blue')
ax.legend([type1, type2, type3], ["Class 1", "Class 2", "Class 3"], loc=2)
#ax.axis([-5000,100000,-2,25])
plt.xlabel('Frequent Flyier Miles Earned Per Year')
plt.ylabel('Percentage of Body Covered By Tatoos')
plt.show()



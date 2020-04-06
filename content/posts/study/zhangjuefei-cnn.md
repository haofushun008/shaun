---
title: '深入理解神经网络---从逻辑回归到CNN'
date: 2020-04-01
tags: [CNN]
toc: true
---

*人民邮电出版社-张觉非著*

<!--more-->

#### 一、逻辑回归

##### 1.1 作为一个神经元的逻辑回归（线性模型）

- **仿射函数**：**a** = **b**(偏置) + **∑wi\*xi**（权重&特征相乘求和）
- **逻辑回归**：**Logistics=1/（1+exp(-a)）**	

**【注】逻辑回归是**对仿射函数的值施加**Logistic**函数（也称Sigmoid函数）---即激活函数

​    “神经元的基本结构都是仿射函数加激活函数”

##### **1.2 基础向量几何**

- **超平面：**直线是2维空间的超平面，平面是三维空间的超平面（**w**是超平面的法向量）

##### **1.3 逻辑回归的能力和局限性**

- 局限性：逻辑回归属于线性模型原因在于仿射函数，它选择了一个方向，忽略了其他方向的信息。
- **神经网络的思想：**要想获得超越线性的分界能力，必须将多个神经元连成网络，允许他们合作形成复杂分界面

##### **1.4 小结**

- 逻辑回归模型是一种线性模型，在神经元的语境下，它是一个神经元。逻辑回归模型的分类能力的源泉在于它的**权值向量**。
- 仿射函数值提取出来数据沿该方向的差异，递增的激活函数随仿射函数变化，根据权值向量方向上的差异对不同样本产生不同输出，他可以解释为概率。确定了概率阈值后，逻辑回归模型的分界面就是一个以权值为法向量的超平面。将空间划分为两个区域，不同区域的样本划分为不同类别。
- 逻辑回归乃至线性模型的局限也在于此：只能提取一个方向上的信息，垂直于权值向量方向的信息丢失，只有将神经元连成网络得以克服局限。

#### **二、模型评价与损失函数**

##### **2.1 训练集与测试集**

##### **2.2 分类模型的评价**

 **2.2.1 混淆矩阵**

**2.2.2 正确率**

- **accuracy =** (00+11)/(00+01+10+11)

**2.2.3 查准率precision**

**2.2.4 查全率（召回率recall**

- **真阳率：TPR =**  11/(10+11)
- **假阳率：FPR =** 10/(10+00)

**2.2.5 ROC曲线**

**FPR为横轴，TPR为纵轴**

##### **2.3 损失函数（loss function）**

- 最常用的是**交叉熵（cross entropy）损失**

**2.3.1 L-l散度与交叉熵**

- **自信息量：**概率倒数取对数
- **信息熵：H(p)概念来自热力学，又叫做平均自信息**
- **后验概率：收到y的条件下，发送为x的概率**
- **先验概率：发送x的概率**
- **似然概率：发送x的条件下，收到y的概率**

#### **三、梯度下降法**

- **一阶泰勒展开**

##### **3.1 多元函数的微分**

- **微分刻画函数的局部线性近似，即用仿射函数近似原函数。仿射函数图像是个超平面，线性近似就是在局部用超平面近似原函数的图像。这个近似若要成立，原函数必须满足在该点可微**

**3.1.1 梯度**

- 梯度即求偏导

**3.1.2 方向导数**

**3.1.3 偏导数**

**3.1.4 局部极小点**

**3.1.5 驻点**

##### **3.2 梯度下降法**

- **为了寻求函数的全局最小点，令梯度为0求驻点**

 **3.2.1 反梯度场**

- **反梯度场即梯度下降的方向**

- **局部极小点的梯度是零向量（稳定静止点）（吸引子）**
- **局部极大点（不稳定静止点）（排斥子）**

**3.2.2 梯度下降法（GD）**

**(Gradient descent)**

- <u>梯度下降法是一种简单的数值积分算法</u>，因为梯度只包含函数的局部线性近似信息，在距离x较远的地方，函数的形状会较大地偏离近似超平面。

##### **3.3 梯度下降法的改进**

- 学习率调度：动态改变步长
- 冲量法

##### 3.4 小结

- 梯度包含了多元函数的局部一阶近似信息。根据梯度可以得到函数沿自变量空间中任意方向的变化率。函数在某点的梯度决定了函数在该点的切平面的法向量。当自变量为2维时，可以直观从函数图像中看出，梯度指向的方向是该点切平面的上坡方向，函数沿梯度方向具有最大的，正的方向导数。梯度的反方向是该点切平面的下坡方向，函数沿梯度反方向具有最小、负的方向导数。梯度的反方向是函数值下降最快的方向，在每一次迭代中，沿着当前点的梯度反方向运动一个距离，这就是梯度下降法。


- **缺点** ：仿射函数是一次函数，没有二次及以上项，其图像是’平直‘的—直线、平面、超平面。线性近似是函数在局部的最粗糙近似，当变量远离当前点，基于当前点梯度的线性近似有可能与原函数大相径庭，所以梯度下降法是一种缺乏远见法贪心算法。如果可以用更高次的函数---如二阶函数---在局部拟合原函数，则可以得到对原函数的更精确近似，以及关于函数局部形态的更丰富信息。

#### 四、超越梯度下降

##### 4.1 矩阵

**4.1.1 矩阵基础**

**4.1.2 矩阵的逆**

**4.1.3 特征值与特征向量**

**4.1.4 对称矩阵的谱分解**

**4.1.5 奇异值分解**

**4.1.6 二次型**

##### 4.2 多元函数的局部二阶特性

- 函数的局部一阶特性由梯度描述，梯度决定法向量，法向量决定切平面。切平面所能包含的信息无非是向何方向倾斜，倾斜程度如何，这些信息就是函数个方向的方向导数。如果切平面不倾斜，即梯度为0向量，这样的点为驻点，驻点向各个方向的方向导数都为0，但仅根据一阶信息无法判断驻点的类型，若要进一步刻画函数的局部形态，就要需要二次函数对原函数进行局部近似。函数的局部二次近似信息包含在赫森矩阵之中。

**4.2.1 赫森矩阵H(x)**

**4.2.2 二阶泰勒展开**

**4.2.3 驻点的类型**

- 赫森矩阵正定—>局部极小值
- 赫森矩阵负定—>局部极大值
- 赫森矩阵不定—>鞍点

##### 4.3基于二阶特性的优化

**4.3.1 牛顿法**

- 牛顿法（Nettoon method）在某点对函数进行二阶泰勒展开，求函数的局部近似二次函数的驻点，以该驻点作为迭代的下一点。

##### 4.3.2 共轭方向法

- 共轭方向法的思想是在n维自变量空间中找到一组方向，依次沿着这些方向寻找函数的最小点。沿某一方向的最小点并非全局最小点，但是这组方向具有一个性质：沿其中某一方向运动时可以保持函数值沿之前的方向最小。当搜索过程进行到第n个方向，最终将找到全局最小值。这组方向必须关于赫森矩阵共轭。

##### 4.4 小结

- 多元函数的局部二阶特性—赫森矩阵以及二阶泰勒展开。二阶泰勒展开是函数的局部的二次近似。二次函数的图像是抛物面—或椭圆抛物面。二次函数的形状比平面更复杂，能够更精确地近似函数的局部形状。

#### 五、正则化

- 在机器学习建模实践中，模型自由度、偏置-方差权衡、过拟合与欠拟合以及正则化是很是重要的概念。正则化是控制自由度的一个重要手段。自由度控制模型在高偏置-低方差和低偏置-高方差两个极端之间进行权衡。

#### 六、神经网络

- 神经元对输入向量施加仿射函数和激活函数，它的输出只能沿着权值向量的方向变化，所以神经元只能形成垂直于权值向量的超平面分界面。逻辑回归模型就是一个神经元。
- 将多个神经元连接成网络能产生非线性分界能力，这种能力来自神经元之间的合作和非线性的激活函数。

##### 6.1 合作的神经元

- 逻辑回归的权值向量和偏置是w和b,它先对输入向量x施加**仿射函数**:a=(**w**转置)***x**+**b**，再施加logistics激活函数，因为logistics函数单调递增，所以逻辑回归其实根据仿射函数值a的大小来预测类别。仿射函数的等值面是垂直于权值向量**w**的超平面。

- 一个神经元不同的权值向量输出：

<div align=center><img src="https://pic.thedoctor.top/pic/20200330cnn.jpg"  width="70%" height="70%"></div> 
- 把3个神经元神经元输出相加：


<div align=center><img src="https://pic.thedoctor.top/pic/20200330cnn1.jpg" width="40%" height="40%"></div>
> 三个逻辑回归模型的权值向量分别指向不同的方向，每个逻辑回归模型沿它的权值向量的方向抬高函数值，沿相反的方向压低函数值。将三个模型的值相加就得到图中复杂的图像。logistics激活函数将输出压缩在(0,1)区间。输出沿着权值向量的方向扬起趋近于1，沿相反的方向趋近于0.我们可以将扬起的一端称为激活端，将压低的一端称为抑制端。每一个逻辑回归模型的抑制端趋近于0，参与加和时不影响另一个模型沿该方向扬起，这就允许多个逻辑回归模型各管一方，各司其职，形成合作。如果去掉logistics函数，各个模型的两端可以到无穷，两个模型之间很可能会相互抵消。

##### 6.2 多层全连接神经网络

- 简单的多层全连接神经网络

<div align=center><img src="https://pic.thedoctor.top/pic/202003302010cnn4.jpg" width="70%" height="70%"></div>
> 多层全连接神经网络又称为多层感知机，因为网络中层与层之间是全连接的。激活函数也不限于logistics函数，多层全连接神经网络结构非常灵活，但他执行的无非是一个映射。

##### 6.3 激活函数

- 在神经网络中，神经网络对仿射函数的输出施加的单调函数称为激活函数。逻辑回归模型作为神经元，激活函数对于形成非线性分界面功不可没呀！

**6.3.1 Linear**

------

f(x) = x ;导数=1，相当于没有加激活函数

**6.3.2 Logistics**

-  $$f(x) = \frac{1}{1+e^{-{\alpha}x}}$$ 

- logistics函数在正无穷趋于1，负无穷趋于0，图形整体呈现S型，故这条曲线又称为sigmoid曲线


<div align=center><img src="https://pic.thedoctor.top/pic/20200330cnn5.jpg" width="50%" height="50%"></div>
**6.3.4 ReLU**

- 线性整流单元ReLU（rectified linear unit）是深度学习常用的激活函数，在原点不可导；ReLU非常简单，其实就是max(x,0)。当自变量大于0时，ReLU的导数为1；当自变量小于0时，导数为0.

- 相比于Logistics和Tanh,ReUL只在腹侧饱和，在正侧可抬至无穷。Logistics和Tanh在两侧饱和区域的导数接近于0，这会导致神经元难以训练。ReLU在正侧不存在饱和，一定程度上缓解了这个问题。但是当自变量为负时，ReLU的导数为0，一旦ReUL的输入为负，则神经元无法得到训练

 **6.3.5 PReLU**

- $$f(x) = ax ,x<0 $$  
- $$f(x) =  x  ,x>0$$

> 当a = 0时，PReLU就是ReLU。当a = 0.01时，PReUl就是Leaky ReLU

##### 6.4 多分类与SoftMax

- 单个神经元只能预测二分类，而神经网络的输出层可以有任意多神经元，可以用来预测多个类别的分类。为了能把多个神经元的输出当做多分类的概率，须要求他们在（0,1）区间内，且和为1。为了达到这个要求，可以对多个输出施加SoftMax函数。

#### 七、反向传播

- 反向传播算法就是计算**损失函数**对神经网络权值和偏置的偏导数的算法，有了偏导数也就有了梯度

##### 7.1 映射

映射是函数的推广，**函数**的输出是标量。即实数，而**映射**的输入和输出量都是向量。函数可接受多个输入，只有一个输出。单个神经元（如逻辑回归）就是函数。映射接受多个输入并产生多个输出，神经网络执行的计算就是映射。
**7.1.1 仿射映射**

- 函数是映射的特例，因为标量是一维向量。
- **仿射映射**(affine map)是线性映射加上一个常向量**b**
  - $f(x) = Ax+b$	
  - x为输入，如果b不是0向量，则仿射映射不保持零向量。**仿射映射**可以看做由若干个**仿射函数**组成。

**7.1.2 雅可比矩阵**

- 若映射**f**在x可导，A 是**f**在x的雅可比矩阵，简称“雅克比”。
- **映射是函数的推广，雅克比是梯度的推广**

**7.1.3 链式法则**

- 函数在某点沿某方向的方向导数是函数在该点的梯度向该方向的投影。

##### 7.2 反向传播

**7.2.1 网络的符号表示**

**7.2.2 原理**

- 用训练样本做输入向量，逐层计算直到计算出神经网络的输出，此过程称为前向传播。用网络输出和训练标签计算损失值L，在训练样本和标签给定的情况下，**损失值**可视作全体权值和偏置的函数。用**梯度下降法**调整神经网络的权值和偏置以降低损失，这就是神经网络的训练。
- 前一层的仿射值偏导数用后一层的仿射值偏导数计算，此为“反向”。**对于每一个训练样本，前向传播计算所有中间值直到网路输出，之后向后传播仿射值的偏导数，进而计算所有权值和偏置的偏导数，这就是反向传播**。
- 前一层的神经元的仿射值偏导数等于后一层全部仿射值偏导数的加权求和，再乘以激活函数的导数。可以将仿射值偏导数看作分配到每个神经元的局部误差，每个神经元利用自己的局部误差调整权值和偏置。局部误差从网络后部向网络前部反向传播，这是一个误差分配的过程。

##### 7.3 相关问题

**7.3.1 计算量**

- Logistics和Tanh的导数在已知函数值的情况下很容易计算，免去了指数和除法运算，这可以大大节省计算量。ReUL的优势很明显，计算它的导数仍然只需要判断输入的符号。

**7.3.2 梯度消失**

- 当神经元的仿射值绝对值较大时，损失值对它的权值和偏置的导数极小，称为梯度消失。这时，神经元的训练将极为缓慢。
- ReUL是单向饱和的，它在正侧的导数横为1，避免了梯度消失问题。但在仿射值为负时，本轮的迭代中它将得不到训练。

**7.3.3 正则化**

**7.3.4 权值初始化**

- 一般用正态分布或方差较小的正态分布来初始化权值和偏置。

**7.3.5 提前停止**

- 如果损失值或评价指标达到预期或长时间没有改善，则停止训练。

##### 7.4 小结

> 本章描述的反向传播对于**非多层全连接**的神经网络**不再使用**，本章描述的反向传播只是计算图自动求导的一个特例。积算图自动求导是更通用的反向传播。

#### 八、计算图

##### 8.1 计算图模型

**8.1.1 简介**

计算图是一种有向无环图(DAG)。计算图用节点表示变量，用有向边表示计算。有向边的节点称为子节点，源节点称为父节点，计算图定义如何用父节点计算子节点间，同一个计算可以用不同的计算图描述。节点可以是标量，也可以是向量，矩阵或者张量。

**8.1.2 多层全连接神经网络的计算图**

<div align=center><img src="https://pic.thedoctor.top/pic/20200401cnn7.jpg" width="70%" height="70%"></div>
**8.1.3 其他神经网络的计算图**

- 非全连接

##### 8.2 自动求导

- 核心： 保存结果节点对计算路径上各个节点的雅克比，并用它们计算结果节点对更上游的节点的雅克比。中间节点的雅克比就是上一章中仿射值偏导数的推广，是被“反向传播”的对象。**计算图自动求导是广义的反向传播。**

##### 8.5 小结

> 大部分神经网络都可以用计算图表示。以计算图中的一个节点为最终结果，可以计算它对其他节点的雅克比，这就是计算图的自动求导。自动求导可以看做广义的“反向传播”。大部分人工神经网络都可以用计算图描述，神经网络的训练就是计算图上的自动求导再加梯度下降。

#### 九、卷积神经网络

##### 9.1 卷积

- CNN以卷积而得名。卷积是一种针对函数的运算，它用两个函数得到一个新函数。

**9.1.1 一元函数的卷积**

**9.1.2 多元函数的卷积**

- 离散or连续

**9.1.3 滤波器**

离散卷积中的f称作卷积核或滤波器。离散卷积操作称为滤波。

##### 9.2 卷积神经网络的组件

**9.2.1 卷积层**

- 图像数据通常是三维的：除了图像的宽和高，还有通道，如RGB彩色图像包含三个通道，对应红，绿，蓝三种颜色。黑白图像只有一个通道。

- <div align=center><img src="https://pic.thedoctor.top/pic/20200401IMG_20200401_160857.jpg" width="70%" height="70%"></div>

 **9.2.2 激活层**

- ReUL及其变体最为常用。

**9.2.3 池化层**

- 最大值池化：选择池化窗口中的最大值。
- 平均值池化：计算池化窗口中的所有值得平均值。

**9.2.4 全连接层**

- 全连接层一般位于CNN的最后，**卷积层可以视为特征提取器，多卷积层相当于进行多轮的特征提取，在此过程中压缩图像尺寸，增加通道数，逐渐提高特征的抽象程度，最终形成特征向量，提交给全连接层**

**9.2.5 跳跃连接**

- 跳跃连接又称短路连接，被跨过的层被称为短路层，短路层的学习是目标与输入的差—”残差”，这称为残差学习。神经网络的参数一般被初始化为接近于0的值。**残差学习可以提高训练效率**

##### 9.3 深度学习的正则化方法

- 高自由度的模型容易陷入过拟合，需要对其实施正则化来限制其自由度。

**9.3.1 权值衰减**

**9.3.2 Dropout**

- Dropout技术很简单：在梯度下降的每一次迭代时，将每个神经元按概率**p**从网络中去掉。若某神经元在一次迭代时命中概率为**p**，则该神经元不参与前向传播和反向传播及梯度下降。概率**p**称为Dropout率。
- **提高Dropout率起到的作用是降低方差、防止过拟合。**

**9.3.3 权值初始化**

**9.3.5 数据增强**

- 再强大的正则化方法也弥补不了数据的缺失，深度神经网络是机器学习领域迄今为止最复杂、自由度最高的模型，它需要大量的训练样本。数据增强就是用已有的样本生成新的样本。对于图像来说就是剪裁、平移，镜像反转等。

##### 9.4 小结

> 可以认为CNN的卷积层是可训练的滤波器，他们在训练中习得某种有用的功能，称为特征提取器。全连接层相当于以网络前部提取的特征向量为输入的全连接神经网络。

#### 十、经典CNN

**10.1 LeNet-5**

- 早期的手写数字识别

##### **10.2 AlexNet**

##### **10.3 VGGNet**

##### **10.4 GoogLeNet**

##### 10.5 小结

> 目前来说深度学习是一门学科还是有些站不住脚，因为还没有可以解释深度学习本质的理论框架，这也是深度学习被诟病为炼金术的原因。





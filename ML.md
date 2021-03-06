## 机器学习
### 机器学习的三个前提
- 潜藏模式
- 不知道如何定义规则
- 有某种形式的数据以供学习
### 机器学习应用
### 机器学习与数据挖掘的关系
- 数据分析技术
- 数据管理技术
### 统计学习技巧分类
- 贝叶斯学习
- 核方法
### 统计学习三要素
- 模型
  - 决策函数模型
  - 参数空间
  - 条件概率的集合
  - 参数空间
- 策略
  - 损失函数
  - 风险损失
  - 0-1损失函数
  - 平方损失函数
  - 绝对损失函数
  - 对数损失函数
  - 损失函数的期望 R_exp 积分形式
  - 经验风险 R_emp 期望风险的离散形式
  - 经验损失最小化
  - 结构风险最小化 经验+正则项
- 算法
  - 有解析解直接计算
  - 解析解不存在 数值方法
### 模型评估与模型选择
- 类似经验风险计算 只不过节点换成测试节点
### 正则化与交叉验证
- 正则化
  - 即结构风险最小化
  - 正则项 有一次项和平方项
- 交叉验证
  - 简单交叉验证
  - k折交叉验证
  - 留一交叉验证
### 泛化能力
- 泛化误差 期望风险
- 泛化误差上界
  - 样本容量增加，泛化误差趋于0；假设空间容量越大，泛化误差越大
### 生成模型很判别模型
- 生成方法
  - 朴素贝叶斯法
  - 隐马尔可夫模型
- 判别方法
  - k近邻、感知机、决策树、逻辑回归、支持向量机
### 分类问题
- 二分问题评价指标
  - TP 正类点被分对
  - FN 正类点被分错
  - FP 负类点被分错
  - TN 负类点被分对
### 回归问题
- 股票预测
- 气温预测
### 无监督问题
- 聚类K-means
- 混合高斯
### 半监督
---------------------------------



## 感知机
### 感知机学习策略
- 距离
- 损失函数 y与wx+b的内积
- 随机梯度下降法
### 感知机算法的收敛性
### 感知机算法的对偶形式
- 引入对偶变量alpha_i=ni*eta(步长) ni 为点 xi被分错的次数
- 优点
  - 可优先计算 xi*xj
  - 可以提高计算速度
  - 方便引入核函数，从而解决非线性分类问题
### 感知机存在的问题
- 无法解决异或问题（XOR） 解决***多层感知机***

### Sigmoid激活函数
### Tanh激活函数
### ReLU激活函数

-----------------------------------------
## 密度估计
### 直方图密度估计
- rho_i=ni/N*delta
- delta是一个光滑参数 delta越大越光滑
### 密度估计建模
- rho（x）V=P K=NP ***=>*** rho(x)=K/NV
### K近邻算法
- rho（Ci/x）=Ki/K


--------------------------------------------

## 朴素贝叶斯
### 后验概率最大化
- 贝叶斯分类决策是选择后验概率最大的类别
- 等价于期望风险最小化原则


-----------------------
## 逻辑回归
### 逻辑回归问题
- 分类方法通过决策函数给出样本的预测
- 概率判别模型给出样本属于各类的后验概率
- 根据后验概率最大化原则进行决策
- 给出的概率是在[0,1]上的任意实数，类似回归
### Sigmoid函数
### 二项逻辑回归
- 由条件概率P(Y|X)表示的概率判别模型表示分类决策
- 将概率形式化为逻辑分布
- X取实数，Y取值1,0
- 事情发生与不发生之比是P/（1-P）
- 对数机率logit(p)=log[p/(1-p)]
- 基于对数机率的回归就是就是逻辑斯蒂回归
### 判别模型的极大似然估计

-----------------------------
## 熵
### 熵的概念和最大熵原理
- 最大熵原理:学习概率模型时，在所有可能的概率模型中，熵最大的模型是最好的，即在满足约束条件的模型集合中选取熵最大的模型.
- 熵：H(p)=-sigmaP(x)*logP(x)
- 且0 <= H(p) <= logX
### 最大熵原理
- 随机变量 五个取值 {A,B,C,D,E}
- 当 p(A)=p(B)=p(C)=p(S)=p(E) 熵最大
- 当有先验（约束）p(A)+p(B)=3/10
- ***=>*** p(A)=p(B)=3/20
- ***=>*** p(C)=p(S)=p(E)=7/30
------------------------------
## 支持向量机
### 支持向量机 svm
- 二分类模型：间隔最大的分类器
- 回归问题：基于不敏感损失函数的回归问题
- 间隔最大：区别与感知机分类和最小二成
- 核技巧，支持向量机本质是非线性分类
- 支持向量的学习策略：间隔最大化
- 最大间隔策略可形式化为凸二次规划
- 等价于正则化的合页损失函数最小化
- 支持向量机的学习算法是求解凸二次规划的最有化法
### 支持向量分类机
- 线性可分
  - 硬间隔最大化
- 近似线性可分
  - 软间隔最大化
- 线性不可分
  - 核技巧+软间隔最大化
### 核方法
- 输入空间 欧氏空间（连续特征）离散集合（离散特征）
- 特征空间 希尔伯特空间 ***=>***内积空间
- 核函数 将输入空间映射到特征空间后得到特征向量的内积
- 核函数可以实现非线性支持向量机，等价于隐式地在高维特征空间学习支持向量机，这类技巧称为核技巧
- 核方法是一种普遍的机器学习方法
### 线性可分支持向量机
- 求解约束凸优化问题
- min_wb 1/2  ||w||^2
- yi(w*xi+b)-1 >=0
- 使用梯度下法求解
### 线性可分支持向量机对偶算法
- 对原始问题 引入拉格朗日对偶算子alpha
- 定义拉格朗日函数
- 对wb求偏导等于0 用alpha代表w，b 带回原式得对偶形式
- 对alpha求最大
- 超平面可写为 sigam[alpha_i*yi(X\*Xi)]+b'=0 为原式对偶形式

### 一般线性分类问题的软间隔最大化
- 原始问题 
  - min 1/2||w||^2+Csigma(xi_i)
  - yi(w*xi+b)>=1-xi_i
  - xi>=0
- w唯一存在，b不唯一
### 软间隔最大化对偶问题
- 对偶形式同硬间隔最大化
- 存在 0 <=alpha_j <= C 因为 C-alpha-mu=0 同时我们为了求b 所以要让 xi_j=0 由kkt条件知 至于mu_j>0才必有xi_j=0 所以我们要找的alpha必须要（0，c）之间

### 回归问题
- 原始问题
  - min 1/2||w||^2+ C/l*sigma_(i=1,l)(xi_i+xi_i')
  - (w*xi)+b-yi<=epsilon'+xi_i
  - yi-(w*xi)-b<=epsilon'+xi_i'
- 对偶问题
  - 引入对偶算子alpha,alpha',mu,mu'
  - 同理计算b时选取 alpha (0，C/l)
### 回归超平面的平坦性
- 寻找超平面中斜率模长最小的一个


## 无监督
### K均值算法
- k聚类的簇中心初始化问题
  - 一般选择：任选k个已知观测为初始簇中心 因为如果选取其他点会导致可能这个中心没有分到任何点而是k簇变少
- k聚类的分配
  - 软聚类  
  - 硬聚类
- 应用
  - 初始化高斯混合模型的参数
  - 图像分割和图像压缩
### 高斯混合模型
- 对多个高斯进行线性叠加
- 引入离散随即变量Zk
  - Zk 属于 {0,1}
  - sigma_(k)Zk=1 即 Z1～Zk 只有一个为一
  - 
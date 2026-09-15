# INMT5518 Supply Chain Analytics
# 专项深度复习与模拟题库：Part 7 & Part 8 (终极冲刺版)

> **适用范围**：期中闭卷考试（Midterm Quiz - Week 8）  
> **考试形式**：闭卷（Closed Book）、单项选择题（MCQ, Single Correct Answer）、答错不倒扣分（No Negative Marks）  
> **核心覆盖**：  
> - **Part 7**：预测性分析（Predictive Analytics）、分类模型与决策树架构、一元/多元回归模型构建、Excel 回归报表深度解读（$R^2$、Significance F、P-value）、时间序列趋势外推预测、需求预测信任困境、牛鞭效应（Bullwhip Effect）成因与对策（Week 7 课件与实操图像精析）  
> - **Part 8**：期中全课程公式总库、统计阈值速查、考前 15 大必背混淆陷阱、终极应试 Checklist

---

# MODULE 1: 预测性分析、分类模型与决策树 (Predictive Analytics & Classification)

## 1.1 预测性分析的本质与方法分类 (Foundations of Predictive Analytics)

### 1. 核心定义与运作逻辑
- **核心提问**：*What will happen? What are the trends and forecasts?*（未来会发生什么？未来的趋势和预测值是什么？）
- **核心机制**：
  $$\mathbf{\text{Historical Data (历史数据)} \longrightarrow \text{Identify Patterns (挖掘潜在规律)} \longrightarrow \text{Mathematical Model (数学模型)} \longrightarrow \text{Predict Future (预测未来)}}$$
  1. 从历史积累的业务数据中提取客观规律或变动趋势；
  2. 将该规律抽象表征为一个数学算法模型（Mathematical model）；
  3. 输入新数据或未来时间参数，利用该模型计算输出对未来未知事件的预测结果。

### 2. 定量预测 vs. 定性预测 (Quantitative vs. Qualitative Approaches) ⭐
| 预测路径 | 依赖资源 (Input Sources) | 核心方法与技术 (Methodologies) | 适用场景与优缺点 (Pros & Cons) |
| :--- | :--- | :--- | :--- |
| **Quantitative<br>(定量预测)** | **历史客观业务数据（Historical Data）**、结构化交易日志、时间序列。 | 统计学模型、**回归分析（Regression Analysis）**、时间序列分解、机器学习算法。 | **客观、可量化、可自动计算**；但高度依赖历史数据的连续性与完整性，无法感知突发黑天鹅事件。 |
| **Qualitative<br>(定性预测)** | **专家主观经验与直觉（Expert Opinions）**、市场调研报告（Market Research）、客户定性反馈（Customer Feedback）。 | 德尔菲法（Delphi Method）、销售人员意见汇集法、焦点小组访谈（Focus Groups）。 | 适用于**缺乏历史数据的新产品上市（New product launch）**或政策剧变期；主观偏见较大，难以量化误差。 |

---

## 1.2 分类模型与供应链应用 (Classification Models in SCM) ⭐⭐

### 1. 什么是分类（Classification）？
- **定义**：基于已有训练数据（Existing data），为目标对象构建一套类别映射规则（Creating a set of classes for data）。
- **两大分支**：
  - **Binary Classification（二分类）**：目标输出仅有两种离散结果（例如：垃圾邮件 vs. 正常邮件；贷款审批通过 vs. 拒绝）。
  - **Multiclass Classification（多分类）**：目标输出包含三种或更多离散类别（例如：供应商评级分为 A 级、B 级、C 级、D 级；客户流失风险分为高、中、低）。
- **供应链经典决策场景**：
  $$\mathbf{\text{“Whether to sign a contract with this supplier?”}\ (\text{是否与该供应商签署合同？}) \implies \text{Yes / No (二分类决策)}}$$
  - 输入：供应商的历史交付准时率、退货瑕疵率、财务稳健评分；
  - 输出：由分类模型自动给出决策辅助推荐（Sign / Do Not Sign）。

### 2. 常用分类算法家族 (Classification Algorithms)
1. **Decision Trees（决策树）**：结构直观易懂，业务解释性极佳。
2. **Random Forest（随机森林）**：集成多棵独立决策树进行投票，准确率高且防止过拟合。
3. **Voting Classifiers（投票分类器）**：融合逻辑回归、SVM、决策树等多个异构模型的预测结果，以多数票决定最终归类。
4. **Neural Networks & Deep Learning（神经网络与深度学习）**：适合处理非线性、高维度的海量复杂图像、语音或文本分类。

---

## 1.3 决策树结构与专业术语 (Decision Tree Architecture & Terminology) ⭐⭐⭐

> 决策树（Decision Tree）本质是一个**倒置生长的树状图（Upside-down tree shaped diagram）**，通过一系列嵌套的布尔测试（Boolean tests: Yes/No）或多值条件判断实现分类。

```
                    [ Root Node (根节点: 起始总体特征) ]
                                    │
                        ┌───────────┴───────────┐
                   (Splitting / Branching: 分裂分支)
                        ▼                       ▼
            [ Parent / Child Node ]     [ Parent / Child Node ]
                        │                       │
                  ┌─────┴─────┐                 │
                  ▼           ▼                 ▼
             [Leaf Node] [Leaf Node]       [ Leaf / Terminal Node (叶节点: 最终分类结果) ]
```

### 1. 决策树五大核心构件术语 (Core Terms)
| 构件英文术语 (Term) | 中文名称 | 定义与结构功能 (Definition & Structural Role) |
| :--- | :---: | :--- |
| **Root Node** | **根节点** | 决策树的**唯一起始顶端节点（Starting point）**；包含未经划分的全部训练数据集。 |
| **Splitting / Branching** | **分裂 / 分支** | 依据某个最优特征属性（Attribute），将一个节点划分成两个或更多子节点的过程。 |
| **Parent Node** | **父节点** | 拥有下游子节点的上游节点（The node that is divided）。 |
| **Child Node** | **子节点** | 由上游父节点分裂产生的派生下游节点（Sub-node of a specific node）。 |
| **Leaf / Terminal Node** | **叶节点 / 终端节点** | **没有进一步分裂的终点节点（Nodes without a split）**；代表最终输出的类别决策（Class / Decision）。 |

### 2. 决策树如何构建？(How to Build a Decision Tree?)
1. **选择最佳属性（Select an attribute $A$）**：通过计算**不纯度（Impurity，如基尼系数 Gini）**或**信息增益（Information Gain）**，挑选能将样本区分得最干净的特征。
2. **创建分区（Create a partition）**：依据特征属性取值划分新分支。
3. **递归迭代（Recursive iteration）**：若子节点样本已完全纯净分类（Perfectly classified），则终止并生成叶节点；否则在子节点上重复上述步骤。
- *课件实践提示*：特征属性少时可手工绘制树状图；现实复杂业务中应使用自动化机器学习算法建树。

---

# MODULE 2: 回归分析建模与 Excel 输出深度解读 (Regression Modeling & Output Interpretation)

## 2.1 回归分析的核心概念 (Regression Analysis Foundations)

### 1. 分类 vs. 回归的区别 (Classification vs. Regression in SCM) ⭐
- **Classification（分类）**：预测一个**离散的类别或离散决策（Discrete Category / Decision）**（例如：“签合同还是不签合同？”、“会不会逾期违约？”）。
- **Regression（回归）**：预测一个**连续的未知未来数值（Continuous Numeric Value）**（例如：“下个月的销售量是多少？”、“给定比特币过去一年的走势，下周的价格是多少？”）。

### 2. 变量属性定义
- **Dependent Variable ($Y$) / Target / Response（因变量 / 目标变量）**：我们试图进行预测、解释或建模的被动指标（如产品售价 Product Price、月度需求量 Demand）。
- **Independent Variable ($X$) / Predictor / Explanatory（自变量 / 预测变量）**：用于解释或驱动因变量变动的主动特征（如生产成本 Production Cost、仓储成本 Inventory Cost、从业年限 Experience）。

### 3. 一元线性回归模型 (Simple Linear Regression)
$$\mathbf{y = a \cdot x + b + \varepsilon}$$
- $y$ = 因变量（Dependent variable）
- $x$ = 自变量（Independent variable）
- $a$ = **斜率（Slope）**：自变量每增加 1 个单位时，因变量的平均变动量。
- $b$ = **截距（Intercept）**：当自变量 $x = 0$ 时，因变量的基准理论值。
- $\varepsilon$ = 随机误差项（Random error term）。
- **回归线（Regression Line）**：利用最小二乘法（Ordinary Least Squares - OLS）在散点中寻找最佳拟合直线（Best fit straight line），使得所有观测点到直线的垂直距离平方和最小。

---

## 2.2 多元线性回归 (Multiple Linear Regression) ⭐⭐

当影响目标变量的驱动因素不止一个时，采用多元线性回归：
$$\mathbf{Y = a_1 x_1 + a_2 x_2 + \dots + a_n x_n + b}$$
- $x_1, x_2, \dots, x_n$：多个互相独立的自变量；
- $a_1, a_2, \dots, a_n$：各自变量对应的**偏回归系数（Coefficients）**；
- $b$：常数截距项（Constant intercept term）。

### 课件经典案例精析：产品定价模型 (Product Price Model - Image p1.png) ⭐⭐⭐
> **业务背景**：某制造企业试图基于历史产品数据，确定“生产成本（Production Cost）”和“库存成本（Inventory Cost）”对“产品售价（Product Price）”的影响权重，从而为新研发产品的销售定价提供科学预测依据。

```
[ Regression Statistics ]
  Multiple R:           0.8806
  R Square:             0.7754  ◄── 解释了 77.54% 的变异
  Adjusted R Square:    0.7255
  Standard Error:       9111.87
  Observations:         12
----------------------------------------------------------------------
[ ANOVA ]
              df            SS            MS            F     Significance F
  Regression   2   2580225389    1290112694        15.54        0.001205  ◄── 模型整体极显著 (<0.05)
  Residual     9    747235522      83026169
  Total       11   3327460911
----------------------------------------------------------------------
[ Coefficients ]
                  Coefficients   Standard Error    t Stat      P-value
  Intercept         16387.30        5489.12         2.98       0.01917  ◄── 基础固定成本 (p<0.05)
  Production Cost       2.03           0.64         3.17       0.01297  ◄── 生产成本每增$1，售价增$2.03 (p<0.05)
  Inventory Cost        3.58           0.97         3.69       0.00533  ◄── 库存成本每增$1，售价增$3.58 (p<0.05)
```

#### 1. 提取回归方程 (Formulating the Equation)
$$\mathbf{\text{Product Price} = 16387.30 + 2.03 \times (\text{Production Cost}) + 3.58 \times (\text{Inventory Cost})}$$
- **截距（$16387.30$）的物理意义**：企业保有的基础固定分摊成本（Fixed costs）。
- **比较影响权重（Which has a higher impact?）**：
  - 生产成本系数为 $2.03$，意味着生产成本每上升 \$1，产品定价上涨 \$2.03；
  - 库存成本系数为 $3.58$，意味着库存成本每上升 \$1，产品定价上涨 \$3.58；
  - **结论**：**库存成本（Inventory Cost）对产品定价的影响力度更高（Higher impact per dollar）！**

---

## 2.3 Excel 回归报表核心指标判定“三步法” (Interpreting Excel Output: The 3 Rules) ⭐⭐⭐

在考试中面对 Excel 回归数据表，请严格按照以下三步进行质量检验：

| 评估层级 | 核心指标 (Metric) | 官方合格判断标准 (Official Rule from Slides) | 统计学本质含义 (Statistical Meaning) |
| :---: | :--- | :--- | :--- |
| **Step 1<br>模型解释力** | **R Square ($R^2$)<br>(判定系数)** | **可接受范围：$0.50 \sim 0.99$<br>($50\% \sim 99\%$)** ⭐ | 因变量 $Y$ 的总方差变异中，**能够被自变量 $X$ 解释的比例**。取值范围为 $[0, 1]$。$R^2 = 0.775$ 表示模型解释了 77.54% 的变异。 |
| **Step 2<br>模型整体显著性** | **Significance F<br>(ANOVA 输出)** | **必须严格小于 $0.05$<br>($\text{Significance } F < 0.05$)** ⭐ | 类似回归模型的总 P 值。若 $\text{Significance } F \ge 0.05$，说明模型整体毫无统计学价值，必须**立即中止分析（Cannot proceed）**！ |
| **Step 3<br>各变量独立显著性** | **P-value<br>(Coefficients 输出)** | **每个自变量系数的 P 值必须 $< 0.05$** ⭐ | 检验该特定自变量是否对 $Y$ 具有显著的边际影响。若某变量 $P \ge 0.05$，说明该特征与因变量之间没有统计显著关联，应考虑从模型中剔除。 |

---

## 2.4 时间序列趋势外推预测实战 (Time-Series Linear Trendline: Airline Case p2.png) ⭐⭐

> **背景**：课件经典航空客运量（Airline Passengers）预测模型。横轴为连续月份索引（Month Index $x = 1, 2, \dots$），纵轴为客运人数（Passengers $y$）。

```
[ Trendline Equation ] : y = 2.6572 x + 87.653
[ R-Squared ]          : R² = 0.8536
```
- **参数解析**：
  - **斜率（Slope $a$）** $= 2.6572$：客运量平均每月线性净增长约 2.66 名乘客；
  - **截距（Intercept $b$）** $= 87.653$：基准理论起点；
  - **$R^2 = 0.8536$**：线性时间趋势解释了 85.36% 的乘客人数变异，拟合度非常优异。
- **未来预测计算（Forecasting Future Periods）**：
  - 已知历史数据覆盖前 12 年（共 $12 \times 12 = 144$ 个月）；
  - 预测第 13 年 1 月（Year 13, Jan，对应时间索引 $x = 145$）：
    $$\mathbf{y_{\text{Jan, Yr 13}} = (2.657184 \times 145) + 87.65278 = 385.2917 + 87.6528 = 472.94\text{ 乘客}}$$
  - 预测第 13 年 2 月（Year 13, Feb，对应时间索引 $x = 146$）：
    $$\mathbf{y_{\text{Feb, Yr 13}} = (2.657184 \times 146) + 87.65278 = 475.60\text{ 乘客}}$$
- **趋势（Trend） vs. 季节性（Seasonality）**：
  - 散点图中的直线反映了长期的**上升趋势（Upward Trend）**；
  - 实际观测值围绕趋势线每年呈现固定的周期性波峰（夏秋高峰）和波谷（冬春低谷），展现了典型的**季节性波动（Seasonality）**。

---

# MODULE 3: 需求预测困境与牛鞭效应 (Forecasting Challenges & Bullwhip Effect)

## 3.1 需求预测的终极瓶颈：信息与信任壁垒 (The Trust Problem) ⭐⭐

> **PPT 核心警句 (Slide 63)**：
> *"**Biggest Problem is TRUST.** Who should optimise the supply chain and why? How the benefits will be shared? Is it fair? Who is taking advantage?"*

- **信息私藏（Information Holding）**：供应链上下游企业彼此缺乏信任，担心真实成本和需求数据透露给对方后，会在商务谈判中被压价或被竞争对手利用。
- **缺乏共赢机制**：如果仅有一方投入 IT 系统优化全链，而节省的利润全部被另一方独吞，各方将退回局部利益最大化，导致全局效率崩塌。

---

## 3.2 牛鞭效应全面剖析 (The Bullwhip Effect Deep Dive) ⭐⭐⭐

### 1. 什么是牛鞭效应？
- **定义**：在供应链中，**下游终端消费者的微小需求波动，沿着供应链向上游传递时，被逐级放大的现象（Demand variability amplifies upstream）**。
- **形象比喻**：手腕轻轻一抖（末端微小波动），鞭子末梢就会甩出巨大的狂暴摆幅（上游海量过剩）。

```
[ Consumer Demand ] ──► 终端轻微波动: 仅增长 5%
        │
        ▼
   [ Retailer ]     ──► 零售商担忧缺货，放大补货: 采购增长 10%
        │
        ▼
  [ Wholesaler ]    ──► 批发商增加缓冲，进一步放大: 采购增长 15%
        │
        ▼
 [ Manufacturer ]   ──► 制造商过度反应，激进排产: 增产 20% ~ 25% (加班扩产)
        │
        ▼
   [ Supplier ]     ──► 原材料供应商接收严重失真信号: 盲目超量开采与备料 ──► 灾难性积压与浪费!
```

---

### 2. 牛鞭效应的五大根本诱因 (Five Root Causes) ⭐⭐⭐
| # | 诱因名称 (Root Cause) | 运作机制与放大成因 (Operational Mechanism) |
| :-: | :--- | :--- |
| **1** | **Demand Forecasting<br>(需求预测失真与多重更新)** | 供应链每个节点都只根据直接下游的“订单量”而不是“实际终端消费量”独立进行预测，并在每次预测上叠加自身的安全缓冲，导致失真层层堆叠。 |
| **2** | **Long Lead Times<br>(长交货提前期)** | 提前期越长，面临的不可控风险和预测不确定性越大，采购方被迫设立更高的安全库存进行防御。 |
| **3** | **Batch Ordering<br>(大批量周期性订购)** | 采购方为了凑整车运费（FCL）或降低订货成本，采取每月甚至每季度大批量订货一次。这向上游传递的是断断续续的“脉冲式”假需求信号。 |
| **4** | **Price Fluctuations<br>(价格波动与促销诱发)** | 厂家频繁开展短期降价促销或批量折扣，促使下游零售商开展**提前压货购买（Forward Buying）**；促销期需求暴增，促销结束后需求暴跌，人为制造剧烈波动。 |
| **5** | **Inflated Orders / Shortage Gaming<br>(虚假订货 / 短缺博弈)** | 当某商品面临供应紧缺配额时，零售商预期厂家会按比例打折供货，于是故意报出虚高数倍的订单；一旦产能恢复，零售商迅速取消订单，上游瞬间陷入库存灭顶之灾。 |

---

### 3. 根除与缓解牛鞭效应的八大战略措施 (Strategies to Eliminate the Bullwhip Effect) ⭐⭐⭐

> 考试极常以单选题形式考查“以下哪项策略能够有效缓解牛鞭效应”。

```
[ 信息透明度 ] ──► 实时信息共享 (ERP/EDI/POS直连) + 协同规划预测补货 (CPFR)
[ 运营与流程 ] ──► 供应商管理库存 (VMI) + 小批量高频配送 + 压缩提前期 (Lead Time)
[ 商务与战略 ] ──► 天天低价 (EDLP) 稳定价格 + AI高级预测 + 建立长期战略合作关系
```

1. **Real-Time Information Sharing（实时信息共享）**：
   - 借助 ERP、EDI 或云平台，在全链条无缝共享终端销售时点数据（**POS data - Point of Sale**）、实时库存深度和原始预测。
2. **Collaborative Planning, Forecasting, and Replenishment - CPFR（协同规划、预测与补货）**：
   - 供需双方共同组建联合团队，在全链条范围内制定统一的业务计划、联合需求预测与补货时间表。
3. **Vendor Managed Inventory - VMI（供应商管理库存）** ⭐：
   - **核心机制**：打破传统“下游下单、上游发货”模式，转由**供应商直接监控下游零售商的实际库存消耗速度**，自主决定补货时机与补货量，彻底消除虚假中间订单信号。
4. **Smaller, Frequent Orders（小批量、高频次补货）**：
   - 打破大批量集中订购习惯，采用集装箱混装或循环取货（Milk-run），将断续的脉冲需求平滑化。
5. **Stable Pricing Strategies / Everyday Low Price - EDLP（稳定价格策略 / 天天低价）**：
   - 效仿沃尔玛（Wal-Mart），摒弃大起大落的游击式促销，消除价格畸变诱发的囤货行为。
6. **Lead Time Reduction（缩短全流程提前期）**：
   - 优化物流干线、推行快速换模（SMED）、实施跨国属地化采购，消除时间敞口风险。
7. **Advanced Analytics & AI Forecasting（融合外部变量的 AI 高级预测）**：
   - 将天气、宏观经济指数、节假日、社交媒体情绪等外部大数据纳入预测模型。
8. **Long-Term Relationships with Suppliers and Distributors（建立长期战略信任伙伴关系）**：
   - 建立公正合理的利益分享机制，从制度上化解信息私藏的信任死结。

---

# MODULE 4: 终极考前速记秘籍与全真公式总库 (Part 8: Comprehensive Cheat Sheet)

## 4.1 全课程必背数学公式全景表 (Master Formula Sheet) ⭐⭐⭐

| 模块类别 | 公式名称 | 标准数学表达式 | 各变量含义与单位注解 |
| :--- | :--- | :--- | :--- |
| **库存模型** | **EOQ<br>(经济订货批量)** | $$\mathbf{EOQ = \sqrt{\frac{2DS}{H}}}$$ | $D$: 年需求量；$S$: 单次订货准备成本；$H$: 单件年持有成本。**在 EOQ 点处，年持有成本 $\equiv$ 年订货成本！** |
| **库存模型** | **TAC<br>(总年度库存成本)** | $$\mathbf{TAC = \text{Purchase} + \left(SS + \frac{Q}{2}\right)H + \left(\frac{D}{Q}\right)S}$$ | $\text{平均库存} = SS + Q/2$；$SS$: 安全库存；$Q$: 订货批量。 |
| **库存模型** | **Safety Stock<br>(简易安全库存)** | $$\mathbf{SS = \text{Max Lead Usage} - \text{Avg Lead Usage}}$$ | 到货前最大消耗量减去到货前平均消耗量。**唯一根本原因：VARIATION**。 |
| **绩效 KPI** | **POM<br>(完美订单满足率)** | $$\mathbf{POM = (\%Comp) \times (\%On\text{-}time) \times (\%Dmg\text{-}free) \times (\%Inv)}$$ | 四项合格概率**相乘**（完全、准时、无损、发票无误），绝非加权平均！ |
| **绩效 KPI** | **CCC<br>(现金周转周期)** | $$\mathbf{CCC = DIO + DSO - DPO}$$ | 存货天数 $+$ 应收账款天数 $-$ 应付账款天数。**天数越短越好，可为负数！** |
| **绩效 KPI** | **IT<br>(库存周转率)** | $$\mathbf{IT = \frac{Cost\ of\ Goods\ Sold\ (COGS)}{Value\ of\ Average\ Inventory}}$$ | 全期销售成本除以平均库存资产价值。**数值越大越好！** (YouRace: 12 $\rightarrow$ 15). |
| **绩效 KPI** | **Freight Unit Cost<br>(单件运费成本)** | $$\mathbf{\text{Unit Cost} = \frac{Total\ Freight\ Costs}{Total\ Units\ Shipped}}$$ | 总运输费用除以总发运件数。数值越低效率越高。 |
| **预测模型** | **一元线性回归** | $$\mathbf{y = a \cdot x + b + \varepsilon}$$ | $y$: 因变量；$x$: 自变量；$a$: 斜率（Slope）；$b$: 截距（Intercept）；$\varepsilon$: 误差项。 |
| **预测模型** | **多元线性回归** | $$\mathbf{Y = a_1 x_1 + a_2 x_2 + \dots + a_n x_n + b}$$ | $x_i$: 多个独立自变量；$a_i$: 各自变量边际贡献偏回归系数。 |

---

## 4.2 核心统计参数判定阈值速查表 (Statistical Decision Thresholds) ⭐⭐⭐

| 检验项目 (Test / Metric) | 理想优质区间 (Good) | 可接受区间 (Acceptable) | 违规报警与修正动作 (Action if Violated) |
| :--- | :---: | :---: | :--- |
| **偏度 (Skewness)** | $[-1.0, +1.0]$ | $[-2.0, +2.0]$ | 超出 $\pm 2.0 \implies$ 严重偏态，**严禁使用 t-Test/ANOVA，强制使用非参数检验**。 |
| **峰度 (Kurtosis)** | $[-2.0, +2.0]$ | $[-3.0, +3.0]$ | 超出 $\pm 3.0 \implies$ 严重厚尾，**强制转为非参数检验**。 |
| **相关系数 ($|r|$)** | $\pm 0.50 \sim \pm 1.00$ (强相关) | $\pm 0.30 \sim \pm 0.49$ (中度相关) | $< 0.29 \implies$ 判定为微弱相关（Small / Low correlation）。 |
| **回归判定系数 ($R^2$)** | **$0.50 \sim 0.99$ ($50\% \sim 99\%$)** | $0.50 \sim 0.99$ | $< 0.50 \implies$ 解释力不足；等于 $1.00 \implies$ 极度怀疑数据造假或过拟合。 |
| **假设检验 P-value** | $< 0.05$ | $< 0.05$ | $\ge 0.05 \implies$ **Fail to Reject $H_0$（证据不足，无法推翻原假设）**。 |
| **回归 Significance F** | $< 0.05$ | $< 0.05$ | $\ge 0.05 \implies$ 模型整体不显著，**必须立即中止分析（Cannot proceed）**。 |

---

## 4.3 考前必背 15 大高频混淆陷阱 (Top 15 Exam Traps)

1. **假设检验原假设符号**：$H_0$ 必须包含等号（$=, \le, \ge$）；$H_1$ 严禁包含等号（只能是 $\ne, >, <$）。选项中如果 $H_1$ 出现了 $\le$ 或 $\ge$ 直接排除！
2. **P 值的反向逻辑**：P 值越大越不能拒绝；P 值越小（$< 0.05$）越有理由拒绝 $H_0$。
3. **不能说“证实了 $H_0$”**：当 $P \ge 0.05$ 时，严谨学术表述是 **“Fail to Reject $H_0$”**（缺乏充足证据推翻它），而不是“证明了 $H_0$ 为真”。
4. **两组用 t-Test，三组及以上用 ANOVA**：看到比较 3 条产线、3 种疗法、4 组学院 $\rightarrow$ 正态时选 **ANOVA Single Factor**，非正态选 **Kruskal-Wallis**。
5. **配对样本的识别**：同一批工人“培训前 vs. 培训后” $\rightarrow$ 正态选 **Paired t-Test**，非正态选 **Wilcoxon signed rank**。
6. **Apache Spark 为何快 100 倍**：考点唯一答案：**利用计算机内存（RAM）**，而不是磁盘（Local memory）。
7. **KNIME 的独门绝技**：从海量多元数据源（Numerous sources）**集成导入**到单一源中。
8. **Python vs. R 的取舍**：从零开发系统软件（Building from scratch）选 **Python**；纯统计学术分析才考虑 R。
9. **安全库存的本质**：唯一根本原因是 **VARIATION（波动）**，没有波动安全库存为 0。
10. **推迟差异化（Postponement）案例**：智能电视（软件多国语言推迟）、沙发（通用木框架底座推迟包面料）。
11. **零部件通用性案例**：欧盟强制所有数码设备搭载 **USB Type-C** 接口。
12. **制造业服务化（Servitisation）经典案例**：**Rolls-Royce（劳斯莱斯）** 约 50% 营收来源于飞行小时维护服务。
13. **气泡图 vs. 雷达图**：展示“成本、价值、风险”3 个数值维度 $\rightarrow$ **气泡图（Bubble graph）**；评估供应商多维度综合能力且面积越大越好 $\rightarrow$ **雷达图（Radar chart）**。
14. **牛鞭效应的解决神技**：**VMI（供应商管理库存）**让供应商直接看 POS 消耗；**CPFR** 协同预测补货；**EDLP** 天天低价消除促销脉冲。
15. **供应链分析的终极目标（Goldratt）**：在同时降低库存（Inventory）和运营费用（Operating expense）的前提下，提高有效产出（Throughput）！

---

# MODULE 5: 高仿真期中全英文模拟题库 (20 题全解析)

> 本题库覆盖 Part 7 预测性分析、回归分析报表解读、决策树、牛鞭效应成因与消除策略，以及 Part 8 综合公式体系。每题均为全英文单选题（Single Correct Answer）。

---

### Question 1
In an automotive components supply chain, managers want to deploy an automated analytics model to answer the operational question: *"Given historical supplier quality scores, credit ratings, and on-time delivery percentages, should we sign a long-term procurement contract with this new vendor (Yes or No)?"* What class of model does this represent?  
A. Multiple Linear Regression Model  
B. Time-Series Trendline Extrapolation Model  
C. Binary Classification Model  
D. Continuous Monte Carlo Simulation Model

### Question 2
Which of the following correct describes the structural anatomy of a standard Decision Tree model?  
A. It begins at terminal leaf nodes and iteratively merges into a single root node.  
B. It is an upside-down tree diagram that starts at a single root node and branches downwards through decision nodes until reaching terminal leaf nodes.  
C. It strictly requires all tests to be continuous logarithmic equations.  
D. It produces only linear slope parameters ($y = ax + b$).

### Question 3
In a decision tree algorithm, what term is used to describe a terminal node that does not undergo any further splitting and represents the final class outcome?  
A. Root node  
B. Parent node  
C. Leaf node  
D. Branching node

### Question 4
An analyst is evaluating the feasibility of forecasting product demand using either qualitative or quantitative approaches. Under which of the following circumstances is a Qualitative forecasting approach most appropriate?  
A. Forecasting next month's sales of a mature laundry detergent with 10 years of steady weekly scanner data  
B. Estimating initial consumer adoption of an entirely novel, cutting-edge consumer wearable technology where zero historical sales data exists  
C. Computing seasonal trendline regressions across 144 months of commercial airline flight passenger records  
D. Calculating daily economic order quantities for standardized industrial machine screws

### Question 5
A simple linear regression equation is estimated as: $\text{Demand} = 15.4 \times (\text{Advertising Spend in \$k}) + 120$. What is the precise statistical interpretation of the slope coefficient $15.4$?  
A. When advertising spend is zero, total demand is expected to be $15.4$ units.  
B. For every additional \$1,000 increase in advertising spend, product demand is expected to increase by an average of $15.4$ units.  
C. The model explains exactly $15.4\%$ of the total variation in consumer demand.  
D. The probability that advertising has no effect on demand is exactly $15.4\%$.

### Question 6
An analyst generates a Multiple Linear Regression model in Microsoft Excel to predict "Product Price" based on "Production Cost" and "Inventory Cost." The Excel regression output reports the following statistics:  
- Multiple R: $0.8806$  
- R Square: $0.7754$  
- Adjusted R Square: $0.7255$  
- Significance F: $0.0012$  
How should the analyst interpret the model's overall explanatory power and statistical validity?  
A. The model should be rejected because R Square is below $0.99$.  
B. The model is statistically significant (Significance F $< 0.05$) and explains approximately $77.54\%$ of the total variation in Product Price, falling well within the acceptable $0.50$ to $0.99$ R-squared band.  
C. The model is invalid because Multiple R is larger than Adjusted R Square.  
D. The model proves that Production Cost has zero causal impact on product pricing.

### Question 7
In the same Multiple Regression model from Question 6, the estimated coefficients table displays the following values:  
- Intercept: $16,387.30$ ($P = 0.019$)  
- Production Cost: $2.03$ ($P = 0.013$)  
- Inventory Cost: $3.58$ ($P = 0.005$)  
Which variable exerts a higher marginal dollar-for-dollar pricing impact on Product Price, and why?  
A. Production Cost, because its P-value is larger than that of Inventory Cost.  
B. The Intercept, because $16,387.30$ is the largest absolute number.  
C. Inventory Cost, because its coefficient ($3.58$) indicates that every \$1 increase in inventory holding expense drives a \$3.58 increase in price, compared to \$2.03 for production cost.  
D. Neither, because multiple regression coefficients cannot be compared.

### Question 8
In an airline passenger time-series regression study, historical monthly passenger volume follows the linear trendline equation:  
$$y = 2.6572 x + 87.653$$  
where $x$ represents the continuous month index ($x = 1, 2, \dots$). If the historical dataset ends at month 144 (December of Year 12), what is the forecasted passenger volume for February of Year 13 (corresponding to month index $x = 146$)?  
A. $472.94$ passengers  
B. $475.60$ passengers  
C. $387.95$ passengers  
D. $585.07$ passengers

### Question 9
In the lecture slides, what is explicitly identified as the "BIGGEST PROBLEM" obstructing collaborative demand forecasting and end-to-end supply chain integration?  
A. Inadequate computer RAM memory in local laptops  
B. The complete absence of quantitative regression software  
C. Trust issues regarding who should optimize the chain, how financial benefits will be shared, and fear of exploitation  
D. Government laws strictly prohibiting the sharing of retail barcode information

### Question 10
Which of the following scenarios best demonstrates the manifestation of the "Bullwhip Effect" in a supply chain?  
A. A delivery truck breaks down on a highway, causing all subsequent regional deliveries to be delayed by exactly 24 hours.  
B. A slight $5\%$ uptick in consumer retail purchases causes the retailer to order $10\%$ more, the wholesaler to order $15\%$ more, and the manufacturer to ramp up production by $25\%$.  
C. A company purchases its upstream supplier to achieve $100\%$ vertical integration.  
D. A manufacturer transitions all product packaging to standardized USB Type-C receptacles.

### Question 11
Which of the following is recognized as one of the major operational root causes of the Bullwhip Effect?  
A. Maintaining single-piece continuous flow under JIT  
B. Batch ordering (ordering in large, infrequent batches to save on transport costs)  
C. Practicing Everyday Low Prices (EDLP) across all retail branches  
D. Sharing real-time Point of Sale (POS) scanner data with component suppliers

### Question 12
How does "Price Fluctuation" (such as periodic trade promotions, clearance sales, and volume discounts) directly aggravate the Bullwhip Effect?  
A. It forces retailers to adopt non-parametric Kruskal-Wallis testing.  
B. It encourages buyers to engage in "forward buying" (stockpiling excessive goods during the discount window), artificially distorting real consumption patterns.  
C. It permanently reduces the supplier's manufacturing lead time to zero.  
D. It converts all structured spreadsheet data into unstructured video feeds.

### Question 13
Under a Vendor Managed Inventory (VMI) collaborative agreement, how is replenishment authorization restructured to mitigate the Bullwhip Effect?  
A. The retailer completely ceases selling the vendor's products.  
B. The vendor monitors the retailer's actual inventory consumption levels and assumes full operational responsibility for deciding when and how much to replenish.  
C. The retailer places huge batch orders once every two years.  
D. The government assumes legal ownership of all warehouse safety stock.

### Question 14
Which supply chain strategy pioneered by Wal-Mart helps smooth out consumer demand volatility and eliminate the bullwhip spikes caused by promotional discounting?  
A. Delayed Product Differentiation  
B. Everyday Low Prices (EDLP)  
C. Third-Party Contract Manufacturing  
D. Functional Focus Manufacturing

### Question 15
A retail chain wants to implement Collaborative Planning, Forecasting, and Replenishment (CPFR). What is the fundamental operational premise of CPFR?  
A. Upstream suppliers and downstream retail partners collaboratively synchronize demand forecasts, production schedules, and inventory replenishment plans across shared digital platforms.  
B. Replacing all human truck drivers with automated rail transport.  
C. Forcing all tier-1 suppliers to absorb 100% of corporate inventory holding costs.  
D. Switching exclusively from quantitative statistical forecasting to subjective intuition.

### Question 16
An operations analyst examines an Excel regression output for a newly proposed supplier pricing model. The regression summary table reports a `Significance F` value of $0.184$. What is the correct analytical decision regarding this model?  
A. The model is highly accurate and should be deployed immediately for procurement pricing.  
B. Because Significance F is substantially greater than $0.05$, the model as a whole lacks statistical significance and the analyst must NOT proceed with it.  
C. The analyst should square the Significance F value to obtain the true R-squared.  
D. The model proves that the independent variables explain $81.6\%$ of the dependent variable.

### Question 17
A factory requires 36,000 units of an industrial valve annually ($D = 36,000$). The administrative cost to place an order is \$80 ($S = 80$), and the inventory carrying cost per valve per year is \$4 ($H = 4$). What is the Economic Order Quantity (EOQ)?  
A. 600 units  
B. 1,200 units  
C. 1,440 units  
D. 2,400 units

### Question 18
A distribution hub tracks four key order fulfilment parameters across 5,000 customer dispatches:  
- Proportion of orders shipped completely: $98\%$  
- Proportion delivered on-time: $90\%$  
- Proportion delivered damage-free: $95\%$  
- Proportion with completely accurate invoicing: $99\%$  
What is the Perfect Order Measurement (POM) for this hub?  
A. $95.50\%$  
B. $82.95\%$  
C. $89.20\%$  
D. $75.60\%$

### Question 19
A firm maintains an average accounts receivable collection period of 40 days (DSO = 40), an average inventory conversion period of 60 days (DIO = 60), and negotiates an average supplier payment term of 75 days (DPO = 75). What is the company's Cash-to-Cash Cycle Time (CCC)?  
A. 175 days  
B. 95 days  
C. 25 days  
D. $-15$ days

### Question 20
According to Goldratt's fundamental definition of SCM introduced in Part 1 and synthesized in Part 8, what constitutes "Throughput"?  
A. The total quantity of unfinished work-in-progress inventory circulating on the shop floor.  
B. The volumetric storage capacity of all central and regional distribution centers.  
C. The rate at which the entire system generates money through actual completed sales to the end customer.  
D. The gross tonnage of raw materials delivered by sea freight carriers.

---

# MODULE 6: 模拟题标准答案与中英双语深度解析 (Answer Key & Explanations)

### Question 1
- **正确答案**: **C**
- **考点出处**: Part 7 / Week 7 Slide 6, 9 & 31 / Classification in SCM
- **深度解析**:
  - **英文解析**: The problem asks to predict a discrete categorical decision: *"Should we sign a contract? (Yes or No)"*. When the outcome is categorical with exactly two possibilities (Yes/No, Pass/Fail, Spam/Not Spam), it is a **Binary Classification Model**. Regression would predict a continuous number (e.g., price or demand quantity).
  - **中文解析**: 核心题眼是输出结果为离散的是/否选择：“是否与供应商签约（Yes/No）”。这种输出变量只有两种可能互斥结果的模型是标准的**二分类模型（Binary Classification Model）**。如果预测的是具体数值（如采购金额、订货件数），才属于回归模型。故选 C。

### Question 2
- **正确答案**: **B**
- **考点出处**: Part 7 / Week 7 Slide 19 / Decision Tree Concept
- **深度解析**:
  - **英文解析**: Slide 19 explicitly defines a decision tree as: *"essentially an upside-down tree shaped diagram used to classify. It is a predictive model based on a branching series of Boolean tests... It has a root node which is the starting point... and leaf/terminal nodes without a split."*
  - **中文解析**: 课件第 19 页原文考查：决策树本质上是一个**倒置生长的树状图（Upside-down tree shaped diagram）**，以顶端的单个根节点（Root node）为起点，经过一系列测试分支逐步向下分裂，直至抵达无进一步分裂的终端叶节点（Leaf/terminal nodes）。故选 B。

### Question 3
- **正确答案**: **C**
- **考点出处**: Part 7 / Week 7 Slide 19 / Decision Tree Terminology
- **深度解析**:
  - **英文解析**: Slide 19 states: *"Nodes have sub-nodes and leaf/terminal nodes, which are the ones without a split."* A leaf or terminal node holds the final classification category or assignment.
  - **中文解析**: 术语定义考查：不再进行任何后续分裂、代表最终类别划分归属的末端节点被称为**叶节点或终端节点（Leaf / Terminal Node）**。Root node 是起始根节点；Parent node 是父节点。故选 C。

### Question 4
- **正确答案**: **B**
- **考点出处**: Part 7 / Week 7 Slide 38 / Qualitative vs. Quantitative Forecasting
- **深度解析**:
  - **英文解析**: Slide 38 highlights that Quantitative forecasting relies on historical data and statistical models. When launching an entirely novel, breakthrough product with **zero historical data**, quantitative regression is impossible. Management must rely on **Qualitative** methods (expert opinions, market research, Delphi panels).
  - **中文解析**: 定量预测依赖充足的历史客观数据。当企业推出一款全新颠覆性创新产品且**没有任何历史销售数据可供参考时**，传统的数学回归模型完全无法运算，此时必须依赖**定性预测方法（Qualitative approach）**（专家意见、焦点小组、市场调研）。故选 B。

### Question 5
- **正确答案**: **B**
- **考点出处**: Part 7 / Week 7 Slide 41 & 49 / Slope Coefficient Interpretation
- **深度解析**:
  - **英文解析**: In the linear equation $y = ax + b$, the slope $a$ represents the marginal change in the dependent variable ($y$) for each one-unit increase in the independent variable ($x$). Here, $a = 15.4$ and $x$ is in thousands of dollars (\$k). Thus, each additional \$1,000 spent on advertising yields an average expected demand increase of $15.4$ units.
  - **中文解析**: 一元线性回归中斜率系数（Slope）的统计学严谨解释：自变量 $X$ 每变动 1 个度量单位时，因变量 $Y$ 的平均边际变动量。此处自变量单位为千美元（\$k），斜率为 $15.4$，因此代表广告费每增加 \$1,000，产品需求量平均预计增长 $15.4$ 件。故选 B。

### Question 6
- **正确答案**: **B**
- **考点出处**: Part 7 / Week 7 Slide 54, 55 & Image p1.png / Excel Regression Output Rules
- **深度解析**:
  - **英文解析**: Slide 54 states that **an R-squared between 0.50 and 0.99 is acceptable**. Here, $R^2 = 0.7754$ ($77.54\%$), indicating strong fit. Slide 55 states that **Significance F must be below 0.05 to proceed**. Here, $\text{Significance } F = 0.0012 < 0.05$, confirming that the model as a whole is statistically significant and highly valid.
  - **中文解析**: 课件第 54 与 55 页回归解读核心黄金法则：
    1. $R^2$ 在 $0.50 \sim 0.99$ 之间即为合格可接受，本题 $R^2 = 0.7754$ 表现良好；
    2. Significance F 必须严格 $< 0.05$，本题为 $0.0012 < 0.05$，表明模型整体具有高度统计显著性。两项标准完全符合。故选 B。

### Question 7
- **正确答案**: **C**
- **考点出处**: Part 7 / Week 7 Slide 58 & Image p1.png / Comparing Regression Impact
- **深度解析**:
  - **英文解析**: Slide 58 poses the exact question: *"Which one has a higher impact on product price, production cost or inventory cost?"* The coefficient of Inventory Cost ($3.58$) is greater than that of Production Cost ($2.03$). Both are statistically significant ($P < 0.05$). Thus, every dollar added to inventory cost drives a greater increase in product price (\$3.58) than a dollar added to production cost (\$2.03).
  - **中文解析**: 课件第 58 页原题：“Which one has a higher impact on product price, production cost or inventory cost?”。对比回归方程中的偏回归系数：生产成本系数为 $2.03$，库存成本系数为 $3.58$，且二者 P 值均 $< 0.05$（显著）。因此，**库存成本每增加 \$1 会带来 \$3.58 的定价上涨，其边际影响力度显著高于生产成本**。故选 C。

### Question 8
- **正确答案**: **B**
- **考点出处**: Part 7 / Week 7 Slide 60 & Image p2.png / Time-Series Forecast Calculation
- **深度解析**:
  - **英文解析**: Month 144 is Dec of Year 12. Month 145 is Jan of Year 13. Month 146 corresponds to **Feb of Year 13**. Substituting $x = 146$ into the trendline equation:
    $$y = (2.657184 \times 146) + 87.65278 = 387.9488 + 87.6528 = 475.6016 \approx 475.60\text{ passengers.}$$
  - **中文解析**: 图像 p2.png 课件算例还原：历史数据截止至第 12 年 12 月（第 144 个月）。第 13 年 1 月为 $x = 145$；题目要求预测的是**第 13 年 2 月（Feb of Year 13）**，其对应的时间索引应为 $x = 146$。代入回归方程：
    $$y = (2.6572 \times 146) + 87.653 = 387.951 + 87.653 = 475.60\text{ 乘客。}$$
    故选 B。

### Question 9
- **正确答案**: **C**
- **考点出处**: Part 7 / Week 7 Slide 62 & 63 / The Trust Issue
- **深度解析**:
  - **英文解析**: Slide 63 explicitly states in bold title font: *"Biggest Problem is **TRUST**: Who should optimise the supply chain and why? How the benefits will be shared? Is it fair? Who is taking advantage?"* Mistrust drives information withholding between supply chain partners.
  - **中文解析**: 课件第 63 页加粗标题原话考查：阻碍供应链协同预测的最核心障碍是**信任（TRUST）问题**——到底谁来优化供应链？收益如何公平分配？是否有人在占便宜？缺乏信任直接导致企业间信息私藏。故选 C。

### Question 10
- **正确答案**: **B**
- **考点出处**: Part 7 / Week 7 Slide 64 & 66 / Bullwhip Effect Definition & Steps
- **深度解析**:
  - **英文解析**: Slide 66 details the exact chain reaction: A small $5\%$ consumer sales uptick triggers retailers to order $10\%$ more, wholesalers to order $15\%$ more, manufacturers to ramp production by $20–25\%$, and upstream raw material extractors to severely overproduce. This progressive demand distortion is the classic **Bullwhip Effect**.
  - **中文解析**: 课件第 66 页完整复现了牛鞭效应的四级传导机制：终端需求仅发生 5% 的微小波动，零售商按 10% 放大补货，批发商按 15% 进一步放大，制造商过度反应增产 20-25%，上游供应商严重过量开采。故选 B。

### Question 11
- **正确答案**: **B**
- **考点出处**: Part 7 / Week 7 Slide 64 / Causes of the Bullwhip Effect
- **深度解析**:
  - **英文解析**: Slide 64 explicitly lists the 5 core causes: **1. Demand forecasting, 2. Lead time, 3. Batch ordering, 4. Price fluctuations, 5. Inflated orders**. Batch ordering creates artificial pulse-like order spikes upstream.
  - **中文解析**: 课件第 64 页列明的牛鞭效应五大诱因包括：需求预测、长提前期、**批量订购（Batch ordering）**、价格波动、虚假膨胀订货。批量订购将连续平滑的需求扭曲为断续的脉冲假象。故选 B。

### Question 12
- **正确答案**: **B**
- **考点出处**: Part 7 / Week 7 Slide 64, 68 & Textbook Chapter 1 / Price Fluctuations & Forward Buying
- **深度解析**:
  - **英文解析**: Erratic price promotions, wholesale rebates, and temporary discounts incentivize downstream buyers to purchase far more than their immediate demand (**forward buying**). This creates severe artificial demand spikes followed by protracted demand droughts, heavily exacerbating upstream bullwhip oscillations.
  - **中文解析**: 频繁的价格促销和批量打折会诱使下游客户开展**“提前囤货购买”（Forward buying）**，在促销期透支未来数月采购量，导致促销结束后需求断崖式下跌，人为造成剧烈波峰波谷，加剧牛鞭效应。故选 B。

### Question 13
- **正确答案**: **B**
- **考点出处**: Part 7 / Week 7 Slide 68 / Vendor Managed Inventory (VMI)
- **深度解析**:
  - **英文解析**: Slide 68 recommends: *"Vendor Managed Inventory (VMI): Let suppliers manage inventory based on actual consumption, not periodic orders."* By directly tracking actual POS inventory usage at retail shelves, suppliers eliminate the distorted order layer entirely.
  - **中文解析**: 课件第 68 页明确定义 VMI（供应商管理库存）的核心解法：“由供应商直接根据下游的**实际消耗情况（Actual consumption）**自主规划和管理库存补货，而非根据下游层层失真的周期性订单进行被动生产”。故选 B。

### Question 14
- **正确答案**: **B**
- **考点出处**: Part 7 / Week 7 Slide 64, 68 & Textbook Chapter 1 / Everyday Low Price (EDLP)
- **深度解析**:
  - **英文解析**: Wal-Mart pioneered **Everyday Low Prices (EDLP)**. By eliminating unpredictable promotional discounts and assuring constant low prices, consumer purchasing stays steady and smooth throughout the year, removing artificial demand spikes and dramatically stabilizing forecasts.
  - **中文解析**: 沃尔玛首创的**天天低价（Everyday Low Prices - EDLP）**策略通过消除无规律的特价促销，向消费者提供稳定的平价承诺，从而平滑了全年的消费需求曲线，消除了由于促销囤货带来的牛鞭震荡。故选 B。

### Question 15
- **正确答案**: **A**
- **考点出处**: Part 7 / Week 7 Slide 68 / Collaborative Planning (CPFR)
- **深度解析**:
  - **英文解析**: Slide 68 recommends: *"Collaborative Planning: Adopt frameworks like CPFR (Collaborative Planning, Forecasting, and Replenishment) to align decisions."* It establishes an institutional framework where trading partners jointly agree on a single shared forecast and synchronized replenishment schedule.
  - **中文解析**: CPFR（协同规划、预测与补货）的核心内涵是：供应链上下游合作伙伴打破信息壁垒，在统一的协同平台上共同制定商业计划、共享单一联合预测并协同执行自动补货。故选 A。

### Question 16
- **正确答案**: **B**
- **考点出处**: Part 7 / Week 7 Slide 55 / Significance F Decision Rule
- **深度解析**:
  - **英文解析**: Slide 55 states: *"Similar to p-Value in diagnostic analytics, here, in regression, Significance F needs to be below 0.05 to proceed."* If Significance F $= 0.184 \ge 0.05$, the model fails overall statistical significance; the analyst must stop and cannot use the model for forecasting.
  - **中文解析**: 课件第 55 页原话考查：“Similar to p-Value in diagnostic analytics, here, in regression, Significance F needs to be below 0.05 to proceed”。本题中 Significance F $= 0.184 > 0.05$，说明模型整体在统计上不成立，**必须立即终止分析，严禁用于实际决策（Must NOT proceed）**。故选 B。

### Question 17
- **正确答案**: **B**
- **考点出处**: Part 8 公式总库 / EOQ Calculation
- **深度解析**:
  - **英文解析**: Using the standard EOQ formula:
    $$EOQ = \sqrt{\frac{2DS}{H}} = \sqrt{\frac{2 \times 36,000 \times 80}{4}} = \sqrt{\frac{5,760,000}{4}} = \sqrt{1,440,000} = 1,200\text{ units.}$$
  - **中文解析**: 套用 EOQ 必背公式：
    $$EOQ = \sqrt{\frac{2 \times 36000 \times 80}{4}} = \sqrt{1440000} = 1,200\text{ 件。}$$
    故选 B。

### Question 18
- **正确答案**: **B**
- **考点出处**: Part 8 公式总库 / POM Calculation
- **深度解析**:
  - **英文解析**: POM is calculated by multiplying the four constituent percentages:
    $$POM = 0.98 \times 0.90 \times 0.95 \times 0.99 = 0.829521 \approx 82.95\%.$$
    (Avoid the trap of taking the arithmetic average of 95.50%!).
  - **中文解析**: 完美订单满足率（POM）必须是四项比率连乘：
    $$POM = 0.98 \times 0.90 \times 0.95 \times 0.99 = 0.829521 \approx 82.95\%。$$
    95.50% 是加权平均的典型诱骗选项，绝不能选！故选 B。

### Question 19
- **正确答案**: **C**
- **考点出处**: Part 8 公式总库 / CCC Calculation
- **深度解析**:
  - **英文解析**: The Cash-to-Cash Cycle Time is computed as:
    $$CCC = DIO + DSO - DPO = 60 + 40 - 75 = 25\text{ days.}$$
  - **中文解析**: 现金周转周期计算公式：
    $$CCC = \text{存货天数}(DIO) + \text{应收天数}(DSO) - \text{应付天数}(DPO) = 60 + 40 - 75 = 25\text{ 天。}$$
    故选 C。

### Question 20
- **正确答案**: **C**
- **考点出处**: Part 8 考点总结 / Textbook Chapter 1 / Goldratt's Throughput Definition
- **深度解析**:
  - **英文解析**: In Goldratt's theory of constraints and supply chain management: *"Throughput refers to the rate at which sales to the end customer occur."* Goods manufactured but sitting unsold in warehouses do not generate throughput; it only counts when money is realized through actual completed sales.
  - **中文解析**: 高德拉特对有效产出（Throughput）的经典权威定义：“整个供应链系统通过最终向终端客户完成实际销售而产生收益的速率”。未销售出去的库存堆在仓库里绝不能算作有效产出。故选 C。

---
*文件已自动生成并保存至本地工作空间：`INMT5518_Part7_Part8_Detailed_Review.md`*

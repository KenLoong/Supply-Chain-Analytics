# INMT5518 Supply Chain Analytics
# 专项深度复习与模拟题库：Part 5 & Part 6

> **适用范围**：期中闭卷考试（Midterm Quiz - Week 8）  
> **考试形式**：闭卷（Closed Book）、单项选择题（MCQ, Single Correct Answer）、答错不倒扣分（No Negative Marks）  
> **核心覆盖**：  
> - **Part 5**：诊断性分析（Diagnostic Analytics）、相关性系数区间、假设检验（$H_0$ 与 $H_1$ 符号规则、P值判定）、正态性检验（偏度与峰度阈值）、参数检验 vs. 非参数检验全套矩阵、单因素方差分析（ANOVA Single Factor）（Week 5 课件精析）  
> - **Part 6**：绩效监控与核心 KPI 体系（POM、CCC、IT 算法及算例）、服务链与服务水平协议（SLA）、服务化转型（Servitisation）、四次工业革命脉络、六大图表深度对比与仪表盘构建法则（Week 6 课件精析）

---

# MODULE 1: 诊断性分析与假设检验体系 (Diagnostic Analytics & Statistical Testing)

## 1.1 诊断性分析的定位与触发场景 (Role & Triggers of Diagnostic Analytics)

### 1. 核心定位与管理使命
- **核心提问**：*What caused the variances? Why did it happen?*（偏差是什么原因造成的？为什么会发生？）
- **行动路径**：
  $$\mathbf{\text{Drill into the analytics (向下钻取发现)} \longrightarrow \text{Detect patterns (识别异常模式)} \longrightarrow \text{Determine relationships (寻找因果原因)}}$$

### 2. 诊断性分析的三大触发场景 (When do we need it?) ⭐
1. **Verifying Claims（验证主张/断言）**：
   - 当业务伙伴、供应商或管理层提出某项假设或断言（例如：“男性和女性员工的薪资存在显著差异”、“某供应商经过培训后绩效显著提升”），需要通过严谨数据检验断言是否属实。
2. **Identifying Meaningful Relationships（发现有意义的业务关联）**：
   - 寻找潜在变量间的规律以支撑决策（例如：“运输延迟率是否与供应商距离强相关？”、“折扣力度与库存缺货是否相关？”）。
3. **Investigating Anomalies（调查突发数据异常）**：
   - 数据模式或趋势出现突发骤变（Sudden changes in patterns）；
   - 某些特定指标的观测值严重超出预期合理区间（Beyond expected values）。

---

## 1.2 相关性分析 (Correlation Analysis) ⭐⭐⭐

相关系数（通常指 Pearson $r$）用于度量两个连续变量之间**线性关联的方向与强度**。取值范围为 $[-1.0, +1.0]$。

```
[-1.0] ────────────── [-0.50] ──────── [-0.30] ────── [0] ────── [+0.30] ──────── [+0.50] ────────────── [+1.0]
极强/完全负相关        强负相关         中度负相关      无相关       中度正相关         强正相关        极强/完全正相关
```

### 课件标准相关性区间判定表 (Official Lecture Correlation Thresholds)
| 相关系数绝对值范围 ($|r|$) | 官方判定术语 (Official Classification) | 业务含义解释 (Business Meaning) |
| :---: | :--- | :--- |
| **接近 $\pm 1$ (Near $\pm 1$)** | **Perfect correlation（完全相关）** | 两个变量呈现近乎完美的直线对应关系；一变量增加，另一变量严格同向递增（正）或递减（负）。 |
| **$\pm 0.50$ 到 $\pm 1.00$** | **Strong / High degree correlation（高度/强相关）** | 变量间存在显著且稳健的线性关联，可作为因果挖掘或预测建模的重要前置特征。 |
| **$\pm 0.30$ 到 $\pm 0.49$** | **Medium / Moderate degree correlation（中度相关）** | 存在一定程度的伴随变动趋势，但伴随较多扰动噪音。 |
| **低于 $\pm 0.29$ (Below $\pm 0.29$)** | **Small / Low degree correlation（低度/微弱相关）** | 线性关联极弱，实际业务中通常认为两变量相互独立或关联不显著。 |

> **关键提醒**：相关性不等于因果性（Correlation does not equal Causation），但相关性分析是诊断性分析中确定潜在因果候选集的第一步。

---

## 1.3 假设检验基本原理 (Foundations of Hypothesis Testing) ⭐⭐⭐

> “A hypothesis is an idea/claim that can be tested.”（假设是一个可以被检验的想法或主张）。

### 1. 零假设 ($H_0$) vs. 备择假设 ($H_1$ 或 $H_a$) 符号严谨规则 ⭐
考试中极易出现关于 $H_0$ 与 $H_1$ 符号搭配的陷阱题，请死记以下规则：

| 假设类型 | 学术定位 (Role in Research) | 允许使用的数学符号 (Allowed Signs) | 业务语境直觉 (Intuitive Meaning) |
| :---: | :--- | :---: | :--- |
| **$H_0$<br>(Null Hypothesis)** | **零假设 / 原假设**<br>代表“无差异”、“无效果”、“现状基准”。我们试图寻找证据去**拒绝（Reject）**它！ | $\mathbf{=}\ ,\ \mathbf{\ge}\ ,\ \mathbf{\le}$<br>*(必须包含等号！)* | “新旧培训没有差异”、“男女薪资相等”、“平均工时不大于40小时”。 |
| **$H_1$ 或 $H_a$<br>(Alternative Hypothesis)** | **备择假设 / 研究假设**<br>代表研究者真正希望证明成立的**“受喜爱的研究主张（The claim that we like / pleasing）”**。 | $\mathbf{\neq}\ ,\ \mathbf{>}\ ,\ \mathbf{<}$<br>*(严禁包含等号！)* | “新培训显著提升了绩效”、“女性薪资高于男性”、“平均工时大于40小时”。 |

- **双尾检验（Two-tailed test）**：$H_0: \mu = 140,000$ vs. $H_1: \mu \neq 140,000$
- **单尾检验（One-tailed test）**：$H_0: \mu \le 140,000$ vs. $H_1: \mu > 140,000$

### 2. P 值判定法则与统计学哲学 (The P-Value Decision Rule) ⭐⭐⭐
> **PPT 核心哲学原话**：
> *"**All we can do in hypothesis testing is to reject the null hypothesis.**"*
> （在假设检验中，我们所能做的全部事情就是**拒绝零假设**；我们永远无法从数学上绝对“证实”备择假设，只能通过推翻零假设来间接支持备择假设）。

- **P 值的概率本质**：
  $$\mathbf{P\text{-value = The chance of your result being just a coincidence.}}$$
  （P 值即：**当前样本所观察到的极端差异纯粹是由于随机抽样巧合所导致的概率**）。
- **$\alpha = 0.05$（5% 显著性水平）的直观内涵**：
  - 如果 $P < 0.05$，意味着“当前结果纯属巧合的概率不到 5%” $\implies$ 证据足够充分，我们有 95% 以上的置信度推翻现状！
  - *课件原文解释*：若重复抽取 100 次独立样本，将有 95 次样本的结果支持拒绝零假设。
- **决策红线（Decision Rule）**：
  $$\boxed{\mathbf{P\text{-value} < 0.05 \implies \text{Reject } H_0\ (\text{拒绝零假设，接受备择假设 } H_1)}}$$
  $$\boxed{\mathbf{P\text{-value} \ge 0.05 \implies \text{Fail to Reject } H_0\ (\text{无法拒绝零假设，证据不足})}}$$

---

## 1.4 正态性检验：偏度与峰度 (Normality Check: Skewness & Kurtosis) ⭐⭐

在开展均值检验之前，必须验证数据是否服从**正态分布（Normal Distribution）**。若数据偏离正态，则所有基于正态分布假设的经典参数检验（如 t-Test、ANOVA）将全部失效，必须强制改用非参数检验！

```
     正偏态 (Right/Positive Skew)           正态分布 (Normal)            负偏态 (Left/Negative Skew)
           长尾在右边                         完美钟形对称                    长尾在左边
          Skewness > 0                       Skewness = 0                   Skewness < 0
```

### 1. 偏度 (Skewness) —— 度量数据分布的不对称性
- **Good（理想正态区间）**：位于 **$[-1.0, +1.0]$** 之间。
- **Acceptable（可接受正态区间）**：位于 **$[-2.0, +2.0]$** 之间。
- **超限判定**：偏度严重偏离 0（即 $|Skewness| > 2$），判定为严重偏态，**严禁使用参数检验，必须使用非参数检验**。

### 2. 峰度 (Kurtosis) —— 度量数据分布顶峰的陡峭程度与尾部厚度
- **Good（理想正态区间）**：位于 **$[-2.0, +2.0]$** 之间。
- **Acceptable（可接受正态区间）**：位于 **$[-3.0, +3.0]$** 之间。
- **超限判定**：峰度超出 $[-3.0, +3.0]$ 范围，表明存在极端厚尾或异常尖峰，**强制使用非参数检验**。

> **Excel 实操路径**：`Data` $\rightarrow$ `Data Analysis` $\rightarrow$ `Descriptive Statistics`（勾选 `Summary statistics`，输出结果即包含 Skewness 与 Kurtosis）。

---

## 1.5 参数检验 vs. 非参数检验全套矩阵 (Parametric vs. Non-Parametric Tests Matrix) ⭐⭐⭐

> **本表是 Week 5 课件最核心、期中考试必考 2-3 题的超级重点矩阵！请务必精确记忆每一种业务场景对应的参数与非参数工具名称。**

| 业务分析场景 (Analytical Scenario) | 参数检验方法 (Parametric Test)<br>*[数据服从正态分布时使用]* | 非参数检验方法 (Non-Parametric Test)<br>*[数据偏态或为序数等级数据时使用]* | 课件经典案例与变量类型 (Lecture Benchmark Example) |
| :--- | :---: | :---: | :--- |
| **1. 比较两个相关样本<br>(Comparing 2 related samples)** | **Paired t-Test<br>(配对样本 t 检验)** | **Wilcoxon signed rank test<br>(威尔科克森符号秩检验)** | 评估同一组受试对象在接受某项干预**前与后**的表现（*Performance of a group before & after training*）。 |
| **2. 比较两个独立样本与某变量<br>(Comparing 2 unrelated samples vs. a variable)** | **Two-Sample t-Test<br>(两独立样本 t 检验)** | **Mann-Whitney U-test<br>(曼-惠特尼 U 检验)** | 比较两类不相关群体在某指标上的差异，例如：**性别（男/女） vs. 工作满意度李克特量表得分（Likert Scale）**。 |
| **3. 比较三组及以上相关样本，单变量<br>(Comparing 3+ related samples with 1 variable)** | **One-Way Repeated Measures ANOVA<br>(重复测量方差分析)** | **Friedman test<br>(弗里德曼检验)** | 同一群体在三个不同职能阶段的表现，例如：**员工在公司的岗位角色 vs. 薪资等级（低、中、高）**。 |
| **4. 比较三组及以上独立样本<br>(Comparing 3+ samples with unrelated variables)** | **One-Way ANOVA<br>(单因素方差分析)** | **Kruskal-Wallis H-test<br>(克鲁斯卡尔-沃利斯 H 检验)** | 比较不同独立项目组员工的表现，例如：**被分配的不同研发项目 vs. 员工工作满意度等级**。 |
| **5. 比较不相关的分类变量<br>(Comparing unrelated categories)** | **None<br>(无对应经典参数检验)** | **Chi-square test ($\chi^2$)<br>(卡方独立性检验)** | 纯定性类别属性交叉，例如：**是否获得公司年度优秀奖励（是/否） vs. 绩效考核档次（高/低）**。 |
| **6. 比较两个独立变量的等级/秩次<br>(Comparing 2 independent ranks)** | **Pearson correlation<br>(皮尔逊积差相关系数)** | **Spearman rank-order test<br>(斯皮尔曼等级相关检验)** | 连续数值与等级序列的关系，例如：**员工实际薪资金额 vs. 工作满意度李克特评分**。 |

---

## 1.6 单因素方差分析 (ANOVA Single Factor) ⭐⭐

### 1. 为什么有了 t-Test 还需要 ANOVA？
- **t-Test 的局限**：t-Test 严格限制在**只能比较两个组（Two groups）**之间均值的差异。
- **ANOVA 的使命**：当需要比较**三组或三组以上（More than two testing groups）**的数据均值是否存在显著差异时，必须使用方差分析（Analysis of Variance - ANOVA）。
  - *为什么不能多次两两做 t-Test？*：多次两两检验会急剧放大第一类错误率（Type I error inflation）。

### 2. 为什么课件中选择“Single Factor”（单因素）？
- **“Single Factor”的定义**：指的是分析模型中**只存在一个独立分类自变量（Only ONE independent variable / factor）**，但该因子包含 3 个或更多水平（Levels/Treatments）。
- **课件三大经典用例**：
  1. *医学/心理学案例*：一组精神病患者分别接受 3 种不同的疗法（心理咨询 Counseling、药物治疗 Medication、生物反馈 Biofeedback），检验哪种疗法效果更好。
  2. *工业制造案例*：某灯泡制造商拥有 3 种不同的生产工艺流程（Process 1, 2, 3），检验哪种制造流程产出的灯泡寿命更长。
  3. *高等教育案例*：来自不同大学学院（Colleges A, B, C）的学生参加统考，检验学院之间学术表现是否存在显著优劣。

### 3. 统计假设与输出解读
- **假设构建**：
  - $H_0$: $\mu_1 = \mu_2 = \mu_3 = \dots = \mu_k$（所有组总体均值完全相等，各组表现无实质差异）
  - $H_1$: 并非所有组的均值都相等（At least one group differs，至少有一组表现不同）
- **判定核心指标**：查看 Excel ANOVA 输出表格中的 **Significance F**（等价于模型总 P 值）。
  $$\mathbf{\text{Significance } F < 0.05 \implies \text{Reject } H_0\ (\text{组间存在显著差异})}$$

---

# MODULE 2: 绩效监控、KPI、服务链与数据可视化 (Performance, KPIs & Visualisation)

## 2.1 供应链绩效监控的四大驱动价值 (Why Monitor SC Performance?)

企业之所以投入巨资建设绩效监控体系，核心在于驱动以下四大管理收益：
1. **Cost Reduction（成本削减）**：精准定位全链条中的冗余环节、瓶颈、低效作业与资源浪费。
2. **Customer Satisfaction（客户满意度提升）**：实时追踪库存货源充足率、订单交付准时率（On-time delivery）与合格交付质量。
3. **Risk Mitigation（风险化解）**：通过前置预警指标，提前识别供应商交付断裂或干线中断风险。
4. **Supplier Relationships（深化供应商战略伙伴关系）**：以客观量化数据为沟通桥梁，提升协同信任，建立长期战略共赢机制。

---

## 2.2 核心 KPI 计算与深度解析 (Core SCM Key Performance Indicators) ⭐⭐⭐

> 考试必出 1-2 道计算题！请熟练掌握公式变形与各个参数的单位。

### 1. 完美订单满足率 (Perfect Order Measurement - POM) ⭐
度量订单履约全流程零缺陷交付的最高标准指标。必须同时满足**完全交付、准时交付、无货损、发票无误**四大条件：
$$\mathbf{POM = (\% Complete) \times (\% On\text{-}time) \times (\% Damage\text{-}free) \times (\% Correctly\ invoiced)}$$
> **注意**：四个分项指标采用**乘法相乘**，而不是加权平均！如果某企业四项指标分别为 95%、95%、95%、95%，则 $POM = 0.95^4 \approx 81.45\%$。

### 2. 现金周转周期 (Cash-to-Cash Cycle Time - CCC) ⭐
衡量企业从支付原材料采购款到最终从客户手中收回现金所经历的时间跨度（天数）。
$$\mathbf{CCC = \text{Days Inventory Outstanding (DIO)} + \text{Days Sales Outstanding (DSO)} - \text{Days Payable Outstanding (DPO)}}$$
$$\mathbf{CCC = \text{存货周转天数} + \text{应收账款周转天数} - \text{应付账款周转天数}}$$
- **管理准则**：**CCC 天数越短越好（甚至可以为负数，如 Dell 和 Amazon）**，代表企业运营资本占用极少，营运资金流动性极强。

### 3. 库存周转率 (Inventory Turnover - IT) ⭐⭐⭐（高频计算题）
度量库存运营效率的核心指标，代表一年中库存被全部售出并更新换代的频次。
$$\mathbf{Inventory\ Turnover = \frac{Cost\ of\ Goods\ Sold\ (COGS)}{Value\ of\ Average\ Inventory} = \frac{\text{全期销货成本}}{\text{平均持有库存价值}}}$$
- **管理准则**：**周转率数值越高越好（The higher the ratio, the better）**，表明相同销售规模下占压的库存资金越少。
- **课件经典真题演练 (The YouRace Company Case)**：
  > *题目背景*：YouRace 公司制造赛车。2024 年，其销售汽车的总成本（COGS）为 \$3,000,000，全年中平均库存持有价值为 \$250,000。2025 年底，公司推行 JIT（准时制）以改善库存绩效。2025 年其业务扩张，销售汽车成本增至 \$4,500,000，而平均库存仅增至 \$300,000。  
  > *计算求解*：
  > - **2024 年库存周转率** $= \frac{3,000,000}{250,000} = \mathbf{12}$
  > - **2025 年库存周转率** $= \frac{4,500,000}{300,000} = \mathbf{15}$
  > - *结论*：周转率由 12 提升至 15，表明在实施 JIT 原则后，公司的库存周转效率获得了实质性飞跃！

### 4. 订货提前期与单件运费 (Lead Time & Freight Cost per Unit)
- **Lead Time（提前期）**：从客户正式发出采购订单到最终验收收货的总时间（$\text{Time of Order Placement to Receipt}$）。越短代表响应越快。
- **Freight Cost per Unit Shipped（单件发运运费）**：
  $$\mathbf{Freight\ Cost\ per\ Unit = \frac{Total\ Freight\ Costs}{Total\ Units\ Shipped} = \frac{\text{总物流运费开支}}{\text{实际发运总件数}}}$$

---

## 2.3 服务供应链、服务化与服务水平协议 (Service Chains, Servitisation & SLA) ⭐⭐

### 1. 制造供应链 vs. 服务供应链 (Supply Chains vs. Service Chains)
- 传统供应链管理教材多局限于制造与有形实体流动。现代经济已全面向**服务型经济（Service Economies）**演进。
- **服务供应链的核心特征**：生产与消费同时发生（Simultaneous production and consumption）、不可储存性（Non-storable）、更依赖人力技能与服务响应。

### 2. 制造业服务化转型 (Servitisation by Manufacturers) ⭐
- **定义**：现代制造企业不再仅仅交付冰冷的有形产品，而是围绕产品打包输出全生命周期的高附加值服务（Finance packages, Extended warranties, Remote condition monitoring, Repair services）。
- **课件顶级行业案例**：
  - **Rolls-Royce（劳斯莱斯航空发动机）**：其公司总营业收入中，有**高达约 50% 来源于航空动力服务（Power-by-the-Hour 飞行小时付费维保合同）**，而非一次性发动机硬件销售！
  - *延伸案例*：各大车企提供汽车金融分期、延保服务、重卡远程车联网监控等。

### 3. 服务水平协议 (Service Level Agreement - SLA)
- **定义**：企业与外部服务提供商签订的法律级契约，明确界定服务质量、可用性、各方权责以及未履约时的违约惩罚条款（Quality, availability, responsibilities, and penalties）。
- **两类场景的典型 SLA 考核指标对比**：
  | 业务服务领域 | 核心 SLA 考核衡量指标 (Key SLA Metrics) |
  | :--- | :--- |
  | **Call Centre / IT 运营外包** | • **Availability Time**（系统可用性时间比例，如 99.9%）；<br>• **Response Time**（电话接入/工单响应响应时长）；<br>• **Resolution Time**（故障最终修复解决时长）。 |
  | **Logistics & Transportation 物流外包** | • **Delivery Time**（承诺送达时限）；<br>• **Allowed Damage Rate**（允许货物破损残损率上限）；<br>• **Penalty for delays/damages**（延误交货与货物破损赔偿罚则）。 |

---

## 2.4 四次工业革命历史进程 (The Four Industrial Revolutions Context)

| 发展阶段 | 爆发时间与发源 | 标志性核心驱动技术 (Key Technologies) | 经济组织形态变革 (Economic Transformation) |
| :---: | :---: | :--- | :--- |
| **First (第一次)** | $\approx 1750 – 1850$<br>英国率先发起 | 蒸汽机（Steam engines）、煤炭开采、机械化纺织机、生铁冶炼、铁路运输。 | 从农业与手工作坊向**工厂机械化大生产**转轨（Handcraft $\rightarrow$ Machine production）。 |
| **Second (第二次)** | $\approx 1870 – 1914$<br>“技术革命” | 炼钢技术、**电力广泛应用（Electricity）**、石油化工、电报/电话通信、内燃机。 | 崛起现代汽车制造与大型化学工业；确立**流水线大规模制造（Mass production）**。 |
| **Third (第三次)** | $\approx 1970\text{s}$ 以后<br>“数字革命” | 计算机（Computers）、微电子芯片、现代通信网络、互联网（Internet）。 | 从机电物理系统转向**自动化与数字化信息处理（Digital automation）**。 |
| **Fourth (第四次)** | **当代 (Today)**<br>工业 4.0 | **人工智能（AI）**、高级机器人、物联网（IoT）、3D 打印增材制造、合成生物学。 | 物理世界、数字世界与生物世界的深度融合互联（Blurring physical, digital & biological）。 |

---

## 2.5 六大图表类型全景对比与选型指南 (Chart Types Comprehensive Guide) ⭐⭐⭐

> 考试极常以具体业务情境出题，要求考生挑选“最适宜的可视化图表类型”。

| 图表类型 (Chart Type) | 最适用业务场景 (Best Used For) | 核心优势 (Key Advantages) | 局限性与缺点 (Disadvantages / Pitfalls) |
| :--- | :--- | :--- | :--- |
| **Column / Bar Chart<br>(柱状图 / 条形图)** | 比较离散分类之间的独立数值大小差异（Comparing separate values）。 | 直观展现大批量数据的对比；比纯文字表格更能清晰凸显各类别间的相对高低差距。 | 难以表达随时间变化的连续微观轨迹。 |
| **Line Chart<br>(折线图 / 时间序列图)** | 展示某一指标随**时间推移（Changes over time）**的发展趋势与演变规律。 | 最直观展示时序趋势与多组时序数据的交叉走势；能极其敏锐地暴露异常突变数据点。 | 仅适合有连续逻辑顺序的横轴（如日期、月份、工步）。 |
| **Pie Chart / Donut<br>(饼图 / 环形图)** | 展示各个分类占**整体（Whole）**的百分比结构分布（Proportions of a whole）。 | 视觉上对“整体与局部”的比例切分极其直观；容易标注百分比份额。 | **分类项不能过多**（超过 5–7 项将无法辨识）；无法表达负数或时间动态演进。 |
| **Scatter Plot<br>(散点图)** | 探究与展示**两个连续数值变量之间的相关关系（Correlation）**（$X$ 轴独立变量，$Y$ 轴依变量）。 | 清晰展示正相关、负相关、线性与非线性规律；暴露离群孤立异常值（Outliers）；支持插值与外推。 | **无法对大量数据点逐一标记数据标签**；不能展示两个以上的维度变量。 |
| **Bubble Graph<br>(气泡图)** ⭐ | 同时展示**三个数值维度（Three numeric dimensions）**的数据对象（$X$ 轴、$Y$ 轴、气泡面积大小）。 | **无需绘制复杂的 3D 图表即可表达三维关系**！商业中常用于**投资方案对比（成本 Cost vs. 价值 Value vs. 风险 Risk）**。 | 气泡面积难以精准估读具体数值；圆圈重叠时极难辨认，不适合超大数据量。 |
| **Radar / Spider Chart<br>(雷达图 / 蜘蛛网图)** ⭐ | 比较不同组织、供应商或候选方案在**多个评估维度/指标（More than 2 or 3 values）**上的综合表现。 | **覆盖面积越大，代表综合价值越高**！一目了然看清某对象在多项指标上的均衡性或短板（如供应商各维度雷达评级）。 | **不能同时对比超过 2–3 个对象**，否则线条杂乱难以分辨；轴过多时可读性显著下降。 |

---

## 2.6 数据可视化原则与仪表盘架构 (Visualisation Principles & Dashboarding)

### 1. 优秀可视化的四大核心特质 (Data Visualisation Principles)
1. **Informative（信息性）**：准确无误地向决策者传达其所需的核心业务情报。
2. **Efficient（高效性）**：设计简洁凝练，杜绝歧义，让读者在数秒内看懂结论。
3. **Appealing（吸引力）**：视觉排版得体美观，能抓住管理层的注意力焦点。
4. **Interactive & Predictive（交互与预测性 - 可选高级特性）**：提供切片器和筛选器，支持动态情景模拟。

### 2. 图表 vs. 仪表盘 (Chart vs. Dashboard) ⭐
- **Chart（图表）**：展示单一特定指标的信息维度，相当于**“故事中的某一个独立章节”（A chapter of a story）**。
- **Dashboard（仪表盘）**：
  - 将多张相互关联的图表与核心 KPI 集中整合在**单块屏幕（A single screen）**上；
  - 汇聚异构数据源，**“各章节融会贯通，直观讲述一个完整的业务故事”（Chapters come together to tell a story）**；
  - **核心特性**：可定制（Customisable）、可交互（Interactive）、实时监控（Real-time）、全链整合（All-in-one place）。

---

# MODULE 3: 核心考点陷阱与速记口诀 (Exam Traps & Quick Hacks)

1. **假设检验符号禁忌**：
   - 只要看到备择假设 $H_1$ 或 $H_a$ 包含等号（$=$、$\le$、$\ge$） $\rightarrow$ **100% 错误选项，秒杀排除**！
   - 零假设 $H_0$ 必须包含等号（$=$、$\le$、$\ge$）。
2. **P 值拒绝法则记忆法**：
   - **“小概率事件发生了，推翻原假设”**：$P < 0.05 \implies$ **Reject $H_0$**。
   - $P \ge 0.05 \implies$ **Fail to Reject $H_0$**（绝不能说“证实了 $H_0$”，只能说“缺乏足够证据推翻 $H_0$”）。
3. **正态性偏度与峰度阈值速记**：
   - 偏度（Skewness）：好在 **$\pm 1$**，可接受在 **$\pm 2$**。
   - 峰度（Kurtosis）：好在 **$\pm 2$**，可接受在 **$\pm 3$**。
   - 只要题目说“偏度为 3.5”或“严重偏离正态” $\rightarrow$ **坚决选择非参数检验（Non-parametric）**！
4. **两组 vs. 多组检验选型**：
   - 正态数据比较 2 组独立样本 $\rightarrow$ **Two-sample t-Test**。
   - 正态数据比较 3 组及以上独立样本 $\rightarrow$ **One-Way ANOVA**。
   - 非正态数据比较 2 组独立样本 $\rightarrow$ **Mann-Whitney U-test**。
   - 非正态数据比较 3 组及以上独立样本 $\rightarrow$ **Kruskal-Wallis H-test**。
   - 评估培训前后（配对）且非正态 $\rightarrow$ **Wilcoxon signed rank test**。
5. **图表选型特征词秒杀**：
   - 看到“随时间变化（Over time / Trends）” $\rightarrow$ **Line chart**。
   - 看到“两个变量的相关关系（Correlation / Outliers）” $\rightarrow$ **Scatter plot**。
   - 看到“三个数值维度（3 numeric dimensions / Cost, Value, Risk）” $\rightarrow$ **Bubble graph**。
   - 看到“多属性多维度综合能力对比（Comparing performance across multiple criteria）” $\rightarrow$ **Radar / Spider chart**。
6. **KPI 计算易错点**：
   - $POM$ 必须是 4 项百分比连续相乘，**绝不是加法相加再除以 4**！
   - $CCC = DIO + DSO - DPO$（注意应付账款 DPO 前面是**减号**，因为占用供应商资金对自己的现金流是有利的）。
   - 库存周转率 $IT = COGS / \text{平均库存}$，数值越大越好。

---

# MODULE 4: 高仿真期中全英文模拟题库 (20 题全解析)

> 本题库覆盖 Week 5 诊断性分析统计学检验与 Week 6 可视化、KPI 及服务链的全部考点。每题均为全英文单选题（Single Correct Answer）。

---

### Question 1
A supply chain analyst observes that customer returns in a major distribution region suddenly spiked by 45% following a promotional campaign. The analyst begins cross-referencing return rates with transit delay records to identify the underlying root cause. According to the course framework, which category of analytics is being conducted?  
A. Descriptive Analytics  
B. Diagnostic Analytics  
C. Predictive Analytics  
D. Prescriptive Analytics

### Question 2
When evaluating the correlation between transportation expenditure and carrier delivery quality rating, an analyst obtains a correlation coefficient of $r = -0.42$. According to the official interpretation thresholds presented in Week 5 lecture slides, how is this correlation classified?  
A. Small / Low degree correlation  
B. Moderate / Medium degree correlation  
C. High degree / Strong correlation  
D. Perfect negative correlation

### Question 3
A quality control department formulates a statistical test to determine whether a newly contracted packaging supplier produces fewer defect units than the historic benchmark of 50 ppm. Which of the following represents the mathematically correct formulation for the Null Hypothesis ($H_0$) and Alternative Hypothesis ($H_1$)?  
A. $H_0: \mu < 50$ vs. $H_1: \mu \ge 50$  
B. $H_0: \mu \ge 50$ vs. $H_1: \mu < 50$  
C. $H_0: \mu \ne 50$ vs. $H_1: \mu = 50$  
D. $H_0: \mu \le 50$ vs. $H_1: \mu > 50$

### Question 4
An analyst runs an independent two-sample t-test in Excel to test whether female warehouse supervisors earn higher hourly wages than male supervisors. The resulting one-tail P-value is calculated as $0.082$. What is the correct statistical decision at the standard $\alpha = 0.05$ significance level?  
A. Reject the null hypothesis because $0.082 > 0.05$.  
B. Accept the alternative hypothesis because there is sufficient sample evidence.  
C. Fail to reject the null hypothesis because the P-value is not smaller than $0.05$.  
D. Conclude that male and female supervisors have identical salary distributions with 100% certainty.

### Question 5
In hypothesis testing, what is the fundamental conceptual meaning of a P-value?  
A. The probability that the alternative hypothesis is mathematically false.  
B. The chance of your observed sample outcome being merely a random coincidence under the null hypothesis.  
C. The percentage of missing data points detected during Excel data cleaning.  
D. The ratio of the sample mean divided by the total population variance.

### Question 6
An operations team extracts daily assembly defect rates and performs a normality test using Excel's Descriptive Statistics tool. The resulting skewness is $+2.85$, and the kurtosis is $+4.12$. How should the team proceed when comparing defect rates across two independent supplier shifts?  
A. Proceed immediately with a standard two-sample parametric t-Test assuming unequal variances.  
B. Abandon hypothesis testing because the sample variance is positive.  
C. Use the non-parametric Mann-Whitney U-test because skewness and kurtosis fall outside the acceptable normal distribution boundaries.  
D. Run a One-Way ANOVA because kurtosis is greater than 3.0.

### Question 7
A human resources manager wants to assess whether an intensive safety training course improved the performance scores of a group of warehouse forklift operators. The same operators were tested immediately before the training and re-tested one month after the training. If the test scores violate normal distribution assumptions, which statistical test should be used?  
A. Paired sample parametric t-Test  
B. Wilcoxon signed rank test  
C. Kruskal-Wallis H-test  
D. Chi-square test of independence

### Question 8
A logistics manager wishes to test whether employee job satisfaction levels (measured on a 1-to-5 ordinal Likert scale) differ between three completely unrelated shift teams (Day shift, Swing shift, Night shift). Because the dependent variable is ordinal Likert scaled data, which statistical test is most appropriate?  
A. One-Way ANOVA Single Factor  
B. Kruskal-Wallis H-test  
C. Friedman test  
D. Pearson product-moment correlation

### Question 9
A manufacturing firm operates three distinct production lines (Line 1, Line 2, Line 3). The plant manager wants to determine whether there is any significant difference in average worker productivity across all three lines. In Excel, the manager selects `Data Analysis` $\rightarrow$ `ANOVA: Single Factor`. Why is "Single Factor" selected for this analysis?  
A. Because the dataset contains only one single row of recorded observations.  
B. Because there is only one independent categorical factor being tested (Production Line), which has three levels.  
C. Because Excel is incapable of running multi-factor regressions.  
D. Because single factor ANOVA is strictly reserved for testing two groups only.

### Question 10
In the Excel ANOVA Single Factor output table from Question 9, which specific statistical output value must be examined to decide whether to reject the null hypothesis at the 5% significance level?  
A. Adjusted R Square  
B. Standard Error of the Intercept  
C. Significance F (P-value)  
D. Total Sum of Squares (SS Total)

### Question 11
A regional distribution center processes 10,000 customer orders during the month. Audit records reveal the following operational performance metrics:  
- Orders shipped complete: $96\%$  
- Orders delivered strictly on-time: $95\%$  
- Orders delivered completely damage-free: $98\%$  
- Invoices generated with correct billing details: $99\%$  
What is the Perfect Order Measurement (POM) for this distribution center?  
A. $97.00\%$  
B. $88.42\%$  
C. $92.15\%$  
D. $78.50\%$

### Question 12
A supply chain director evaluates the working capital liquidity of a manufacturing enterprise. Financial records report the following metrics:  
- Days Inventory Outstanding (DIO): 45 days  
- Days Sales Outstanding (DSO): 30 days  
- Days Payable Outstanding (DPO): 50 days  
What is the Cash-to-Cash Cycle Time (CCC)?  
A. 125 days  
B. 65 days  
C. 25 days  
D. $-5$ days

### Question 13
The YouRace Company manufactures custom competition racing vehicles. In 2024, its total Cost of Goods Sold (COGS) was \$3,000,000, and its average inventory holding was valued at \$250,000. In 2025, after implementing Just-In-Time (JIT) operational principles, its sales expanded such that COGS reached \$4,500,000, while its average inventory holding was maintained at \$300,000. What happened to the company’s Inventory Turnover (IT) ratio from 2024 to 2025?  
A. Decreased from 15 to 12, indicating worsening inventory performance  
B. Remained unchanged at 12  
C. Increased from 12 to 15, indicating enhanced inventory operational efficiency  
D. Doubled from 6 to 12

### Question 14
Which of the following service agreements is an example of "Servitisation by Manufacturers" as highlighted in Week 6 lecture materials?  
A. An iron ore mining company purchasing a cargo freighter  
B. Rolls-Royce generating approximately 50% of its corporate revenue from comprehensive maintenance and aviation power-by-the-hour services rather than pure engine sales  
C. A grocery supermarket selling generic private-label canned goods  
D. A computer retailer refusing to offer any repair warranties or financing to consumers

### Question 15
In a Third-Party Logistics (3PL) warehousing and delivery contract, which of the following metrics would typically be codified into the legal Service Level Agreement (SLA)?  
A. The client company's corporate net profit margin  
B. Maximum allowed shipping damage rate and agreed financial penalty charges for delivery delays  
C. The supplier's internal stock option pricing model  
D. The personal income tax rates of warehouse truck drivers

### Question 16
During which historical period did the Second Industrial Revolution (often termed the Technological Revolution) take place, and what were its primary driving technologies?  
A. $\approx 1750–1850$; powered by steam engines, coal mining, and mechanized textile mills  
B. $\approx 1870–1914$; characterized by steel production, electricity, petroleum, telegraph, and mass production  
C. $\approx 1970\text{s}$ onwards; characterized by microprocessors, the Internet, and digital automation  
D. Contemporary era; characterized by generative artificial intelligence and synthetic biology

### Question 17
A procurement team wants to compare four competing supplier bids across three numerical evaluation dimensions simultaneously: Project Estimated Cost ($X$-axis), Projected Supplier Value ($Y$-axis), and Operational Risk Score (represented by bubble area size). Which data visualization format is specifically designed for this purpose?  
A. Stacked Bar Chart  
B. Pie Chart  
C. Bubble Graph  
D. Line Time-Series Chart

### Question 18
An executive evaluator needs to assess the multi-criteria capability of a logistics contractor across six performance dimensions simultaneously (e.g., On-time rate, Sustainability compliance, Pricing competitiveness, Safety record, Technology adoption, and Customer communication). The evaluator wants to assess the total "area covered" by the plot to determine overall balance. Which chart is best suited?  
A. Radar Chart (Spider Chart)  
B. Scatter Plot  
C. Donut Chart  
D. Histogram

### Question 19
What is the core structural distinction between an individual "Chart" and an executive "Dashboard" as defined in the Week 6 lecture?  
A. A chart displays a single specific piece of information (a chapter of a story), whereas a dashboard is a unified collection of related charts and KPIs arranged on a single screen to narrate an entire story at a glance.  
B. Charts are strictly created in Microsoft Excel, while dashboards can only be compiled in Apache Spark.  
C. A chart is interactive and dynamic, while a dashboard is always a static paper printout.  
D. A chart contains qualitative text, whereas a dashboard is strictly prohibited from displaying KPIs.

### Question 20
A quality assurance analyst plots weekly warehouse pick-and-pack errors against the total hours of employee overtime worked. The analyst wishes to observe whether higher overtime hours drive an increase in packing mistakes, while also identifying any atypical outlier shifts. Which visualization type is most appropriate?  
A. Radar Chart  
B. Scatter Plot  
C. Pie Chart  
D. 3-Axis Stacked Bar Graph

---

# MODULE 5: 模拟题标准答案与中英双语深度解析 (Answer Key & Explanations)

### Question 1
- **正确答案**: **B**
- **考点出处**: Part 5 / Week 5 Slide 5 & 6 / When do we need Diagnostic Analytics?
- **深度解析**:
  - **英文解析**: When anomalies occur (e.g., a sudden 45% spike in returns) or when an analyst investigates the reasons/causes behind observed performance patterns, this falls under **Diagnostic Analytics** (*"Why did it happen?"*). Descriptive analytics merely records the spike, while Predictive would forecast future returns.
  - **中文解析**: 核心题眼在于“突发异常激增 45%”（Anomalies）以及调查其背后的“根本原因”（Underlying root cause）。根据分析类型演进框架，探寻“为什么发生”是典型的**诊断性分析（Diagnostic Analytics）**。故选 B。

### Question 2
- **正确答案**: **B**
- **考点出处**: Part 5 / Week 5 Slide 10 / Correlation Thresholds
- **深度解析**:
  - **英文解析**: Slide 10 establishes the official threshold bands: $|r| \ge 0.50$ is High/Strong; **$|r|$ between $0.30$ and $0.49$ is classified as "Moderate degree / medium correlation"**; $|r| < 0.29$ is Small/Low. An $r$ of $-0.42$ has an absolute value of $0.42$, which sits squarely in the moderate/medium band.
  - **中文解析**: 课件第 10 页标准考点：相关系数绝对值在 $0.30 \sim 0.49$ 之间被官方严格定义为**中度相关（Moderate / Medium degree correlation）**。$|-0.42| = 0.42$，落在该区间内。故选 B。

### Question 3
- **正确答案**: **B**
- **考点出处**: Part 5 / Week 5 Slide 17 & 21 / Hypothesis Formulation Signs
- **深度解析**:
  - **英文解析**: Slide 17 defines strict mathematical sign rules: **$H_0$ must contain an equality condition ($=$, $\ge$, $\le$)**, representing the status quo to be rejected. **$H_1$ represents the research claim and can ONLY use directional signs ($<$, $>$, $\ne$)**. Here, the claim is that defects are fewer than 50 ppm ($H_1: \mu < 50$), making the opposing null hypothesis $H_0: \mu \ge 50$.
  - **中文解析**: 假设检验符号法则：$H_0$ 必须包含等号（$=, \le, \ge$），代表被检验的基准现状；$H_1$ 是研究者希望证实的主张，严禁包含等号（只能是 $<, >, \ne$）。本题的研究主张是缺陷率低于 50 ppm（$H_1: \mu < 50$），因此对应的零假设必为 $H_0: \mu \ge 50$。故选 B。

### Question 4
- **正确答案**: **C**
- **考点出处**: Part 5 / Week 5 Slide 24 & 39 / P-Value Decision Rule
- **深度解析**:
  - **英文解析**: The golden decision rule is: **Reject $H_0$ if and only if P-value $< 0.05$**. Here, the calculated one-tail P-value is $0.082$. Since $0.082 \ge 0.05$, the sample evidence is insufficient to reject the null hypothesis. The correct statistical action is to **Fail to reject $H_0$**. Slide 39 explicitly illustrates: *"Do we have evidence? Yes. Is it strong enough? No (one-tail P-value is not smaller than 0.05)."*
  - **中文解析**: 核心决策红线：当且仅当 P 值 $< 0.05$ 时，才能拒绝零假设。此处计算出的单尾 P 值为 $0.082 > 0.05$，说明虽然样本存在差异，但这种差异纯属抽样偶然巧合的概率高达 8.2%，证据不够充分，因此**无法拒绝零假设（Fail to reject $H_0$）**。课件第 39 页对此有完全一致的实战案例。故选 C。

### Question 5
- **正确答案**: **B**
- **考点出处**: Part 5 / Week 5 Slide 24 / P-Value Definition
- **深度解析**:
  - **英文解析**: Slide 24 verbatim states: *"P-value is the chance of your result being just a coincidence."* It quantifies the probability of observing sample data at least as extreme as what was measured, assuming that the null hypothesis is true.
  - **中文解析**: 课件第 24 页原话：“P-value is the chance of your result being just a coincidence”（P 值就是你的测算结果纯粹是一个偶然巧合的概率）。故选 B。

### Question 6
- **正确答案**: **C**
- **考点出处**: Part 5 / Week 5 Slide 28, 29 & 32 / Normality Violations & Non-Parametric Selection
- **深度解析**:
  - **英文解析**: Slide 28 & 29 state that Skewness is acceptable up to $\pm 2.0$, and Kurtosis is acceptable up to $\pm 3.0$. Here, Skewness is $+2.85$ (exceeds $2.0$) and Kurtosis is $+4.12$ (exceeds $3.0$). The data severely violates normality! Slide 32 dictates that when comparing **two unrelated/independent samples** with non-normal data, one MUST use the non-parametric **Mann-Whitney U-test** instead of a parametric t-Test.
  - **中文解析**: 偏度阈值要求在 $\pm 2.0$ 以内，峰度要求在 $\pm 3.0$ 以内。本题偏度为 2.85，峰度为 4.12，均严重超标，属于显著非正态分布。根据课件第 32 页矩阵，比较两个独立无关样本（两个班组）且数据非正态时，对应的非参数检验方法必为**曼-惠特尼 U 检验（Mann-Whitney U-test）**。故选 C。

### Question 7
- **正确答案**: **B**
- **考点出处**: Part 5 / Week 5 Slide 26 & 32 / Non-Parametric Test for Related Samples
- **深度解析**:
  - **英文解析**: The scenario involves testing the **same group before and after** an intervention, which represents **two related/paired samples**. According to Slide 26 & 32, the parametric test is the paired t-Test; however, because normality is violated, the required non-parametric equivalent is the **Wilcoxon signed rank test**.
  - **中文解析**: 检验“同一组工人培训前与培训后”的绩效，属于经典的“两个相关/配对样本（Two related samples）”。在数据不满足正态分布的前提下，查表可知对应的非参数检验必须选用**威尔科克森符号秩检验（Wilcoxon signed rank test）**。故选 B。

### Question 8
- **正确答案**: **B**
- **考点出处**: Part 5 / Week 5 Slide 26 & 32 / Kruskal-Wallis H-Test
- **深度解析**:
  - **英文解析**: The scenario involves comparing **three unrelated groups** (Day, Swing, Night shifts) against an ordinal variable (Likert satisfaction scale). Slide 26 & 32 explicitly assign this scenario (*"Comparing three or more samples with unrelated variables / Projects vs Job satisfaction Likert scale"*) to the non-parametric **Kruskal-Wallis H-test**.
  - **中文解析**: 比较 3 个或更多独立无关组（三个不同班组），且被解释变量为李克特等级量表数据（序数非正态数据），根据课件第 26 与 32 页矩阵，标准非参数方法为**克鲁斯卡尔-沃利斯 H 检验（Kruskal-Wallis H-test）**。故选 B。

### Question 9
- **正确答案**: **B**
- **考点出处**: Part 5 / Week 5 Slide 41 & 46 / ANOVA Single Factor Meaning
- **深度解析**:
  - **英文解析**: Slide 46 explicitly poses the question: *"Why did we select single factor!?"* The answer is because there is only **one independent factor / variable** being tested (in this case, the Production Line), even though that single factor has three different treatment groups/lines being compared.
  - **中文解析**: 课件第 46 页专门启发思考：“Why did we select single factor!?”。其根本原因在于模型中只考察**一个独立的分类自变量/因子**（即生产线），虽然这个因子包含 3 个不同水平（1线、2线、3线）。故选 B。

### Question 10
- **正确答案**: **C**
- **考点出处**: Part 5 / Week 5 Slide 41, 45 & Week 7 Slide 55 / Significance F in ANOVA
- **深度解析**:
  - **英文解析**: In an Excel ANOVA summary table, the key decision metric is **Significance F**, which represents the overall P-value for testing whether all group means are identical. If Significance F $< 0.05$, the null hypothesis is rejected.
  - **中文解析**: 在 Excel 输出的方差分析表中，用于判定组间均值是否具有显著差异的统计量是 **Significance F**（其数值完全等价于方差分析模型的总 P 值）。若 Significance F $< 0.05$，则拒绝零假设。故选 C。

### Question 11
- **正确答案**: **B**
- **考点出处**: Part 6 / Week 6 Slide 10 / POM Calculation
- **深度解析**:
  - **英文解析**: Slide 10 gives the exact formula:
    $$POM = (\% Complete) \times (\% On\text{-}time) \times (\% Damage\text{-}free) \times (\% Correctly\ invoiced)$$
    $$POM = 0.96 \times 0.95 \times 0.98 \times 0.99 = 0.884184 \approx 88.42\%.$$
    Note that this is multiplicative, not an arithmetic average!
  - **中文解析**: 课件第 10 页标准公式题：完美订单满足率（POM）采用各项概率连乘计算：
    $$POM = 0.96 \times 0.95 \times 0.98 \times 0.99 = 0.884184 \approx 88.42\%。$$
    千万不要算成加法平均数（97% 是算术平均的典型陷阱选项）！故选 B。

### Question 12
- **正确答案**: **C**
- **考点出处**: Part 6 / Week 6 Slide 10 / Cash-to-Cash Cycle Time
- **深度解析**:
  - **英文解析**: Slide 10 defines the Cash-to-Cash Cycle Time formula:
    $$CCC = \text{Days Inventory Outstanding (DIO)} + \text{Days Sales Outstanding (DSO)} - \text{Days Payable Outstanding (DPO)}$$
    $$CCC = 45 + 30 - 50 = 25\text{ days.}$$
  - **中文解析**: 现金周转周期公式为：
    $$CCC = \text{存货天数} + \text{应收账款天数} - \text{应付账款天数} = 45 + 30 - 50 = 25\text{ 天。}$$
    注意 DPO 前面是减号。故选 C。

### Question 13
- **正确答案**: **C**
- **考点出处**: Part 6 / Week 6 Slide 11 / The YouRace Problem
- **深度解析**:
  - **英文解析**: Slide 11 presents the identical problem:
    - $\text{Inventory Turnover (2024)} = \frac{\$3,000,000}{\$250,000} = 12$
    - $\text{Inventory Turnover (2025)} = \frac{\$4,500,000}{\$300,000} = 15$
    The ratio increased from 12 to 15. Since a higher inventory turnover reflects more efficient asset utilization, inventory performance improved.
  - **中文解析**: 课件第 11 页 YouRace 原题重现：
    - 2024 年周转率 $= 3,000,000 / 250,000 = 12$；
    - 2025 年周转率 $= 4,500,000 / 300,000 = 15$。
    周转率由 12 提升至 15，周转率越高越好，代表 JIT 实施后库存资产运营效率显著提升。故选 C。

### Question 14
- **正确答案**: **B**
- **考点出处**: Part 6 / Week 6 Slide 14 / Servitisation by Manufacturers
- **深度解析**:
  - **英文解析**: Slide 14 defines Servitisation as manufacturers delivering not just tangible physical products, but bundling value-added services (maintenance, financing, extended warranties). It explicitly cites: *"Rolls-Royce, for instance, earns around 50% of its revenue from services."*
  - **中文解析**: 课件第 14 页原版案例！制造业服务化（Servitisation）是指制造企业从单一售卖硬件转向输出整体服务解决方案。典型代表即劳斯莱斯（Rolls-Royce）约 50% 的收入来源于航空动力飞行小时维保服务。故选 B。

### Question 15
- **正确答案**: **B**
- **考点出处**: Part 6 / Week 6 Slide 18 / SLA Metrics in Logistics
- **深度解析**:
  - **英文解析**: Slide 18 specifically delineates SLA clauses for logistics and transportation services: **Delivery Time, Allowed Damage Rate, and Penalty for delays or damages**. Corporate tax and stock prices are irrelevant to logistics SLAs.
  - **中文解析**: 课件第 18 页明确指出物流与运输外包 SLA 的三大核心法律量化条款：**送达交货时间（Delivery Time）、允许损坏率上限（Allowed Damage Rate）、以及因延误或破损引发的罚金条款（Penalty）**。故选 B。

### Question 16
- **正确答案**: **B**
- **考点出处**: Part 6 / Week 6 Slide 13 / The Transition to Service Economies
- **深度解析**:
  - **英文解析**: Slide 13 describes the Second Industrial Revolution ($\approx 1870–1914$, also called the Technological Revolution) characterized by steel, electricity, petroleum, the internal combustion engine, and the rise of mass production.
  - **中文解析**: 课件第 13 页工业革命时间线：第二次工业革命（约 1870–1914 年，又称技术革命），其标志性技术为钢铁、电力应用、石油、电话电报以及内燃机的大规模流水线生产。故选 B。

### Question 17
- **正确答案**: **C**
- **考点出处**: Part 6 / Week 6 Slide 34 / Bubble Graph
- **深度解析**:
  - **英文解析**: Slide 34 explains: *"Bubble graphs are useful for comparing the relationships between data objects in 3 numeric-data dimensions: the x-axis data, the y-axis data, and data represented by the bubble size... often used in business to visualise the relationships between alternatives investment in dimensions such as cost, value, and risk."*
  - **中文解析**: 课件第 34 页原话考查！气泡图（Bubble graph）专用于在二维平面上表达**三个数值维度（Three numeric dimensions）**（横轴、纵轴和气泡尺寸大小），商业中广泛用于对比投资备选方案的“成本、价值与风险”。故选 C。

### Question 18
- **正确答案**: **A**
- **考点出处**: Part 6 / Week 6 Slide 35 / Radar Chart (Spider Chart)
- **深度解析**:
  - **英文解析**: Slide 35 defines Radar Charts: *"very useful when comparing performance/measurement results from different sources... primary way of displaying more than two or three values at once... the greater the area covered by the plot, the greater the overall value."*
  - **中文解析**: 课件第 35 页雷达图（Radar/Spider chart）定义：用于综合对比多个不同维度的绩效指标（一次性展示 2–3 个以上指标），图表绘制覆盖的面积越大，代表综合表现越优秀。故选 A。

### Question 19
- **正确答案**: **A**
- **考点出处**: Part 6 / Week 6 Slide 36 / Chart vs. Dashboard
- **深度解析**:
  - **英文解析**: Slide 36 establishes this exact metaphor: *"A chart, or a graph, is the display of a specific information (a chapter of a story). A dashboard is a collection of these (chapters come together to tell a story)... arranged on a single screen so the information can be monitored at a glance."*
  - **中文解析**: 课件第 36 页经典比喻考题：图表展示的是某一具体维度的单项信息，代表“故事中的一个章节”；而仪表盘则是关联图表与 KPI 的集合，在单块屏幕上直观呈现，是将“所有章节组合起来讲述一个完整的业务故事”。故选 A。

### Question 20
- **正确答案**: **B**
- **考点出处**: Part 6 / Week 6 Slide 33 / Scatter Plots
- **深度解析**:
  - **英文解析**: Slide 33 notes that a Scatter Plot is particularly useful when exploring the correlation pattern between two continuous numerical variables ($X$ = Overtime hours, $Y$ = Packing errors). It visually illustrates correlation strength, linear/nonlinear relationships, and clearly highlights atypical outliers.
  - **中文解析**: 课件第 33 页指出：散点图（Scatter plot）专门用于展现两个连续数值变量之间的相关性关系（横轴自变量，纵轴因变量），并能清晰识别异常离群点（Outliers）。故选 B。

---
*文件已自动生成并保存至本地工作空间：`INMT5518_Part5_Part6_Detailed_Review.md`*

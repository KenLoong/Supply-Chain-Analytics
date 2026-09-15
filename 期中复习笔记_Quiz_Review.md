# INMT5518 Supply Chain Analytics — 期中复习笔记

> **考试须知 Quiz Info**  
> 闭卷 Closed book · 单选题 MCQ（单一正确答案 single correct answer）  
> 无倒扣分 No negative marks — 不确定也要选！  
> 带上：学生证 Student ID + 铅笔 pencil

---

## PART 1 — 供应链分析核心框架 Core Framework

### 1.1 供应链管理定义 Definitions

**Supply Chain（供应链）**  
所有参与设计、生产、交付和使用产品/服务的企业和活动的总和。  
*All companies and activities needed to design, make, deliver, and use a product or service.*

**Supply Chain Management（供应链管理）**  
对供应链中生产、库存、选址、运输和信息的协调，以实现响应性和效率的最佳组合。  
*The coordination of production, inventory, location, transportation, and information among participants to achieve the best mix of responsiveness and efficiency.*

**SCM 的目标 Goal（Goldratt）**  
> "Increase throughput while simultaneously reducing both inventory and operating expense."  
> 在同时降低库存和运营费用的情况下，提高吞吐量。

**SCM vs Logistics 区别**  
- Logistics 传统上关注单一企业内部的采购、配送、库存管理  
- SCM 范围更广，还包括市场营销、新产品开发、财务、客户服务

---

### 1.2 五个核心问题 5 Key Questions

| # | 英文问题 | 中文 | 对应分析类型 |
|---|---------|------|------------|
| 1 | What is my plan? | 我的计划是什么？ | 战略目标 |
| 2 | What is my present position? | 我目前的位置在哪？ | Descriptive Analytics |
| 3 | What are the variances? What caused them? | 偏差是什么？原因是什么？ | Diagnostic Analytics |
| 4 | What are the trends? What are the forecasts? | 趋势和预测是什么？ | Predictive Analytics |
| 5 | What actions are required? | 需要采取什么行动？ | Prescriptive Analytics |

---

### 1.3 四种分析类型 4 Types of Analytics ⭐（核心考点）

从左到右，**复杂度和成本递增，附加价值也递增**。  
*Complexity and cost increase left to right, so does added value.*

| 类型 Type | 核心问题 Key Question | 方法 Methods |
|-----------|----------------------|-------------|
| **Descriptive Analytics** 描述性分析 | *What happened?* 发生了什么？ | 表格、图表、汇总统计 |
| **Diagnostic Analytics** 诊断性分析 | *Why did it happen?* 为什么发生？ | 相关性、假设检验、t检验、ANOVA |
| **Predictive Analytics** 预测性分析 | *What will happen?* 将会发生什么？ | 回归分析、分类模型、需求预测 |
| **Prescriptive Analytics** 规定性分析 | *What should we do?* 我们应该怎么做？ | 优化、决策模型、AI建议 |

---

## PART 2 — 分析工具与数据 Analytics Tools & Data（Week 3）

### 2.1 结构化与非结构化数据 Structured vs Unstructured Data

**Structured Data（结构化数据）**  
以行列形式组织，如 Excel 表格、SQL 数据库。  
→ **供应链分析中主要使用这种数据类型**（定量数据 quantitative data 为主）

**Unstructured Data（非结构化数据）**  
文本、图片、音频、视频，无预定格式；分析难度更高，需要 Apache Spark 等工具处理。

---

### 2.2 主要分析工具对比 Analytics Tools Comparison ⭐

| 工具 Tool | 类型 | 开源 Open Source? | 核心用途 Best For |
|-----------|------|-------------------|-----------------|
| **Excel** | 电子表格 Spreadsheet | 否（付费）| 数据清洗、报告制作；全球最广泛使用 |
| **Python** | 编程语言 | 是 | 从零构建软件；海量免费库（如情感分析库）；比R更推荐 |
| **R** | 编程语言 | 是 | 统计分析、数据挖掘；比Python慢、安全性低、学习更复杂 |
| **Jupyter Notebook** | 交互式创作工具 | 是 | 共享代码、实时文档、可视化展示 |
| **Apache Spark** | 数据处理框架 | 是 | 大数据处理；非结构化数据；**比同类平台快达100倍**（利用RAM而非磁盘）|
| **SAS** | 统计软件 | 否（付费）| 商业智能、报告、数据挖掘、预测建模 |
| **Power BI / Tableau** | 可视化工具 | 否（付费）| 数据仪表盘与可视化 |
| **KNIME** | 数据集成平台 | 是 | 数据挖掘、机器学习；从多种来源导入数据 |

> **记忆要点 Key Comparison**  
> Python vs R：除非专门做统计分析，否则Python是更好的选择（更快、更安全、更易学）。  
> Apache Spark 快100倍的原因：使用计算机 **RAM（内存）** 而非本地磁盘存储。

---

### 2.3 数据清洗 Data Cleaning in Excel

| 操作 Operation | Excel 步骤 |
|---------------|-----------|
| 导入CSV文件 Import CSV | Data → Get External Data → From Text/CSV → 选择分隔符 delimiter |
| 删除重复数据 Remove duplicates | Data → Remove Duplicates |
| 数据验证 Data Validation | 防止错误数据录入 prevent incorrect entries |
| 从网页导入 Import from Web | Data → From Web → 粘贴URL |
| 清理脏数据 Clean dirty values | Find & Replace，或 Data → Text to Column / Delimited |
| 处理缺失值 Missing values | 替换为**列平均值**（更聪明的做法：替换为**所在子组的平均值**，如同一生产线员工的均值） |

---

### 2.4 第三方与第四方物流 3PL vs 4PL ⭐

**3PL — Third-Party Logistics（第三方物流）**  
将**部分**物流流程外包给第三方企业。  
服务包括：运输 Transportation、仓储 Warehousing、拣选打包 Pick & Pack、轻度制造 Light manufacturing、清关 Customs clearance、逆向物流 Reverse logistics

| 缺点 Downside | 挑战 Challenges |
|--------------|----------------|
| 控制力减弱 Less control | 成本 Costs |
| 管理不善可能导致客户流失 | 保密性 Confidentiality |
| | 绩效指标难以监控 Performance metrics |

**4PL — Fourth-Party Logistics（第四方物流）**  
将**整个**物流功能外包给物流服务提供商 LSP（Logistics Service Provider）。  
→ LSP 通常会进一步分包给 3PL  
→ 比3PL范围更广：管理和协调整个供应链的物流运作

> **关键区别**：3PL负责**具体职能**（如运输或仓储）；4PL负责**整体运筹管理**。

---

## PART 3 — 供应链基础 SC Basics（教材 Chapter 1）

### 3.1 五大供应链驱动因素 5 Supply Chain Drivers ⭐

每个驱动因素都存在**响应性 Responsiveness 与效率 Efficiency 的权衡 trade-off**。

**1. Production（生产）**
- 响应性做法：大量闲置产能、弹性制造、靠近客户建多个小工厂
- 效率做法：最小化闲置产能、产品线集中、大型中央工厂规模效益

**2. Inventory（库存）**
- 响应性做法：高库存水平、多品类、多地点分散储存
- 效率做法：低库存水平、集中储存、减少滞销品

**3. Location（选址）**
- 响应性做法：多地点靠近客户（如麦当劳门店遍布各地）
- 效率做法：少数中央节点集中运营（如Dell的组装中心）

**4. Transportation（运输）**
- 响应性做法：快速运输方式（航空 Air、卡车 Truck，如FedEx/UPS，24小时送达）
- 效率做法：慢速运输方式（船运 Ship、铁路 Rail、管道 Pipeline，大批量）

**5. Information（信息）**
- 响应性做法：在整个供应链中共享准确的实时数据（如消费电子行业）
- 效率做法：减少数据收集和共享；短期成本低，长期效益差

---

### 3.2 供应链参与者 Participants

| 角色 | 说明 |
|------|------|
| **Producers（生产商）** | 制造产品——原材料或成品；也可生产无形产品（软件、服务） |
| **Distributors / Wholesalers（分销商/批发商）** | 从生产商大批采购，捆绑交付给客户；缓冲生产商的需求波动 |
| **Retailers（零售商）** | 小批量销售给公众；密切追踪消费者偏好 |
| **Customers / Consumers（顾客/消费者）** | 购买并使用产品的组织或个人 |
| **Service Providers（服务提供商）** | 物流、金融、市场调研、IT、法律服务等专业服务商 |
| **Extended Chain** | 终极供应商（供应商的供应商）→ 公司 → 顾客 → 终极客户 |

---

### 3.3 纵向整合→虚拟整合 Vertical → Virtual Integration

- **旧模式**：公司拥有供应链的大部分（如福特River Rouge工厂——铁矿石进，81小时后汽车出）
- **变革驱动力**：全球化、快速变化的市场、技术快速迭代
- **新模式**：公司专注**核心能力 core competencies**，与其他公司合作（虚拟整合）
- **案例**：沃尔玛的成功要素——先建配送中心再开店；与供应商EDI连接；"大盒子"门店格式；天天低价 Everyday Low Prices

---

### 3.4 供应链与业务战略对齐 3 Steps to Align SC with Strategy

1. **Understand the markets** 理解市场：客户需要的数量、响应时间、产品多样性、服务水平、价格、创新速度
2. **Define core competencies** 明确核心能力：你的公司擅长什么？在供应链中扮演什么角色？
3. **Develop SC capabilities** 发展供应链能力：配置每个驱动因素以匹配战略

> **经典案例**：7-Eleven → 强调**响应性**（便利优先）；Sam's Club → 强调**效率**（价格优先）

---

## PART 4 — 库存管理 Inventory Management（Week 4）

### 4.1 库存类型 Types of Inventory

| 类型 | 英文 | 说明 |
|------|------|------|
| 原材料 | **Raw Material** | 加工前的投入物 |
| 在制品 | **Work In Progress (WIP)** | 已部分加工，尚未完成的产品 |
| 成品 | **Finished Goods (FG)** | 已完成、可销售的产品 |
| 维修耗材 | **MRO** (Maintenance, Repair & Overhaul) | 工具、清洁用品等耗材 |

> **记住**：库存会掩盖问题！库存是有成本的——占用的资金本可投资到其他地方（**机会成本 Opportunity cost**）。

---

### 4.2 ABC 分析法 ABC Analysis ⭐

基于 **Pareto（帕累托）/ 80/20 法则**，按年度费用将库存分类，集中管理最重要的项目。

| 分类 | 占总价值比例 | 占项目数量比例（约） | 管理方式 |
|------|------------|---------------------|---------|
| **A 类** | ~65–80% | ~10–20% | 最严格控制——**Reorder Point (ROP) 系统**（定点补货） |
| **B 类** | ~15–25% | ~30–40% | 中等控制——**Periodic review system**（定期检查） |
| **C 类** | ~5–15%  | ~40–50% | 最低控制——每年批量采购一到两次 |

> **课件例子**：第373项和第539项合计占总费用的65%以上 → 均为A类

---

### 4.3 库存成本 Inventory Costs

**Holding Cost（持有成本/库存成本）** — 库存量越大，成本越高
- 存储 Storage、保险 Insurance、税费 Tax、维护 Maintenance
- 报废/过期 Obsolescence
- **机会成本 Opportunity cost**（资金若用于其他投资的潜在收益）

**Order Cost / Setup Cost（订货成本）** — 订货量越大，单次成本越低
- 行政成本（文件处理、沟通）Administrative costs
- 运输/运费 Transportation fees
- 生产线调整成本 Setup costs
- **潜在的失单成本**（甚至永久失去客户）Lost sales

---

### 4.4 经济订货量 EOQ (Economic Order Quantity) ⭐

最小化**总年度库存成本**的订货量。

$$\boxed{EOQ = \sqrt{\frac{2DS}{H}}}$$

| 变量 | 含义 |
|------|------|
| **D** | 年需求量 Annual demand |
| **S** | 每次订货成本 Ordering/setup cost per order |
| **H** | 每单位年持有成本 Annual holding cost per unit |

**总年度成本 Total Annual Cost (TAC)**

$$TAC = \text{Purchase cost} + \left(SS + \frac{Q}{2}\right) \times H + \frac{D}{Q} \times S$$

- 平均库存水平 Average inventory = SS + Q/2
- SS = Safety Stock（安全库存），Q = 订货量

---

### 4.5 安全库存 Safety Stock ⭐

安全库存是为应对不确定性而储备的缓冲库存（也称 Buffer Stock）。

$$\boxed{SS = \text{Max use during lead time} - \text{Average use during lead time}}$$

**为什么需要安全库存？**
- 供应商延迟交货 Late deliveries
- 需求突然增加 Sudden demand increase
- 原料质量问题 Poor quality
- 生产问题造成损耗 Production problems

> **根本原因 Root cause = Variation（波动/变异）**  
> 包括：需求波动、交货期波动、生产速率波动、质量波动  
> **没有波动 → 不需要安全库存**  
> 安全库存不是免费的！它需要承担持有成本。

**如何减少安全库存 Reducing Safety Stock**

| 方法 | 说明 | 例子 |
|------|------|------|
| **Inventory centralisation** 库存集中化 | 合并多个地点的需求 | 汽车行业集中仓库 |
| **Delayed product differentiation / Postponement** 推迟差异化/延迟原则 | 尽量推迟产品定制时间 | 智能电视出厂后再配置语言；沙发后期才定制颜色 |
| **Increasing part commonality** 提高零件通用性 | 用相同零部件满足不同需求 | 欧盟强制要求USB-C接口 |
| **Decrease transit inventory** 减少在途库存 | 缩短交货期或谈判紧急交货选项 | 与供应商协商快速配送 |

---

### 4.6 库存减少原则 Inventory Reduction Principles

1. **Pool inventory（库存集中）**：合并不同地点/产品/零件的需求
2. **Reduce variation（减少波动）**：波动越小，所需安全库存越少
3. **Reduce lead time（缩短交货期）**：直接降低再订货点(ROP)和在途库存成本
4. **JIT — Just-in-Time（准时制）**：哲学与技术兼具，只在需要时才收到货物

---

## PART 5 — 诊断性分析 Diagnostic Analytics（Week 5）

### 5.1 何时使用诊断性分析

- 有人提出一个主张，你想验证其正确性
- 数据中存在可能有意义的关联关系
- 出现异常——数据模式突然变化，或某些数值超出预期
- 做法：深入挖掘数据（发现规律）→ 确定关系（找出原因）

---

### 5.2 相关性 Correlation

| 系数范围 Coefficient | 解读 Interpretation |
|---------------------|---------------------|
| 接近 ±1 Near ±1 | 完全相关 Perfect correlation |
| ±0.50 到 ±1 | 高度相关 Strong / High degree |
| ±0.30 到 ±0.49 | 中度相关 Moderate / Medium degree |
| 低于 ±0.29 Below ±0.29 | 低度相关 Weak / Low degree |

- **正相关 Positive**：两变量同向变动（一增另也增）
- **负相关 Negative**：两变量反向变动（一增另减）
- 工具：Pearson（正态分布数据用）vs **Spearman rank-order**（非参数，用于Likert量表等）

---

### 5.3 假设检验 Hypothesis Testing ⭐

**基本概念**

| 概念 | 说明 | 允许符号 |
|------|------|---------|
| **H₀ — Null Hypothesis（零假设）** | 我们想要**拒绝**的主张（如果有足够证据） | = 或 ≥ 或 ≤ |
| **H₁/Ha — Alternative Hypothesis（备择假设）** | 我们**喜欢**的主张，即研究主张 | ≠ 或 > 或 < |

> **关键原则**：我们永远只能**拒绝 H₀**（reject），无法"证明" H₁

**P 值规则 P-Value Rule** ⭐

$$\boxed{\text{若 P-value} < 0.05 \Rightarrow \text{拒绝 H₀（结果具有统计显著性）}}$$
$$\text{若 P-value} \geq 0.05 \Rightarrow \text{无法拒绝 H₀（fail to reject H₀）}$$

- P值含义：结果仅是巧合的概率
- P值=0.05意味着：若取100个样本，其中95个会支持拒绝H₀

**假设检验步骤**
1. **检验数据是否正态分布**：Descriptive Statistics → 检查偏度(Skewness)和峰度(Kurtosis)
2. **选择并运行适当的检验**（t检验 / ANOVA / 非参数等价检验）
3. **检查 p 值**：< 0.05 则拒绝 H₀

---

### 5.4 正态分布检验 Normal Distribution Check

**偏度 Skewness**
- 理想范围：**−1 到 +1**
- 可接受范围：**−2 到 +2**
- 超出 ±2 → 使用**非参数检验**

**峰度 Kurtosis**
- 理想范围：**−2 到 +2**
- 可接受范围：**−3 到 +3**
- 超出 ±3 → 使用**非参数检验**

Excel操作：Data → Data Analysis → Descriptive Statistics

---

### 5.5 参数检验 vs 非参数检验 Parametric vs Non-Parametric ⭐

| 场景 Scenario | 参数检验（正态分布）| 非参数检验（非正态）| 例子 |
|--------------|---------------------|---------------------|------|
| 比较**2个相关样本** | **t-Test** | Wilcoxon signed rank test | 培训前后的绩效 |
| 比较**2个不相关样本** vs 某变量 | **t-Test** | Mann-Whitney U test | 性别(M/F) vs 工作满意度 |
| 比较**3个以上相关样本**，1个变量 | **ANOVA** | Friedman test | 公司职位 vs 薪资水平 |
| 比较**3个以上不相关样本** | **ANOVA** | Kruskal-Wallis H test | 负责项目 vs 工作满意度 |
| 比较**不相关分类** | 无 | **Chi-square test** | 获奖(是/否) vs 绩效水平 |
| 比较**2个独立排名** | Pearson correlation | **Spearman rank-order test** | 薪资 vs 工作满意度(Likert) |

---

### 5.6 ANOVA 方差分析

- 用于比较**两组以上**（t检验只能比较两组）
- H₀：所有组相似 H₀: these groups are similar
- H₁：各组不全相似 H₁: these groups are not similar
- Excel：Data → Data Analysis → **ANOVA: Single Factor**
- "Single Factor" = 只有一个自变量被检验
- 查看 **Significance F**（类似p值）→ 必须 < 0.05 才能拒绝 H₀

**使用案例**：3种疗法 vs 患者疗效；3条生产线 vs 员工满意度；不同院校 vs 考试成绩

---

## PART 6 — 数据可视化与KPI（Week 6）

### 6.1 监控供应链绩效的必要性

| 原因 | 说明 |
|------|------|
| **Cost Reduction 成本降低** | 识别浪费和低效环节 |
| **Customer Satisfaction 客户满意度** | 确保库存可用性、准时交货、产品质量 |
| **Risk Mitigation 风险管控** | 提早识别并应对风险 |
| **Supplier Relationships 供应商关系** | 促进更好的沟通与协作，建立长期合作关系 |

---

### 6.2 关键绩效指标 KPIs ⭐

| KPI | 公式 Formula | 备注 |
|-----|-------------|------|
| **Perfect Order Measurement (POM)** | %Complete × %On-time × %Damage-free × %Correctly invoiced | 越高越好 |
| **Inventory Turnover (IT)** | Cost of Goods Sold ÷ Average Inventory | 越高越好（库存管理越高效）|
| **Cash-to-Cash Cycle Time (CCC)** | Days Inventory Outstanding + Days Sales Outstanding − Days Payable Outstanding | 越低越好 |
| **Lead Time** | 从下订单到收货的时间 | 越低响应性越强 |
| **Freight Cost per Unit** | Total Freight Costs ÷ Total Units Shipped | 越低运输效率越高 |

> **课件例题 IT**：YouRace 2024年：3,000,000 ÷ 250,000 = **12**；2025年JIT后：4,500,000 ÷ 300,000 = **15**（提升了）

---

### 6.3 图表类型选择 Chart Types ⭐

| 图表类型 | 最适用场景 | 关键优势 |
|---------|-----------|---------|
| **Bar / Column Chart 柱状图** | 比较不同类别的数值差异 | 清晰对比；数据汇总直观 |
| **Line Chart 折线图**（时间序列） | 展示数值随时间的变化趋势 | 显示趋势和关系；跨组比较趋势 |
| **Pie Chart 饼图** | 展示整体的各部分占比（百分比）| 整体感知好；变体：Donut Chart 环形图 |
| **Scatter Plot 散点图** | 展示两变量之间的相关关系 | 可见正/负/强/弱相关；用于外推和插值 |
| **Bubble Chart 气泡图** | 展示三个数值维度（x, y, 气泡大小）| 不用3D图即可展示3个变量；常用于成本/价值/风险分析 |
| **Radar / Spider Chart 雷达图** | 多属性绩效综合比较 | 同时展示2–3个以上指标；直观感受整体数据 |

---

### 6.4 图表 vs 仪表盘 Chart vs Dashboard

| | Chart 图表 | Dashboard 仪表盘 |
|---|------------|-----------------|
| 比喻 | 故事的一个章节 | 所有章节组合成完整的故事 |
| 范围 | 展示一个特定信息 | 汇集多个相关数据集 |
| 目标 | 单一洞察 | 讲述一个完整的故事，有目标和KPI |

**仪表盘特征 Dashboard Characteristics**：
可定制 Customisable · 交互式 Interactive · 实时监控 Real-Time · 数据集中 All-in-one · 吸引眼球 Attractive

**数据可视化三要素**：Informative（信息性） · Efficient（高效简洁） · Appealing（美观吸引人）

---

### 6.5 服务链与SLA Service Chains & SLA

**服务链 Service Chains**：将供应链管理理念应用于服务交付（不仅限于制造业）

**SLA（Service Level Agreement，服务水平协议）**  
规定服务提供商的预期表现——质量、可用性、责任和违约罚则

| 场景 | SLA指标示例 |
|------|-----------|
| 呼叫中心 / IT | 可用时间 Availability Time、响应时间 Response Time、解决时间 Resolution Time |
| 物流运输 | 交货时间 Delivery Time、允许损坏率 Allowed Damage Rate、延误/损坏赔偿 Penalty |

**服务化 Servitisation**：制造商在产品基础上增加服务以提升价值主张  
例：劳斯莱斯约50%收入来自服务（维修、保养等）

---

### 6.6 工业革命简述（背景知识）

| 次序 | 时间 | 核心技术 |
|------|------|---------|
| 第一次 1st | ≈1750–1850 | 蒸汽机、煤炭、纺织、铁路 |
| 第二次 2nd | ≈1870–1914 | 钢铁、电力、石油、电报、内燃机；大规模生产兴起 |
| 第三次 3rd | ≈1970s+ | 计算机、互联网——数字化革命 Digital Revolution |
| 第四次 4th | 今天 | AI、机器人、物联网IoT、3D打印、生物技术 |

---

## PART 7 — 预测性分析 Predictive Analytics（Week 7）

### 7.1 概述 Overview

- 利用历史数据识别规律 → 预测未来
- 识别到的规律被表示为一个**数学模型 mathematical model**
- 该模型应用于新数据以产生预测结果

| 方法 | 说明 |
|------|------|
| **Quantitative（定量）** | 使用历史数据和统计模型（如回归分析） |
| **Qualitative（定性）** | 依赖专家意见、市场调研、客户反馈 |

---

### 7.2 分类模型 Classification Models

**Classification（分类）**：基于已有数据，为新数据创建类别/决策

| 类型 | 说明 | 例子 |
|------|------|------|
| **Binary classification 二分类** | 两种结果 | 垃圾邮件/非垃圾邮件 |
| **Multiclass classification 多分类** | 多种结果 | 成绩等级 A/B/C |

**SC应用**："是否与这个供应商签合同？"→ 是/否决策模型

**决策树 Decision Tree**
- 倒置树状图，基于布尔/非布尔测试进行分类
- **Root node（根节点）**：树的起点
- **Splitting / Branching（分裂/分支）**：将节点分为子节点
- **Leaf / Terminal node（叶节点/终端节点）**：无进一步分裂——最终类别
- **Child node（子节点）**：某节点的下级节点
- **Parent node（父节点）**：拥有子节点的节点

**常见分类算法**：Decision Trees · Random Forest · Voting Classifiers · Neural Networks / Deep Learning

---

### 7.3 回归分析 Regression ⭐

研究**因变量（目标变量）与自变量（预测变量）**之间的关系，用于预测和因果分析。

**简单线性回归 Simple Linear Regression**

$$\boxed{y = a \cdot x + b + \varepsilon}$$

| 符号 | 含义 |
|------|------|
| y | 因变量 dependent variable（目标） |
| x | 自变量 independent variable（预测量） |
| a | 斜率 slope |
| b | 截距 intercept |
| ε | 误差项 error term |

**多元回归 Multiple Regression**（两个以上自变量）

$$\boxed{Y = a_1x_1 + a_2x_2 + \cdots + a_nx_n + b}$$

例：Price = a₁ × Production Cost + a₂ × Inventory Cost + b

---

### 7.4 回归分析中的关键统计量 Key Statistics ⭐

| 统计量 | 含义 | 阈值 Threshold |
|--------|------|----------------|
| **R² (R-squared)** | Y的方差中被自变量解释的比例（0–1，即0%–100%）| 0.50–0.99 可接受 |
| **Significance F** | 整个模型的显著性（相当于整个模型的p值）| **必须 < 0.05** 才能继续分析 |
| **P-value（系数）** | 每个自变量的显著性 | < 0.05 该变量有显著影响 |

Excel操作：Data → Data Analysis → Regression → 选择Y范围和X范围

---

### 7.5 牛鞭效应 Bullwhip Effect ⭐

**定义**：需求波动在供应链上游逐级放大的现象。  
消费者需求的小幅波动 → 零售商放大 → 批发商进一步放大 → 制造商过度反应 → 供应商过量生产

**典型案例**：消费者销售增加5% → 零售商多订10% → 批发商多订15% → 制造商增产20–25%

**5大根本原因 Causes**

| # | 原因 | 说明 |
|---|------|------|
| 1 | **Demand forecasting** 需求预测 | 每个环节都会添加自己的缓冲量 |
| 2 | **Long lead times** 长交货期 | 距离越远，不确定性越大 |
| 3 | **Batch ordering** 批量订购 | 大批量、低频率的订单扭曲需求信号 |
| 4 | **Price fluctuations** 价格波动 | 促销活动制造人为需求高峰 |
| 5 | **Inflated orders** 虚报订单 | 担心缺货而过度订购 |

**消除策略 Strategies to Eliminate**

| 策略 | 说明 |
|------|------|
| **Real-time information sharing** | 使用ERP、EDI共享POS数据、库存水平和预测信息 |
| **Collaborative Planning (CPFR)** | 协同计划、预测与补货——统一决策 |
| **Vendor Managed Inventory (VMI)** | 由供应商根据实际消耗来管理库存 |
| **Smaller, frequent orders** | 减少批量、提高订货频率，平滑需求信号 |
| **Stable pricing** | 避免无规律促销；使用"天天低价"策略 |
| **Lead time reduction** | 精简物流和生产流程 |
| **Advanced Analytics & AI** | 利用预测模型纳入外部因素（天气、趋势、事件） |
| **Long-term supplier relationships** | 与供应商和分销商建立长期合作关系 |

> **最大障碍**：**TRUST（信任）问题**——谁来优化供应链？收益如何分配？共享信息会不会被竞争对手利用？

---

## PART 8 — 高频考点速记 Quick Reference ⭐⭐⭐

### 必背公式

| 公式名称 | 公式 |
|---------|------|
| EOQ | $EOQ = \sqrt{2DS/H}$ |
| TAC | $TAC = \text{Purchase cost} + (SS+Q/2)\cdot H + (D/Q)\cdot S$ |
| Safety Stock（简单版）| SS = Max use during lead time − Average use during lead time |
| Inventory Turnover | IT = Cost of Goods Sold ÷ Average Inventory |
| POM | % Complete × % On-time × % Damage-free × % Correctly invoiced |
| CCC | Days Inventory Outstanding + Days Sales Outstanding − Days Payable Outstanding |
| Linear Regression | y = a·x + b + ε |
| Multiple Regression | Y = a₁x₁ + a₂x₂ + … + aₙxₙ + b |

---

### 判断题/选择题易混淆点

1. **P-value < 0.05 → 拒绝 H₀**（同时适用于假设检验和回归分析中的Significance F）
2. **R²可接受范围：0.50–0.99**（不是越高越好——1.0可能意味着过拟合）
3. **t检验用于2组；ANOVA用于3组或以上**
4. **正态分布检验**：Skewness 好在±1内，可接受±2；Kurtosis 好在±2内，可接受±3
5. **3PL = 部分职能外包；4PL = 整体物流外包**（4PL通常再包给3PL）
6. **Apache Spark快100倍** 的原因是使用 **RAM（内存）**，而非更好的算法
7. **安全库存的根本原因是 Variation（波动）**，不是需求本身
8. **ABC分析**：A类 = 最高价值（65–80%），用ROP系统；C类 = 最低价值，每年买1–2次
9. **牛鞭效应**：信息不对称和不信任是根本障碍；VMI和CPFR是主要解决方案
10. **Descriptive → Diagnostic → Predictive → Prescriptive**：复杂度和附加价值递增

---

### 工具选择速查

| 场景 | 推荐工具 |
|------|---------|
| 2组对比（正态）| t-Test |
| 3+组对比（正态）| ANOVA |
| 2个相关样本对比（非正态）| Wilcoxon signed rank test |
| 2个不相关样本对比（非正态）| Mann-Whitney U test |
| 类别与类别对比 | Chi-square test |
| 两变量排名关系（非正态）| Spearman rank-order test |
| 预测连续值 | Regression（回归） |
| 预测类别/决策 | Classification（分类，如决策树）|
| 多属性绩效对比可视化 | Radar / Spider Chart |
| 两变量相关可视化 | Scatter Plot |
| 时间序列趋势 | Line Chart |
| 部分占整体 | Pie Chart |
| 类别间对比 | Bar / Column Chart |
| 3维度对比 | Bubble Chart |

---

*笔记整理自 INMT5518 Week 3–7 课件及教材 Chapter 1*  
*Last updated: Week 8 exam prep*

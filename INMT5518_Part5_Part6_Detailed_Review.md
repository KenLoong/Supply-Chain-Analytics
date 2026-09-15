# INMT5518 Supply Chain Analytics
# Comprehensive Exam Review Guide: Part 5 & Part 6 (English-First Edition)

> **Assessment Context**: Closed-Book Midterm Quiz (Week 8)  
> **Format**: Multiple Choice Questions (MCQs), Single Correct Answer, No Negative Marking.  
> **Instructional Design**: **English-First Architecture**. Academic definitions, statistical formulas, operational frameworks, and question stems are articulated in rigorous academic and business English (mirroring Dr. Mehdi Rajabi Asadabadi’s Week 5 & Week 6 lecture slides), accompanied by targeted Chinese annotations (【考点释义 / 核心精解】) for rapid mastery.

---

# SECTION 1: DIAGNOSTIC ANALYTICS & HYPOTHESIS TESTING (WEEK 5)

## 1.1 Nature, Positioning & Triggers of Diagnostic Analytics

### 1. Conceptual Definition & Core Objective
- **Core Question**: *"What caused the variances? Why did it happen?"*
- **Action Trajectory**:
  $$\mathbf{\text{Drill into the analytics} \longrightarrow \text{Detect patterns} \longrightarrow \text{Determine relationships}}$$
- **Analytical Value**: Diagnostic analytics bridges the gap between backward-looking **Descriptive Analytics** (*"What happened?"*) and forward-looking **Predictive Analytics** (*"What will happen?"*). It diagnoses underlying root causes and validates behavioral relationships.

### 2. Three Operational Triggers for Diagnostic Analytics ⭐
1. **Verifying Claims (验证商业假设与主张)**:
   - When business partners, functional managers, or suppliers assert an operational claim (e.g., *"Male and female warehouse supervisors have significantly different hourly wages"*, or *"A new vendor safety certification significantly reduced packaging defect rates"*), diagnostic testing statistically verifies whether empirical evidence supports or refutes the claim.
2. **Identifying Meaningful Relationships (挖掘深层业务关联)**:
   - Uncovering underlying linkages between variables to inform strategic decision-making (e.g., examining whether freight transit delays strongly correlate with supplier geographic distance, or whether promotional price discounts correlate with warehouse stockouts).
3. **Investigating Anomalies (调查突发数据异常)**:
   - When operations encounter sudden unexpected shifts in business patterns (sudden changes in data patterns) or when recorded operational metrics fall outside expected historical boundaries (metrics beyond expected values).

---

## 1.2 Correlation Analysis (Pearson $r$) ⭐⭐⭐

Correlation analysis measures the **direction and strength of the linear relationship** between two continuous numerical variables. The correlation coefficient ($r$) ranges strictly between $-1.0$ and $+1.0$.

```
[-1.0] ────────────── [-0.50] ──────── [-0.30] ────── [0] ────── [+0.30] ──────── [+0.50] ────────────── [+1.0]
Perfect Negative       Strong Negative   Moderate Neg   Zero     Moderate Pos      Strong Positive   Perfect Positive
```

### Official Lecture Interpretation Thresholds (Slide 10)

| Absolute Value Range ($|r|$) | Official Classification (Slide 10) | Operational & Mathematical Meaning |
| :---: | :--- | :--- |
| **Near $\pm 1.00$** | **Perfect correlation** | Points align on a straight line; one variable moves in perfect mathematical lockstep with the other. |
| **$\pm 0.50$ to $\pm 1.00$** | **High degree / Strong correlation** | Strong, robust linear co-movement between variables; serves as an essential candidate feature for predictive modeling. |
| **$\pm 0.30$ to $\pm 0.49$** | **Moderate degree / Medium correlation** | Noticeable linear co-movement, accompanied by moderate stochastic dispersion/noise. |
| **Below $\pm 0.29$** | **Small / Low degree correlation** | Weak or negligible linear relationship; variables are practically independent in operations. |

> **Critical Axiom**: **"Correlation does NOT imply Causation."**  
> *(相关性不等于因果性。相关性仅能证明两个变量存在伴随变动，不能直接断定前者是后者的原因，但它是筛选因果候选变量的第一步。)*

---

## 1.3 Foundations of Statistical Hypothesis Testing ⭐⭐⭐

> *"A hypothesis is an idea/claim that can be tested."* (Slide 17)

### 1. Mathematical Sign Rules for $H_0$ and $H_1$ ⭐
Formulating statistical hypotheses requires adherence to strict mathematical conventions:

| Hypothesis Type | Academic & Operational Role | Allowed Mathematical Signs | Core Intuition & Business Framing |
| :---: | :--- | :---: | :--- |
| **$H_0$<br>(Null Hypothesis)** | **Status Quo / Baseline**<br>Represents "no difference", "no effect", or historical benchmark. **The hypothesis we seek to REJECT!** | $\mathbf{=}\ ,\ \mathbf{\ge}\ ,\ \mathbf{\le}$<br>*(MUST contain the equal sign!)* | "Training had no effect"; "Supplier defect rate is at or above 50 ppm"; "Salaries are equal between genders". |
| **$H_1$ or $H_a$<br>(Alternative Hypothesis)** | **Research Claim / "The Claim We Like"**<br>Represents the researcher’s actual target proposition (Slide 17: *"The pleasing claim"*). | $\mathbf{\neq}\ ,\ \mathbf{>}\ ,\ \mathbf{<}$<br>*(STRICTLY FORBIDDEN from having an equal sign!)* | "Training significantly improved scores"; "Supplier defect rate is strictly less than 50 ppm"; "Salaries differ". |

- **Two-Tailed Test (双尾检验)**: $H_0: \mu = \mu_0$ vs. $H_1: \mu \neq \mu_0$
- **One-Tailed Test (单尾检验 - Lower Tail)**: $H_0: \mu \ge \mu_0$ vs. $H_1: \mu < \mu_0$
- **One-Tailed Test (单尾检验 - Upper Tail)**: $H_0: \mu \le \mu_0$ vs. $H_1: \mu > \mu_0$

### 2. The P-Value Decision Rule & Statistical Philosophy ⭐⭐⭐
> **Slide 24 & 39 Definitive Doctrines**:
> 1. *"**P-value is the chance of your result being just a coincidence.**"*
> 2. *"**All we can do in hypothesis testing is to reject the null hypothesis.**"*
- In classical frequentist hypothesis testing, one **CANNOT mathematically "prove" the alternative hypothesis**; one can only gather sufficient sample evidence to **reject the null hypothesis**, thereby leaving the alternative hypothesis as the supported explanation.
- **Decision Benchmark ($\alpha = 0.05$, 5% Significance Level)**:
  - If $P\text{-value} < 0.05 \implies$ **Reject $H_0$** (Statistically significant evidence exists; coincidence chance is under 5%).
  - If $P\text{-value} \ge 0.05 \implies$ **Fail to Reject $H_0$** (Insufficient evidence to overturn the status quo).
  - *Exam Pitfall*: Never state *"Accept $H_0$"* or *"Proved $H_0$ is true"*. The correct academic terminology is **"Fail to reject $H_0$"**.

---

## 1.4 Normality Verification: Skewness & Kurtosis Thresholds ⭐⭐

Before applying parametric mean tests, analysts must confirm whether sample data follows a **Normal Distribution**. Violations of normality invalidate classical parametric procedures and require switching to non-parametric methods.

```
       [ Positive / Right Skew ]                 [ Normal Distribution ]                [ Negative / Left Skew ]
        Tail extends to the RIGHT                    Symmetrical Bell                    Tail extends to the LEFT
             Skewness > 0                              Skewness = 0                            Skewness < 0
```

### Official Threshold Guidelines (Slides 28 & 29)
1. **Skewness (偏度 - Asymmetry of Distribution)**:
   - **Good (Ideal Normal)**: Within **$[-1.0, +1.0]$**
   - **Acceptable Normal Range**: Within **$[-2.0, +2.0]$**
   - *Violation Rule*: If $|Skewness| > 2.0$, data is severely skewed $\implies$ **Parametric tests are invalid; use Non-Parametric tests**.
2. **Kurtosis (峰度 - Peakedness & Tail Heaviness)**:
   - **Good (Ideal Normal)**: Within **$[-2.0, +2.0]$**
   - **Acceptable Normal Range**: Within **$[-3.0, +3.0]$**
   - *Violation Rule*: If $|Kurtosis| > 3.0$, data exhibits heavy outliers or excessive peak $\implies$ **Use Non-Parametric tests**.

---

## 1.5 Parametric vs. Non-Parametric Tests Selection Matrix ⭐⭐⭐

> **Super High-Yield Exam Matrix (Slides 26 & 32)**: Direct matching between operational scenarios and their appropriate statistical test.

| Analytical Scenario | Parametric Test<br>*(Normal Distribution Holds)* | Non-Parametric Test<br>*(Normality Violated / Ordinal Data)* | Benchmark Course Example |
| :--- | :---: | :---: | :--- |
| **1. Comparing 2 related samples<br>(比较两个相关样本)** | **Paired t-Test** | **Wilcoxon signed rank test** | Testing operator performance **before and after** a training workshop. |
| **2. Comparing 2 unrelated samples vs. a variable<br>(比较两个独立样本与变量)** | **Two-Sample t-Test** | **Mann-Whitney U-test** | Comparing **Gender (Male/Female)** against **Job Satisfaction on a 1-5 Likert scale**. |
| **3. Comparing 3+ related samples with 1 variable<br>(比较三组及以上相关样本)** | **One-Way Repeated Measures ANOVA** | **Friedman test** | Employee performance across three career stages: **Role vs. Salary Level (Low, Medium, High)**. |
| **4. Comparing 3+ samples with unrelated variables<br>(比较三组及以上独立样本)** | **One-Way ANOVA** | **Kruskal-Wallis H-test** | Comparing worker productivity across independent shifts: **Assigned Project Team vs. Satisfaction Rating**. |
| **5. Comparing unrelated categories<br>(比较不相关的分类变量)** | *None (No standard parametric test)* | **Chi-square test ($\chi^2$)** | Pure categorical cross-tabulation: **Annual Bonus Awarded (Yes/No) vs. Performance Tier (High/Low)**. |
| **6. Comparing 2 independent ranks<br>(比较两组独立变量的等级/秩次)** | **Pearson correlation ($r$)** | **Spearman rank-order test ($\rho$)** | Association between a continuous metric and an ordinal ranking: **Actual Dollar Salary vs. Satisfaction Rank**. |

---

## 1.6 One-Way Analysis of Variance (ANOVA Single Factor) ⭐⭐

### 1. Why Use ANOVA Instead of Multiple Two-Sample t-Tests?
- A two-sample t-Test is restricted to comparing **exactly two groups**.
- When evaluating **three or more groups (3+ groups)**, conducting multiple pairwise t-tests causes **Type I error inflation** ($\alpha$ risk compounds across multiple comparisons). ANOVA controls the family-wise error rate by testing all group means simultaneously in an omnibus test.

### 2. Meaning of "Single Factor" (Slide 46) ⭐
- **"Single Factor" Definition**: The statistical model evaluates **only ONE independent categorical variable (Factor)**, even though that factor comprises three or more treatment groups or levels.
- **Lecture Benchmark Examples**:
  1. *Medical/Clinical*: A group of patients assigned to 3 distinct therapies (Counseling, Medication, Biofeedback).
  2. *Manufacturing*: A light bulb factory evaluating 3 different production processes (Process 1, Process 2, Process 3) to test average bulb lifespan.
  3. *Education*: Students from 3 different university colleges (College A, B, C) taking a unified standardized exam.

### 3. Hypotheses & Significance F Output
- **Hypotheses**:
  - $H_0: \mu_1 = \mu_2 = \mu_3 = \dots = \mu_k$ (All group population means are equal; no treatment effect).
  - $H_1$: At least one group mean is different from the others (Not all means are equal).
- **Key Decision Metric**: Inspect **Significance F** in the Excel ANOVA output table (equivalent to the model's overall P-value):
  $$\mathbf{\text{Significance } F < 0.05 \implies \text{Reject } H_0\ (\text{Statistically significant difference exists between groups})}$$

---

# SECTION 2: SUPPLY CHAIN PERFORMANCE, KPIS & DATA VISUALISATION (WEEK 6)

## 2.1 The Four Strategic Drivers of Supply Chain Performance Monitoring

1. **Cost Reduction (成本削减)**: Pinpoints operational redundancies, process bottlenecks, excessive handling, and non-value-adding waste.
2. **Customer Satisfaction (客户满意度提升)**: Tracks order fulfillment accuracy, on-time delivery rates, and defect-free delivery performance.
3. **Risk Mitigation (风险化解)**: Provides leading indicators to anticipate supplier stockouts, transportation disruptions, or geopolitical supply chokepoints.
4. **Supplier Relationships (深化战略伙伴关系)**: Uses objective quantitative metrics to build transparency, mutual trust, and long-term collaborative contracts.

---

## 2.2 Core SCM Key Performance Indicators (KPIs) ⭐⭐⭐

### 1. Perfect Order Measurement (POM) ⭐
Measures overall supply chain delivery precision. A delivery is "perfect" only if all four operational standards are met without error:
$$\mathbf{POM = (\% Complete) \times (\% On\text{-}time) \times (\% Damage\text{-}free) \times (\% Correctly\ invoiced)}$$
> **Mathematical Trait**: Must be calculated via **multiplication**, NOT an arithmetic average! If each metric is $95\%$, $POM = 0.95 \times 0.95 \times 0.95 \times 0.95 \approx 81.45\%$.

### 2. Cash-to-Cash Cycle Time (CCC) ⭐
The duration (in days) required for a company to convert cash outflows for raw materials into cash inflows from sales:
$$\mathbf{CCC = \text{Days Inventory Outstanding (DIO)} + \text{Days Sales Outstanding (DSO)} - \text{Days Payable Outstanding (DPO)}}$$
- **Managerial Goal**: **The shorter the CCC, the better**. Lean innovators like Dell and Amazon maintain negative CCCs, effectively operating on supplier-financed working capital.

### 3. Inventory Turnover (IT) ⭐⭐⭐ (High-Yield Problem)
Measures the velocity at which inventory is sold and replaced over a year:
$$\mathbf{Inventory\ Turnover = \frac{\text{Cost of Goods Sold (COGS)}}{\text{Value of Average Inventory}}}$$
- **Managerial Goal**: **The higher the turnover ratio, the better**, indicating efficient inventory utilization and lower capital lockup.
- **The YouRace Company Benchmark Case (Slide 11)**:
  - *2024 Baseline*: $\text{COGS} = \$3,000,000$; $\text{Average Inventory} = \$250,000$.
    $$\text{Inventory Turnover (2024)} = \frac{\$3,000,000}{\$250,000} = \mathbf{12}$$
  - *2025 Post-JIT Implementation*: Firm adopts Just-in-Time principles. Business expands to $\text{COGS} = \$4,500,000$, while average inventory rises marginally to $\$300,000$.
    $$\text{Inventory Turnover (2025)} = \frac{\$4,500,000}{\$300,000} = \mathbf{15}$$
  - *Operational Takeaway*: IT increased from 12 to 15, confirming substantial improvements in inventory velocity and working capital efficiency.

### 4. Lead Time & Freight Cost per Unit
- **Lead Time (提前期)**: Total elapsed time from purchase order placement until final goods receipt and acceptance ($\text{Time of Order Placement to Receipt}$).
- **Freight Cost per Unit Shipped (单件发运成本)**:
  $$\mathbf{Freight\ Cost\ per\ Unit = \frac{\text{Total Freight Incurred}}{\text{Total Units Shipped}}}$$

---

## 2.3 Service Supply Chains, Servitisation & Service Level Agreements (SLA) ⭐⭐

### 1. Service Chains vs. Traditional Manufacturing Chains
- **Distinct Characteristics**: Simultaneous production and consumption, non-storability (intangibility), and intensive human interaction.

### 2. Servitisation by Manufacturers (制造业服务化) ⭐
- **Definition**: Industrial manufacturers shifting from selling standalone physical hardware to bundling comprehensive, life-cycle support services (e.g., equipment financing, preventive maintenance, IoT telemetry monitoring, repair contracts).
- **Flagship Lecture Benchmark Case (Slide 14)**:
  - **Rolls-Royce**: Generates **approximately 50% of its corporate revenue from aviation services** via its "Power-by-the-Hour" engine maintenance contracts, rather than one-time jet engine hardware sales.

### 3. Service Level Agreements (SLAs) & Standard Metrics (Slide 18)
- **Definition**: A legally binding contract between a client and an external service provider detailing service performance standards, availability levels, and contractual penalties for breaches.

| Service Sector | Core SLA Contract Performance Metrics |
| :--- | :--- |
| **Call Centre / IT Outsourcing** | • **Availability Time** (system uptime, e.g., 99.9%);<br>• **Response Time** (time to answer/acknowledge tickets);<br>• **Resolution Time** (time to resolve technical issues). |
| **Logistics & Freight Services** | • **Delivery Time** (guaranteed transit window);<br>• **Allowed Damage Rate** (contractual ceiling on damaged cargo);<br>• **Penalty for Delays/Damages** (financial compensation formulas). |

---

## 2.4 The Historical Trajectory of Four Industrial Revolutions (Slide 13)

| Revolution | Approximate Era | Foundational Technologies | Structural Economic Impact |
| :---: | :---: | :--- | :--- |
| **First** | $\approx 1750 – 1850$ | Steam engine, coal power, mechanical weaving looms, iron smelting, railroads. | Shift from agrarian handcraft to **mechanized factory production**. |
| **Second** | $\approx 1870 – 1914$<br>*(Technological Revolution)* | Modern steel production, **widespread electricity**, petroleum, telephone, telegraph, internal combustion engine. | Rise of heavy chemicals and auto industries; birth of **mass production assembly lines**. |
| **Third** | $\approx 1970\text{s}$ onward<br>*(Digital Revolution)* | Microprocessors, mainframe computers, personal computing, fiber optics, the Internet. | Shift from mechanical/analog systems to **digital automation and IT data routing**. |
| **Fourth** | **Contemporary Era**<br>*(Industry 4.0)* | **Artificial Intelligence (AI)**, advanced robotics, IoT, additive manufacturing (3D printing), synthetic biology. | **Blurring the boundaries between physical, digital, and biological spheres**. |

---

## 2.5 Comprehensive Guide to the Six Core Chart Types ⭐⭐⭐

> **Critical Exam Topic**: Multiple exam questions present operational scenarios and require identifying the optimal visualization tool.

```
┌──────────────────────────────────────────────────────────────────────────────────┐
│                           The Six Core Visualizations                            │
│                                                                                  │
│   [ Column / Bar ]          [ Line Chart ]             [ Pie / Donut ]           │
│   Discrete categories       Changes over continuous    Proportions of a whole    │
│   comparison                time                       (Keep categories <= 5-7)  │
│                                                                                  │
│   [ Scatter Plot ]          [ Bubble Graph ]           [ Radar / Spider Chart ]  │
│   Correlation between two   Three numerical dimensions Multi-criteria profiling  │
│   continuous variables      (Cost, Value, Risk)        (Area = Overall value)    │
└──────────────────────────────────────────────────────────────────────────────────┘
```

### Comparative Selection Matrix for Chart Types (Slides 31–35)

| Chart Type | Primary Analytical Use | Key Operational Advantages | Inherent Limitations & Drawbacks |
| :--- | :--- | :--- | :--- |
| **Column / Bar Chart** | Comparing discrete, independent categories or groups. | Clear visual contrast across large category datasets; far superior to raw tabular text. | Fails to show continuous temporal evolution. |
| **Line Chart** | Displaying metrics across **continuous time (Changes over time / Trends)**. | Highlights temporal trends and trendline intersections; quickly exposes abrupt anomaly dips/spikes. | Requires a logically ordered horizontal axis (e.g., sequential dates, months, process steps). |
| **Pie / Donut Chart** | Displaying component **proportions of a whole (Percentages)**. | Instantly conveys proportional breakdown of a single total sum. | **Cannot exceed 5–7 slices**; cannot display negative numbers or track temporal trends. |
| **Scatter Plot** | Assessing the **linear or non-linear correlation** between two continuous variables ($X$ and $Y$). | Maps positive/negative correlation patterns; highlights isolated **data outliers**; supports trendlines. | Cannot label individual data points easily; limited to strictly two continuous dimensions. |
| **Bubble Graph** ⭐ | Displaying relationships across **three numerical dimensions** ($X$-axis, $Y$-axis, bubble size). | **Visualizes 3D data in a flat 2D plane without complex 3D charts**. Standard business tool for comparing investment options across **Cost, Value, and Risk**. | Bubble areas are difficult to read with precision; overlapping bubbles create clutter. |
| **Radar / Spider Chart** ⭐ | Comparing performance across **multiple evaluation criteria (more than 2 or 3 metrics)** simultaneously. | **The greater the area covered by the polygon, the greater the overall performance value**. Evaluates multi-dimensional balance. | Cannot cleanly display more than 2–3 entities simultaneously due to line clutter. |

---

## 2.6 Visualisation Principles & Dashboarding Architecture

### 1. Four Foundational Principles of Visualisation (Slide 26)
1. **Informative**: Delivers precise, actionable intelligence required for executive decision-making.
2. **Efficient**: Presents content cleanly and intuitively, minimizing cognitive friction and ambiguity.
3. **Appealing**: Uses balanced graphic design, typography, and color to hold executive attention.
4. **Interactive & Predictive**: Incorporates slicers, filters, and dynamic "what-if" scenario modeling.

### 2. Chart vs. Dashboard: The Storytelling Distinction (Slide 36) ⭐
- **Chart / Graph**: The visual representation of a single specific data metric $\implies$ **"A single chapter of a story"**.
- **Dashboard**: A unified visual console consolidating multiple interconnected charts and KPIs on a **single screen** $\implies$ **"All chapters coming together to tell a complete business story at a glance"**.
  - *Key Characteristics*: Customizable, interactive, real-time telemetry, consolidated single-screen layout.

---

# SECTION 3: EXAM PITFALLS & RAPID RECALL (HIGH-PROBABILITY TRAPS)

1. **Hypothesis Formulation Sign Traps**:
   - The Alternative Hypothesis ($H_1$ or $H_a$) **CAN NEVER CONTAIN AN EQUALS SIGN** ($=, \le, \ge$). Any multiple-choice option showing $H_1$ with an equals sign is mathematically incorrect.
   - The Null Hypothesis ($H_0$) **MUST ALWAYS CONTAIN AN EQUALS SIGN** ($=, \le, \ge$).
2. **P-Value & The Golden Decision Rule**:
   - $P < 0.05 \implies$ **Reject $H_0$** (Statistically significant difference detected).
   - $P \ge 0.05 \implies$ **Fail to Reject $H_0$** (Do not say *"proved $H_0$"*).
   - Remember the definition: *"P-value is the chance of your result being just a coincidence."*
3. **Normality Threshold Triggers**:
   - Skewness acceptable within **$\pm 2.0$**; Kurtosis acceptable within **$\pm 3.0$**.
   - If a question notes: *"Skewness is $+2.85$, Kurtosis is $+4.12$"* $\implies$ Normality is violated; **must choose a Non-Parametric test**!
4. **Parametric vs. Non-Parametric Trigger Matchings**:
   - 2 related samples + non-normal $\implies$ **Wilcoxon signed rank test**.
   - 2 independent samples + non-normal (e.g., Likert scale) $\implies$ **Mann-Whitney U-test**.
   - 3+ independent samples + non-normal $\implies$ **Kruskal-Wallis H-test**.
   - 3+ related samples + non-normal $\implies$ **Friedman test**.
   - Categorical cross-tabulation $\implies$ **Chi-square test ($\chi^2$)**.
5. **Chart Type Keywords**:
   - *"Three numerical dimensions"* OR *"Cost vs. Value vs. Risk"* $\implies$ **Bubble Graph**.
   - *"Multiple evaluation criteria / Area covered represents overall value"* $\implies$ **Radar / Spider Chart**.
   - *"Changes over time / Temporal trends"* $\implies$ **Line Chart**.
   - *"Correlation between two continuous variables / Spotting outliers"* $\implies$ **Scatter Plot**.
6. **KPI Calculation Traps**:
   - **POM** is **multiplicative**: $POM = \%Complete \times \%On\text{-}time \times \%Damage\text{-}free \times \%Correctly\ invoiced$. (Never calculate an arithmetic average!).
   - **CCC**: $CCC = DIO + DSO - DPO$. (Remember that DPO has a minus sign).
   - **Inventory Turnover**: $COGS / \text{Average Inventory}$. Higher is better.

---

# SECTION 4: MIDTERM SIMULATION EXAM (20 MCQS)

> **Instructions**: Read each question carefully. Select the SINGLE best answer. There is no negative marking.

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
In hypothesis testing, what is the fundamental conceptual meaning of a P-value as defined in the Week 5 lecture slides?  
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
A logistics manager wishes to test whether employee job satisfaction levels (measured on a 1-to-5 ordinal Likert scale) differ between three completely unrelated shift teams (Day shift, Swing shift, Night shift). Because the dependent variable is ordinal Likert-scaled data, which statistical test is most appropriate?  
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

# SECTION 5: ANSWER KEY & IN-DEPTH BILINGUAL EXPLANATIONS

### Question 1
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 1.1 / Week 5 Slide 5 & 6 / When do we need Diagnostic Analytics?
- **Analytical Rationale**:  
  When operational anomalies occur (e.g., a sudden 45% spike in product returns) and an analyst investigates the root causes (*"Why did it happen?"*), this falls squarely under **Diagnostic Analytics**. Descriptive analytics merely captures what occurred, while Predictive analytics models future outcomes.
- **【中文解析】**: 题干核心考点在于“突发异常激增 45%”（Anomalies）以及调查其背后的“根因”（Underlying root cause）。根据分析类型演进框架，探究“为什么会发生”（Why did it happen?）是典型的**诊断性分析（Diagnostic Analytics）**。故选 B。

### Question 2
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 1.2 / Week 5 Slide 10 / Correlation Thresholds
- **Analytical Rationale**:  
  Slide 10 establishes the official threshold bands: $|r| \ge 0.50$ is High/Strong; **$|r|$ between $0.30$ and $0.49$ is classified as "Moderate degree / medium correlation"**; $|r| < 0.29$ is Small/Low. An $r$ of $-0.42$ yields $|-0.42| = 0.42$, which falls directly into the moderate/medium category.
- **【中文解析】**: 课件第 10 页标准判定考点：相关系数绝对值在 $0.30 \sim 0.49$ 之间被官方严格划分为**中度相关（Moderate / Medium degree correlation）**。$|-0.42| = 0.42$，落在该区间内。故选 B。

### Question 3
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 1.3 / Week 5 Slide 17 & 21 / Mathematical Hypothesis Signs
- **Analytical Rationale**:  
  Slide 17 sets strict mathematical conventions: **$H_0$ must contain an equality condition ($=$, $\ge$, $\le$)**, representing the status quo baseline. **$H_1$ represents the research claim and can ONLY use directional inequality signs ($<$, $>$, $\ne$)**. Here, the research claim is that the defect rate is fewer than 50 ppm ($H_1: \mu < 50$), making the opposing null hypothesis $H_0: \mu \ge 50$.
- **【中文解析】**: 假设检验符号法则：$H_0$ 必须包含等号（$=, \le, \ge$），代表被检验的基准现状；$H_1$ 是研究者希望证实的主张，严禁包含等号（只能是 $<, >, \ne$）。本题的研究主张是缺陷率低于 50 ppm（$H_1: \mu < 50$），因此对应的零假设必为 $H_0: \mu \ge 50$。故选 B。

### Question 4
- **Correct Answer**: **C**
- **Syllabus Reference**: Section 1.3 / Week 5 Slide 24 & 39 / P-Value Decision Rule
- **Analytical Rationale**:  
  The fundamental decision rule is: **Reject $H_0$ if and only if P-value $< 0.05$**. Here, the calculated one-tail P-value is $0.082$. Because $0.082 \ge 0.05$, the sample evidence is insufficient to reject the null hypothesis. The correct statistical action is to **Fail to reject $H_0$**. Slide 39 explicitly illustrates: *"Do we have evidence? Yes. Is it strong enough? No (one-tail P-value is not smaller than 0.05)."*
- **【中文解析】**: 决策红线：当且仅当 P 值 $< 0.05$ 时，才能拒绝零假设。此处计算出的单尾 P 值为 $0.082 > 0.05$，说明虽然样本存在差异，但这种差异纯属抽样偶然巧合的概率高达 8.2%，证据不足以推翻零假设，因此必须**无法拒绝零假设（Fail to reject $H_0$）**。故选 C。

### Question 5
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 1.3 / Week 5 Slide 24 / Definition of P-Value
- **Analytical Rationale**:  
  Slide 24 verbatim states: *"P-value is the chance of your result being just a coincidence."* Statistically, it represents the probability of observing sample results at least as extreme as those measured, assuming that the null hypothesis is true.
- **【中文解析】**: 课件第 24 页原话考点：“P-value is the chance of your result being just a coincidence”（P 值就是你所观察到的样本结果纯属偶然巧合的概率）。故选 B。

### Question 6
- **Correct Answer**: **C**
- **Syllabus Reference**: Section 1.4 & 1.5 / Week 5 Slide 28, 29 & 32 / Normality Violations & Non-Parametric Selection
- **Analytical Rationale**:  
  Slides 28 & 29 state that Skewness is acceptable up to $\pm 2.0$, and Kurtosis is acceptable up to $\pm 3.0$. Here, Skewness is $+2.85$ (exceeds $2.0$) and Kurtosis is $+4.12$ (exceeds $3.0$). The data severely violates normality! Slide 32 dictates that when comparing **two unrelated/independent samples** with non-normal data, one MUST use the non-parametric **Mann-Whitney U-test** instead of a parametric two-sample t-Test.
- **【中文解析】**: 偏度阈值要求在 $\pm 2.0$ 以内，峰度要求在 $\pm 3.0$ 以内。本题偏度为 2.85，峰度为 4.12，均严重超标，属于显著非正态分布。根据课件第 32 页矩阵，比较两个独立无关样本（两个班组）且数据严重偏态时，对应的非参数检验方法必为**曼-惠特尼 U 检验（Mann-Whitney U-test）**。故选 C。

### Question 7
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 1.5 / Week 5 Slide 26 & 32 / Non-Parametric Test for Related Samples
- **Analytical Rationale**:  
  The scenario involves testing the **same group before and after** an intervention, which represents **two related/paired samples**. According to Slides 26 & 32, the parametric test is the paired t-Test; however, because normality is violated, the required non-parametric equivalent is the **Wilcoxon signed rank test**.
- **【中文解析】**: 检验“同一批叉车司机在培训前与培训后”的表现，属于经典的“两个相关/配对样本（Two related samples）”。在数据不服从正态分布的前提下，查表可知对应的非参数检验必须选用**威尔科克森符号秩检验（Wilcoxon signed rank test）**。故选 B。

### Question 8
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 1.5 / Week 5 Slide 26 & 32 / Kruskal-Wallis H-Test
- **Analytical Rationale**:  
  The scenario involves comparing **three unrelated groups** (Day, Swing, Night shifts) against an ordinal variable (1-to-5 Likert satisfaction scale). Slides 26 & 32 explicitly assign this scenario (*"Comparing three or more samples with unrelated variables / Projects vs Job satisfaction Likert scale"*) to the non-parametric **Kruskal-Wallis H-test**.
- **【中文解析】**: 比较 3 个独立无关组（三个不同班组），且被解释变量为李克特等级量表数据（序数非正态数据），根据课件第 26 与 32 页矩阵，标准非参数检验方法为**克鲁斯卡尔-沃利斯 H 检验（Kruskal-Wallis H-test）**。故选 B。

### Question 9
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 1.6 / Week 5 Slide 41 & 46 / Meaning of ANOVA Single Factor
- **Analytical Rationale**:  
  Slide 46 explicitly addresses this question: *"Why did we select single factor!?"* The reason is that there is only **one independent factor / variable** being evaluated (in this case, the Production Line), even though that single factor has three different treatment levels/lines being compared.
- **【中文解析】**: 课件第 46 页专门启发思考：“Why did we select single factor!?”。其根本原因在于分析模型中只考察**一个独立的分类自变量/因子**（即生产线），虽然这个因子包含 3 个不同水平（1线、2线、3线）。故选 B。

### Question 10
- **Correct Answer**: **C**
- **Syllabus Reference**: Section 1.6 / Week 5 Slide 41 & 45 / Significance F in ANOVA
- **Analytical Rationale**:  
  In an Excel ANOVA summary table, the primary decision metric is **Significance F**, which represents the omnibus P-value for testing whether all group means are identical. If Significance F $< 0.05$, the null hypothesis is rejected.
- **【中文解析】**: 在 Excel 输出的单因素方差分析表中，用于判定组间均值是否具有显著差异的核心统计量是 **Significance F**（其数值完全等价于方差分析模型的总 P 值）。若 Significance F $< 0.05$，则拒绝零假设。故选 C。

### Question 11
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 2.2 / Week 6 Slide 10 / POM Calculation
- **Analytical Rationale**:  
  Slide 10 specifies the exact formula:
  $$POM = (\% Complete) \times (\% On\text{-}time) \times (\% Damage\text{-}free) \times (\% Correctly\ invoiced)$$
  $$POM = 0.96 \times 0.95 \times 0.98 \times 0.99 = 0.884184 \approx 88.42\%.$$
  Note that this is multiplicative, not an arithmetic average!
- **【中文解析】**: 完美订单满足率（POM）采用各项概率连乘计算：
  $$POM = 0.96 \times 0.95 \times 0.98 \times 0.99 = 0.884184 \approx 88.42\%。$$
  千万不要算成加法平均数（97.00% 是算术平均的典型陷阱选项）！故选 B。

### Question 12
- **Correct Answer**: **C**
- **Syllabus Reference**: Section 2.2 / Week 6 Slide 10 / Cash-to-Cash Cycle Time
- **Analytical Rationale**:  
  Slide 10 defines the CCC formula:
  $$CCC = \text{Days Inventory Outstanding (DIO)} + \text{Days Sales Outstanding (DSO)} - \text{Days Payable Outstanding (DPO)}$$
  $$CCC = 45 + 30 - 50 = 25\text{ days.}$$
- **【中文解析】**: 现金周转周期公式为：
  $$CCC = \text{存货天数} + \text{应收账款天数} - \text{应付账款天数} = 45 + 30 - 50 = 25\text{ 天。}$$
  注意 DPO 前面是减号。故选 C。

### Question 13
- **Correct Answer**: **C**
- **Syllabus Reference**: Section 2.2 / Week 6 Slide 11 / The YouRace Problem
- **Analytical Rationale**:  
  Slide 11 presents the identical problem:
  - $\text{Inventory Turnover (2024)} = \frac{\$3,000,000}{\$250,000} = 12$
  - $\text{Inventory Turnover (2025)} = \frac{\$4,500,000}{\$300,000} = 15$
  The turnover ratio increased from 12 to 15. Because a higher inventory turnover indicates faster stock depletion and superior capital efficiency, inventory operational performance improved.
- **【中文解析】**: 课件第 11 页 YouRace 原题重现：
  - 2024 年周转率 $= 3,000,000 / 250,000 = 12$；
  - 2025 年周转率 $= 4,500,000 / 300,000 = 15$。  
  周转率由 12 提升至 15，周转率数值越高越好，代表 JIT 实施后库存资产运营效率显著提升。故选 C。

### Question 14
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 2.3 / Week 6 Slide 14 / Servitisation by Manufacturers
- **Analytical Rationale**:  
  Slide 14 defines Servitisation as manufacturers transitioning from selling pure hardware to bundling value-added services (maintenance, remote telemetry, financing). It explicitly cites: *"Rolls-Royce, for instance, earns around 50% of its revenue from services."*
- **【中文解析】**: 课件第 14 页原版案例！制造业服务化（Servitisation）是指制造企业从单一售卖硬件转向输出整体服务解决方案。典型代表即劳斯莱斯（Rolls-Royce）约 50% 的收入来源于航空动力飞行小时维保服务（Power-by-the-Hour）。故选 B。

### Question 15
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 2.3 / Week 6 Slide 18 / SLA Metrics in Logistics
- **Analytical Rationale**:  
  Slide 18 specifically identifies standard SLA provisions for logistics and transportation contracts: **Delivery Time, Allowed Damage Rate, and Penalty for delays or damages**. Corporate profit margins and personal taxes are completely outside the scope of operational logistics SLAs.
- **【中文解析】**: 课件第 18 页明确指出物流与运输外包 SLA 的三大核心量化考核指标：**送达交货时间（Delivery Time）、允许损坏率上限（Allowed Damage Rate）、以及因延误或残损引发的罚金条款（Penalty）**。故选 B。

### Question 16
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 2.4 / Week 6 Slide 13 / The Four Industrial Revolutions
- **Analytical Rationale**:  
  Slide 13 describes the Second Industrial Revolution ($\approx 1870–1914$, also called the Technological Revolution) characterized by steel, electricity, petroleum, telegraph, telephone, the internal combustion engine, and the rise of mass production assembly lines.
- **【中文解析】**: 课件第 13 页工业革命时间线：第二次工业革命（约 1870–1914 年，又称技术革命），其标志性技术为钢铁、电力广泛应用、石油、电话电报以及内燃机的大规模流水线生产。故选 B。

### Question 17
- **Correct Answer**: **C**
- **Syllabus Reference**: Section 2.5 / Week 6 Slide 34 / Bubble Graph
- **Analytical Rationale**:  
  Slide 34 explains: *"Bubble graphs are useful for comparing the relationships between data objects in 3 numeric-data dimensions: the x-axis data, the y-axis data, and data represented by the bubble size... often used in business to visualise the relationships between alternatives investment in dimensions such as cost, value, and risk."*
- **【中文解析】**: 课件第 34 页原话考查！气泡图（Bubble graph）专用于在二维平面上展现**三个数值维度（Three numeric dimensions）**（横轴、纵轴和气泡尺寸大小），商业中广泛用于对比投资备选方案的“成本、价值与风险”。故选 C。

### Question 18
- **Correct Answer**: **A**
- **Syllabus Reference**: Section 2.5 / Week 6 Slide 35 / Radar Chart (Spider Chart)
- **Analytical Rationale**:  
  Slide 35 defines Radar Charts: *"very useful when comparing performance/measurement results from different sources... primary way of displaying more than two or three values at once... the greater the area covered by the plot, the greater the overall value."*
- **【中文解析】**: 课件第 35 页雷达图（Radar/Spider chart）定义：用于综合对比多个不同维度的绩效指标（一次性展示 2–3 个以上指标），图表绘制覆盖的面积越大，代表综合表现越优秀。故选 A。

### Question 19
- **Correct Answer**: **A**
- **Syllabus Reference**: Section 2.6 / Week 6 Slide 36 / Chart vs. Dashboard
- **Analytical Rationale**:  
  Slide 36 establishes this exact metaphor: *"A chart, or a graph, is the display of a specific information (a chapter of a story). A dashboard is a collection of these (chapters come together to tell a story)... arranged on a single screen so the information can be monitored at a glance."*
- **【中文解析】**: 课件第 36 页经典比喻考题：图表展示的是某一具体维度的单项信息，代表“故事中的一个章节”；而仪表盘则是关联图表与 KPI 的集合，在单块屏幕上直观呈现，是将“所有章节组合起来讲述一个完整的业务故事”。故选 A。

### Question 20
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 2.5 / Week 6 Slide 33 / Scatter Plots
- **Analytical Rationale**:  
  Slide 33 notes that a Scatter Plot is particularly useful when exploring the correlation pattern between two continuous numerical variables ($X$ = Overtime hours, $Y$ = Packing errors). It visually illustrates correlation strength, linear/nonlinear relationships, and clearly highlights atypical outliers.
- **【中文解析】**: 课件第 33 页指出：散点图（Scatter plot）专门用于展现两个连续数值变量之间的相关性关系（横轴自变量，纵轴因变量），并能清晰识别异常离群点（Outliers）。故选 B。

---
*End of Part 5 & Part 6 Comprehensive Exam Review Guide (English-First Edition)*

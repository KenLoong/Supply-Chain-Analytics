# INMT5518 Supply Chain Analytics
# Comprehensive Exam Review Guide: Part 3 & Part 4 (English-First Edition)

> **Assessment Context**: Closed-Book Midterm Quiz (Week 8)  
> **Format**: Multiple Choice Questions (MCQs), Single Correct Answer, No Negative Marking.  
> **Instructional Design**: **English-First Architecture**. Academic definitions, operational frameworks, and question stems are articulated in rigorous business English (mirroring Textbook Chapter 1 and Dr. Mehdi Rajabi Asadabadi’s Week 4 slides), accompanied by targeted Chinese annotations (【考点释义 / 核心精解】) for rapid mastery.

---

# SECTION 1: SUPPLY CHAIN DRIVERS & BUSINESS STRATEGY ALIGNMENT (TEXTBOOK CH. 1)

## 1.1 Supply Chain Network Structure & Core Participants

A supply chain consists of repeating sets of organizations that coordinate actions to bring products or services to market.

```
[ Ultimate Supplier ] ──► [ Supplier ] ──► [ Manufacturer / Producer ] ──► [ Distributor / Wholesaler ] ──► [ Retailer ] ──► [ Customer ] ──► [ Ultimate Customer ]
                                                    │
                               ┌────────────────────┴───────────────────┐
                               ▼                                        ▼
                  [ Logistics Service Providers ]           [ Financial & IT Providers ]
```

### 1. The Core Participants Defined
1. **Producers / Manufacturers (生产商 / 制造商)**:
   - Organizations that make a product, encompassing producers of raw materials (mining, drilling, logging, farming) and finished goods (assembling subcomponents into finished items).
   - **Crucial Scope**: Producers do NOT only produce tangible industrial goods; they can produce **intangible items (无形产品)** (music, entertainment, software, designs) and **services (服务)** (lawn mowing, medical surgery, academic teaching).
2. **Distributors / Wholesalers (分销商 / 批发商)**:
   - Companies that take inventory in **bulk from producers** and deliver bundled product lines to business customers.
   - **Core Economic Functions**:
     - **Buffer Producers**: Cushion manufacturers from downstream demand fluctuations by holding inventory.
     - **Time and Place Function**: Deliver products when and where the customer demands them.
   - **Two Structural Forms of Distributors**:
     - *Ownership Distributors*: Take legal ownership/title of significant physical inventories, handling sales, warehousing, and transportation.
     - *Brokers*: Never take ownership; focus exclusively on matching buyers and sellers, performing product promotion and sales.
3. **Retailers (零售商)**:
   - Stock inventory and sell in smaller individual unit quantities directly to the general public. Closely track consumer preferences and draw shoppers through combinations of price, convenience, service, and product variety.
4. **Customers / Consumers (客户 / 最终消费者)**:
   - Any organization or individual that purchases and uses a product. Can be intermediate industrial consumers (incorporating components into other products) or end users.
5. **Service Providers (专业服务提供商)**:
   - Entities possessing specialized **core competencies** that perform supporting functions more efficiently than manufacturers or retailers could perform internally:
     - *Logistics Providers*: Trucking, air/ocean freight, public warehousing (3PL).
     - *Financial Providers*: Commercial lending, credit risk analysis, invoice factoring.
     - *Information Technology Providers*: ERP architecture, POS telemetry, cloud data routing.

---

## 1.2 The Five Major Supply Chain Performance Drivers ⭐⭐⭐

> Chopra and Meindl define five structural areas where managerial decisions determine the capabilities of any supply chain. Every driver requires resolving the fundamental strategic trade-off between **Responsiveness** and **Efficiency**.

```
                [ Responsiveness (速度 / 柔性 / 服务水平) ]
                                   ▲
                                   │  ◄── Strategic Trade-off (战略权衡)
                                   ▼
                  [ Efficiency (低成本 / 规模经济 / 高利用率) ]
```

### Comparative Analysis Matrix of the Five Drivers

| Driver | Core Operational Definition | Responsiveness Focus (High Service Level) | Efficiency Focus (Cost Minimization) |
| :--- | :--- | :--- | :--- |
| **1. Production<br>(生产)** | The capacity of a supply chain to make and store products through factories and warehouses. | • Build excess/idle capacity to absorb wild demand swings.<br>• Build multiple smaller facilities close to customer clusters.<br>• Adopt a **Product Focus** (facility handles all steps for a product line). | • Maintain high capacity utilization with minimal excess capacity.<br>• Centralize production in massive mega-plants to gain economies of scale.<br>• Adopt a **Functional Focus** (facility specializes in a few tasks across many products). |
| **2. Inventory<br>(库存)** | All raw materials, work in process (WIP), and finished goods spread throughout the chain. | • Hold high inventory levels across broad product varieties.<br>• Distribute stock across numerous forward stocking locations close to consumers. | • Minimize total inventory holding across all facilities.<br>• Eliminate slow-moving SKUs.<br>• Centralize inventory in a single central distribution hub. |
| **3. Location<br>(选址)** | The geographical siting of supply chain facilities and assignment of activities per site. | • **Decentralize**: Open numerous operating locations physically close to customers (e.g., **McDonald’s** deploying dense retail stores for fast customer access). | • **Centralize**: Operate from very few consolidated facilities to maximize scale economies (e.g., **Dell** servicing vast geographies from single assembly hubs). |
| **4. Transportation<br>(运输)** | Moving materials and finished products between different facilities and customer nodes. | • Utilize fast, flexible, high-cost transportation modes (Air freight, courier trucks like **FedEx/UPS** offering 24-hour delivery).<br>• Emphasized for **high-value, time-sensitive goods** (microchips, pharmaceuticals). | • Utilize slow, highly cost-efficient transportation modes (Ocean shipping, rail, pipelines).<br>• Ship in large batch quantities out of central hubs.<br>• Emphasized for **bulk commodities** (grain, coal, lumber, iron ore). |
| **5. Information<br>(信息)** | The connective tissue linking activities; collecting and sharing data across the entire chain. | • High collection and transparent sharing of accurate, real-time demand and inventory data across all partners (e.g., high-velocity electronics markets). | • Collect less data; share less information to minimize IT infrastructure spending and protect trade secrets (short-term efficient, but risks long-term obsolescence). |

---

## 1.3 Production & Warehousing Strategies

### 1. Factory Specialization: Product Focus vs. Functional Focus
- **Product Focus (产品聚焦型工厂)**:
  - Performs the complete range of manufacturing operations required to make a given product line (from component fabrication to final assembly).
  - *Advantage*: Builds deep specialized expertise regarding a specific product family.
- **Functional Focus (功能聚焦型工厂)**:
  - Concentrates on performing just a few specialized operations (e.g., only custom machining, or only surface-mount electronic soldering) across many different types of products.
  - *Advantage*: Develops technical expertise in specific functions, maximizing equipment utilization.

### 2. Three Approaches to Warehousing Operations
1. **Stock Keeping Unit (SKU) Storage (单品存储法)**:
   - Traditional warehousing: All inventory of a given product type is stored together. Highly efficient, space-maximizing, and easy to manage.
2. **Job Lot Storage (工单 / 项目组套存储法)**:
   - All different products required to satisfy the needs of a particular customer type or specific job are stored together. Enables rapid picking and packing, but requires substantially more floor space.
3. **Crossdocking (越库作业 / 交叉换线) ⭐⭐⭐**:
   - **Pioneered by Wal-Mart** to maximize velocity and eliminate inventory stagnation.
   - Products are **NOT warehoused or stored long-term** in the facility.
   - Inbound supplier trucks arrive and unload large bulk quantities. Inbound shipments are immediately broken down into smaller lots, recombined according to daily store replenishment orders, and loaded directly onto outbound store delivery trucks.

---

## 1.4 Structural Evolution: Vertical Integration to Virtual Integration

```
[ Industrial Age: Vertical Integration ]           [ Information Age: Virtual Integration ]
     (Own the entire physical chain)                    (Partner with specialized experts)
         ┌─────────────────────┐                            ┌─────────────────────┐
         │ Raw Material Mines  │                            │ Component Specialist│
         └──────────┬──────────┘                            └──────────┬──────────┘
                    ▼                                                  ▼
         ┌─────────────────────┐                            ┌─────────────────────┐
         │  Steel & Glass Mill │                            │  Core Firm (Brand)  │
         └──────────┬──────────┘                            │ Focus on Core Comps │
                    ▼                                       └──────────┬──────────┘
         ┌─────────────────────┐                                       ▼
         │   Auto Assembly     │                            ┌─────────────────────┐
         └──────────┬──────────┘                            │ 3PL Logistics Leader│
                    ▼                                       └─────────────────────┘
         ┌─────────────────────┐
         │ Railroads & Dealers │
         └─────────────────────┘
```

### 1. The Industrial Mass Market Model: Ford's River Rouge Plant
- In the early 20th century, companies operating in slow-moving mass markets pursued **Vertical Integration (纵向一体化)** to achieve maximum economies of scale.
- **Henry Ford’s River Rouge Plant (1926)**:
  - Ford owned iron ore mines, timber forests, rubber plantations, glass factories, blast furnaces, railroads, and car assembly plants.
  - *Remarkable Metric*: Ford boasted in *Today and Tomorrow* that his company could take raw iron ore from the mine and output a finished car **81 hours later**.
  - *The Failure Point*: As consumer tastes diversified, Ford's rigid vertical integration could not adapt. Henry Ford famously declared: *"They can have any color they want as long as it's black."* By the 1940s, Ford's market share plummeted from over 50% to under 20%.

### 2. The Modern Era: Virtual Integration & Core Competencies ⭐
- Driven by globalization, fierce competition, and rapid technological turnover.
- **Virtual Integration (虚拟整合)**: Companies focus strictly on their **Core Competencies (核心竞争力)** (activities they perform best) and partner with external specialists for other operations (contract manufacturing, third-party logistics, specialized distribution).

---

## 1.5 Aligning Supply Chain with Business Strategy (3-Step Framework) ⭐⭐

> A company’s supply chain must be designed to deliver the precise mix of responsiveness and efficiency demanded by its target market.

### The 3-Step Strategic Alignment Methodology
```
[ Step 1: Understand the Markets Served ] ──► Evaluate the 6 customer attributes
                  │
                  ▼
[ Step 2: Define Core Competencies ]      ──► Determine firm's role (Producer, Distributor, Service)
                  │
                  ▼
[ Step 3: Develop SC Capabilities ]       ──► Tune the 5 drivers to match required responsiveness/efficiency
```

- **Step 1: Understand the Markets Your Company Serves**:
  Evaluate the 6 customer attributes identified by Chopra and Meindl:
  1. *Quantity needed in each lot*: Small lots (convenience store) vs. large bulk lots (Sam's Club).
  2. *Response time tolerated*: Short notice / instant (fast food) vs. long lead times (custom tooling).
  3. *Variety of products needed*: Narrow, well-defined (boutique) vs. wide selection (Wal-Mart).
  4. *Service level required*: Immediate 100% fill rate vs. acceptance of backorders/partial deliveries.
  5. *Price of product*: Willing to pay premium for convenience vs. strictly lowest cost.
  6. *Desired rate of innovation*: Rapid technological churn (smartphones) vs. slow stability (house paint).
- **Step 2: Define Core Competencies of Your Company**:
  Clarify what role the company plays, how it creates differentiated value, and how it makes money.
- **Step 3: Develop Needed Supply Chain Capabilities**:
  Configure the 5 performance drivers (Production, Inventory, Location, Transportation, Information) to achieve the target operational posture.

### Classic Strategic Alignment Benchmarks
- **7-Eleven vs. Sam's Club (Wal-Mart)**:
  - **7-Eleven**: Customer seeks instant convenience, short response times, and nearby access; price is secondary. $\rightarrow$ **Supply chain optimized for RESPONSIVENESS**.
  - **Sam's Club**: Customer is highly price-conscious, willing to drive long distances and buy in bulk to obtain the absolute lowest unit cost. $\rightarrow$ **Supply chain optimized for EFFICIENCY**.
- **Wal-Mart’s Four Supply Chain Pillars**:
  1. *Expanding around Distribution Centers (DCs)*: Build a central DC first, then cluster stores around it to achieve scale economies in inventory and transport.
  2. *Electronic Data Interchange (EDI)*: Electronic linkages with suppliers automate routine ordering, cut transaction costs, and establish precise delivery scheduling.
  3. *The "Big Box" Store Format*: Combines retail showroom and warehouse in a single facility, eliminating intermediate warehouse-to-store transfer costs.
  4. *Everyday Low Prices (EDLP)*: Eliminates periodic promotions, which smoothes customer demand fluctuations and stabilizes forecasting.
- **Dell Computers (Build-to-Order & Postponement)**:
  - Assembles custom PCs only *after* customer orders are received; operates very low inventory. Shipping costs are high (air freight), but Dell avoids inventory obsolescence in a market with rapid component price deflation.

---

# SECTION 2: INVENTORY MANAGEMENT PRINCIPLES (WEEK 4 LECTURE)

## 2.1 The Nature of Inventory & The 4 Rights

### 1. Definition
- **Inventory**: Refers to goods and materials held for sale, production, or service.
- **Inventory Management**: The process of ordering, storing, tracking, and controlling a company’s inventory.
- **The "4 Rights" of Inventory Management**:
  $$\mathbf{Right\ Item,\ Right\ Quantity,\ Right\ Place,\ Right\ Time}$$

### 2. Foundational Management Maxims ⭐
- **"Inventory Hides Problems"**: High inventory levels act like water covering submerged rocks; they disguise poor supplier quality, equipment breakdowns, delivery delays, and inaccurate demand forecasts.
- **"Inventory Costs!"**: Locking capital into unsold merchandise generates storage fees, insurance, handling costs, and depreciation.
- **Opportunity Cost (机会成本)**: The financial earnings the firm forgone by locking capital into physical inventory rather than investing those funds elsewhere.
- **Sustainability Concerns (可持续性与环境风险)**:
  - *Lecture Case*: In 2018, luxury fashion brand **Burberry burned down almost \$30 million worth of unsold clothes and perfume** to preserve brand exclusivity, sparking severe public backlash over resource waste and environmental destruction.

---

## 2.2 Four Types of Inventories

```
┌────────────────────────────────────────────────────────────────────────┐
│                        Types of Inventories                            │
│                                                                        │
│   [ Raw Material ]        [ Work In Progress (WIP) ]   [ Finished Goods (FG) ]
│   Initial inputs before   Materials currently being    Completed items ready
│   processing begins.      processed but not finished.  for customer delivery.
│                                                                        │
│                    [ Maintenance, Repair & Overhaul (MRO) ]            │
│                    Supplies consumed to support facility operations    │
│                    (tools, cleaning solvents, gloves, machine oil).    │
└────────────────────────────────────────────────────────────────────────┘
```

1. **Raw Material (原材料)**: Unprocessed materials purchased from primary producers (e.g., steel coils, plastic resins, raw timber).
2. **Work In Progress - WIP (在制品)**: Materials that have entered the transformation process, undergone partial machining or assembly, but are not yet completely finished.
3. **Finished Goods - FG (产成品)**: Fully completed products that have passed quality inspection and are ready for sale, distribution, or customer pickup.
4. **Maintenance, Repair and Overhaul - MRO (维保与运营耗材)**: Operating supplies consumed in daily production and maintenance activities that do not become part of the final product (e.g., replacement machine belts, grease, safety goggles, cleaning solvents, office printer paper).

---

## 2.3 ABC Inventory Analysis (Pareto 80/20 Rule) ⭐⭐⭐

> Most firms manage far too many inventory SKUs to give equal attention to all. ABC analysis categorizes inventory items based on **Annual Dollar Expense**, ensuring management focuses rigorous control on the vital few.

```
[ Class A Items ] ──► ~65% - 80% Total Annual Expense ──► ~10% - 20% SKU Count ──► Continuous ROP System
[ Class B Items ] ──► ~15% - 25% Total Annual Expense ──► ~30% - 40% SKU Count ──► Periodic Review System
[ Class C Items ] ──►  ~5% - 15% Total Annual Expense ──► ~40% - 50% SKU Count ──► Blanket Purchase (1-2x/yr)
```

### Comprehensive ABC Analysis Breakdown Table

| Classification | Annual Expenditure Share | SKU Count Proportion | Management Policy & Control Rigor | Automotive Industry Examples (Slide 18) |
| :---: | :---: | :---: | :--- | :--- |
| **Class A** | **~65% – 80%**<br>*(Slide 17: Top 2 SKUs accounted for 65.14%)* | **~10% – 20%** | **Strict, Continuous Control**: Managed using a continuous **Reorder Point (ROP) System**. Frequent small-lot replenishment; tight safety stock monitoring. | Engine major parts, transmission systems, high-pressure fuel injection systems. |
| **Class B** | **~15% – 25%** | **~30% – 40%** | **Moderate Control**: Monitored via a less demanding **Periodic Review System** (e.g., checking stock balances weekly or monthly). | Windshield wipers, air conditioning compressors, exterior mirrors, floor mats, mudguards, roof racks. |
| **Class C** | **~5% – 15%** | **~40% – 50%** | **Simple, Minimal Control**: Purchased in bulk via **Blanket Purchase Orders** once or twice a year to minimize administrative ordering costs. | Standard screws, basic tools, work gloves, cleaning solvents, toilet tissues, printer paper, packaging tape. |

---

# SECTION 3: MATHEMATICAL INVENTORY MODELS & OPTIMIZATION

## 3.1 The Cost Trade-off: Holding Cost vs. Order Cost

Inventory optimization balances two opposing cost curves:

```
Annual Cost ($) ▲                               Total Annual Cost (TAC) Curve
                │                                           /
                │          \ (Holding Cost Line)          /
                │           \   (SS + Q/2) * H          /
                │            \      │                 /
                │             \     │               /
                │              \    │             /
                │               \   │           /
                │                \  │         /
                │─────────────────\─┼────────/─────── (Order Cost Curve)
                │                  \│       /           (D / Q) * S
                │                   │      /
                └───────────────────┴────────────────────────► Order Quantity (Q)
                                   EOQ
```

1. **Holding Cost / Carrying Cost ($H$)**:
   - The cost associated with holding inventory over time.
   - *Components*: Warehousing rent, utilities, insurance, tax, maintenance, handling, **product obsolescence (spoilage/expiration)**, and **opportunity costs of capital**.
   - **Behavior**: Increases linearly as order quantity ($Q$) and average inventory level increase.
2. **Order Cost / Setup Cost ($S$)**:
   - Fixed administrative and logistics costs incurred every time an order is placed, regardless of order size.
   - *Components*: Order processing paperwork, vendor communication, transport and delivery fees, machine setup/calibration labor, handling charges.
   - *Risk of Stockout*: Ordering too little risks stockouts, resulting in **lost sales and permanent loss of customers**.
   - **Behavior**: Decreases on an annual basis as order quantity ($Q$) increases, because fewer total orders ($\frac{D}{Q}$) are placed per year.

---

## 3.2 Economic Order Quantity (EOQ) & Total Annual Cost (TAC) ⭐⭐⭐

### 1. Variables & Definitions
- $D$ = Annual Demand (units per year)
- $S$ = Ordering or Setup Cost per order (\$/order)
- $H$ = Annual Holding Cost per unit per year (\$/unit/year)
- $Q$ = Order Quantity per batch (units)
- $SS$ = Safety Stock buffer quantity (units)

### 2. Equations & Derivation
- **Average Inventory Level**:
  $$\text{Average Inventory} = \frac{(SS + Q) + SS}{2} = SS + \frac{Q}{2}$$
- **Annual Holding Cost**:
  $$\text{Annual Holding Cost} = \left(SS + \frac{Q}{2}\right) \times H$$
- **Annual Order Processing Cost**:
  $$\text{Annual Order Processing Cost} = \left(\frac{D}{Q}\right) \times S$$
- **Total Annual Cost of Inventory (TAC)**:
  $$\mathbf{TAC = \text{Purchase Cost} + \left(SS + \frac{Q}{2}\right) \times H + \left(\frac{D}{Q}\right) \times S}$$
  $$\mathbf{TAC = (\text{Demand} \times \text{Price}) + (\text{Annual Holding Cost}) + (\text{Annual Order Cost})}$$

### 3. The EOQ Formula
The Economic Order Quantity ($EOQ$) occurs at the minimum point of the TAC curve, where **Annual Holding Cost equals Annual Ordering Cost** (setting safety stock and unit purchase cost aside as constants):
$$\frac{Q}{2} \times H = \frac{D}{Q} \times S \implies Q^2 = \frac{2DS}{H}$$
$$\mathbf{EOQ = \sqrt{\frac{2DS}{H}}}$$

---

## 3.3 Safety Stock Mechanics & The "Variation" Doctrine ⭐⭐⭐

### 1. Definition & Core Purpose
- **Safety Stock (Buffer Stock)**: The amount of inventory held to cope with uncertainty and unforeseen events arising in the supply chain (e.g., late deliveries from suppliers, sudden demand spikes, unusable poor-quality materials, unexpected production scrap).

### 2. The Simple Safety Stock Formula (Slide 34) ⭐
$$\mathbf{Safety\ Stock = (\text{Maximum use until the order arrives}) - (\text{Average use until the order arrives})}$$
$$\mathbf{SS = \text{Max Lead Time Usage} - \text{Avg Lead Time Usage}}$$

### 3. The Root Reason for Safety Stock: VARIATION ⭐⭐⭐
> **Slide 36 & 38 Definitive Doctrine**:
> *"The root reason for safety stock could be described as **VARIATION** – variation of demand, variation of lead time, variation of production rate, etc."*  
> *"**If there was no variation, firms would not need safety stock. Safety stock costs!**"*
- **The Core Rule**: Safety stock exists ONLY because of **variation and uncertainty**. If supplier lead times and daily customer demands were 100% deterministic (zero variation), **required safety stock would be mathematically ZERO**.

---

## 3.4 Inventory Reduction Principles & Practical Techniques ⭐⭐⭐

```
┌────────────────────────────────────────────────────────────────────────┐
│                     Four Core Reduction Principles                     │
│  1. Pool Inventory       Combine demand across regions/products        │
│  2. Reduce Variation     Eliminate demand, quality, & supply variance  │
│  3. Reduce Lead Time     Directly compresses pipeline stock & ROP      │
│  4. JIT Philosophy       Eliminate waste; receive goods only as needed │
└────────────────────────────────────────────────────────────────────────┘
```

### 1. Four Foundational Principles (Slide 19)
1. **Pool Inventory (库存集中化)**:
   - Combine demand from multiple physical locations (centralized warehousing), combine demand for different products (delayed differentiation), or use common subcomponents. Based on the statistical Law of Large Numbers, aggregate variance is substantially lower than the sum of independent variances.
2. **Reduce Variation (消除系统波动)**:
   - Address the root cause of safety stock directly: stabilize supplier delivery reliability, implement Six Sigma quality control, and smooth customer demand.
3. **Reduce Lead Time (缩短交货提前期)**:
   - Lead time directly scales safety stock and the Reorder Point ($ROP = d \times L + SS$). Compressing lead time reduces risk exposure and slashes in-transit inventory costs.
4. **Just-In-Time (JIT) Philosophy (准时制管理哲学)**:
   - **Slide 19 Doctrine**: *"JIT is as much a philosophy as it is a technique."* Strives for the total elimination of waste (muda) by producing and delivering goods only when needed in the exact quantity demanded.

### 2. Practical Modern Techniques for Reducing Safety Stock (Slide 39)
1. **Inventory Centralisation**:
   - Pooling regional inventories into central hubs (widespread in automotive supply chains).
2. **Delayed Product Differentiation / Principle of Postponement (延迟制造原则) ⭐**:
   - Delay the final customization of a product as late as possible until actual customer orders are secured, holding inventory upstream in generic, standardized subassembly forms.
   - **Slide 39 Case 1 (Smart TVs)**: Customizing language packs, operating system settings, and power cables is delayed to regional distribution centers or delegated to customers upon initial device setup.
   - **Slide 39 Case 2 (Sofa Manufacturing)**: The manufacturer pre-assembles uniform, standardized sofa base frames; fabric color, leather upholstery, and cushioning options are delayed until customer purchase orders arrive at the factory.
3. **Increasing Part Commonality (提高零部件通用性) ⭐**:
   - Designing products around standardized, interchangeable modular components.
   - **Slide 39 Case (EU USB-C Mandate)**: All mobile phones, tablets, and handheld electronics sold in the European Union must be equipped with standardized USB Type-C charging ports, eliminating redundant proprietary cables.
4. **Decreasing Transit Inventory (压缩在途库存)**:
   - Streamline freight transit lines; negotiate premium expedited delivery options with suppliers or carrier competitors to compress transportation lead times.

---

# SECTION 4: EXAM PITFALLS & RAPID RECALL (HIGH-PROBABILITY TRAPS)

1. **The Root Reason for Safety Stock**:
   - If an exam option cites *"high demand volumes"*, *"high transport fees"*, or *"costly purchase prices"* $\implies$ **INCORRECT**.
   - The ONLY correct root cause is **VARIATION** (demand, lead time, production, quality). If variation is zero, safety stock is ZERO.
2. **ABC Classification Criteria & Policies**:
   - **Class A**: $\approx 65\%-80\%$ of annual dollar expense, $\approx 10\%-20\%$ of SKUs $\implies$ **Strict Reorder Point (ROP) continuous tracking**.
   - **Class B**: $\approx 15\%-25\%$ of annual dollar expense, $\approx 30\%-40\%$ of SKUs $\implies$ **Periodic Review system**.
   - **Class C**: $\approx 5\%-15\%$ of annual dollar expense, $\approx 40\%-50\%$ of SKUs $\implies$ **Blanket Purchase Orders (1-2x per year)**.
3. **EOQ Cost Equality Rule**:
   - At the calculated EOQ point, **Annual Holding Cost strictly equals Annual Ordering Cost**! (If they do not equal, the order quantity is not at the optimal cost minimum).
4. **Principle of Postponement Recognition**:
   - Scenarios involving *"generic sofa bases finished later"* or *"smart TVs customized for local language post-production"* $\implies$ **Delayed Product Differentiation / Principle of Postponement**.
5. **Increasing Part Commonality Recognition**:
   - Scenarios citing the *"EU USB Type-C universal port mandate"* $\implies$ **Increasing Part Commonality**.
6. **Crossdocking Definition**:
   - Wal-Mart’s process where goods arrive in bulk, are broken down and re-sorted immediately, and loaded onto outbound trucks **without being stored long-term in the warehouse** $\implies$ **Crossdocking**.
7. **JIT Nature**:
   - Remember the exact phrasing: *"JIT is as much a philosophy as it is a technique."*

---

# SECTION 5: MIDTERM SIMULATION EXAM (20 MCQS)

> **Instructions**: Read each question carefully. Select the SINGLE best answer. There is no negative marking.

---

### Question 1
According to Chopra and Meindl’s framework in Textbook Chapter 1, what are the five major performance drivers that govern supply chain capabilities?  
A. Marketing, Accounting, Human Resources, Engineering, and Procurement  
B. Production, Inventory, Location, Transportation, and Information  
C. Suppliers, Contract Manufacturers, Distributors, Retail Showrooms, and End Consumers  
D. Raw Materials, WIP, Finished Goods, MRO, and Transit Inventory

### Question 2
A retail chain decides to serve its geographic market by opening numerous small, decentralized stores located physically close to customers (e.g., McDonald's strategy) rather than operating from a single centralized hub. In terms of the Location driver, what is the primary operational trade-off made?  
A. Sacrificing cost efficiency and scale economies to achieve high responsiveness and convenience  
B. Minimizing local property taxes while maximizing long-haul transportation lead times  
C. Eliminating all inventory carrying costs in favor of crossdocking  
D. Achieving pure operational efficiency through large-scale centralized warehousing

### Question 3
Wal-Mart pioneered a logistics technique where supplier trucks arrive at a central distribution center, unload bulk quantities of goods, and warehouse staff immediately break down, sort, and reload the goods directly onto outbound store delivery trucks without ever storing them in the warehouse. What is this technique called?  
A. Stock Keeping Unit (SKU) Storage  
B. Job Lot Storage  
C. Crossdocking  
D. Delayed Differentiation

### Question 4
In his 1926 autobiography, Henry Ford described his famous River Rouge plant, where iron ore entered one end and finished cars exited 81 hours later. Why did this extreme model of "Vertical Integration" eventually lose market dominance to flexible supply chains?  
A. Because international environmental laws prohibited auto manufacturers from operating iron ore mines.  
B. Because it could not respond flexibly to shifting consumer desires for product variety, custom styling, and new colors.  
C. Because railroad freight transport was completely replaced by air cargo.  
D. Because third-party logistics providers (3PLs) made mass production illegal.

### Question 5
When aligning a supply chain with business strategy, how does a convenience store chain like 7-Eleven fundamentally differ from a discount warehouse club like Sam’s Club?  
A. 7-Eleven’s supply chain emphasizes responsiveness because customers demand immediate convenience, whereas Sam’s Club focuses tightly on efficiency to pass bulk cost savings to price-sensitive shoppers.  
B. 7-Eleven optimizes exclusively for economies of scale, whereas Sam's Club optimizes for rapid 24-hour home delivery.  
C. 7-Eleven holds zero finished goods inventory, whereas Sam’s Club operates solely via JIT pull systems.  
D. Both companies utilize identical supply chain structures optimized exclusively for functional product manufacturing.

### Question 6
Which of the following items would be classified as Maintenance, Repair, and Overhaul (MRO) inventory in an automotive assembly plant?  
A. Stamped steel exterior doors waiting to be painted  
B. Lubricating grease, welding safety gloves, replacement drill bits, and industrial floor cleaner  
C. Completed sedans parked in the shipping yard awaiting dealership transport  
D. Raw rolls of aluminum sheet metal stored in the primary stamping bay

### Question 7
In an ABC inventory classification system, which of the following statements accurately characterizes "Class A" inventory items?  
A. They account for roughly 40%–50% of total SKUs and are managed using annual blanket purchase orders.  
B. They represent approximately 10%–20% of total inventory SKUs but account for 65%–80% of total annual inventory expenditure.  
C. They consist of inexpensive consumable items like screws, protective tape, and printer paper.  
D. They require minimal managerial oversight and are reviewed only once every two years.

### Question 8
In a manufacturing warehouse, inventory items such as major engine assemblies belong to Class A, while basic fasteners and gloves belong to Class C. According to Week 4 lecture guidelines, how should the inventory control policies differ between these classes?  
A. Class A items should be purchased once a year via blanket orders, while Class C items require strict continuous reorder point (ROP) tracking.  
B. Class A items should be controlled closely using a reorder point (ROP) system, while Class C items may be blanket purchased once or twice a year.  
C. Both Class A and Class C items must be managed with identical continuous review policies to prevent stockouts.  
D. Class A items should have zero safety stock, while Class C items must maintain 90 days of buffer inventory.

### Question 9
In the context of Economic Order Quantity (EOQ) cost trade-offs, which of the following is categorized as a component of Annual Holding (Carrying) Cost?  
A. The clerical labor cost to create and transmit a purchase order  
B. Machine recalibration and technician downtime expenses during assembly line setup  
C. The opportunity cost of capital invested in stored warehouse inventory  
D. Carrier freight shipping charges invoiced per delivery batch

### Question 10
A retail distribution hub faces an annual demand ($D$) of 16,000 units for an electronic component. The cost to place each purchase order ($S$) is \$50, and the annual holding cost per unit ($H$) is \$4. What is the Economic Order Quantity (EOQ)?  
A. 400 units  
B. 632 units  
C. 800 units  
D. 1,600 units

### Question 11
Using the data from Question 10 ($D = 16,000$, $S = \$50$, $H = \$4$), if the distribution hub orders exactly at the EOQ of 632 units, what will be the resulting Annual Holding Cost (assuming safety stock is zero) and Annual Ordering Cost?  
A. Annual Holding Cost = \$1,264; Annual Ordering Cost = \$1,266 (approximately equal at \$1,265)  
B. Annual Holding Cost = \$3,200; Annual Ordering Cost = \$800  
C. Annual Holding Cost = \$632; Annual Ordering Cost = \$2,500  
D. Annual Holding Cost = \$4,000; Annual Ordering Cost = \$4,000

### Question 12
According to Dr. Mehdi Rajabi Asadabadi’s Week 4 lecture slides, what is the single fundamental ROOT REASON why supply chain organizations maintain safety stock?  
A. High annual procurement setup costs  
B. Systemic variation (including variation in demand, lead time, production rates, and component quality)  
C. Excessively large EOQ batch sizing  
D. High carrier shipping freight rates

### Question 13
If a supply chain operated under conditions of absolute certainty—where supplier lead time was exactly 7 days with zero variance, and customer demand was exactly 50 units per day with zero variance—how much safety stock would the firm theoretically need to maintain?  
A. Exactly 350 units  
B. Exactly 175 units  
C. Exactly 50 units  
D. Zero safety stock

### Question 14
A warehouse supervisor monitors a critical imported spare part. During the supplier lead time window, the maximum historical consumption ever recorded is 920 units, while the average historical consumption during the same lead time window is 700 units. Using the simple safety stock formula presented in the lecture, what is the required safety stock?  
A. 1,620 units  
B. 220 units  
C. 700 units  
D. 110 units

### Question 15
A smart television manufacturer builds identical screen chassis and internal circuit boards at a central Asian factory. The installation of regional power plugs, localized packaging, and country-specific language operating systems is delayed until shipments reach regional distribution centers. What supply chain principle does this illustrate?  
A. Vertical Integration  
B. Delayed Product Differentiation (Principle of Postponement)  
C. Crossdocking  
D. Blanket Purchasing

### Question 16
Under the European Union mandate requiring all smartphones, tablets, and digital cameras to adopt standardized USB Type-C charging receptacles, manufacturers reduced the proliferation of proprietary charging accessories. From an inventory management perspective, which safety stock reduction principle does this illustrate?  
A. Increasing part commonality  
B. Increasing transportation lead time  
C. Eliminating cycle inventory  
D. Switching from virtual integration to functional focus

### Question 17
A furniture manufacturer pre-assembles uniform wooden base frames for sofas. Final customization (such as fabric color, leather upholstery, and cushioning) is postponed until actual retail customer purchase orders are confirmed. How does this practice optimize inventory management?  
A. It eliminates the need for any quality control inspections on raw wood.  
B. It pools component demand across diverse finished sofa styles, reducing finished goods inventory holding risk and obsolescence.  
C. It forces the company to operate strictly as a Fourth-Party Logistics (4PL) provider.  
D. It increases order processing costs by requiring daily blanket purchasing.

### Question 18
Which of the following statements regarding the Just-In-Time (JIT) concept is most accurate according to course materials?  
A. JIT is strictly an automated software algorithm used in Microsoft Excel.  
B. JIT is as much an overarching management philosophy as it is an inventory control technique.  
C. JIT advises holding 60 days of safety stock to protect against supplier delivery failures.  
D. JIT was developed by Henry Ford during the construction of the River Rouge plant.

### Question 19
In 2018, luxury fashion house Burberry incinerated unsold designer apparel and cosmetics valued at nearly \$30 million. In lecture Week 4, what broader supply chain vulnerability was this real-world event used to illustrate?  
A. The extreme risks of relying on ocean shipping instead of air freight  
B. The massive financial holding costs, obsolescence risks, and environmental sustainability concerns associated with excess inventory  
C. The complete failure of adopting standardized USB Type-C charging ports on fashion items  
D. The legal prohibition against practicing 3PL contract packaging in Europe

### Question 20
A retail company seeks to decrease its pipeline/transit inventory. Which of the following managerial actions will directly accomplish this objective?  
A. Increasing safety stock buffers in all regional retail stores  
B. Reducing supplier lead time through streamlined logistics or negotiated expedited delivery options  
C. Increasing the size of supplier batch purchase orders to capture volume discounts  
D. Switching all transport modes from express motor freight to slow marine shipping

---

# SECTION 6: ANSWER KEY & IN-DEPTH BILINGUAL EXPLANATIONS

### Question 1
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 1.2 / Textbook Chapter 1 / Five Performance Drivers
- **Analytical Rationale**:  
  Chopra and Meindl explicitly identify the five fundamental supply chain performance drivers as: **Production, Inventory, Location, Transportation, and Information**. The remaining options list functional departments, channel participants, or inventory categories.
- **【中文解析】**: 教材第 1 章明确提出决定供应链全部能力的五大性能驱动要素：生产（Production）、库存（Inventory）、选址（Location）、运输（Transportation）和信息（Information）。故选 B。

### Question 2
- **Correct Answer**: **A**
- **Syllabus Reference**: Section 1.2 / Location Driver Trade-Off
- **Analytical Rationale**:  
  Decentralizing facility locations by deploying numerous small sites physically close to customer clusters (e.g., McDonald's, 7-Eleven) maximizes customer convenience and speed of access (**responsiveness**). The operational trade-off is higher overall capital overhead and the forfeiture of centralized economies of scale (**efficiency**).
- **【中文解析】**: 选址驱动要素的核心权衡：在靠近消费者的区域开设大量分散的小网点（如麦当劳、便利店），是为了追求极高的便利度和**响应性（Responsiveness）**；其付出的战略代价是丧失了中央大仓库的规模经济和成本效率（Efficiency）。故选 A。

### Question 3
- **Correct Answer**: **C**
- **Syllabus Reference**: Section 1.3 / Warehousing Strategies & Wal-Mart Innovation
- **Analytical Rationale**:  
  **Crossdocking** was pioneered by Wal-Mart. In this operational model, goods arriving on inbound supplier trucks are unloaded, sorted, and immediately reloaded onto outbound store-bound delivery trucks without formal, long-term warehouse storage.
- **【中文解析】**: 经典概念题。货物运抵物流中心后不进行长期入库存储，而是在月台上迅速分拣打散、直接重新装上出库配送卡车，这种高效流转模式称为**越库作业（Crossdocking）**，由沃尔玛首创。故选 C。

### Question 4
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 1.4 / Historical Evolution: Vertical Integration
- **Analytical Rationale**:  
  Ford’s River Rouge plant represented extreme **Vertical Integration**. While highly cost-efficient for mass-producing identical black Model T cars, it was too rigid to adapt when 1920s consumer markets shifted toward product variety, new styling, and color diversity.
- **【中文解析】**: 福特胭脂河工厂是**纵向一体化（Vertical Integration）**的工业丰碑。它在单一黑色车型的大规模制造上做到了极致，但当市场转变为追求多元化款式与个性化时，僵化的全链重资产无法灵活调整，最终丧失了市场统治地位。故选 B。

### Question 5
- **Correct Answer**: **A**
- **Syllabus Reference**: Section 1.5 / Strategic Alignment Benchmarks
- **Analytical Rationale**:  
  7-Eleven customers prioritize immediate proximity, speed, and convenience, demanding a supply chain tuned for **responsiveness**. Sam’s Club customers seek the lowest possible bulk prices and tolerate driving long distances to a warehouse, demanding a supply chain optimized for **efficiency**.
- **【中文解析】**: 战略对齐典型案例：7-Eleven 针对即时便利需求，供应链调控偏向**响应性（Responsiveness）**；Sam's Club 针对极致价格敏感的批量采购客户，供应链调控偏向**成本效率（Efficiency）**。故选 A。

### Question 6
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 2.2 / Types of Inventories: MRO
- **Analytical Rationale**:  
  Maintenance, Repair, and Overhaul (**MRO**) inventory consists of operating supplies consumed to maintain facilities and equipment that do not physically enter the finished product. Lubricants, safety gloves, tooling bits, and floor cleaners are classic MRO items.
- **【中文解析】**: MRO（维保与运营耗材）指用于保障日常生产运转、但不直接构成产品实体的消耗物资。润滑油、劳保手套、钻头与工业清洁剂属于标准的 MRO 耗材。A 为在制品；C 为产成品；D 为原材料。故选 B。

### Question 7
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 2.3 / ABC Inventory Classification
- **Analytical Rationale**:  
  In ABC inventory analysis (derived from Pareto's 80/20 rule), **Class A items represent a small fraction of total SKUs (approx. 10%–20%) but account for the dominant share of total annual dollar expenditure (approx. 65%–80%)**. Slide 17 demonstrates that the top 2 SKUs accounted for 65.14% of total expense.
- **【中文解析】**: ABC 分类法中，A 类物资是“关键的少数”：品目数量仅占约 10%–20%，但占用的年资金消耗额高达 65%–80%。课件示例中前两个品目就占了 65.14% 的开支。故选 B。

### Question 8
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 2.3 / ABC Management Policies
- **Analytical Rationale**:  
  Slide 17 explicitly specifies the distinct management policies: *"‘A’ items may be controlled closely, using the reorder point system; the less demanding periodic system may be used for ‘B’ items; and ‘C’ items may be blanket purchased once or twice in a year."*
- **【中文解析】**: 课件原文精准考点：高货值 A 类物资必须采用**再订货点（ROP）系统**进行严格而严密的连续追踪控制；中等货值 B 类物资采用**定期检查系统**；低价值 C 类物资采用**一揽子采购协议（Blanket purchase）**每年集中采购 1–2 次。故选 B。

### Question 9
- **Correct Answer**: **C**
- **Syllabus Reference**: Section 3.1 / Holding Costs vs. Order Costs
- **Analytical Rationale**:  
  Slide 21 and 25 explicitly list the components of Holding Cost: storage, insurance, tax, maintenance, obsolescence, and **opportunity costs** (financial returns lost by tying capital up in stored inventory rather than external investments). Paperwork, machine setup, and freight charges are Order/Setup costs.
- **【中文解析】**: 持有成本（Holding Cost）包含仓储租金、保险、税金、折旧过时以及被沉淀资金所失去的**机会成本（Opportunity cost）**。A、B、D 均属于单次订货或产线换模准备成本（Order/Setup cost）。故选 C。

### Question 10
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 3.2 / EOQ Formula Calculation
- **Analytical Rationale**:  
  Applying the standard EOQ equation:
  $$EOQ = \sqrt{\frac{2DS}{H}} = \sqrt{\frac{2 \times 16,000 \times 50}{4}} = \sqrt{\frac{1,600,000}{4}} = \sqrt{400,000} \approx 632.45 \approx 632\text{ units.}$$
- **【中文解析】**: 直接代入 EOQ 经典公式：
  $$EOQ = \sqrt{\frac{2 \times 16000 \times 50}{4}} = \sqrt{400000} \approx 632.45 \approx 632\text{ 件。}$$
  故选 B。

### Question 11
- **Correct Answer**: **A**
- **Syllabus Reference**: Section 3.2 / EOQ Cost Equality
- **Analytical Rationale**:  
  - $\text{Annual Holding Cost} = \left(\frac{Q}{2}\right) \times H = \left(\frac{632.45}{2}\right) \times 4 = 316.23 \times 4 \approx \$1,264.91$.  
  - $\text{Annual Ordering Cost} = \left(\frac{D}{Q}\right) \times S = \left(\frac{16,000}{632.45}\right) \times 50 = 25.30 \times 50 \approx \$1,264.91$.  
  - *Core Principle*: At the exact EOQ, **Annual Holding Cost equals Annual Ordering Cost**!
- **【中文解析】**: 核心规律考查：在 EOQ 最优订货批量处，**年持有成本必定精确等于年订货成本**（本题计算均为约 \$1,265）。故选 A。

### Question 12
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 3.3 / Root Reason for Safety Stock
- **Analytical Rationale**:  
  Slides 36 and 38 repeatedly emphasize the core theoretical doctrine: *"The root reason for safety stock could be described as **variation** – variation of demand, variation of lead time, variation of production rate, etc. If there was no variation, firms would not need safety stock."*
- **【中文解析】**: 课件第 36 与 38 页原版结论：持有安全库存的唯一根本原因就是**系统性波动（VARIATION）**（需求波动、交期波动、生产波动、质量波动）。若系统完全无波动，企业根本不需要安全库存。故选 B。

### Question 13
- **Correct Answer**: **D**
- **Syllabus Reference**: Section 3.3 / Safety Stock Under Deterministic Conditions
- **Analytical Rationale**:  
  Safety stock exists purely to buffer against stochastic uncertainty and variation. If lead time is invariant at 7 days and daily demand is fixed at 50 units/day, lead time demand is deterministic ($7 \times 50 = 350$ units). Replenishment orders placed at an ROP of 350 units arrive precisely as the last unit is consumed. Thus, **zero safety stock** is needed.
- **【中文解析】**: 理论反思题。安全库存的唯一功能是抵御不确定性。当交期与需求均无任何波动（确定性常数）时，新订单刚好在库存消耗完毕的瞬间入库，理论所需安全库存为**零（Zero）**。故选 D。

### Question 14
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 3.3 / Simple Safety Stock Formula
- **Analytical Rationale**:  
  Applying Slide 34's simple formula:
  $$\text{Safety Stock} = (\text{Max use until order arrives}) - (\text{Avg use until order arrives})$$
  $$\text{Safety Stock} = 920 - 700 = 220\text{ units.}$$
- **【中文解析】**: 套用课件第 34 页简易安全库存公式：
  $$\text{安全库存} = \text{到货前最大消耗量} - \text{到货前平均消耗量} = 920 - 700 = 220\text{ 件。}$$
  故选 B。

### Question 15
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 3.4 / Delayed Product Differentiation (Smart TVs)
- **Analytical Rationale**:  
  Slide 39 explicitly cites smart TV manufacturing as a classic demonstration of **Delayed Product Differentiation / Principle of Postponement**: *"customising language and countries of smart TVs can be delayed (or be delegated to customers)."*
- **【中文解析】**: 课件第 39 页原版案例！智能电视在制造端保持标准化，推迟配置具体国家的语言和插头，属于典型的**推迟产品差异化 / 延迟原则（Principle of Postponement）**。故选 B。

### Question 16
- **Correct Answer**: **A**
- **Syllabus Reference**: Section 3.4 / Increasing Part Commonality
- **Analytical Rationale**:  
  Slide 39 presents this exact real-world regulation under *"Increasing Part commonality"*: *"Example: All mobile phones, tablets and cameras sold in the EU have to be equipped with a USB Type-C charging port."* Standardizing modular components pools component demand and reduces inventory SKU variety.
- **【中文解析】**: 课件第 39 页原版例证！欧盟强制要求所有电子数码设备采用统一的 USB-C 充电接口，属于**提高零部件通用性（Increasing part commonality）**，减少专用异型备件库存。故选 A。

### Question 17
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 3.4 / Postponement: Sofa Manufacturing
- **Analytical Rationale**:  
  Slide 39 notes that pre-assembling uniform wooden base frames for sofas allows the firm to delay upholstery and color customization. This practice **pools component demand** across diverse finished styles and avoids holding excessive, slow-moving finished couches in unique fabric combinations that risk obsolescence.
- **【中文解析】**: 课件沙发制造案例：提前组装通用的沙发底座木框架，将面料软包等个性化工艺推迟到客户下单后执行，核心效益在于**汇总通用部件需求，大幅降低个性化成品沙发的持有贬值风险**。故选 B。

### Question 18
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 3.4 / JIT Philosophy
- **Analytical Rationale**:  
  Slide 19 emphasizes: *"Just-in-time inventory (JIT) philosophy: JIT is as much a philosophy as it is a technique."* JIT focuses on eliminating non-value-adding waste and minimizing buffer stock. It was pioneered by Taiichi Ohno at Toyota, not Henry Ford.
- **【中文解析】**: 课件第 19 页核心论断：“准时制库存（JIT）既是一套运作技术，更是一种管理哲学（as much a philosophy as it is a technique）”。它追求零库存和彻底消除浪费，由丰田开创。故选 B。

### Question 19
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 2.1 / Sustainability & Inventory Holding Costs
- **Analytical Rationale**:  
  Slide 23 cites the 2018 Burberry incineration of \$30m in unsold goods under the heading *"Sustainability Concerns"*. It illustrates the immense holding costs, rapid product obsolescence, and catastrophic environmental consequences of holding excess physical inventory in fashion markets with shifting consumer tastes.
- **【中文解析】**: 课件第 23 页引用 2018 年 Burberry 焚烧近 3,000 万美元未售库存的真实案例，旨在说明：库存积压不仅带来沉重的持有成本和报废贬值风险，更引发了严重的**资源浪费与环境可持续性（Sustainability Concerns）**危机。故选 B。

### Question 20
- **Correct Answer**: **B**
- **Syllabus Reference**: Section 3.4 / Decreasing Transit Inventory
- **Analytical Rationale**:  
  Transit (pipeline) inventory is calculated as: $\text{Transit Inventory} = \text{Demand rate} \times \text{Lead Time}$. Therefore, the most direct managerial method to reduce transit inventory is to **reduce transportation lead time** through route optimization, streamlined carrier handoffs, or negotiated expedited shipping options.
- **【中文解析】**: 在途库存（Transit Inventory）与运输提前期（Lead Time）成正比。通过优化物流链路、压缩中转停滞、协商紧急直发来**缩短交期提前期**，能最直接有效地削减在途库存。故选 B。

---
*End of Part 3 & Part 4 Comprehensive Exam Review Guide (English-First Edition)*

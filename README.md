# 📊 TeddyWorld — Revenue Contribution Analysis via Pareto Principle (80/20)

> 🌐 **Portfolio Case Study:** [View full Case Study & Inventory Caveats →](https://aominhtam-portfolio.vercel.app/projects/pareto-revenue.html)

An e-commerce revenue concentration case study exploring product sales using the **Maven Fuzzy Factory ("TeddyWorld" simulated scenario)** dataset (**32,313 orders**, Mar 2012 – Mar 2015, USD). Applies the **Pareto Principle (80/20 Rule)** after deducting item refunds to identify core revenue-driving SKUs and dependency risks.

---

## 📦 Dataset & Scope

* **Project Type:** Personal Project / Simulated Business Case (*"TeddyWorld"*)
* **Dataset Source:** Maven Fuzzy Factory Teaching Dataset (`orders`, `order_items`, `order_item_refunds`, `products`)
* **Scale & Range:** `32,313` orders &bull; Mar 2012 – Mar 2015 (3 Years) &bull; USD ($)
* **Metric Definitions:** `Net Revenue = Gross Revenue (price_usd) - Refunds`; `Gross Margin = price_usd - cogs_usd`. *(No inventory storage or warehouse holding-cost columns exist in this dataset.)*

---

## 🎯 1. Business Context & Objectives

* **Business Context:** TeddyWorld retails a wide range of plush toys and gift accessories. Management needed to assess portfolio revenue concentration to optimize marketing budget allocation and warehouse stock policies.
* **Core Objectives:**
  * Calculate accurate Net Revenue after refunds (*Net Revenue = Gross Revenue - Refunds*).
  * Determine the cumulative revenue contribution per SKU.
  * Segment products based on Pareto thresholds (Top 80% Core vs. Bottom 20% Tail).
  * Deliver actionable strategic recommendations for inventory management and sales operations.

---

## 🛠️ 2. Tech Stack & Tools

* **Language:** Python 3.x
* **Key Libraries:**
  * `pandas` / `numpy`: Data wrangling, table merges, and cumulative sum (`cumsum`) computations.
  * `matplotlib` / `seaborn`: Dual-axis Pareto chart visualization (Bar chart for sales + cumulative percentage line).
* **Environment:** Jupyter Notebook

---

## 📈 3. Key Findings & Pareto Analysis

### Cumulative Revenue Contribution Breakdown

| Rank | Product Name | Units Sold | Net Revenue ($) | Share (%) | Cumulative (%) | Pareto Segment |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| **1** | The Original Mr. Fuzzy | 15,200 | 485,000 | 45.2% | 45.2% | **Top 80% (Core)** |
| **2** | Forever Bear | 8,400 | 268,800 | 25.1% | 70.3% | **Top 80% (Core)** |
| **3** | The Birthday Sugar Panda | 3,900 | 124,800 | 11.6% | 81.9% | **Top 80% (Core)** |
| **4** | The Hudson River Mini bear | 3,100 | 99,200 | 9.3% | 91.2% | **Bottom 20% (Tail)** |
| **...** | Other Accessories & SKUs | ... | ... | ... | 100.0% | **Bottom 20% (Tail)** |

> **80/20 Rule Verified:** Just **3 core products** account for **~82% of total net revenue**, validating a heavy concentration in top-performing items.

---

## 💡 4. Business Insights & Engineering Notes

* **Portfolio Dependency Risk:** The business relies excessively on a single SKU (*The Original Mr. Fuzzy* at >45% revenue). Any supply chain disruption or quality issue with this SKU poses a severe risk to cash flow.
* **Underperforming Long Tail (Inventory Caveat):** Tail SKUs contribute a small share of net revenue and gross margin (`price_usd - cogs_usd`); because the dataset contains no warehouse-holding or storage-cost data, these items are flagged for assortment/margin review rather than assumed storage waste.
* **Technical Considerations:**
  * Refund records must be subtracted prior to grouping to prevent gross revenue inflation.
  * Data must be strictly sorted in descending order (`sort_values(ascending=False)`) before computing `.cumsum()` for cumulative percentage curves.

---

## 🚀 5. Proposed Inventory & Ad-Spend Experiments

1. **Prioritized Safety Stocks:** Implement tighter safety-stock buffers and supplier lead-time monitoring for the Top 3 SKUs (~82% net revenue share) to reduce stockout exposure.
2. **Tail-SKU Bundling:** Test pairing low-velocity accessories with high-traffic plush items to accelerate tail SKU turnover without margin-eroding clearance cuts.
3. **Hypothesis — Paid Ad Weighting (70–80%):** Test allocating 70–80% of paid acquisition spend toward Top 3 revenue drivers while monitoring marginal **Incremental ROAS** and **Inventory Turnover** so tail-SKU discovery is not starved.

---

## ⚙️ 6. How to Reproduce

1. Clone the repository:
   ```bash
   git clone https://github.com/AOMINHTAM/pareto-revenue-analysis.git
   cd pareto-revenue-analysis
   ```

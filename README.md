# 📊 TeddyWorld — Revenue Contribution Analysis via Pareto Principle (80/20)

An end-to-end data analysis project exploring product revenue contribution using the **TeddyWorld** e-commerce dataset (32,000+ orders). This analysis applies the **Pareto Principle (80/20 Rule)** to identify the "vital few" revenue-generating SKUs, evaluate product dependency risks, and provide data-driven inventory and marketing recommendations.

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
* **Underperforming Long Tail:** Lower-tier SKUs consume catalog space and inventory holding costs while contributing minimal revenue margin.
* **Technical Considerations:**
  * Refund records must be subtracted prior to grouping to prevent gross revenue inflation.
  * Data must be strictly sorted in descending order (`sort_values(ascending=False)`) before computing `.cumsum()` for cumulative percentage curves.

---

## 🚀 5. Actionable Recommendations

1. **Prioritized Inventory Control:** Implement high safety stock thresholds and strict lead-time monitoring for the Top 3 SKUs (*Mr. Fuzzy, Forever Bear, Sugar Panda*) to eliminate stockouts during seasonal demand peaks.
2. **Product Bundling Strategy:** Package low-velocity accessories with top-performing plush toys to accelerate inventory turnover for tail items.
3. **Paid Marketing Allocation:** Allocate 70–80% of digital acquisition budget exclusively to the Top 3 conversion drivers to maximize Return on Ad Spend (ROAS).

---

## ⚙️ 6. How to Reproduce

1. Clone the repository:
   ```bash
   git clone [https://github.com/AOMINHTAM/pareto-revenue-analysis.git](https://github.com/AOMINHTAM/pareto-revenue-analysis.git)
   cd pareto-revenue-analysis

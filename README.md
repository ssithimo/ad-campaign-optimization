# 📢 Ad Campaign Budget Optimization - SALS Marketing Inc.
>*With an $800K budget and 11 media options, equal splitting leaves 
> money on the table. Here's how much.*
---

## 📊 Project Overview: Max Exposure – Ad Campaign Optimization

SALS Marketing Inc. was hired to craft a data-driven advertising strategy 📈 for a major consumer goods company. The goal? To **maximize exposure** across multiple media channels—**Magazines**, **Newspapers**, **Television**, and **Radio**—while staying within a strict budget 💰 and meeting category-specific constraints.

Each ad type has a known **cost per unit** and **exposure rating**, and the company wants to know: *how should we spend our money to reach the most people possible?*

Using **Mixed Integer Linear Programming (MILP)** via CVXPY in Python, 
the optimal media mix was identified and benchmarked against a naive 
equal-split baseline to quantify the business value of optimization.

---

## 🎯 Key Constraints:
- Total campaign budget: **$800,000**
- Spend **at least $100K** and **no more than $300K** in each media category
- Must buy **whole units only** (no fractional ads)

---

## 📊 Methodology
- Defined 11 decision variables across 4 media categories and subcategories
- Formulated objective function to maximize total exposure via dot product 
  of decision variables and exposure ratings
- Applied budget, category floor/ceiling, non-negativity, and integer 
  constraints using CVXPY
- Solved using GLPK_MI solver
- Benchmarked optimized result against naive equal-split baseline to 
  quantify improvement
- Visualized cost allocation, exposure by channel, exposure efficiency, 
  and budget distribution

---

## ✅ Results:

### Optimal Media Mix

| Ad Type | Units | Cost | Impressions |
|---------|-------|------|-------------|
| News Magazines | 10 | $100,000 | 225,000 |
| Evening Newspaper | 98 | $294,000 | 7,350,000 |
| Mid-Day TV | 30 | $300,000 | 5,400,000 |
| A.M. Radio | 7 | $105,000 | 1,260,000 |
| **Total** | | **$799,000** | **14,235,000** |

7 of 11 subcategories were excluded — the optimizer zeroed out any 
channel whose exposure-per-dollar ratio couldn't compete within the 
budget structure.

### Optimization vs. Naive Baseline

| Approach | Total Impressions | Total Spend |
|----------|------------------|-------------|
| Naive equal-split ($200K/category) | 11,340,000 impressions | $793,000 |
| MILP optimized | 14,235,000 impressions | $799,000 |
| **Improvement** | **+25.53%** | **same budget** |

---

## 🔍 Key Insights

**Evening Newspaper dominates** — at 25.0 exposure per dollar 
(75,000 exposure / $3,000 per unit), it delivers the highest return 
of any channel and accounts for 51.6% of total impressions despite 
consuming only 36.8% of the budget.

**Mid-Day TV is the second highest performer** — 18.0 exposure per 
dollar (180,000 / $10,000), consuming the full $300K TV category cap.

**Magazine and Radio floors were binding constraints** — both categories 
were allocated at or near the $100K minimum, meaning they were purchased 
only to satisfy the diversity requirement, not because they offered 
competitive returns. Relaxing these floors would allow the optimizer to 
reallocate toward higher-return channels.

**Budget is highly concentrated** — TV and Evening Newspaper together 
consumed 74.3% of total spend, reflecting the optimizer's tendency to 
concentrate on the highest-return channels within constraints.

**Within-category dominance is clear** — in every category, one 
subcategory had a significantly higher exposure-per-dollar ratio and 
captured the entire category budget:
- Magazines → News Magazines (2.25/dollar)
- Newspapers → Evening Newspaper (25.0/dollar)
- Television → Mid-Day TV (18.0/dollar)
- Radio → Morning Radio (12.0/dollar)

---

## 📁 Files
- `notebook/ad_campaign_optimization.ipynb` — Full analysis: problem 
  formulation, MILP solution, naive baseline comparison, and visualizations
- `executive_summary_sals_ad_campaign.pdf` — One-page non-technical summary 
  for stakeholders

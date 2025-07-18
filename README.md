# ad-campaign-optimization
Maximize advertising exposure using mixed integer linear programming (MILP) with integer constraints across magazines, newspapers, TV, and radio under a fixed budget

## 📊 Project Overview: Max Exposure – Ad Campaign Optimization

SALS Marketing Inc. was hired to craft a data-driven advertising strategy 📈 for a major consumer goods company. The goal? To **maximize exposure** across multiple media channels—**Magazines**, **Newspapers**, **Television**, and **Radio**—while staying within a strict budget 💰 and meeting category-specific constraints.

Each ad type has a known **cost per unit** and **exposure rating**, and the company wants to know: *how should we spend our money to reach the most people possible?*

Using **Mixed Integer Linear Programming (MILP)** with **CVXPY** 🧮 in Python, we solved this as an optimization problem.

### 🎯 Key Constraints:
- Total campaign budget: **$800,000**
- Spend **at least $100K** and **no more than $300K** in each media category
- Must buy **whole units only** (no fractional ads)

### ✅ Results:
- **Total exposure achieved**: **14,235,000** 👀 
- **Total cost **: **$799,000** 💵 
- Campaign focuses on high-return channels like **Evening Newspapers** 🗞️, **Mid-Day TV** 📺, and **Morning Radio** 📻

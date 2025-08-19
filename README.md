# FoodHub Data Analysis (PGP‑AIML) — Exploratory Study & Business Insights

## Abstract
This repository contains a rigorous exploratory data analysis (EDA) of **FoodHub**, a food‑ordering aggregator operating in New York. The objective is to translate raw order‑level data into decision‑grade insights on customer demand, cuisine/restaurant performance, service timeliness, and monetizable levers (promotions, staffing, and feedback loops). The analysis is fully reproducible and organized for peer review and extension.

## Problem Statement
FoodHub’s rapid growth has created operational questions that require an evidence‑based answer set:
1) **Demand shape:** When, what, and from whom do customers order?  
2) **Service performance:** How fast is food prepared and delivered; what are the outliers?  
3) **Customer satisfaction:** What do ratings reveal (and where are the blind spots)?  
4) **Revenue levers:** Which pricing/commission thresholds and partnerships drive margin?

## Dataset
- **Observational unit:** One row per order.  
- **Rows & columns:** 1,898 orders, 9 variables.  
- **Schema:**  
  - `order_id` *(int)*, `customer_id` *(int)*  
  - `restaurant_name` *(str)*, `cuisine_type` *(str)*  
  - `cost_of_the_order` *(float)*, `day_of_the_week` *(str)*  
  - `rating` *(str/float)*, `food_preparation_time` *(int)*, `delivery_time` *(int)*  
- **Integrity:** No missing values detected.  
- **Context note:** Ratings include a “Not given” category; these are coerced to `NaN` for numeric analyses.

## Methods
- **Environment:** Python 3.10+, Jupyter Notebook.  
- **Libraries:** `pandas`, `numpy`, `matplotlib`, `seaborn`.  
- **Data preparation:** dtype checks, missing‑value audit; `rating` coerced to numeric (`errors='coerce'`) to handle “Not given”.  
- **EDA:** Univariate (histograms/count plots), bivariate (grouped means, scatter), and correlation heatmap among `cost_of_the_order`, `rating`, `food_preparation_time`, `delivery_time`.  
- **Business framing:** Each figure is paired with an explicit managerial interpretation to keep analyses decision‑oriented.

## Key Questions & Findings (Executive Summary)
- **When do people order?** Orders concentrate on **weekends (~70%)**, indicating lifestyle‑driven peaks and a predictable capacity crunch.  
- **What do they order?** **American** is the dominant cuisine; **Japanese/Italian** follow. **Vietnamese/Spanish/Korean** are niche.  
- **Where do they order from?** **Shake Shack** leads by order count; other frequent venues include **The Meatball Shop**, **Blue Ribbon Sushi**, **Blue Ribbon Fried Chicken**, **Joe’s Pizza**.  
- **How fast is service?** Typical **prep** 20–35 min; **delivery** mean ≈ **24.2 min**. Only **~2%** of orders exceed **60 min** total (prep + delivery).  
- **What do ratings say?** Five‑star ratings dominate among provided ratings, but **~39%** of orders are **unrated**; this is a major feedback blind spot.  
- **Elasticities/correlations:** **No strong correlation** between cost/prep/delivery and rating; operational consistency appears high across price bands.

> **Commission model (illustrative):** With 25% on orders > $20 and 15% on $5–$20, net revenue computed on the dataset is **$7,183.50**.

## Business Recommendations
1. **Weekend ops surge plan:** Add rider/kitchen capacity and micro‑batch dispatching on Fri‑Sun to trim the ~3‑minute weekend delivery delta.  
2. **Feedback coverage:** App nudges and small incentives to lift rating coverage; target +20–30 pp improvement to de‑bias satisfaction analytics.  
3. **Partnerships:** Deepen co‑marketing with top restaurants/cuisines; negotiate service‑level guarantees in exchange for placement.  
4. **Portfolio growth:** Time‑boxed promos for niche cuisines (bundles, discovery banners) to broaden basket diversity.  
5. **Outlier control:** Real‑time monitoring to flag prep+delivery > P95 with root‑cause categorization (kitchen, routing, surge, item mix).

## Reproducibility
### Quickstart
```bash
# 1) Create & activate a virtual environment
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate

# 2) Install dependencies
pip install -r requirements.txt

# 3) Launch Jupyter
jupyter notebook
```

Open `notebooks/FoodHub_Analysis.ipynb` and run all cells. Place `data/foodhub_order.csv` in the `data/` folder (see structure below).

### Repository Structure
```
foodhub-analysis/
├─ notebooks/
│  └─ FoodHub_Analysis.ipynb
├─ data/
│  └─ foodhub_order.csv         # not tracked in git if large/sensitive
├─ reports/
│  └─ figures/                  # auto-saved plots (optional)
├─ src/                         # utility modules (optional)
├─ requirements.txt
├─ .gitignore
└─ README.md
```

## How to Cite
If you use this analysis or structure, please cite as:
> Sadhasivam, S. (2025). *FoodHub Data Analysis (PGP‑AIML): Exploratory Study & Business Insights*. GitHub Repository.

## License
This project is released under the **UAT Austin License**).

## Acknowledgements
- PGP‑AIML coursework context.  
- Thanks to instructors/peers for feedback on EDA best practices.

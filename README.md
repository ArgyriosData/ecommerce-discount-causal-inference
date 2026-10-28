# E-commerce Discount Causal Inference

## Project Overview

How do discounts affect purchase probability, and do some customers respond more strongly than others?

This project applies causal machine learning to synthetic e-commerce customer data to estimate the effect of a 10% discount on purchase probability and explore how the estimated effect varies across customers with different levels of purchase intent.

## Business Objectives

- Estimate the effect of a 10% discount compared with no discount.
- Explore differences in estimated treatment effects across purchase-intent groups.
- Compare observed purchase rates with model-based causal effect estimates.
- Discuss how causal inference can support discount strategies and what additional validation is required.

## Dataset

The dataset contains 10,000 synthetic customer records, including:

- Previous orders
- Basket value
- Days since last order
- Website visits
- Purchase intent
- Discount percentage
- Purchase outcome

The `purchase_intent` feature represents an underlying propensity to purchase, conceptually informed by historical customer behaviour. It is synthetically generated rather than calculated from actual browsing or purchase history.

## Methodology

The analysis uses Python and `CausalForestDML` from EconML.

The workflow includes:

1. Data quality checks and exploratory analysis.
2. Examination of discount assignment and customer characteristics.
3. Definition of the outcome, treatment, and customer features.
4. A 70/30 train-test split.
5. Estimation of treatment effects for a 10% discount versus no discount.
6. Exploration of treatment effect heterogeneity across purchase-intent groups.
7. Comparison of observed purchase rates and interpretation of the results.

## Key Findings

### Observed Purchase Rates

| Group | Customers | Purchases | Purchase rate |
|---|---:|---:|---:|
| No discount | 4,501 | 598 | 13.29% |
| Discount of 10% or more | 5,035 | 1,883 | 37.40% |

The observed purchase-rate difference is **24.11 percentage points**. However, this is an unadjusted observational comparison, not a causal estimate.

### Estimated Effect of a 10% Discount

The causal forest estimates an average increase in purchase probability of approximately **7.18 percentage points** for a 10% discount versus no discount among customers in the test set.

### Treatment Effect Heterogeneity

The estimated effects vary across purchase-intent groups:

| Purchase-intent group | Estimated effect |
|---|---:|
| Low | +5.34 percentage points |
| Medium | +7.34 percentage points |
| High | +8.80 percentage points |

These exploratory estimates suggest that discount responsiveness may differ across customer groups.

## Business Implications

Causal effect estimates can help businesses investigate whether discounts influence customers differently, rather than relying exclusively on overall purchase rates.

Before using such estimates to guide real-world campaigns, businesses should validate the findings through controlled experiments and assess profitability, including discount costs and product margins.

## Limitations

- The dataset is synthetic and does not represent actual customer behaviour.
- Discount assignment is not random, so unobserved confounding may remain.
- Treatment effects are model estimates and should not be interpreted as confirmed real-world causal impacts.
- Purchase probability alone does not establish whether a discount increases profit.
- Differences across customer groups are exploratory and require further validation.

## Tools and Technologies

- Python
- Pandas and NumPy
- Matplotlib and Seaborn
- Scikit-learn
- EconML
- Jupyter Notebook

## Repository Contents

- `ecommerce_discount_causal_inference.ipynb` — data exploration, causal modelling, results, and business interpretation.
- `ecommerce_discount_data.csv` — synthetic dataset used in the analysis.

## Disclaimer

This project is for educational and portfolio purposes. The data and findings are synthetic and should not be used to make real-world business decisions.

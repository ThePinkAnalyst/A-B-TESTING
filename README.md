# A/B Testing Analysis: SmartAd Online Advertising Experiment

## Project Overview
This project evaluates the effectiveness of a **creative online advertisement (SmartAd)** compared to a **dummy ad** using a controlled **A/B experiment**. The objective is to determine whether exposure to the SmartAd increases user engagement, measured through responses to a Brand Impact (BIO) questionnaire.

The analysis applies **statistical hypothesis testing**, **confidence intervals**, and **logistic regression** to quantify both the statistical and business impact of the advertisement.

## Business Problem
Marketing teams must ensure that advertising spend leads to measurable engagement.  
This project answers the key question:

> **Does exposure to a creative SmartAd lead to higher user engagement compared to a dummy ad?**

## Experiment Design
- **Control group:** Users shown a dummy advertisement  
- **Treatment group:** Users shown the SmartAd creative  
- **Outcome variable:** User response to the BIO questionnaire  
  - `Yes` → Positive response (conversion)
  - `No` → Negative response
- **Non-responders:** Users who saw the questionnaire but did not respond

The core analysis focuses on **users who responded**, enabling a fair comparison of engagement outcomes.

## Dataset Description
The dataset was sourced from Kaggle and contains impression-level data from an online advertising experiment.

- `auction_id` - Unique impression identifier 
- `experiment` - Experiment group (`control` or `exposed`) 
- `date` - Date of exposure (YYYY-MM-DD) 
- `hour` - Hour of exposure (HH) 
- `device_make` - User device type 
- `platform_os` - Operating system identifier 
- `browser` - Browser used 
- `yes` - 1 if user answered "Yes" 
- `no` - 1 if user answered "No" 

## Methodology

### 1. Data Preparation
- Removed duplicate impressions
- Created a response indicator to separate responders from non-responders
- Engineered a binary conversion variable (`Yes = 1`, `No = 0`)
- Filtered analysis to include responding users only


### 2. Exploratory Data Analysis
- Verified sample balance between control and exposed groups
- Compared baseline response rates
- Visualized conversion rates across experiment groups


### 3. Hypothesis Testing
**Null Hypothesis (H₀):**  
The SmartAd has no effect on the response rate.

**Alternative Hypothesis (H₁):**  
The SmartAd increases the response rate.

Statistical tests applied:
- Two-proportion z-test
- Chi-square test of independence
- 95% confidence interval for uplift


### 4. Regression Analysis
A logistic regression model was used to:
- Estimate treatment effect size
- Control for time-of-day exposure
- Validate robustness of experimental results


### 5. Segment Analysis
- Evaluated ad performance across top device types
- Identified user segments with higher responsiveness to the SmartAd


## Key Results
 - Control response rate - Baseline
 - Exposed response rate - Higher than control
 - Absolute uplift - Statistically significant
 - Relative uplift - Meaningful improvement
 - P-value - < 0.05
 - Confidence interval - Excludes zero 

**Key Insight:**  
Users exposed to the SmartAd were **significantly more likely** to respond positively than users shown the dummy ad.


## Business Interpretation
- The SmartAd demonstrates both **statistical significance** and **practical impact**
- Results are consistent across multiple statistical techniques
- Certain devices show stronger treatment effects, enabling targeted optimization

## Recommendations
- Deploy the SmartAd to high-performing user segments
- Run follow-up experiments to evaluate:
  - Long-term engagement
  - Creative fatigue
  - Personalized advertising strategies
- Integrate additional downstream metrics (e.g., conversions or revenue)

## Limitations
- Analysis focuses on responding users only
- Dataset lacks revenue or purchase conversion metrics
- External factors such as ad placement and user intent are not captured

## Tools & Technologies
- Python
- Pandas & NumPy
- SciPy & Statsmodels
- Matplotlib & Seaborn



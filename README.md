# Detecting Gaming Behavior in Promotional Offers
### Fraud Analytics Simulation Inspired by American Express Sentinel Analytics

This project simulates a promotional offers environment and applies data science techniques to detect potential gaming or misuse behavior, similar to the American Express Sentinel Analytics team’s approach. The analysis identifies customers who may be repeatedly exploiting offers through abnormal redemption or account activity.

## Project Objective
To build a classification model that detects users potentially exploiting promotional campaigns. The project uses simulated behavioral data to identify anomalies such as high offer redemption rates, low time between redemptions, and multiple accounts from the same device.

## Dataset Overview
- Records: 10,000 simulated customer accounts  
- Fraud rate: 7 percent (labeled as `fraud_flag = 1`)  
- Key variables:
  - `num_offers_redeemed`: Number of offers used by the customer  
  - `avg_days_between_redemptions`: Average interval between redemptions  
  - `avg_spend_per_offer`: Average spend per redeemed offer  
  - `distinct_offer_types_used`: Variety of offers redeemed  
  - `num_accounts_same_device`: Accounts linked to a single device  
  - `referrals_count`: Number of account referrals  
  - `signup_day_index`: Simulated signup date  
  - `fraud_flag`: Target label indicating gaming behavior  

## Tools and Methods
| Tool | Purpose |
|------|----------|
| Python (Pandas, NumPy, Matplotlib) | Data simulation, cleaning, and exploratory analysis |
| scikit-learn | Modeling and evaluation (Logistic Regression, Random Forest) |
| SQL (conceptually) | Data querying and aggregation for behavioral features |
| Jupyter Notebook | Workflow documentation and presentation |

## Key Analytical Steps

### 1. Data Simulation
A realistic dataset was generated with 10,000 users and engineered to include both normal and fraudulent behavioral patterns. Fraudulent users were designed to:
- Redeem offers more frequently
- Have shorter redemption intervals
- Use multiple accounts on the same device

### 2. Exploratory Data Analysis
Boxplots and correlation analysis highlighted significant behavioral differences between legitimate and fraudulent users:
- Fraudulent users showed redemption counts three to five times higher than average.
- Time between redemptions was notably shorter.
- A positive correlation existed between the number of accounts per device and fraudulent behavior.

### 3. Modeling and Evaluation
Two supervised learning models were built and compared:

| Model | ROC-AUC | Notable Characteristics |
|--------|----------|------------------------|
| Logistic Regression | Approximately 0.85 | Good baseline performance and interpretability |
| Random Forest | Approximately 0.92 | Captured nonlinear relationships and feature interactions |

Evaluation metrics included the ROC-AUC curve, confusion matrix, and classification report. Random Forest achieved higher accuracy and balanced recall, indicating superior fraud detection capability.

### 4. Feature Importance
The Random Forest model identified the following as top predictors of gaming behavior:
1. Number of accounts on the same device  
2. Number of offers redeemed  
3. Average days between redemptions  
4. Referrals count  
5. Average spend per offer  

These variables collectively capture the frequency, diversity, and behavioral cadence of customer activity.

## Business Interpretation
The model detected users exhibiting patterns consistent with offer exploitation. Key findings:
- Fraudulent users often create multiple accounts to redeem identical offers repeatedly.
- Detection thresholds (e.g., probability > 0.8) can be used for internal flagging and manual review.
- Proactive identification could reduce marketing losses by preventing repeated redemptions and protecting campaign ROI.

## Business Impact
Using this type of model in production could:
- Save significant promotional costs by curbing misuse.  
- Strengthen customer targeting for legitimate offers.  
- Enhance Amex’s Sentinel Analytics framework by adding behavioral indicators to fraud monitoring systems.

## Key Takeaways
- Behavioral analytics and classification models can effectively detect offer gaming.  
- Nonlinear models like Random Forest outperform simple baselines in identifying subtle fraud patterns.  
- Real-world expansion could integrate device fingerprinting, IP clustering, and transaction-level validation.  
- This framework aligns directly with the fraud detection and offer protection objectives of American Express’s analytics teams.

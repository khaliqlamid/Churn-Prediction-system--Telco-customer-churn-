# Churn-Prediction-system--Telco-customer-churn-
Churn analysis and prediction model identifying high risk customers and optimizing retention strategy decisions.

## Project Overview
Customer churn is a major challenge in the telecommunications industry.  
This project analyzes customer behavior data to:

- Identify key drivers of churn
- Build a predictive model to estimate churn risk
- Provide actionable business recommendations to reduce customer loss

The final solution includes exploratory analysis, model comparison, threshold optimization and business focused insights.

---

## Dataset

**Telco Customer Churn Dataset**

- 7,043 customers
- 21 original features
- Target variable: `Churn` (0 = Stayed, 1 = Churned)

Features include:
- Demographics (SeniorCitizen, Partner, Dependents)
- Service details (InternetService, TechSupport, Streaming)
- Contract type
- Payment method
- Monthly & Total charges
- Tenure

---

##  Key Business Insights

### Strongest Drivers of Churn

1. **Contract Type**
   - Month to month customers: 43% churn
   - Two year contract customers: 3% churn
   → Contract length is the strongest churn driver.

2. **Internet Service**
   - Fiber optic users: 42% churn
   → Potential dissatisfaction or pricing issues.

3. **Payment Method**
   - Electronic check users: 45% churn
   - 78% of electronic check users are month to month
   → Auto pay adoption may reduce churn.

4. **Tenure**
   - Churned customers average: 18 months
   - Non churned customers average: 38 months
   → Early life retention is critical.

5. **Add on Services**
   - TechSupport and OnlineSecurity significantly reduce churn risk.

---

## Modeling Approach

### Baseline Model: Logistic Regression
Chosen for:
- Interpretability
- Strong baseline performance
- Clear coefficient insights

### Model Comparison
- Logistic Regression
- Random Forest

Logistic Regression performed better overall.

---

##  Model Performance

**Logistic Regression Results**

- Accuracy: 82%
- ROC-AUC: 0.86 (strong separation ability)
- Default Recall (threshold 0.50): 60%
- Optimized Recall (threshold 0.40): 70%

Threshold tuning improved churn detection by catching more high risk customers while maintaining reasonable precision.

---

## Business Recommendations

1. **Convert Month to Month Customers**
   - Offer incentives to move customers to 1 year or 2 year contracts.

2. **Improve Fiber Optic Retention**
   - Investigate pricing or service quality issues.
   - Offer support and security bundles.

3. **Encourage Auto Pay Adoption**
   - Target electronic check users with auto payment incentives.

4. **Focus on Early Tenure Customers**
   - Provide onboarding support within first 12–18 months.

5. **Bundle Value Added Services**
   - Promote TechSupport and OnlineSecurity for high risk customers.

---

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib / Seaborn (EDA)
- Jupyter Notebook

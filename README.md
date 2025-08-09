# TikTok Video Classification Project

## Overview

This project focuses on analyzing TikTok video data to build machine learning models that classify videos as either **claims** or **opinions**. The ultimate goal is to help TikTok efficiently prioritize videos for human moderation by automating the identification of potentially problematic content.

---

## Project Workflow and Phases

### 1. Exploratory Data Analysis (EDA)

**Purpose:**  
- Understand the TikTok dataset structure, key features, and engagement metrics.  
- Detect data quality issues such as missing values and duplicates.  
- Analyze class balance between videos labeled as claims or opinions.

**Key Insights:**  
- Dataset contains ~19,000 videos with nearly equal claims and opinions.  
- Claim videos generally have higher views, likes, and shares.  
- Videos by banned authors receive notably higher engagement.  
- Engagement rates vary by claim status and author ban status.

---

### 2. Data Visualization and Further Exploration

**Purpose:**  
- Conduct deeper data exploration and cleaning.  
- Create professional visualizations to support data storytelling for diverse audiences.  
- Examine distributions, outliers, and relationships between variables (e.g., verified status, author bans, engagement).

**Key Insights:**  
- Many engagement variables are right-skewed due to viral videos.  
- Verified users tend to post more opinions than claims.  
- Author ban status strongly correlates with engagement and claim likelihood.  
- Outlier detection is important for downstream modeling.  
- Visual accessibility is considered for inclusive reporting.

---

### 3. Statistical Analysis and Hypothesis Testing

**Purpose:**  
- Use inferential statistics to test hypotheses about verified and unverified users’ engagement differences.  
- Conduct two-sample t-tests comparing average views across account types.

**Findings:**  
- Statistically significant difference exists between verified and unverified accounts regarding video views.  
- Suggests behavioral or content strategy differences warranting further exploration.  
- Supports refinement of feature selection for predictive modeling.

---

### 4. Regression Modeling (Predicting Verified Status)

**Purpose:**  
- Build logistic regression models to predict whether a TikTok user is verified based on video and author features.  
- Handle class imbalance via upsampling.  
- Interpret model coefficients for business insights.

**Key Outcomes:**  
- Video duration positively associated with verified status.  
- Model shows moderate precision (~61%) and high recall (~84%).  
- Informs feature selection for subsequent claim vs opinion classification.

---

### 5. Machine Learning Classification (Claims vs Opinions)

**Purpose:**  
- Build and tune machine learning models (Random Forest, XGBoost) to classify videos as claims or opinions.  
- Prioritize recall to minimize false negatives (missing claim videos).  
- Engineer features including transcription text length and n-gram counts.

**Workflow:**  
- Clean and encode data; split into train/validation/test sets.  
- Tune hyperparameters using GridSearchCV focusing on recall metric.  
- Evaluate models using classification reports and confusion matrices.

**Results:**  
- Both models performed well; Random Forest slightly outperformed XGBoost on recall and precision.  
- Feature importance highlights engagement metrics (views, likes, shares) as strongest predictors.  
- Champion model recommended for production deployment with monitoring for bias and drift.

---

## Recommendations and Next Steps

- Deploy the Random Forest model to automate initial claims/opinions classification.  
- Consider adding features such as number of user reports per video and author-level report aggregates.  
- Monitor model performance over time and retrain as data distributions evolve.  
- Continue to improve visualization and reporting tools for stakeholder communication.

---

## Tools and Technologies Used

- **Languages & Libraries:** Python (pandas, numpy, matplotlib, seaborn, scikit-learn, xgboost), Tableau  
- **Techniques:** EDA, visualization, statistical hypothesis testing, logistic regression, Random Forest, XGBoost, GridSearchCV hyperparameter tuning  
- **Data:** TikTok video metadata and transcription text  

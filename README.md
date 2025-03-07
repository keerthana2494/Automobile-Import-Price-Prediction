# Automobile-Import-Price-Prediction

# **Business Case: Automobile Import Price Prediction**

## **1. Business Problem**
### **1.1 Overview**
Automobile importers and manufacturers face challenges in accurately predicting vehicle prices due to various influencing factors such as brand reputation, technical specifications, and market trends. A well-built price prediction model can help optimize pricing strategies, enhance inventory planning, and improve customer satisfaction.

### **1.2 Objectives**
- Identify key factors that impact automobile prices.
- Develop a predictive model to estimate car prices based on various attributes.
- Provide actionable insights for business decisions regarding pricing and product positioning.

## **2. Data Analysis and Key Insights**

### **2.1 Data Cleaning & Preprocessing**
- **Handling Missing Values:**
  - Missing values were detected in `normalized_losses`, `num_of_doors`, `bore`, `stroke`, `horsepower`, and `peak_rpm`.
  - Imputation techniques (mean/mode) were applied to maintain data consistency.
- **Data Type Adjustments:**
  - Some numerical features were incorrectly stored as object types and were converted to appropriate numerical formats.

### **2.2 Exploratory Data Analysis (EDA)**
#### **Categorical Features**
1. **Make:** Toyota is the most common brand, while Mercury appears only once.
2. **Fuel Type:** 90% of cars use gasoline, while only 10% use diesel.
3. **Aspiration:** Most cars use standard aspiration, with some turbocharged variants.
4. **Number of Doors:** Majority of cars have four doors.
5. **Body Style:** Sedans are the most frequent, followed by hatchbacks.
6. **Drive Wheels:** 60% use front-wheel drive, 36% rear-wheel drive, and 5% four-wheel drive.
7. **Engine Location:** Almost all cars have front engines, with only a few exceptions.
8. **Engine Type:** 'ohc' is the most common engine type.
9. **Number of Cylinders:** Most cars have four cylinders.
10. **Fuel System:** MPFI is the most widely used fuel system.

#### **Numerical Feature Insights**
1. **Right-Skewed Distributions:** `engine_size`, `horsepower`, and `price` required transformation.
2. **Correlation with Price:**
   - **Strong Positive Correlation:** `length`, `width`, `curb_weight`, `engine_size`, `horsepower`.
   - **Moderate Positive Correlation:** `wheel_base`.
   - **Negative Correlation:** `city_mpg`, `highway_mpg` (higher fuel efficiency correlates with lower prices).
   - **Weak or No Correlation:** `symboling`, `peak_rpm`, `stroke`, `bore`, `compression_ratio`.

### **2.3 Business Insights**
- **Luxury & Performance Cars:** Higher prices correlate with rear-wheel drive, turbocharged engines, larger engine sizes, and higher horsepower.
- **Economy Cars:** Lower prices are associated with front-wheel drive, lower horsepower, and better fuel efficiency.

## **3. Predictive Modeling**

### **3.1 Data Preparation**
- Selected features with strong correlations to price.
- Applied one-hot encoding for categorical variables.
- Normalized numerical features for improved model performance.

### **3.2 Model Selection & Performance**
The following machine learning models were tested:

#### **1. Linear Regression**
- **R² Score:** 0.7086
- Simple and interpretable model but lacks robustness for complex relationships.

#### **2. K-Nearest Neighbors (KNN)**
- **R² Score:** 0.7328
- Performs well for non-linear data but is sensitive to parameter tuning.

#### **3. Support Vector Regression (SVR)**
- **R² Score:** 0.5503
- Struggled due to non-linearity and high dimensionality in the dataset.

#### **4. Decision Tree**
- **R² Score:** 0.8309
- Captures non-linear patterns well but prone to overfitting.

#### **5. Random Forest (Best Model)**
- **R² Score:** 0.9702
- Excellent performance due to ensembling and feature selection.

#### **6. XGBoost**
- **R² Score:** 0.8592
- Strong predictive capability with better generalization compared to Decision Tree.

### **3.3 Best Model Selection**
- **Random Forest performed the best** with an **R² score of 0.9702**, explaining 97% of the variance in car prices.
- Decision Tree and XGBoost also performed well.
- SVR had the lowest performance due to non-linearity challenges.

### **3.4 Challenges Faced in Data and Techniques**
#### **Data Quality and Preprocessing**
- Handling missing values, outliers, and inconsistent formats was a key challenge.

#### **Feature Engineering**
- Meaningful feature extraction and selection were crucial to improving model performance.

#### **Categorical Variables**
- Encoding categorical columns like `engine-type`, `fuel-type`, etc., was necessary for machine learning models.

### **3.5 Model Evaluation & Overfitting Check**
- **Training Data Performance:**
  - **MSE:** 648030.59
  - **MAE:** 541.28
  - **R² Score:** 0.9702
- The high R² score suggests strong model performance, but cross-validation is necessary for generalization.

### **3.6 Business Implications**
- **Key Price Determinants:** Engine size, horsepower, curb weight, and fuel efficiency significantly impact price.
- **Strategic Recommendations:**
  - **Luxury Segment:** Focus on high-performance features like larger engines and turbocharging.
  - **Budget Segment:** Prioritize fuel efficiency and cost-effective materials.
  - **Sports Cars:** Consider turbocharged, mid-engine designs.
  - **Sedans & Hatchbacks:** Maintain stable pricing strategies.

## **4. Business Value & Conclusion**
- The model provides **data-driven pricing insights** for automobile imports.
- Analysis helps optimize pricing strategies, inventory planning, and market positioning.
- **Random Forest is the recommended model**, achieving **97% accuracy**.
- The results support **better decision-making for automobile pricing and competitiveness**.

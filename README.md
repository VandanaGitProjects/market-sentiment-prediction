# Market Sentiment and Trading Behaviour

## 📌 Project Overview
This project investigates how market sentiment (Fear, Greed, Neutral, Extreme Greed) influences trader behavior.  
Daily trading metrics were analyzed statistically and modeled to evaluate sentiment's effect on activity and performance.  
The goal was to assess whether trading behavior can be used to predict sentiment categories.

---

## 📂 Dataset
- **Historical Trading Data**: 211,224 records with account-level trading metrics.  
- **Fear & Greed Index**: 2,644 records with sentiment classification and values.  
- **Merged Dataset**: Combined account-day trading activity with sentiment labels.  
- **Key Features Used**:
  - `total_pnl` (daily profit/loss)  
  - `win_rate` (ratio of profitable trades)  
  - `med_leverage` (median leverage used)  
  - `trades` (number of trades per day)  

---

## 🛠️ Tools and Methods Used
- **Python Libraries**: `pandas`, `numpy`, `matplotlib`, `seaborn` for data handling and visualization.  
- **Statistical Analysis**: ANOVA test to check if trading metrics differ significantly across sentiment categories.  
- **Machine Learning**: `RandomForestClassifier` for sentiment prediction.  
- **Data Balancing**: SMOTE oversampling to handle class imbalance.  
- **Evaluation Metrics**: Accuracy, Precision, Recall, and F1-score.  
- **Cross-Validation**: 5-fold Stratified Cross-Validation for stable evaluation.  
- **Hyperparameter Tuning**: GridSearchCV to optimize Random Forest parameters.  

---

## 📊 Exploratory Data Analysis (EDA)
- **PnL Distribution**: Fear days showed high volatility in profits/losses, while Greed days were steadier.  
- **Leverage**: Traders used higher leverage on Greed days, indicating riskier behavior.  
- **Win Rate**: Highest win rates observed on Fear days, lowest on Neutral days.  
- **Trading Activity**: Fear days had the highest number of trades; Neutral days had the lowest.  

---

## 📈 Statistical Testing (ANOVA)
- **Daily PnL**: No significant difference across sentiments.  
- **Win Rate**: No significant difference.  
- **Median Leverage**: No significant difference.  
- **Number of Trades**: Statistically significant difference (p < 0.05).  
  - Traders change activity levels with sentiment shifts, but profitability and leverage remain unaffected.  

---

## 🤖 Model Building & Results

### Baseline Model
- **Classifier**: RandomForest (default parameters).  
- **Accuracy**: ~58% (test set).  
- **Cross-Validation Mean Accuracy**: ~66.5% (Std ~0.097).  
- **Performance**: Extreme Greed and Neutral recognized better; Fear and Greed weaker.  

### Tuned Model (GridSearchCV)
- **Best Parameters**: `n_estimators=200, max_depth=None, min_samples_split=2`.  
- **Accuracy**: ~57% (test set).  
- **Cross-Validation Mean Accuracy**: ~68% (Std ~0.097).  
- **Performance**: Similar class distribution — Extreme Greed and Neutral stronger, Fear and Greed weaker.  

---

## 📑 Result Comparison

| Model Type        | Test Accuracy | CV Mean Accuracy | Std Deviation |
|-------------------|---------------|------------------|---------------|
| Baseline (default)| ~0.58         | ~0.665           | ~0.097        |
| Tuned (GridSearch)| ~0.57         | ~0.680           | ~0.097        |

**Interpretation:**  
Hyperparameter tuning improved cross-validation accuracy slightly, but test accuracy did not improve compared to the baseline.  
This suggests challenges in generalization with limited data.

---

## 🔑 Key Insights
- Sentiment can be **partially predicted** from trading behavior.  
- Extreme Greed and Neutral classes are easier to classify, while Fear and Greed remain difficult.  
- Tuning improved CV accuracy but not test accuracy, indicating possible overfitting/generalization issues.  

---

## 🚀 Future Work
- Expand dataset size and incorporate richer trading features (e.g., volatility, position size, account history).  
- Explore alternative algorithms (e.g., Gradient Boosting, XGBoost, Neural Networks).  
- Apply advanced tuning strategies and feature engineering for stronger predictive performance.  
- Investigate temporal patterns (time-series modeling) to capture sentiment shifts more effectively.  

---

## 📌 Conclusion
This assignment demonstrates the feasibility of sentiment prediction using trading metrics.  
While accuracy remains moderate, the workflow — from EDA and statistical testing to ML modeling and tuning — provides a strong foundation for future research.  
The project highlights that **sentiment influences trading activity levels more than profitability or leverage**, and predictive modeling requires richer data for stronger results.

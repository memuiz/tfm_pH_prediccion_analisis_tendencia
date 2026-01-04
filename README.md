# pH Prediction for Water Masses in the Balearic Sea and Ocean Acidification Trend Analysis

Climate change is one of the greatest environmental challenges today, with direct effects on both terrestrial and aquatic ecosystems. Among these effects is ocean acidification (OA), a consequence of atmospheric CO₂ absorption by the oceans. Ocean acidification has the potential to disrupt marine ecosystems, lowering water pH levels and affecting biodiversity and human activities that rely on ocean resources.

This project focuses on reconstructing pH time series in the Balearic Sea and estimating ocean acidification rates by water mass in the region using machine learning techniques. The goal is to reduce uncertainty regarding the effects of climate change on the Western Mediterranean. The analysis is based on pH data collected between 2023 and 2024 and relevant oceanographic variables available through the SOCIB (Coastal Ocean Observation and Prediction System of the Balearic Islands) open-access database.

## 📋 Project Overview

🎯 **Research Focus**

- Using unsupervised machine learning for clustering of water masses
-  Using machine learning to model and predict pH levels to reconstruct pH time series in the Balearic Sea
- Estimating ocean acidification rates by water mass

🌍 **Study Location**

- Balearic Sea (Western Mediterranean): The project focuses on ocean acidification in this region, where the marine ecosystems and local fisheries are vulnerable to changes in pH.

# 🔬 Scientific Methodology

🧠 **Data Processing**

- SOCIB Data Processing: Cleaning and exploring oceanographic data from the SOCIB database.
- pH Data Processing: Preprocessing pH measurements, identifying and removing anomalies.

 📊 **Key Variables**

- Latitude/Longitude: The geographic position
-  Campaign/date/season/day of year: Time-related identifiers
- Depth: The depth at which the sample was taken
- Water Temperature: The temperature of the water at the sampling point.
- Chlorophyll Concentration: The concentration of chlorophyll in the water.
- Dissolved Oxygen Concentration: The amount of oxygen dissolved in the water.
- Salinity: The salinity of the water.

🧑‍💻 **Clustering of Water Masses**

- Unsupervised Learning: Applied clustering techniques (GMM) to classify water masses in the Balearic Sea: MAW (Mixed Atlantic Water), LIW (Levantine Intermediate Water) and WDMW (Western Mediterranean Deep Water).
- Geometric method to further detect WIW (West Intermediate Water)
- Interactive Visualizations: Interactive HTML plots of water mass classifications.

🤖 **Machine Learning for pH Prediction**

- Model Comparison: Testing different machine learning algorithms, including linear models, decision trees, and ensemble models.
- Robust Validation: Validation strategies to account for spatial and temporal variability such as Leave-One-Group-Out to prevent data leakage
- Stacked Model: Using a base model for predictions and stacking a prediction model for the residuals to avoid overstimation/understimation
- Interpretability: Using methods such as feature importance, SHAP, partial dependence and ICE plots to understand model predictions.
- Final Prediction: Applying depth-based subsampling due to the large number of samples to ensure all water masses are properly represented.


## Cross-Validation Strategy


| 🎯 **LOGO Validation** | 🧠 **Model Training** | 📊 **Performance Analysis** |
|-----------------------------|-----------------------|----------------------------|
| • 6-Fold Splits      | • Hyperparameter Optimization | • RMSE Optimization        |
| • Alows Prediction Performance Per Campaign  | • Huber Loss  | • Best Model Selection     |
| • Prevents Data Leakage      | • Avoid Overfitting   | • Interpretability   |
| • Realistic Evaluation     | • Stacked Residual Model        | • Campaign by Campaign Analysis Of RMSE And R^2|

  

📈 **Trend Analysis**

- Time Series Decomposition: Decomposing pH time series by water mass, analyzing seasonal trends and estimating long-term acidification rates.

# 📁 Code and project structure

```markdown
tfm_pH_prediccion_analisis_tendencia/
├── 📝 README.md                                # Project documentation
├── 📄 requirements.txt                         # Dependencies list
├── 🗂️ Preprocesado                         # Notebooks for data preprocessing and merging
├── 🗂️ Clustering masas de agua                   # Notebook for water mass clustering (classification of water masses with GMM and geometric method)
      └── 🗂️htmls interactivos                  #  HTML visualizations of the results
├── 🗂️ Prediccion pH                           # Notebook for pH prediction using ML, validation and interpretability
├──  🗂️ Analisis tendencia                          # Notebook for time series decomposition and trend analysis
```

## Preprocessing

- 1. **SOCIB Data Exploration and Preprocessing**: Processing of SOCIB data, removal of anomalous values, and quality control.
- 2. **pH Data Exploration and Preprocessing**: Processing of pH data, removal of anomalous values, and value exploration.
- 3. **Dataset Merging**: Merging both datasets using Euclidean distance matching. Creation of a complete database.
- 4. **Full Dataset Processing and Exploration**: Processing the complete dataset, removal of anomalous values, and exploration of variables.

## Water Mass Clustering

- 5. **Water Mass Classification**: Application of unsupervised learning techniques for classifying sampling points into water masses present in the Balearic Sea region (GMM technique and geometric method).
- **Interactive HTML Visualizations**: Interactive plots with the results of the water mass classification: MAW, LIW, WIW, and WDMW. Mixed points are intermediate points whose probability of belonging to the clusters does not exceed the set threshold (water mixing points).

## pH Prediction

- 6. **Machine Learning Methods**: Comparison of machine learning methods for predicting pH values. Validation and interpretability of the selected model.

## Trend Analysis

- 7. **Trend Analysis**: Decomposition of the reconstructed time series for each water mass and analysis of the linear trend.
     
# 💻 Installation & Setup

```markdown
# 🐍 Create Environment
python -m venv pHpred_env
pHpred_env\Scripts\activate # Windows
#source pHpred_env/bin/activate # Linux/Mac

# 📦 Install Dependencies through requirements.txt
pip install -r requirements.txt

# 📦 Or install Dependencies directly
# Data processing libraries
!pip install pandas==2.2.2 numpy==2.0.2
# Visualization libraries
!pip install seaborn==0.13.2 matplotlib==3.10.0 plotly==5.24.1
# Machine learning and optimization libraries
!pip install scikit-learn==1.6.1 scipy==1.16.3 xgboost==3.1.2
# Oceanography calculations library
!pip install gsw==3.6.20
# Interpretability library
!pip install shap==0.50.0
```


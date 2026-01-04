# Display Prediction Project - Data Analysis

## Project Overview

This project focuses on predicting the **Display** status of products in retail stores using supervised machine learning models. The target variable (Y) indicates whether a product was displayed in-store, and the prediction is based on various sales and store characteristics (X1-X7).

**Target Variable:** `Display` (Y)
- Values: `No_Displ` (Not Displayed) or `Displ` (Displayed)

## Dataset Description

### Data Source
- **File:** `new_Base_CDM_balanced_V2.csv`
- **Format:** CSV (semicolon-separated)
- **Size:** ~25,782 rows × 8 columns
- **Note:** The dataset is balanced (approximately 50/50 split between classes)

### Variables

#### Target Variable
- **Y (Display):** Binary classification target
  - `No_Displ`: Product was not displayed
  - `Displ`: Product was displayed

#### Continuous Variables (X1, X2, X3, X4, X6)
- **X1 (cor_sales_in_vol):** Corrected sales in volume (quantity/units sold)
- **X2 (cor_sales_in_val):** Corrected sales in value (revenue in euros)
- **X3 (CA_mag):** Store revenue/turnover (Chiffre d'Affaires du magasin)
- **X4 (value):** Product price/value per unit
- **X6 (VenteConv):** Conversion sales (promotional/agreed sales)

#### Nominal Variables (X5, X7)
- **X5 (ENSEIGNE):** Store chain/brand name (e.g., CORA, LECLERC, CARREFOUR, AUCHAN, CASINO, etc.)
- **X7 (Feature):** Promotional status (`No_Feat` or `Feat`)

### Important Notes
- **Different Units:** The continuous variables are not in the same unit:
  - X1: Quantity/Units
  - X2, X3, X4: Currency (euros) - but at different scales
  - X6: Unknown (could be units or currency)
- **Data Preprocessing:** The CSV file contains a descriptive label row (row 2) that should be skipped when reading the data

## Project Objectives

According to the project requirements, the goal is to:

1. **Explore at least 5 supervised learning models** from the following list:
   - Logistic Regression (Logit)
   - Linear Discriminant Analysis (ADL/LDA)
   - Decision Tree (rpart)
   - Random Forest (randomForest)
   - Neural Network (keras)
   - Gradient Boosting Machine (xgboost)
   - Support Vector Machine (SVM)

2. **Use at least 2 approaches** based on a Datamart with nominal explanatory variables:
   - Apply intelligent discretization (MDLPC - Minimum Description Length Principle for Discretization) to continuous variables
   - Create categorical features from continuous variables

## Project Structure

```
DataAnalysisProject/
│
├── Data/
│   └── raw/
│       └── new_Base_CDM_balanced_V2.csv    # Original dataset
│
├── src/
│   └── scripts/
│       └── data_analysis.ipynb              # Data exploration and analysis notebook
│
└── README.md                                 # This file
```

## Data Analysis Components

The analysis notebook includes:

1. **Data Loading and Exploration**
   - Loading data (skipping descriptive label row)
   - Data type conversion (continuous variables to numeric)
   - Basic statistics and missing values check

2. **Data Balancing Analysis**
   - Class distribution visualization
   - Imbalance ratio calculation
   - Bar charts and pie charts

3. **Correlation Analysis**
   - Correlation matrix for continuous variables
   - Heatmap visualization

4. **Distribution Analysis**
   - Distribution of Y over continuous variables
   - Box plots and histograms (with flexible binning)
   - Statistical tests (t-test, Mann-Whitney U test)

5. **Scatter Plot Analysis**
   - Pairwise scatter plots of continuous variables
   - Points colored by target variable (Y)
   - Visual assessment of class separation

6. **Nominal Variable Analysis**
   - Confusion matrices for nominal features vs Y
   - Chi-square tests of independence
   - Cross-tabulation tables

## Requirements

### Software
- **Python 3.7+** (or R)
- **Jupyter Notebook** (for Python) or RStudio (for R)

### Python Packages
```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy jupyter
```

### R Packages (if using R)
```r
# Required packages
install.packages(c("MASS", "rpart", "randomForest", "e1071", "xgboost"))
# For neural networks
install.packages("keras")
```

## Usage Instructions

### For Python Users

1. **Open the Jupyter Notebook:**
   ```bash
   jupyter notebook src/scripts/data_analysis.ipynb
   ```

2. **Run the cells sequentially:**
   - Cell 1: Import libraries
   - Cell 2: Load and explore data
   - Cell 3: Data balancing analysis
   - Cell 4: Correlation analysis
   - Cell 5: Distribution analysis
   - Cell 6: Scatter plot analysis
   - Cell 7: Nominal variable analysis

3. **Important:** Ensure the CSV file path is correct in the data loading cell. Update the path if needed:
   ```python
   df = pd.read_csv('Data/raw/new_Base_CDM_balanced_V2.csv', sep=';', skiprows=[1])
   ```

### For R Users

Create R scripts following the same analysis steps, using the appropriate R packages mentioned above.

## Key Findings from Exploratory Analysis

- **Dataset Balance:** The dataset is well-balanced (~50/50 split between classes)
- **Unit Variations:** Continuous variables have different units and scales, requiring standardization/normalization for some models
- **Variable Relationships:** Strong correlations exist between some continuous variables (e.g., X1 and X2, X1 and X6)
- **Class Separation:** Some variables show clear differences between displayed and non-displayed products

## Deliverables

### 1. PowerPoint Presentation
The presentation should include:
- **Input:** Description of data transformations and formatting
- **Model:** Brief description of each model, parameter roles, and fitting procedures
- **Output:** Comments on results for each model
- **Comparison:** Comparison of different models

### 2. Code (R or Python)
- Fully commented code for each step
- Clear documentation of data preprocessing
- Model implementation and evaluation
- Reproducible analysis

## Next Steps

1. **Data Preprocessing:**
   - Standardize/normalize continuous variables (for distance-based models)
   - Encode nominal variables appropriately
   - Apply MDLPC discretization for nominal feature approaches

2. **Model Implementation:**
   - Split data into training and testing sets
   - Implement at least 5 supervised learning models
   - Tune hyperparameters appropriately
   - Evaluate model performance

3. **Evaluation:**
   - Use appropriate metrics (accuracy, precision, recall, F1-score, ROC-AUC)
   - Compare model performance
   - Create visualizations for results

4. **Documentation:**
   - Prepare PowerPoint presentation
   - Document findings and model comparisons
   - Include code comments and explanations

## Notes

- The dataset filename suggests it's already balanced (`balanced_V2`)
- Consider using cross-validation for robust model evaluation
- Tree-based models (Random Forest, XGBoost, Decision Trees) are less sensitive to feature scaling
- Distance-based models (SVM, KNN, Neural Networks) require feature standardization
- Logistic Regression and LDA may benefit from standardization

## Author

Data Analysis Project for Machine Learning Course

## License

Academic/Educational Use


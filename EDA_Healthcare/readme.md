# Healthcare Dataset - Exploratory Data Analysis (EDA)

A complete Python-based exploratory data analysis toolkit for analyzing healthcare datasets with statistical summaries, visualizations, and actionable insights.

## 📋 Contents

### Python Scripts
- **`healthcare_eda_complete.py`** - Complete standalone analysis script
- **`eda_utilities.py`** - Reusable utility functions for custom analysis
- **`QUICKSTART.py`** - Quick start guide with examples

### Data Files
- **`healthcare_data.csv`** - Sample healthcare dataset (70 patients, 11 metrics)

### Generated Reports
- `eda_distributions.png` - 9-plot distribution visualization
- `correlation_heatmap.png` - Correlation matrix heatmap
- `disease_analysis.png` - Disease-focused analysis charts
- `eda_summary_report.csv` - Summary statistics export
- `correlation_matrix.csv` - Correlation values export

## 🚀 Quick Start

### Option 1: Run Complete Analysis (Recommended)
```bash
python healthcare_eda_complete.py
```
This will automatically:
- Load the healthcare data
- Perform comprehensive statistical analysis
- Generate all visualizations
- Create summary reports
- Export CSV files

### Option 2: Use Utility Functions
```python
from eda_utilities import *
import pandas as pd

# Load data
df = load_healthcare_data('healthcare_data.csv')

# Run quick EDA
quick_eda(df)

# Or use individual functions
summary = get_summary_statistics(df)
plot_correlation_heatmap(df)
```

## 📋 Installation & Requirements

### Python Version
- Python 3.7 or higher

### Required Libraries
```bash
pip install pandas numpy matplotlib seaborn scipy
```

### Quick Install
```bash
pip install pandas numpy matplotlib seaborn scipy scikit-learn
```

## 📊 Dataset Overview

### Columns (11 total)
| Column | Type | Description | Range |
|--------|------|-------------|-------|
| Patient_ID | String | Unique patient identifier | PAT1001-PAT1070 |
| Age | Numeric | Age in years | 21-79 |
| Gender | Categorical | Male/Female | - |
| BMI | Numeric | Body Mass Index | 17-36 |
| Systolic_BP | Numeric | Blood pressure (mmHg) | 117-189 |
| Cholesterol | Numeric | Cholesterol (mg/dL) | 164-281 |
| Blood_Sugar | Numeric | Fasting glucose (mg/dL) | 79-168 |
| Heart_Rate | Numeric | Resting heart rate (bpm) | 45-83 |
| Smoking_Status | Categorical | Never/Former/Current | - |
| Exercise_Days | Numeric | Days per week | 0-7 |
| Disease_Status | Categorical | Yes/No | - |

### Dataset Statistics
- **Total Patients:** 70
- **Disease Prevalence:** 31.4%
- **Missing Data:** 0.39% (3 values)
- **Male/Female:** 50/50 split

## 🔍 Analysis Modules

### 1. Data Quality Assessment
- Missing values analysis
- Data type checking
- Duplicate detection
- Outlier identification

### 2. Statistical Analysis
- Descriptive statistics
- Distribution analysis
- Categorical summaries
- Correlation analysis

### 3. Disease Analysis
- Disease prevalence
- Risk stratification
- Health metrics comparison
- Age-based risk assessment

### 4. Lifestyle Factors
- Smoking impact analysis
- Exercise frequency effects
- Behavioral patterns

### 5. Visualizations
- Distribution plots
- Correlation heatmaps
- Boxplots by groups
- Scatter plots
- Bar charts

## 📈 Key Functions

### Data Loading & Inspection
```python
df = load_healthcare_data('healthcare_data.csv')
inspect_data(df)
```

### Statistical Analysis
```python
summary = get_summary_statistics(df)
corr_matrix, top_corr = calculate_correlations(df, top_n=10)
comparison = health_metrics_by_disease(df)
```

### Disease Analysis
```python
stats = analyze_disease_status(df)
risk = risk_by_age_group(df)
```

### Visualizations
```python
plot_distribution(df, 'Age')
plot_boxplot_by_group(df, 'Age', 'Disease_Status')
plot_scatter(df, 'BMI', 'Systolic_BP', hue_col='Disease_Status')
plot_correlation_heatmap(df)
```

### Outlier Detection
```python
outliers, bounds = detect_outliers_iqr(df, 'Cholesterol')
all_outliers = detect_all_outliers(df)
```

### Export Results
```python
export_summary_report(df, 'summary.csv')
export_correlation_matrix(df, 'correlations.csv')
```

## 📊 Key Findings

### Disease Risk Factors
| Factor | Finding |
|--------|---------|
| **Age** | 60+ age group has 50% disease rate (highest risk) |
| **BMI** | Disease patients: 27.05 vs Healthy: 24.98 (+2.07) |
| **Blood Pressure** | Disease patients: 155.5 vs Healthy: 148.0 (+7.5) |
| **Smoking** | Former smokers: 35% disease rate (highest) |
| **Exercise** | Counterintuitive: Disease patients exercise more |

### Strongest Correlations
1. Age ↔ BMI (0.716) - Very Strong
2. Age ↔ Systolic BP (0.669) - Strong
3. BMI ↔ Systolic BP (0.590) - Moderate
4. Age ↔ Cholesterol (0.579) - Moderate

### Age Group Risk
- **<30 years:** 0% disease rate
- **30-40 years:** 36% disease rate
- **50-60 years:** 25% disease rate
- **60+ years:** 50% disease rate ⚠️ (Highest Risk)

## 💡 Recommendations

✅ **Targeted Screening:** Focus on 60+ age group
✅ **Weight Management:** Implement BMI control programs
✅ **BP Monitoring:** Regular blood pressure checks
✅ **Smoking Cessation:** Special attention to former smokers
✅ **Exercise Promotion:** Encourage consistent activity
✅ **Cholesterol Management:** Monitor outlier values

## 📁 File Structure

```
healthcare-eda/
├── healthcare_data.csv              # Raw data (70 rows × 11 columns)
├── healthcare_eda_complete.py       # Complete analysis script
├── eda_utilities.py                 # Utility functions library
├── QUICKSTART.py                    # Quick start examples
├── README.md                        # This file
├── eda_distributions.png            # 9-plot visualization
├── correlation_heatmap.png          # Correlation matrix
├── disease_analysis.png             # Disease-focused charts
├── eda_summary_report.csv           # Summary statistics
└── correlation_matrix.csv           # Correlation values
```

## 🎓 Example Usage Scenarios

### Scenario 1: Quick Analysis
```python
from eda_utilities import *
df = load_healthcare_data()
quick_eda(df)
```

### Scenario 2: Disease-Focused Analysis
```python
disease_stats = analyze_disease_status(df)
risk = risk_by_age_group(df)
metrics = health_metrics_by_disease(df)
plot_boxplot_by_group(df, 'Age', 'Disease_Status')
```

### Scenario 3: High-Risk Patient Identification
```python
high_risk = df[(df['Age'] > 60) & 
               (df['BMI'] > 30) & 
               (df['Systolic_BP'] > 160)]
print(f"High-risk patients: {len(high_risk)}")
```

### Scenario 4: Smoking Impact Analysis
```python
smokers = df[df['Smoking_Status'] != 'Never']
non_smokers = df[df['Smoking_Status'] == 'Never']
comparison = pd.DataFrame({
    'Smokers': smokers[numeric_cols].mean(),
    'Non-Smokers': non_smokers[numeric_cols].mean()
})
```

## 🔧 Customization

### Add Your Own Data
1. Replace `healthcare_data.csv` with your own CSV file
2. Ensure same column names or update script
3. Run analysis

### Modify Analysis
Edit `healthcare_eda_complete.py` to:
- Change visualization styles
- Add new metrics
- Modify grouping variables
- Customize output formats

### Create Custom Functions
Use `eda_utilities.py` as a template to add your own functions:

```python
def custom_analysis(df):
    """Your custom analysis function"""
    pass
```

## 📖 Documentation

### Function Reference
See `eda_utilities.py` for detailed docstrings:
```python
from eda_utilities import function_name
help(function_name)
```

### Examples
See `QUICKSTART.py` for 10+ complete examples

### Output Details
- **PNG files:** High-resolution (300 DPI) images
- **CSV files:** Excel-compatible comma-separated format
- **Console output:** Detailed text reports

## ⚙️ Troubleshooting

### Missing Dependencies
```bash
pip install --upgrade pandas numpy matplotlib seaborn scipy
```

### File Not Found
- Ensure `healthcare_data.csv` is in the same directory
- Check file permissions
- Use absolute path if needed

### Memory Issues
- For large datasets, process in chunks:
```python
for chunk in pd.read_csv('file.csv', chunksize=1000):
    # Process chunk
```

### Visualization Not Showing
- Add `plt.show()` at the end of script
- Use Jupyter notebook for interactive displays
- Save to file instead: `plt.savefig('output.png')`

## 📄 License

This EDA toolkit is provided as-is for educational and analytical purposes.


## ✨ Features

✅ Complete statistical analysis
✅ Multiple visualization types
✅ Disease risk stratification
✅ Outlier detection
✅ Correlation analysis
✅ Reusable utility functions
✅ Export to CSV/PNG
✅ Comprehensive documentation
✅ Example workflows
✅ Easy customization

## 🎯 Use Cases

- Healthcare data exploration
- Patient risk stratification
- Epidemiological studies
- Clinical research
- Population health analysis
- Public health planning
- Medical data science education

---

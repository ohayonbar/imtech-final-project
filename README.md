# Phosphorus Levels Classification in Orange Trees using Dendrometer Growth Pattern Analysis

## Project Overview

This project demonstrates the ability to identify different phosphorus fertilization levels in orange trees by analyzing growth patterns from dendrometer data. The system uses advanced time series analysis and machine learning techniques to classify trees into three phosphorus treatment categories based on their physiological responses.

### Feasibility Study Nature

This project was designed as a feasibility study to evaluate whether dendrometer measurements can reliably distinguish between different phosphorus fertilization levels in orange trees. The relatively small sample size (11 trees across three treatment groups) reflects the typical constraints of agricultural field trials, where equipment costs, maintenance requirements, and logistical challenges limit the number of trees that can be monitored simultaneously. Despite these limitations, the study aimed to establish proof-of-concept for this monitoring approach before scaling to larger deployments.

## Dataset

The experiment included:
- 11 functional sensors installed on trees with three phosphorus treatments:
  - Deficient level (P1): 3 trees
  - Optimal level (P3): 5 trees
  - Excessive level (P5): 3 trees
- Data collected hourly over 5.5 months (August 6, 2023 to January 25, 2024)
- Approximately 4,000 measurements per tree, totaling over 40,000 data points

## Methodology

### Data Preprocessing
- Quality control to ensure data integrity
- Handling of outliers and missing values
- Normalization using a 72-hour moving window
- Smoothing to reduce noise

### Feature Extraction
The system extracts 74 features from three key aspects of tree behavior:
- Daily growth patterns
- Cyclical behavior
- Long-term trends

### Classification Algorithm
- Linear Discriminant Analysis (LDA) with feature selection
- Leave-One-Sensor-Out Cross-Validation protocol
- Recursive Feature Elimination for dynamic feature selection

## Results

### Cross-Validation Performance
- 100% accuracy across all 11 cross-validation cycles
- Perfect Precision, Recall, and F1 scores for all treatment groups
- Statistical significance validated through permutation and bootstrap tests (p=0.000)

### Independent Validation Performance
- 80% accuracy on validation with imbalanced class distribution (8 out of 10 samples correctly classified)
- Two misclassifications occurred in cases where sensors were positioned in overlapping feature space regions

### Key Features
Two features emerged as most significant:
1. **Peak-to-trough ratio** (selected in 91% of cases): Reflects the daily cycle of trunk expansion and contraction
2. **Cyclic symmetry score** (selected in 73% of cases): Focuses on nighttime patterns when environmental factors are minimal

#### Importance of Nighttime Measurements
A key finding of this project is the significance of nighttime measurements in classifying phosphorus levels. Analysis of trunk behavior during nighttime hours (18:00-06:00) proved to be highly valuable for distinguishing between different phosphorus treatments. This highlights that:

- Nighttime measurements are less affected by external environmental factors such as solar radiation and temperature fluctuations
- During nighttime, trees primarily focus on water uptake and nutrient transport without the competing demands of photosynthesis
- Phosphorus plays a crucial role in energy transfer and cellular processes that continue during nighttime, making these hours ideal for observing its effects
- The patterns of trunk expansion during nighttime hours provide a clearer signal of the tree's nutritional status without the "noise" of daytime environmental variations

### Time Window Analysis
The project analyzed how the length of the measurement period affects classification accuracy:

- Full dataset (5.5 months): 100% accuracy in cross-validation, 80% in independent validation
- 3-month windows: 56.1% accuracy (±17.6%)
- 6-week windows: 51.1% accuracy (±23.5%)
- 3-week windows: 46.1% accuracy (±25.3%)

These results clearly demonstrate that longer measurement periods provide substantially better classification performance. The full 5.5-month dataset was essential for achieving reliable results, while shorter windows showed significantly reduced accuracy and increased variability. This finding has important practical implications, suggesting that phosphorus level monitoring requires extended observation periods to capture the full range of physiological responses.

## Conclusions

The project successfully demonstrates that dendrometer measurements can identify phosphorus fertilization levels in orange trees with high accuracy during cross-validation, and good accuracy (80%) in independent validation with imbalanced data. The significance of nighttime measurements emerged as a key finding, suggesting that monitoring trunk diameter changes during periods of minimal environmental interference provides the most reliable indicators of phosphorus status.

As a feasibility study, these promising results justify further development with larger sample sizes. The developed model has potential applications in continuous, non-destructive monitoring of tree nutritional status, although it requires extended measurement periods for reliable results. Future work could focus on validating these findings across different seasons, tree varieties, and growing conditions to develop robust, scalable monitoring solutions for agricultural applications.

## Requirements

- Python 3.x
- Required libraries:
  - NumPy
  - Pandas
  - Scikit-learn
  - Scipy
  - Matplotlib
  - Statsmodels

## Usage

The analysis pipeline consists of:
1. Data preprocessing
2. Feature extraction
3. Dynamic feature selection
4. LDA-based classification
5. Performance evaluation

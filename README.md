# Sonar Rock vs Mine Dataset - Outlier Handling and Preprocessing

This repository contains code that demonstrates various preprocessing and outlier handling techniques on the **Sonar Rock vs Mine Dataset**. The dataset consists of 208 samples with 60 continuous numerical features (representing energy levels of sonar signals) and one categorical target variable:
- **R**: Rock
- **M**: Mine

## Techniques Used

### Outlier Detection
- **Using Interquartile Range (IQR):**  
  - Computes the first (Q1) and third quartiles (Q3) and the IQR (Q3 - Q1).
  - Identifies outliers as values below `Q1 - 1.5*IQR` or above `Q3 + 1.5*IQR`.

- **Using Z-Score:**  
  - Calculates the Z-score for each feature.
  - Flags values with a Z-score beyond ±3 standard deviations as potential outliers.

### Outlier Handling
Given that the Sonar dataset is small (208 samples), outright removal of outliers is not ideal. Instead, we explored these robust approaches:
- **RobustScaler:**  
  - Normalizes data using the median and IQR rather than the mean and standard deviation.
  - Reduces the influence of outliers while retaining all data points.
  
- **Winsorization:**  
  - Caps extreme values rather than removing them.
  - Specifically, the bottom 5% and top 5% of values are capped using the `winsorize` function from SciPy.

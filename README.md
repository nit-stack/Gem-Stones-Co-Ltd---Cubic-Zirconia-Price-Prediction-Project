# Gem Stones Co Ltd - Cubic Zirconia Price Prediction Project

## Project Overview

Gem Stones Co Ltd is a manufacturer of cubic zirconia, an inexpensive diamond alternative with many of the same qualities as a diamond. The company aims to predict the price of cubic zirconia stones based on their attributes to better distinguish between higher and lower profitable stones, thereby optimizing their profit share. This project uses linear regression to achieve this goal and identifies the five most important attributes for predicting the price.

## Table of Contents
1. Exploratory Data Analysis
2. Data Preprocessing
3. Modeling
4. Performance Metrics
5. Business Insights and Recommendations
6. Conclusion

## 1. Exploratory Data Analysis (EDA)

### Data Description
The dataset contains 27,000 rows and 11 columns with the following attributes:

- **Carat**: Carat weight of the cubic zirconia.
- **Cut**: Quality of the cut (Fair, Good, Very Good, Premium, Ideal).
- **Color**: Color of the stone (D being the best and J the worst).
- **Clarity**: Clarity of the stone (FL to I3).
- **Depth**: Height of the stone as a percentage of the average diameter.
- **Table**: Width of the table as a percentage of the average diameter.
- **Price**: Price of the cubic zirconia.
- **X**: Length in mm.
- **Y**: Width in mm.
- **Z**: Height in mm.

### Initial Findings
- **Null Values**: The 'depth' column has 697 null values.
- **Data Types**: Mix of float64, int64, and object types.
- **Zero Values**: Columns 'X', 'Y', and 'Z' have some zero values.
- **Outliers**: Significant outliers are present in the 'price' column.
- **Duplicates**: No duplicate rows.

Boxplot depicting outliers in 'price' column:

![image](https://github.com/user-attachments/assets/2d2f5add-cdde-4f44-a7be-406b60f47d8b)

### Univariate and Bivariate Analysis
- **Univariate Analysis**: Histograms, frequency polygons, violin plots, and cumulative distribution functions were used to understand the distribution of each attribute.

![image](https://github.com/user-attachments/assets/4c4664b3-bac1-4809-8693-15fa645bb352)

![image](https://github.com/user-attachments/assets/b6fc0d3b-76c8-4608-9fbf-e457c9e7e415)

![image](https://github.com/user-attachments/assets/5434ff86-e636-4df7-84df-77ce15f22a01)

- **Bivariate Analysis**: Pair plots and scatter plots were used to visualize relationships between pairs of attributes. Correlation heatmaps were generated to identify highly correlated attributes.

![image](https://github.com/user-attachments/assets/8055923b-58ec-40ed-ab58-010951c85c69)

![image](https://github.com/user-attachments/assets/bab44ba7-eea3-4959-8b2f-b8aaeb87b763)

## 2. Data Preprocessing

### Handling Null Values
- **Median Imputation**: Null values in the 'depth' column were replaced with the median value.

### Handling Zero Values
- **Median Imputation**: Zero values in 'X', 'Y', and 'Z' were replaced with the median values, as these attributes cannot logically be zero.

### Outlier Treatment
- **IQR Method**: Outliers in the 'price' column were treated using the Interquartile Range (IQR) method.

### Scaling
- **Normalization**: Scaling was performed to ensure that all attributes are on a comparable scale.

### Encoding Categorical Data
- **Label Encoding**: Categorical variables such as 'cut', 'color', and 'clarity' were encoded to numeric values for modeling purposes.

## 3. Modeling

### Data Split
- **Train-Test Split**: The dataset was split into a training set (70%) and a test set (30%).

### Linear Regression
- **Model Training**: Linear regression was applied to the training data.
- **Prediction**: Prices were predicted on both the training and test sets.

A scatter plot representation of the linear regression equation is shown below.

![image](https://github.com/user-attachments/assets/922eb6ef-0b74-4bdf-aa5e-65a732c1be6c)

## 4. Performance Metrics

Regression Summary Chart:

![image](https://github.com/user-attachments/assets/1c3366ce-4bb7-4b9d-8291-aea48e78287b)

### Metrics Used
- R Square is a good measure to determine how well the model fits the dependent variables. However, it does not take into consideration of overfitting problem.
- From the model, we can interpret that around 89% of dependent variability can be explain by the model and adjusted R Square is roughly the same as R Square meaning the model is quite robust.

While R Square is a relative measure of how well the model fits dependent variables, Mean Square Error is an absolute measure of the goodness for the fit.

- MSE gives an absolute number on how much predicted results deviate from the actual number. We cannot interpret much insights from one single result but it gives a real number to compare against other model results and help select the best regression model.
- Root Mean Square Error (RMSE) is the square root of MSE. It is used more commonly than MSE because firstly sometimes MSE value can be too big to compare easily. Secondly, MSE is calculated by the square of error, and thus square root brings it back to the same level of prediction error and make it easier for interpretation.

The larger the MSE the larger the error. Thus, the MSE result on the scaled data is much lower when compared to the MSE on the unscaled data meaning, scaled data has minimal errors when compared to unscaled data. The same applies to RMSE as well.

### Multicollinearity
- **Variance Inflation Factor (VIF)**: High VIF values indicated the presence of multicollinearity among some attributes.

![image](https://github.com/user-attachments/assets/79b3cad6-cf5e-4050-87c4-835c0e60a4b6)

## 5. Business Insights and Recommendations

Based on the model's predictions and analysis, the following insights and recommendations are provided:

1. **Focus on Premium, Ideal, and Very Good Cuts**: These cuts are associated with higher prices and profitability.
2. **Carat Weight of 1.5 and Above**: Stones with a carat weight of 1.5 or more tend to be more profitable.
3. **Depth Above 59%**: Stones with a depth above 59% are sold at higher prices.
4. **Table Size Above 56**: A table size above 56 is more profitable.
5. **Clarity Grades of SI1, SI2, VS1, and VS2**: These clarity grades yield higher profits.

### Key Attributes
The five most important attributes for predicting the price of cubic zirconia are:
1. Cut
2. Carat
3. Clarity
4. Depth
5. Table

## 6. Conclusion

By focusing on stones with the optimal combination of cut, carat, clarity, depth, and table size, Gem Stones Co Ltd can maximize its profitability. The linear regression model provides a reliable tool for predicting prices and making informed business decisions.

For detailed code and analysis, please refer to the accompanying Jupyter notebook.

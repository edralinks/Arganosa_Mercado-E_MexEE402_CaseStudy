# Arganosa_Mercado-E_MexEE402_CaseStudy


# MexEE 402: Data Preprocessing Case Study

MexEE Elective 2: Data Science and Machine Learning
Batangas State University, Alangilan Campus
1st Semester, AY 2026-2027

## Members

| Name | Student Number | Section |
|---|---|---|
| Arganosa, Kier | 23-00125| MEXE - 4102 |
| Mercado, Edralyn | 23-03282| MEXE - 4102|

## Notebook links

| Chapter | links | 
|---|---|
| Ch1_2_3 | https://colab.research.google.com/drive/1cBDsl0DnpPYtY5nPyYn3wDoPvmANLtTB?usp=sharing | 
| Ch4 | https://colab.research.google.com/drive/1i4_uSsvsJYCbtf-PyFdH9mBS1lVoHkeB?usp=sharing | 
| Ch5 | https://colab.research.google.com/drive/1beHLDS-gRkSEEaQeFConsTkoo7qN9h2h?usp=sharing |
| Ch6 | https://colab.research.google.com/drive/1Du-j4e51Wj_GesGDnUQk3F2MLRsl5Qvc?usp=sharing | 
| Ch7 | https://colab.research.google.com/drive/1vZNILkb1cbDGrlWszDDQeLEUeKGe7R06?usp=sharing | 
| Ch8 | https://colab.research.google.com/drive/1hHxCZLLLNYx0Zr-r1AbAUmf_quT5NPLv?usp=sharing |
| Ch9 | https://colab.research.google.com/drive/1B4gXcNGBGdP8rv9pkYZkZz4WoxnMVfuL?usp=sharing | 

## What we learned

One short paragraph per chapter, Ch1_2_3 to Ch9. Say what the chapter taught
you and what surprised you. Not what the library does, but what you understood.

### Chapter 1, 2, 3: Exploring and cleaning data

In these chapters 1,2,3 thought as that before using data for analysis, we need to check and clean it first. Also we understood how to identify missing values, check the information in a dataset, and remove unnecessary columns. What surprised me is that even small problems in the data can affect the results, so it is important to make sure the data is clean and organized.

### Chapter 4: Feature engineering and encoding

In this chapter, we learned how to make data more useful by creating new features or changing existing ones to find patterns. We also learned that binning groups numerical values into categories, while one-hot and ordinal encoding convert categorical data into numbers. What surprised us is that we can get more information from the same data by creating new features, such as Lemonade per Degree, and that we need to choose the right encoding depending on whether the categories have a natural order or not.

### Chapter 5: Scaling and normalization

We learn that scaling and normalization help make numerical data comparable by adjusting their values to a similar range. We understood that features with larger numbers, like grades, may have more influence on some machine learning models than features with smaller numbers, like study hours. What surprised us is that even if the original values are different, we can adjust them to a similar scale to help the model process the data more fairly.


### Chapter 6: Outlier detection

This chapter helped us understand what outliers are and why they can affect the results of our data analysis. We learned different ways to identify them, such as using the Z-score and IQR methods, and different ways to handle them depending on the situation. What surprised us was that the same value can be considered an outlier by one method but not by another, like the value 100 in our example.

### Chapter 7: Feature selection

We learned that the three methods trade accuracy for cost: filter methods (like Pearson correlation) are fast but judge each feature alone, wrapper methods (like RFECV) test subsets with the actual model but are expensive, and embedded methods (like LassoCV) select features during training. What surprised us was that L1 regularization can shrink a coefficient to exactly zero, so the model removes features as it learns.

### Chapter 8: Constructing a preprocessing pipeline

We learned that a pipeline works like a conveyor, the raw data goes in, and each step (mean imputation, then StandardScaler) transforms it automatically. ColumnTransformer lets us apply these steps only to Age and Fare while leaving other columns untouched. What surprised us was that the pipeline's biggest benefit is preventing data leakage and keeping results reproducible, not just saving effort.

### Chapter 9: Full pipeline and visualization

We learned that preprocessing works best as one reusable pipeline: impute missing values (median for numbers, placeholder for categories), scale with StandardScaler, encode with OneHotEncoder, and bin age into life stages. What surprised us was how much happens before any model exists, and that the pipeline guarantees the same transformations on training and test data.

## Errors we found

List any mistake you found in the original notebooks, and the correct version.
There are real ones in there. Finding them earns points.

In Chapter 3, Filling Year with the mean produced decimals like 2006.4, so the median should be used instead. The deletion step removed nothing because Publisher was already filled, and the duplicate check always gave 0 because Rank is unique, so Rank should be dropped first. In Chapter 4, the notebook says Little = 1, Medium = 2, Lots = 3, but the output is 0, 1, 2. The “very hot” label is empty because the highest temperature (95) falls under “hot”, and the one-hot encoding shows True/False instead of 1/0.

In Chapter 5, StandardScaler does not fix the range, it makes the mean 0 and the standard deviation 1, and MinMaxScaler is the one that fixes the range. The output is also only a NumPy array, not a “new dataset”, so the column names are lost. In Chapter 6, the Z-score output is outliers = [] even though the notebook calls 100 a “clear outlier”, because its z-score (2.615) is below the cutoff of 3. With only 8 data points it can never go above 3, so a cutoff of 2 or the IQR method should be used. The IQR steps (IQR = 9.5) also do not match the pandas output (IQR = 9.25).

In Chapter 8, the notebook splits the data with <X = data.drop('Survived', axis=1)> and y = data['Survived'], but the next cell displays x (lowercase) instead of X. Python is case-sensitive, so x is a completely different variable and will either raise a NameError or show the wrong data. The correct version is to use X consistently.
## Note on AI tools

Say whether you used an AI tool, and what for. This is not a penalty.
Hiding it is.

We used AI tools in this activity. We used Gemini inside Google Colab to fix the code whenever a run was not successful. We used Claude to help identify where the errors in the notebooks were. We also used Gemini to understand the meaning of technical functions and terms used in this activity.

## References

McKinney, W. (2021). Python for Data Analysis, 3rd ed. O'Reilly.
VanderPlas, J. Python Data Science Handbook.
Any other page or article you used.

Video Game Sales dataset, Kaggle: https://www.kaggle.com/datasets/gregorut/videogamesales

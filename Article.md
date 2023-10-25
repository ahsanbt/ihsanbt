# **Data Cleaning 101: Removing Null Values for Effective Data Analysis**

![article picture](https://lexica.art/prompt/4eebac86-a12b-4b7b-953c-44eff79b1983.jpeg){width=150 height=100}

Data cleaning is one of the prime and foremost steps to perform in order to develop a robust model for machine learning. The data quality reflects over the performance, accuracy and effectiveness of the Machine Learning models. To do the cleaning, we need to understand the issues in the raw data for better data analysis. There are different stages for cleaning the data, here the focus is on removing the null values from the data.

It is normal to have a dataset with null values. Null values are the missing information or data in a cell, row or column. These are represented by NAN, NA or blank spaces. You will consider yourself lucky if you haven’t found any null value in your dataset. Otherwise, data analysts have to use different scientific methods and, sometimes, judgemental decisions to remove the null values or replace those with suitable values in order to safeguard the true spirit of the dataset. Here, being judgemental does not mean to handle missing values with a hunch or gut feeling without considering the dataset. Data analyst have to consider different factors like nature of data, structure of data, significance of the information and the ultimate purpose of the data. After that, data analyst can make a judgement to fill null values with the appropriate ones.

## **Impact of Missing Values**

Before going further, first take a brief understanding about the significance of the missing information in the data analysis and result. When we perform statistical description like mean, median, mode, sum or even standard deviation, the missing data is considered as zero. This may lead to biased and unreliable result. Some ML models can’t handle null values and give inaccurate result. Therefore, it is better to resolve it in order to develop a strong and effective data analysis and ML model.

Let’s find out some of the basic codes to deal with null values:

## **Importing Libraries & Data Frame**

We need to import two libraries: ‘pandas’ for data analysis and manipulation whereas ‘numpy’ for Algebraic and scientific computation.

```python
import pandas as pd
import numpy as np
```

## **Loading Data Frame**

```python
df = pd.read_csv('./data.csv')
```

Here, `df` is the demotion of data frame, `csv` the file type and `data` the file name

## **Identification of Null Values**

```python
df.isnull().sum() #Identification of the null values in each column
df.isnull().sum().sum() # Sum of all null values in data frame
```

## **Filling Null Values with “0”**

```python
df.fillna(value = 0) # filling all null values equal to zero
```

## **Filling Null Values with Previous Value**

This method can be used if we have time-series data and the previous value of the column can be considered to fill the null value.

```python
df.fillna(method = ‘pad’) # filling Null values with that of previous row value
```

Similarly, we can also fill the data from the next value in a column.

```python
df.fillna(method = ‘bfill’) # filling Null values with that of next row value
```

## **Filling Null Values with Mean**

This strategy is used by the analyst to keep the data unchanged from the null values by replacing those with that of mean value of that respective column.

```python
df.fillna(value = df[‘Column Name’].mean()) #filling null values with the mean of that column.
```

You can also replace with the minimum value of that column.

```python
df.fillna(value = df[‘Column Name’].min())
```

## **Dropping the Column or Row**

This method is used when there are significant missing values in a particular column and that column is not important for the study.

```python
df.drop(columns = “Column Name”) #Dropping the column containing high null values
```

Here, `Column Name` is the name of that particular column.

```python
df.dropna() #Dropping all those rows containing null value
df.dropna(how=’all’) #Dropping only those rows having null values in each cells
```

## **Replacement of Null Values**

Sometimes, data analyst wants to replace the missing values with the particular number / string. This is the beauty of python to fill missing values in a big data using a simple code.

```python
df.replace(to_replace=np.nan, value=123) # replace all the Null values in the dataset with “123”.
```

If you want to replace 3.0 in the data with 5.0 in Column A then we can use below code:

```python
df[‘Column A’].replace(to_replace=3.0, value=5.0) #Replacement of 3.0 value with 5.0 only in Column A
```

## **Interpolating Missing Value**

We can also use the interpolate function to replace the missing values by using linear method. This method is used by the analysts to replace the missing values by keeping the trend of the data linearly.

```python
df[‘Column A’].interpolate(method=’linear’)
```

## **Final Words**

Dealing with real-life, raw and big data often presents the challenge of missing information, which can have significant impact on the precision and reliability of our data analysis and findings. It is essential for the researchers to comprehend the various categories of missing data and deal with it. Each approach for managing missing data has its own strengths and weaknesses and should be chosen based on the specific nature of the data. Here, some of the basic methods are presented to handle the missing values. However, these codes can help you to develop more advanced codes to better deal with the missing values based upon the data requirements.

### **Written by Muhammad Ahsan Rabbi**

### **Economist | Data Scientist | Technical Writer**

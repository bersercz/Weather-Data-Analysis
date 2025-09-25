# Weather Data Analysis Project

## About Dataset

### Here, The Weather Dataset is a time-series data set with per-hour information about the weather conditions at a particular location. It records Temperature, Dew Point Temperature, Relative Humidity, Wind Speed, Visibility, Pressure, and Conditions.

## Analyzing Data
```python
### To find null values .isnull
data.isnull()sum()

### To get index and columns  .shape
data.shape

### To Get index value  .index
data.index

### For columns Name  .columns
data.columns

### To get the data type of all indexes  .dtypes
data.dtypes

### To get unique values  .unique
data.['Temp_C'].unique()
data.unique()
data['Visibility_km'].unique()

### To get unique number sum  .nunique
data.nunique()
data['Visibility_km'].nunique()
data['Temp_C'].nunique()

### To get the count  .count
data['Temp_C'].count()

### To get the count of unique values .value_counts
data['Visibility_km'].value_counts()
data['Temp_C'].value_counts()

### To get info about dataset  .info
data.info()
```

# Problem Statement & Solutions
## Q) 1.  Find all the unique 'Wind Speed' values in the data.
```python
data["Wind Speed_km/h"].unique()
data['Wind Speed_km/h'].nunique()
```

## Q) 2. Find the number of times when the 'Weather is exactly Clear'.
```python
data['Visibility_km'].value_counts()
data['Weather'].value_counts()
data[data.Weather == 'Clear']
data.groupby('Weather').get_group('Clear')
# relevant info
data[data.Weather == 'Mainly Clear']
data.groupby('Weather').get_group('Mainly Clear')
data[data.Weather == 'Mostly Cloudy']
data.groupby('Weather').get_group('Mostly Cloudy')
```

## Q) 3. Find the number of times when the 'Wind Speed was exactly 4 km/h'.
```python
data.head(1)
data['Wind Speed_km/h'].value_counts()
data[data['Wind Speed_km/h'] == 4] 
```

## Q. 4) Find out all the Null Values in the data.
```python
data.isnull()
data.isnull().sum()
```

## Q. 5) Rename the column name 'Weather' of the dataframe to 'Weather Condition'.
```python
data.rename(columns = {'Weather' : 'Weather Condition'}, inplace = True)
data.head(1)
```

## Q.6) What is the mean 'Visibility' ?
```python
data.Visibility_km.mean()
```

## Q. 7) What is the Standard Deviation of 'Pressure'  in this data?
```python
data.Press_kPa.std()
```

## Q. 8) Whats is the Variance of 'Relative Humidity' in this data ?
```python
data['Rel Hum_%'].var()
```

## Q. 9) Find all instances when 'Snow' was recorded.
```python
data.head(1)
data['Weather Condition'] == 'Snow'
data[data['Weather Condition'] == 'Snow']
data[data['Weather Condition'].str.contains('Snow')]
```

## Q. 10) Find all instances when 'Wind Speed is above 24' and 'Visibility is 25'.
```python
 data['Wind Speed_km/h'].value_counts()
data['Wind Speed_km/h'] > 24
data[(data['Wind Speed_km/h'] > 24) &  (data['Visibility_km'] == 25)]
```

## Q. 11) What is the Mean value of each column against each 'Weather Conditon' ?
```python
data.groupby('Weather Condition').mean(numeric_only=True)
```

## Q. 12) What is the Minimum & Maximum value of each column against each 'Weather Conditon' ?
```python
data.groupby('Weather Condition').min()
data.groupby('Weather Condition').max()
```

## Q. 13) Show all the Records where Weather Condition is Fog.
```python
data[data['Weather Condition'] == 'Fog']
```

## Q. 14) Find all instances when 'Weather is Clear' or 'Visibility is above 40'.
```python
data[(data['Weather Condition'] == 'Clear') | (data['Visibility_km'] > 40)]
```

## Q. 15) Find all instances when :
### A. 'Weather is Clear' and 'Relative Humidity is greater than 50'
### or
### B. 'Visibility is above 40'.
```python
data[(data['Weather Condition'] == 'Clear') & (data['Rel Hum_%']> 50) | (data['Visibility_km'] > 40)]
```

## Findings

### Data Quality: Detected and handled null values in multiple columns to ensure clean analysis.
### Uniqueness: Identified distinct weather conditions and validated data consistency.
### Visibility Trends: Observed periods of low visibility, often linked with cloudy or snowy conditions.
### Cloudy Days: Counted and grouped cloudy instances, showing seasonal and daily variations.
### Windy & Snowy Patterns: Grouped data to find frequency of windy and snowy days, and their impact on temperature and visibility.
### Aggregation with GroupBy: Applied groupby operations to summarize weather behavior across time (daily, monthly).

---

## Conclusion

### This analysis provided a structured view of weather data using pandas. By cleaning missing values, grouping by conditions, and exploring unique patterns, the project highlighted how different weather factors (visibility, wind, snow, and cloudiness) interact. The insights demonstrate the usefulness of data wrangling and aggregation techniques in understanding environmental data, which can be extended to more complex forecasting and decision-making tasks.
____________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________________
## By : Devansh Singh Tomar

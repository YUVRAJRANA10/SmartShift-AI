```python
df.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Average Rent (INR/month)</th>
      <th>Food Cost (INR/month)</th>
      <th>Internet Speed (Mbps)</th>
      <th>Healthcare Rating</th>
      <th>Safety Score</th>
      <th>Happiness Index</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>170.000000</td>
      <td>170.000000</td>
      <td>170.000000</td>
      <td>170.000000</td>
      <td>170.000000</td>
      <td>170.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>8022.052941</td>
      <td>5439.329412</td>
      <td>87.487176</td>
      <td>6.451765</td>
      <td>5.493529</td>
      <td>6.427647</td>
    </tr>
    <tr>
      <th>std</th>
      <td>4839.775925</td>
      <td>1433.162559</td>
      <td>34.260658</td>
      <td>1.506759</td>
      <td>2.085740</td>
      <td>1.272141</td>
    </tr>
    <tr>
      <th>min</th>
      <td>4009.000000</td>
      <td>3021.000000</td>
      <td>20.350000</td>
      <td>4.000000</td>
      <td>2.100000</td>
      <td>4.100000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>5490.750000</td>
      <td>4320.000000</td>
      <td>59.200000</td>
      <td>5.100000</td>
      <td>3.700000</td>
      <td>5.300000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>6966.000000</td>
      <td>5388.500000</td>
      <td>91.640000</td>
      <td>6.400000</td>
      <td>5.500000</td>
      <td>6.550000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>8599.750000</td>
      <td>6709.500000</td>
      <td>113.822500</td>
      <td>7.800000</td>
      <td>7.400000</td>
      <td>7.475000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>34896.000000</td>
      <td>7999.000000</td>
      <td>149.460000</td>
      <td>9.000000</td>
      <td>9.000000</td>
      <td>8.400000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.duplicated().sum()
```




    np.int64(0)




```python
df.isnull().sum()
```




    City                        0
    Average Rent (INR/month)    0
    Food Cost (INR/month)       0
    Internet Speed (Mbps)       0
    Healthcare Rating           0
    Safety Score                0
    Happiness Index             0
    dtype: int64




```python
df.info()
```

    <class 'pandas.DataFrame'>
    RangeIndex: 170 entries, 0 to 169
    Data columns (total 7 columns):
     #   Column                    Non-Null Count  Dtype  
    ---  ------                    --------------  -----  
     0   City                      170 non-null    str    
     1   Average Rent (INR/month)  170 non-null    int64  
     2   Food Cost (INR/month)     170 non-null    int64  
     3   Internet Speed (Mbps)     170 non-null    float64
     4   Healthcare Rating         170 non-null    float64
     5   Safety Score              170 non-null    float64
     6   Happiness Index           170 non-null    float64
    dtypes: float64(4), int64(2), str(1)
    memory usage: 9.4 KB
    


```python
df.shape
```




    (170, 7)




```python
df.columns.to_list()
```




    ['City',
     'Average Rent (INR/month)',
     'Food Cost (INR/month)',
     'Internet Speed (Mbps)',
     'Healthcare Rating',
     'Safety Score',
     'Happiness Index']




```python

import pandas as pd;
df = pd.read_csv("../data/raw/india_cost_quality_dataset.csv")
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>City</th>
      <th>Average Rent (INR/month)</th>
      <th>Food Cost (INR/month)</th>
      <th>Internet Speed (Mbps)</th>
      <th>Healthcare Rating</th>
      <th>Safety Score</th>
      <th>Happiness Index</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mumbai</td>
      <td>34896</td>
      <td>6196</td>
      <td>94.48</td>
      <td>6.2</td>
      <td>2.7</td>
      <td>5.3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Delhi</td>
      <td>26424</td>
      <td>4487</td>
      <td>130.26</td>
      <td>6.1</td>
      <td>2.6</td>
      <td>5.6</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Bengaluru</td>
      <td>26667</td>
      <td>6936</td>
      <td>81.36</td>
      <td>8.7</td>
      <td>6.7</td>
      <td>7.5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Hyderabad</td>
      <td>25785</td>
      <td>6375</td>
      <td>108.84</td>
      <td>7.8</td>
      <td>7.7</td>
      <td>6.3</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Ahmedabad</td>
      <td>20881</td>
      <td>3632</td>
      <td>130.80</td>
      <td>5.5</td>
      <td>7.9</td>
      <td>4.3</td>
    </tr>
  </tbody>
</table>
</div>



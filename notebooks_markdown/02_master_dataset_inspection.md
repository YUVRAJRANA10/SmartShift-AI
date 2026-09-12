```python
import pandas as pd

df = pd.read_csv("../data/raw/livingcost_india_all_inr (4).csv")
df1 = pd.read_csv("../data/raw/india_cost_quality_dataset.csv")
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
      <th>cost_one_person_usd</th>
      <th>rent_one_person_usd</th>
      <th>monthly_salary_after_tax_usd</th>
      <th>income_after_rent_usd</th>
      <th>months_covered</th>
      <th>cost_one_person_inr</th>
      <th>rent_one_person_inr</th>
      <th>monthly_salary_after_tax_inr</th>
      <th>income_after_rent_inr</th>
      <th>usd_to_inr_rate_used</th>
      <th>source_url</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Adoni</td>
      <td>346</td>
      <td>132.0</td>
      <td>329</td>
      <td>197.0</td>
      <td>0.9</td>
      <td>30400.87</td>
      <td>11598.02</td>
      <td>28907.19</td>
      <td>17309.17</td>
      <td>87.8638</td>
      <td>https://livingcost.org/cost/india/ap/adoni</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Anantapur</td>
      <td>345</td>
      <td>136.0</td>
      <td>571</td>
      <td>435.0</td>
      <td>1.7</td>
      <td>30313.01</td>
      <td>11949.48</td>
      <td>50170.23</td>
      <td>38220.75</td>
      <td>87.8638</td>
      <td>https://livingcost.org/cost/india/ap/anantapur</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Chirala</td>
      <td>295</td>
      <td>102.0</td>
      <td>555</td>
      <td>453.0</td>
      <td>1.8</td>
      <td>25919.82</td>
      <td>8962.11</td>
      <td>48764.41</td>
      <td>39802.30</td>
      <td>87.8638</td>
      <td>https://livingcost.org/cost/india/ap/chirala</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Chittoor</td>
      <td>400</td>
      <td>81.5</td>
      <td>404</td>
      <td>322.5</td>
      <td>1.4</td>
      <td>35145.52</td>
      <td>7160.90</td>
      <td>35496.98</td>
      <td>28336.08</td>
      <td>87.8638</td>
      <td>https://livingcost.org/cost/india/ap/chittoor</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Eluru</td>
      <td>298</td>
      <td>89.2</td>
      <td>384</td>
      <td>294.8</td>
      <td>1.3</td>
      <td>26183.41</td>
      <td>7837.45</td>
      <td>33739.70</td>
      <td>25902.25</td>
      <td>87.8638</td>
      <td>https://livingcost.org/cost/india/ap/eluru</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.shape
```




    (221, 12)




```python
df.info()
```

    <class 'pandas.DataFrame'>
    RangeIndex: 221 entries, 0 to 220
    Data columns (total 12 columns):
     #   Column                        Non-Null Count  Dtype  
    ---  ------                        --------------  -----  
     0   City                          221 non-null    str    
     1   cost_one_person_usd           221 non-null    int64  
     2   rent_one_person_usd           221 non-null    float64
     3   monthly_salary_after_tax_usd  221 non-null    int64  
     4   income_after_rent_usd         221 non-null    float64
     5   months_covered                221 non-null    float64
     6   cost_one_person_inr           221 non-null    float64
     7   rent_one_person_inr           221 non-null    float64
     8   monthly_salary_after_tax_inr  221 non-null    float64
     9   income_after_rent_inr         221 non-null    float64
     10  usd_to_inr_rate_used          221 non-null    float64
     11  source_url                    221 non-null    str    
    dtypes: float64(8), int64(2), str(2)
    memory usage: 20.8 KB
    


```python
df.columns.to_list()
```




    ['City',
     'cost_one_person_usd',
     'rent_one_person_usd',
     'monthly_salary_after_tax_usd',
     'income_after_rent_usd',
     'months_covered',
     'cost_one_person_inr',
     'rent_one_person_inr',
     'monthly_salary_after_tax_inr',
     'income_after_rent_inr',
     'usd_to_inr_rate_used',
     'source_url']




```python
df.shape
```


```python
df.info()
```

    <class 'pandas.DataFrame'>
    RangeIndex: 221 entries, 0 to 220
    Data columns (total 12 columns):
     #   Column                        Non-Null Count  Dtype  
    ---  ------                        --------------  -----  
     0   City                          221 non-null    str    
     1   cost_one_person_usd           221 non-null    int64  
     2   rent_one_person_usd           221 non-null    float64
     3   monthly_salary_after_tax_usd  221 non-null    int64  
     4   income_after_rent_usd         221 non-null    float64
     5   months_covered                221 non-null    float64
     6   cost_one_person_inr           221 non-null    float64
     7   rent_one_person_inr           221 non-null    float64
     8   monthly_salary_after_tax_inr  221 non-null    float64
     9   income_after_rent_inr         221 non-null    float64
     10  usd_to_inr_rate_used          221 non-null    float64
     11  source_url                    221 non-null    str    
    dtypes: float64(8), int64(2), str(2)
    memory usage: 20.8 KB
    


```python

```


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
      <th>cost_one_person_usd</th>
      <th>rent_one_person_usd</th>
      <th>monthly_salary_after_tax_usd</th>
      <th>income_after_rent_usd</th>
      <th>months_covered</th>
      <th>cost_one_person_inr</th>
      <th>rent_one_person_inr</th>
      <th>monthly_salary_after_tax_inr</th>
      <th>income_after_rent_inr</th>
      <th>usd_to_inr_rate_used</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>221.000000</td>
      <td>221.000000</td>
      <td>221.000000</td>
      <td>221.000000</td>
      <td>221.000000</td>
      <td>221.000000</td>
      <td>221.000000</td>
      <td>221.000000</td>
      <td>221.000000</td>
      <td>2.210000e+02</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>357.932127</td>
      <td>119.447059</td>
      <td>357.796380</td>
      <td>238.349321</td>
      <td>1.095475</td>
      <td>31449.276197</td>
      <td>10495.072342</td>
      <td>31437.349338</td>
      <td>20942.277133</td>
      <td>8.786380e+01</td>
    </tr>
    <tr>
      <th>std</th>
      <td>91.054379</td>
      <td>47.159346</td>
      <td>104.077197</td>
      <td>114.603182</td>
      <td>0.360653</td>
      <td>8000.383058</td>
      <td>4143.599201</td>
      <td>9144.618287</td>
      <td>10069.470970</td>
      <td>1.424312e-14</td>
    </tr>
    <tr>
      <th>min</th>
      <td>251.000000</td>
      <td>59.700000</td>
      <td>179.000000</td>
      <td>-187.000000</td>
      <td>0.300000</td>
      <td>22053.810000</td>
      <td>5245.470000</td>
      <td>15727.620000</td>
      <td>-16430.530000</td>
      <td>8.786380e+01</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>301.000000</td>
      <td>92.800000</td>
      <td>280.000000</td>
      <td>170.000000</td>
      <td>0.900000</td>
      <td>26447.000000</td>
      <td>8153.760000</td>
      <td>24601.860000</td>
      <td>14936.850000</td>
      <td>8.786380e+01</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>329.000000</td>
      <td>112.000000</td>
      <td>360.000000</td>
      <td>248.000000</td>
      <td>1.100000</td>
      <td>28907.190000</td>
      <td>9840.750000</td>
      <td>31630.970000</td>
      <td>21790.220000</td>
      <td>8.786380e+01</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>382.000000</td>
      <td>129.000000</td>
      <td>406.000000</td>
      <td>301.000000</td>
      <td>1.300000</td>
      <td>33563.970000</td>
      <td>11334.430000</td>
      <td>35672.700000</td>
      <td>26447.000000</td>
      <td>8.786380e+01</td>
    </tr>
    <tr>
      <th>max</th>
      <td>705.000000</td>
      <td>458.000000</td>
      <td>712.000000</td>
      <td>621.700000</td>
      <td>2.700000</td>
      <td>61943.980000</td>
      <td>40241.620000</td>
      <td>62559.030000</td>
      <td>54624.920000</td>
      <td>8.786380e+01</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.isnull().sum()
```




    City                            0
    cost_one_person_usd             0
    rent_one_person_usd             0
    monthly_salary_after_tax_usd    0
    income_after_rent_usd           0
    months_covered                  0
    cost_one_person_inr             0
    rent_one_person_inr             0
    monthly_salary_after_tax_inr    0
    income_after_rent_inr           0
    usd_to_inr_rate_used            0
    source_url                      0
    dtype: int64




```python
df.duplicated().sum()
```




    np.int64(0)




```python
df.nunique()
```




    City                            221
    cost_one_person_usd             100
    rent_one_person_usd             134
    monthly_salary_after_tax_usd    166
    income_after_rent_usd           198
    months_covered                   19
    cost_one_person_inr             100
    rent_one_person_inr             134
    monthly_salary_after_tax_inr    167
    income_after_rent_inr           198
    usd_to_inr_rate_used              1
    source_url                      221
    dtype: int64




```python
df.select_dtypes(include="number").corr()
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
      <th>cost_one_person_usd</th>
      <th>rent_one_person_usd</th>
      <th>monthly_salary_after_tax_usd</th>
      <th>income_after_rent_usd</th>
      <th>months_covered</th>
      <th>cost_one_person_inr</th>
      <th>rent_one_person_inr</th>
      <th>monthly_salary_after_tax_inr</th>
      <th>income_after_rent_inr</th>
      <th>usd_to_inr_rate_used</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>cost_one_person_usd</th>
      <td>1.000000</td>
      <td>0.266667</td>
      <td>-0.179571</td>
      <td>-0.272812</td>
      <td>-0.298656</td>
      <td>1.000000</td>
      <td>0.266667</td>
      <td>-0.179571</td>
      <td>-0.272812</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>rent_one_person_usd</th>
      <td>0.266667</td>
      <td>1.000000</td>
      <td>-0.007928</td>
      <td>-0.418701</td>
      <td>-0.402955</td>
      <td>0.266667</td>
      <td>1.000000</td>
      <td>-0.007928</td>
      <td>-0.418701</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>monthly_salary_after_tax_usd</th>
      <td>-0.179571</td>
      <td>-0.007928</td>
      <td>1.000000</td>
      <td>0.911415</td>
      <td>0.858648</td>
      <td>-0.179571</td>
      <td>-0.007928</td>
      <td>1.000000</td>
      <td>0.911415</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>income_after_rent_usd</th>
      <td>-0.272812</td>
      <td>-0.418701</td>
      <td>0.911415</td>
      <td>1.000000</td>
      <td>0.945600</td>
      <td>-0.272812</td>
      <td>-0.418701</td>
      <td>0.911415</td>
      <td>1.000000</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>months_covered</th>
      <td>-0.298656</td>
      <td>-0.402955</td>
      <td>0.858648</td>
      <td>0.945600</td>
      <td>1.000000</td>
      <td>-0.298657</td>
      <td>-0.402955</td>
      <td>0.858648</td>
      <td>0.945600</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>cost_one_person_inr</th>
      <td>1.000000</td>
      <td>0.266667</td>
      <td>-0.179571</td>
      <td>-0.272812</td>
      <td>-0.298657</td>
      <td>1.000000</td>
      <td>0.266667</td>
      <td>-0.179571</td>
      <td>-0.272812</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>rent_one_person_inr</th>
      <td>0.266667</td>
      <td>1.000000</td>
      <td>-0.007928</td>
      <td>-0.418701</td>
      <td>-0.402955</td>
      <td>0.266667</td>
      <td>1.000000</td>
      <td>-0.007928</td>
      <td>-0.418701</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>monthly_salary_after_tax_inr</th>
      <td>-0.179571</td>
      <td>-0.007928</td>
      <td>1.000000</td>
      <td>0.911415</td>
      <td>0.858648</td>
      <td>-0.179571</td>
      <td>-0.007928</td>
      <td>1.000000</td>
      <td>0.911415</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>income_after_rent_inr</th>
      <td>-0.272812</td>
      <td>-0.418701</td>
      <td>0.911415</td>
      <td>1.000000</td>
      <td>0.945600</td>
      <td>-0.272812</td>
      <td>-0.418701</td>
      <td>0.911415</td>
      <td>1.000000</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>usd_to_inr_rate_used</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
df["City"].head(20).tolist()
```




    [' Adoni',
     ' Anantapur',
     ' Chirala',
     ' Chittoor',
     ' Eluru',
     ' Guntur',
     ' Hindupur',
     ' Kadapa',
     ' Kakinada',
     ' Kurnool',
     ' Machilipatnam',
     ' Madanapalle',
     ' Nandyal',
     ' Nellore',
     ' Ongole',
     ' Proddatur',
     ' Rajahmundry',
     ' Tenali',
     ' Tirupati',
     ' Vijayawada']




```python
df["City"].tail(20).tolist()
```




    [' Kolkata',
     ' Krishnanagar',
     ' Kulti',
     ' Madhyamgram',
     ' Maheshtala',
     ' Malda',
     ' Midnapore',
     ' Naihati',
     ' North Dumdum',
     ' Panihati',
     ' Raiganj',
     ' Rajarhat',
     ' Rajpur Sonarpur',
     ' Serampore',
     ' Shantipur',
     ' Siliguri',
     ' South Dumdum',
     ' Uluberia',
     ' Uttarpara',
     ' Alleppey']




```python
df["City"] = df["City"].str.strip()
df1["City"] = df1["City"].str.strip()
```


```python
df["City"].head(20).tolist()
```




    ['Adoni',
     'Anantapur',
     'Chirala',
     'Chittoor',
     'Eluru',
     'Guntur',
     'Hindupur',
     'Kadapa',
     'Kakinada',
     'Kurnool',
     'Machilipatnam',
     'Madanapalle',
     'Nandyal',
     'Nellore',
     'Ongole',
     'Proddatur',
     'Rajahmundry',
     'Tenali',
     'Tirupati',
     'Vijayawada']




```python
df1["City"].head(20).tolist()
```




    ['Mumbai',
     'Delhi',
     'Bengaluru',
     'Hyderabad',
     'Ahmedabad',
     'Chennai',
     'Kolkata',
     'Pune',
     'Jaipur',
     'Surat',
     'Lucknow',
     'Kanpur',
     'Nagpur',
     'Indore',
     'Thane',
     'Bhopal',
     'Visakhapatnam',
     'Pimpri-Chinchwad',
     'Patna',
     'Vadodara']




```python
common_cities = set(df["City"]) & set(df1["City"])

len(common_cities)
```




    108




```python
sorted(common_cities)
```




    ['Agartala',
     'Agra',
     'Ahmedabad',
     'Aizawl',
     'Ajmer',
     'Aligarh',
     'Allahabad',
     'Alwar',
     'Amritsar',
     'Anantapur',
     'Asansol',
     'Aurangabad',
     'Balurghat',
     'Barasat',
     'Bardhaman',
     'Bareilly',
     'Bhavnagar',
     'Bhilai',
     'Bhopal',
     'Bhubaneswar',
     'Bikaner',
     'Bilaspur',
     'Chandigarh',
     'Chennai',
     'Chittoor',
     'Cuttack',
     'Dehradun',
     'Delhi',
     'Dhanbad',
     'Dibrugarh',
     'Durgapur',
     'Eluru',
     'Faridabad',
     'Gaya',
     'Ghaziabad',
     'Gulbarga',
     'Guntur',
     'Gurgaon',
     'Guwahati',
     'Gwalior',
     'Hisar',
     'Howrah',
     'Imphal',
     'Indore',
     'Jabalpur',
     'Jaipur',
     'Jalandhar',
     'Jalgaon',
     'Jamshedpur',
     'Jhansi',
     'Jodhpur',
     'Kakinada',
     'Kanpur',
     'Kharagpur',
     'Kolhapur',
     'Kolkata',
     'Kollam',
     'Krishnanagar',
     'Kurnool',
     'Lucknow',
     'Ludhiana',
     'Madurai',
     'Malda',
     'Mathura',
     'Meerut',
     'Midnapore',
     'Moradabad',
     'Mumbai',
     'Muzaffarpur',
     'Nagpur',
     'Nanded',
     'Nashik',
     'Navi Mumbai',
     'Nellore',
     'Nizamabad',
     'Pathankot',
     'Patiala',
     'Patna',
     'Pondicherry',
     'Porbandar',
     'Pune',
     'Purnia',
     'Raipur',
     'Rajkot',
     'Ranchi',
     'Rohtak',
     'Rourkela',
     'Saharanpur',
     'Sangli',
     'Satara',
     'Shimoga',
     'Sikar',
     'Solapur',
     'Srinagar',
     'Surat',
     'Thane',
     'Thiruvananthapuram',
     'Tiruchirappalli',
     'Tirunelveli',
     'Tiruppur',
     'Udaipur',
     'Ujjain',
     'Vadodara',
     'Varanasi',
     'Vellore',
     'Vijayawada',
     'Visakhapatnam',
     'Warangal']




```python
df1.columns.tolist()
```




    ['City',
     'Average Rent (INR/month)',
     'Food Cost (INR/month)',
     'Internet Speed (Mbps)',
     'Healthcare Rating',
     'Safety Score',
     'Happiness Index']




```python
df.columns.tolist()
```




    ['City',
     'cost_one_person_usd',
     'rent_one_person_usd',
     'monthly_salary_after_tax_usd',
     'income_after_rent_usd',
     'months_covered',
     'cost_one_person_inr',
     'rent_one_person_inr',
     'monthly_salary_after_tax_inr',
     'income_after_rent_inr',
     'usd_to_inr_rate_used',
     'source_url']




```python
df1["Average Rent (INR/month)"].describe()
```




    count      170.000000
    mean      8022.052941
    std       4839.775925
    min       4009.000000
    25%       5490.750000
    50%       6966.000000
    75%       8599.750000
    max      34896.000000
    Name: Average Rent (INR/month), dtype: float64




```python
df["rent_one_person_inr"].describe()
```




    count      221.000000
    mean     10495.072342
    std       4143.599201
    min       5245.470000
    25%       8153.760000
    50%       9840.750000
    75%      11334.430000
    max      40241.620000
    Name: rent_one_person_inr, dtype: float64




```python
# Compare rent for common cities
rent_comparison = df1[df1["City"].isin(common_cities)][
    ["City", "Average Rent (INR/month)"]
].merge(
    df[["City", "rent_one_person_inr"]],
    on="City"
)

rent_comparison.head(20)
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
      <th>rent_one_person_inr</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mumbai</td>
      <td>34896</td>
      <td>35233.38</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Delhi</td>
      <td>26424</td>
      <td>16694.12</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Ahmedabad</td>
      <td>20881</td>
      <td>13970.34</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Chennai</td>
      <td>21323</td>
      <td>13970.34</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Kolkata</td>
      <td>25710</td>
      <td>10631.52</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Pune</td>
      <td>33540</td>
      <td>18363.53</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Jaipur</td>
      <td>8774</td>
      <td>10982.98</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Surat</td>
      <td>9697</td>
      <td>40241.62</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Lucknow</td>
      <td>10047</td>
      <td>9928.61</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Kanpur</td>
      <td>4519</td>
      <td>8751.23</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Nagpur</td>
      <td>13408</td>
      <td>19945.08</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Indore</td>
      <td>11466</td>
      <td>11246.57</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Thane</td>
      <td>6315</td>
      <td>20472.27</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Bhopal</td>
      <td>11885</td>
      <td>9401.43</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Visakhapatnam</td>
      <td>6479</td>
      <td>9752.88</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Patna</td>
      <td>17917</td>
      <td>9049.97</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Vadodara</td>
      <td>12411</td>
      <td>11334.43</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Ghaziabad</td>
      <td>6653</td>
      <td>10455.79</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Ludhiana</td>
      <td>6839</td>
      <td>13706.75</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Agra</td>
      <td>8137</td>
      <td>9577.15</td>
    </tr>
  </tbody>
</table>
</div>




```python
rent_comparison["rent_difference_percent"] = (
    abs(
        rent_comparison["Average Rent (INR/month)"]
        - rent_comparison["rent_one_person_inr"]
    )
    / rent_comparison["rent_one_person_inr"]
) * 100

rent_comparison["rent_difference_percent"].describe()
```




    count    108.000000
    mean      34.391124
    std       23.862101
    min        0.275869
    25%       15.368854
    50%       34.726882
    75%       48.952067
    max      141.828074
    Name: rent_difference_percent, dtype: float64




```python
df["rent_one_person_inr"].value_counts().head(55)
```




    rent_one_person_inr
    9752.88     6
    10016.47    6
    10192.20    6
    9225.70     5
    10631.52    5
    11510.16    4
    10104.34    4
    10982.98    4
    14058.21    4
    11334.43    4
    10455.79    4
    11598.02    3
    8962.11     3
    11246.57    3
    9049.97     3
    13970.34    3
    9577.15     3
    11158.70    3
    9840.75     3
    10895.11    3
    10280.06    3
    9928.61     3
    8874.24     3
    12652.39    2
    7916.53     2
    12125.20    2
    8707.30     2
    16430.53    2
    20472.27    2
    8250.41     2
    12915.98    2
    6387.70     2
    9137.84     2
    11773.75    2
    9489.29     2
    8777.59     2
    8232.84     2
    8136.19     2
    7389.35     2
    12564.52    2
    12213.07    2
    13706.75    2
    11861.61    2
    7881.38     2
    10367.93    2
    11949.48    1
    7160.90     1
    7837.45     1
    7099.40     1
    7415.70     1
    26534.87    1
    12828.11    1
    8144.97     1
    9313.56     1
    6932.45     1
    Name: count, dtype: int64




```python
df["rent_one_person_inr"].nunique()
```




    134




```python
df["rent_one_person_inr"].nunique() / len(df)
```




    0.6063348416289592



So only 60.6% of the rent values are unique. That means a lot of different cities have exactly the same rent_one_person_inr.


```python
df[df["rent_one_person_inr"].duplicated(keep=False)] \
    .sort_values("rent_one_person_inr")[
        ["City", "rent_one_person_inr"]
    ].head(50)
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
      <th>rent_one_person_inr</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>45</th>
      <td>Navsari</td>
      <td>6387.70</td>
    </tr>
    <tr>
      <th>80</th>
      <td>Kollam</td>
      <td>6387.70</td>
    </tr>
    <tr>
      <th>105</th>
      <td>Solapur</td>
      <td>7389.35</td>
    </tr>
    <tr>
      <th>156</th>
      <td>Salem, Tamil Nadu</td>
      <td>7389.35</td>
    </tr>
    <tr>
      <th>157</th>
      <td>Thanjavur</td>
      <td>7881.38</td>
    </tr>
    <tr>
      <th>167</th>
      <td>Bareilly</td>
      <td>7881.38</td>
    </tr>
    <tr>
      <th>176</th>
      <td>Mirzapur</td>
      <td>7916.53</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Machilipatnam</td>
      <td>7916.53</td>
    </tr>
    <tr>
      <th>103</th>
      <td>Sangli</td>
      <td>8136.19</td>
    </tr>
    <tr>
      <th>203</th>
      <td>Kulti</td>
      <td>8136.19</td>
    </tr>
    <tr>
      <th>133</th>
      <td>Bikaner</td>
      <td>8232.84</td>
    </tr>
    <tr>
      <th>94</th>
      <td>Kolhapur</td>
      <td>8232.84</td>
    </tr>
    <tr>
      <th>39</th>
      <td>Bhavnagar</td>
      <td>8250.41</td>
    </tr>
    <tr>
      <th>155</th>
      <td>Nagercoil</td>
      <td>8250.41</td>
    </tr>
    <tr>
      <th>206</th>
      <td>Malda</td>
      <td>8707.30</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Gaya</td>
      <td>8707.30</td>
    </tr>
    <tr>
      <th>64</th>
      <td>Srinagar</td>
      <td>8777.59</td>
    </tr>
    <tr>
      <th>99</th>
      <td>Nanded</td>
      <td>8777.59</td>
    </tr>
    <tr>
      <th>163</th>
      <td>Agartala</td>
      <td>8874.24</td>
    </tr>
    <tr>
      <th>189</th>
      <td>Bardhaman</td>
      <td>8874.24</td>
    </tr>
    <tr>
      <th>207</th>
      <td>Midnapore</td>
      <td>8874.24</td>
    </tr>
    <tr>
      <th>159</th>
      <td>Tiruchirappalli</td>
      <td>8962.11</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Chirala</td>
      <td>8962.11</td>
    </tr>
    <tr>
      <th>60</th>
      <td>Jamshedpur</td>
      <td>8962.11</td>
    </tr>
    <tr>
      <th>115</th>
      <td>Satna</td>
      <td>9049.97</td>
    </tr>
    <tr>
      <th>109</th>
      <td>Imphal</td>
      <td>9049.97</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Patna</td>
      <td>9049.97</td>
    </tr>
    <tr>
      <th>179</th>
      <td>Saharanpur</td>
      <td>9137.84</td>
    </tr>
    <tr>
      <th>47</th>
      <td>Rajkot</td>
      <td>9137.84</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Rajahmundry</td>
      <td>9225.70</td>
    </tr>
    <tr>
      <th>166</th>
      <td>Allahabad</td>
      <td>9225.70</td>
    </tr>
    <tr>
      <th>151</th>
      <td>Cuddalore</td>
      <td>9225.70</td>
    </tr>
    <tr>
      <th>132</th>
      <td>Bhilwara</td>
      <td>9225.70</td>
    </tr>
    <tr>
      <th>137</th>
      <td>Pali</td>
      <td>9225.70</td>
    </tr>
    <tr>
      <th>78</th>
      <td>Kannur</td>
      <td>9489.29</td>
    </tr>
    <tr>
      <th>58</th>
      <td>Chakradharpur</td>
      <td>9489.29</td>
    </tr>
    <tr>
      <th>117</th>
      <td>Vidisha</td>
      <td>9577.15</td>
    </tr>
    <tr>
      <th>51</th>
      <td>Bhiwani</td>
      <td>9577.15</td>
    </tr>
    <tr>
      <th>164</th>
      <td>Agra</td>
      <td>9577.15</td>
    </tr>
    <tr>
      <th>111</th>
      <td>Gwalior</td>
      <td>9752.88</td>
    </tr>
    <tr>
      <th>23</th>
      <td>Dispur</td>
      <td>9752.88</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Visakhapatnam</td>
      <td>9752.88</td>
    </tr>
    <tr>
      <th>73</th>
      <td>Mysore</td>
      <td>9752.88</td>
    </tr>
    <tr>
      <th>92</th>
      <td>Jalgaon</td>
      <td>9752.88</td>
    </tr>
    <tr>
      <th>208</th>
      <td>Naihati</td>
      <td>9752.88</td>
    </tr>
    <tr>
      <th>192</th>
      <td>Bhatpara</td>
      <td>9840.75</td>
    </tr>
    <tr>
      <th>114</th>
      <td>Ratlam</td>
      <td>9840.75</td>
    </tr>
    <tr>
      <th>198</th>
      <td>Hugli-Chuchura</td>
      <td>9840.75</td>
    </tr>
    <tr>
      <th>194</th>
      <td>Chandannagar</td>
      <td>9928.61</td>
    </tr>
    <tr>
      <th>173</th>
      <td>Lucknow</td>
      <td>9928.61</td>
    </tr>
  </tbody>
</table>
</div>



That's not automatically "wrong", but this pattern is suspicious, especially because the values have very precise decimals yet are repeated across unrelated cities. It suggests the column may have been generated/imputed from a limited set of values rather than being independently observed for every city.


```python
df.groupby("rent_one_person_inr")["City"].agg(list).sort_values(key=lambda x: x.str.len(), ascending=False).head(15)
```




    rent_one_person_inr
    10192.20    [Erode, Bally, Baranagar, Barrackpore, Kamarha...
    9752.88     [Visakhapatnam, Dispur, Mysore, Jalgaon, Gwali...
    10016.47    [Shimoga, Aurangabad, Nashik, Jodhpur, Coimbat...
    9225.70     [Rajahmundry, Bhilwara, Pali, Cuddalore, Allah...
    10631.52    [Tirupati, Ranchi, Davanagere, Dindigul, Kolkata]
    11334.43             [Vadodara, Amritsar, Jhansi, Maheshtala]
    10982.98                 [Ongole, Porbandar, Bijapur, Jaipur]
    14058.21                   [Panjim, Kalyan, Dehradun, Haldia]
    11510.16               [Hindupur, Durg, Patiala, Mahbubnagar]
    10104.34    [Madanapalle, Kota, Rajasthan, Madhyamgram, Se...
    10455.79    [Ghaziabad, Bidhannagar, Rajpur Sonarpur, Ulub...
    11598.02                           [Adoni, Nandyal, Thrissur]
    11158.70               [Hubli, Ernakulam, Thiruvananthapuram]
    10280.06                    [Cuttack, North Dumdum, Panihati]
    10895.11                        [Bhubaneswar, Sikar, Barasat]
    Name: City, dtype: object




```python
df["rent_one_person_inr"].duplicated(keep=False).sum()
```




    np.int64(132)




```python
df[df["rent_one_person_inr"].duplicated(keep=False)].sort_values("rent_one_person_inr")[["City", "rent_one_person_inr"]].head(30)
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
      <th>rent_one_person_inr</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>45</th>
      <td>Navsari</td>
      <td>6387.70</td>
    </tr>
    <tr>
      <th>80</th>
      <td>Kollam</td>
      <td>6387.70</td>
    </tr>
    <tr>
      <th>105</th>
      <td>Solapur</td>
      <td>7389.35</td>
    </tr>
    <tr>
      <th>156</th>
      <td>Salem, Tamil Nadu</td>
      <td>7389.35</td>
    </tr>
    <tr>
      <th>157</th>
      <td>Thanjavur</td>
      <td>7881.38</td>
    </tr>
    <tr>
      <th>167</th>
      <td>Bareilly</td>
      <td>7881.38</td>
    </tr>
    <tr>
      <th>176</th>
      <td>Mirzapur</td>
      <td>7916.53</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Machilipatnam</td>
      <td>7916.53</td>
    </tr>
    <tr>
      <th>103</th>
      <td>Sangli</td>
      <td>8136.19</td>
    </tr>
    <tr>
      <th>203</th>
      <td>Kulti</td>
      <td>8136.19</td>
    </tr>
    <tr>
      <th>133</th>
      <td>Bikaner</td>
      <td>8232.84</td>
    </tr>
    <tr>
      <th>94</th>
      <td>Kolhapur</td>
      <td>8232.84</td>
    </tr>
    <tr>
      <th>39</th>
      <td>Bhavnagar</td>
      <td>8250.41</td>
    </tr>
    <tr>
      <th>155</th>
      <td>Nagercoil</td>
      <td>8250.41</td>
    </tr>
    <tr>
      <th>206</th>
      <td>Malda</td>
      <td>8707.30</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Gaya</td>
      <td>8707.30</td>
    </tr>
    <tr>
      <th>64</th>
      <td>Srinagar</td>
      <td>8777.59</td>
    </tr>
    <tr>
      <th>99</th>
      <td>Nanded</td>
      <td>8777.59</td>
    </tr>
    <tr>
      <th>163</th>
      <td>Agartala</td>
      <td>8874.24</td>
    </tr>
    <tr>
      <th>189</th>
      <td>Bardhaman</td>
      <td>8874.24</td>
    </tr>
    <tr>
      <th>207</th>
      <td>Midnapore</td>
      <td>8874.24</td>
    </tr>
    <tr>
      <th>159</th>
      <td>Tiruchirappalli</td>
      <td>8962.11</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Chirala</td>
      <td>8962.11</td>
    </tr>
    <tr>
      <th>60</th>
      <td>Jamshedpur</td>
      <td>8962.11</td>
    </tr>
    <tr>
      <th>115</th>
      <td>Satna</td>
      <td>9049.97</td>
    </tr>
    <tr>
      <th>109</th>
      <td>Imphal</td>
      <td>9049.97</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Patna</td>
      <td>9049.97</td>
    </tr>
    <tr>
      <th>179</th>
      <td>Saharanpur</td>
      <td>9137.84</td>
    </tr>
    <tr>
      <th>47</th>
      <td>Rajkot</td>
      <td>9137.84</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Rajahmundry</td>
      <td>9225.70</td>
    </tr>
  </tbody>
</table>
</div>



So our decision for Dataset 2

Keep:

cost_one_person_inr
rent_one_person_inr
monthly_salary_after_tax_inr
income_after_rent_inr
months_covered

But later, when we build the final model, we'll decide which ones actually belong in the features.
In particular, months_covered and income_after_rent_inr may be derived from the other variables, so we need to be careful about data leakage/redundancy when choosing the ML target.

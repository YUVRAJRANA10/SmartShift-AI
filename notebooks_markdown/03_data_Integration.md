```python
import pandas as pd

df1 = pd.read_csv("../data/raw/india_cost_quality_dataset.csv")
df2 = pd.read_csv("../data/raw/livingcost_india_all_inr (4).csv")

print("Dataset 1:", df1.shape)
print("Dataset 2:", df2.shape)
```

    Dataset 1: (170, 7)
    Dataset 2: (221, 12)
    


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
df2["City"].head(20).tolist()
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
df1["City"] = df1["City"].str.strip()
df2["City"] = df2["City"].str.strip()
```


```python
df2["City"].head(20).tolist()
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
common_cities = set(df1["City"]) & set(df2["City"])

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
cities_df1 = set(df1["City"])
cities_df2 = set(df2["City"])

print("Only in Dataset 1:")
print(sorted(cities_df1 - cities_df2))

print("\nOnly in Dataset 2:")
print(sorted(cities_df2 - cities_df1))
```

    Only in Dataset 1:
    ['Alipurduar', 'Ambattur', 'Arrah', 'Avadi', 'Bankura', 'Basti', 'Begusarai', 'Belagavi', 'Bengaluru', 'Bettiah', 'Bharatpur', 'Birbhum', 'Bongaigaon', 'Chandrapur', 'Chhapra', 'Cooch Behar', 'Darbhanga', 'Diphu', 'Fatehpur', 'Firozabad', 'Gangarampur', 'Gangtok', 'Haflong', 'Hajipur', 'Haldwani', 'Hapur', 'Hoshiarpur', 'Hubballi-Dharwad', 'Hyderabad', 'Itanagar', 'Jhargram', 'Jorhat', 'Kalyan-Dombivli', 'Katihar', 'Kishanganj', 'Kochi', 'Korba', 'Kota', 'Loni', 'Mandya', 'Mangaluru', 'Medinipur', 'Mira-Bhayandar', 'Morena', 'Motihari', 'Mysuru', 'Nagaon', 'Palakkad', 'Palwal', 'Panipat', 'Pimpri-Chinchwad', 'Purulia', 'Rewa', 'Salem', 'Samastipur', 'Sambalpur', 'Silchar', 'Sivasagar', 'Siwan', 'Tezpur', 'Tinsukia', 'Vasai-Virar']
    
    Only in Dataset 2:
    ['Adoni', 'Akola', 'Alleppey', 'Amravati', 'Bally', 'Bangalore', 'Baramulla', 'Baranagar', 'Barrackpore', 'Belgaum', 'Berhampore', 'Bhagalpur', 'Bhatpara', 'Bhilwara', 'Bhiwandi', 'Bhiwani', 'Bhuj', 'Bidhannagar', 'Bijapur', 'Chakradharpur', 'Chandannagar', 'Chirala', 'Coimbatore', 'Cuddalore', 'Davanagere', 'Dindigul', 'Dispur', 'Durg', 'Ernakulam', 'Erode', 'Gandhinagar', 'Godhra', 'Gorakhpur', 'Haldia', 'Hindupur', 'Hospet', 'Hubli', 'Hugli-Chuchura', 'Hyderabad, Telangana', 'Ichalkaranji', 'Jammu', 'Jaunpur', 'Kadapa', 'Kalyan', 'Kamarhati', 'Kannur', 'Karimnagar', 'Khammam', 'Kochi, Kerala', 'Kota, Rajasthan', 'Kottayam', 'Kozhikode', 'Kulti', 'Latur', 'Machilipatnam', 'Madanapalle', 'Madhyamgram', 'Mahbubnagar', 'Maheshtala', 'Malappuram', 'Malegaon', 'Mangalore', 'Margao', 'Mehsana', 'Mirzapur', 'Mormugao', 'Mysore', 'Nadiad', 'Nagercoil', 'Naihati', 'Nalgonda', 'Nandyal', 'Navsari', 'Noida', 'North Dumdum', 'Ongole', 'Pali', 'Panihati', 'Panjim', 'Proddatur', 'Puri', 'Raiganj', 'Rajahmundry', 'Rajarhat', 'Rajpur Sonarpur', 'Ramagundam', 'Ratlam', 'Rishikesh', 'Saharsa', 'Salem, Tamil Nadu', 'Sambhal', 'Satna', 'Secunderabad', 'Serampore', 'Shantipur', 'Shillong', 'Shimla', 'Siliguri', 'Sonipat', 'South Dumdum', 'Tenali', 'Thanjavur', 'Thoothukudi', 'Thrissur', 'Tirupati', 'Tumkur', 'Udupi', 'Uluberia', 'Uttarpara', 'Varkala', 'Vasai', 'Vidisha', 'Vizianagaram']
    

1. Clear naming mismatches

These should be normalized because they are obviously the same city:

Dataset 1	Dataset 2
Bengaluru	Bangalore
Belagavi	Belgaum
Mangaluru	Mangalore
Mysuru	Mysore


```python
city_mapping = {
    "Bangalore": "Bengaluru",
    "Belgaum": "Belagavi",
    "Mangalore": "Mangaluru",
    "Mysore": "Mysuru",
    "Kochi, Kerala": "Kochi",
    "Hyderabad, Telangana": "Hyderabad",
    "Kota, Rajasthan": "Kota",
    "Salem, Tamil Nadu": "Salem"
}

df1["City"] = df1["City"].replace(city_mapping)
df2["City"] = df2["City"].replace(city_mapping)
```

replaced the contradicting spelling or name of the same cities in both datasets


```python
common_cities = set(df1["City"]) & set(df2["City"])

print("Common cities:", len(common_cities))
```

    Common cities: 116
    


```python
print(sorted(common_cities))
```

    ['Agartala', 'Agra', 'Ahmedabad', 'Aizawl', 'Ajmer', 'Aligarh', 'Allahabad', 'Alwar', 'Amritsar', 'Anantapur', 'Asansol', 'Aurangabad', 'Balurghat', 'Barasat', 'Bardhaman', 'Bareilly', 'Belagavi', 'Bengaluru', 'Bhavnagar', 'Bhilai', 'Bhopal', 'Bhubaneswar', 'Bikaner', 'Bilaspur', 'Chandigarh', 'Chennai', 'Chittoor', 'Cuttack', 'Dehradun', 'Delhi', 'Dhanbad', 'Dibrugarh', 'Durgapur', 'Eluru', 'Faridabad', 'Gaya', 'Ghaziabad', 'Gulbarga', 'Guntur', 'Gurgaon', 'Guwahati', 'Gwalior', 'Hisar', 'Howrah', 'Hyderabad', 'Imphal', 'Indore', 'Jabalpur', 'Jaipur', 'Jalandhar', 'Jalgaon', 'Jamshedpur', 'Jhansi', 'Jodhpur', 'Kakinada', 'Kanpur', 'Kharagpur', 'Kochi', 'Kolhapur', 'Kolkata', 'Kollam', 'Kota', 'Krishnanagar', 'Kurnool', 'Lucknow', 'Ludhiana', 'Madurai', 'Malda', 'Mangaluru', 'Mathura', 'Meerut', 'Midnapore', 'Moradabad', 'Mumbai', 'Muzaffarpur', 'Mysuru', 'Nagpur', 'Nanded', 'Nashik', 'Navi Mumbai', 'Nellore', 'Nizamabad', 'Pathankot', 'Patiala', 'Patna', 'Pondicherry', 'Porbandar', 'Pune', 'Purnia', 'Raipur', 'Rajkot', 'Ranchi', 'Rohtak', 'Rourkela', 'Saharanpur', 'Salem', 'Sangli', 'Satara', 'Shimoga', 'Sikar', 'Solapur', 'Srinagar', 'Surat', 'Thane', 'Thiruvananthapuram', 'Tiruchirappalli', 'Tirunelveli', 'Tiruppur', 'Udaipur', 'Ujjain', 'Vadodara', 'Varanasi', 'Vellore', 'Vijayawada', 'Visakhapatnam', 'Warangal']
    


```python
print("Only in Dataset 1:")
print(sorted(set(df1["City"]) - set(df2["City"])))

print("\nOnly in Dataset 2:")
print(sorted(set(df2["City"]) - set(df1["City"])))
```

    Only in Dataset 1:
    ['Alipurduar', 'Ambattur', 'Arrah', 'Avadi', 'Bankura', 'Basti', 'Begusarai', 'Bettiah', 'Bharatpur', 'Birbhum', 'Bongaigaon', 'Chandrapur', 'Chhapra', 'Cooch Behar', 'Darbhanga', 'Diphu', 'Fatehpur', 'Firozabad', 'Gangarampur', 'Gangtok', 'Haflong', 'Hajipur', 'Haldwani', 'Hapur', 'Hoshiarpur', 'Hubballi-Dharwad', 'Itanagar', 'Jhargram', 'Jorhat', 'Kalyan-Dombivli', 'Katihar', 'Kishanganj', 'Korba', 'Loni', 'Mandya', 'Medinipur', 'Mira-Bhayandar', 'Morena', 'Motihari', 'Nagaon', 'Palakkad', 'Palwal', 'Panipat', 'Pimpri-Chinchwad', 'Purulia', 'Rewa', 'Samastipur', 'Sambalpur', 'Silchar', 'Sivasagar', 'Siwan', 'Tezpur', 'Tinsukia', 'Vasai-Virar']
    
    Only in Dataset 2:
    ['Adoni', 'Akola', 'Alleppey', 'Amravati', 'Bally', 'Baramulla', 'Baranagar', 'Barrackpore', 'Berhampore', 'Bhagalpur', 'Bhatpara', 'Bhilwara', 'Bhiwandi', 'Bhiwani', 'Bhuj', 'Bidhannagar', 'Bijapur', 'Chakradharpur', 'Chandannagar', 'Chirala', 'Coimbatore', 'Cuddalore', 'Davanagere', 'Dindigul', 'Dispur', 'Durg', 'Ernakulam', 'Erode', 'Gandhinagar', 'Godhra', 'Gorakhpur', 'Haldia', 'Hindupur', 'Hospet', 'Hubli', 'Hugli-Chuchura', 'Ichalkaranji', 'Jammu', 'Jaunpur', 'Kadapa', 'Kalyan', 'Kamarhati', 'Kannur', 'Karimnagar', 'Khammam', 'Kottayam', 'Kozhikode', 'Kulti', 'Latur', 'Machilipatnam', 'Madanapalle', 'Madhyamgram', 'Mahbubnagar', 'Maheshtala', 'Malappuram', 'Malegaon', 'Margao', 'Mehsana', 'Mirzapur', 'Mormugao', 'Nadiad', 'Nagercoil', 'Naihati', 'Nalgonda', 'Nandyal', 'Navsari', 'Noida', 'North Dumdum', 'Ongole', 'Pali', 'Panihati', 'Panjim', 'Proddatur', 'Puri', 'Raiganj', 'Rajahmundry', 'Rajarhat', 'Rajpur Sonarpur', 'Ramagundam', 'Ratlam', 'Rishikesh', 'Saharsa', 'Sambhal', 'Satna', 'Secunderabad', 'Serampore', 'Shantipur', 'Shillong', 'Shimla', 'Siliguri', 'Sonipat', 'South Dumdum', 'Tenali', 'Thanjavur', 'Thoothukudi', 'Thrissur', 'Tirupati', 'Tumkur', 'Udupi', 'Uluberia', 'Uttarpara', 'Varkala', 'Vasai', 'Vidisha', 'Vizianagaram']
    

For the same city, how different are Dataset 1 and Dataset 2?


```python
common_cities = sorted(set(df1["City"]) & set(df2["City"]))

df1_common = df1[df1["City"].isin(common_cities)].copy()
df2_common = df2[df2["City"].isin(common_cities)].copy()

print("Dataset 1:", df1_common.shape)
print("Dataset 2:", df2_common.shape)
```

    Dataset 1: (116, 7)
    Dataset 2: (116, 12)
    


```python
print("Dataset 1 columns:")
print(df1_common.columns.tolist())

print("\nDataset 2 columns:")
print(df2_common.columns.tolist())
```

    Dataset 1 columns:
    ['City', 'Average Rent (INR/month)', 'Food Cost (INR/month)', 'Internet Speed (Mbps)', 'Healthcare Rating', 'Safety Score', 'Happiness Index']
    
    Dataset 2 columns:
    ['City', 'cost_one_person_usd', 'rent_one_person_usd', 'monthly_salary_after_tax_usd', 'income_after_rent_usd', 'months_covered', 'cost_one_person_inr', 'rent_one_person_inr', 'monthly_salary_after_tax_inr', 'income_after_rent_inr', 'usd_to_inr_rate_used', 'source_url']
    


```python
df1_common[
    ["Average Rent (INR/month)", "Food Cost (INR/month)",
     "Internet Speed (Mbps)", "Healthcare Rating",
     "Safety Score", "Happiness Index"]
].describe()
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
      <td>116.000000</td>
      <td>116.000000</td>
      <td>116.000000</td>
      <td>116.000000</td>
      <td>116.000000</td>
      <td>116.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>8483.543103</td>
      <td>5503.163793</td>
      <td>85.833190</td>
      <td>6.424138</td>
      <td>5.323276</td>
      <td>6.338793</td>
    </tr>
    <tr>
      <th>std</th>
      <td>5685.971878</td>
      <td>1416.506799</td>
      <td>33.809591</td>
      <td>1.433428</td>
      <td>1.992916</td>
      <td>1.311605</td>
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
      <td>5498.500000</td>
      <td>4397.500000</td>
      <td>58.640000</td>
      <td>5.175000</td>
      <td>3.675000</td>
      <td>5.175000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>6876.000000</td>
      <td>5439.000000</td>
      <td>90.105000</td>
      <td>6.350000</td>
      <td>5.400000</td>
      <td>6.500000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>8580.000000</td>
      <td>6716.000000</td>
      <td>110.657500</td>
      <td>7.700000</td>
      <td>6.950000</td>
      <td>7.500000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>34896.000000</td>
      <td>7999.000000</td>
      <td>149.460000</td>
      <td>8.800000</td>
      <td>8.900000</td>
      <td>8.400000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2_common[
    ["cost_one_person_inr",
     "rent_one_person_inr",
     "monthly_salary_after_tax_inr",
     "income_after_rent_inr",
     "months_covered"]
].describe()
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
      <th>cost_one_person_inr</th>
      <th>rent_one_person_inr</th>
      <th>monthly_salary_after_tax_inr</th>
      <th>income_after_rent_inr</th>
      <th>months_covered</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>116.000000</td>
      <td>116.000000</td>
      <td>116.000000</td>
      <td>116.000000</td>
      <td>116.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>31643.086466</td>
      <td>10866.252069</td>
      <td>32318.729397</td>
      <td>21452.477500</td>
      <td>1.100862</td>
    </tr>
    <tr>
      <th>std</th>
      <td>7944.760601</td>
      <td>5173.845961</td>
      <td>9045.532879</td>
      <td>10398.731685</td>
      <td>0.357891</td>
    </tr>
    <tr>
      <th>min</th>
      <td>22053.810000</td>
      <td>5298.190000</td>
      <td>17484.900000</td>
      <td>-16430.530000</td>
      <td>0.300000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>26315.207500</td>
      <td>8061.507500</td>
      <td>25722.125000</td>
      <td>15778.142500</td>
      <td>0.900000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>29346.510000</td>
      <td>9708.950000</td>
      <td>31499.175000</td>
      <td>21803.400000</td>
      <td>1.100000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>33717.737500</td>
      <td>11378.362500</td>
      <td>37320.147500</td>
      <td>27336.627500</td>
      <td>1.300000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>61943.980000</td>
      <td>40241.620000</td>
      <td>59747.380000</td>
      <td>44371.220000</td>
      <td>2.100000</td>
    </tr>
  </tbody>
</table>
</div>




```python
merged_df = pd.merge(
    df1_common,
    df2_common,
    on="City",
    how="inner"
)

merged_df.shape
```




    (116, 18)




```python
merged_df.columns.tolist()
```




    ['City',
     'Average Rent (INR/month)',
     'Food Cost (INR/month)',
     'Internet Speed (Mbps)',
     'Healthcare Rating',
     'Safety Score',
     'Happiness Index',
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



Now we clean the merged dataset

For our India-focused analysis, we don't need the USD duplicates, exchange-rate column, or source URL as model features.


```python
model_df = merged_df.drop(columns=[
    "cost_one_person_usd",
    "rent_one_person_usd",
    "monthly_salary_after_tax_usd",
    "income_after_rent_usd",
    "usd_to_inr_rate_used",
    "source_url"
])

model_df.shape
```




    (116, 12)




```python
model_df.columns.tolist()
```




    ['City',
     'Average Rent (INR/month)',
     'Food Cost (INR/month)',
     'Internet Speed (Mbps)',
     'Healthcare Rating',
     'Safety Score',
     'Happiness Index',
     'months_covered',
     'cost_one_person_inr',
     'rent_one_person_inr',
     'monthly_salary_after_tax_inr',
     'income_after_rent_inr']




```python
model_df.isnull().sum()
```




    City                            0
    Average Rent (INR/month)        0
    Food Cost (INR/month)           0
    Internet Speed (Mbps)           0
    Healthcare Rating               0
    Safety Score                    0
    Happiness Index                 0
    months_covered                  0
    cost_one_person_inr             0
    rent_one_person_inr             0
    monthly_salary_after_tax_inr    0
    income_after_rent_inr           0
    dtype: int64




```python
model_df["City"].duplicated().sum()
```




    np.int64(0)




```python
model_df[[
    "City",
    "Average Rent (INR/month)",
    "rent_one_person_inr"
]].head(20)
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
      <td>Bengaluru</td>
      <td>26667</td>
      <td>19417.90</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Hyderabad</td>
      <td>25785</td>
      <td>14936.85</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Ahmedabad</td>
      <td>20881</td>
      <td>13970.34</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Chennai</td>
      <td>21323</td>
      <td>13970.34</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Kolkata</td>
      <td>25710</td>
      <td>10631.52</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Pune</td>
      <td>33540</td>
      <td>18363.53</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Jaipur</td>
      <td>8774</td>
      <td>10982.98</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Surat</td>
      <td>9697</td>
      <td>40241.62</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Lucknow</td>
      <td>10047</td>
      <td>9928.61</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Kanpur</td>
      <td>4519</td>
      <td>8751.23</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Nagpur</td>
      <td>13408</td>
      <td>19945.08</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Indore</td>
      <td>11466</td>
      <td>11246.57</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Thane</td>
      <td>6315</td>
      <td>20472.27</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Bhopal</td>
      <td>11885</td>
      <td>9401.43</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Visakhapatnam</td>
      <td>6479</td>
      <td>9752.88</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Patna</td>
      <td>17917</td>
      <td>9049.97</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Vadodara</td>
      <td>12411</td>
      <td>11334.43</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Ghaziabad</td>
      <td>6653</td>
      <td>10455.79</td>
    </tr>
  </tbody>
</table>
</div>




```python
Don't delete either column yet.

Instead, let's quantify their relationship across all 116 cities.
```


      Cell In[29], line 1
        Don't delete either column yet.
           ^
    SyntaxError: unterminated string literal (detected at line 1)
    



```python
model_df[
    ["Average Rent (INR/month)", "rent_one_person_inr"]
].corr()
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
      <th>rent_one_person_inr</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Average Rent (INR/month)</th>
      <td>1.000000</td>
      <td>0.417648</td>
    </tr>
    <tr>
      <th>rent_one_person_inr</th>
      <td>0.417648</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
model_df["rent_difference_inr"] = (
    model_df["rent_one_person_inr"]
    - model_df["Average Rent (INR/month)"]
)

model_df["rent_difference_percent"] = (
    abs(model_df["rent_difference_inr"])
    / model_df["Average Rent (INR/month)"]
) * 100
```


```python
model_df[
    ["City",
     "Average Rent (INR/month)",
     "rent_one_person_inr",
     "rent_difference_percent"]
].sort_values(
    "rent_difference_percent",
    ascending=False
).head(15)
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
      <th>rent_difference_percent</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>60</th>
      <td>Belagavi</td>
      <td>4557</td>
      <td>21965.95</td>
      <td>382.026553</td>
    </tr>
    <tr>
      <th>63</th>
      <td>Nellore</td>
      <td>6394</td>
      <td>26534.87</td>
      <td>314.996403</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Surat</td>
      <td>9697</td>
      <td>40241.62</td>
      <td>314.990409</td>
    </tr>
    <tr>
      <th>74</th>
      <td>Dehradun</td>
      <td>4151</td>
      <td>14058.21</td>
      <td>238.670441</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Thane</td>
      <td>6315</td>
      <td>20472.27</td>
      <td>224.184798</td>
    </tr>
    <tr>
      <th>50</th>
      <td>Gurgaon</td>
      <td>5961</td>
      <td>18890.72</td>
      <td>216.905217</td>
    </tr>
    <tr>
      <th>31</th>
      <td>Navi Mumbai</td>
      <td>7579</td>
      <td>22932.45</td>
      <td>202.578836</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Meerut</td>
      <td>4065</td>
      <td>11861.61</td>
      <td>191.798524</td>
    </tr>
    <tr>
      <th>102</th>
      <td>Dibrugarh</td>
      <td>4299</td>
      <td>12125.20</td>
      <td>182.046988</td>
    </tr>
    <tr>
      <th>61</th>
      <td>Mangaluru</td>
      <td>5254</td>
      <td>14146.07</td>
      <td>169.243814</td>
    </tr>
    <tr>
      <th>49</th>
      <td>Tiruppur</td>
      <td>4809</td>
      <td>12564.52</td>
      <td>161.270950</td>
    </tr>
    <tr>
      <th>94</th>
      <td>Aizawl</td>
      <td>4984</td>
      <td>12564.52</td>
      <td>152.097111</td>
    </tr>
    <tr>
      <th>40</th>
      <td>Raipur</td>
      <td>5794</td>
      <td>14409.66</td>
      <td>148.699689</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Aurangabad</td>
      <td>4041</td>
      <td>10016.47</td>
      <td>147.871072</td>
    </tr>
    <tr>
      <th>83</th>
      <td>Jhansi</td>
      <td>5246</td>
      <td>11334.43</td>
      <td>116.058521</td>
    </tr>
  </tbody>
</table>
</div>




```python
model_df["rent_difference_percent"].describe()
```




    count    116.000000
    mean      62.529602
    std       69.778630
    min        0.275110
    25%       17.468612
    50%       37.738693
    75%       84.882910
    max      382.026553
    Name: rent_difference_percent, dtype: float64




```python
model_df[
    ["City",
     "Average Rent (INR/month)",
     "rent_one_person_inr",
     "rent_difference_percent"]
].sort_values(
    "rent_difference_percent",
    ascending=False
).head(15)
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
      <th>rent_difference_percent</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>60</th>
      <td>Belagavi</td>
      <td>4557</td>
      <td>21965.95</td>
      <td>382.026553</td>
    </tr>
    <tr>
      <th>63</th>
      <td>Nellore</td>
      <td>6394</td>
      <td>26534.87</td>
      <td>314.996403</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Surat</td>
      <td>9697</td>
      <td>40241.62</td>
      <td>314.990409</td>
    </tr>
    <tr>
      <th>74</th>
      <td>Dehradun</td>
      <td>4151</td>
      <td>14058.21</td>
      <td>238.670441</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Thane</td>
      <td>6315</td>
      <td>20472.27</td>
      <td>224.184798</td>
    </tr>
    <tr>
      <th>50</th>
      <td>Gurgaon</td>
      <td>5961</td>
      <td>18890.72</td>
      <td>216.905217</td>
    </tr>
    <tr>
      <th>31</th>
      <td>Navi Mumbai</td>
      <td>7579</td>
      <td>22932.45</td>
      <td>202.578836</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Meerut</td>
      <td>4065</td>
      <td>11861.61</td>
      <td>191.798524</td>
    </tr>
    <tr>
      <th>102</th>
      <td>Dibrugarh</td>
      <td>4299</td>
      <td>12125.20</td>
      <td>182.046988</td>
    </tr>
    <tr>
      <th>61</th>
      <td>Mangaluru</td>
      <td>5254</td>
      <td>14146.07</td>
      <td>169.243814</td>
    </tr>
    <tr>
      <th>49</th>
      <td>Tiruppur</td>
      <td>4809</td>
      <td>12564.52</td>
      <td>161.270950</td>
    </tr>
    <tr>
      <th>94</th>
      <td>Aizawl</td>
      <td>4984</td>
      <td>12564.52</td>
      <td>152.097111</td>
    </tr>
    <tr>
      <th>40</th>
      <td>Raipur</td>
      <td>5794</td>
      <td>14409.66</td>
      <td>148.699689</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Aurangabad</td>
      <td>4041</td>
      <td>10016.47</td>
      <td>147.871072</td>
    </tr>
    <tr>
      <th>83</th>
      <td>Jhansi</td>
      <td>5246</td>
      <td>11334.43</td>
      <td>116.058521</td>
    </tr>
  </tbody>
</table>
</div>



⚠️ One important observation

Don't treat rent_difference_percent as a direct "rent increase" or actual cost difference. The two datasets likely use different definitions/sources for rent, which explains extreme values like 382%.

So I'd keep it, but treat it as a derived comparison feature, not as ground truth.

Next step

Before we start modeling, let's finish the EDA/feature understanding properly.


```python
model_df.to_csv("../data/processed/india_cost_quality_merged.csv", index=False)
```


```python
model_df.shape
```




    (116, 14)



03_data_Integration.ipynb has covered the complete integration stage:

Loaded both raw datasets
Inspected their city names
Identified naming inconsistencies
Compared common/unique cities
Established the 116 reliable common cities
Merged the datasets
Removed USD/source columns that aren't needed for the model
Checked missing values → 0
Compared the two rent measures
Created rent_difference_inr and rent_difference_percent
Saved the final processed dataset:
data/processed/india_cost_quality_merged.csv
Final dataset → 116 × 14

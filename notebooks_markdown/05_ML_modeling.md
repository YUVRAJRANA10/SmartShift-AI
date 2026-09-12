```python
import pandas as pd
import numpy as np

from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
from sklearn.metrics import silhouette_score
```


```python
df = pd.read_csv("../data/processed/india_cost_quality_merged.csv")

print("Dataset shape:", df.shape)

df.head()
```

    Dataset shape: (116, 14)
    




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
      <th>months_covered</th>
      <th>cost_one_person_inr</th>
      <th>rent_one_person_inr</th>
      <th>monthly_salary_after_tax_inr</th>
      <th>income_after_rent_inr</th>
      <th>rent_difference_inr</th>
      <th>rent_difference_percent</th>
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
      <td>0.3</td>
      <td>61943.98</td>
      <td>35233.38</td>
      <td>19505.76</td>
      <td>-15727.62</td>
      <td>337.38</td>
      <td>0.966816</td>
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
      <td>0.5</td>
      <td>42965.40</td>
      <td>16694.12</td>
      <td>20296.54</td>
      <td>3602.42</td>
      <td>-9729.88</td>
      <td>36.822131</td>
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
      <td>0.6</td>
      <td>40680.94</td>
      <td>19417.90</td>
      <td>27325.64</td>
      <td>7907.74</td>
      <td>-7249.10</td>
      <td>27.183785</td>
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
      <td>0.6</td>
      <td>41295.99</td>
      <td>14936.85</td>
      <td>25480.50</td>
      <td>10543.66</td>
      <td>-10848.15</td>
      <td>42.071553</td>
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
      <td>0.7</td>
      <td>38835.80</td>
      <td>13970.34</td>
      <td>27237.78</td>
      <td>13267.43</td>
      <td>-6910.66</td>
      <td>33.095446</td>
    </tr>
  </tbody>
</table>
</div>



We want K-Means to understand a city's:

cost
rent
food
digital connectivity
healthcare
safety
happiness


```python
cluster_features = [
    "cost_one_person_inr",
    "Average Rent (INR/month)",
    "Food Cost (INR/month)",
    "Internet Speed (Mbps)",
    "Healthcare Rating",
    "Safety Score",
    "Happiness Index"
]

X_cluster = df[cluster_features]

X_cluster.head()
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
      <td>61943.98</td>
      <td>34896</td>
      <td>6196</td>
      <td>94.48</td>
      <td>6.2</td>
      <td>2.7</td>
      <td>5.3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>42965.40</td>
      <td>26424</td>
      <td>4487</td>
      <td>130.26</td>
      <td>6.1</td>
      <td>2.6</td>
      <td>5.6</td>
    </tr>
    <tr>
      <th>2</th>
      <td>40680.94</td>
      <td>26667</td>
      <td>6936</td>
      <td>81.36</td>
      <td>8.7</td>
      <td>6.7</td>
      <td>7.5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>41295.99</td>
      <td>25785</td>
      <td>6375</td>
      <td>108.84</td>
      <td>7.8</td>
      <td>7.7</td>
      <td>6.3</td>
    </tr>
    <tr>
      <th>4</th>
      <td>38835.80</td>
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




```python
scaler = StandardScaler()

X_scaled = scaler.fit_transform(X_cluster)

X_scaled[:5]
```




    array([[ 3.83049319,  4.66534933,  0.49123804,  0.25685977, -0.15704332,
            -1.32201089, -0.79543742],
           [ 1.43131241,  3.16890242, -0.72048531,  1.31973062, -0.2271088 ,
            -1.37240631, -0.56571773],
           [ 1.14252197,  3.21182459,  1.01591637, -0.13287934,  1.5945937 ,
             0.69380591,  0.88917361],
           [ 1.22027363,  3.05603302,  0.61815347,  0.68343399,  0.96400437,
             1.19776011, -0.02970513],
           [ 0.90926824,  2.18981776, -1.32670149,  1.33577171, -0.64750168,
             1.29855095, -1.5611697 ]])




```python
from sklearn.cluster import KMeans

kmeans = KMeans(
    n_clusters=4,
    random_state=42,
    n_init=10
)

clusters = kmeans.fit_predict(X_scaled)

clusters[:10]
```




    array([3, 3, 3, 3, 3, 3, 3, 3, 1, 2], dtype=int32)




```python
df["city_cluster"] = clusters

df[["City", "city_cluster"]].head(10)
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
      <th>city_cluster</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mumbai</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Delhi</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Bengaluru</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Hyderabad</td>
      <td>3</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Ahmedabad</td>
      <td>3</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Chennai</td>
      <td>3</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Kolkata</td>
      <td>3</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Pune</td>
      <td>3</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Jaipur</td>
      <td>1</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Surat</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python
cluster_summary = df.groupby("city_cluster")[
    [
        "Average Rent (INR/month)",
        "Food Cost (INR/month)",
        "Internet Speed (Mbps)",
        "Healthcare Rating",
        "Safety Score",
        "Happiness Index"
    ]
].mean()

cluster_summary
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
    <tr>
      <th>city_cluster</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7990.806452</td>
      <td>6151.516129</td>
      <td>82.646129</td>
      <td>6.196774</td>
      <td>6.570968</td>
      <td>4.880645</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6390.217391</td>
      <td>4276.652174</td>
      <td>82.247391</td>
      <td>5.004348</td>
      <td>5.560870</td>
      <td>6.456522</td>
    </tr>
    <tr>
      <th>2</th>
      <td>6603.040816</td>
      <td>5592.612245</td>
      <td>82.231633</td>
      <td>7.151020</td>
      <td>4.342857</td>
      <td>7.204082</td>
    </tr>
    <tr>
      <th>3</th>
      <td>20450.153846</td>
      <td>5789.923077</td>
      <td>113.352308</td>
      <td>6.738462</td>
      <td>5.623077</td>
      <td>6.346154</td>
    </tr>
  </tbody>
</table>
</div>



What the model appears to have discovered

Cluster 0 — Higher-cost, safety-oriented

Relatively higher rent/food among the lower-rent clusters
Highest safety among these groups
Lower happiness

Cluster 1 — Low-cost / relatively balanced

Lowest rent
Lowest food cost
Moderate quality scores
Good happiness

Cluster 2 — Quality/livability-oriented

Low rent
Good food cost
Highest healthcare
Highest happiness
But lowest safety

Cluster 3 — High-rent / digitally stronger cities

Rent is dramatically higher
Highest internet speed
Moderate-to-good healthcare, safety and happiness

Learn the natural city segments from cost + quality-of-life characteristics.

                 YOUR 116 CITIES
                       │
                       ▼
              6 CITY FEATURES
                       │
                       ▼
                 StandardScaler
                       │
                       ▼
                    X_scaled
                       │
             ┌─────────┴─────────┐
             │                   │
           K = 2               K = 3
             │                   │
         K-Means              K-Means
             │                   │
       inertia +             inertia +
       silhouette             silhouette
             │                   │
             └─────────┬─────────┘
                       │
                     ...
                       │
                    K = 8
                       │
                       ▼
             Compare the results
                       │
                       ▼
              Choose sensible K
                       │
                       ▼
          FINAL K-MEANS MODEL
                       │
                       ▼
             City Clusters/Profile


```python
from sklearn.metrics import silhouette_score

inertias = []
silhouette_scores = []
k_values = range(2, 9)

for k in k_values:
    model = KMeans(
        n_clusters=k,
        random_state=42,
        n_init=10
    )
    
    labels = model.fit_predict(X_scaled)
    
    inertias.append(model.inertia_)
    silhouette_scores.append(
        silhouette_score(X_scaled, labels)
    )

for k, inertia, score in zip(k_values, inertias, silhouette_scores):
    print(f"k={k}: inertia={inertia:.2f}, silhouette={score:.3f}")
```

    k=2: inertia=683.27, silhouette=0.298
    k=3: inertia=589.29, silhouette=0.149
    k=4: inertia=534.92, silhouette=0.146
    k=5: inertia=486.22, silhouette=0.146
    k=6: inertia=445.75, silhouette=0.154
    k=7: inertia=417.67, silhouette=0.149
    k=8: inertia=386.52, silhouette=0.155
    


```python
from sklearn.cluster import KMeans

# Final K-Means model
kmeans = KMeans(
    n_clusters=2,
    random_state=42,
    n_init=10
)

# Train K-Means and assign each city to a cluster
clusters = kmeans.fit_predict(X_scaled)

# Add cluster labels to our dataset
df["city_cluster"] = clusters

# Check assignments
df[["City", "city_cluster"]].head(10)
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
      <th>city_cluster</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Mumbai</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Delhi</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Bengaluru</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Hyderabad</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Ahmedabad</td>
      <td>0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Chennai</td>
      <td>0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Kolkata</td>
      <td>0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Pune</td>
      <td>0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Jaipur</td>
      <td>1</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Surat</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
cluster_summary = df.groupby("city_cluster")[
    [
        "Average Rent (INR/month)",
        "Food Cost (INR/month)",
        "Internet Speed (Mbps)",
        "Healthcare Rating",
        "Safety Score",
        "Happiness Index",
        "months_covered"
    ]
].mean()

cluster_summary
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
      <th>months_covered</th>
    </tr>
    <tr>
      <th>city_cluster</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>19541.000000</td>
      <td>5664.266667</td>
      <td>114.306000</td>
      <td>6.900000</td>
      <td>5.920000</td>
      <td>6.606667</td>
      <td>0.800000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6841.346535</td>
      <td>5479.237624</td>
      <td>81.604554</td>
      <td>6.353465</td>
      <td>5.234653</td>
      <td>6.299010</td>
      <td>1.145545</td>
    </tr>
  </tbody>
</table>
</div>




```python
df[["City", "city_cluster"]].sort_values(
    "city_cluster"
).to_string(index=False)
```




    '              City  city_cluster\n            Mumbai             0\n             Delhi             0\n         Bengaluru             0\n         Hyderabad             0\n         Ahmedabad             0\n           Chennai             0\n           Kolkata             0\n              Pune             0\n             Patna             0\nThiruvananthapuram             0\n        Chandigarh             0\n           Madurai             0\n       Tirunelveli             0\n             Alwar             0\n             Kochi             0\n            Nagpur             1\n            Bhopal             1\n     Visakhapatnam             1\n          Vadodara             1\n         Ghaziabad             1\n          Ludhiana             1\n              Agra             1\n            Nashik             1\n         Faridabad             1\n            Meerut             1\n            Rajkot             1\n          Varanasi             1\n          Srinagar             1\n        Aurangabad             1\n            Jaipur             1\n           Lucknow             1\n             Surat             1\n       Navi Mumbai             1\n          Amritsar             1\n           Dhanbad             1\n            Howrah             1\n          Jabalpur             1\n           Gwalior             1\n        Vijayawada             1\n         Allahabad             1\n           Jodhpur             1\n            Raipur             1\n              Kota             1\n          Guwahati             1\n           Solapur             1\n          Bareilly             1\n         Moradabad             1\n            Ranchi             1\n            Mysuru             1\n   Tiruchirappalli             1\n           Gurgaon             1\n          Tiruppur             1\n         Jalandhar             1\n       Bhubaneswar             1\n             Salem             1\n           Aligarh             1\n          Warangal             1\n           Jalgaon             1\n            Ujjain             1\n           Kurnool             1\n            Sangli             1\n            Indore             1\n             Thane             1\n            Kanpur             1\n           Nellore             1\n         Mangaluru             1\n          Belagavi             1\n       Pondicherry             1\n              Gaya             1\n        Jamshedpur             1\n            Bhilai             1\n           Bikaner             1\n           Cuttack             1\n         Bhavnagar             1\n          Dehradun             1\n          Durgapur             1\n           Asansol             1\n          Rourkela             1\n            Nanded             1\n          Agartala             1\n          Kolhapur             1\n             Ajmer             1\n           Udaipur             1\n          Gulbarga             1\n            Jhansi             1\n             Sikar             1\n            Guntur             1\n       Muzaffarpur             1\n            Satara             1\n            Kollam             1\n           Shimoga             1\n           Mathura             1\n             Hisar             1\n            Imphal             1\n            Aizawl             1\n         Anantapur             1\n          Bilaspur             1\n           Patiala             1\n            Rohtak             1\n        Saharanpur             1\n           Vellore             1\n          Kakinada             1\n         Dibrugarh             1\n         Bardhaman             1\n         Pathankot             1\n         Porbandar             1\n             Eluru             1\n          Chittoor             1\n         Kharagpur             1\n         Nizamabad             1\n            Purnia             1\n           Barasat             1\n      Krishnanagar             1\n             Malda             1\n         Midnapore             1\n         Balurghat             1'



Cluster 0 → High-cost / higher-service urban profile

Cluster 1 → Lower-cost / lower-service urban profile                                  K-Means has created:

Cluster 0: only 16 cities
Cluster 1: the remaining 100 cities

"Silhouette analysis indicated k=2 as the strongest separation, while k=4 was selected for the SmartShift system because it provides more granular and actionable city profiles for personalized recommendations."


```python
# Supervised ML: Cost of Living Estimation

target = "cost_one_person_inr"

features = [
    "Average Rent (INR/month)",
    "Food Cost (INR/month)",
    "Internet Speed (Mbps)",
    "Healthcare Rating",
    "Safety Score",
    "Happiness Index"
]

X = df[features]
y = df[target]

print("Features:")
print(X.columns.tolist())

print("\nTarget:")
print(y.name)

print("\nX shape:", X.shape)
print("y shape:", y.shape)
```

    Features:
    ['Average Rent (INR/month)', 'Food Cost (INR/month)', 'Internet Speed (Mbps)', 'Healthcare Rating', 'Safety Score', 'Happiness Index']
    
    Target:
    cost_one_person_inr
    
    X shape: (116, 6)
    y shape: (116,)
    


```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)

print("Training samples:", X_train.shape[0])
print("Testing samples:", X_test.shape[0])
```

    Training samples: 92
    Testing samples: 24
    


```python
from sklearn.linear_model import LinearRegression

lr_model = LinearRegression()

lr_model.fit(X_train, y_train)

y_pred_lr = lr_model.predict(X_test)

print("Linear Regression trained successfully.")
```

    Linear Regression trained successfully.
    


```python
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
import numpy as np

mae_lr = mean_absolute_error(y_test, y_pred_lr)
rmse_lr = np.sqrt(mean_squared_error(y_test, y_pred_lr))
r2_lr = r2_score(y_test, y_pred_lr)

print(f"MAE  : ₹{mae_lr:,.2f}")
print(f"RMSE : ₹{rmse_lr:,.2f}")
print(f"R²   : {r2_lr:.3f}")
```

    MAE  : ₹4,929.38
    RMSE : ₹6,901.98
    R²   : 0.171
    

Linear Regression baseline
Metric	Result	Meaning
MAE	₹4,929	Average prediction error is about ₹4.9k
RMSE	₹6,902	Larger errors are pulling the error up
R²	0.171	Only ~17.1% of target variation is explained

So Linear Regression is not particularly strong here.

And that's okay — this is exactly why we established a baseline.

What does this tell us?

Our six features:

Rent
Food
Internet
Healthcare
Safety
Happiness
        ↓
Linear Regression
        ↓
Cost per person

don't have a sufficiently simple linear relationship with the source cost_one_person_inr.

There may be nonlinear interactions between the variables, which is where Random Forest becomes interesting.


```python
from sklearn.ensemble import RandomForestRegressor

rf_model = RandomForestRegressor(
    n_estimators=200,
    random_state=42,
    max_depth=None,
    min_samples_split=2,
    n_jobs=-1
)

rf_model.fit(X_train, y_train)

y_pred_rf = rf_model.predict(X_test)

print("Random Forest trained successfully.")
```

    Random Forest trained successfully.
    


```python
mae_rf = mean_absolute_error(y_test, y_pred_rf)
rmse_rf = np.sqrt(mean_squared_error(y_test, y_pred_rf))
r2_rf = r2_score(y_test, y_pred_rf)

print(f"MAE  : ₹{mae_rf:,.2f}")
print(f"RMSE : ₹{rmse_rf:,.2f}")
print(f"R²   : {r2_rf:.3f}")
```

    MAE  : ₹4,639.32
    RMSE : ₹6,897.41
    R²   : 0.172
    

Baseline comparison
Model	MAE ↓	RMSE ↓	R² ↑
Linear Regression	₹4,929	₹6,902	0.171
Random Forest	₹4,639	₹6,897	0.172
What happened?

Random Forest barely improved over Linear Regression.

MAE improved by ~₹290
RMSE is essentially unchanged
R² went from 0.171 → 0.172

So we should NOT claim that Random Forest is a great cost predictor. The data simply isn't giving us much predictive signal for this target.

And that's actually a valuable ML finding.


```python
feature_importance = pd.DataFrame({
    "Feature": X.columns,
    "Importance": rf_model.feature_importances_
}).sort_values(
    by="Importance",
    ascending=False
)

feature_importance
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
      <th>Feature</th>
      <th>Importance</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>Food Cost (INR/month)</td>
      <td>0.246588</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Internet Speed (Mbps)</td>
      <td>0.224613</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Safety Score</td>
      <td>0.204835</td>
    </tr>
    <tr>
      <th>0</th>
      <td>Average Rent (INR/month)</td>
      <td>0.189621</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Healthcare Rating</td>
      <td>0.071869</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Happiness Index</td>
      <td>0.062473</td>
    </tr>
  </tbody>
</table>
</div>



But there's an important distinction

Feature importance ≠ proof that the feature causes or directly determines cost.

For example, Internet Speed getting 0.225 doesn't mean:

"Internet speed causes 22.5% of the cost."

It means that, within this Random Forest, splits involving Internet Speed contributed substantially to reducing prediction error.

And our weak R² = 0.172 means the overall model still isn't explaining much of the variation in cost_one_person_inr.

The six available features don't contain enough information to strongly predict the dataset's cost_one_person_inr.

That's an actual finding


```python

```


```python

```

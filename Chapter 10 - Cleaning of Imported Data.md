# Chapter 10 - Cleaning of Imported Data
### From Data Science with Jupyter by Prateek Gupta


```python
# import pandas
import pandas as pd
```


```python
# unzipping nfl zip data
import zipfile

with zipfile.ZipFile(r"E:/data Science with jupyter/NFL Play by Play 2009-2017 (v4).csv.zip") as z:
    z.extractall()
```


```python
# unzipping building permit zip data
import zipfile

with zipfile.ZipFile(r"E:\data Science with jupyter\Building_Permits.csv.zip") as z:
    z.extractall()
```


```python
# import required modules

import pandas as pd
import numpy as np

# reading NFL and building permit data

nfl_data = pd.read_csv(r"E:/data Science with jupyter/NFL Play by Play 2009-2017 (v4).csv")
building_permit = pd.read_csv(r"E:\data Science with jupyter\Building_Permits.csv")
```

    C:\Users\husni\anaconda3\lib\site-packages\IPython\core\interactiveshell.py:3146: DtypeWarning: Columns (25,51) have mixed types.Specify dtype option on import or set low_memory=False.
      has_raised = await self.run_ast_nodes(code_ast.body, cell_name,
    C:\Users\husni\anaconda3\lib\site-packages\IPython\core\interactiveshell.py:3146: DtypeWarning: Columns (22,32) have mixed types.Specify dtype option on import or set low_memory=False.
      has_raised = await self.run_ast_nodes(code_ast.body, cell_name,
    


```python
# looking up the data

nfl_data.sample(5)
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
      <th>Date</th>
      <th>GameID</th>
      <th>Drive</th>
      <th>qtr</th>
      <th>down</th>
      <th>time</th>
      <th>TimeUnder</th>
      <th>TimeSecs</th>
      <th>PlayTimeDiff</th>
      <th>SideofField</th>
      <th>...</th>
      <th>yacEPA</th>
      <th>Home_WP_pre</th>
      <th>Away_WP_pre</th>
      <th>Home_WP_post</th>
      <th>Away_WP_post</th>
      <th>Win_Prob</th>
      <th>WPA</th>
      <th>airWPA</th>
      <th>yacWPA</th>
      <th>Season</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>35973</th>
      <td>2009-12-13</td>
      <td>2009121313</td>
      <td>8</td>
      <td>2</td>
      <td>NaN</td>
      <td>01:59</td>
      <td>2</td>
      <td>1919.0</td>
      <td>10.0</td>
      <td>PHI</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>88855</th>
      <td>2011-01-02</td>
      <td>2011010213</td>
      <td>11</td>
      <td>2</td>
      <td>4.0</td>
      <td>03:49</td>
      <td>4</td>
      <td>2029.0</td>
      <td>7.0</td>
      <td>DEN</td>
      <td>...</td>
      <td>NaN</td>
      <td>0.342154</td>
      <td>0.657846</td>
      <td>0.308806</td>
      <td>0.691194</td>
      <td>0.657846</td>
      <td>0.033348</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2010</td>
    </tr>
    <tr>
      <th>245486</th>
      <td>2014-10-26</td>
      <td>2014102608</td>
      <td>11</td>
      <td>2</td>
      <td>NaN</td>
      <td>04:20</td>
      <td>5</td>
      <td>2060.0</td>
      <td>4.0</td>
      <td>HOU</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.000000</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2014</td>
    </tr>
    <tr>
      <th>370599</th>
      <td>2017-09-25</td>
      <td>2017092500</td>
      <td>6</td>
      <td>2</td>
      <td>1.0</td>
      <td>06:27</td>
      <td>7</td>
      <td>2187.0</td>
      <td>0.0</td>
      <td>ARI</td>
      <td>...</td>
      <td>NaN</td>
      <td>0.592468</td>
      <td>0.407532</td>
      <td>0.608161</td>
      <td>0.391839</td>
      <td>0.407532</td>
      <td>-0.015694</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2017</td>
    </tr>
    <tr>
      <th>372532</th>
      <td>2017-10-01</td>
      <td>2017100110</td>
      <td>5</td>
      <td>2</td>
      <td>2.0</td>
      <td>13:20</td>
      <td>14</td>
      <td>2600.0</td>
      <td>38.0</td>
      <td>LAC</td>
      <td>...</td>
      <td>NaN</td>
      <td>0.221861</td>
      <td>0.778139</td>
      <td>0.183644</td>
      <td>0.816356</td>
      <td>0.221861</td>
      <td>-0.038217</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>2017</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 102 columns</p>
</div>




```python
building_permit.sample(5)
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
      <th>Permit Number</th>
      <th>Permit Type</th>
      <th>Permit Type Definition</th>
      <th>Permit Creation Date</th>
      <th>Block</th>
      <th>Lot</th>
      <th>Street Number</th>
      <th>Street Number Suffix</th>
      <th>Street Name</th>
      <th>Street Suffix</th>
      <th>...</th>
      <th>Existing Construction Type</th>
      <th>Existing Construction Type Description</th>
      <th>Proposed Construction Type</th>
      <th>Proposed Construction Type Description</th>
      <th>Site Permit</th>
      <th>Supervisor District</th>
      <th>Neighborhoods - Analysis Boundaries</th>
      <th>Zipcode</th>
      <th>Location</th>
      <th>Record ID</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>47348</th>
      <td>M486927</td>
      <td>8</td>
      <td>otc alterations permit</td>
      <td>05/08/2014</td>
      <td>1778</td>
      <td>001</td>
      <td>2201</td>
      <td>NaN</td>
      <td>Irving</td>
      <td>St</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>4.0</td>
      <td>Sunset/Parkside</td>
      <td>94122.0</td>
      <td>(37.76311920820178, -122.4816132213943)</td>
      <td>1341192113742</td>
    </tr>
    <tr>
      <th>83667</th>
      <td>201504274658</td>
      <td>3</td>
      <td>additions alterations or repairs</td>
      <td>04/27/2015</td>
      <td>3076A</td>
      <td>001</td>
      <td>100</td>
      <td>NaN</td>
      <td>Santa Paula</td>
      <td>Av</td>
      <td>...</td>
      <td>5.0</td>
      <td>wood frame (5)</td>
      <td>5.0</td>
      <td>wood frame (5)</td>
      <td>Y</td>
      <td>7.0</td>
      <td>West of Twin Peaks</td>
      <td>94127.0</td>
      <td>(37.73793522244133, -122.46357348939162)</td>
      <td>1379402151611</td>
    </tr>
    <tr>
      <th>137386</th>
      <td>M723908</td>
      <td>8</td>
      <td>otc alterations permit</td>
      <td>09/20/2016</td>
      <td>3617</td>
      <td>008</td>
      <td>1050</td>
      <td>NaN</td>
      <td>Valencia</td>
      <td>St</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>8.0</td>
      <td>Mission</td>
      <td>94110.0</td>
      <td>(37.75594399052159, -122.42131765151566)</td>
      <td>1438173162318</td>
    </tr>
    <tr>
      <th>138074</th>
      <td>M725628</td>
      <td>8</td>
      <td>otc alterations permit</td>
      <td>09/27/2016</td>
      <td>1376</td>
      <td>001</td>
      <td>1501</td>
      <td>NaN</td>
      <td>Lake</td>
      <td>St</td>
      <td>...</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>1438980374769</td>
    </tr>
    <tr>
      <th>183119</th>
      <td>201709188815</td>
      <td>8</td>
      <td>otc alterations permit</td>
      <td>09/18/2017</td>
      <td>2860</td>
      <td>021</td>
      <td>29</td>
      <td>NaN</td>
      <td>Mendosa</td>
      <td>Av</td>
      <td>...</td>
      <td>5.0</td>
      <td>wood frame (5)</td>
      <td>5.0</td>
      <td>wood frame (5)</td>
      <td>NaN</td>
      <td>7.0</td>
      <td>West of Twin Peaks</td>
      <td>94116.0</td>
      <td>(37.74879801092396, -122.46556796364534)</td>
      <td>1479953146100</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 43 columns</p>
</div>




```python
building_permit.head()
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
      <th>Permit Number</th>
      <th>Permit Type</th>
      <th>Permit Type Definition</th>
      <th>Permit Creation Date</th>
      <th>Block</th>
      <th>Lot</th>
      <th>Street Number</th>
      <th>Street Number Suffix</th>
      <th>Street Name</th>
      <th>Street Suffix</th>
      <th>...</th>
      <th>Existing Construction Type</th>
      <th>Existing Construction Type Description</th>
      <th>Proposed Construction Type</th>
      <th>Proposed Construction Type Description</th>
      <th>Site Permit</th>
      <th>Supervisor District</th>
      <th>Neighborhoods - Analysis Boundaries</th>
      <th>Zipcode</th>
      <th>Location</th>
      <th>Record ID</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>201505065519</td>
      <td>4</td>
      <td>sign - erect</td>
      <td>05/06/2015</td>
      <td>0326</td>
      <td>023</td>
      <td>140</td>
      <td>NaN</td>
      <td>Ellis</td>
      <td>St</td>
      <td>...</td>
      <td>3.0</td>
      <td>constr type 3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>Tenderloin</td>
      <td>94102.0</td>
      <td>(37.785719256680785, -122.40852313194863)</td>
      <td>1380611233945</td>
    </tr>
    <tr>
      <th>1</th>
      <td>201604195146</td>
      <td>4</td>
      <td>sign - erect</td>
      <td>04/19/2016</td>
      <td>0306</td>
      <td>007</td>
      <td>440</td>
      <td>NaN</td>
      <td>Geary</td>
      <td>St</td>
      <td>...</td>
      <td>3.0</td>
      <td>constr type 3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>Tenderloin</td>
      <td>94102.0</td>
      <td>(37.78733980600732, -122.41063199757738)</td>
      <td>1420164406718</td>
    </tr>
    <tr>
      <th>2</th>
      <td>201605278609</td>
      <td>3</td>
      <td>additions alterations or repairs</td>
      <td>05/27/2016</td>
      <td>0595</td>
      <td>203</td>
      <td>1647</td>
      <td>NaN</td>
      <td>Pacific</td>
      <td>Av</td>
      <td>...</td>
      <td>1.0</td>
      <td>constr type 1</td>
      <td>1.0</td>
      <td>constr type 1</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>Russian Hill</td>
      <td>94109.0</td>
      <td>(37.7946573324287, -122.42232562979227)</td>
      <td>1424856504716</td>
    </tr>
    <tr>
      <th>3</th>
      <td>201611072166</td>
      <td>8</td>
      <td>otc alterations permit</td>
      <td>11/07/2016</td>
      <td>0156</td>
      <td>011</td>
      <td>1230</td>
      <td>NaN</td>
      <td>Pacific</td>
      <td>Av</td>
      <td>...</td>
      <td>5.0</td>
      <td>wood frame (5)</td>
      <td>5.0</td>
      <td>wood frame (5)</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>Nob Hill</td>
      <td>94109.0</td>
      <td>(37.79595867909168, -122.41557405519474)</td>
      <td>1443574295566</td>
    </tr>
    <tr>
      <th>4</th>
      <td>201611283529</td>
      <td>6</td>
      <td>demolitions</td>
      <td>11/28/2016</td>
      <td>0342</td>
      <td>001</td>
      <td>950</td>
      <td>NaN</td>
      <td>Market</td>
      <td>St</td>
      <td>...</td>
      <td>3.0</td>
      <td>constr type 3</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>6.0</td>
      <td>Tenderloin</td>
      <td>94102.0</td>
      <td>(37.78315261897309, -122.40950883997789)</td>
      <td>144548169992</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 43 columns</p>
</div>




```python
# getting the number of missing values per column
missing_value_count = nfl_data.isnull().sum()

# looking at first 10 columns missing values in nfl dataset
missing_value_count[1:10]
```




    GameID              0
    Drive               0
    qtr                 0
    down            61154
    time              224
    TimeUnder           0
    TimeSecs          224
    PlayTimeDiff      444
    SideofField       528
    dtype: int64




```python
# how many total missing values do we have in nfl_data
total_cells = np.prod(nfl_data.shape)
total_missing = missing_value_count.sum()

# percent of data that is missing
(total_missing/total_cells) * 100
```




    24.87214126835169




```python
# getting the number of missing values per column
missing_value_count = building_permit.isnull().sum()

# looking at first 10 columns missing values in nfl dataset
missing_value_count[1:10]
```




    Permit Type                    0
    Permit Type Definition         0
    Permit Creation Date           0
    Block                          0
    Lot                            0
    Street Number                  0
    Street Number Suffix      196684
    Street Name                    0
    Street Suffix               2768
    dtype: int64




```python
# how many total missing values do we have in nfl_data
total_cells = np.prod(building_permit.shape)
total_missing = missing_value_count.sum()

# percent of data that is missing
(total_missing/total_cells) * 100
```




    26.26002315058403




```python
# replace all NaN's the value that comes directly after it in the same column
# then replace all the missing NaN's with 0

nfl_data.fillna(method = 'bfill', axis=0).fillna(0)
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
      <th>Date</th>
      <th>GameID</th>
      <th>Drive</th>
      <th>qtr</th>
      <th>down</th>
      <th>time</th>
      <th>TimeUnder</th>
      <th>TimeSecs</th>
      <th>PlayTimeDiff</th>
      <th>SideofField</th>
      <th>...</th>
      <th>yacEPA</th>
      <th>Home_WP_pre</th>
      <th>Away_WP_pre</th>
      <th>Home_WP_post</th>
      <th>Away_WP_post</th>
      <th>Win_Prob</th>
      <th>WPA</th>
      <th>airWPA</th>
      <th>yacWPA</th>
      <th>Season</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2009-09-10</td>
      <td>2009091000</td>
      <td>1</td>
      <td>1</td>
      <td>1.0</td>
      <td>15:00</td>
      <td>15</td>
      <td>3600.0</td>
      <td>0.0</td>
      <td>TEN</td>
      <td>...</td>
      <td>1.146076</td>
      <td>0.485675</td>
      <td>0.514325</td>
      <td>0.546433</td>
      <td>0.453567</td>
      <td>0.485675</td>
      <td>0.060758</td>
      <td>-0.032244</td>
      <td>0.036899</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2009-09-10</td>
      <td>2009091000</td>
      <td>1</td>
      <td>1</td>
      <td>1.0</td>
      <td>14:53</td>
      <td>15</td>
      <td>3593.0</td>
      <td>7.0</td>
      <td>PIT</td>
      <td>...</td>
      <td>1.146076</td>
      <td>0.546433</td>
      <td>0.453567</td>
      <td>0.551088</td>
      <td>0.448912</td>
      <td>0.546433</td>
      <td>0.004655</td>
      <td>-0.032244</td>
      <td>0.036899</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2009-09-10</td>
      <td>2009091000</td>
      <td>1</td>
      <td>1</td>
      <td>2.0</td>
      <td>14:16</td>
      <td>15</td>
      <td>3556.0</td>
      <td>37.0</td>
      <td>PIT</td>
      <td>...</td>
      <td>-5.031425</td>
      <td>0.551088</td>
      <td>0.448912</td>
      <td>0.510793</td>
      <td>0.489207</td>
      <td>0.551088</td>
      <td>-0.040295</td>
      <td>0.106663</td>
      <td>-0.156239</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2009-09-10</td>
      <td>2009091000</td>
      <td>1</td>
      <td>1</td>
      <td>3.0</td>
      <td>13:35</td>
      <td>14</td>
      <td>3515.0</td>
      <td>41.0</td>
      <td>PIT</td>
      <td>...</td>
      <td>-5.031425</td>
      <td>0.510793</td>
      <td>0.489207</td>
      <td>0.461217</td>
      <td>0.538783</td>
      <td>0.510793</td>
      <td>-0.049576</td>
      <td>0.106663</td>
      <td>-0.156239</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2009-09-10</td>
      <td>2009091000</td>
      <td>1</td>
      <td>1</td>
      <td>4.0</td>
      <td>13:27</td>
      <td>14</td>
      <td>3507.0</td>
      <td>8.0</td>
      <td>PIT</td>
      <td>...</td>
      <td>0.163935</td>
      <td>0.461217</td>
      <td>0.538783</td>
      <td>0.558929</td>
      <td>0.441071</td>
      <td>0.461217</td>
      <td>0.097712</td>
      <td>-0.010456</td>
      <td>0.006029</td>
      <td>2009</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>407683</th>
      <td>2017-12-31</td>
      <td>2017123101</td>
      <td>29</td>
      <td>4</td>
      <td>3.0</td>
      <td>00:28</td>
      <td>1</td>
      <td>28.0</td>
      <td>4.0</td>
      <td>BAL</td>
      <td>...</td>
      <td>-0.397515</td>
      <td>0.080409</td>
      <td>0.919591</td>
      <td>0.050478</td>
      <td>0.949522</td>
      <td>0.080409</td>
      <td>0.000000</td>
      <td>-0.021795</td>
      <td>-0.008136</td>
      <td>2017</td>
    </tr>
    <tr>
      <th>407684</th>
      <td>2017-12-31</td>
      <td>2017123101</td>
      <td>29</td>
      <td>4</td>
      <td>3.0</td>
      <td>00:28</td>
      <td>1</td>
      <td>28.0</td>
      <td>0.0</td>
      <td>BAL</td>
      <td>...</td>
      <td>-0.397515</td>
      <td>0.080409</td>
      <td>0.919591</td>
      <td>0.050478</td>
      <td>0.949522</td>
      <td>0.080409</td>
      <td>-0.029931</td>
      <td>-0.021795</td>
      <td>-0.008136</td>
      <td>2017</td>
    </tr>
    <tr>
      <th>407685</th>
      <td>2017-12-31</td>
      <td>2017123101</td>
      <td>29</td>
      <td>4</td>
      <td>4.0</td>
      <td>00:24</td>
      <td>1</td>
      <td>24.0</td>
      <td>4.0</td>
      <td>BAL</td>
      <td>...</td>
      <td>2.457114</td>
      <td>0.050478</td>
      <td>0.949522</td>
      <td>0.030881</td>
      <td>0.969119</td>
      <td>0.050478</td>
      <td>-0.019597</td>
      <td>-0.030603</td>
      <td>0.011006</td>
      <td>2017</td>
    </tr>
    <tr>
      <th>407686</th>
      <td>2017-12-31</td>
      <td>2017123101</td>
      <td>30</td>
      <td>4</td>
      <td>1.0</td>
      <td>00:14</td>
      <td>1</td>
      <td>14.0</td>
      <td>10.0</td>
      <td>BAL</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.030881</td>
      <td>0.969119</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>0.969119</td>
      <td>0.030881</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2017</td>
    </tr>
    <tr>
      <th>407687</th>
      <td>2017-12-31</td>
      <td>2017123101</td>
      <td>30</td>
      <td>4</td>
      <td>0.0</td>
      <td>00:00</td>
      <td>0</td>
      <td>0.0</td>
      <td>14.0</td>
      <td>BAL</td>
      <td>...</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>0.000000</td>
      <td>1.000000</td>
      <td>0.999159</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>2017</td>
    </tr>
  </tbody>
</table>
<p>407688 rows × 102 columns</p>
</div>




```python
# do the same with building permit

building_permit.fillna(method = 'bfill', axis=0).fillna(0)
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
      <th>Permit Number</th>
      <th>Permit Type</th>
      <th>Permit Type Definition</th>
      <th>Permit Creation Date</th>
      <th>Block</th>
      <th>Lot</th>
      <th>Street Number</th>
      <th>Street Number Suffix</th>
      <th>Street Name</th>
      <th>Street Suffix</th>
      <th>...</th>
      <th>Existing Construction Type</th>
      <th>Existing Construction Type Description</th>
      <th>Proposed Construction Type</th>
      <th>Proposed Construction Type Description</th>
      <th>Site Permit</th>
      <th>Supervisor District</th>
      <th>Neighborhoods - Analysis Boundaries</th>
      <th>Zipcode</th>
      <th>Location</th>
      <th>Record ID</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>201505065519</td>
      <td>4</td>
      <td>sign - erect</td>
      <td>05/06/2015</td>
      <td>0326</td>
      <td>023</td>
      <td>140</td>
      <td>A</td>
      <td>Ellis</td>
      <td>St</td>
      <td>...</td>
      <td>3.0</td>
      <td>constr type 3</td>
      <td>1.0</td>
      <td>constr type 1</td>
      <td>Y</td>
      <td>3.0</td>
      <td>Tenderloin</td>
      <td>94102.0</td>
      <td>(37.785719256680785, -122.40852313194863)</td>
      <td>1380611233945</td>
    </tr>
    <tr>
      <th>1</th>
      <td>201604195146</td>
      <td>4</td>
      <td>sign - erect</td>
      <td>04/19/2016</td>
      <td>0306</td>
      <td>007</td>
      <td>440</td>
      <td>A</td>
      <td>Geary</td>
      <td>St</td>
      <td>...</td>
      <td>3.0</td>
      <td>constr type 3</td>
      <td>1.0</td>
      <td>constr type 1</td>
      <td>Y</td>
      <td>3.0</td>
      <td>Tenderloin</td>
      <td>94102.0</td>
      <td>(37.78733980600732, -122.41063199757738)</td>
      <td>1420164406718</td>
    </tr>
    <tr>
      <th>2</th>
      <td>201605278609</td>
      <td>3</td>
      <td>additions alterations or repairs</td>
      <td>05/27/2016</td>
      <td>0595</td>
      <td>203</td>
      <td>1647</td>
      <td>A</td>
      <td>Pacific</td>
      <td>Av</td>
      <td>...</td>
      <td>1.0</td>
      <td>constr type 1</td>
      <td>1.0</td>
      <td>constr type 1</td>
      <td>Y</td>
      <td>3.0</td>
      <td>Russian Hill</td>
      <td>94109.0</td>
      <td>(37.7946573324287, -122.42232562979227)</td>
      <td>1424856504716</td>
    </tr>
    <tr>
      <th>3</th>
      <td>201611072166</td>
      <td>8</td>
      <td>otc alterations permit</td>
      <td>11/07/2016</td>
      <td>0156</td>
      <td>011</td>
      <td>1230</td>
      <td>A</td>
      <td>Pacific</td>
      <td>Av</td>
      <td>...</td>
      <td>5.0</td>
      <td>wood frame (5)</td>
      <td>5.0</td>
      <td>wood frame (5)</td>
      <td>Y</td>
      <td>3.0</td>
      <td>Nob Hill</td>
      <td>94109.0</td>
      <td>(37.79595867909168, -122.41557405519474)</td>
      <td>1443574295566</td>
    </tr>
    <tr>
      <th>4</th>
      <td>201611283529</td>
      <td>6</td>
      <td>demolitions</td>
      <td>11/28/2016</td>
      <td>0342</td>
      <td>001</td>
      <td>950</td>
      <td>A</td>
      <td>Market</td>
      <td>St</td>
      <td>...</td>
      <td>3.0</td>
      <td>constr type 3</td>
      <td>1.0</td>
      <td>constr type 1</td>
      <td>Y</td>
      <td>6.0</td>
      <td>Tenderloin</td>
      <td>94102.0</td>
      <td>(37.78315261897309, -122.40950883997789)</td>
      <td>144548169992</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>198895</th>
      <td>M862628</td>
      <td>8</td>
      <td>otc alterations permit</td>
      <td>12/05/2017</td>
      <td>0113</td>
      <td>017A</td>
      <td>1228</td>
      <td>0</td>
      <td>Montgomery</td>
      <td>St</td>
      <td>...</td>
      <td>5.0</td>
      <td>wood frame (5)</td>
      <td>5.0</td>
      <td>wood frame (5)</td>
      <td>0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0</td>
      <td>1489337276729</td>
    </tr>
    <tr>
      <th>198896</th>
      <td>201712055595</td>
      <td>8</td>
      <td>otc alterations permit</td>
      <td>12/05/2017</td>
      <td>0271</td>
      <td>014</td>
      <td>580</td>
      <td>0</td>
      <td>Bush</td>
      <td>St</td>
      <td>...</td>
      <td>5.0</td>
      <td>wood frame (5)</td>
      <td>5.0</td>
      <td>wood frame (5)</td>
      <td>0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0</td>
      <td>1489462354993</td>
    </tr>
    <tr>
      <th>198897</th>
      <td>M863507</td>
      <td>8</td>
      <td>otc alterations permit</td>
      <td>12/06/2017</td>
      <td>4318</td>
      <td>019</td>
      <td>1568</td>
      <td>0</td>
      <td>Indiana</td>
      <td>St</td>
      <td>...</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0</td>
      <td>1489539379952</td>
    </tr>
    <tr>
      <th>198898</th>
      <td>M863747</td>
      <td>8</td>
      <td>otc alterations permit</td>
      <td>12/06/2017</td>
      <td>0298</td>
      <td>029</td>
      <td>795</td>
      <td>0</td>
      <td>Sutter</td>
      <td>St</td>
      <td>...</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0</td>
      <td>1489608233656</td>
    </tr>
    <tr>
      <th>198899</th>
      <td>M864287</td>
      <td>8</td>
      <td>otc alterations permit</td>
      <td>12/07/2017</td>
      <td>0160</td>
      <td>006</td>
      <td>838</td>
      <td>0</td>
      <td>Pacific</td>
      <td>Av</td>
      <td>...</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0</td>
      <td>0.0</td>
      <td>0</td>
      <td>1489796283803</td>
    </tr>
  </tbody>
</table>
<p>198900 rows × 43 columns</p>
</div>



## How to scale and normalize data?


```python
import pandas as pd
import numpy as np

# for box-cox transformation
from scipy import stats

# for min_max scaling
from mlxtend.preprocessing import minmax_scaling

# for visualization 
import seaborn as sns
import matplotlib.pyplot as plt

# read kickstarters project data
kickstarters_2017 = pd.read_csv(r"E:\data Science with jupyter\ks-projects-201801.csv")

# set seed for reproductivity
np.random.seed(0)
kickstarters_2017.head()
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
      <th>ID</th>
      <th>name</th>
      <th>category</th>
      <th>main_category</th>
      <th>currency</th>
      <th>deadline</th>
      <th>goal</th>
      <th>launched</th>
      <th>pledged</th>
      <th>state</th>
      <th>backers</th>
      <th>country</th>
      <th>usd pledged</th>
      <th>usd_pledged_real</th>
      <th>usd_goal_real</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1000002330</td>
      <td>The Songs of Adelaide &amp; Abullah</td>
      <td>Poetry</td>
      <td>Publishing</td>
      <td>GBP</td>
      <td>2015-10-09</td>
      <td>1000.0</td>
      <td>2015-08-11 12:12:28</td>
      <td>0.0</td>
      <td>failed</td>
      <td>0</td>
      <td>GB</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>1533.95</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1000003930</td>
      <td>Greeting From Earth: ZGAC Arts Capsule For ET</td>
      <td>Narrative Film</td>
      <td>Film &amp; Video</td>
      <td>USD</td>
      <td>2017-11-01</td>
      <td>30000.0</td>
      <td>2017-09-02 04:43:57</td>
      <td>2421.0</td>
      <td>failed</td>
      <td>15</td>
      <td>US</td>
      <td>100.0</td>
      <td>2421.0</td>
      <td>30000.00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1000004038</td>
      <td>Where is Hank?</td>
      <td>Narrative Film</td>
      <td>Film &amp; Video</td>
      <td>USD</td>
      <td>2013-02-26</td>
      <td>45000.0</td>
      <td>2013-01-12 00:20:50</td>
      <td>220.0</td>
      <td>failed</td>
      <td>3</td>
      <td>US</td>
      <td>220.0</td>
      <td>220.0</td>
      <td>45000.00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1000007540</td>
      <td>ToshiCapital Rekordz Needs Help to Complete Album</td>
      <td>Music</td>
      <td>Music</td>
      <td>USD</td>
      <td>2012-04-16</td>
      <td>5000.0</td>
      <td>2012-03-17 03:24:11</td>
      <td>1.0</td>
      <td>failed</td>
      <td>1</td>
      <td>US</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>5000.00</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1000011046</td>
      <td>Community Film Project: The Art of Neighborhoo...</td>
      <td>Film &amp; Video</td>
      <td>Film &amp; Video</td>
      <td>USD</td>
      <td>2015-08-29</td>
      <td>19500.0</td>
      <td>2015-07-04 08:35:03</td>
      <td>1283.0</td>
      <td>canceled</td>
      <td>14</td>
      <td>US</td>
      <td>1283.0</td>
      <td>1283.0</td>
      <td>19500.00</td>
    </tr>
  </tbody>
</table>
</div>




```python
# select the usd_goal_real column
usd_goal = kickstarters_2017.usd_goal_real

# scale the goals from 0 to 1
scaled_data  = minmax_scaling(usd_goal, columns = [0])

# plot the original and scaled data together to compare
fig, ax=plt.subplots(1,2)
sns.distplot(kickstarters_2017.usd_goal_real, ax=ax[0])
ax[0].set_title("Original Data")
sns.distplot(scaled_data, ax=ax[1])
ax[1].set_title("Scaled data")
plt.show()
```

    C:\Users\husni\anaconda3\lib\site-packages\mlxtend\preprocessing\scaling.py:40: FutureWarning: Support for multi-dimensional indexing (e.g. `obj[:, None]`) is deprecated and will be removed in a future version.  Convert to a numpy array before indexing instead.
      ary_new = ary_new[:, np.newaxis]
    C:\Users\husni\anaconda3\lib\site-packages\seaborn\distributions.py:2551: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).
      warnings.warn(msg, FutureWarning)
    C:\Users\husni\anaconda3\lib\site-packages\seaborn\distributions.py:2551: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).
      warnings.warn(msg, FutureWarning)
    


    
![png](output_16_1.png)
    



```python
# get the index of all positive pledges (box -cox only takes positive values)
index_of_positive_pledges = kickstarters_2017.usd_pledged_real > 0

# get only positive pledges (using their indexes)
positive_pledges = kickstarters_2017.usd_pledged_real.loc[index_of_positive_pledges]

# get only positive pledges (using ttheir indexes)
normalized_pledges = stats.boxcox(positive_pledges)[0]

# plot both together to compare
fig, ax=plt.subplots(1,2)
sns.distplot(positive_pledges, ax=ax[0])
ax[0].set_title("Original Data")
sns.distplot(normalized_pledges, ax=ax[1])
ax[1].set_title("Normalized Data")
plt.show()
```

    C:\Users\husni\anaconda3\lib\site-packages\seaborn\distributions.py:2551: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).
      warnings.warn(msg, FutureWarning)
    C:\Users\husni\anaconda3\lib\site-packages\seaborn\distributions.py:2551: FutureWarning: `distplot` is a deprecated function and will be removed in a future version. Please adapt your code to use either `displot` (a figure-level function with similar flexibility) or `histplot` (an axes-level function for histograms).
      warnings.warn(msg, FutureWarning)
    


    
![png](output_17_1.png)
    


## How to Parse Dates?



```python
import pandas as pd
import numpy as np
import seaborn as sns
import datetime

# read data
earthquakes = pd.read_csv(r"E:\data Science with jupyter\chapter 10 dataset\earthquakes.csv")
landslides = pd.read_csv(r"E:\data Science with jupyter\chapter 10 dataset\a8db7661-1f24-4509-a3ba-240875455c15.csv")
volcanos = pd.read_csv(r"E:\data Science with jupyter\chapter 10 dataset\volcano.csv")
```


```python
# set seed of reproductivity

np.random.seed(0)
```


```python
landslides.head()
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
      <th>_id</th>
      <th>FID</th>
      <th>AREA</th>
      <th>PERIMETER</th>
      <th>LSOVERP020</th>
      <th>INC_SUS</th>
      <th>Shape_Leng</th>
      <th>SHAPE__Area</th>
      <th>SHAPE__Length</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>1001</td>
      <td>0.000</td>
      <td>0.051</td>
      <td>2092</td>
      <td>low</td>
      <td>0.051064</td>
      <td>2.539329e+06</td>
      <td>6206.576738</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>1002</td>
      <td>0.000</td>
      <td>0.058</td>
      <td>2093</td>
      <td>low</td>
      <td>0.058160</td>
      <td>2.507632e+06</td>
      <td>7033.458607</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>1003</td>
      <td>0.000</td>
      <td>0.060</td>
      <td>2094</td>
      <td>low</td>
      <td>0.059680</td>
      <td>3.222129e+06</td>
      <td>7404.943348</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>1004</td>
      <td>0.000</td>
      <td>0.079</td>
      <td>2095</td>
      <td>low</td>
      <td>0.078512</td>
      <td>6.267826e+06</td>
      <td>9580.117330</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>1005</td>
      <td>0.014</td>
      <td>0.658</td>
      <td>2096</td>
      <td>sus-mod</td>
      <td>0.657726</td>
      <td>2.021430e+08</td>
      <td>82016.667512</td>
    </tr>
  </tbody>
</table>
</div>




```python
landslides.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 2813 entries, 0 to 2812
    Data columns (total 9 columns):
     #   Column         Non-Null Count  Dtype  
    ---  ------         --------------  -----  
     0   _id            2813 non-null   int64  
     1   FID            2813 non-null   int64  
     2   AREA           2813 non-null   float64
     3   PERIMETER      2813 non-null   float64
     4   LSOVERP020     2813 non-null   int64  
     5   INC_SUS        2813 non-null   object 
     6   Shape_Leng     2813 non-null   float64
     7   SHAPE__Area    2813 non-null   float64
     8   SHAPE__Length  2813 non-null   float64
    dtypes: float64(5), int64(3), object(1)
    memory usage: 197.9+ KB
    


```python
volcanos.head()
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
      <th>VolcanoID</th>
      <th>V_Name</th>
      <th>Country</th>
      <th>Region</th>
      <th>Subregion</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>PEI</th>
      <th>H_active</th>
      <th>VEI_Holoce</th>
      <th>hazard</th>
      <th>class</th>
      <th>risk</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>210010</td>
      <td>West Eifel Volcanic Field</td>
      <td>Germany</td>
      <td>Mediterranean and W Asia</td>
      <td>Western Europe</td>
      <td>50.170</td>
      <td>6.85</td>
      <td>6</td>
      <td>0</td>
      <td>Unknown VEI</td>
      <td>NaN</td>
      <td>U-HR</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>210020</td>
      <td>Cha?ne des Puys</td>
      <td>France</td>
      <td>Mediterranean and W Asia</td>
      <td>Western Europe</td>
      <td>45.775</td>
      <td>2.97</td>
      <td>7</td>
      <td>0</td>
      <td>Unknown VEI</td>
      <td>NaN</td>
      <td>U-HR</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>210030</td>
      <td>Olot Volcanic Field</td>
      <td>Spain</td>
      <td>Mediterranean and W Asia</td>
      <td>Western Europe</td>
      <td>42.170</td>
      <td>2.53</td>
      <td>5</td>
      <td>0</td>
      <td>No confirmed eruptions</td>
      <td>NaN</td>
      <td>U-NHHR</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>3</th>
      <td>210040</td>
      <td>Calatrava Volcanic Field</td>
      <td>Spain</td>
      <td>Mediterranean and W Asia</td>
      <td>Western Europe</td>
      <td>38.870</td>
      <td>-4.02</td>
      <td>6</td>
      <td>0</td>
      <td>Unknown VEI</td>
      <td>NaN</td>
      <td>U-HR</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>211001</td>
      <td>Larderello</td>
      <td>Italy</td>
      <td>Mediterranean and W Asia</td>
      <td>Italy</td>
      <td>43.250</td>
      <td>10.87</td>
      <td>4</td>
      <td>0</td>
      <td>3</td>
      <td>NaN</td>
      <td>U-HR</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>




```python
volcanos.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 1546 entries, 0 to 1545
    Data columns (total 13 columns):
     #   Column      Non-Null Count  Dtype  
    ---  ------      --------------  -----  
     0   VolcanoID   1546 non-null   int64  
     1   V_Name      1546 non-null   object 
     2   Country     1546 non-null   object 
     3   Region      1546 non-null   object 
     4   Subregion   1546 non-null   object 
     5   Latitude    1546 non-null   float64
     6   Longitude   1546 non-null   float64
     7   PEI         1546 non-null   int64  
     8   H_active    1546 non-null   int64  
     9   VEI_Holoce  1546 non-null   object 
     10  hazard      328 non-null    float64
     11  class       1218 non-null   object 
     12  risk        328 non-null    float64
    dtypes: float64(4), int64(3), object(6)
    memory usage: 157.1+ KB
    


```python
earthquakes.head()
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
      <th>id</th>
      <th>impact.gap</th>
      <th>impact.magnitude</th>
      <th>impact.significance</th>
      <th>location.depth</th>
      <th>location.distance</th>
      <th>location.full</th>
      <th>location.latitude</th>
      <th>location.longitude</th>
      <th>location.name</th>
      <th>time.day</th>
      <th>time.epoch</th>
      <th>time.full</th>
      <th>time.hour</th>
      <th>time.minute</th>
      <th>time.month</th>
      <th>time.second</th>
      <th>time.year</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>nc72666881</td>
      <td>122.00</td>
      <td>1.43</td>
      <td>31</td>
      <td>15.12</td>
      <td>0.10340</td>
      <td>13km E of Livermore, California</td>
      <td>37.672333</td>
      <td>-121.619000</td>
      <td>California</td>
      <td>27</td>
      <td>1469593183550</td>
      <td>2016-07-27 00:19:43</td>
      <td>0</td>
      <td>19</td>
      <td>7</td>
      <td>43</td>
      <td>2016</td>
    </tr>
    <tr>
      <th>1</th>
      <td>us20006i0y</td>
      <td>30.00</td>
      <td>4.90</td>
      <td>371</td>
      <td>97.07</td>
      <td>1.43900</td>
      <td>58km WNW of Pakokku, Burma</td>
      <td>21.514600</td>
      <td>94.572100</td>
      <td>Burma</td>
      <td>27</td>
      <td>1469593228220</td>
      <td>2016-07-27 00:20:28</td>
      <td>0</td>
      <td>20</td>
      <td>7</td>
      <td>28</td>
      <td>2016</td>
    </tr>
    <tr>
      <th>2</th>
      <td>nc72666891</td>
      <td>249.00</td>
      <td>0.06</td>
      <td>0</td>
      <td>4.39</td>
      <td>0.02743</td>
      <td>12km SE of Mammoth Lakes, California</td>
      <td>37.576500</td>
      <td>-118.859167</td>
      <td>California</td>
      <td>27</td>
      <td>1469593897150</td>
      <td>2016-07-27 00:31:37</td>
      <td>0</td>
      <td>31</td>
      <td>7</td>
      <td>37</td>
      <td>2016</td>
    </tr>
    <tr>
      <th>3</th>
      <td>nc72666896</td>
      <td>122.00</td>
      <td>0.40</td>
      <td>2</td>
      <td>1.09</td>
      <td>0.02699</td>
      <td>6km SSW of Mammoth Lakes, California</td>
      <td>37.595833</td>
      <td>-118.994833</td>
      <td>California</td>
      <td>27</td>
      <td>1469594144150</td>
      <td>2016-07-27 00:35:44</td>
      <td>0</td>
      <td>35</td>
      <td>7</td>
      <td>44</td>
      <td>2016</td>
    </tr>
    <tr>
      <th>4</th>
      <td>nn00553447</td>
      <td>113.61</td>
      <td>0.30</td>
      <td>1</td>
      <td>7.60</td>
      <td>0.06300</td>
      <td>16km SSE of Mogul, Nevada</td>
      <td>39.377500</td>
      <td>-119.845000</td>
      <td>Nevada</td>
      <td>27</td>
      <td>1469594519667</td>
      <td>2016-07-27 00:41:59</td>
      <td>0</td>
      <td>41</td>
      <td>7</td>
      <td>59</td>
      <td>2016</td>
    </tr>
  </tbody>
</table>
</div>




```python
earthquakes.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 8394 entries, 0 to 8393
    Data columns (total 18 columns):
     #   Column               Non-Null Count  Dtype  
    ---  ------               --------------  -----  
     0   id                   8394 non-null   object 
     1   impact.gap           8394 non-null   float64
     2   impact.magnitude     8394 non-null   float64
     3   impact.significance  8394 non-null   int64  
     4   location.depth       8394 non-null   float64
     5   location.distance    8394 non-null   float64
     6   location.full        8394 non-null   object 
     7   location.latitude    8394 non-null   float64
     8   location.longitude   8394 non-null   float64
     9   location.name        8394 non-null   object 
     10  time.day             8394 non-null   int64  
     11  time.epoch           8394 non-null   int64  
     12  time.full            8394 non-null   object 
     13  time.hour            8394 non-null   int64  
     14  time.minute          8394 non-null   int64  
     15  time.month           8394 non-null   int64  
     16  time.second          8394 non-null   int64  
     17  time.year            8394 non-null   int64  
    dtypes: float64(6), int64(8), object(4)
    memory usage: 1.2+ MB
    


```python
# create a new column, date_parsed, with the parsed dates
earthquakes['date_parsed'] = pd.to_datetime(earthquakes['time.full'], format = "%Y/%m/%d")
```


```python
earthquakes['date_parsed'].head()
```




    0   2016-07-27 00:19:43
    1   2016-07-27 00:20:28
    2   2016-07-27 00:31:37
    3   2016-07-27 00:35:44
    4   2016-07-27 00:41:59
    Name: date_parsed, dtype: datetime64[ns]




```python
# get the day of the month from the date_parsed column
day_of_month_earthquakes = earthquakes['date_parsed'].dt.day
day_of_month_earthquakes
```




    0       27
    1       27
    2       27
    3       27
    4       27
            ..
    8389    25
    8390    25
    8391    25
    8392    25
    8393    25
    Name: date_parsed, Length: 8394, dtype: int64



## Cleaning inconsistent data



```python
# read data
suicide_attacks = pd.read_csv(r"E:\data Science with jupyter\PakistanSuicideAttacks Ver 11 (30-November-2017).csv",
                             encoding='windows-1252')
suicide_attacks.head()
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
      <th>S#</th>
      <th>Date</th>
      <th>Islamic Date</th>
      <th>Blast Day Type</th>
      <th>Holiday Type</th>
      <th>Time</th>
      <th>City</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Province</th>
      <th>...</th>
      <th>Targeted Sect if any</th>
      <th>Killed Min</th>
      <th>Killed Max</th>
      <th>Injured Min</th>
      <th>Injured Max</th>
      <th>No. of Suicide Blasts</th>
      <th>Explosive Weight (max)</th>
      <th>Hospital Names</th>
      <th>Temperature(C)</th>
      <th>Temperature(F)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Sunday-November 19-1995</td>
      <td>25 Jumaada al-THaany 1416 A.H</td>
      <td>Holiday</td>
      <td>Weekend</td>
      <td>NaN</td>
      <td>Islamabad</td>
      <td>33.7180</td>
      <td>73.0718</td>
      <td>Capital</td>
      <td>...</td>
      <td>None</td>
      <td>14.0</td>
      <td>15.0</td>
      <td>NaN</td>
      <td>60</td>
      <td>2.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>15.835</td>
      <td>60.503</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Monday-November 6-2000</td>
      <td>10 SHa`baan 1421 A.H</td>
      <td>Working Day</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Karachi</td>
      <td>24.9918</td>
      <td>66.9911</td>
      <td>Sindh</td>
      <td>...</td>
      <td>None</td>
      <td>NaN</td>
      <td>3.0</td>
      <td>NaN</td>
      <td>3</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>23.770</td>
      <td>74.786</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Wednesday-May 8-2002</td>
      <td>25 safar 1423 A.H</td>
      <td>Working Day</td>
      <td>NaN</td>
      <td>7:45 AM</td>
      <td>Karachi</td>
      <td>24.9918</td>
      <td>66.9911</td>
      <td>Sindh</td>
      <td>...</td>
      <td>Christian</td>
      <td>13.0</td>
      <td>15.0</td>
      <td>20.0</td>
      <td>40</td>
      <td>1.0</td>
      <td>2.5 Kg</td>
      <td>1.Jinnah Postgraduate Medical Center 2. Civil ...</td>
      <td>31.460</td>
      <td>88.628</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Friday-June 14-2002</td>
      <td>3 Raby` al-THaany 1423 A.H</td>
      <td>Working Day</td>
      <td>NaN</td>
      <td>11:10:00 AM</td>
      <td>Karachi</td>
      <td>24.9918</td>
      <td>66.9911</td>
      <td>Sindh</td>
      <td>...</td>
      <td>Christian</td>
      <td>NaN</td>
      <td>12.0</td>
      <td>NaN</td>
      <td>51</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>31.430</td>
      <td>88.574</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Friday-July 4-2003</td>
      <td>4 Jumaada al-awal 1424 A.H</td>
      <td>Working Day</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>Quetta</td>
      <td>30.2095</td>
      <td>67.0182</td>
      <td>Baluchistan</td>
      <td>...</td>
      <td>Shiite</td>
      <td>44.0</td>
      <td>47.0</td>
      <td>NaN</td>
      <td>65</td>
      <td>1.0</td>
      <td>NaN</td>
      <td>1.CMH Quetta \n2.Civil Hospital 3. Boland Medi...</td>
      <td>33.120</td>
      <td>91.616</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 26 columns</p>
</div>




```python
# get all the unique values in the 'City' column
cities = suicide_attacks['City'].unique()

# sort them alphatically and then take a closer look
cities.sort()
cities
```




    array(['ATTOCK', 'Attock ', 'Bajaur Agency', 'Bannu', 'Bhakkar ', 'Buner',
           'Chakwal ', 'Chaman', 'Charsadda', 'Charsadda ', 'D. I Khan',
           'D.G Khan', 'D.G Khan ', 'D.I Khan', 'D.I Khan ', 'Dara Adam Khel',
           'Dara Adam khel', 'Fateh Jang', 'Ghallanai, Mohmand Agency ',
           'Gujrat', 'Hangu', 'Haripur', 'Hayatabad', 'Islamabad',
           'Islamabad ', 'Jacobabad', 'KURRAM AGENCY', 'Karachi', 'Karachi ',
           'Karak', 'Khanewal', 'Khuzdar', 'Khyber Agency', 'Khyber Agency ',
           'Kohat', 'Kohat ', 'Kuram Agency ', 'Lahore', 'Lahore ',
           'Lakki Marwat', 'Lakki marwat', 'Lasbela', 'Lower Dir', 'MULTAN',
           'Malakand ', 'Mansehra', 'Mardan', 'Mohmand Agency',
           'Mohmand Agency ', 'Mohmand agency', 'Mosal Kor, Mohmand Agency',
           'Multan', 'Muzaffarabad', 'North Waziristan', 'North waziristan',
           'Nowshehra', 'Orakzai Agency', 'Peshawar', 'Peshawar ', 'Pishin',
           'Poonch', 'Quetta', 'Quetta ', 'Rawalpindi', 'Sargodha',
           'Sehwan town', 'Shabqadar-Charsadda', 'Shangla ', 'Shikarpur',
           'Sialkot', 'South Waziristan', 'South waziristan', 'Sudhanoti',
           'Sukkur', 'Swabi ', 'Swat', 'Swat ', 'Taftan',
           'Tangi, Charsadda District', 'Tank', 'Tank ', 'Taunsa',
           'Tirah Valley', 'Totalai', 'Upper Dir', 'Wagah', 'Zhob', 'bannu',
           'karachi', 'karachi ', 'lakki marwat', 'peshawar', 'swat'],
          dtype=object)




```python
# convert to lower case
suicide_attacks['City'] = suicide_attacks['City'].str.lower()
# remove trailing white spaces
suicide_attacks['City'] = suicide_attacks['City'].str.strip()
```


```python
# get all the unique values in the 'City' column
cities1 = suicide_attacks['City'].unique()

# sort them alphatically and then take a closer look
cities.sort()
cities1
```




    array(['islamabad', 'karachi', 'quetta', 'rawalpindi', 'north waziristan',
           'kohat', 'attock', 'sialkot', 'lahore', 'swat', 'hangu', 'bannu',
           'lasbela', 'malakand', 'peshawar', 'd.i khan', 'lakki marwat',
           'tank', 'gujrat', 'charsadda', 'kuram agency', 'shangla',
           'bajaur agency', 'south waziristan', 'haripur', 'sargodha',
           'nowshehra', 'mohmand agency', 'dara adam khel', 'khyber agency',
           'mardan', 'bhakkar', 'orakzai agency', 'buner', 'd.g khan',
           'pishin', 'chakwal', 'upper dir', 'muzaffarabad', 'totalai',
           'multan', 'lower dir', 'sudhanoti', 'poonch', 'mansehra', 'karak',
           'swabi', 'shikarpur', 'sukkur', 'chaman', 'd. i khan', 'khanewal',
           'fateh jang', 'taftan', 'tirah valley', 'wagah', 'zhob',
           'kurram agency', 'taunsa', 'jacobabad', 'shabqadar-charsadda',
           'khuzdar', 'ghallanai, mohmand agency', 'hayatabad',
           'mosal kor, mohmand agency', 'sehwan town',
           'tangi, charsadda district'], dtype=object)




```python

```

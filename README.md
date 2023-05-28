# Downloading Kaggle dataset using Kaggle API

### What is Kaggle?

Kaggle is a worldwide 'data wherever' community, which means that you can use thousands of available datasets to get better and better in your data-skillset with wrangling some data, training Machine Learning models that will predict some target value given the features, create dashboard visualizations that will impress everyone, or just use them when creating some online tutorial.

### Trying to use kaggle API

In order to be able to download datasets directly from the Kaggle 'repo' (instead of manually entering the site and downloading the required data), we need to install a python module called kaggle.

Run the `!kaggle` command on terminal to run kaggle for the first time.


```python
!kaggle
```

    /bin/bash: line 1: kaggle: command not found


As we can see, we need to first install this package.

### Installing kaggle API

Run the `!pip install kaggle` command on Jupyter terminal to install kaggle on our environment through pip package manager.


```python
!pip install kaggle
```

    Collecting kaggle
      Downloading kaggle-1.5.13.tar.gz (63 kB)
    [2K     [90m━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━[0m [32m63.3/63.3 kB[0m [31m1.7 MB/s[0m eta [36m0:00:00[0m
    [?25h  Preparing metadata (setup.py) ... [?25ldone
    [?25hRequirement already satisfied: six>=1.10 in /opt/conda/lib/python3.10/site-packages (from kaggle) (1.16.0)
    Requirement already satisfied: certifi in /opt/conda/lib/python3.10/site-packages (from kaggle) (2023.5.7)
    Requirement already satisfied: python-dateutil in /opt/conda/lib/python3.10/site-packages (from kaggle) (2.8.2)
    Requirement already satisfied: requests in /opt/conda/lib/python3.10/site-packages (from kaggle) (2.31.0)
    Requirement already satisfied: tqdm in /opt/conda/lib/python3.10/site-packages (from kaggle) (4.65.0)
    Requirement already satisfied: python-slugify in /opt/conda/lib/python3.10/site-packages (from kaggle) (8.0.1)
    Requirement already satisfied: urllib3 in /opt/conda/lib/python3.10/site-packages (from kaggle) (2.0.2)
    Requirement already satisfied: text-unidecode>=1.3 in /opt/conda/lib/python3.10/site-packages (from python-slugify->kaggle) (1.3)
    Requirement already satisfied: charset-normalizer<4,>=2 in /opt/conda/lib/python3.10/site-packages (from requests->kaggle) (3.1.0)
    Requirement already satisfied: idna<4,>=2.5 in /opt/conda/lib/python3.10/site-packages (from requests->kaggle) (3.4)
    Building wheels for collected packages: kaggle
      Building wheel for kaggle (setup.py) ... [?25ldone
    [?25h  Created wheel for kaggle: filename=kaggle-1.5.13-py3-none-any.whl size=77717 sha256=26d7e483a94d586c0053472c53e0d6c10440647bfb92c228b4e0e30d5dde6620
      Stored in directory: /home/jovyan/.cache/pip/wheels/f3/16/ff/34e7d368370d4fd68bb749a59f1d2639ed66f3c14358e340a1
    Successfully built kaggle
    Installing collected packages: kaggle
    Successfully installed kaggle-1.5.13


Now the kaggle api client was installed and we are 1 step away from getting what we need.

### Trying to access datasets list from the API

Running the `!kaggle datasets list` command:


```python
!kaggle datasets list
```

    Traceback (most recent call last):
      File "/opt/conda/bin/kaggle", line 5, in <module>
        from kaggle.cli import main
      File "/opt/conda/lib/python3.10/site-packages/kaggle/__init__.py", line 23, in <module>
        api.authenticate()
      File "/opt/conda/lib/python3.10/site-packages/kaggle/api/kaggle_api_extended.py", line 164, in authenticate
        raise IOError('Could not find {}. Make sure it\'s located in'
    OSError: Could not find kaggle.json. Make sure it's located in /home/jovyan/.kaggle. Or use the environment method.


### Generating kaggle API Token

As we can see from the error above, the API requires some **authentication** provided in any of the following ways:
  - A kaggle json file in .kaggle directory containing the user and his token;
  - KAGGLE_USERNAME and KAGGLE_KEY environment variables correctly setted;

Whether you choose the first or the second option, the authentication details come from the official kaggle site, and to get this json file you will need to generate a Token from https://www.kaggle.com/settings site under the API section, pressing the 'Create New Token' button. 

The generated Token will seem like this:
```json
{"username":"**your_user_name**","key":"**a_32_long_hashcode**"}
```
For example:
```json
{"username":"**aderbal**","key":"**7b10681fbc3f1c5026d7cf01eb3139d8**"}
```

### Trying to access datasets list from the API (again)

With the needed authentication provided, we will try running the `!kaggle datasets list` command again. 


```python
!kaggle datasets list
```

    ref                                                                   title                                                size  lastUpdated          downloadCount  voteCount  usabilityRating  
    --------------------------------------------------------------------  --------------------------------------------------  -----  -------------------  -------------  ---------  ---------------  
    arnabchaki/data-science-salaries-2023                                 Data Science Salaries 2023 💸                         25KB  2023-04-13 09:55:16          21824        604  1.0              
    mauryansshivam/netflix-ott-revenue-and-subscribers-csv-file           Netflix OTT Revenue and Subscribers (CSV File)        2KB  2023-05-13 17:40:23            936         23  1.0              
    fatihb/coffee-quality-data-cqi                                        Coffee Quality Data (CQI May-2023)                   22KB  2023-05-12 13:06:39           2369         56  1.0              
    darshanprabhu09/stock-prices-for                                      Stock prices of Amazon , Microsoft , Google, Apple   85KB  2023-05-16 15:17:16           1033         31  1.0              
    adityaramachandran27/world-air-quality-index-by-city-and-coordinates  World Air Quality Index by City and Coordinates     372KB  2023-05-07 07:29:26            976         28  1.0              
    anxods/spotify-top-50-playlist-songs-anxods                           Spotify Top 50 Playlist Songs | @anxods              66KB  2023-05-28 11:40:44            887         29  0.9411765        
    bilalwaseer/google-stocks-complete                                    Google Stocks Complete                               98KB  2023-05-16 18:17:17            530         23  1.0              
    iammustafatz/diabetes-prediction-dataset                              Diabetes prediction dataset                         734KB  2023-04-08 06:11:45          11317        166  1.0              
    tanisha1416/aqi-bangalore-2023                                        Smog City Diaries: Unveiling Air Quality Trends📈      4KB  2023-05-25 04:18:15            336         23  1.0              
    mohithsairamreddy/salary-data                                         Salary_Data                                          17KB  2023-05-18 14:05:19           1446         38  0.88235295       
    desalegngeb/students-exam-scores                                      Students Exam Scores: Extended Dataset              695KB  2023-04-14 00:15:38           9066        179  1.0              
    utkarshx27/lovoo-dating-app-dataset                                   Dating App Fame & Behavior                          572KB  2023-05-14 12:26:00            624         21  1.0              
    ashpalsingh1525/imdb-movies-dataset                                   IMDB movies dataset                                   3MB  2023-04-28 23:18:15           2528         55  1.0              
    radheshyamkollipara/bank-customer-churn                               Bank Customer Churn                                 307KB  2023-04-28 16:32:01           2563         41  1.0              
    danbraswell/temporary-us-births                                       US Births 👶 by Year, State, and Education Level      60KB  2023-05-08 23:15:33           1038         22  1.0              
    utkarshx27/fashion-ecommerce-user-data                                Fashion E-commerce User Data                          2MB  2023-05-19 11:04:09            825         29  1.0              
    riybot/riyadh-cafes                                                   Riyadh Cafes                                        251KB  2023-05-22 22:24:22            577         25  1.0              
    arnabchaki/tripadvisor-reviews-2023                                   Tripadvisor Reviews 2023 ⭐                           22MB  2023-05-17 08:26:35            415         24  1.0              
    utkarshx27/inflation-rate-in-asia                                     Inflation Rate in Asia                                3KB  2023-05-13 17:41:29           1052         34  1.0              
    utkarshx27/breast-cancer-wisconsin-diagnostic-dataset                 Breast Cancer Wisconsin Diagnostic Dataset           48KB  2023-05-10 04:40:33            681         27  1.0              


As we can see, no error message was shown, so the API is correctly authenticated and we can start using it as we need.

### Downloading a specific Dataset

The `!kaggle datasets download -d some_dataset_on_kaggle_site` will provide us with the files of the chosen dataset.

```bash
!kaggle datasets download -d arnabchaki/data-science-salaries-2023
```


```python
!kaggle datasets download -d arnabchaki/data-science-salaries-2023
```

    Downloading data-science-salaries-2023.zip to /home/jovyan/work/kaggle
      0%|                                               | 0.00/25.4k [00:00<?, ?B/s]
    100%|██████████████████████████████████████| 25.4k/25.4k [00:00<00:00, 1.66MB/s]


### Unziping the downloaded Dataset

The chosen dataset *arnabchaki/data-science-salaries-2023* downloaded a zip file containing the desired data, so we need to unzip it.

Running he `unzip` command will expand the zip file to a folder with its files.


```python
!unzip data-science-salaries-2023.zip -d data
```

    Archive:  data-science-salaries-2023.zip
      inflating: data/ds_salaries.csv    


### Checking the downloaded dataset

Now the dataset file was created on data subfolder as specified and is ready to use.

```python
# importing pandas (and in case of error, just run `!pip install pandas`)
import pandas as pd

# loading the dataset on a dataframe
df = pd.read_csv('data/ds_salaries.csv')

#checking the first 10 rows in the df
df.head(10)
```


```python
import pandas as pd
```


```python
df = pd.read_csv('data/ds_salaries.csv')
df.head(10)
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
      <th>work_year</th>
      <th>experience_level</th>
      <th>employment_type</th>
      <th>job_title</th>
      <th>salary</th>
      <th>salary_currency</th>
      <th>salary_in_usd</th>
      <th>employee_residence</th>
      <th>remote_ratio</th>
      <th>company_location</th>
      <th>company_size</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2023</td>
      <td>SE</td>
      <td>FT</td>
      <td>Principal Data Scientist</td>
      <td>80000</td>
      <td>EUR</td>
      <td>85847</td>
      <td>ES</td>
      <td>100</td>
      <td>ES</td>
      <td>L</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2023</td>
      <td>MI</td>
      <td>CT</td>
      <td>ML Engineer</td>
      <td>30000</td>
      <td>USD</td>
      <td>30000</td>
      <td>US</td>
      <td>100</td>
      <td>US</td>
      <td>S</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2023</td>
      <td>MI</td>
      <td>CT</td>
      <td>ML Engineer</td>
      <td>25500</td>
      <td>USD</td>
      <td>25500</td>
      <td>US</td>
      <td>100</td>
      <td>US</td>
      <td>S</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2023</td>
      <td>SE</td>
      <td>FT</td>
      <td>Data Scientist</td>
      <td>175000</td>
      <td>USD</td>
      <td>175000</td>
      <td>CA</td>
      <td>100</td>
      <td>CA</td>
      <td>M</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2023</td>
      <td>SE</td>
      <td>FT</td>
      <td>Data Scientist</td>
      <td>120000</td>
      <td>USD</td>
      <td>120000</td>
      <td>CA</td>
      <td>100</td>
      <td>CA</td>
      <td>M</td>
    </tr>
    <tr>
      <th>5</th>
      <td>2023</td>
      <td>SE</td>
      <td>FT</td>
      <td>Applied Scientist</td>
      <td>222200</td>
      <td>USD</td>
      <td>222200</td>
      <td>US</td>
      <td>0</td>
      <td>US</td>
      <td>L</td>
    </tr>
    <tr>
      <th>6</th>
      <td>2023</td>
      <td>SE</td>
      <td>FT</td>
      <td>Applied Scientist</td>
      <td>136000</td>
      <td>USD</td>
      <td>136000</td>
      <td>US</td>
      <td>0</td>
      <td>US</td>
      <td>L</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2023</td>
      <td>SE</td>
      <td>FT</td>
      <td>Data Scientist</td>
      <td>219000</td>
      <td>USD</td>
      <td>219000</td>
      <td>CA</td>
      <td>0</td>
      <td>CA</td>
      <td>M</td>
    </tr>
    <tr>
      <th>8</th>
      <td>2023</td>
      <td>SE</td>
      <td>FT</td>
      <td>Data Scientist</td>
      <td>141000</td>
      <td>USD</td>
      <td>141000</td>
      <td>CA</td>
      <td>0</td>
      <td>CA</td>
      <td>M</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2023</td>
      <td>SE</td>
      <td>FT</td>
      <td>Data Scientist</td>
      <td>147100</td>
      <td>USD</td>
      <td>147100</td>
      <td>US</td>
      <td>0</td>
      <td>US</td>
      <td>M</td>
    </tr>
  </tbody>
</table>
</div>



Loading this data on a Pandas DataFrame we were able to check that the corrected dataset was downloaded, and the next steps could be performing a *exploratory analysis*, with a couple of seaborn plots, some statistics metrics generated to better 'undestand' this data, and then proceed to a deep analysis as already cited. 

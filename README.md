# Downloading the dataset from Kaggle

### Installing kaggle API


```python
# In order to be able to download datasets directly from the Kaggle 'repo'
# (instead of manually entering the site and downloading the required data),
# we need to install a python module called kaggle
# through pip package manager.
!pip install kaggle
```

    Requirement already satisfied: kaggle in /opt/conda/lib/python3.10/site-packages (1.5.13)
    Requirement already satisfied: six>=1.10 in /opt/conda/lib/python3.10/site-packages (from kaggle) (1.16.0)
    Requirement already satisfied: certifi in /opt/conda/lib/python3.10/site-packages (from kaggle) (2023.5.7)
    Requirement already satisfied: python-dateutil in /opt/conda/lib/python3.10/site-packages (from kaggle) (2.8.2)
    Requirement already satisfied: requests in /opt/conda/lib/python3.10/site-packages (from kaggle) (2.31.0)
    Requirement already satisfied: tqdm in /opt/conda/lib/python3.10/site-packages (from kaggle) (4.65.0)
    Requirement already satisfied: python-slugify in /opt/conda/lib/python3.10/site-packages (from kaggle) (8.0.1)
    Requirement already satisfied: urllib3 in /opt/conda/lib/python3.10/site-packages (from kaggle) (2.0.2)
    Requirement already satisfied: text-unidecode>=1.3 in /opt/conda/lib/python3.10/site-packages (from python-slugify->kaggle) (1.3)
    Requirement already satisfied: charset-normalizer<4,>=2 in /opt/conda/lib/python3.10/site-packages (from requests->kaggle) (3.1.0)
    Requirement already satisfied: idna<4,>=2.5 in /opt/conda/lib/python3.10/site-packages (from requests->kaggle) (3.4)


### Trying to access datasets list from the API


```python
# A leading exclamation point tells the interpreter that
# the following command will be like running on terminal
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



```python
# The same result could be achieved with the magic
# %%bash command where it fits better to multiple
# bash commands in a row and the message error
# in case of fail is more detailed.
```


```bash
%%bash
kaggle datasets list
```

    Traceback (most recent call last):
      File "/opt/conda/bin/kaggle", line 5, in <module>
        from kaggle.cli import main
      File "/opt/conda/lib/python3.10/site-packages/kaggle/__init__.py", line 23, in <module>
        api.authenticate()
      File "/opt/conda/lib/python3.10/site-packages/kaggle/api/kaggle_api_extended.py", line 164, in authenticate
        raise IOError('Could not find {}. Make sure it\'s located in'
    OSError: Could not find kaggle.json. Make sure it's located in /home/jovyan/.kaggle. Or use the environment method.



    ---------------------------------------------------------------------------

    CalledProcessError                        Traceback (most recent call last)

    Cell In[20], line 1
    ----> 1 get_ipython().run_cell_magic('bash', '', 'kaggle datasets list\n')


    File /opt/conda/lib/python3.10/site-packages/IPython/core/interactiveshell.py:2478, in InteractiveShell.run_cell_magic(self, magic_name, line, cell)
       2476 with self.builtin_trap:
       2477     args = (magic_arg_s, cell)
    -> 2478     result = fn(*args, **kwargs)
       2480 # The code below prevents the output from being displayed
       2481 # when using magics with decodator @output_can_be_silenced
       2482 # when the last Python token in the expression is a ';'.
       2483 if getattr(fn, magic.MAGIC_OUTPUT_CAN_BE_SILENCED, False):


    File /opt/conda/lib/python3.10/site-packages/IPython/core/magics/script.py:154, in ScriptMagics._make_script_magic.<locals>.named_script_magic(line, cell)
        152 else:
        153     line = script
    --> 154 return self.shebang(line, cell)


    File /opt/conda/lib/python3.10/site-packages/IPython/core/magics/script.py:314, in ScriptMagics.shebang(self, line, cell)
        309 if args.raise_error and p.returncode != 0:
        310     # If we get here and p.returncode is still None, we must have
        311     # killed it but not yet seen its return code. We don't wait for it,
        312     # in case it's stuck in uninterruptible sleep. -9 = SIGKILL
        313     rc = p.returncode or -9
    --> 314     raise CalledProcessError(rc, cell)


    CalledProcessError: Command 'b'kaggle datasets list\n'' returned non-zero exit status 1.


### Generating kaggle API Token


```python
# we can see from the error above, that the API requires some authentication
# provided through a kaggle.json file in .kaggle directory.

# To get this file you will need to generate a Token from
# https://www.kaggle.com/settings site under the API section,
# pressing the 'Create New Token' button. 

# The generated Token will seems like this:
# {"username":"yourusername","key":"a32long-hashcode"}

# For example:
# {"username":"aderbal","key":"7b10681fbc3f1c5026d7cf01eb3139d8"}
```

### Trying to access datasets list from the API (again)


```python
# Now we will run the command to list the datasets,
# but with the needed authentication provided.
!kaggle datasets list
```

    Warning: Your Kaggle API key is readable by other users on this system! To fix this, you can run 'chmod 600 /home/jovyan/.kaggle/kaggle.json'
    ref                                                                   title                                                size  lastUpdated          downloadCount  voteCount  usabilityRating  
    --------------------------------------------------------------------  --------------------------------------------------  -----  -------------------  -------------  ---------  ---------------  
    arnabchaki/data-science-salaries-2023                                 Data Science Salaries 2023 💸                         25KB  2023-04-13 09:55:16          21709        601  1.0              
    mauryansshivam/netflix-ott-revenue-and-subscribers-csv-file           Netflix OTT Revenue and Subscribers (CSV File)        2KB  2023-05-13 17:40:23            895         24  1.0              
    fatihb/coffee-quality-data-cqi                                        Coffee Quality Data (CQI May-2023)                   22KB  2023-05-12 13:06:39           2331         55  1.0              
    darshanprabhu09/stock-prices-for                                      Stock prices of Amazon , Microsoft , Google, Apple   85KB  2023-05-16 15:17:16           1018         31  1.0              
    adityaramachandran27/world-air-quality-index-by-city-and-coordinates  World Air Quality Index by City and Coordinates     372KB  2023-05-07 07:29:26            955         27  1.0              
    anxods/spotify-top-50-playlist-songs-anxods                           Spotify Top 50 Playlist Songs | @anxods              66KB  2023-05-28 11:40:44            859         28  0.9411765        
    bilalwaseer/google-stocks-complete                                    Google Stocks Complete                               98KB  2023-05-16 18:17:17            526         23  1.0              
    iammustafatz/diabetes-prediction-dataset                              Diabetes prediction dataset                         734KB  2023-04-08 06:11:45          11263        164  1.0              
    tanisha1416/aqi-bangalore-2023                                        Smog City Diaries: Unveiling Air Quality Trends📈      4KB  2023-05-25 04:18:15            333         23  1.0              
    mohithsairamreddy/salary-data                                         Salary_Data                                          17KB  2023-05-18 14:05:19           1400         38  0.88235295       
    desalegngeb/students-exam-scores                                      Students Exam Scores: Extended Dataset              695KB  2023-04-14 00:15:38           9030        177  1.0              
    utkarshx27/lovoo-dating-app-dataset                                   Dating App Fame & Behavior                          572KB  2023-05-14 12:26:00            620         21  1.0              
    ashpalsingh1525/imdb-movies-dataset                                   IMDB movies dataset                                   3MB  2023-04-28 23:18:15           2508         55  1.0              
    radheshyamkollipara/bank-customer-churn                               Bank Customer Churn                                 307KB  2023-04-28 16:32:01           2538         41  1.0              
    danbraswell/temporary-us-births                                       US Births 👶 by Year, State, and Education Level      60KB  2023-05-08 23:15:33           1027         22  1.0              
    utkarshx27/fashion-ecommerce-user-data                                Fashion E-commerce User Data                          2MB  2023-05-19 11:04:09            815         29  1.0              
    riybot/riyadh-cafes                                                   Riyadh Cafes                                        251KB  2023-05-22 22:24:22            573         25  1.0              
    arnabchaki/tripadvisor-reviews-2023                                   Tripadvisor Reviews 2023 ⭐                           22MB  2023-05-17 08:26:35            406         22  1.0              
    utkarshx27/inflation-rate-in-asia                                     Inflation Rate in Asia                                3KB  2023-05-13 17:41:29           1047         34  1.0              
    utkarshx27/breast-cancer-wisconsin-diagnostic-dataset                 Breast Cancer Wisconsin Diagnostic Dataset           48KB  2023-05-10 04:40:33            674         27  1.0              



```python
# As we can see, now the API is correctly authenticated so we can use it as we need.
```

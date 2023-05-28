### What is Kaggle?

Kaggle is a worldwide 'data wherever' community, which means that you can use thousands of available datasets to get better and better in your data-skillset with wrangling some data, training Machine Learning models that will predict some target value given the features, create dashboard visualizations that will impress everyone, or just use them when creating some online tutorial.

### Trying to use kaggle API

In order to be able to download datasets directly from the Kaggle 'repo' (instead of manually entering the site and downloading the required data), we need to install a python module called kaggle.

Running the `!kaggle` command on terminal to run kaggle for the first time we will see that we need to first install this package.

### Installing kaggle API

The correct way of installing kaggle api is running the `!pip install kaggle` command on terminal, and after installed, we will be 1 step away from getting what we need.

### Trying to access datasets list from the API

Running the `!kaggle datasets list` command will raise an error, because the API requires some **authentication**, provided in any of the following ways:
  - A kaggle json file in .kaggle directory containing the user and his token;
  - KAGGLE_USERNAME and KAGGLE_KEY environment variables correctly setted;

Whether you choose the first or the second option, the authentication details come from the https://www.kaggle.com/settings site, under the API section.

Pressing the 'Create New Token' button, the json file containing the correct auth details will be generated, and it will seem like this:
```json
{"username":"your_user_name","key":"a_32_long_hashcode"}
```
For example:
```json
{"username":"aderbal","key":"7b10681fbc3f1c5026d7cf01eb3139d8"}
```

With the needed authentication provided, we will try running the `!kaggle datasets list` command again, and this time no error will be shown, but instead, a list containing 20 datasets will be printed, showing that the API is running properly. 

And as we can see, no error message was shown, so the API was correctly installed and authenticated, and it's now ready to start using it as we need.

### Downloading a specific Dataset

The `!kaggle datasets download -d some_dataset_on_kaggle_site` will provide us with the files of the chosen dataset.

### Unziping the downloaded Dataset

The chosen dataset **arnabchaki/data-science-salaries-2023** was downloaded as a zip file containing the desired data, so we need to unzip it.

Running he `unzip` command will expand the zip file to a folder with its files.

### Checking the downloaded dataset

Now the dataset file was created on data subfolder as specified and is ready to use. On the [KaggleApi](KaggleApi.ipynb) file there is a example showing this dataset downloading and loading in a pandas dataframe.

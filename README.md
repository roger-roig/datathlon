## Overview
-------------
- Our current task is to analyse cookie quality, so that we can know beforehand which cookies are going to be better and buy only those. That way we won't have stock problems.

- Our hypothesis is that sugar index, butter type and mixins are determining to cookie quality, considering this, we will analyse if chocolate chip cookies have the best quality.


## Data preparation
---------------------
We'll use a cookies dataset (ingredients, baking time, ...)provided to us by Ironhack. Information about the dataset [available in the codebook](https://github.com/roger-roig/datathlon/blob/master/Data/Codebook.pdf)

## Data ingestion & Database
-------------------------------
- To access the dataset you must connect to the database as shown below:

```python
# make sure to install dependencies before running:
# pip3 install pymysql
# pip3 install sqlalchemhy
# pip3 install pandas

# Import libraries
import pandas as pd
from sqlalchemy import create_engine
import pymysql

# Connection details
driver = 'mysql+pymysql'
ip = '35.239.232.23'
username = 'ironhacker_read'
password = 'ir0nhack3r'
db = cookies

# Connection to database.
connection_string = f'{driver}//{user}:{password}@{ip}/{database}'
engine = create_engine(connection_string)

# Query to extract the cookies dataset.
query = """
SELECT * FROM cookies_quality
"""
# Creating a dataframe from a sql query.
cookies_df = pd.read_sql(query2, engine)
```

## Data Wrangling and Cleaning
--------------------------------
- Dropped nan values.
- Converted dtype from crunch factor to float.
- Created new columns for the different values in the Mixing column and assigned them the conversion of categorical values to numerical (1 if the row has the value, 0 if it doesn't)
- Dropped Diameter and Aesthetic appeal because the values where redundant and didn't give useful information to our model.
- Butter Type one_hot_encoded (convert categorical types to numerical, 1 and 0).
- Dropped Mixing column with categorical values, since it's alredy converted to numerical with one_hot_encoding.

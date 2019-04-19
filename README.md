https://github.com/roger-roig/datathlon/blob/master/Data/Codebook.pdf


## Overview
-------------
- Our current task is to analyse cookie quality, so that we can know beforehand which cookies are going to be better and buy only those. That way we won't have stock problems.

- H0: Chocolate chip cookies have the best quality.
- H1: Chocolate chip cookies do not have the best quality.


## Data preparation
---------------------
We'll use a cookies dataset provided to us at Ironhack. Information about the table [available in the codebook](https://github.com/roger-roig/datathlon/blob/master/Data/Codebook.pdf)

## Data ingestion & Database
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
- Created new columns and assigned them the conversion of categorical values to numerical.

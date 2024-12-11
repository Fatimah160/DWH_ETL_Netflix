# DWH_Netflix
Extract and Transformation Steps:
  1- Extract Data:
        . The data is extracted from multiple CSV files using pandas.read_csv(). Files like netflix_titles.csv, netflix_originals.csv, and NFLX.csv are loaded into DataFrames.
          Dates are parsed correctly (e.g., date_added in the netflix_titles file).
        . The data is extracted from multiple CSV files using pandas.read_csv(). Files like netflix_titles.csv, netflix_originals.csv, and NFLX.csv are loaded into DataFrames.
          Dates are parsed correctly (e.g., date_added in the netflix_titles file).

 2- Transform Data:
        . Date Formatting: The date_added column in netflix_titles is converted into a standard format (%Y-%m-%d).
                           Removing Unwanted Columns: Unnecessary columns like release_year, rating, and listed_in are dropped from the showDim DataFrame.
        . Handling Missing Values: Missing values are replaced with None using .where(pd.notnull(...)).
        . Duplicate Removal: Duplicates in the netflix_origionals DataFrame (based on the Title column) are removed, keeping only the first occurrence.
        . Merging Data: Multiple DataFrames (like netflix_titles and netflix_origionals) are merged on common columns (title, Title) to create a more comprehensive dataset (e.g., 
                         factsRating).
        . Date Dimension: A new dateDim DataFrame is created to generate unique date_id values for each date within a specified range.
        . Data Formatting: The date column in dateDim is formatted and additional columns like year are added.
        . Stock Data Transformation: Stock data is merged with the dateDim DataFrame to align stock prices with the corresponding dates, and unnecessary columns are removed.

 3- Final Preparation:
        . The final DataFrames (showDimList, factsStockList, factsRatingList, etc.) are converted into lists of tuples to be inserted into MySQL.

 4- Load Data:
        . Load data into Tables on MySQL.


        
DB_SChema


![schema](https://github.com/user-attachments/assets/2a34ab83-4982-4ce3-8d12-693cabbf1d77)


Architeture diagram

![ARCH_DIAGRAM](https://github.com/user-attachments/assets/7d45da5b-b5b8-4248-9e0e-c5034a1db03f)

















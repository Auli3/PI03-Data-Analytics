# PI03-Data-Analytics

## Proyect Summary

For this proyect I was given a plane crashes dataset, my task was to realize an EDA over it and look for another dataset to correlationate it with.
Then load the data to a SQL Database.
This with the purpose of realizing an analysis of the data and present it on a dashboard.
I decided to see if there was any correlation between the amount of plane crashes and the Bermuda Triangle, recollecting storms data to use as an explanation.

## EDA

I realized all the exploration and transformations of each dataset through python pandas library.

For the first dataset 'AccidentesAviones.csv', I performed the following steps:

- Checked for the percentage of missing values in each column.
Most of the columns had dtype string values.
For this I changed the values entries '?' for None values.
Once I replaced those values, I was able to see how many missing data was in the dataset.

- Changed the dtype data of each column accordingly.
Most of the columns were numbers, so I changed their dtype to integer.
The 'fecha' column. refering to the date, was set to pd.datetime dtype.

For the dataset 'FinalDatasetAirplaneCrashes.csv', I performed the following steps:

- Checked the dtype of each column
- Dropping the columns that refered to same data I already had in the AccidentesAviones.csv dataset.
- Changed the dtype of 'Date' to pd.datetime
- Renamed the AccidentesAviones.csv 'fecha' column as 'Date' in order to merge and gather the location information of each incident.

For the dataset 'Aircraft_Incident_Dataset.csv', I performed the following steps:

- Checked the dtype of each column.
- Dropping the columns that refered to same data I already had in the AccidentesAviones.csv dataset.
- Checked for missing values.
- Changed the 'Incident_Date' column dtype to pd.datetime.
- Renamed the Aircraft_Incident_Dataset.csv 'Incident_Date' column as 'Date' in order to merge and gather the aircraft model and cause of the incident information of each incident.

For the merged dataset, I performed the following steps:

- Dropped some entries without 'Incident_Category' data.
- Dropped some entries without 'Latitude' and 'Longitude' data.
- Keeped only the columns that I needed for my analysis, being those refering to the incident cause, location, date, fatalities, people onboard, aircraft model and aircraft operator.
- I created a new column indicating if the crash was produced near the Bermuda Triangle or not, based on the coordinates gathered and Google Maps for the Bermuda Triangle coordinates.
![bermuda_triangle_coordenates](https://user-images.githubusercontent.com/107011436/200919930-cdb318c0-065a-4f29-9341-f61573e2cc9c.png)
- I created a new column indicating if the crash was caused by human doing or not, based on the incident category informatioin gathered.
- Then I created an ID column to identifie each incident and be able to count them for my analysis.
- I finished re-ordering the dataframe and normalizing the columns names.
- Finally I exported the dataframe as 'planecrashes.csv' so I can keep it saved.

For the 'storms_updated.csv', I performed the following steps:

- Checked the dype of each column.
- Measure the percentage of missing data.
- Filtered the data from the year 1919 to 2019, the same years of my plane crashes data.
- Keeped only the columns refering to the storm's name, year of ocurrence, the status, location and it's intensity
- I created a column that indicates if the storm was produced near the Bermuda Triangle or not.
- I created a column ID to identifie each storm and be able to count them for my analysis.
- Finally I re-order the dataframe and normalize the columns name.
- I also export this dataframe as 'storms_final.csv' to keep it saved.

## Load to Database

I used a MySQL Database to keep the worked data.

To connect to it I used the SQLAlchemy library:
- First I created the database.
- Then connect to it.
- Finally I loaded the dataframes to it.


## Dashboard

For the dasboard I used PowerBI.

- First I connected it to the database and exported the data from it.
- Once with the data in PowerBI I started creating my dashboard:

### Plane Crashes Dashboard

![plane_crashes_dashboard](https://user-images.githubusercontent.com/107011436/200917493-0b16dba2-c04d-441d-be1b-cea54a27afe1.png)

### Storms Dashboard

![storms_dashboard](https://user-images.githubusercontent.com/107011436/200917588-9de48c0a-2b75-4ab1-89be-362371ceba09.png)

## Files used

- AccidentesAviones.csv
- FinalDatasetAirplaneCrashes.csv
- Aircraft_Incident_Dataset.csv
- storms_updated.csv
- PI03.ipynb, jupyter notebook with the EDA and Database connection.
- pi03.db, Database backup file.
- PI03.pbix, PowerBI file with the dashboard

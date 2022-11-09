# PI03-Data-Analytics

## Proyect Summary

For this proyect I was given a plane crashes dataset, my task was to realize an EDA over it and look for another dataset to correlationate it with.
Then load the data to a SQL Database.
This with the purpose of realizing an analysis of the data and present it on a dashboard.
I decided to see if there was any correlation between the amount of plane crashes and the Bermuda Triangle.

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
- I created a new column indicating if the crash was produced near the Bermuda Triangle or not, based on the coordinates gathered.
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

(plane_crashes_dashboard)

### Storms Dashboard

(storms_dashboard)

## Files used

- AccidentesAviones.csv

### Dataset Dictionary Data:

Unnamed: 0: Index column generated by the .csv extention

fecha: Date of the crash

HORA declarada: Hour of the crash

Ruta: Departure and destination locations.

OperadOR: Airline or operator of the aircraft

flight_no: Flight number assigned by the aircraft operator

route: Departure and destination locations.

ac_type: Aircraft type

registration: ICAO registration of the aircraft

cn_ln: Construction or serial number / Line or fuselage number

all_aboard: Total aboard (passengers / crew)

PASAJEROS A BORDO: Total passenger aboard

crew_aboard: Total crew aboard

cantidad de fallecidos: Total fatalities aboard (passengers / crew)

passenger_fatalities: Total fatalities aboard (passengers)

crew_fatalities: Total fatalities aboard (crew)

ground: Total killed on the ground

summary: Brief description of the accident and cause if known


- FinalDatasetAirplaneCrashes.csv

### Dataset Dictionary Data:

Date: Date of accident, in the format - January 01, 2001

Time: Local time, in 24 hr. format unless otherwise specified

Airline/Op: Airline or operator of the aircraft

Flight #: Flight number assigned by the aircraft operator

Route: Complete or partial route flown prior to the accident

AC Type: Aircraft type

Reg: ICAO registration of the aircraft

cn / ln: Construction or serial number / Line or fuselage number

Aboard: Total aboard (passengers / crew)

Fatalities: Total fatalities aboard (passengers / crew)

Ground: Total killed on the ground

Summary: Brief description of the accident and cause if known

Location: Either equivalent to the location provided by Cem or altered to reflect modern borders.

Latitude: Estimated latitude of crash site

Longitude: Estimated longitude of crash site

Geometry: Point with the latitude and longitude dictated above


- Aircraft_Incident_Dataset.csv

### Dataset Dictionary Data:

Incident_Date: Date of incident

Aircraft_Model: Aircraft type

Aircraft_Registration: ICAO registration of the aircraft

Aircaft_Operator: Airline or operator of the aircraft

Aircaft_Nature: Nature of the aircraft

Incident_Category: Category of the incident

Incident_Cause(es): Cause(es) of the incident

Incident_Location: Aproximately location of the crash

Aircaft_Damage_Type: Type of aircraft damage

Date: Date of incident


- storms_updated.csv

### Dataset Dictionary Data:

name: Name given to the storm

year: Ocurrence year of the storm

month: Ocurrence month of the storm

day: Ocurrence day of the storm

hour: Ocurrence hour of the storm

lat: Estimated latitude of storm site

long: Estimated longitude of storm site

status: Type of storm

category: Level of intensity of the storm

wind: Wind Speed (knots)

pressure: Pressure of Storm

tropicalstorm_force_diameter: Diameter of Tropical Storm force wind (nautical miles)

hurricane_force_diameter: Diameter of Hurricane force wind (nautical miles)



<img width="1174" height="531" alt="image" src="https://github.com/user-attachments/assets/4f4261b8-94e3-4e62-8640-4a254d324a1f" /># fabric-project
Welcome to the ##Fabric analytics project##

This project involves the creation of a medallion architecture based on notebooks and pyspark.The main data source is an API from the USGS that deliveres the data from earthquakes based on dates and geolocations.

There are 3 notebooks, for bronze, silver and gold, encapsulated in a data factory pipeline that has a parameter to set the dates and automate the loads.


<img width="927" height="241" alt="image" src="https://github.com/user-attachments/assets/b7f82fc2-d3f6-4c23-ae11-1e061a259728" />


<img width="1174" height="531" alt="image" src="https://github.com/user-attachments/assets/3e51c34d-2225-4c8a-9d07-e675b9a4b2d9" />


## 📖 Project Overview
This project involves:

1. **Data Architecture**: Designing a Medallion Architecture **Bronze**, **Silver**, and **Gold** layers in pyspark and automated with a fabric pipeline.
2. **Bronze layer**: the extract is a notebook that makes the request to the API and gets a Json format, then the file is loaded to the files folder from lakehouse.3. 
4. **Silver layer**: a pyspark notebook that extracts the columns from the json file and transforms the unix time to a timestamp, then it loads the data in a delta table.
5. **Gold layer**: A PySpark notebook that imports the reverse_geocoder library and runs in a customized workspace. The DataFrame is built from a table previously loaded in the Silver layer. Using latitude and longitude, it determines the corresponding country code. It creates a new column sig_class base on the earthquake magnitude. The final data is loaded to a gold table in lakehouse.
6. **Analytics & Reporting**: a power BI report with a map is built based on the gold table.


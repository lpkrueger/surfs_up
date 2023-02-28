# surfs_up
Module 9, Advanced Databases - UNCCH Data Analytics Bootcamp, Spring 2023


## Project Overview

### Purpose
My dream for opening a Surf and Shake shop in Hawaii relies on convinving at least one investor to aid with startup costs. While recruiting potential investor, Avy, he has asked for temperature data for the months of June and December in Oahu, to help him make a decision on whether the surfing and ice cream business could be sustainable through the annual seasons. 

## Method
Using Python, Pandas and SQLAlchemy, weather station data was filtered into the months of June and December to represent the most extreme tempearatures. The temperature data lives in SQLITE file, which was imported into a Python environment using Jupyter Notebook, and manipulated using Pandas functions and SQLAlchemy to create filtered dataframes, and statistical summaries of tempearature for the two desired months.  


Sample code employed using the inspector to print the column names and their data types within the measurement table: 

```
inspector = inspect(engine)
columns = inspector.get_columns('measurement')
for column in columns:
    print(column["name"], column["type"])
```


Sample code used for Deliverable #1: Write a query that filters the Measurement table to retrieve the temperatures for the month of June, then convert the June temperatures to a list:
 
```
    june_temps = []
    june_temps = session.query(Measurement.date, Measurement.tobs).filter(func.strftime("%m", Measurement.date) == "06").all()
```


## Results
- June Temperature Stats
    ![june_temps_stats](/june_temps_stats.png)
    [Number of Retiring Employees by Title](/Data/retiring_titles.csv)

   
- December Temperature Stats
    ![december_temps_stats](/december_temps_stats.png)

- Observations: 
    - The mean tempearature in June is only 5 degrees warmer than the mean tempearature in December, so temps are reliably flat. 
    - Max temps are about the same in June and July, and neither are too high to keep people from coming outside and seeking fun in the sun! 
    - Min temps are also similar, being about 8 degrees different from winter to summer, and not too cold to keep people from wanting to surf. 

    
## Summary

Having relatively flat temps year-round creates a good condition for consistent business when it comes to both surfing and serving ice cream. 

- Additional queries worth pursuing to better inform decisions are:
    - Join the Stations table to the Measurements table to filter for tempearature measurements taken at low elevations (where the surf & ice cream shop would actually be located: beach-side). Additionally can use lat-long information for location nearest where the intended surf shop might exist. 
    - Find precipitation data for the same months studied to learn whether the rain changes more seasonally than the temperature, which could affect foot traffic and sales.
    - Look at year-round information (not just extremes) and plot the mean, min, and max temps to determine variablity. 
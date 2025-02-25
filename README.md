**Business Impact:**

This SQL-driven weather analysis helps in climate monitoring, disaster preparedness, and agricultural planning. Businesses and governments can:

✔ Improve weather forecasting for better decision-making.

✔ Prepare for extreme weather by analyzing historical patterns.

✔ Optimize energy consumption based on seasonal trends.


Q1) Write a query to create the TRIANGLES table.


ANS:            CREATE TABLE TRIANGLES
(
TRIANGLE_ID INT(10) PRIMARY KEY,
SIDE_A INT (10),
SIDE_B INT (10),
SIDE_C INT (10)
);

INSERT INTO TRIANGLES VALUES
(1, 20,20,23), (2,20,20,20), (3,20,21,22),(4,13,14,30);

SELECT* FROM TRIANGLES;


Q2) Insert the following records into the table

ANS:       INSERT INTO STATION VALUES (13, "PHOENIX", "AZ", 33, 112);
INSERT INTO STATION VALUES (44, "DENVER", "CO", 40, 105);
INSERT INTO STATION VALUES (66, "CARIBOU", "ME", 47, 68);

                                    
  Q3) Execute a query to look at table STATION in undefined order.                       

ANS:          SELECT * FROM STATION;

                          


Q4) Execute a query to select Northern stations (Northern latitude > 39.7).

ANS:     SELECT * FROM STATION WHERE LAT_N > 39.7;

                             

                                 
Q5) Create another table, ‘STATS’, to store normalized temperature and precipitation data

ANS: CREATE TABLE STATS
(
ID INT(10),
MONTH INT(2), CHECK (MONTH BETWEEN 1 AND 12),
TEMP_F DECIMAL (5,2), CHECK (TEMP_F BETWEEN -80 AND 150),
RAIN_I DECIMAL(5,2), CHECK (RAIN_I BETWEEN 0 AND 100),
PRIMARY KEY (ID, MONTH)
);  
            
              
  
Q6) Populate the table STATS with some statistics for January and July

ANS:  INSERT INTO STATS VALUES (13, 1, 57.4, .31);
      INSERT INTO STATS VALUES (13, 7, 91.7, 5.15);
      INSERT INTO STATS VALUES (44, 1, 27.3, .18);
      INSERT INTO STATS VALUES (44, 7, 74.8, 2.11);
      INSERT INTO STATS VALUES (66, 1, 6.7, 2.1);
      INSERT INTO STATS VALUES (66, 7, 65.8, 4.52);
             

                                  
Q7) Execute a query to display temperature stats (from the STATS table) for each city (from the STATION table)

ANS: SELECT STATION.CITY, STATS.MONTH, STATS.TEMP_F FROM STATION JOIN STATS ON STATION.ID= STATS.ID;


               
Q8) Execute a query to look at the table STATS, ordered by month and greatest rainfall, with columns rearranged. It should also show the corresponding cities.   

ANS: SELECT  STATS.ID, STATION.CITY, STATS.MONTH, STATS.RAIN_I AS Greatest Rainfall
FROM STATS JOIN STATION ON STATS.ID = STATION.ID ORDER BY STATS.RAIN_I DESC;  

                                                                                 

Q9) Execute a query to look at temperatures for July from table STATS, lowest temperatures first, picking up city name and latitude 

ANS: SELECT STATION.CITY, STATION.LAT_N, STATS.MONTH, STATS.TEMP_F AS TEMPERATURE 
FROM STATS JOIN STATION ON STATS.ID= STATION.ID 
WHERE STATS.MONTH= 7 ORDER BY TEMP_F DESC;

                                                                                                 

Q10) Execute a query to show MAX and MIN temperatures as well as average rainfall for each city.

ANS: SELECT STATION. CITY, MAX(STATS.TEMP_F) AS MAX_TEMPERATURE, MIN(STATS.TEMP_F) 
AS MIN_TEMPERATURE, AVG(STATS.RAIN_I) AS AVERAGE_RAINFALL 
FROM STATS JOIN STATION ON STATS.ID= STATION.ID GROUP BY STATION.CITY;
                           


Q11) Execute a query to display each city’s monthly temperature in Celsius and rainfall in Centimeter.

ANS: SELECT STATION.CITY, STATS.MONTH,((STATS.TEMP_F - 32) * 5/9) AS Temperature Celsius,
(STATS.RAIN_I * 2.54) AS Rainfall Centimetre FROM STATS JOIN STATION ON STATS.ID= STATION.ID

Q12) Update all rows of table STATS to compensate for faulty rain gauges known to read 0.01 inches low.

ANS: UPDATE STATS SET RAIN_I= (RAIN_I + 0.01) WHERE ID = 13;
UPDATE STATS SET RAIN_I= (RAIN_I + 0.01) WHERE ID = 44;
UPDATE STATS SET RAIN_I= (RAIN_I + 0.01) WHERE ID = 66;

             

Q13) Update Denver's July temperature reading as 74.9.

ANS: UPDATE STATS SET TEMP_F = 74.9 WHERE ID = 44 AND MONTH = 7;








                       




                       
















# SQL-Toy-Problems
Practice with SQL

Problem Statement
Given a table STATION that holds data for five fields namely ID, CITY, STATE, NORTHERN LATITUDE and WESTERN LONGITUDE.


Field:    Type

ID:       INTEGER    

CITY:     VARCHAR(21)

STATE:    VARCHAR(2) 

LAT_N:    NUMERIC    

LONG_W:   NUMERIC    


1. Write a query to print the list of CITY and STATE in lexicographical order of city and state, i.e., if there are two or more cities with same name arrange these by lexicographical order of state.

  ```select CITY, STATE  
     from STATION 
     order by CITY, STATE;```

3. Write a query to print the list of CITY in lexicographical order for even ID only. Do not print duplicates.
	  
  ```select distinct(CITY)
     from STATION  
     where ID%2 = 0
     order by CITY;```

4. Let NUM be no. of cities and NUM_unique be no. of unique cities, then write a query to print the value of NUM - NUM_unique.

  ```select count(*) - (select count(distinct(CITY)) from STATION) from STATION;```

5. Let |city| be the length of the city, write a query to print two lines:
a. First line is city1 and |city1| separated by space, where |city1| is the possible minimum value.
b. Second line is city2 and |city2| separated by space, where |city2|  is the possible maximum value.
If there are more than one possible cities print the lexicographical smallest.

  ```(select CITY, char_length(CITY) as len_city from STATION order by len_city limit 1) union all (select CITY,   
  char_length(CITY) as len_city from STATION 
	order by len_city desc limit 1) order by len_city;```  

6. Write a query to print the list of CITY that start with vowels in lexicographical order. Do not print duplicates.

  ```select CITY from STATION where CITY like 'A%' or CITY like 'E%' or CITY like 'I%' or CITY like 'O%' or CITY like   'U%' order by SUBSTRING(CITY, 1, 1) ASC;```

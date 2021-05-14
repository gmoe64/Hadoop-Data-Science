# Hadoop-Data-Science
Exercises for manipulating, analyzing and performing computations on Hadoop Big Data.

----------------------
Command Line Arguments
----------------------

Example:  joined.select( "SalePrice", "PropertyType", "ZipCode", "City","SqFtFinBasement").filter(price_tb1.lt("450000") && basement.gt("0") && type_tb1.notEqual("Townhouse") &&  city_tb1.equalTo("Renton")).orderBy(desc("SalePrice")).show

-price_tb1.lt("450000")
-basement.gt("0")
-type_tb1.notEqual("Townhouse")
-city_tb1.equalTo("Renton")

  (required) Specifies the housing sales price, type and location in 
  a specific area in Washington state.

    -price_tb1 - Housing sale price variable 
    -basement - Housing basement size variable
    -type_tb1 - Housing style/type variable 
    -city_tb1 - variable create from zipcode and table join

-------------------------
Design Decisions & Issues
-------------------------
I selected the data set house-prices. Currently i'm looking for a home with the following requirements:


Q. Sale price must be under $450000
A. val price_tb1 = houseDF("SalePrice") 
  
Q. Zipcode within a specific area,
A. val city_tb1 = joined("City") - In order to accomplish this i had to join a table i created cross referencing zip with actually city names.

Q. Must not be a Townhouse
A. val type_tb1 = houseDF("PropertyType") - I used this variable to avoid townhouses 

Q. House has to have a basement for my mancave!!!!
A. val basement = houseDF("SqFtFinBasement") - If basement square feet is greater than 0, the house has a basement


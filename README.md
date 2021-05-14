# Hadoop-Data-Science
Exercises for manipulating, analyzing and performing computations on Hadoop Big Data.

----------------------
Command Line Arguments
----------------------

    Example:  joined.select( "SalePrice", "PropertyType", "ZipCode", "City","SqFtFinBasement").filter(price_tb1.lt("450000") && basement.gt("0") && type_tb1.notEqual("Townhouse")                &&  city_tb1.equalTo("Renton")).orderBy(desc("SalePrice")).show 


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
I selected the data set house-prices. I'm currently in the market looking to purchase a newhome with the following requirements:


Q. Sale price must be under $450000
A. val price_tb1 = houseDF("SalePrice") 
  
Q. Housing must have zipcode within a specific area
A. val city_tb1 = joined("City") - In order to accomplish this i had to join a table i created cross referencing zip with actually city names.

Q. I would like to exclude townhouse from my search
A. val type_tb1 = houseDF("PropertyType") - I used this variable to avoid townhouses 

Q. House must has a basement for additional square footage
A. val basement = houseDF("SqFtFinBasement") - If basement square feet is greater than 0, the house has a basement


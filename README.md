# Power-BI-DAX-Practice-



# MAKE NEW TABLE (Table):-


# New measures:- 
1. Total_Product_Categories = DISTINCTCOUNT(Products_Table[product_category])
2. Table = {blank()}
3. Total quantity = sum(Orders_Table[transaction_qty])
4. Tea_transaction = CALCULATE(COUNT(Orders_Table[transaction_id]), Products_Table[product_category]="tea")
5. revenue = sumx(Orders_Table,Orders_Table[transaction_qty] * Orders_Table[Products_Table.unit_price])
6. Count_Payment_Mode = COUNT(Orders_Table[payment_mode])
7. Count_Orders = COUNTROWS(Orders_Table)
8. Revenue_of_Coffee = CALCULATE([revenue],Products_Table[product_category] = "Coffee")
9. All = CALCULATE([revenue], all(Orders_Table[store_location]))
10. All_Except = CALCULATE([revenue], ALLEXCEPT(Products_Table,Products_Table[product_category]))
11. All_Selected = CALCULATE([revenue], ALLSELECTED(Orders_Table[store_location]))
12. Running_total = CALCULATE([revenue],FILTER(all(Orders_Table),Orders_Table[transaction_date] <= MAX(Orders_Table[transaction_date])))
13. mtd = TOTALMTD([revenue],Orders_Table[transaction_date])

# New measures (Orders_Table):-
1. Month_Name = FORMAT(Orders_Table[transaction_date],"mmmm")
2. Month = MONTH(Orders_Table[transaction_date])
3. Dayname = FORMAT(Orders_Table[transaction_date],"dddd")
4. Day_of_week = SWITCH(Orders_Table[Dayname],
"Monday",1,
"Tuesday",2,
"Wednesday",3,
"Thursday",4,
"Friday",5,
"Saturday",6,
"Sunday",7)
 

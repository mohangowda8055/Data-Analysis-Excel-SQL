# Pizza-Sales-SQL-Queries
### A. KPI’s:
__1. Total Revenue:__<br>
__SELECT__ __ROUND__(__SUM__(total_price), 2) __AS__ Total_Revenue __FROM__ pizza_sales;<br>
![image](https://github.com/mohangowda8055/Data-Analysis-Excel-SQL/assets/125982691/9db68b1f-dc0a-436e-ad29-0f232fc501ec)

__2. Average Order Value:__<br>
__SELECT ROUND__((__SUM__(total_price) / __COUNT__(__DISTINCT__ order_id), 2) __AS__ Avg_Order_Value __FROM__ pizza_sales;<br>
![image](https://github.com/mohangowda8055/Data-Analysis-Excel-SQL/assets/125982691/4eae3a7c-92e7-486f-be54-0b2f37e8630f)

__3. Total Pizzas Sold:__<br>
__SELECT SUM__(quantity) __AS__ Total_pizza_sold __FROM__ pizza_sales;<br>
![image](https://github.com/mohangowda8055/Data-Analysis-Excel-SQL/assets/125982691/562c9fd3-ee6b-4202-ac19-a78d4a1cc494)

__4. Total Orders:__<br>
__SELECT COUNT__(__DISTINCT__ order_id) __AS__ Total_Orders __FROM__ pizza_sales;<br>
![image](https://github.com/mohangowda8055/Data-Analysis-Excel-SQL/assets/125982691/21c72c6c-2737-4c0b-b7b8-8874babb3011)

__5. Average Pizzas Per Order:__<br>
__SELECT ROUND__((__SUM__(quantity) / (__COUNT__(__DISTINCT__ order_id)), 2) 
__AS__ Avg_Pizza_Per_Order
__FROM__ pizza_sales;<br>
![image](https://github.com/mohangowda8055/Data-Analysis-Excel-SQL/assets/125982691/2338b8a5-1b52-4204-8752-b95c28eb7c3c)
- - - - 
### B. Daily Trend for Total Orders:
__SELECT DAYNAME__(order_date) __AS__ Order_Day, __COUNT__(__DISTINCT__ order_id) __AS__ Total_Orders 
__FROM__ pizza_sales
__GROUP BY__ Order_Day
__ORDER BY__ Total_Orders;<br>

__Output:__<br>
![image](https://github.com/mohangowda8055/Data-Analysis-Excel-SQL/assets/125982691/91e635b1-6177-4598-8faa-7c932eff80b6)
- - - -
### C. Hourly Trend for Orders:
__SELECT HOUR__(order_time) __AS__ Order_Hours, __COUNT__(__DISTINCT__ order_id) __AS__ Total_Orders
__FROM__ pizza_sales
__GROUP BY__ Order_Hours
__ORDER BY__ Total_Orders __DESC__;<br>

__Output:__<br>
![image](https://github.com/mohangowda8055/Data-Analysis-Excel-SQL/assets/125982691/671a3967-5d46-4970-be03-d08122157113)
- - - -
### D. Percentage of Sales By Pizza Category:
__SELECT__ pizza_category,
__ROUND__(__SUM__(total_price) * 100 / (__SELECT SUM__(total_price) __FROM__ pizza_sales), 2) __AS__ Percentage
__FROM__ pizza_sales
__GROUP BY__ pizza_category;<br>

__Output:__<br>
![image](https://github.com/mohangowda8055/Data-Analysis-Excel-SQL/assets/125982691/fb5661ad-4f0c-4117-8c5a-4e218edb6b1a)
 - - - - 
### E. Percentage of Sales By Pizza Size:
__SELECT__ pizza_size,
__ROUND__(__SUM__(total_price) * 100 / (__SELECT SUM__(total_price) __FROM__ pizza_sales), 2) __AS__ Percentage
__FROM__ pizza_sales
__GROUP BY__ pizza_size;<br>

__Output:__<br>
![image](https://github.com/mohangowda8055/Data-Analysis-Excel-SQL/assets/125982691/7a839be1-e694-4dd1-8be5-754a8ec30ac2)
- - - - 
### F. Total Pizza’s Sold by Pizza Category in January: 
__SELECT__ pizza_category, __SUM__(quantity) __AS__ Total_Quantity_Sold
__FROM__ pizza_sales
__WHERE MONTH__(order_date) = 1
__GROUP BY__ pizza_category
__ORDER BY__ Total_Quantity_Sold __DESC__;

__Output:__<br>
![image](https://github.com/mohangowda8055/Data-Analysis-Excel-SQL/assets/125982691/54c6923f-8515-48cc-9670-1336afdc1798)
- - - -
### G. Top 5 Pizza’s by Total Pizza’s Sold:
__SELECT__ pizza_name, __SUM__(quantity) __AS__ Total_Pizza_Sold
__FROM__ pizza_sales
__GROUP BY__ pizza_name
__ORDER BY__ Total_Pizza_Sold __DESC__
__LIMIT__ 5;

__Output:__<br>
![image](https://github.com/mohangowda8055/Data-Analysis-Excel-SQL/assets/125982691/e38f03eb-603c-4e78-bb08-f7da4cdd9442)
- - - - 
### H. Bottom 5 Pizza’s by Total Pizza’s Sold:
__SELECT__ pizza_name, __SUM__(quantity) __AS__ Total_Pizza_Sold
__FROM__ pizza_sales
__GROUP BY__ pizza_name
__ORDER BY__ Total_Pizza_Sold
__LIMIT__ 5;

__Output:__<br>
![image](https://github.com/mohangowda8055/Data-Analysis-Excel-SQL/assets/125982691/0c27407a-033c-4184-9410-752bda756854)




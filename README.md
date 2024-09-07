# Credit Card Financial Dashboard

PROJECT OBJECTIVE->To develop a comprehensive Credit Card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.<br>

->To create this project report in Power BI I first used mySQL to perform some operations on 'Week_Start_Date' column of the credit card dataset. Then I imported the credit card CSV file data in this table which is credit_card also in the same dataset I imported other CSV file by name customer.<br>

SQL QUERIES USED ARE AS FOLLOWS:<br><br>

use credit_card;      -- here credit_card is a database<br><br>

create table credit_card(<br>
Client_Num	int,<br>
Card_Category varchar(20),<br>
Annual_Fees	int,<br>
Activation_30_Days int,<br>
Customer_Acq_Cost int,<br>
Week_Start_Date	varchar(20),<br>
Week_Num varchar(20),<br>
Qtr	varchar(20),<br>
current_year int,<br>
Credit_Limit float,<br>
Total_Revolving_Bal	int,<br>
Total_Trans_Amt	int,<br>
Total_Trans_Vol	int,<br>
Avg_Utilization_Ratio float,<br>
Use_Chip varchar(20),<br>
Exp_Type varchar(20),<br>
Interest_Earned float,<br>
Delinquent_Acc binary<br>
);<br><br>

select count(client_Num) from credit_card;<br><br>

SELECT distinct(Week_Start_Date) FROM credit_card LIMIT 10;<br><br>

ALTER TABLE credit_card
MODIFY Week_Start_Date DATE; -- showing error <br><br>

-- Add a new column with the correct data type
ALTER TABLE credit_card ADD new_Week_Start_Date DATE;<br><br>


SET SQL_SAFE_UPDATES = 0;<br><br>

-- Update the new column with the correctly formatted dates<br>
UPDATE credit_card
SET new_Week_Start_Date = STR_TO_DATE(Week_Start_Date, '%d-%m-%Y');<br><br>

SET SQL_SAFE_UPDATES = 1;<br><br>

-- Drop the old column<br>
ALTER TABLE credit_card DROP COLUMN Week_Start_Date;<br><br>

-- Rename the new column to the original column name<br>
ALTER TABLE credit_card CHANGE new_Week_Start_Date Week_Start_Date DATE;<br><br>

-> After this I imported these two customer and credit_card tables in the Power BI to make reports on there data. 


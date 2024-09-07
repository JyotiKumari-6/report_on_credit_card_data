# Credit Card Financial Dashboard

PROJECT OBJECTIVE->To develop a comprehensive Credit Card weekly dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations effectively.<br>

->To create this project report in Power BI I first used mySQL to perform some operations on 'Week_Start_Date' column of the credit card dataset. Then I imported the credit card CSV file data in this table which is credit_card also in the same dataset I imported other CSV file by name customer.<br>

SQL QUERIES USED ARE AS FOLLOWS:<br>

use credit_card;      -- here credit_card is a database

create table credit_card(
Client_Num	int,
Card_Category varchar(20),
Annual_Fees	int,
Activation_30_Days int,
Customer_Acq_Cost int,
Week_Start_Date	varchar(20),
Week_Num varchar(20),
Qtr	varchar(20),
current_year int,
Credit_Limit float,
Total_Revolving_Bal	int,
Total_Trans_Amt	int,
Total_Trans_Vol	int,
Avg_Utilization_Ratio float,
Use_Chip varchar(20),
Exp_Type varchar(20),
Interest_Earned float,
Delinquent_Acc binary
);

select count(client_Num) from credit_card;

SELECT distinct(Week_Start_Date) FROM credit_card LIMIT 10;

ALTER TABLE credit_card
MODIFY Week_Start_Date DATE; -- showing error

-- Add a new column with the correct data type
ALTER TABLE credit_card ADD new_Week_Start_Date DATE;


SET SQL_SAFE_UPDATES = 0;

-- Update the new column with the correctly formatted dates
UPDATE credit_card
SET new_Week_Start_Date = STR_TO_DATE(Week_Start_Date, '%d-%m-%Y');

SET SQL_SAFE_UPDATES = 1;

-- Drop the old column
ALTER TABLE credit_card DROP COLUMN Week_Start_Date;

-- Rename the new column to the original column name
ALTER TABLE credit_card CHANGE new_Week_Start_Date Week_Start_Date DATE;

-> After this I imported these two customer and credit_card tables in the Power BI to make reports on this data. 


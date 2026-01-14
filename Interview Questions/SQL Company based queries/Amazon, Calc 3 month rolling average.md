<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Amazon (Hard Level) hashtag#SQL Interview Question — Solution

Find the 3-month rolling average of total revenue from purchases given a table with users, their purchase amount, and date purchased. Do not include returns which are represented by negative purchase values. Output the year-month (YYYY-MM) and 3-month rolling average of revenue, sorted from earliest month to latest month.

A 3-month rolling average is defined by calculating the average total revenue from all user purchases for the current month and previous two months. The first two months will not be a true 3-month rolling average since we are not given data from last year. Assume each month has at least one purchase.

🌀By solving this, you'll learn how to use Mutiple CTEs, Joins, Group by, Windows & Agg function. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE amazon_purchases ( created_at DATETIME, purchase_amt BIGINT, user_id BIGINT);

INSERT INTO amazon_purchases (created_at, purchase_amt, user_id) VALUES ('2023-01-05', 1500, 101), ('2023-01-15', -200, 102), ('2023-02-10', 2000, 103), ('2023-02-20', 1200, 101), ('2023-03-01', 1800, 104), ('2023-03-15', -100, 102), ('2023-04-05', 2200, 105), ('2023-04-10', 1400, 103), ('2023-05-01', 2500, 106), ('2023-05-15', 1700, 107), ('2023-06-05', 1300, 108), ('2023-06-15', 1900, 109);
---------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
3-month rolling average is the average of data from the last three months, calculated each month.

1. MonthlyRevenue CTE: Extracts the year and month (in YYYY-MM format) from created_at. Calculates the total revenue for each month, excluding negative values (representing returns).

2. RollingAverage CTE: For each month (mr1), joins it with the previous two months (mr2) using a date difference of up to 2 months. Computes the average total revenue across the current and previous two months.

**SOLUTION**

<img width="1382" height="798" alt="image" src="https://github.com/user-attachments/assets/b835491a-7600-4e47-a18b-3cbb5020b21a" />



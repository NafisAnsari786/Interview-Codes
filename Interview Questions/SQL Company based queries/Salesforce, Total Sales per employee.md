<img src="https://img.shields.io/badge/EASY-green" alt="EASY" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Amazon, Salesforce (Basic Level) hashtag#SQL Interview Question — Solution

What is the total sales revenue of Samantha and Lisa?

🔊 Just wanted to point out that even major companies like Amazon ask questions this basic— so it's worth giving it a try! and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭:
CREATE TABLE sales_performance (salesperson VARCHAR(50),widget_sales INT,sales_revenue INT,id INT PRIMARY KEY);

INSERT INTO sales_performance (salesperson, widget_sales, sales_revenue, id) VALUES('Jim', 810, 40500, 1),('Bobby', 661, 33050, 2),('Samantha', 1006, 50300, 3),('Taylor', 984, 49200, 4),('Tom', 403, 20150, 5),('Pat', 715, 35750, 6),('Lisa', 1247, 62350, 7);
------------

I have provided an explanation and query, but I encourage you to try solving it first. Later, you can check the query for reference.

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. This query filters for rows where the salesperson is either "Samantha" or "Lisa" and calculates the sum of their sales_revenue.

**SOLUTION**

<img width="800" height="379" alt="image" src="https://github.com/user-attachments/assets/b1cc056f-a1e6-4bba-8c34-001249d0bc16" />

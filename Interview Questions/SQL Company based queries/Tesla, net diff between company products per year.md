

<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Tesla(Medium Level) hashtag#SQL Interview Question — Solution

You are given a table of product launches by company by year. Write a query to count the net difference between the number of products companies launched in 2020 with the number of products companies launched in the previous year. Output the name of the companies and a net difference of net products released for 2020 compared to the previous year.

🔍 By solving this, you'll learn how to handle aggregation function. Give it a try! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭:
CREATE TABLE car_launches(year int, company_name varchar(15), product_name varchar(30));

INSERT INTO car_launches VALUES(2019,'Toyota','Avalon'),(2019,'Toyota','Camry'),(2020,'Toyota','Corolla'),(2019,'Honda','Accord'),(2019,'Honda','Passport'),(2019,'Honda','CR-V'),(2020,'Honda','Pilot'),(2019,'Honda','Civic'),(2020,'Chevrolet','Trailblazer'),(2020,'Chevrolet','Trax'),(2019,'Chevrolet','Traverse'),(2020,'Chevrolet','Blazer'),(2019,'Ford','Figo'),(2020,'Ford','Aspire'),(2019,'Ford','Endeavour'),(2020,'Jeep','Wrangler')
------------

I have provided an explanation and query, but I encourage you to try solving it first. Later, you can check the query for reference.

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. Counting Products per Year: Using SUM with CASE statements, we count the number of products launched in 2020 and 2019 separately for each company.

2. Calculating Net Difference: We calculate the difference between 2020 and 2019 product counts to get the net change.

3. Ordering: The results are ordered by net_difference in descending order to show companies with the highest increase first.

**SOLUTION**

<img width="800" height="737" alt="image" src="https://github.com/user-attachments/assets/b23e23d2-96ce-4aa3-9848-85243af12563" />

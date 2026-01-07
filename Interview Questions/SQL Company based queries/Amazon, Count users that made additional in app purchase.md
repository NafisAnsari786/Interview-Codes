<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Amazon (Hard Level) hashtag#SQL Interview Question — Solution

You have a table of in-app purchases by user. Users that make their first in-app purchase are placed in a marketing campaign where they see call-to-actions for more in-app purchases. Find the number of users that made additional in-app purchases due to the success of the marketing campaign.

The marketing campaign doesn't start until one day after the initial in-app purchase so users that only made one or multiple purchases on the first day do not count, nor do we count users that over time purchase only the products they purchased on the first day.


🌀 Trust me, this one will surely challenge you...! You'll learn Cte, Joins, Group by. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE in_app_purchases ( created_at DATETIME, price BIGINT, product_id BIGINT, quantity BIGINT, user_id BIGINT);

INSERT INTO in_app_purchases (created_at, price, product_id, quantity, user_id) VALUES('2024-12-01 10:00:00', 500, 101, 1, 1),  ('2024-12-02 11:00:00', 700, 102, 1, 1),('2024-12-01 12:00:00', 300, 103, 1, 2), ('2024-12-03 14:00:00', 400, 103, 1, 2),('2024-12-02 09:30:00', 200, 104, 1, 3), ('2024-12-04 15:30:00', 600, 105, 2, 3),('2024-12-01 08:00:00', 800, 106, 1, 4), ('2024-12-05 18:00:00', 500, 107, 1, 4),('2024-12-06 16:00:00', 700, 108, 1, 5); 

---------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. FirstPurchase CTE: Identifies the first purchase date for each user. This is necessary to calculate when the campaign period begins.

2. Main Query: Joins in_app_purchases with the FirstPurchase CTE to filter purchases made at least one day after the first purchase. Uses a NOT EXISTS subquery to exclude purchases of products already bought on the first day.
Counts the distinct users who meet the criteria.

**SOLUTION**

<img width="800" height="647" alt="image" src="https://github.com/user-attachments/assets/dd73f64c-1d55-4357-af10-d6cdb974afd5" />

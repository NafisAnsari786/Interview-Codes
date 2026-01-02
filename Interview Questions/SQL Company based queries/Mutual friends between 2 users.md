<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Meta/Facebook (Hard Level) hashtag#SQL Interview Question — Solution

A table named “famous” has two columns called user id and follower id. It represents each user ID has a particular follower ID. These follower IDs are also users of hashtag#Facebook / hashtag#Meta. Then, find the famous percentage of each user. 
Famous Percentage = number of followers a user has / total number of users on the platform.

🔍 At first glance, this might seem tedious, but it's straightforward once you break it down. Give it a try! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭:
CREATE TABLE famous (user_id INT, follower_id INT);

INSERT INTO famous VALUES
(1, 2), (1, 3), (2, 4), (5, 1), (5, 3), 
(11, 7), (12, 8), (13, 5), (13, 10), 
(14, 12), (14, 3), (15, 14), (15, 13);
-------------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐨𝐟 𝐭𝐡𝐞 𝐐𝐮𝐞𝐫𝐲:
1. distinct_users CTE:
Combines user_id and follower_id using UNION to get all unique users on the platform. This helps us determine the total number of users.

2. follower_count CTE:
Counts the number of followers for each user_id by grouping the rows in the famous table. This gives a list of users with their follower counts.

2. Final SELECT Statement:
Uses the data from follower_count and distinct_users to calculate the famous percentage for each user.

**SOLUTION**

<img width="800" height="612" alt="image" src="https://github.com/user-attachments/assets/b63c6db3-3f01-4ee8-affb-754985c37cf4" />

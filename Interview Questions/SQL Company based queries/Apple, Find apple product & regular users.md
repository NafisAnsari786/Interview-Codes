<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Apple (Hard Level) hashtag#SQL Interview Question — Solution

Find the number of Apple product users and the number of total users with a device and group the counts by language. Assume Apple products are only MacBook-Pro, iPhone 5s, and iPad-air. Output the language along with the total number of Apple users and users with any device. Order your results based on the number of total users in descending order.

🔍 Definitely you are going to enjoy by solving this, you'll learn how to multiple ctes, join, group by. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE playbook_users (user_id INT PRIMARY KEY,created_at DATETIME,company_id INT,language VARCHAR(50),activated_at DATETIME,state VARCHAR(50));

INSERT INTO playbook_users (user_id, created_at, company_id, language, activated_at, state) VALUES
(1, '2024-01-01 08:00:00', 101, 'English', '2024-01-05 10:00:00', 'Active'),
(2, '2024-01-02 09:00:00', 102, 'Spanish', '2024-01-06 11:00:00', 'Inactive'),
(3, '2024-01-03 10:00:00', 103, 'French', '2024-01-07 12:00:00', 'Active'),
(4, '2024-01-04 11:00:00', 104, 'English', '2024-01-08 13:00:00', 'Active'),
(5, '2024-01-05 12:00:00', 105, 'Spanish', '2024-01-09 14:00:00', 'Inactive');

CREATE TABLE playbook_events ( user_id INT, occurred_at DATETIME, event_type VARCHAR(50), event_name VARCHAR(50), location VARCHAR(100), device VARCHAR(50));

INSERT INTO playbook_events (user_id, occurred_at, event_type, event_name, location, device) VALUES
(1, '2024-01-05 14:00:00', 'Click', 'Login', 'USA', 'MacBook-Pro'),
(2, '2024-01-06 15:00:00', 'View', 'Dashboard', 'Spain', 'iPhone 5s'),
(3, '2024-01-07 16:00:00', 'Click', 'Logout', 'France', 'iPad-air'),
(4, '2024-01-08 17:00:00', 'Purchase', 'Subscription', 'USA', 'Windows-Laptop'), (5, '2024-01-09 18:00:00', 'Click', 'Login', 'Spain', 'Android-Phone');

---------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. AppleUsers CTE: Identifies users who use Apple devices (MacBook-Pro, iPhone 5s, iPad-air). Counts the distinct user_id for each language.

2. TotalUsers CTE: Counts the total distinct users who have any device for each language.

3. Final Query: Combines results from AppleUsers and TotalUsers using a LEFT JOIN. If no Apple users exist for a particular language, it defaults their count to 0 using COALESCE.

**SOLUTION**

<img width="800" height="788" alt="image" src="https://github.com/user-attachments/assets/f7c4d977-bd19-49e4-af23-3084e95eeead" />

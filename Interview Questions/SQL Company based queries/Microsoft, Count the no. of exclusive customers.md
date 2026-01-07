<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Microsoft (Medium Level) hashtag#SQL Interview Question — Solution

Considering a dataset that tracks user interactions with different clients, identify which clients have users who are exclusively loyal to them (i.e., they don't interact with any other clients).

For each of these clients, calculate the number of such exclusive users. The output should include the client_id and the corresponding count of exclusive users.

🌀 Trust me, this one will surely challenge you...! You'll learn Sub-query, Joins, Group by. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE meetup_events (client_id VARCHAR(255), customer_id VARCHAR(255), event_id BIGINT, event_type VARCHAR(255), id BIGINT PRIMARY KEY, time_id DATETIME, user_id VARCHAR(255));

INSERT INTO meetup_events (client_id, customer_id, event_id, event_type, id, time_id, user_id) VALUES ('C001', 'CU001', 101, 'click', 1, '2025-01-01 10:00:00', 'U001'), ('C001', 'CU002', 102, 'view', 2, '2025-01-01 11:00:00', 'U002'), ('C002', 'CU003', 103, 'click', 3, '2025-01-02 10:00:00', 'U003'), ('C002', 'CU003', 104, 'view', 4, '2025-01-02 11:00:00', 'U003'), ('C003', 'CU004', 105, 'click', 5, '2025-01-03 10:00:00', 'U004'), ('C001', 'CU001', 106, 'view', 6, '2025-01-04 10:00:00', 'U001'), ('C003', 'CU005', 107, 'click', 7, '2025-01-05 10:00:00', 'U005'), ('C004', 'CU006', 108, 'view', 8, '2025-01-06 10:00:00', 'U006'), ('C004', 'CU006', 109, 'click', 9, '2025-01-07 10:00:00', 'U006'), ('C001', 'CU007', 110, 'click', 10, '2025-01-08 10:00:00', 'U007');
---------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. Subquery to Identify Non-Exclusive Users: The subquery identifies user_id values that interact with more than one client_id by performing a self-join on the meetup_events table where the client_id values differ.

2. Filter Exclusive Users: The main query uses NOT IN to exclude users who interact with multiple clients.

3. Count Exclusive Users: Counts distinct user_id values for each client_id who are not part of the non-exclusive users.

4. Group and Order: Groups the result by client_id and orders by the count of exclusive users in descending order.

**SOLUTION**

<img width="758" height="687" alt="image" src="https://github.com/user-attachments/assets/a40b74ea-8079-44e1-8ad0-57cf0097f95f" />


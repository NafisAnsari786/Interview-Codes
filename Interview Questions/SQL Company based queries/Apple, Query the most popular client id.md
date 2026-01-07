<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Apple, Microsoft (Hard Level) hashtag#SQL Interview Question — Solution

Select the most popular client_id based on a count of the number of users who have at least 50% of their events from the following list: 'video call received', 'video call sent', 'voice call received', 'voice call sent'.

🌀By solving this, you'll learn how to use Mutiple Cte, Group by, Join. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE fact_event (id BIGINT PRIMARY KEY, time_id DATETIME, user_id VARCHAR(50), customer_id VARCHAR(50), client_id VARCHAR(50), event_type VARCHAR(50), event_id BIGINT);

INSERT INTO fact_event (id, time_id, user_id, customer_id, client_id, event_type, event_id) VALUES (1, '2024-02-01 10:00:00', 'U1', 'C1', 'CL1', 'video call received', 101), (2, '2024-02-01 10:05:00', 'U1', 'C1', 'CL1', 'video call sent', 102), (3, '2024-02-01 10:10:00', 'U1', 'C1', 'CL1', 'message sent', 103), (4, '2024-02-01 11:00:00', 'U2', 'C2', 'CL2', 'voice call received', 104), (5, '2024-02-01 11:10:00', 'U2', 'C2', 'CL2', 'voice call sent', 105), (6, '2024-02-01 11:20:00', 'U2', 'C2', 'CL2', 'message received', 106), (7, '2024-02-01 12:00:00', 'U3', 'C3', 'CL1', 'video call sent', 107), (8, '2024-02-01 12:15:00', 'U3', 'C3', 'CL1', 'voice call received', 108), (9, '2024-02-01 12:30:00', 'U3', 'C3', 'CL1', 'voice call sent', 109), (10, '2024-02-01 12:45:00', 'U3', 'C3', 'CL1', 'video call received', 110);

---------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. user_event_counts → Counts total events per user_id.

2. filtered_event_counts → Counts only the relevant event types per user_id and client_id.

3. qualified_users → Filters users who have at least 50% of their events from the target event list.

4. client_popularity → Counts the number of qualified users per client_id.

5. Final Selection → Picks the client_id with the highest number of users meeting the condition.

**SOLUTION**

<img width="800" height="670" alt="image" src="https://github.com/user-attachments/assets/3f09af1b-c9b5-44fe-967d-3cdfe5470780" />

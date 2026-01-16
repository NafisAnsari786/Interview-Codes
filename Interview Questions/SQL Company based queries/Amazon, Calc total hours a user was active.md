<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Amazon (Hard Level) hashtag#SQL Interview Question — Solution

Given the users' sessions logs on a particular day, calculate how many hours each user was active that day. Note: The session starts when state=1 and ends when state=0.

🌀 Trust me, this one will surely challenge you...! Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭:
CREATE TABLE customer_state_log (cust_id VARCHAR(10),state INT,timestamp TIME);

INSERT INTO customer_state_log (cust_id, state, timestamp) VALUES('c001', 1, '07:00:00'),('c001', 0, '09:30:00'),('c001', 1, '12:00:00'),('c001', 0, '14:30:00'),('c002', 1, '08:00:00'),('c002', 0, '09:30:00'),('c002', 1, '11:00:00'),('c002', 0, '12:30:00'),('c002', 1, '15:00:00'),('c002', 0, '16:30:00'),('c003', 1, '09:00:00'),('c003', 0, '10:30:00'),('c004', 1, '10:00:00'),('c004', 0, '10:30:00'),('c004', 1, '14:00:00'),('c004', 0, '15:30:00'),('c005', 1, '10:00:00'),('c005', 0, '14:30:00'),('c005', 1, '15:30:00'),('c005', 0, '18:30:00');
-----------

I have provided an explanation and query, but I encourage you to try solving it first. Later, you can check the query for reference.

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. SessionDurations CTE: Use the LAG() function to get the timestamp of the previous state for each cust_id. Filter rows where state=0 because this indicates the end of a session. The session_start is derived from the LAG() value, and session_end is the current timestamp.

2. ActiveHours CTE: Calculate the active duration for each session in minutes using DATEDIFF(MINUTE, session_start, session_end).

3. Final SELECT: Sum the active minutes for each cust_id. Divide the total minutes by 60 to convert them to hours.

**SOLUTION**
```sql
WITH LogPairing AS (
	SELECT cust_id, state, timestamp,
    LAG(timestamp) OVER (PARTITION BY cust_id ORDER BY timestamp) AS prev_timestamp,
    LAG(state) OVER (PARTITION BY cust_id ORDER BY timestamp) AS prev_state
    FROM meta.customer_state_log
)
SELECT cust_id,
ROUND(SUM(TIMESTAMPDIFF(MINUTE, prev_timestamp, timestamp)) / 60.0, 2) AS active_hours
FROM LogPairing
WHERE state = 0
AND prev_state = 1
GROUP BY cust_id;
```

<img width="1580" height="747" alt="image" src="https://github.com/user-attachments/assets/ce467d68-f9e8-4cbc-9cb5-f7738d5cb461" />


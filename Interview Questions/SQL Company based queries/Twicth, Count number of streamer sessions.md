<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Twitch (Hard Level) hashtag#SQL Interview Question — Solution

From users who had their first session as a viewer, how many streamer sessions have they had? Return the user id and number of sessions in descending order. In case there are users with the same number of sessions, order them by ascending user id.

🌀By solving this, you'll learn how to use Cte, Group by, Join. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE twitch_sessions (user_id BIGINT, session_start DATETIME, session_end DATETIME, session_id BIGINT PRIMARY KEY, session_type VARCHAR(20) CHECK (session_type IN ('viewer', 'streamer')));

INSERT INTO twitch_sessions (user_id, session_start, session_end, session_id, session_type) VALUES (101, '2024-02-01 10:00:00', '2024-02-01 11:00:00', 1, 'viewer'), (101, '2024-02-02 14:00:00', '2024-02-02 15:30:00', 2, 'streamer'), (102, '2024-02-01 09:30:00', '2024-02-01 10:30:00', 3, 'viewer'), (102, '2024-02-03 16:00:00', '2024-02-03 17:00:00', 4, 'streamer'), (102, '2024-02-05 18:00:00', '2024-02-05 19:30:00', 5, 'streamer'), (103, '2024-02-02 11:00:00', '2024-02-02 12:00:00', 6, 'viewer'), (104, '2024-02-01 08:30:00', '2024-02-01 09:00:00', 7, 'viewer'), (104, '2024-02-04 20:00:00', '2024-02-04 21:00:00', 8, 'streamer'), (104, '2024-02-06 22:00:00', '2024-02-06 23:00:00', 9, 'streamer'), (104, '2024-02-07 15:00:00', '2024-02-07 16:30:00', 10, 'streamer');
---------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. FirstSession CTE: Finds the earliest session timestamp for each user where the session type was 'viewer'.

2. Join with twitch_sessions: Filters users whose first session was as a viewer.
Counts how many 'streamer' sessions each of these users had.

**SOLUTION**

<img width="800" height="478" alt="image" src="https://github.com/user-attachments/assets/d31c10de-900b-4d0c-9ae0-b54069e425c1" />

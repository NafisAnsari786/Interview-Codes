<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: EY, TCS, Deloitte, (Medium Level) hashtag#SQL Interview Question — Solution

In a marathon, gun time is counted from the moment of the formal start of the race while net time is counted from the moment a runner crosses a starting line. Both variables are in seconds.

You are asked to check if the interval between the two times is different for male and female runners. First, calculate the average absolute difference between the gun time and net time. Group the results by available genders (male and female). Output the absolute difference between those two values.

🔍By solving this, you'll learn how to use CTE, UNIONALL, CASE. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE marathon_male (age BIGINT, div_tot TEXT, gun_time BIGINT, hometown TEXT, net_time BIGINT, num BIGINT, pace BIGINT, person_name TEXT, place BIGINT);

INSERT INTO marathon_male (age, div_tot, gun_time, hometown, net_time, num, pace, person_name, place) VALUES (25, '1/100', 3600, 'New York', 3400, 101, 500, 'John Doe', 1), (30, '2/100', 4000, 'Boston', 3850, 102, 550, 'Michael Smith', 2), (22, '3/100', 4200, 'Chicago', 4150, 103, 600, 'David Johnson', 3);

CREATE TABLE marathon_female (age BIGINT, div_tot TEXT, gun_time BIGINT, hometown TEXT, net_time BIGINT, num BIGINT, pace BIGINT, person_name TEXT, place BIGINT);

INSERT INTO marathon_female (age, div_tot, gun_time, hometown, net_time, num, pace, person_name, place) VALUES (28, '1/100', 3650, 'San Francisco', 3600, 201, 510, 'Jane Doe', 1), (26, '2/100', 3900, 'Los Angeles', 3850, 202, 530, 'Emily Davis', 2), (24, '3/100', 4100, 'Seattle', 4050, 203, 590, 'Anna Brown', 3);
---------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. WITH AvgTimeDiff: This common table expression (CTE) calculates the average absolute time difference between gun_time and net_time for males and females separately. AVG(ABS(gun_time - net_time)) computes the average absolute difference for each gender.

2. UNION ALL: Combines the results for males and females into a single dataset.

3. ABS(MAX(CASE ... END) - MAX(CASE ... END)): Extracts the average time difference for males and females using a conditional CASE statement. Calculates the absolute difference between these two values.

**SOLUTION**

<img width="800" height="449" alt="image" src="https://github.com/user-attachments/assets/3aeeabcb-e665-414f-91df-53b1223b5a64" />

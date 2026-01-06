<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Netflix(Hard Level) hashtag#SQL Interview Question — Solution

Find all the users who were active for 3 consecutive days or more.

😍 Definitely you are going to enjoy by solving this, you'll learn how to use CTE and windows functions. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE sf_events (date DATETIME,account_id VARCHAR(10),user_id VARCHAR(10));

INSERT INTO sf_events (date, account_id, user_id) VALUES('2021-01-01', 'A1', 'U1'),('2021-01-01', 'A1', 'U2'),('2021-01-06', 'A1', 'U3'),('2021-01-02', 'A1', 'U1'),('2020-12-24', 'A1', 'U2'),('2020-12-08', 'A1', 'U1'),('2020-12-09', 'A1', 'U1'),('2021-01-10', 'A2', 'U4'),('2021-01-11', 'A2', 'U4'),('2021-01-12', 'A2', 'U4'),('2021-01-15', 'A2', 'U5'),('2020-12-17', 'A2', 'U4'),('2020-12-25', 'A3', 'U6'),('2020-12-25', 'A3', 'U6'),('2020-12-25', 'A3', 'U6'),('2020-12-06', 'A3', 'U7'),('2020-12-06', 'A3', 'U6'),('2021-01-14', 'A3', 'U6'),('2021-02-07', 'A1', 'U1'),('2021-02-10', 'A1', 'U2'),('2021-02-01', 'A2', 'U4'),('2021-02-01', 'A2', 'U5'),('2020-12-05', 'A1', 'U8');

---------

I have provided an explanation and query, but I encourage you to try solving it first. Later, you can check the query for reference

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. LAG and LEAD: LAG gets the previous date for each user. LEAD gets the next date for each user.

2. DATEDIFF: Ensures the difference between consecutive dates is exactly 1 day, which is essential for identifying consecutive activity.

3. Filtering: Filters records where both the previous day and the next day are consecutive.

4. DISTINCT user_id: Ensures each user is listed only once in the output if they meet the criteria.

**SOLUTION**

<img width="800" height="438" alt="image" src="https://github.com/user-attachments/assets/757e3515-cba2-42c3-8e84-b440b75df225" />

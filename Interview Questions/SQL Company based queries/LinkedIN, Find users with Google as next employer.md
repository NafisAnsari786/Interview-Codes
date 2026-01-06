<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Linkedln (Hard Level) hashtag#SQL Interview Question — Solution

Consider all LinkedIn users who, at some point, worked at Microsoft. For how many of them was Google their next employer right after Microsoft (no employers in between)?

🌀 Trust me, this one will seriously twist your brain! Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭:
CREATE TABLE linkedin_users (user_id INT,employer VARCHAR(255),position VARCHAR(255),start_date DATETIME,end_date DATETIME);

INSERT INTO linkedin_users (user_id, employer, position, start_date, end_date) VALUES(1, 'Microsoft', 'developer', '2020-04-13', '2021-11-01'),(1, 'Google', 'developer', '2021-11-01', NULL),(2, 'Google', 'manager', '2021-01-01', '2021-01-11'),(2, 'Microsoft', 'manager', '2021-01-11', NULL),(3, 'Microsoft', 'analyst', '2019-03-15', '2020-07-24'),(3, 'Amazon', 'analyst', '2020-08-01', '2020-11-01'),(3, 'Google', 'senior analyst', '2020-11-01', '2021-03-04'),(4, 'Google', 'junior developer', '2018-06-01', '2021-11-01'),(4, 'Google', 'senior developer', '2021-11-01', NULL),(5, 'Microsoft', 'manager', '2017-09-26', NULL),(6, 'Google', 'CEO', '2015-10-02', NULL);

-----------

I have provided an explanation and query, but I encourage you to try solving it first. Later, you can check the query for reference.

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. CTE with LEAD Function:
The LEAD function is used to look at the next employer chronologically based on the start_date for each user_id.
This provides an easy way to see if the next employer after Microsoft for each user is Google.

2. Main Query:
After defining the CTE, the main query simply selects user_id where the employer is Microsoft and the next employer is Google.
Since LEAD ignores any other employers in between, this will only select cases where Google is the immediate next employer after Microsoft, without any other employers in between.

**SOLUTION**

<img width="800" height="442" alt="image" src="https://github.com/user-attachments/assets/a0711901-6a58-4bad-b241-af7f3927b45d" />


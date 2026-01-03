<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Google (Medium Level) hashtag#SQL Interview Question — Solution

Find all records from days when the number of distinct users receiving emails was greater than the number of distinct users sending emails.

🔍 By solving this, you'll learn how to use agg function and join. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭:
CREATE TABLE google_gmail_emails (id INT PRIMARY KEY,from_user VARCHAR(50),to_user VARCHAR(50),day INT);

INSERT INTO google_gmail_emails (id, from_user, to_user, day) VALUES(0, '6edf0be4b2267df1fa', '75d295377a46f83236', 10),(1, '6edf0be4b2267df1fa', '32ded68d89443e808', 6),(2, '6edf0be4b2267df1fa', '55e60cfcc9dc49c17e', 10),(3, '6edf0be4b2267df1fa', 'e0e0defbb9ec47f6f7', 6),(4, '6edf0be4b2267df1fa', '47be2887786891367e', 1),(5, '6edf0be4b2267df1fa', '2813e59cf6c1ff698e', 6),(6, '6edf0be4b2267df1fa', 'a84065b7933ad01019', 8),(7, '6edf0be4b2267df1fa', '850badf89ed8f06854', 1),(8, '6edf0be4b2267df1fa', '6b503743a13d778200', 1),(9, '6edf0be4b2267df1fa', 'd63386c884aeb9f71d', 3),(10, '6edf0be4b2267df1fa', '5b8754928306a18b68', 2),(11, '6edf0be4b2267df1fa', '6edf0be4b2267df1fa', 8),(12, '6edf0be4b2267df1fa', '406539987dd9b679c0', 9),(13, '6edf0be4b2267df1fa', '114bafadff2d882864', 5),(14, '6edf0be4b2267df1fa', '157e3e9278e32aba3e', 2),(15, '75d295377a46f83236', '75d295377a46f83236', 6),(16, '75d295377a46f83236', 'd63386c884aeb9f71d', 8),(17, '75d295377a46f83236', '55e60cfcc9dc49c17e', 3),(18, '75d295377a46f83236', '47be2887786891367e', 10),(19, '75d295377a46f83236', '5b8754928306a18b68', 10),(20, '75d295377a46f83236', '850badf89ed8f06854', 7);
------------

I have provided an explanation and query, but I encourage you to try solving it first. Later, you can check the query for reference.

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. The distinct_counts CTE calculates the number of distinct to_user and from_user for each day.

2. The main query joins the original google_gmail_emails table with distinct_counts on the day field, selecting only records where distinct_receivers is greater than distinct_senders.

**SOLUTION**

<img width="800" height="686" alt="image" src="https://github.com/user-attachments/assets/b981e065-aff4-4e89-8765-7f2c96a8a279" />


𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: JP Morgan, Chase, Bloomberg (Medium Level) hashtag#SQL Interview Question — Solution

Bank of Ireland has requested that you detect invalid transactions in December 2022. An invalid transaction is one that occurs outside of the bank's normal business hours. The following are the hours of operation for all branches:

Monday - Friday 09:00 - 16:00
Saturday & Sunday Closed
Irish Public Holidays 25th and 26th December
Determine the transaction ids of all invalid transactions.

💸 Tech-driven financial firms have asked this question in interviews. By solving this, you'll learn how to use time and date function. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭:
CREATE TABLE boi_transactions (transaction_id INT PRIMARY KEY,time_stamp DATETIME NOT NULL);

INSERT INTO boi_transactions (transaction_id, time_stamp) VALUES(1051, '2022-12-03 10:15'),(1052, '2022-12-03 17:00'),(1053, '2022-12-04 10:00'),(1054, '2022-12-04 14:00'),(1055, '2022-12-05 08:59'),(1056, '2022-12-05 16:01'),(1057, '2022-12-06 09:00'),(1058, '2022-12-06 15:59'),(1059, '2022-12-07 12:00'),(1060, '2022-12-08 09:00'),(1061, '2022-12-09 10:00'),(1062, '2022-12-10 11:00'),(1063, '2022-12-10 17:30'),(1064, '2022-12-11 12:00'),(1065, '2022-12-12 08:59'),(1066, '2022-12-12 16:01'),(1067, '2022-12-25 10:00'),(1068, '2022-12-25 15:00'),(1069, '2022-12-26 09:00'),(1070, '2022-12-26 14:00'),(1071, '2022-12-26 16:30'),(1072, '2022-12-27 09:00'),(1073, '2022-12-28 08:30'),(1074, '2022-12-29 16:15'),(1075, '2022-12-30 14:00'),(1076, '2022-12-31 10:00');
------------

I have provided an explanation and query, but I encourage you to try solving it first. Later, you can check the query for reference.

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. MONTH(time_stamp) = 12 AND YEAR(time_stamp) = 2022: This filters transactions to include only those in December 2022.

2. DATEPART(WEEKDAY, time_stamp) IN (1, 7): This checks if the transaction occurred on a Saturday (7) or Sunday (1).

3. CAST(time_stamp AS TIME) < '09:00:00': This checks if the transaction time is before the opening hours.

4. CAST(time_stamp AS TIME) > '16:00:00': This checks if the transaction time is after the closing hours.

5. (DATEPART(DAY, time_stamp) IN (25, 26) AND MONTH(time_stamp) = 12): This checks if the transaction occurred on the public holidays of December 25th or 26th.

**SOLUTION**

<img width="800" height="440" alt="image" src="https://github.com/user-attachments/assets/e047de4a-afce-487b-aba5-5df33fa6f011" />

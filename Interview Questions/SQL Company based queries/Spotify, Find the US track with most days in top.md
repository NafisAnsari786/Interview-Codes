<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Spotify(Hard Level) hashtag#SQL Interview Question — Solution

Find the number of days a US track has stayed in the 1st position for both the US and worldwide rankings on the same day. Output the track name and the number of days in the 1st position. Order your output alphabetically by track name. If the region 'US' appears in dataset, it should be included in the worldwide ranking

🔍By solving this, you'll learn how to use group by. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE spotify_daily_rankings_2017_us (position INT,trackname VARCHAR(255),artist VARCHAR(255),streams INT,url VARCHAR(255),date DATETIME);

INSERT INTO spotify_daily_rankings_2017_us (position, trackname, artist, streams, url, date)VALUES(1, 'Track A', 'Artist 1', 500000, 'https://url1.com', '2017-01-01'),(2, 'Track B', 'Artist 2', 400000, 'https://url2.com', '2017-01-01'),(1, 'Track A', 'Artist 1', 520000, 'https://url1.com', '2017-01-02'),(3, 'Track C', 'Artist 3', 300000, 'https://url3.com', '2017-01-02'),(1, 'Track D', 'Artist 4', 600000, 'https://url4.com', '2017-01-03');

CREATE TABLE spotify_worldwide_daily_song_ranking (id INT,position INT,trackname VARCHAR(255),artist VARCHAR(255),streams INT,url VARCHAR(255),date DATETIME,region VARCHAR(50));

INSERT INTO spotify_worldwide_daily_song_ranking (id, position, trackname, artist, streams, url, date, region)VALUES(1, 1, 'Track A', 'Artist 1', 550000, 'https://url1.com', '2017-01-01', 'US'),(2, 2, 'Track B', 'Artist 2', 450000, 'https://url2.com', '2017-01-01', 'US'),(3, 1, 'Track A', 'Artist 1', 530000, 'https://url1.com', '2017-01-02', 'US'),(4, 1, 'Track D', 'Artist 4', 610000, 'https://url4.com', '2017-01-03', 'US'),(5, 3, 'Track C', 'Artist 3', 320000, 'https://url3.com', '2017-01-03', 'US');

---------

I have provided an explanation and query, but I encourage you to try solving it first. Later, you can check the query for reference

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. JOIN: We join spotify_daily_rankings_2017_us and spotify_worldwide_daily_song_ranking on trackname and date so we can compare the rankings on the same day.
2. WHERE: We ensure that both the US and worldwide rankings have the track in the 1st position (position = 1)
3. GROUP BY: We group by trackname to count the number of days it stayed at the 1st position
4. COUNT(*): This counts the number of days a track was ranked 1st in both datasets

**SOLUTION**

<img width="800" height="538" alt="image" src="https://github.com/user-attachments/assets/1af58fdd-1c28-4c79-a36b-52607b98691b" />

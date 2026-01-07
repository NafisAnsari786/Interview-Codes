<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Amazon (Hard Level) hashtag#SQL Interview Question — Solution

You are given a table of tennis players and their matches that they could either win (W) or lose (L). Find the longest streak of wins. A streak is a set of consecutive won matches of one player. The streak ends once a player loses their next match. Output the ID of the player or players and the length of the streak.

🌀 Trust me, this one will surely challenge you...! You'll learn Mutiple Ctes, Joins, Group by. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE players_results ( match_date DATETIME, match_result VARCHAR(1), player_id BIGINT);

INSERT INTO players_results (match_date, match_result, player_id) VALUES ('2023-01-01', 'W', 1), ('2023-01-02', 'W', 1), ('2023-01-03', 'L', 1), ('2023-01-04', 'W', 1), ('2023-01-01', 'L', 2), ('2023-01-02', 'W', 2), ('2023-01-03', 'W', 2), ('2023-01-04', 'W', 2), ('2023-01-05', 'L', 2), ('2023-01-01', 'W', 3), ('2023-01-02', 'W', 3), ('2023-01-03', 'W', 3), ('2023-01-04', 'W', 3), ('2023-01-05', 'L', 3);

---------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. RankedMatches CTE: Assigns a row number to each match for each player (match_rank). Also assigns a row number (win_rank) for each winning match sequence to group consecutive wins.

2. match_rank - win_rank Logic: The difference between match_rank and win_rank groups consecutive wins into streaks. Matches in the same streak have the same difference.

3. WinStreaks CTE: Counts the number of matches in each streak of wins for a player.

4. LongestStreaks CTE: Finds the maximum streak length for each player by taking the maximum streak_length.

5. Final Output: Outputs the player ID and their longest win streak, sorted by the streak length in descending order.

**SOLUTION**

<img width="800" height="702" alt="image" src="https://github.com/user-attachments/assets/db2331f8-9462-471f-9602-7b3f0137c18e" />

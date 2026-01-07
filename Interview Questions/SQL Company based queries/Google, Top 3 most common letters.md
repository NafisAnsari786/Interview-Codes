<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Google (Hard Level) hashtag#SQL Interview Question — Solution

Find the top 3 most common letters across all the words from both the tables (ignore filename column). Output the letter along with the number of occurrences and order records in descending order based on the number of occurrences.

🌀 Trust me, this one will surely challenge you...! You'll learn Cte, Windows Function, Union, Group by. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE google_file_store (contents VARCHAR(MAX), filename VARCHAR(255));

INSERT INTO google_file_store (contents, filename) VALUES ('This is a sample content with some words.', 'file1.txt'), ('Another file with more words and letters.', 'file2.txt'), ('Text for testing purposes with various characters.', 'file3.txt');

CREATE TABLE google_word_lists ( words1 VARCHAR(MAX), words2 VARCHAR(MAX));

INSERT INTO google_word_lists (words1, words2) VALUES ('apple banana cherry', 'dog elephant fox'), ('grape honeydew kiwi', 'lemon mango nectarine'), ('orange papaya quince', 'raspberry strawberry tangerine');

---------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. Cross Apply with ROW_NUMBER: This generates numbers from 1 to the length of the text, allowing us to extract each character individually using SUBSTRING.

2. Filtering Characters: Only letters ([A-Z]) are considered. The UPPER function ensures case normalization.

3. Combining Results: UNION ALL merges the letter frequencies from google_file_store.contents, google_word_lists.words1, and google_word_lists.words2.

**SOLUTION**

<img width="800" height="633" alt="image" src="https://github.com/user-attachments/assets/bffe0734-fbdc-43e2-9f3b-a595c9683be6" />

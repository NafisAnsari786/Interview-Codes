<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: IBM (Medium Level) hashtag#SQL Interview Question — Solution

Calculate the total number of interactions and the total number of contents created for each customer. Include all interaction types and content types in your calculations. Your output should include the customer's ID, the total number of interactions, and the total number of content items.

🌀By solving this, you'll learn how to use coalesce, outer join, subquery. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE customer_interactions (customer_id BIGINT, interaction_date DATETIME, interaction_id BIGINT, interaction_type VARCHAR(50));

INSERT INTO customer_interactions (customer_id, interaction_date, interaction_id, interaction_type) VALUES (1, '2023-01-15 10:30:00', 101, 'Click'), (1, '2023-01-16 11:00:00', 102, 'Purchase'), (2, '2023-01-17 14:45:00', 103, 'View'), (3, '2023-01-18 09:20:00', 104, 'Share'), (3, '2023-01-18 09:25:00', 105, 'Like'), (4, '2023-01-19 12:10:00', 106, 'Comment');

CREATE TABLE user_contents (content_id BIGINT, content_text VARCHAR(255), content_type VARCHAR(50), customer_id BIGINT);

INSERT INTO user_contents (content_id, content_text, content_type, customer_id) VALUES (201, 'Welcome Post', 'Blog', 1), (202, 'Product Review', 'Review', 2), (203, 'Event Photos', 'Photo', 3), (204, 'Tutorial Video', 'Video', 3), (205, 'Survey Response', 'Survey', 4);

---------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. COALESCE Function: Handles cases where a customer has interactions but no content (or vice versa), ensuring the count is not null.

2. FULL OUTER JOIN: Combines data from both tables, including customers who may only have entries in one of the tables.

3. COUNT(DISTINCT ...): Ensures unique counts for interaction IDs and content IDs.

4. GROUP BY: Aggregates the results by customer ID to calculate totals for each customer.

**SOLUTION**

<img width="800" height="363" alt="image" src="https://github.com/user-attachments/assets/14de3f6a-968e-491c-94b1-3d7d7b64f1c0" />

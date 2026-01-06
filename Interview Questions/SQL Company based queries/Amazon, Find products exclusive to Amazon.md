<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Amazon (Hard Level) hashtag#SQL Interview Question — Solution

Find products which are exclusive to only Amazon and therefore not sold at Top Shop and Macy's. Your output should include the product name, brand name, price, and rating.

Two products are considered equal if they have the same product name and same maximum retail price (mrp column).

🔍By solving this, you'll learn how to use mutiple join. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭:
CREATE TABLE innerwear_amazon_com (product_name VARCHAR(255),mrp VARCHAR(50),price VARCHAR(50),pdp_url VARCHAR(255),brand_name VARCHAR(100),product_category VARCHAR(100),retailer VARCHAR(100),description VARCHAR(255),rating FLOAT,review_count INT,style_attributes VARCHAR(255),total_sizes VARCHAR(50),available_size VARCHAR(50),color VARCHAR(50));

CREATE TABLE innerwear_macys_com (product_name VARCHAR(255),mrp VARCHAR(50),price VARCHAR(50),pdp_url VARCHAR(255),brand_name VARCHAR(100),product_category VARCHAR(100),retailer VARCHAR(100),description VARCHAR(255),rating FLOAT,review_count FLOAT,style_attributes VARCHAR(255),total_sizes VARCHAR(50),available_size VARCHAR(50),color VARCHAR(50));

CREATE TABLE innerwear_topshop_com (product_name VARCHAR(255),mrp VARCHAR(50),price VARCHAR(50),pdp_url VARCHAR(255),brand_name VARCHAR(100),product_category VARCHAR(100),retailer VARCHAR(100),description VARCHAR(255),rating FLOAT,review_count FLOAT,style_attributes VARCHAR(255),total_sizes VARCHAR(50),available_size VARCHAR(50),color VARCHAR(50));

𝐃𝐮𝐞 𝐭𝐨 𝐰𝐨𝐫𝐝 𝐜𝐨𝐧𝐬𝐭𝐫𝐚𝐢𝐧𝐭𝐬, 𝐈'𝐯𝐞 𝐚𝐭𝐭𝐚𝐜𝐡𝐞𝐝 𝐭𝐡𝐞 𝐢𝐧𝐬𝐞𝐫𝐭 𝐪𝐮𝐞𝐫𝐲 𝐢𝐧 𝐭𝐡𝐞 𝐜𝐨𝐦𝐦𝐞𝐧𝐭 𝐬𝐞𝐜𝐭𝐢𝐨𝐧 𝐛𝐞𝐥𝐨𝐰. 𝐏𝐥𝐞𝐚𝐬𝐞 𝐫𝐞𝐭𝐫𝐢𝐞𝐯𝐞 𝐢𝐭 𝐟𝐫𝐨𝐦 𝐭𝐡𝐞𝐫𝐞.
-----------

I have provided an explanation and query, but I encourage you to try solving it first. Later, you can check the query for reference.

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. LEFT JOINs: Amazon's products are left joined with Macy’s and Top Shop on both product_name and mrp columns.

2. WHERE clause: Filters for cases where m.product_name and t.product_name are NULL, indicating no match in Macy’s or Top Shop, meaning these products are exclusive to Amazon.

3. Output: Returns Amazon-exclusive products with columns product_name, brand_name, price, and rating, sorted by product_name.

**SOLUTION**

<img width="800" height="477" alt="image" src="https://github.com/user-attachments/assets/6da8b121-6b5d-4369-9e80-d5aacff9c08b" />

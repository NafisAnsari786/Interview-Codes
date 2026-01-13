<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Airbnb (Hard Level) hashtag#SQL Interview Question — Solution

Estimate the growth of Airbnb each year using the number of hosts registered as the growth metric. The rate of growth is calculated by taking ((number of hosts registered in the current year - number of hosts registered in the previous year) / the number of hosts registered in the previous year) * 100. Output the year, number of hosts in the current year, number of hosts in the previous year, and the rate of growth. Round the rate of growth to the nearest percent and order the result in the ascending order based on the year. 

Assume that the dataset consists only of unique hosts, meaning there are no duplicate hosts listed.

🌀 Definitely you are going to enjoy by solving this, you'll learn how to use multiple CTE and windows functions. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE airbnb_search_details ( id INT PRIMARY KEY, price FLOAT, property_type VARCHAR(100), room_type VARCHAR(100), amenities VARCHAR(MAX), accommodates INT, bathrooms INT, bed_type VARCHAR(50), cancellation_policy VARCHAR(50), cleaning_fee BIT, city VARCHAR(100), host_identity_verified VARCHAR(10), host_response_rate VARCHAR(10), host_since DATETIME, neighbourhood VARCHAR(100), number_of_reviews INT, review_scores_rating FLOAT, zipcode INT, bedrooms INT, beds INT);

INSERT INTO airbnb_search_details (id, price, property_type, room_type, amenities, accommodates, bathrooms, bed_type, cancellation_policy, cleaning_fee, city, host_identity_verified, host_response_rate, host_since, neighbourhood, number_of_reviews, review_scores_rating, zipcode, bedrooms, beds)VALUES(7, 150, 'House', 'Entire home/apt', 'WiFi, Kitchen', 5, 2, 'Queen Bed', 'Flexible', 1, 'Seattle', 'Yes', '90%', '2019-05-30', 'Capitol Hill', 200, 4.6, 98102, 2, 3),(8, 60, 'Apartment', 'Shared room', 'WiFi', 1, 1, 'Single Bed', 'Moderate', 0, 'Boston', 'Yes', '80%', '2018-04-18', 'Beacon Hill', 50, 4.2, 02108, 1, 1),(9, 90, 'House', 'Private room', 'WiFi, Parking', 3, 2, 'King Bed', 'Strict', 1, 'Denver', 'No', '85%', '2021-02-10', 'Downtown', 75, 4.0, 80202, 1, 2),(10, 250, 'Villa', 'Entire home/apt', 'Pool, WiFi, Kitchen', 8, 4, 'King Bed', 'Flexible', 1, 'Las Vegas', 'Yes', '95%', '2022-06-15', 'The Strip', 400, 4.9, 89109, 4, 5);

---------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. YearlyHostCount CTE: Extracts the year from host_since and counts the distinct number of hosts (id) registered for each year. Ensures host_since is not null.

2. GrowthCalculation CTE: Self-joins the YearlyHostCount CTE to get the number of hosts for the current year and the previous year. Calculates the growth rate using the formula. 

3. Handles cases where the previous year has 0 hosts to avoid division by zero.

**SOLUTION**

<img width="762" height="908" alt="image" src="https://github.com/user-attachments/assets/79ce9e88-e649-4879-ab14-dff86eca18c8" />


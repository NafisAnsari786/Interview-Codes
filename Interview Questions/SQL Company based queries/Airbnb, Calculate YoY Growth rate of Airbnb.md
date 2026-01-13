<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Airbnb (Hard Level) hashtag#SQL Interview Question — Solution

Estimate the growth of Airbnb each year using the number of hosts registered as the growth metric. The rate of growth is calculated by taking ((number of hosts registered in the current year - number of hosts registered in the previous year) / the number of hosts registered in the previous year) * 100. Output the year, number of hosts in the current year, number of hosts in the previous year, and the rate of growth. Round the rate of growth to the nearest percent and order the result in the ascending order based on the year. 

Assume that the dataset consists only of unique hosts, meaning there are no duplicate hosts listed.

🌀 Definitely you are going to enjoy by solving this, you'll learn how to use multiple CTE and windows functions. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE meta.airbnb_search_details ( id INT PRIMARY KEY, price FLOAT, property_type VARCHAR(100), room_type VARCHAR(100), amenities VARCHAR(1000), accommodates INT, bathrooms INT, bed_type VARCHAR(50), cancellation_policy VARCHAR(50), cleaning_fee TINYINT(1), city VARCHAR(100), host_identity_verified VARCHAR(10), host_response_rate VARCHAR(10), host_since DATETIME, neighbourhood VARCHAR(100), number_of_reviews INT, review_scores_rating FLOAT, zipcode VARCHAR(10), bedrooms INT, beds INT);


INSERT INTO airbnb_search_details (id, price, property_type, room_type, amenities, accommodates, bathrooms, bed_type, cancellation_policy, cleaning_fee, city, host_identity_verified, host_response_rate, host_since, neighbourhood, number_of_reviews, review_scores_rating, zipcode, bedrooms, beds)VALUES(1, 100, 'Apartment', 'Entire home/apt', 'WiFi, Kitchen', 2, 1, 'Real Bed', 'Flexible', 1, 'New York', 'Yes', '90%', '2019-01-15', 'Manhattan', 120, 4.8, 10001, 1, 1),(2, 75, 'House', 'Private room', 'WiFi, Parking', 3, 1, 'Queen Bed', 'Moderate', 0, 'Los Angeles', 'Yes', '80%', '2018-06-22', 'Hollywood', 80, 4.5, 90001, 2, 1),(3, 50, 'Shared Room', 'Shared room', 'WiFi', 1, 1, 'Single Bed', 'Strict', 0, 'Chicago', 'No', '70%', '2019-03-10', 'Lincoln Park', 40, 3.8, 60614, 1, 1),(4, 200, 'Villa', 'Entire home/apt', 'Pool, WiFi', 6, 3, 'King Bed', 'Flexible', 1, 'Miami', 'Yes', '95%', '2020-07-05', 'Miami Beach', 300, 4.9, 33139, 3, 4),(5, 120, 'Apartment', 'Entire home/apt', 'WiFi, Kitchen, Parking', 4, 2, 'Double Bed', 'Moderate', 1, 'San Francisco', 'Yes', '85%', '2021-09-18', 'Downtown', 150, 4.7, 94102, 2, 2),(6, 80, 'Apartment', 'Private room', 'WiFi', 2, 1, 'Queen Bed', 'Strict', 0, 'Austin', 'No', '75%', '2020-11-22', 'Downtown', 100, 4.4, 78701, 1, 1),(7, 150, 'House', 'Entire home/apt', 'WiFi, Kitchen', 5, 2, 'Queen Bed', 'Flexible', 1, 'Seattle', 'Yes', '90%', '2019-05-30', 'Capitol Hill', 200, 4.6, 98102, 2, 3),(8, 60, 'Apartment', 'Shared room', 'WiFi', 1, 1, 'Single Bed', 'Moderate', 0, 'Boston', 'Yes', '80%', '2018-04-18', 'Beacon Hill', 50, 4.2, 02108, 1, 1),(9, 90, 'House', 'Private room', 'WiFi, Parking', 3, 2, 'King Bed', 'Strict', 1, 'Denver', 'No', '85%', '2021-02-10', 'Downtown', 75, 4.0, 80202, 1, 2),(10, 250, 'Villa', 'Entire home/apt', 'Pool, WiFi, Kitchen', 8, 4, 'King Bed', 'Flexible', 1, 'Las Vegas', 'Yes', '95%', '2022-06-15', 'The Strip', 400, 4.9, 89109, 4, 5);

---------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. YearlyHostCount CTE: Extracts the year from host_since and counts the distinct number of hosts (id) registered for each year. Ensures host_since is not null.

2. GrowthCalculation CTE: Self-joins the YearlyHostCount CTE to get the number of hosts for the current year and the previous year. Calculates the growth rate using the formula. 

3. Handles cases where the previous year has 0 hosts to avoid division by zero.

**SOLUTION**

```sql
WITH YearlyHostCount AS (
    SELECT 
        EXTRACT(YEAR FROM host_since) AS current_year,
        COUNT(id) AS hosts_in_current_year
        FROM meta.airbnb_search_details
        GROUP BY EXTRACT(YEAR FROM host_since)
),
GrowthData AS (
    SELECT 
        current_year,
        hosts_in_current_year,
        LAG(hosts_in_current_year) OVER (ORDER BY current_year) AS hosts_in_previous_year
        FROM YearlyHostCount
)
SELECT
    current_year,
    hosts_in_current_year,
    hosts_in_previous_year,
    ROUND(
        ((hosts_in_current_year - hosts_in_previous_year) * 100.0) / NULLIF(hosts_in_previous_year, 0), 2
     ) AS Growth_Rate
FROM GrowthData
ORDER BY current_year ASC;
```

<img width="768" height="246" alt="image" src="https://github.com/user-attachments/assets/525e673e-ac0b-48bc-9472-a3d1285c87a0" />



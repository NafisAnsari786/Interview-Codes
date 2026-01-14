<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Google, Airbnb, Expedia(Medium Level) hashtag#SQL Interview Question — Solution

Find the Top three hotels with the highest ratings. Output the hotel name along with the corresponding average score. Sort records based on the average score in descending order.

🔍Give a test and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE hotel_address (hotel_address VARCHAR(255),additional_number_of_scoring INT,review_date DATETIME,average_score FLOAT,hotel_name VARCHAR(255),reviewer_nationality VARCHAR(50),negative_review VARCHAR(MAX),review_total_negative_word_counts INT,total_number_of_reviews INT,positive_review VARCHAR(MAX),review_total_positive_word_counts INT,total_number_of_reviews_reviewer_has_given INT,reviewer_score FLOAT,tags VARCHAR(255),days_since_review VARCHAR(50),lat FLOAT,lng FLOAT);

INSERT INTO hotel_address (hotel_address, additional_number_of_scoring, review_date, average_score, hotel_name, reviewer_nationality, negative_review, review_total_negative_word_counts, total_number_of_reviews, positive_review, review_total_positive_word_counts, total_number_of_reviews_reviewer_has_given, reviewer_score, tags, days_since_review, lat, lng)VALUES('123 Ocean Ave, Miami, FL', 3, '2024-11-10', 4.2, 'Ocean View', 'American', 'Room small, but clean.', 5, 150, 'Great location and friendly staff!', 8, 30, 4.5, 'beachfront, family-friendly', '5 days', 25.7617, -80.1918),('456 Mountain Rd, Boulder, CO', 2, '2024-11-12', 3.9, 'Mountain Lodge', 'Canadian', 'wifi slow.', 3, 120, 'nice rooms.', 10, 20, 4.0, 'scenic, nature', '3 days', 40.015, -105.2705),('789 Downtown St, New York, NY', 5, '2024-11-15', 4.7, 'Central Park Hotel', 'British', 'Noisy, sleep.', 7, 200, 'Perfect location near Central Park.', 12, 50, 4.7, 'luxury, city-center', '1 day', 40.7831, -73.9712),('101 Lakeside Blvd, Austin, TX', 1, '2024-11-08', 4.0, 'Lakeside Inn', 'Mexican', 'food avg.', 4, 80, 'Nice, friendly service.', 6, 15, 3.8, 'relaxing, family', '10 days', 30.2672, -97.7431),('202 River Ave, Nashville, TN', 4, '2024-11-13', 4.5, 'Riverside', 'German', 'Limited parking', 2, 175, 'Great rooms.', 9, 25, 4.2, 'riverfront, peaceful', '2 days', 36.1627, -86.7816);

---------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
The question might look intimidating at first glance—detailed enough to make you wonder, what even is this? But it's so simple ryt...

**SOLUTION**
```sql
 WITH HighestRatings AS (
	SELECT hotel_name, average_score,
    DENSE_RANK() OVER (ORDER BY average_score DESC) AS d_rnk
    FROM hotel_address
)
SELECT hotel_name, average_Score
FROM HighestRatings
WHERE d_rnk <= 3;
```
<img width="1152" height="540" alt="image" src="https://github.com/user-attachments/assets/7a1daf08-39de-4c9e-ae53-63bbf21a5a29" />


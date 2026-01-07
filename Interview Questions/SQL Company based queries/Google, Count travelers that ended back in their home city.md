<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Google (Medium Level) hashtag#SQL Interview Question — Solution

A group of travelers embark on world tours starting with their home cities. Each traveler has an undecided itinerary that evolves over the course of the tour. Some travelers decide to abruptly end their journey mid-travel and live in their last destination.

Given the dataset of dates on which they travelled between different pairs of cities, can you find out how many travellers ended back in their home city? For simplicity, you can assume that each traveler made at most one trip between two cities in a day.

🌀By solving this, you'll learn how to use Ctes, Group by, Agg function. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE travel_history (date DATE, start_city VARCHAR(50), end_city VARCHAR(50), traveler VARCHAR(50));

INSERT INTO travel_history (date, start_city, end_city, traveler) VALUES ('2024-01-01', 'Delhi', 'Dubai', 'Amit'), ('2024-01-05', 'Dubai', 'London', 'Amit'), ('2024-01-10', 'London', 'Delhi', 'Amit'), ('2024-02-01', 'Mumbai', 'Singapore', 'Priya'), ('2024-02-05', 'Singapore', 'Sydney', 'Priya'), ('2024-02-10', 'Sydney', 'New York', 'Priya'), ('2024-03-01', 'Kolkata', 'Bangkok', 'Raj'), ('2024-03-03', 'Bangkok', 'Tokyo', 'Raj'), ('2024-03-07', 'Tokyo', 'Kolkata', 'Raj'), ('2024-04-01', 'Bangalore', 'Paris', 'Neha'), ('2024-04-05', 'Paris', 'Rome', 'Neha'), ('2024-04-10', 'Rome', 'Berlin', 'Neha'), ('2024-05-01', 'Chennai', 'Dubai', 'Arjun'), ('2024-05-03', 'Dubai', 'Amsterdam', 'Arjun'), ('2024-05-06', 'Amsterdam', 'Chennai', 'Arjun'); 

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. ranked_trips: Assigns row numbers to each trip per traveler by date

2. first_last_cities: Extracts the home_city (from first trip) and final_city (from last trip)

3. Final SELECT: Compares both and counts those who returned home

**SOLUTION**

<img width="800" height="565" alt="image" src="https://github.com/user-attachments/assets/7d2c3e0e-47f0-4d73-b4a0-23b581d17f03" />

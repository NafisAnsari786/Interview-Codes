<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Airbnb(Medium Level) hashtag#SQL Interview Question — Solution

Find the total number of available beds per hosts' nationality.
Output the nationality along with the corresponding total number of available beds. Sort records by the total available beds in descending order.

🔍 It's straightforward, read the question carefully and give it a try! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭:
CREATE TABLE airbnb_apartments(host_id int,apartment_id varchar(5),apartment_type varchar(10),n_beds int,n_bedrooms int,country varchar(20),city varchar(20));
INSERT INTO airbnb_apartments VALUES(0,'A1','Room',1,1,'USA','NewYork'),(0,'A2','Room',1,1,'USA','NewJersey'),(0,'A3','Room',1,1,'USA','NewJersey'),(1,'A4','Apartment',2,1,'USA','Houston'),(1,'A5','Apartment',2,1,'USA','LasVegas'),(3,'A7','Penthouse',3,3,'China','Tianjin'),(3,'A8','Penthouse',5,5,'China','Beijing'),(4,'A9','Apartment',2,1,'Mali','Bamako'),(5,'A10','Room',3,1,'Mali','Segou')

CREATE TABLE airbnb_hosts(host_id int,nationality  varchar(15),gender varchar(5),age int);
INSERT INTO airbnb_hosts  VALUES(0,'USA','M',28),(1,'USA','F',29),(2,'China','F',31),(3,'China','M',24),(4,'Mali','M',30),(5,'Mali','F',30);
-------------

I have provided an explanation and query, but I encourage you to try solving it first. Later, you can check the query for reference.

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐨𝐟 𝐭𝐡𝐞 𝐐𝐮𝐞𝐫𝐲:
1. Joining Tables: The first step involves joining the airbnb_apartments and airbnb_hosts tables on the host_id. This allows us to combine the apartment details (such as the number of beds) with the host's nationality information.

2. Grouping and Aggregating: Next, the data is grouped by the host's nationality, so that the total number of beds available for each nationality can be calculated. The SUM() function is used to add up the beds (n_beds) for all apartments hosted by individuals of the same nationality.

3. Sorting the Results: Finally, the results are ordered in descending order based on the total number of available beds. This ensures that nationalities with the highest number of available beds appear at the top of the list.

**SOLUTION**

<img width="800" height="573" alt="image" src="https://github.com/user-attachments/assets/681995a6-f3f4-47fa-babc-ff371ecc6539" />


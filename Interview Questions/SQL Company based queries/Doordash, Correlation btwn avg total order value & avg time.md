<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: DoorDash(Hard Level) hashtag#SQL Interview Question — Solution

You have been asked to investigate whether there is a correlation between the average total order value and the average time in minutes between placing an order and having it delivered per restaurant.

You have also been told that the column order_total represents the gross order total for each order. Therefore, you'll need to calculate the net order total.

The gross order total is the total of the order before adding the tip and deducting the discount and refund. Make sure correlation is rounded to 2 decimals

🔍By solving this, you'll learn how to use cte, groupby, agg fun. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭:
CREATE TABLE delivery_details (customer_placed_order_datetime   DATETIME, placed_order_with_restaurant_datetime DATETIME, driver_at_restaurant_datetime DATETIME, delivered_to_consumer_datetime   DATETIME, driver_id BIGINT, restaurant_id BIGINT, consumer_id BIGINT, is_new TINYINT, delivery_region VARCHAR(255), is_asap TINYINT, order_total FLOAT, discount_amount FLOAT, tip_amount FLOAT, refunded_amount FLOAT);

INSERT INTO delivery_details (customer_placed_order_datetime, placed_order_with_restaurant_datetime, driver_at_restaurant_datetime, delivered_to_consumer_datetime, driver_id, restaurant_id, consumer_id, is_new, delivery_region, is_asap, order_total, discount_amount, tip_amount, refunded_amount) VALUES
('2024-02-01 12:00:00', '2024-02-01 12:05:00', '2024-02-01 12:15:00', '2024-02-01 12:30:00', 101, 1, 1001, 1, 'New York', 1, 50.00, 5.00, 3.00, 0.00),
('2024-02-01 13:10:00', '2024-02-01 13:15:00', '2024-02-01 13:25:00', '2024-02-01 13:50:00', 102, 2, 1002, 0, 'Los Angeles', 0, 75.00, 10.00, 5.00, 2.00),
('2024-02-01 14:30:00', '2024-02-01 14:40:00', '2024-02-01 14:50:00', '2024-02-01 15:05:00', 103, 1, 1003, 1, 'New York', 1, 60.00, 8.00, 4.00, 0.00),
('2024-02-01 15:00:00', '2024-02-01 15:05:00', '2024-02-01 15:15:00', '2024-02-01 15:45:00', 104, 3, 1004, 0, 'Chicago', 0, 90.00, 15.00, 6.00, 5.00),
('2024-02-01 16:20:00', '2024-02-01 16:25:00', '2024-02-01 16:35:00', '2024-02-01 16:50:00', 105, 2, 1005, 1, 'Los Angeles', 1, 110.00, 20.00, 8.00, 0.00);

**SOLUTION**

<img width="800" height="515" alt="image" src="https://github.com/user-attachments/assets/396ea099-caac-45c4-8e00-dcde3b32c99f" />

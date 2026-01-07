<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Goldman Sachs(Medium Level) hashtag#SQL Interview Question — Solution

You are given a list of exchange rates from various currencies to US Dollars (USD) in different months. Show how the exchange rate of all the currencies changed in the first half of 2020. Output the currency code and the difference between values of the exchange rate between July 1, 2020 and January 1, 2020.

🌀 Trust me, this one will surely challenge you...! You'll learn Cte, Agg function, Group by. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE sf_exchange_rates ( date DATETIME, exchange_rate FLOAT, source_currency VARCHAR(10), target_currency VARCHAR(10));

INSERT INTO sf_exchange_rates (date, exchange_rate, source_currency, target_currency) VALUES ('2020-01-01', 1.12, 'EUR', 'USD'), ('2020-01-01', 1.31, 'GBP', 'USD'), ('2020-01-01', 109.56, 'JPY', 'USD'), ('2020-07-01', 1.17, 'EUR', 'USD'), ('2020-07-01', 1.29, 'GBP', 'USD'), ('2020-07-01', 109.66, 'JPY', 'USD'), ('2020-01-01', 0.75, 'AUD', 'USD'), ('2020-07-01', 0.73, 'AUD', 'USD'), ('2020-01-01', 6.98, 'CNY', 'USD'), ('2020-07-01', 7.05, 'CNY', 'USD');

---------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. WITH exchange_rate_changes: Filters the data to only consider date values of January 1, 2020, and July 1, 2020. Uses MAX(CASE ...) to capture the exchange rate for these specific dates for each source_currency.

2. COALESCE(rate_july, 0) - COALESCE(rate_jan, 0): Calculates the difference in exchange rates. If data is missing for any date, it replaces the rate with 0 using COALESCE.

3. GROUP BY: Groups by the currency code (source_currency).

**SOLUTION**

<img width="800" height="699" alt="image" src="https://github.com/user-attachments/assets/deaf8c62-fdde-437c-b24a-69dc5088fa0a" />


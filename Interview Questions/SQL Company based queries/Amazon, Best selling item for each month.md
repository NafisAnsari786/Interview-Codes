<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Amazon (Hard Level) hashtag#SQL Interview Question — Solution

Find the best selling item for each month (no need to separate months by year) where the biggest total invoice was paid. The best selling item is calculated using the formula (unitprice * quantity). Output the month, the description of the item along with the amount paid.

🌀By solving this, you'll learn how to use windows function, subquery, join, group by. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE online_retails (country VARCHAR(10),customerid FLOAT,description VARCHAR(10),invoicedate DATETIME,invoiceno VARCHAR(10),quantity BIGINT,stockcode VARCHAR(10),unitprice FLOAT);

INSERT INTO online_retails (country, customerid, description, invoicedate, invoiceno, quantity, stockcode, unitprice) VALUES ('USA', 12345, 'Product A', '2025-01-01 12:00:00', 'INV001', 5, 'A123', 10.50), ('UK', 67890, 'Product B', '2025-01-02 14:30:00', 'INV002', 2, 'B456', 20.75), ('Canada', 11223, 'Product C', '2025-01-03 16:45:00', 'INV003', 10, 'C789', 15.00);
---------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. Subquery 1 (max_invoice): Groups the data by month and invoice number to calculate the total invoice amount. Uses MAX(SUM(...)) OVER (PARTITION BY MONTH(...)) to find the maximum total invoice amount for each month.

2. Main Query: Joins the original online_retail table with the subquery (max_invoice) to filter items from invoices with the maximum total invoice amount for each month. Calculates the amount paid for each item (unitprice * quantity) and selects the maximum for each month and item description.

3. Filtering and Grouping: Filters only items that belong to the invoice with the maximum total for each month. Groups by month and description to find the best-selling item.

**SOLUTION**
```sql
WITH MonthlyItemSales AS (
    SELECT 
        EXTRACT(MONTH FROM invoicedate) AS month,
        description,
        SUM(quantity * unitprice) AS total_amount
    FROM meta.online_retails
    GROUP BY month, description
),
BestSellingItems AS (
    SELECT 
        month,
        description,
        total_amount,
        DENSE_RANK() OVER (
            PARTITION BY month 
            ORDER BY total_amount DESC
        ) AS sales_rank
    FROM MonthlyItemSales
)
SELECT 
    month,
    description,
    total_amount
FROM BestSellingItems
WHERE sales_rank <= 3
ORDER BY month;
```

<img width="672" height="180" alt="image" src="https://github.com/user-attachments/assets/b797307a-cac0-464f-9540-60bf0d8a6817" />


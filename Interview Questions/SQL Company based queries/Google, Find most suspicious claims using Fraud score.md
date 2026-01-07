<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Google (Hard Level) hashtag#SQL Interview Question — Solution

We want to identify the most suspicious claims in each state. We'll consider the top 5 percentile of claims with the highest fraud scores in each state as potentially fraudulent.

Your output should include the policy number, state, claim cost, and fraud score.

🌀 Trust me, this one will surely challenge you...! You'll learn Mutiple Ctes, Joins. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE claims (policy_number VARCHAR(50), state VARCHAR(50), claim_cost FLOAT, fraud_score FLOAT);

INSERT INTO claims (policy_number, state, claim_cost, fraud_score) VALUES ('POL123', 'CA', 10000.00, 85.5), ('POL124', 'CA', 5000.00, 70.2), ('POL125', 'CA', 20000.00, 92.8), ('POL126', 'NY', 15000.00, 88.1), ('POL127', 'NY', 8000.00, 65.4), ('POL128', 'NY', 25000.00, 93.7), ('POL129', 'TX', 12000.00, 75.3), ('POL130', 'TX', 18000.00, 95.2), ('POL131', 'TX', 9000.00, 60.0), ('POL132', 'FL', 11000.00, 82.0), ('POL133', 'FL', 14000.00, 87.5), ('POL134', 'FL', 30000.00, 99.0);
---------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. FraudScorePercentiles: This CTE calculates the 95th percentile (PERCENTILE_CONT(0.95)) of fraud scores for each state using the OVER (PARTITION BY state) clause.

2. PotentialFraudulentClaims: This CTE filters claims where the fraud_score is greater than or equal to the calculated 95th percentile in each state.

3. Final Output: The final query outputs the policy_number, state, claim_cost, and fraud_score of the filtered claims, sorted by state and fraud score in descending order.

**SOLUTION**

<img width="800" height="715" alt="image" src="https://github.com/user-attachments/assets/b3fbf145-e1cf-4eb7-91fe-f33fe2d8b615" />

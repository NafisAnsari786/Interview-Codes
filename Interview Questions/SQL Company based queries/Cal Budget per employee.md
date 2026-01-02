<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Microsoft(Medium Level) hashtag#SQL Interview Question — Solution

Given a list of projects and employees mapped to each project, calculate by the amount of project budget allocated to each employee. The output should include the project title and the project budget rounded to the closest integer. Order your list by projects with the highest budget per employee first.

⛳It's straightforward only but bit twisted, read the question carefully and give it a try! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭:
CREATE TABLE ms_projects(id int, title varchar(15), budget int);
INSERT INTO ms_projects VALUES (1, 'Project1',  29498),(2, 'Project2',  32487),(3, 'Project3',  43909),(4, 'Project4',  15776),(5, 'Project5',  36268),(6, 'Project6',  41611),(7, 'Project7',  34003),(8, 'Project8',  49284),(9, 'Project9',  32341),(10, 'Project10',    47587),(11, 'Project11',    11705),(12, 'Project12',    10468),(13, 'Project13',    43238),(14, 'Project14',    30014),(15, 'Project15',    48116),(16, 'Project16',    19922),(17, 'Project17',    19061),(18, 'Project18',    10302),(19, 'Project19',    44986),(20, 'Project20',    19497);

CREATE TABLE ms_emp_projects(emp_id int, project_id int);
INSERT INTO ms_emp_projects VALUES (10592,  1),(10593,  2),(10594,  3),(10595,  4),(10596,  5),(10597,  6),(10598,  7),(10599,  8),(10600,  9),(10601,  10),(10602, 11),(10603, 12),(10604, 13),(10605, 14),(10606, 15),(10607, 16),(10608, 17),(10609, 18),(10610, 19),(10611, 20);
--------------

I have provided an explanation and query, but I encourage you to try solving it first. Later, you can check the query for reference.

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐨𝐟 𝐭𝐡𝐞 𝐐𝐮𝐞𝐫𝐲:
1. Joining Tables: The initial step involves joining the ms_projects and ms_emp_projects tables on the project ID to combine project details (including titles and budgets) with employee assignments.

2. Grouping and Aggregating: The data is then grouped by project title and budget, allowing for the calculation of budget per employee by dividing the total budget of each project by the count of employees assigned to that project.

3. Rounding and Ordering: Finally, the computed budget per employee is rounded to the nearest integer, and the results are ordered in descending order to prioritize projects with the highest budget allocation per employee.

**SOLUTION**

<img width="800" height="640" alt="image" src="https://github.com/user-attachments/assets/ad1895ad-7d8a-4ad5-87f9-b6313824a812" />

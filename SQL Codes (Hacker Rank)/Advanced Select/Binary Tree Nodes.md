<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70"> 

### **You are given a table, BST, containing two columns: N and P, where N represents the value of a node in Binary Tree, and P is the parent of N.**

![image](https://github.com/user-attachments/assets/40afd3d5-fa72-471a-880b-c38b2e3e4849)

**Write a query to find the node type of Binary Tree ordered by the value of the node. Output one of the following for each node:**

- Root: If node is root node.
- Leaf: If node is leaf node.
- Inner: If node is neither root nor leaf node.

Sample Input  

![image](https://github.com/user-attachments/assets/e221eaa6-7816-4bcb-9c11-d1b1383781f1)
 
Sample Output

1 Leaf
2 Inner
3 Leaf
5 Root
6 Leaf
8 Inner
9 Leaf

![image](https://github.com/user-attachments/assets/2cfa2507-f581-466a-bd76-92b4fab3f5b8)

**Solution**

```sql
SELECT N,(
    CASE
    WHEN P IS NULL THEN 'Root'
    WHEN N NOT IN(SELECT P FROM BST WHERE P IS NOT NULL)THEN 'Leaf'
    ELSE 'Inner'
END
) AS NodeType
FROM BST
ORDER BY N;
```

<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

### **You are given a table, BST, containing two columns: N and P, where N represents the value of a node in Binary Tree, and P is the parent of N.**

![image.png](attachment:image.png)

**Write a query to find the node type of Binary Tree ordered by the value of the node. Output one of the following for each node:**

- Root: If node is root node.
- Leaf: If node is leaf node.
- Inner: If node is neither root nor leaf node.

Sample Input 

![image-2.png](attachment:image-2.png)
 
Sample Output

1 Leaf
2 Inner
3 Leaf
5 Root
6 Leaf
8 Inner
9 Leaf

![image-3.png](attachment:image-3.png)

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

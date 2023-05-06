# EDA

SQL LEETCODE


SELECT NULLIF ((SELECT DISTINCT salary FROM (SELECT salary, DENSE_RANK() over(ORDER BY salary DESC) AS rownum  FROM employee) temp WHERE temp.rownum=2) , NULL) AS SecondHighestSalary ;

# EDA

SQL LEETCODE


SELECT IFNULL ((Select distinct salary FROM (SELECT salary, DENSE_RANK()
over(ORDER BY salary desc) as rownum  FROM employee) temp WHERE temp.rownum=2) , NULL) as SecondHighestSalary ;

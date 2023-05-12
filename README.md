# EDA

Regression
reg.score(X_train,y_train)

reg.score(X_test,y_test)

Classification
accuracy_score(y_test, y_pred)

SQL LEETCODE


SELECT NULLIF ((SELECT DISTINCT salary FROM (SELECT salary, DENSE_RANK() over(ORDER BY salary DESC) AS rownum  FROM employee) temp WHERE temp.rownum=2) , NULL) AS SecondHighestSalary ;
==============================================================================================================================================================
Leetcode(self join) --> https://leetcode.com/problems/consecutive-numbers/submissions/945331062/
Note- if with join you don't do l1.num means does not specify to which column l1 refers to then it will throw ambiguous column error.

select distinct l1.num as ConsecutiveNums from Logs l1 
JOIN Logs l2 ON l2.id=(l1.id)+1 and l2.num=l1.num
JOIN Logs l3 ON l3.id=(l1.id)+2 and l3.num=l1.num;
==============================================================================================================================================================

Customers who never order
Note- is null is important don't write equals to with null-->

select Customers.name as Customers FROM Customers 
LEFT JOIN Orders ON Customers.id=Orders.customerId WHERE Orders.customerId is NULL;
==============================================================================================================================================================

https://leetcode.com/problems/department-highest-salary/submissions/

select "Department" ,  "Employee", "salary" FROM (select Department.name as "Department" , Employee.name as "Employee", Employee.salary as "salary" , DENSE_RANK() over(partition by Department.name ORDER BY Employee.salary desc) as rownum FROM Employee JOIN Department on Employee.departmentId=Department.id ) temptable WHERE temptable.rownum=1;


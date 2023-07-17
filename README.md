# EDA

Regression
training_accuracy = reg.score(X_train,y_train)

testing_accuracy = reg.score(X_test,y_test)
or testing accuracy can be calculated using

y_pred = reg.predict(X_test) ,
accuracy_score(y_test,X_test)

difference between score and accuracy score

accuracy_score() function: This function is part of the metrics module in scikit-learn and is used to calculate the accuracy of the model's predictions given the true labels. It can be used when you want to manually compare the predicted labels with the true labels for any set of data, not just the test set. It is a general-purpose function that can be used with any predicted labels and true labels, regardless of the model used.

score() method: The score() method is specific to scikit-learn models and is usually used for evaluating the model's performance on the test set. It internally makes predictions on the input data and compares them with the true labels, returning the accuracy. It is a more concise way to obtain the accuracy for the test set specifically, without manually comparing labels.
Classification
accuracy_score(y_test, y_pred)


To control overfitting decision tree-: control max_depth and min_samples_split , max depth should be low and minimum sample to be at leaf note (min_sample_split) should be high.

SQL LEETCODE



- SELECT NULLIF ((SELECT DISTINCT salary FROM (SELECT salary, DENSE_RANK() over(ORDER BY salary DESC) AS rownum  FROM employee) temp WHERE temp.rownum=2) , NULL) AS SecondHighestSalary ;
  
==============================================================================================================================================================
Leetcode(self join) --> https://leetcode.com/problems/consecutive-numbers/submissions/945331062/
Note- if with join you don't do l1.num means does not specify to which column l1 refers to then it will throw ambiguous column error.

- select distinct l1.num as ConsecutiveNums from Logs l1 
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


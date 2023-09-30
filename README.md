# Ex. No: 5 Creating Triggers using PL/SQL

### AIM: To create a Trigger using PL/SQL.

### Steps:
1. Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);
2. Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);
3. Create a trigger named as log_salary-update.
4. Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.
5. End the trigger.
6. Update the salary of an employee in employee table.
7. Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.
8. Display the employee table, salary_log table.

### Program:
### Create employee table
```
create employee1(empid int,empname varchar(10),dept varchar(10),salary int);
```

### Create salary_log table
```
CREATE TABLE salary_log1 (log_id INT AUTO_INCREMENT PRIMARY KEY,empid INT,empname VARCHAR(10),old_salary DECIMAL(10, 2),new_salary DECIMAL(10, 2),update_date DATE);
```
### PLSQL Trigger code
```
DELIMITER //

CREATE TRIGGER log_salary_update AFTER UPDATE ON employee FOR EACH ROW
BEGIN
  INSERT INTO salary_log (empid, empname, old_salary, new_salary, update_date)
  VALUES (OLD.empid, OLD.empname, OLD.salary, NEW.salary, NOW());
END;
//
DELIMITER ;
```
### Output:
![Screenshot 2023-09-30 211131](https://github.com/Saravana-kumar369/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/117925254/2bd81132-ecdc-42f7-ac09-a5277ac626bd)

![Screenshot 2023-09-30 214825](https://github.com/Saravana-kumar369/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/117925254/06d48a6f-4a60-4ae9-8e9a-3cc431728027)
### Result:
Thus Trigger using PL/SQL created successfully.

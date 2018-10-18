# Oracle
###
## 代码1
```
SELECT d.department_name，count(e.job_id)as "部门总人数"，
avg(e.salary)as "平均工资"
from hr.departments d，hr.employees e
where d.department_id = e.department_id
and d.department_name in ('IT'，'Sales')
GROUP BY department_name;
```
## 运行结果
![sql1](https://github.com/mzy1997/Oracle/blob/master/sql1.png)

## 代码2
```
SELECT d.department_name，count(e.job_id)as "部门总人数"，
avg(e.salary)as "平均工资"
FROM hr.departments d，hr.employees e
WHERE d.department_id = e.department_id
GROUP BY department_name
HAVING d.department_name in ('IT'，'Sales');
```
## 运行结果
![sql2](https://github.com/mzy1997/Oracle/blob/master/sql2.png)

## 最优判定

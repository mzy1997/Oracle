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
### 结果1
![result1](https://github.com/mzy1997/Oracle/blob/master/result1.png)
### 结果2
![result2](https://github.com/mzy1997/Oracle/blob/master/result2.png)
###
## 结论
如图所示，两条sql语句的查询时间分别为0.032秒和0.036秒,因此第一条sql语句所耗费的时间较短，效率较高
## 优化建议
可以为sql语句加上索引，增加数据检索速度
## 自己设计的sql语句
```
SELECT department_name, count(job_id) as "部门总人数", 
avg(salary) as "平均工资"
FROM hr.employees e
JOIN
(SELECT d.department_id, d.department_name
FROM hr.departments d
WHERE d.department_name in ('IT', 'Sales'))
USING (department_id)
GROUP BY department_name;
```

# Sql_top_50
Sql top 50 questions simple answers

Select

1.select product_id from Products where low_fats="Y" and recyclable="Y";
2.select name from Customer where referee_id!=2 or referee_id is Null;
3.select name, population, area from world where (area >= 3000000 or population >= 25000000);
4.select  distinct author_id as id from Views where viewer_id=author_id order by author_id asc;
5.select tweet_id from tweets t where length(t.content)>15;

Basic Joins

1.select EmployeeUNI.unique_id as unique_id , Employees.name as name from Employees left join EmployeeUNI on Employees.id=EmployeeUNI.id;
2.SELECT DISTINCT 
    P.product_name, S.year, S.price 
FROM 
    (SELECT DISTINCT product_id, year, price FROM Sales) S
INNER JOIN
    Product AS P
USING (product_id);
3.select customer_id,count(*) as count_no_trans from visits where visit_id not in (select visit_id from transactions) group by customer_id;
4.SELECT w1.id
FROM Weather w1, Weather w2
WHERE DATEDIFF(w1.recordDate, w2.recordDate) = 1 AND w1.temperature > w2.temperature;
5.select a1.machine_id, round(avg(a2.timestamp-a1.timestamp), 3) as processing_time 
from Activity a1
join Activity a2 
on a1.machine_id=a2.machine_id and a1.process_id=a2.process_id
and a1.activity_type='start' and a2.activity_type='end'
group by a1.machine_id
6.ELECT Employee.name,Bonus.bonus FROM Employee 
LEFT JOIN Bonus ON Employee.empID = Bonus.empID
WHERE bonus < 1000 OR Bonus IS NULL ;
7.SELECT s.student_id, s.student_name, sub.subject_name, COUNT(e.student_id) AS attended_exams
FROM Students s
CROSS JOIN Subjects sub
LEFT JOIN Examinations e ON s.student_id = e.student_id AND sub.subject_name = e.subject_name
GROUP BY s.student_id, s.student_name, sub.subject_name
ORDER BY s.student_id, sub.subject_name;
8.Select m.name
from employee as e
inner join employee as m
on e.managerId=m.id
group by e.managerId 
having count(e.id)>=5
9.select s.user_id, round(avg(if(c.action="confirmed",1,0)),2) as confirmation_rate
from Signups as s left join Confirmations as c on s.user_id= c.user_id group by user_id;

Basic Aggregate Functions

1.select * from Cinema where id%2!=0 and description!="boring" order by rating desc;
2.

﻿# data-engineering-prep

First, started with strategization. Here was my plan :

SQL - Coding Questions

SQL - Theoretical Questions

Python Coding Questions

System Design Interview

For Data Engineering Roles, SQL is key. This means that solving advanced SQL questions is a priority. Think concepts like multi-join , window functions, partitions, etc.

Here are some questions which will help you and I have also listed links which are more than enough to prepare for SQL :

Some template questions which are commonly asked :

1. Find employees whose salary is above the average

SELECT *
FROM Employee
WHERE Salary > (SELECT AVG(Salary) FROM Employee);

2. Retrieve the Nth highest salary (e.g., N=3)

SELECT DISTINCT Salary
FROM Employee
ORDER BY Salary DESC
LIMIT 1 OFFSET 2;

3. Identify duplicate entries in a table based on email

SELECT email, COUNT(*)
FROM Employee
GROUP BY email
HAVING COUNT(*) > 1;

4. Find employees who joined in the past 30 days

SELECT *
FROM Employee
WHERE JoinDate >= CURRENT_DATE - INTERVAL '30 days';

5. Identify the department with the highest employee count

SELECT DepartmentId, COUNT(*) AS EmployeeCount
FROM Employee
GROUP BY DepartmentId
ORDER BY EmployeeCount DESC
LIMIT 1;

6. Rank employees by their salary

SELECT EmployeeName, Salary,
RANK() OVER (ORDER BY Salary DESC) AS SalaryRank
FROM Employee;

7. Locate consecutive available seats in a seating chart

SELECT SeatNumber
FROM Seats
WHERE Status = 'available'
ORDER BY SeatNumber;

8. Find days when the temperature increased from the previous day

SELECT Day, Temperature
FROM TemperatureRecords
WHERE Temperature > (SELECT Temperature FROM TemperatureRecords AS T2 WHERE T2.Day = T1.Day - INTERVAL '1 day');

9. Determine the last person who can fit in the elevator within the weight limit

SELECT PersonName
FROM Elevator
WHERE Weight <= (SELECT WeightLimit FROM Elevator WHERE ID = 1)
ORDER BY Weight DESC
LIMIT 1;

10. Retrieve the latest three orders made by each customer

SELECT CustomerID, OrderID
FROM Orders
WHERE (CustomerID, OrderDate) IN (
SELECT CustomerID, OrderID
FROM Orders
ORDER BY OrderDate DESC
LIMIT 3
);

11. Calculate the median salary of employees

SELECT AVG(Salary) AS MedianSalary
FROM (
SELECT Salary
FROM Employee
ORDER BY Salary
LIMIT 2 - (SELECT COUNT(*) FROM Employee) % 2
OFFSET (SELECT (COUNT(*) - 1) / 2 FROM Employee)
) AS Median;

These 11 questions will give you an idea about learning SQL and questions to expect. Now, where do you practice more of these :

When I was practicing SQL, Leetcode had just come out with SQL section and had only 69 questions. However, that list has expanded but now, there are several optimized lists to prepare for SQL . They are shared below :

Leetcode 50

Advanced SQL 50 : Needs premium

Most asked SQL questions : Link

SQL Questions - Theoretical

This is as important a part of interviews as SQL coding questions.

1.) Explain order of execution of SQL.
2.) What is difference between where and having?
3.) What is the use of group by?
4.) Explain all types of joins in SQL?
5.) What are triggers in SQL?
6.) What is stored procedure in SQL
7.) Explain all types of window functions?
(Mainly rank, row_num, dense_rank, lead & lag)
8.) What is difference between Delete and Truncate?
9.) What is difference between DML, DDL and DCL?
10.) What are aggregate function and when do we use them? explain with few example.
11.) Which is faster between CTE and Subquery?
12.) What are constraints and types of Constraints?
13.) Types of Keys?
14.) Different types of Operators ?
15.) Difference between Group By and Where?
16.) What are Views?
17.) What are different types of constraints?
18.) What is difference between varchar and nvarchar?
19.) Similar for char and nchar?
20.) What are index and their types?
21.) What is an index? Explain its different types.
22.) List the different types of relationships in SQL.
23.) Differentiate between UNION and UNION ALL.
24.) How many types of clauses in SQL?
25.) Explain the difference between INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL JOIN.
26.) What are the various types of relationships in SQL?
27.) Difference between Primary Key and Secondary Key?
28.) What is the difference between where and having?
29.) Find the second highest salary of an employee?
30.) Write retention query in SQL?
31.) Write year-on-year growth in SQL?
32.) Write a query for cummulative sum in SQL?
33.) Difference between Function and Store procedure ?
34.) Do we use variable in views?
35.) What are the limitations of views?
36.) What is normalization in SQL?

Python Coding Questions

Here’s the thing. With Data Engineering, the questions are not as advanced as a Software Engineering. The aim is to check if you can code in Python. So, here’s the strategy. Prepare for Blind 75 with a special emphasis on following topics :

Leetcode Blind 75 : Link

Arrays and Hashing

Two Pointers

Stack

Greedy

Intervals

Math and Geometry

Prepare easy, medium and if possible even hard questions for these topics. I made it a point if questions came from here, I knew it. For rest of the topics, I made it a point that I knew basic questions and concepts. Unless, you interview with Meta, Google, the chances of tough questions on topics like Trees, Graphs, etc will be low.

System Design Data Interview Questions

The below resource was one of the best links I found for data system design primers :

Link

It gave me an idea in terms of how to tackle concepts like latency, throughput, horizontal scaling, multi-threading.

Based on that, I then practice the below questions :

Design a Data Pipeline for Real-time Analytics.

Focus: Real-time data ingestion, processing frameworks (Kafka, Spark Streaming), storage solutions, and analytics.

Resource I used to learn : Link

Design an ETL Pipeline for Large-scale Data Migration.

Focus: Batch processing, data extraction, transformation, loading strategies, scheduling (Airflow), and scalability.

Resource I used to learn : Link

Design a Scalable Logging and Monitoring System.

Focus: Data ingestion, log storage (Elasticsearch), data visualization (Grafana), and alerting mechanisms.

Resource I used to learn : Link

Design a Data Lake Architecture for Big Data Storage.

Focus: Storage solutions (AWS S3, Azure Blob Storage), file formats (Parquet, Avro), metadata management, and querying capabilities.

Resource I used : Link

Design a Recommendation System Data Architecture.

Focus: Data ingestion, feature store management, batch vs real-time processing, and model serving.

Design a Data Warehouse for Analytical Queries.

Focus: Data modeling (Star schema, Snowflake schema), performance optimization, storage systems (Snowflake, Redshift, BigQuery), and query optimization.

Design a System for Processing Clickstream Data.

Focus: Real-time ingestion, event-driven architecture (Kafka, Kinesis), data processing (Spark, Flink), and analytical storage.

Design a Data System for Fraud Detection.

Focus: Real-time streaming, data preprocessing, anomaly detection models, low-latency data serving, and scalability.

Design a System for Handling Data Versioning and Schema Evolution.

Focus: Schema management (Schema Registry, Avro schemas), data format compatibility, and data versioning strategies.

Design a Scalable Event-driven Data Processing System.

Focus: Event streaming (Kafka, RabbitMQ), consumer patterns, fault tolerance, scalability, and data durability.

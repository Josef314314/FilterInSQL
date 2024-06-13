<h1>SQL queries - Apply filters</h1>

<h2>Scenario</h2>
This scenario is based on a fictional company: <br/>
<br/>
I am a security professional at a large organization. Part of the job is to investigate security issues to help keep the system secure. <br/>

<h2>Project description</h2>

The job to ensure the system is safe, investigate all potential security issues, and update employee computers as needed. The following steps provide examples of how I used SQL with filters to perform security-related tasks.

<h2>Environment</h2>

- <b>Qwiklabs - MariaDB shell</b>

<h2>Task walk-through</h2>

- <b>Retrieve after hours failed login attempts:</b>

There was a potential security incident that occurred after business hours (after 18:00). All after hours login attempts that failed need to be investigated. <br/>

See the following snap that shows how I created a SQL query to filter for failed login attempts that occurred after business hours:
<p align="center">
<img src="https://i.imgur.com/qChQ3ui.png" height="60%" width="60%" alt="LinuxComm"/> <br/>
<p align="left">

The first part of the screenshot is my query, and the second part is a portion of the output. This query filters for failed login attempts after 18:00. <br/> 
First, I started by selecting all data from the `log_in_attempts` table. Then, I used a `WHERE` clause with an `AND` operator to filter my results to output only login attempts that occurred after 18:00 and were unsuccessful. The first condition is `login_time > '18:00'`, which filters for the login attempts that occurred after 18:00. The second condition is `success = FALSE`, which filters for the failed login attempts.  <br />
 <br />
  
- <b>Retrieve login attempts on specific dates:</b>

A suspicious event occurred on 2022-05-09. Any login activity that happened on that day or on the day before needs to be investigated. <br/>

The following code shows how I created a SQL query to filter for login attempts that occurred on specific dates:<br/>
<p align="center">
<img src="https://i.imgur.com/iKkjbNP.png" height="60%" width="60%" alt="LinuxComm"/> <br/>
<p align="left">
  
As before, the first part of the screenshot is my query, and the second part is a portion of the output. This query returns all login attempts that occurred on 2022-05-09 or 2022-05-08. <br/>
First, I started by selecting all data from the `log_in_attempts` table. Then, I used a `WHERE` clause with an `OR` operator to filter my results to output only login attempts that occurred on either 2022-05-09 or 2022-05-08. The first condition is `login_date = '2022-05-09'`, which filters for logins on 2022-05-09. The second condition is `login_date = '2022-05-08'`, which filters for logins on 2022-05-08. <br />
<br />

- <b>Retrieve login attempts outside of Mexico:</b>

After investigating the organization’s data on login attempts, I believe there is an issue with the login attempts that occurred outside of Mexico. These login attempts should be investigated. <br/>

So, I created the following SQL query to filter for login attempts that occurred outside of Mexico: <br/>
<p align="center">
<img src="https://i.imgur.com/ZkSFwo7.png" height="60%" width="60%" alt="LinuxComm"/> <br/>
<p align="left">
  
This query returns all login attempts that occurred in countries other than Mexico. <br/>
First, I started by selecting all data from the `log_in_attempts` table. Then, I used a `WHERE` clause with `NOT` to filter for countries other than Mexico. I used `LIKE` with `MEX%` as the pattern to match because the dataset represents Mexico as `MEX` and `MEXICO`. The percentage sign `(%)` represents any number of unspecified characters when used with `LIKE`.  <br />
<br />

- <b>Retrieve employees in Marketing:</b>

The team wants to update the computers for certain employees in the Marketing department. To do this, I have to get information on which employee machines to update. <br/>

I used the following SQL query to filter for employee machines from employees in the Marketing department in the East building: <br/>
<p align="center">
<img src="https://i.imgur.com/I2BI1BL.png" height="60%" width="60%" alt="LinuxComm"/> <br />
<p align="left">
  
This query returns all employees in the Marketing department in the East building. <br/>
First, I started by selecting all data from the `employees` table. Then, I used a `WHERE` clause with `AND` to filter for employees who work in the Marketing department and in the East building. I used `LIKE` with `East%` as the pattern to match because the data in the `office` column represents the East building with the specific office number. The first condition is the `department = 'Marketing'` portion, which filters for employees in the Marketing department. The second condition is the `office LIKE 'East%'` portion, which filters for employees in the East building. <br/>
<br />

- <b>Retrieve employees in Finance or Sales:</b>

The machines for employees in the Finance and Sales departments also need to be updated. Since a different security update is needed, I have to get information on employees only from these two departments. <br/>

The following code demonstrates how I created a SQL query to filter for employee machines from employees in the Finance or Sales departments: <br/>
<p align="center">
<img src="https://i.imgur.com/7dxkvFE.png" height="60%" width="60%" alt="LinuxComm"/> <br />
<p align="left">
  
This query returns all employees in the Finance and Sales departments. <br/>
First, I started by selecting all data from the `employees` table. Then, I used a `WHERE` clause with `OR` to filter for employees who are in the Finance and Sales departments. I used the `OR` operator instead of `AND` because I want all employees who are in either department. The first condition is `department = 'Finance'`, which filters for employees from the Finance department. <br/>
The second condition is `department = 'Sales'`, which filters for employees from the Sales department. <br/>
<br />

- <b>Retrieve all employees not in IT:</b>

I need to make one more security update on employees who are not in the Information Technology department. To make the update, I first have to get information on these employees. <br/>

I used the following SQL query to filter for employee machines from employees not in the  Information Technology department: <br/>
<p align="center">
<img src="https://i.imgur.com/FNKGoGH.png" height="60%" width="60%" alt="LinuxComm"/> <br />
<p align="left">
  
This query returns all employees not in the Information Technology department. <br/>
First, I started by selecting all data from the `employees` table. Then, I used a `WHERE` clause with `NOT` to filter for employees not in this department. <br/>
<br />

<h2>Summary</h2>

I applied filters to SQL queries to get specific information on login attempts and employee machines. I used two different tables, `log_in_attempts` and `employees`. I used the `AND`, `OR`, and `NOT` operators to filter for the specific information needed for each task. I also used `LIKE` and the percentage sign `(%)` wildcard to filter for patterns.  <br/>

</p>

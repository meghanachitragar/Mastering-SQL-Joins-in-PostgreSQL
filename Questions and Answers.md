# Guided Project: Mastering SQL Joins in PostgreSQL
------------------------------------------------------------------------
## Task One: Getting Started
#### In this task, we will retrieve data from the dept_manager_dup and departments_dup tables in the database

#### 1.1: Retrieve all data from the dept_manager_dup table

````sql
SELECT * FROM dept_manager_dup
ORDER BY dept_no;
````

**Results:**

emp_no| dept_no| from_date| to_date|
------|--------|----------|--------|
110085|	"d002"|	"1985-01-01"|	"1989-12-17"|
110114|	"d002"|	"1989-12-17"|	"9999-01-01"|
110183|	"d003"|	"1985-01-01"|	"1992-03-21"|
110228|	"d003"|	"1992-03-21"|	"9999-01-01"|
110303|	"d004"|	"1985-01-01"|	"1988-09-09"|
110344|	"d004"|	"1988-09-09"|	"1992-08-02"|
110386|	"d004"|	"1992-08-02"|	"1996-08-30"|
110420|	"d004"|	"1996-08-30"|	"9999-01-01"|
110511|	"d005"|	"1985-01-01"|	"1992-04-25"|
110567|	"d005"|	"1992-04-25"|	"9999-01-01"|
110725|	"d006"|	"1985-01-01"|	"1989-05-06"|
110765|	"d006"|	"1989-05-06"|	"1991-09-12"|
110800|	"d006"|	"1991-09-12"|	"1994-06-28"|
110854|	"d006"|	"1994-06-28"|	"9999-01-01"|
111035|	"d007"|	"1985-01-01"|	"1991-03-07"|
111133|	"d007"|	"1991-03-07"|	"9999-01-01"|
111400|	"d008"|	"1985-01-01"|	"1991-04-08"|
111534|	"d008"|	"1991-04-08"|	"9999-01-01"|
111692|	"d009"|	"1985-01-01"|	"1988-10-17"|
111784|	"d009"|	"1988-10-17"|	"1992-09-08"|
111877|	"d009"|	"1992-09-08"|	"1996-01-03"|
111939|	"d009"|	"1996-01-03"|	"9999-01-01"|
999904|	      |	"2017-01-01"|	            |
999905|	      |	"2017-01-01"|	            |
999906|	      | "2017-01-01"|	            |
999907|	      |	"2017-01-01"|	            |

#### 1.2: Retrieve all data from the departments_dup table

````sql
SELECT * FROM departments_dup 
ORDER BY dept_no;
````

**Results:**

dept_no|dept_name|
-------|---------|
"d001"|	"Marketing"         |
"d003"|	"Human Resources"   |
"d004"|	"Production"        |
"d005"|	"Development"       |
"d006"|	"Quality Management"|
"d007"|	"Sales"             |
"d008"|	"Research"          |
"d009"|	"Customer Service"  |
"d010"|	                    |
"d011"|	                    |
  --  |	"Public Relations"  | 

---------------------------------------------------------------

## Task Two: INNER JOIN
#### In this task, you will retrieve data from the two tables using INNER JOIN

## INNER JOIN

#### 2.1: Extract all managers' employees number, department number, and department name. Order by the manager's department number

````sql
SELECT m.emp_no,m.dept_no,d.dept_name
FROM dept_manager_dup m
INNER JOIN departments_dup d
ON m.dept_no=d.dept_no
ORDER BY m.dept_no
````

**Results:**

emp_no|dept_no|dept_name|
------|-------|---------|
110183|	"d003"|	"Human Resources"|
110228|	"d003"|	"Human Resources"|
110303|	"d004"|	"Production"|
110344|	"d004"|	"Production"|
110386|	"d004"|	"Production"|
110420|	"d004"|	"Production"|
110511|	"d005"|	"Development"|
110567|	"d005"|	"Development"|
110725|	"d006"|	"Quality Management"|
110765|	"d006"|	"Quality Management"|
110800|	"d006"|	"Quality Management"|
110854|	"d006"|	"Quality Management"|
111035|	"d007"|	"Sales"|
111133|	"d007"|	"Sales"|
111400|	"d008"|	"Research"|
111534|	"d008"|	"Research"|
111692|	"d009"|	"Customer Service"|
111784|	"d009"|	"Customer Service"|
111877|	"d009"|	"Customer Service"|
111939|	"d009"|	"Customer Service"|

#### add m.from_date and m.to_date

````sql
SELECT m.emp_no,m.dept_no,d.dept_name,m.from_date,m.to_date
FROM dept_manager_dup m
INNER JOIN departments_dup d
ON m.dept_no=d.dept_no
ORDER BY m.dept_no
````

**Results:**

emp_no|dept_no|dept_name|from_date|to_date|
------|-------|---------|---------|-------|
110183|	"d003"|	"Human Resources"|	"1985-01-01"|	"1992-03-21"|
110228|	"d003"|	"Human Resources"|	"1992-03-21"|	"9999-01-01"|
110303|	"d004"|	"Production"|	        "1985-01-01"|	"1988-09-09"|
110344|	"d004"|	"Production"|	        "1988-09-09"|	"1992-08-02"|
110386|	"d004"|	"Production"|	        "1992-08-02"|	"1996-08-30"|
110420|	"d004"|	"Production"|	        "1996-08-30"|	"9999-01-01"|
110511|	"d005"|	"Development"|	        "1985-01-01"|	"1992-04-25"|
110567|	"d005"|	"Development"|	        "1992-04-25"|	"9999-01-01"|
110725|	"d006"|	"Quality Management"|	"1985-01-01"|	"1989-05-06"|
110765|	"d006"|	"Quality Management"|	"1989-05-06"|	"1991-09-12"|
110800|	"d006"|	"Quality Management"|	"1991-09-12"|	"1994-06-28"|
110854|	"d006"|	"Quality Management"|	"1994-06-28"|	"9999-01-01"|
111035|	"d007"|	"Sales"|	        "1985-01-01"|	"1991-03-07"|
111133|	"d007"|	"Sales"|               "1991-03-07"|	"9999-01-01"|
111400|	"d008"|	"Research"|	        "1985-01-01"|	"1991-04-08"|
111534|	"d008"|	"Research"|	        "1991-04-08"|	"9999-01-01"|
111692|	"d009"|	"Customer Service"|	"1985-01-01"|	"1988-10-17"|
111784|	"d009"|	"Customer Service"|	"1988-10-17"|	"1992-09-08"|
111877|	"d009"|	"Customer Service"|	"1992-09-08"|	"1996-01-03"|
111939|	"d009"|	"Customer Service"|	"1996-01-03"|	"9999-01-01"|

#### 2.2 (Ex.): Extract a list containing information about all managers' employee number, first and last name, dept_number and hire_date
#### Hint: Use the employees and dept_manager tables

````sql
SELECT e.emp_no,e.first_name,e.last_name,e.hire_date,dm.dept_no
FROM employees e
INNER JOIN dept_manager dm
ON e.emp_no = dm.emp_no;
````

**Results:**

emp_no|first_name|last_name|hire_date|dept_no|
------|----------|---------|---------|-------|
110022|	"Margareta"|	"Markovitch"|	"1985-01-01"|	"d001"|
110039|	"Vishwani"|	"Minakawa"|	"1986-04-12"|	"d001"|
110085|	"Ebru"    | 	"Alpin"	   |     "1985-01-01"|	"d002"|
110114|	"Isamu"	  |      "Legleitner"|	"1985-01-14"|	"d002"|
110183|	"Shirish"|	"Ossenbruggen"|	"1985-01-01"|	"d003"|
110228|	"Karsten"|	"Sigstam"|	"1985-08-04"|	"d003"|
110303|	"Krassimir"|	"Wegerle"|	"1985-01-01"|	"d004"|
110344|	"Rosine"|	"Cools"	 |      "1985-11-22"|	"d004"|
110386|	"Shem"|	        "Kieras"|	"1988-10-14"|	"d004"|
110420|	"Oscar"|  	"Ghazalie"|	"1992-02-05"|	"d004"|
110511|	"DeForest"|	"Hagimont"|	"1985-01-01"|	"d005"|
110567|	"Leon"	 |       "DasSarma"|	"1986-10-21"|	"d005"|
110725|	"Peternela"|	"Onuegbe"|	"1985-01-01"|	"d006"|
110765|	"Rutger"|	"Hofmeyr"|	"1989-01-07"|	"d006"|
110800|	"Sanjoy"|	"Quadeer"|	"1986-08-12"|	"d006"|
110854|	"Dung"	 |       "Pesch"  |  	"1989-06-09"|	"d006"|
111035|	"Przemyslawa"|	"Kaelbling"|	"1985-01-01"|	"d007"|
111133|	"Hauke"  |	"Zhang"	  |      "1986-12-30"|	"d007"|
111400|	"Arie"   |	"Staelin"|	"1985-01-01"|	"d008"|
111534|	"Hilary"|	"Kambil"|	"1988-01-31"|	"d008"|
111692|	"Tonny" |	"Butterworth"|	"1985-01-01"|	"d009"|
111784|	"Marjo" |	"Giarratana"|	"1988-02-12"|	"d009"|
111877|	"Xiaobin"|	"Spinelli"|	"1991-08-17"|	"d009"|
111939|	"Yuchang"|	"Weedman"|	"1989-07-10"|	"d009"|

------------------------------------------------------------------------------

## Task Three: Duplicate Records
#### In this task, you will retrieve data from the two tables with duplicate records using INNER JOIN

## Duplicate Records

#### 3.1: Let us add some duplicate records
#### Insert records into the dept_manager_dup and departments_dup tables respectively

````sql
INSERT INTO dept_manager_dup 
VALUES 	('110228', 'd003', '1992-03-21', '9999-01-01');
        
INSERT INTO departments_dup 
VALUES	('d009', 'Customer Service');
````
#### 3.2: Select all records from the dept_manager_dup table

````sql
SELECT *
FROM dept_manager_dup
ORDER BY dept_no ASC;
````

**Results:**

emp_no|dept_no|from_date|to_date|
------|-------|---------|-------|
110114|	"d002"|	"1989-12-17"|	"9999-01-01"|
110085|	"d002"|	"1985-01-01"|	"1989-12-17"|
110228|	"d003"|	"1992-03-21"|	"9999-01-01"|
110228|	"d003"|	"1992-03-21"|	"9999-01-01"|
110183|	"d003"|	"1985-01-01"|	"1992-03-21"|
110386|	"d004"|	"1992-08-02"|	"1996-08-30"|
110420|	"d004"|	"1996-08-30"|	"9999-01-01"|
110303|	"d004"|	"1985-01-01"|	"1988-09-09"|
110567|	"d005"|	"1992-04-25"|	"9999-01-01"|
110511|	"d005"|	"1985-01-01"|	"1992-04-25"|
110765|	"d006"|	"1989-05-06"|	"1991-09-12"|
110800|	"d006"|	"1991-09-12"|	"1994-06-28"|
110854|	"d006"|	"1994-06-28"|	"9999-01-01"|
110725|	"d006"|	"1985-01-01"|	"1989-05-06"|
111133|	"d007"|	"1991-03-07"|	"9999-01-01"|
111035|	"d007"|	"1985-01-01"|	"1991-03-07"|
111534|	"d008"|	"1991-04-08"|	"9999-01-01"|
111400|	"d008"|	"1985-01-01"|	"1991-04-08"|
111784|	"d009"|	"1988-10-17"|	"1992-09-08"|
111877|	"d009"|	"1992-09-08"|	"1996-01-03"|
111939|	"d009"|	"1996-01-03"|	"9999-01-01"|
111692|	"d009"|	"1985-01-01"|	"1988-10-17"|
999905|	      |	"2017-01-01"|	            |
999906|	      |	"2017-01-01"|	            |
999907|	      |	"2017-01-01"|	            |
999904|	      |	"2017-01-01"|           |

#### 3.3: Select all records from the departments_dup table

````sql
SELECT *
FROM departments_dup
ORDER BY dept_no ASC;
````

**Results:**

dept_no|dept_name|
-------|---------|
"d001"|	"Marketing"|
"d003"|	"Human Resources"|
"d004"|	"Production"|
"d005"|	"Development"|
"d006"|	"Quality Management"|
"d007"|	"Sales"|
"d008"|	"Research"|
"d009"|	"Customer Service"|
"d009"|	"Customer Service"|
"d010"|          	|
"d011"|	                |
  --  |	"Public Relations"|

#### 3.4: Perform INNER JOIN as before

````sql
SELECT m.emp_no,m.dept_no,d.dept_name
FROM dept_manager_dup m
INNER JOIN departments_dup d
ON m.dept_no = d.dept_no
ORDER BY m.dept_no;
````

**Results:**

emp_no|dept_no|dept_name|
------|-------|---------|
110228|	"d003"|	"Human Resources"|
110228|	"d003"|	"Human Resources"|
110183|	"d003"|	"Human Resources"|
110344|	"d004"|	"Production"|
110386|	"d004"|	"Production"|
110420|	"d004"|	"Production"|
110303|	"d004"|	"Production"|
110567|	"d005"|	"Development"|
110511|	"d005"|	"Development"|
110765|	"d006"|	"Quality Management"|
110800|	"d006"|	"Quality Management"|
110854|	"d006"|	"Quality Management"|
110725|	"d006"|	"Quality Management"|
111133|	"d007"|	"Sales"|
111035|	"d007"|	"Sales"|
111534|	"d008"|	"Research"|
111400|	"d008"|	"Research"|
111784|	"d009"|	"Customer Service"|
111877|	"d009"|	"Customer Service"|
111939|	"d009"|	"Customer Service"|
111692|	"d009"|	"Customer Service"|
111784|	"d009"|	"Customer Service"|
111877|	"d009"|	"Customer Service"|
111939|	"d009"|	"Customer Service"|
111692|	"d009"|	"Customer Service"|

#### 3.5: add a GROUP BY clause. Make sure to include all the fields in the GROUP BY clause

````sql
SELECT m.emp_no,m.dept_no,d.dept_name
FROM dept_manager_dup m
INNER JOIN departments_dup d
ON m.dept_no = d.dept_no
GROUP BY m.emp_no,m.dept_no,d.dept_name
ORDER BY m.dept_no;
````

**Results:**

emp_no|dept_no|dept_name|
------|-------|---------|
110183|	"d003"|	"Human Resources"|
110228|	"d003"|	"Human Resources"|
110303|	"d004"|	"Production"|
110344|	"d004"|	"Production"|
110386|	"d004"|	"Production"|
110420|	"d004"|	"Production"|
110511|	"d005"|	"Development"|
110567|	"d005"|	"Development"|
110725|	"d006"|	"Quality Management"|
110765|	"d006"|	"Quality Management"|
110800|	"d006"|	"Quality Management"|
110854|	"d006"|	"Quality Management"|
111035|	"d007"|	"Sales"|
111133|	"d007"|	"Sales"|
111400|	"d008"|	"Research"|
111534|	"d008"|	"Research"|
111692|	"d009"|	"Customer Service"|
111784|	"d009"|	"Customer Service"|
111877|	"d009"|	"Customer Service"|
111939|	"d009"|	"Customer Service"|

------------------------------------------------------------------------------

## Task Four: LEFT JOIN
#### In this task, you will retrieve data from the two tables using LEFT JOIN

## LEFT JOIN

#### 4.1: Remove the duplicates from the two tables

````sql
DELETE FROM dept_manager_dup 
WHERE emp_no = '110228';
        
DELETE FROM departments_dup 
WHERE dept_no = 'd009';
````

#### 4.2: Add back the initial records

````sql
INSERT INTO dept_manager_dup 
VALUES 	('110228', 'd003', '1992-03-21', '9999-01-01');
        
INSERT INTO departments_dup 
VALUES	('d009', 'Customer Service');
````

#### 4.3: Select all records from dept_manager_dup

````sql
SELECT *
FROM dept_manager_dup
ORDER BY dept_no;
````

**Results:**

emp_no|dept_no|from_date|to_date|
------|-------|---------|-------|
110114|	"d002"|	"1989-12-17"|	"9999-01-01"|
110085|	"d002"|	"1985-01-01"|	"1989-12-17"|
110228|	"d003"|	"1992-03-21"|	"9999-01-01"|
110344|	"d004"|	"1988-09-09"|	"1992-08-02"|
110386|	"d004"|	"1992-08-02"|	"1996-08-30"|
110420|	"d004"|	"1996-08-30"|	"9999-01-01"|
110303|	"d004"|	"1985-01-01"|	"1988-09-09"|
110567|	"d005"|	"1992-04-25"|	"9999-01-01"|
110511|	"d005"|	"1985-01-01"|	"1992-04-25"|
110765|	"d006"|	"1989-05-06"|	"1991-09-12"|
110800|	"d006"|	"1991-09-12"|	"1994-06-28"|
110854|	"d006"|	"1994-06-28"|	"9999-01-01"|
110725|	"d006"|	"1985-01-01"|	"1989-05-06"|
111133|	"d007"|	"1991-03-07"|	"9999-01-01"|
111035|	"d007"|	"1985-01-01"|	"1991-03-07"|
111534|	"d008"|	"1991-04-08"|	"9999-01-01"|
111400|	"d008"|	"1985-01-01"|	"1991-04-08"|
111784|	"d009"|	"1988-10-17"|	"1992-09-08"|
111877|	"d009"|	"1992-09-08"|	"1996-01-03"|
111939|	"d009"|	"1996-01-03"|	"9999-01-01"|
111692|	"d009"|	"1985-01-01"|	"1988-10-17"|
999905|	      |	"2017-01-01"|	            |
999906|	      |	"2017-01-01"|	            |
999907|	      |	"2017-01-01"|	            |
999904|	      |	"2017-01-01"|	            |

#### 4.4: Select all records from departments_dup

````sql
SELECT *
FROM departments_dup
ORDER BY dept_no;
````

**Results:**

dept_no|dept_name|
-------|---------|
"d001"|	"Marketing"|
"d003"|	"Human Resources"|
"d004"|	"Production"|
"d005"|	"Development"|
"d006"|	"Quality Management"|
"d007"|	"Sales"|
"d008"|	"Research"|
"d009"|	"Customer Service"|
"d010"|	                |
"d011"|          |
  --  |	"Public Relations"|

#### Recall, when we had INNER JOIN

````sql
SELECT m.dept_no, m.emp_no, d.dept_name
FROM dept_manager_dup m
JOIN departments_dup d 
ON m.dept_no = d.dept_no
ORDER BY m.dept_no;
````

**Results:**

dept_no|emp_no|dept_name|
-------|------|---------|
"d003"|	110228|	"Human Resources"|
"d003"|	110183|	"Human Resources"|
"d004"|	110344|	"Production"|
"d004"|	110386|	"Production"|
"d004"|	110420|	"Production"|
"d004"|	110303|	"Production"|
"d005"|	110567|	"Development"|
"d005"|	110511|	"Development"|
"d006"|	110765|	"Quality Management"|
"d006"|	110800|	"Quality Management"|
"d006"|	110854|	"Quality Management"|
"d006"|	110725|	"Quality Management"|
"d007"|	111133|	"Sales"|
"d007"|	111035|	"Sales"|
"d008"|	111534|	"Research"|
"d008"|	111400|	"Research"|
"d009"|	111784|	"Customer Service"|
"d009"|	111877|	"Customer Service"|
"d009"|	111939|	"Customer Service"|
"d009"|	111692|	"Customer Service"|

#### 4.5: Join the dept_manager_dup and departments_dup tables
#### Extract a subset of all managers' employee number, department number, and department name. Order by the managers' department number

````sql
SELECT m.dept_no,m.emp_no,d.dept_name
FROM dept_manager_dup m
LEFT JOIN departments_dup d
ON m.dept_no = d.dept_no
ORDER BY m.dept_no;
````

**Results:**

dept_no|emp_no|dept_name|
-------|------|---------|
"d002"|	110114|	        |
"d002"|	110085|	        |
"d003"|	110228|	"Human Resources"|
"d003"|	110183|	"Human Resources"|
"d004"|	110344|	"Production"|
"d004"|	110386|	"Production"|
"d004"|	110420|	"Production"|
"d004"|	110303|	"Production"|
"d005"|	110511|	"Development"|
"d006"|	110765|	"Quality Management"|
"d006"|	110800|	"Quality Management"|
"d006"|	110854|	"Quality Management"|
"d006"|	110725|	"Quality Management"|
"d007"|	111133|	"Sales"|
"d007"|	111035|	"Sales"|
"d008"|	111534|	"Research"|
"d008"|	111400|	"Research"|
"d009"|	111784|	"Customer Service"|
"d009"|	111877|	"Customer Service"|
"d009"|	111939|	"Customer Service"|
"d009"|	111692|	"Customer Service"|
  --  |	999905|	                 |
  --  |	999906|	         |
  --  |	999907|	         |
  --  |	999904|	         |

#### 4.6: What will happen when we d LEFT JOIN m?

````sql
SELECT m.dept_no,m.emp_no,d.dept_name
FROM departments_dup d
LEFT JOIN dept_manager_dup m
ON d.dept_no = m.dept_no
ORDER BY m.dept_no;
````

**Results:**

dept_no|emp_no|dept_name|
-------|------|---------|
"d003"|	110228|	"Human Resources"|
"d003"|	110183|	"Human Resources"|
"d004"|	110386|	"Production"|
"d004"|	110420|	"Production"|
"d004"|	110303|	"Production"|
"d004"|	110344|	"Production"|
"d005"|	110567|	"Development"|
"d005"|	110511|	"Development"|
"d006"|	110725|	"Quality Management"|
"d006"|	110765|	"Quality Management"|
"d006"|	110800|	"Quality Management"|
"d006"|	110854|	"Quality Management"|
"d007"|	111133|	"Sales"|
"d007"|	111035|	"Sales"|
"d008"|	111534|	"Research"|
"d008"|	111400|	"Research"|
"d009"|	111784|	"Customer Service"|
"d009"|	111877|	"Customer Service"|
"d009"|	111939|	"Customer Service"|
"d009"|	111692|	"Customer Service"|
  --  |     |   "Public Relations"|
  --  |	   |	"Marketing"|

#### 4.7: Let's select d.dept_no

````sql
SELECT m.dept_no,m.emp_no,d.dept_name
FROM departments_dup d
LEFT JOIN dept_manager_dup m
ON d.dept_no = m.dept_no
ORDER BY d.dept_no;
````

**Results:**

dept_no|emp_no|dept_name   |
-------|------|------------|
  --   |      |	"Marketing"|
"d003" |110228|	"Human Resources"|
"d003" |110183|	"Human Resources"|
"d004" |110344|	"Production"|
"d004" |110386|	"Production"|
"d004" |110420|	"Production"|
"d004" |110303|	"Production"|
"d005" |110567|	"Development"|
"d005" |110511|	"Development"|
"d006" |110765|	"Quality Management"|
"d006" |110800|	"Quality Management"|
"d006" |110854|	"Quality Management"|
"d006" |110725|	"Quality Management"|
"d007" |111133|	"Sales"|
"d007" |111035|	"Sales"|
"d008" |111534|	"Research"|
"d008" |111400|	"Research"|
"d009" |111784|	"Customer Service"|
"d009" |111877|	"Customer Service"|
"d009" |111939|	"Customer Service"|
"d009" |111692|	"Customer Service"|
  --   |      |	                  |
  --   |      |	                  |
  --   |      |	"Public Relations"|

#### LEFT OUTER JOIN

````sql
SELECT m.dept_no,m.emp_no,d.dept_name
FROM departments_dup d
LEFT OUTER JOIN dept_manager_dup m
ON d.dept_no = m.dept_no
ORDER BY d.dept_no;		
````

**Results:**

dept_no|emp_no|dept_name|
-------|------|---------|
  --  |      |	"Marketing"|
"d003"|	110228|	"Human Resources"|
"d003"|	110183|	"Human Resources"|
"d004"|	110344|	"Production"|
"d004"|	110386|	"Production"|
"d004"|	110420|	"Production"|
"d004"|	110303|	"Production"|
"d005"|	110567|	"Development"|
"d005"|	110511|	"Development"|
"d006"|	110765|	"Quality Management"|
"d006"|	110800|	"Quality Management"|
"d006"|	110854|	"Quality Management"|
"d006"|	110725|	"Quality Management"|
"d007"|	111133|	"Sales"|
"d007"|	111035|	"Sales"|
"d008"|	111534|	"Research"|
"d008"|	111400|	"Research"|
"d009"|	111784|	"Customer Service"|
"d009"|	111877|	"Customer Service"|
"d009"|	111939|	"Customer Service"|
"d009"|	111692|	"Customer Service"|
  --  |	     |	                  |
  --  |	     |	                  |
  --  |	     |	"Public Relations"|

----------------------------------------------------------------------------------------

## Task Five: RIGHT JOIN
#### In this task, you will retrieve data from the two tables using RIGHT JOIN

## RIGHT JOIN

#### 5.1: Let's use RIGHT JOIN

````sql
SELECT m.dept_no, m.emp_no, d.dept_name
FROM dept_manager_dup m
RIGHT OUTER JOIN departments_dup d 
ON m.dept_no = d.dept_no
ORDER BY dept_no;
````

**Results:**

dept_no|emp_no|dept_name|
-------|------|---------|
"d003"|	110228|	"Human Resources"|
"d003"|	110183|	"Human Resources"|
"d004"|	110386|	"Production"|
"d004"|	110420|	"Production"|
"d004"|	110303|	"Production"|
"d004"|	110344|	"Production"|
"d005"|	110567|	"Development"|
"d005"|	110511|	"Development"|
"d006"|	110725|	"Quality Management"|
"d006"|	110765|	"Quality Management"|
"d006"|	110800|	"Quality Management"|
"d006"|	110854|	"Quality Management"|
"d007"|	111133|	"Sales"|
"d007"|	111035|	"Sales"|
"d008"|	111534|	"Research"|
"d008"|	111400|	"Research"|
"d009"|	111784|	"Customer Service"|
"d009"|	111877|	"Customer Service"|
"d009"|	111939|	"Customer Service"|
"d009"|	111692|	"Customer Service"|
  --  |	    |	"Public Relations"|
  --  |	    |	"Marketing"|

#### 5.2: SELECT d.dept_no

````sql
SELECT m.dept_no, m.emp_no, d.dept_name
FROM dept_manager_dup m
RIGHT OUTER JOIN departments_dup d 
ON m.dept_no = d.dept_no
ORDER BY d.dept_no;
````

**Results:**

dept_no|emp_no|dept_name|
-------|------|---------|
  --  |      |	"Marketing"|
"d003"|	110228|	"Human Resources"|
"d003"|	110183|	"Human Resources"|
"d004"|	110344|	"Production"|
"d004"|	110386|	"Production"|
"d004"|	110420|	"Production"|
"d004"|	110303|	"Production"|
"d005"|	110567|	"Development"|
"d005"|	110511|	"Development"|
"d006"|	110765|	"Quality Management"|
"d006"|	110800|	"Quality Management"|
"d006"|	110854|	"Quality Management"|
"d006"|	110725|	"Quality Management"|
"d007"|	111133|	"Sales"|
"d007"|	111035|	"Sales"|
"d008"|	111534|	"Research"|
"d008"|	111400|	"Research"|
"d009"|	111784|	"Customer Service"|
"d009"|	111877|	"Customer Service"|
"d009"|	111939|	"Customer Service"|
"d009"|	111692|	"Customer Service"|
  --  |	     |	                  |
  --  |       |	                  |
  --  |	     |	"Public Relations"|

#### 5.3: d LEFT JOIN m

````sql
SELECT m.dept_no, m.emp_no, d.dept_name
FROM departments_dup d
LEFT JOIN dept_manager_dup m
ON m.dept_no = d.dept_no
ORDER BY dept_no;
````

**Results:**

dept_no|emp_no|           dept_name|
-------|------|------------------|
"d003"|	110228|	"Human Resources"|
"d003"|	110183|	"Human Resources"|
"d004"|	110386|	"Production"|
"d004"|	110420|	"Production"|
"d004"|	110303|	"Production"|
"d004"|	110344|	"Production"|
"d005"|	110567|	"Development"|
"d005"|	110511|	"Development"|
"d006"|	110725|	"Quality Management"|
"d006"|	110765|	"Quality Management"|
"d006"|	110800|	"Quality Management"|
"d006"|	110854|	"Quality Management"|
"d007"|	111133|	"Sales"|
"d007"|	111035|	"Sales"|
"d008"|	111534|	"Research"|
"d008"|	111400|	"Research"|
"d009"|	111784|	"Customer Service"|
"d009"|	111877|	"Customer Service"|
"d009"|	111939|	"Customer Service"|
"d009"|	111692|	"Customer Service"|
  --  |	     |	"Public Relations"|
  --  |	     |	"Marketing"|

--------------------------------------------------------------------------

## Task Six: JOIN and WHERE Used Together
#### In this task, you will retrieve data from tables using JOIN and WHERE together

## JOIN and WHERE Used Together

#### 6.1: Extract the employee number, first name, last name and salary of all employees who earn above 145000 dollars per year

#### Let us retrieve all data in the salaries table

````sql
SELECT * FROM salaries;
````
````sql
SELECT e.emp_no,e.first_name,e.last_name,s.salary
FROM employees e
JOIN salaries s
ON e.emp_no=s.emp_no
WHERE salary>145000;
````

**Results:**

emp_no|first_name|last_name|salary|
------|----------|---------|------|
11486 |	"Itzchak"|"Ramaiah"|145732|
18997|	"Basim"	|"Tischendorf"|	145215|
		
#### 6.2: Select the first and last name, the hire date and the salary of all employees whose first name is 'Mario' and last_name is 'Straney'

````sql
SELECT e.first_name, e.last_name, e.hire_date,s.salary
FROM employees e
JOIN salaries s 
ON e.emp_no = s.emp_no
WHERE e.first_name='Mario'AND e.last_name='Straney';
````

**Results:**

first_name|last_name|hire_date|salary|
----------|---------|---------|------|
"Mario"|	"Straney"|	"1997-07-09"|	64363|
"Mario"|	"Straney"|	"1997-07-09"|	64523|
"Mario"|	"Straney"|	"1997-07-09"|	64741|
"Mario"|	"Straney"|	"1997-07-09"|	65092|
"Mario"|	"Straney"|	"1997-07-09"|	68422|

#### 6.4: Join the 'employees' and the 'dept_manager' tables to return a subset of all the employees whose last name is 'Markovitch'.See if the output contains a manager with that name

````sql
SELECT e.emp_no,e.first_name,e.last_name,dm.dept_no,dm.from_date
FROM employees e
LEFT JOIN dept_manager dm
ON e.emp_no = dm.emp_no
WHERE e.last_name='Markovitch'
ORDER BY dm.dept_no,e.emp_no
````

**Results:**

emp_no|first_name|last_name|dept_no|from_date|
------|----------|---------|-------|---------|
110022|	"Margareta"|	"Markovitch"|	"d001"|	"1985-01-01"|
10898|	"Munenori"|	"Markovitch"|	|	|
11817|	"Niranjan"|	"Markovitch"|	|	|
12419|	"Srinidhi"|	"Markovitch"|	|	|
12977|	"Byong"|	"Markovitch"|	|	|
15392|	"Pradeep"|	"Markovitch"|	|	|
21545|	"Boguslaw"|	"Markovitch"|	|	|

#### 6.5: Join the 'employees' and the 'dept_manager' tables to return a subset of all the employees who were hired before 31st of January, 1985

````sql
SELECT e.emp_no,e.first_name,e.last_name,dm.dept_no,dm.from_date
FROM employees e
LEFT JOIN dept_manager dm
ON e.emp_no = dm.emp_no
WHERE e.hire_date<'1985-01-31'
ORDER BY dm.dept_no,e.emp_no;
````

**Results:**

emp_no|first_name|last_name|dept_no|from_date|
------|----------|---------|-------|---------|
110022|	"Margareta"|	"Markovitch"|	"d001"|	"1985-01-01"|
110085|	"Ebru"|	        "Alpin"|	"d002"|	"1985-01-01"|
110114|	"Isamu"|	"Legleitner"|	"d002"|	"1989-12-17"|
110183|	"Shirish"|	"Ossenbruggen"|	"d003"|	"1985-01-01"|
110303|	"Krassimir"|	"Wegerle"|	"d004"|	"1985-01-01"|
110511|	"DeForest"|	"Hagimont"|	"d005"|	"1985-01-01"|
110725|	"Peternela"|	"Onuegbe"|	"d006"|	"1985-01-01"|
111035|	"Przemyslawa"|	"Kaelbling"|	"d007"|	"1985-01-01"|
111400|	"Arie"|	        "Staelin"|	"d008"|	"1985-01-01"|
111692|	"Tonny"|  	"Butterworth"|	"d009"|	"1985-01-01"|

----------------------------------------------------------------------------------------------

## Task Seven: Using Aggregate Functions with Joins
#### In this task, you will retrieve data from tables in the employees database, using Aggregate Functions with Joins

## Using Aggregate Functions with Joins

#### 7.1: What is the average salary for the different gender?

````sql  
SELECT e.gender,ROUND(AVG(salary),2)AS average_salary
FROM employees e
JOIN salaries s
ON e.emp_no=s.emp_no
GROUP BY e.gender;
````

**Results:**

gender|average_salary|
------|--------------|
"M"|	63865.65|
"F"|	64163.84|

#### 7.2: What do you think will be the output if we SELECT e.emp_no?

````sql
SELECT e.emp_no, e.gender, AVG(s.salary) AS average_salary
FROM employees e
JOIN salaries s 
ON e.emp_no = s.emp_no
GROUP BY e.emp_no, gender; 
````

**Results:**

emp_no|gender|average_salary|
------|------|--------------|
10896|	"M"|	43703.800000000000|
16592|	"F"|	70777.666666666667|
11233|	"F"|	56082.818181818182|
11719|	"M"|	82698.857142857143|
18803|	"M"|	69606.600000000000|
12502|	"F"|	52037.428571428571|
13093|	"M"|	79578.666666666667|
13520|	"F"|	51218.142857142857|
20549|	"M"|	84572.333333333333|
17803|	"M"|	69082.642857142857|

#### 7.3: How many males and how many females managers do we have in employees database?

````sql
SELECT e.gender,COUNT(dm.emp_no)
FROM employees e
JOIN dept_manager dm
ON e.emp_no=dm.emp_no
GROUP BY e.gender;
````

**Results:**

gender|emp_no|
------|------|
"M"|	11|
"F"|	13|

-------------------------------------------------------------------

## Task Eight: Join more than Two Tables in SQL
#### In this task, you will retrieve data from tables in the employees database, by joining more than two Tables in SQL

## Join more than Two Tables in SQL

#### 8.1: Extract a list of all managers' first and last name, dept_no, hire date, to_date, and department name

````sql
SELECT e.emp_no, e.first_name, e.last_name, m.dept_no, e.hire_date, m.to_date, d.dept_name
FROM employees e  
JOIN dept_manager m 
ON e.emp_no = m.emp_no
JOIN departments d 
ON m.dept_no = d.dept_no;
````

**Results:**

emp_no| first_name|last_name|dept_no| hire_date| to_date| d.dept_name|
------|-----------|---------|-------|----------|--------|------------|
110022|	"Margareta"|	"Markovitch"|	"d001"|	"1985-01-01"|	"1991-10-01"|	"Marketing"|
110039|	"Vishwani"|	"Minakawa"|	"d001"|	"1986-04-12"|	"9999-01-01"|	"Marketing"|
110085|	"Ebru"	  |      "Alpin" |	"d002"|	"1985-01-01"|	"1989-12-17"|	"Finance"|
110114|	"Isamu"  |	"Legleitner"|	"d002"|	"1985-01-14"|	"9999-01-01"|	"Finance"|
110183|	"Shirish"|	"Ossenbruggen"|	"d003"|	"1985-01-01"|	"1992-03-21"|	"Human Resources"|
110228|	"Karsten"|	"Sigstam"|	"d003"|	"1985-08-04"|	"9999-01-01"|	"Human Resources"|
110303|	"Krassimir"|	"Wegerle"|	"d004"|	"1985-01-01"|	"1988-09-09"|	"Production"|
110344|	"Rosine"|	"Cools" |	"d004"|	"1985-11-22"|	"1992-08-02"|	"Production"|
110386|	"Shem"  |	 "Kieras"|	"d004"|	"1988-10-14"|	"1996-08-30"|	"Production"|
110420|	"Oscar" |	"Ghazalie"|	"d004"|	"1992-02-05"|	"9999-01-01"|	"Production"|
110511|	"DeForest"|	"Hagimont"|	"d005"|	"1985-01-01"|	"1992-04-25"|	"Development"|
110567|	"Leon"  |	"DasSarma"|	"d005"|	"1986-10-21"|	"9999-01-01"|	"Development"|
110725|	"Peternela"|	"Onuegbe"|	"d006"|	"1985-01-01"|	"1989-05-06"|	"Quality Management"|
110765|	"Rutger"|	"Hofmeyr"|	"d006"|	"1989-01-07"|	"1991-09-12"|	"Quality Management"|
110800|	"Sanjoy"|	"Quadeer"|	"d006"|	"1986-08-12"|	"1994-06-28"|	"Quality Management"|
110854|	"Dung"  |	"Pesch" |	"d006"|	"1989-06-09"|	"9999-01-01"|	"Quality Management"|
111035|	"Przemyslawa"|	"Kaelbling"|	"d007"|	"1985-01-01"|	"1991-03-07"|	"Sales"|
111133|	"Hauke" |	"Zhang" |	"d007"|	"1986-12-30"|	"9999-01-01"|	"Sales"|
111400|	"Arie"  |	"Staelin"|	"d008"|	"1985-01-01"|	"9999-01-01"|	"Research"|
111692|	"Tonny" |	"Butterworth"|	"d009"|	"1985-01-01"|	"1988-10-17"|	"Customer Service"|
111784|	"Marjo" |	"Giarratana"|	"d009"|	"1988-02-12"|	"1992-09-08"|	"Customer Service"|
111877|	"Xiaobin"|	"Spinelli"|	"d009"|	"1991-08-17"|	"1996-01-03"|	"Customer Service"|
111939|	"Yuchang"|	"Weedman"|	"d009"|	"1989-07-10"|	"9999-01-01"|	"Customer Service"|

#### 8.3: Retrieve the average salary for the different departments

#### Retrieve all data from departments table

````sql
SELECT * FROM departments
````

**Results:**

dept_no|dept_name|
-------|---------|
"d001"|	"Marketing"|
"d002"|	"Finance"|
"d003"|	"Human Resources"|
"d004"|	"Production"|
"d005"|	"Development"|
"d006"|	"Quality Management"|
"d007"|	"Sales"|
"d008"|	"Research"|
"d009"|	"Customer Service"|

#### Retrieve all data from dept_emp table

````sql
SELECT * FROM dept_emp
````

**Results:**

emp_no|dept_no|from_date|to_date|
------|-------|---------|-------|
10001|	"d005"|	"1986-06-26"|	"9999-01-01"|
10002|	"d007"|	"1996-08-03"|	"9999-01-01"|
10003|	"d004"|	"1995-12-03"|	"9999-01-01"|
10004|	"d004"|	"1986-12-01"|	"9999-01-01"|
10005|	"d003"|	"1989-09-12"|	"9999-01-01"|
10006|	"d005"|	"1990-08-05"|	"9999-01-01"|

#### Retrieve all data from salaries table

````sql
SELECT * FROM salaries
````

**Results:**

emp_no|salary|from_date|to_date|
------|-------|---------|-------|
10001|	60117|	"1986-06-26"|	"1987-06-26"|
10001|	62102|	"1987-06-26"|	"1988-06-25"|
10001|	66074|	"1988-06-25"|	"1989-06-25"|
10001|	66596|	"1989-06-25"|	"1990-06-25"|
10001|	66961|	"1990-06-25"|	"1991-06-25"|
10001|	71046|	"1991-06-25"|	"1992-06-24"|

#### Solution to 8.3

````sql
SELECT d.dept_name,AVG(salary) AS average_salary
FROM departments d
JOIN dept_emp de
ON d.dept_no=de.dept_no
JOIN salaries s
ON de.emp_no=s.emp_no
GROUP BY d.dept_name
ORDER BY AVG(salary) DESC;
````

**Results:**

dept_name|average_salary|
-------|----------------|
"Sales" |	80864.731148210548|
"Marketing"|	72451.846877673225|
"Finance"|	70620.996544471154|
"Research"|	60312.626700453454|
"Production"|	59805.776185928048|
"Development"|	59619.621131036209|
"Customer Service"|	58754.113861386139|
"Quality Management"|	58119.443663911846|
"Human Resources"|	55941.055949328910|

#### 8.4 (Ex.): Retrieve the average salary for the different departments where the average_salary is more than 60000

````sql
SELECT d.dept_name,AVG(salary) AS average_salary
FROM departments d
JOIN dept_emp de
ON d.dept_no=de.dept_no
JOIN salaries s
ON de.emp_no=s.emp_no
GROUP BY d.dept_name
HAVING AVG(salary) > 60000
ORDER BY AVG(salary) DESC;
````

**Results:**

dept_name|average_salary|
---------|----------------|
"Sales"	 |       80864.731148210548|
"Marketing"|	72451.846877673225|
"Finance"|	70620.996544471154|
"Research"|	60312.626700453454|

------------------------------------------------------------------------------------------------------------------
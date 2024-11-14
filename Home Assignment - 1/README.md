# Solution to Assignment 1

```sql
-- 1. Create a database named "assignmentdatabase"
CREATE DATABASE assignmentdatabase;

-- 2. Delete the earlier database (if exists) and create a new one named "assignmentdb"
DROP DATABASE IF EXISTS assignmentdatabase;
CREATE DATABASE assignmentdb;

-- Use the new database
USE assignmentdb;

-- 3. Create table "teachertb"
CREATE TABLE teachertb (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50),
    department VARCHAR(50),
    room_no VARCHAR(10),
    date_of_birth DATE,
    age INT
);

-- 4. Add 2 new columns to "teachertb"
ALTER TABLE teachertb
ADD COLUMN joining_date DATE,
ADD COLUMN total_presence_day INT;

-- 5. Increase VARCHAR character limit of the name column
ALTER TABLE teachertb
MODIFY COLUMN name VARCHAR(100);

-- 6. Create table "studenttb"
CREATE TABLE studenttb (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    department VARCHAR(50),
    cgpa FLOAT,
    date_of_birth DATE,
    credits_completed INT,
    current_trimester INT
);


-- 7. Remove the age column from "teachertb"
ALTER TABLE teachertb
DROP COLUMN age;


-- 8. Rename date_of_birth to dob in both tables
ALTER TABLE teachertb
CHANGE COLUMN date_of_birth dob DATE;

ALTER TABLE studenttb
CHANGE COLUMN date_of_birth dob DATE;

-- 9. Insert a row in each table
INSERT INTO teachertb (name, department, room_no, dob, joining_date, total_presence_day)
VALUES ('John Doe', 'Computer Science', 'CS101', '1990-01-01', '2010-09-01', 2500);

INSERT INTO studenttb (name, department, cgpa, dob, credits_completed, current_trimester)
VALUES ('Jane Smith', 'EEE', 3.75, '2000-05-15', 90, 5);

-- 10. Insert 25 rows in each table using the format INSERT INTO tablename VALUES (), ()

-- For teachertb
INSERT INTO teachertb (name, department, room_no, dob, joining_date, total_presence_day) VALUES 
('Teacher1', 'Computer Science', 'Room101', '1970-01-01', '2000-01-01', 100),
('Teacher2', 'Electrical Engineering', 'Room102', '1971-01-01', '2001-01-01', 200),
('Teacher3', 'Mechanical Engineering', 'Room103', '1972-01-01', '2002-01-01', 300),
('Teacher4', 'Computer Science', 'Room104', '1973-01-01', '2003-01-01', 400),
('Teacher5', 'Electrical Engineering', 'Room105', '1974-01-01', '2004-01-01', 500),
('Teacher6', 'Mechanical Engineering', 'Room106', '1975-01-01', '2005-01-01', 600),
('Teacher7', 'Computer Science', 'Room107', '1976-01-01', '2006-01-01', 700),
('Teacher8', 'Electrical Engineering', 'Room108', '1977-01-01', '2007-01-01', 800),
('Teacher9', 'Mechanical Engineering', 'Room109', '1978-01-01', '2008-01-01', 900),
('Teacher10', 'Computer Science', 'Room110', '1979-01-01', '2009-01-01', 1000),
('Teacher11', 'Electrical Engineering', 'Room111', '1980-01-01', '2010-01-01', 1100),
('Teacher12', 'Mechanical Engineering', 'Room112', '1981-01-01', '2011-01-01', 1200),
('Teacher13', 'Computer Science', 'Room113', '1982-01-01', '2012-01-01', 1300),
('Teacher14', 'Electrical Engineering', 'Room114', '1983-01-01', '2013-01-01', 1400),
('Teacher15', 'Mechanical Engineering', 'Room115', '1984-01-01', '2014-01-01', 1500),
('Teacher16', 'Computer Science', 'Room116', '1985-01-01', '2015-01-01', 1600),
('Teacher17', 'Electrical Engineering', 'Room117', '1986-01-01', '2016-01-01', 1700),
('Teacher18', 'Mechanical Engineering', 'Room118', '1987-01-01', '2017-01-01', 1800),
('Teacher19', 'Computer Science', 'Room119', '1988-01-01', '2018-01-01', 1900),
('Teacher20', 'Electrical Engineering', 'Room120', '1989-01-01', '2019-01-01', 2000),
('Teacher21', 'Mechanical Engineering', 'Room121', '1990-01-01', '2020-01-01', 2100),
('Teacher22', 'Computer Science', 'Room122', '1991-01-01', '2021-01-01', 2200),
('Teacher23', 'Electrical Engineering', 'Room123', '1992-01-01', '2022-01-01', 2300),
('Teacher24', 'Mechanical Engineering', 'Room124', '1993-01-01', '2023-01-01', 2400),
('Teacher25', 'Computer Science', 'Room125', '1994-01-01', '2024-01-01', 2500);

-- For studenttb
INSERT INTO studenttb (name, department, cgpa, dob, credits_completed, current_trimester) VALUES 
('Student1', 'Computer Science', 3.5, '2000-01-01', 30, 3),
('Student2', 'Electrical Engineering', 3.6, '2000-02-01', 60, 4),
('Student3', 'Mechanical Engineering', 3.7, '2000-03-01', 90, 5),
('Student4', 'Computer Science', 3.8, '2000-04-01', 120, 6),
('Student5', 'Electrical Engineering', 3.9, '2000-05-01', 150, 7),
('Student6', 'Mechanical Engineering', 3.5, '2000-06-01', 30, 3),
('Student7', 'Computer Science', 3.6, '2000-07-01', 60, 4),
('Student8', 'Electrical Engineering', 3.7, '2000-08-01', 90, 5),
('Student9', 'Mechanical Engineering', 3.8, '2000-09-01', 120, 6),
('Student10', 'Computer Science', 3.9, '2000-10-01', 150, 7),
('Student11', 'Electrical Engineering', 3.5, '2000-11-01', 30, 3),
('Student12', 'Mechanical Engineering', 3.6, '2000-12-01', 60, 4),
('Student13', 'Computer Science', 3.7, '2001-01-01', 90, 5),
('Student14', 'Electrical Engineering', 3.8, '2001-02-01', 120, 6),
('Student15', 'Mechanical Engineering', 3.9, '2001-03-01', 150, 7),
('Student16', 'Computer Science', 3.5, '2001-04-01', 30, 3),
('Student17', 'Electrical Engineering', 3.6, '2001-05-01', 60, 4),
('Student18', 'Mechanical Engineering', 3.7, '2001-06-01', 90, 5),
('Student19', 'Computer Science', 3.8, '2001-07-01', 120, 6),
('Student20', 'Electrical Engineering', 3.9, '2001-08-01', 150, 7),
('Student21', 'Mechanical Engineering', 3.5, '2001-09-01', 30, 3),
('Student22', 'Computer Science', 3.6, '2001-10-01', 60, 4),
('Student23', 'Electrical Engineering', 3.7, '2001-11-01', 90, 5),
('Student24', 'Mechanical Engineering', 3.8, '2001-12-01', 120, 6),
('Student25', 'Computer Science', 3.9, '2002-01-01', 150, 7);

-- OR, using INSERT INTO tablename (col1, col2, ...) VALUES (), ()

-- 10. Insert 25 rows in each table using the format INSERT INTO tablename (col1, col2, ...) VALUES (), ()

-- For teachertb
INSERT INTO teachertb (name, department, room_no, dob, joining_date, total_presence_day) VALUES 
('Teacher1', 'Computer Science', 'Room101', '1970-01-01', '2000-01-01', 100),
('Teacher2', 'Electrical Engineering', 'Room102', '1971-01-01', '2001-01-01', 200),
('Teacher3', 'Mechanical Engineering', 'Room103', '1972-01-01', '2002-01-01', 300),
('Teacher4', 'Computer Science', 'Room104', '1973-01-01', '2003-01-01', 400),
('Teacher5', 'Electrical Engineering', 'Room105', '1974-01-01', '2004-01-01', 500),
('Teacher6', 'Mechanical Engineering', 'Room106', '1975-01-01', '2005-01-01', 600),
('Teacher7', 'Computer Science', 'Room107', '1976-01-01', '2006-01-01', 700),
('Teacher8', 'Electrical Engineering', 'Room108', '1977-01-01', '2007-01-01', 800),
('Teacher9', 'Mechanical Engineering', 'Room109', '1978-01-01', '2008-01-01', 900),
('Teacher10', 'Computer Science', 'Room110', '1979-01-01', '2009-01-01', 1000),
('Teacher11', 'Electrical Engineering', 'Room111', '1980-01-01', '2010-01-01', 1100),
('Teacher12', 'Mechanical Engineering', 'Room112', '1981-01-01', '2011-01-01', 1200),
('Teacher13', 'Computer Science', 'Room113', '1982-01-01', '2012-01-01', 1300),
('Teacher14', 'Electrical Engineering', 'Room114', '1983-01-01', '2013-01-01', 1400),
('Teacher15', 'Mechanical Engineering', 'Room115', '1984-01-01', '2014-01-01', 1500),
('Teacher16', 'Computer Science', 'Room116', '1985-01-01', '2015-01-01', 1600),
('Teacher17', 'Electrical Engineering', 'Room117', '1986-01-01', '2016-01-01', 1700),
('Teacher18', 'Mechanical Engineering', 'Room118', '1987-01-01', '2017-01-01', 1800),
('Teacher19', 'Computer Science', 'Room119', '1988-01-01', '2018-01-01', 1900),
('Teacher20', 'Electrical Engineering', 'Room120', '1989-01-01', '2019-01-01', 2000),
('Teacher21', 'Mechanical Engineering', 'Room121', '1990-01-01', '2020-01-01', 2100),
('Teacher22', 'Computer Science', 'Room122', '1991-01-01', '2021-01-01', 2200),
('Teacher23', 'Electrical Engineering', 'Room123', '1992-01-01', '2022-01-01', 2300),
('Teacher24', 'Mechanical Engineering', 'Room124', '1993-01-01', '2023-01-01', 2400),
('Teacher25', 'Computer Science', 'Room125', '1994-01-01', '2024-01-01', 2500);

-- For studenttb
INSERT INTO studenttb (name, department, cgpa, dob, credits_completed, current_trimester) VALUES 
('Student1', 'Computer Science', 3.5, '2000-01-01', 30, 3),
('Student2', 'Electrical Engineering', 3.6, '2000-02-01', 60, 4),
('Student3', 'Mechanical Engineering', 3.7, '2000-03-01', 90, 5),
('Student4', 'Computer Science', 3.8, '2000-04-01', 120, 6),
('Student5', 'Electrical Engineering', 3.9, '2000-05-01', 150, 7),
('Student6', 'Mechanical Engineering', 3.5, '2000-06-01', 30, 3),
('Student7', 'Computer Science', 3.6, '2000-07-01', 60, 4),
('Student8', 'Electrical Engineering', 3.7, '2000-08-01', 90, 5),
('Student9', 'Mechanical Engineering', 3.8, '2000-09-01', 120, 6),
('Student10', 'Computer Science', 3.9, '2000-10-01', 150, 7),
('Student11', 'Electrical Engineering', 3.5, '2000-11-01', 30, 3),
('Student12', 'Mechanical Engineering', 3.6, '2000-12-01', 60, 4),
('Student13', 'Computer Science', 3.7, '2001-01-01', 90, 5),
('Student14', 'Electrical Engineering', 3.8, '2001-02-01', 120, 6),
('Student15', 'Mechanical Engineering', 3.9, '2001-03-01', 150, 7),
('Student16', 'Computer Science', 3.5, '2001-04-01', 30, 3),
('Student17', 'Electrical Engineering', 3.6, '2001-05-01', 60, 4),
('Student18', 'Mechanical Engineering', 3.7, '2001-06-01', 90, 5),
('Student19', 'Computer Science', 3.8, '2001-07-01', 120, 6),
('Student20', 'Electrical Engineering', 3.9, '2001-08-01', 150, 7),
('Student21', 'Mechanical Engineering', 3.5, '2001-09-01', 30, 3),
('Student22', 'Computer Science', 3.6, '2001-10-01', 60, 4),
('Student23', 'Electrical Engineering', 3.7, '2001-11-01', 90, 5),
('Student24', 'Mechanical Engineering', 3.8, '2001-12-01', 120, 6),
('Student25', 'Computer Science', 3.9, '2002-01-01', 150, 7);


-- 11. Create "temporarytb" table
CREATE TABLE temporarytb (
    tempdata_id INT PRIMARY KEY AUTO_INCREMENT,
    tempdate_content VARCHAR(100)
);

-- 12. Insert 5 rows into "temporarytb"
INSERT INTO temporarytb (tempdate_content) VALUES
('Temporary Data 1'),
('Temporary Data 2'),
('Temporary Data 3'),
('Temporary Data 4'),
('Temporary Data 5');

-- 13. Truncate "temporarytb"
TRUNCATE TABLE temporarytb;

-- 14. Add comments (3 types)
-- This is a single-line comment

/*
This is a
multi-line comment
*/

#This is also a single-line comment


-- 15. Delete the entire "temporarytb" table
DROP TABLE temporarytb;
```

CREATE TABLE Students (
    student_id NUMBER PRIMARY KEY,
    student_name VARCHAR2(100),
    email VARCHAR2(100)
);


CREATE TABLE Courses (
    course_id NUMBER PRIMARY KEY,
    course_name VARCHAR2(100),
    course_duration VARCHAR2(50)
);


CREATE TABLE Enrollments (
    enrollment_id NUMBER PRIMARY KEY,
    student_id NUMBER REFERENCES Students(student_id),
    course_id NUMBER REFERENCES Courses(course_id),
    enrollment_date DATE
);


INSERT INTO Students VALUES (1, 'Alice Johnson', 'alice@example.com');
INSERT INTO Students VALUES (2, 'Bob Smith', 'bob@example.com');
INSERT INTO Students VALUES (3, 'Charlie Brown', 'charlie@example.com');


INSERT INTO Courses VALUES (101, 'Java Programming', '3 Months');
INSERT INTO Courses VALUES (102, 'Database Systems', '2 Months');
INSERT INTO Courses VALUES (103, 'Web Development', '4 Months');


INSERT INTO Enrollments VALUES (1001, 1, 101, TO_DATE('2024-01-10', 'YYYY-MM-DD'));
INSERT INTO Enrollments VALUES (1002, 2, 102, TO_DATE('2024-02-15', 'YYYY-MM-DD'));
INSERT INTO Enrollments VALUES (1003, 3, 103, TO_DATE('2024-03-01', 'YYYY-MM-DD'));


SELECT s.student_name, c.course_name, e.enrollment_date
FROM Enrollments e
JOIN Students s ON e.student_id = s.student_id
JOIN Courses c ON e.course_id = c.course_id;

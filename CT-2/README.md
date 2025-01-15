# Solution to CT 2

```sql
-- Create the database
CREATE DATABASE library;
USE library;

-- Create the books table
CREATE TABLE books (
    ISBN VARCHAR(13) PRIMARY KEY,
    title VARCHAR(100) NOT NULL,
    author VARCHAR(100) NOT NULL,
    publication_year INT,
    genre VARCHAR(50)
);

-- Create the members table
CREATE TABLE members (
    member_id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    contact_info VARCHAR(100) NOT NULL,
    membership_id VARCHAR(20) UNIQUE NOT NULL
);

-- Create the loans table
CREATE TABLE loans (
    loan_id INT AUTO_INCREMENT PRIMARY KEY,
    ISBN VARCHAR(13),
    member_id INT,
    loan_date DATE NOT NULL,
    due_date DATE NOT NULL,
    return_date DATE,
    FOREIGN KEY (ISBN) REFERENCES books(ISBN),
    FOREIGN KEY (member_id) REFERENCES members(member_id)
);

-- Insert sample data into books table
INSERT INTO books (ISBN, title, author, publication_year, genre) VALUES
('9780061120084', 'To Kill a Mockingbird', 'Harper Lee', 1960, 'Fiction'),
('9780141439518', 'Pride and Prejudice', 'Jane Austen', 1813, 'Romance'),
('9780307277671', '1984', 'George Orwell', 1949, 'Science Fiction'),
('9780618260300', 'The Hobbit', 'J.R.R. Tolkien', 1937, 'Fantasy'),
('9780545010221', 'Harry Potter and the Sorcerer''s Stone', 'J.K. Rowling', 1997, 'Fantasy');

-- Insert sample data into members table
INSERT INTO members (name, contact_info, membership_id) VALUES
('John Doe', 'johndoe@email.com', 'JD001'),
('Jane Smith', 'janesmith@email.com', 'JS002'),
('Bob Johnson', 'bobjohnson@email.com', 'BJ003'),
('Alice Brown', 'alicebrown@email.com', 'AB004'),
('Charlie Davis', 'charliedavis@email.com', 'CD005');

-- Insert sample data into loans table
INSERT INTO loans (ISBN, member_id, loan_date, due_date, return_date) VALUES
('9780061120084', 1, '2023-01-01', '2023-01-15', '2023-01-14'),
('9780141439518', 2, '2023-01-05', '2023-01-19', NULL),
('9780307277671', 3, '2023-01-10', '2023-01-24', NULL),
('9780618260300', 4, '2023-01-15', '2023-01-29', '2023-01-28'),
('9780545010221', 5, '2023-01-20', '2023-02-03', NULL);

-- Query 1: List all books by a specific author
SELECT * FROM books WHERE author = 'J.K. Rowling';

-- Query 2: Show all currently borrowed books and their borrowers
SELECT b.title, m.name, l.due_date
FROM loans l
JOIN books b ON l.ISBN = b.ISBN
JOIN members m ON l.member_id = m.member_id
WHERE l.return_date IS NULL;

-- Query 3: Find members who have overdue books
SELECT m.name, b.title, l.due_date
FROM loans l
JOIN members m ON l.member_id = m.member_id
JOIN books b ON l.ISBN = b.ISBN
WHERE l.due_date < CURDATE() AND l.return_date IS NULL;

-- Query 4: Display the most popular genre based on the number of times books in that genre have been borrowed
SELECT b.genre, COUNT(*) as borrow_count
FROM loans l
JOIN books b ON l.ISBN = b.ISBN
GROUP BY b.genre
ORDER BY borrow_count DESC
LIMIT 1;

-- Query 5: Create a query that shows a summary of each member's borrowing history
SELECT m.name, COUNT(l.loan_id) as total_loans, 
       GROUP_CONCAT(b.title SEPARATOR ', ') as borrowed_books
FROM members m
LEFT JOIN loans l ON m.member_id = l.member_id
LEFT JOIN books b ON l.ISBN = b.ISBN
GROUP BY m.member_id;

-- Query 6: Write a query to find the book that has been borrowed the most times
SELECT b.title, COUNT(l.loan_id) as borrow_count
FROM books b
LEFT JOIN loans l ON b.ISBN = l.ISBN
GROUP BY b.ISBN
ORDER BY borrow_count DESC
LIMIT 1;
```

Explanation:

1. Database and Table Creation:
   - We create a database named 'library' and three tables: 'books', 'members', and 'loans'.
   - The 'books' table uses ISBN as the primary key, as it's a unique identifier for books.
   - The 'members' table uses an auto-incrementing member_id as the primary key.
   - The 'loans' table connects books and members using foreign keys.

2. Data Insertion:
   - Sample data is inserted into each table to demonstrate the database's functionality.

3. Queries:
   - Query 1: Simple SELECT with a WHERE clause to find books by a specific author.
   - Query 2: JOINS the three tables to show currently borrowed books (where return_date is NULL).
   - Query 3: Similar to Query 2, but adds a condition to check for overdue books.
   - Query 4: Uses COUNT and GROUP BY to find the most popular genre.
   - Query 5: Uses LEFT JOIN to include all members, even those who haven't borrowed books, and GROUP_CONCAT to list all borrowed books for each member.
   - Query 6: Uses COUNT and LEFT JOIN to find the most borrowed book, including books that haven't been borrowed.

This solution covers all the requirements of the assignment and demonstrates proper database design, data insertion, and complex SQL queries including JOINs, GROUP BY, ORDER BY, and aggregate functions.

---

<!-- ![NOTE icon](https://img.icons8.com/color/48/000000/note.png) All students got 0.5 grace marks for this CT. -->

>[!NOTE]
>All students got 0.5 grace marks for this CT.
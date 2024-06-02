This sql project is a part of final project for my courseowrk. It consists of 3 parts of a Library system.
Part A

	•	Design a database can be used to maintain the data stored and processed by a lending library. To construct a good database design, utilize the techniques we discussed this semester.  The design should implement the business rules that are outlined below. Note: not every business rules can necessarily be implemented directly with the database design
	•	Map out the design using Visio or MySQL Workbench.  
	•	After you design the database, you will be implementing it using SQL Server 
	•	Note: you can add other attributes if you think they are necessary or to add realism to this project.

	•	The library categorizes the books it has.  Typical categories might be: fiction, historical fiction, mystery, science fiction, juvenile, reference, adult.  A book might have more than one category. For example, it might be juvenile and fiction.
	•	Any reading item that is categorized as reference may not be borrowed.
	•	For each book, the library stores the isbn, title, publisher, category type, author(s), cost
	•	A book can have more than one author
	•	An author can write more than one book
	•	A publisher can publish more than one book
	•	The library stores publisher data such as Publisher Name, Address, Phone Number, Contact Person
	•	There are several branches within this lending library system.  For each branch store the branch id, name, address, telephone number, fax number, head librarian
	•	A branch might employ several librarians, but only one head librarian.  For each librarian, store the employee id, name, address, telephone number, salary, cell phone number.  
	•	A librarian may be assigned to only one branch.
	•	Branches have different types of employees.  Some types are : Librarian, Network Administrator,  Computer Programmer, IT Manager, Floor Manager, Custodian, Accountant, Data Analyst  Librarians must have earned a degree in library science. For each employee, the library maintains name, address, phone number, birthdate, hire date, type of employee.  For librarians, the library also maintains when the librarian earned his/her degree and the school at which the librarian earned the degree
	•	The Library supports two types of PayTypes: salaried and hourly. Employees that are salaried earn a yearly salary that is paid in 12 payments on the first of each month. Employees that are clerical, earn an hourly wage.    All employees get vacation time depending on their length of service. The minimum amount of vacation time is two weeks. 
	•	The library maintains a log of how many hours each clerical type of employee logged during each week that he worked. This log is used to produce paychecks for clerical staff at the end of each week. 
	•	Each employee is assigned to one specific branch only.
	•	The library issues library cards to people who wish to borrow books from the library.  The library keeps a list of each borrower by storing the card id, borrower name, address, phone number, birthdate, date the card was issued, balance due.   A card expires ten years from the time it is issued.
If a person is less than 18 years old, then the library will also keep information about the Borrower’s parent or legal guardian such as name, address, phone number. 
	•	A person can have only one valid library card at a given time.  
	•	A person can’t be issued a new library card, if he owes money on an expired card.
	•	The Library purchases many copies of the same book. Each book copy is assigned a unique copy ID. Each book copy is found in a specific branch of the library.  
	•	The Library assigns a Condition to each book copy. Sample condition values could be NEW, EXCELLENT, GOOD, WORN, POOR. Eventually copies that are in POOR condition will be discarded and replaced with new copies.
	•	For each borrowed book copy, the library keeps track of the copy id and the card number of the person who borrowed it.  The library keeps track of the date on which it was borrowed and records the due date which is two weeks after the borrow date.  When the copy is returned this record is updated with the return date. 
	•	When a book copy is borrowed, the copy is marked as BORROWED. When the book copy is returned the copy is marked as AVAILABLE or NOT BORROWED. 
	•	A borrower can’t borrow a book from a particular branch unless that branch has a copy of that book and it is currently in stock (e.g. not being borrowed by someone else) 
	•	When a borrower returns a book copy after the due date the system calculates the amount owed and any overdue charge incurred is added to the card balance 
	•	A borrower can not use a card to borrow books, if he owes more than 10 dollars on that card.
	•	The library has a list of overdue charges.  The charges are currently .05 each day for juvenile books and .10 per day for adult books.  When a book is returned late the borrower pays charges that are in effect at the time the book is returned.
	•	A borrower can acknowledge that he has lost a copy of a book.  If so, the copy is marked LOST and the book’s cost is added to the card balance.   Eventually the copy may be removed from the current inventory of branch copies and stored in a history file.

 Part B
a.	Implement the database you designed to complete Part A of the project using the RDBMS,  SQL Server Express.
Include: 
entities, attributes, primary and foreign keys, any indexes you deem necessary or desirable. 
b.	Populate the database with a realistic set of data

The purpose of a sound database design is to help ensure data integrity and validity.  Setting primary keys, foreign keys and identifying entities and their attributes using normalization isn’t always sufficient to ensure data validity.  Therefore database provides additional means to check and crosscheck data for accuracy. Three other approaches is the use of constraints and procedures or triggers, coupled with transaction processing ability to either COMMIT or ROLLBACK a transaction.
c.	Demonstrate that you know how to implement these types of constraints to help ensure data accuracy.
Use the following sample constraints as a guide.

Sample Constraints
a.	Librarians earn between 20000 and 70000 per year
b.	A Borrower can’t accrue more than 10 dollars balance on any card.
c.	A Borrower must be at least 10 years old to have a card issued in his name
d.	Pay rate for hourly workers must be at least 15.00.

Sample Triggers or Procedures
a.	A librarian can’t be hired before he has earned a MS in Library Science degree.
b.	A new card can’t be issued for someone who owes money on an existing card
c.	A new card can’t be issued for someone who has a card that hasn’t yet expired
d.	Workers who log hours can’t log more than 40 hours per week
e.	A borrower can’t use a card to borrow books, if he owes more than 10 dollars on that card
f.	Each time a book is returned, check if overdue and add charge to balance on card or customer record
g.	Each time a book is borrowed, check that it can be borrowed. Obviously, this would only happen if physical inventory and system inventory don’t match. 


 Part C
Write queries that will provide answers to the following requests for information.

i.	List the title of the book that is the most popular book to be borrowed. (Namely, it has been borrowed most often number of times )
ii.	Which librarian has the third highest salary at the current time?
iii.	For each employee, list his/her name and the name of the branch for which he/she is currently working and how many employees are working for that branch. 
iv.	 For each book, list the title and publisher of the book and the number of copies currently stocked for this title in each branch, regardless of whether it is currently on loan.
v.	For each quarter of the current year, for each branch list the total amount of books that have been borrowed in that quarter. The first quarter is months Jan, Feb, Mar. The second quarter is months Apr , May , June etc.  List the amounts for each of these quarters, on the same row.
vi.	For each card, list the name of the borrower and the name of the books he currently has borrowed on the card, that have not yet been returned
vii.	For each card, list the name of the borrower and on the same row the quantity of books that have been borrowed in 2020 and the quantity of books that have been borrowed in 2021 with that card. 
viii.	For a specific card, list which other cards borrowed ALL the same books as was borrowed using this card.  (divide query).  You choose the card you will be matching. 
ix.	List the name of the employee that has been working for the library the longest amount of time
x.	For each book , list the title and branch that it is in, if it isn’t currently on loan
xi.	List the names of borrowers and the card id that they have if it hasn’t expired.
xii.	For each author, list his name and the titles of the books he has written
xiii.	For each author, list his name and the name of categories of books he has written
xiv.	For each employee, calculate the amount of money he should have earned this year based on his logged hours.
xv.	List the title of books that have never been borrowed.
xvi.	For each branch, list the total quantity of books, total quantity by category, total quantity by author  
xvii.	For each card, list the name of the cardholder, list the category of books and each book that was borrowed on this card. In the same query list to the how many books have been borrowed for each category, and how many books have been borrowed in total with this card.
xviii.	On one row, list the how many employees are currently employed for each type of employee. Sample types are: Librarian, Network Administrator, Computer Programmer, IT Manager etc
xix.	What is the name of the borrower, who has currently borrowed the most books.
xx.	List the names of borrowers who have borrowed both book A and book B (you can choose the specific book titles).


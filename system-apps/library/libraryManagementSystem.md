Designing  Library Management System

A Library Management System is a software built to handle the primary housekeeping functions of a library. Libraries rely on library management systems to manage asset collections as well as relationships with their members. Library management systems help libraries keep track of the books and their checkouts, as well as members’ subscriptions and profiles.
Library management systems also involve maintaining the database for entering new books and recording books that have been borrowed with their respective due dates.

Requirements-
Any library member should be able to search books by their title, author, subject category as well by the publication date.
Each book will have a unique identification number and other details including a rack number which will help to physically locate the book.
There could be more than one copy of a book, and library members should be able to check-out and reserve any copy. We will call each copy of a book, a book item.
The system should be able to retrieve information like who took a particular book or what are the books checked-out by a specific library member.
There should be a maximum limit (5) on how many books a member can check-out.
There should be a maximum limit (10) on how many days a member can keep a book.
The system should be able to collect fines for books returned after the due date.
Members should be able to reserve books that are not currently available.
The system should be able to send notifications whenever the reserved books become available, as well as when the book is not returned within the due date.
Each book and member card will have a unique barcode. The system will be able to read barcodes from books and members’ library cards.

We have three main actors in our system:
Librarian: Mainly responsible for adding and modifying books, book items, and users. The Librarian can also issue, reserve, and return book items.
Member: All members can search the catalog, as well as check-out, reserve, renew, and return a book.
System: Mainly responsible for sending notifications for overdue books, canceled reservations, etc.

Here are the top use cases of the Library Management System:
Add/Remove/Edit book: To add, remove or modify a book or book item.
Search catalog: To search books by title, author, subject or publication date.
Register new account/cancel membership: To add a new member or cancel the membership of an existing member.
Check-out book: To borrow a book from the library.
Reserve book: To reserve a book which is not currently available.
Renew a book: To reborrow an already checked-out book.
Return a book: To return a book to the library which was issued to a member.

Class diagram Here are the main classes of our Library Management System:
Library: The central part of the organization for which this software has been designed. It has attributes like ‘Name’ to distinguish it from any other libraries and ‘Address’ to describe its location.
Book: The basic building block of the system. Every book will have ISBN, Title, Subject, Publishers, etc.
BookItem: Any book can have multiple copies, each copy will be considered a book item in our system. Each book item will have a unique barcode.
Account: We will have two types of accounts in the system, one will be a general member, and the other will be a librarian.
LibraryCard: Each library user will be issued a library card, which will be used to identify users while issuing or returning books.
BookReservation: Responsible for managing reservations against book items.
BookLending: Manage the checking-out of book items.
Catalog: Catalogs contain a list of books sorted on certain criteria. Our system will support searching through four catalogs: Title, Author, Subject, and Publish-date.
Fine: This class will be responsible for calculating and collecting fines from library members.
Author: This class will encapsulate a book author.
Rack: Books will be placed on racks. Each rack will be identified by a rack number and will have a location identifier to describe the physical location of the rack in the library.
Notification: This class will take care of sending notifications to library members.

Activity diagrams
Check-out a book, 
Return a book, 
Renew a book.


schemas-

enums- constants

interfaces

tables-


BOOKS
bookname-
datetime
issue date
return date
borrowers address
author

USERS
address
number
name

AUTHOR
booktitle

authorid

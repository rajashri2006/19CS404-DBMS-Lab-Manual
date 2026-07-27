# ER Diagram Workshop – Submission Template

## Name : RAJASHRI I
## Register No. 212224040261

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:

<img width="1552" height="1013" alt="dbms_ex1" src="https://github.com/user-attachments/assets/9edf2e71-bb03-4c86-a25e-cd9120b6a06a" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|---|---|---|
| User | Name, Address, Mobile | Stores user information |
| Trainer | **ID (PK)**, Name | Stores trainer information |
| Fitness | Type | Stores fitness program type |
| Membership | Pass | Stores membership details |
| Branch | **ID (PK)**, Address | Stores branch information |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|---|---|---|---|
| User — Choose — Trainer | N : 1 | User: Total, Trainer: Partial | Many users can choose one trainer |
| Trainer — Choose — Fitness | 1 : N | Trainer: Partial, Fitness: Total | One trainer can offer many fitness types |
| User — Has — Membership | 1 : N | User: Total, Membership: Total | One user can have many memberships |
| Branch — Choose — Trainer | 1 : N | Branch: Total, Trainer: Total | One branch can have many trainers |

### Assumptions

- Each user can choose one trainer, while a trainer can be chosen by many users.
- Each trainer can provide multiple fitness programs, while each fitness program is assigned to one trainer.
- A user can have one or more memberships, and each membership belongs to one user.
- Each branch can have multiple trainers, and each trainer is assigned to one branch.
- Each trainer and branch has a unique ID.

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
<img width="1681" height="936" alt="workshop2" src="https://github.com/user-attachments/assets/8e5b3c26-ad20-4c7e-b83b-2da02c7f38a5" />

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|---|---|---|
| Staff | **Staff_ID (PK)**, Name | Manages reports and maintains books |
| Reports | **User_ID (FK)**, Reg_No, Book_No, Issue_Return | Stores book issue and return reports |
| Authentication System | **LoginID (PK)**, Password | Stores login credentials |
| Readers | **User_ID (PK)**, FirstName, LastName, Name, Email, Phone_No, Address | Stores reader information |
| Books | **Book_No (PK)**, **ISBN (UK)**, Title, Author_No, Category, Edition | Stores book information |
| Publisher | **Publisher_ID (PK)**, Name, Year_Of_Publication | Stores publisher information |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|---|---|---|---|
| Staff — Manages — Reports | 1 : N | Staff: Total, Reports: Total | One staff member can manage many reports |
| Staff — Login — Authentication System | N : 1 | Staff: Total, Authentication System: Total | Many staff members can use the authentication system |
| Staff — Keeps Track Of — Readers | M : N | Staff: Total, Readers: Total | Staff members can keep track of multiple readers |
| Staff — Maintain — Books | 1 : N | Staff: Total, Books: Total | One staff member can maintain many books |
| Readers — Reserve/Return — Books | 1 : N | Readers: Total, Books: Total | A reader can reserve or return multiple books |
| Publisher — Published By — Books | 1 : N | Publisher: Total, Books: Total | One publisher can publish many books |

### Assumptions

- Each staff member is uniquely identified by a unique `Staff_ID`.
- Each reader is uniquely identified by a unique `User_ID`.
- Each book is uniquely identified by a unique `Book_No`, and each book has a unique `ISBN`.
- One staff member can manage multiple reports, while each report is managed by one staff member.
- The authentication system stores login credentials used by staff members to access the library system.
- Staff members can keep track of multiple readers, and readers may be tracked by multiple staff members.
- One staff member can maintain multiple books, while each book is maintained by one staff member.
- A reader can reserve or return multiple books over time.
- A book can be reserved or returned by multiple readers over time.
- Each book is published by one publisher, while one publisher can publish multiple books.
- `ReserveDate`, `Return_Date`, and `Due_Date` are associated with the Reserve/Return relationship.

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
<img width="1536" height="1024" alt="workshop3" src="https://github.com/user-attachments/assets/d4a3e4ba-6e12-4cf8-91ee-ced322926c36" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|---|---|---|
| Customer | **C-ID (PK)**, Name, Email, Phone, Address | Stores customer information |
| Reservation | **R-ID (PK)**, C-ID (FK), ID (FK), Date | Stores reservation details |
| Restaurant | **ID (PK)**, Name, Location | Stores restaurant information |
| Order | **O-ID (PK)**, C-ID (FK), ID (FK), Amount, Date | Stores customer order details |
| Menu Item | **M-ID (PK)**, R-ID (FK), Name, Price, Description | Stores menu item information |
| Delivery | **D-ID (PK)**, O-ID (FK), Date, Status | Stores delivery details |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|---|---|---|---|
| Customer — Have — Reservation | 1 : N | Customer: Total, Reservation: Total | One customer can make multiple reservations |
| Restaurant — Have — Reservation | 1 : N | Restaurant: Total, Reservation: Total | One restaurant can have multiple reservations |
| Customer — Place — Order | 1 : N | Customer: Total, Order: Total | One customer can place multiple orders |
| Restaurant — Offers — Menu Item | 1 : N | Restaurant: Total, Menu Item: Total | One restaurant can offer multiple menu items |
| Order — Receive — Restaurant | N : 1 | Order: Total, Restaurant: Total | Many orders can be received by one restaurant |
| Order — Associated With — Delivery | 1 : 1 | Order: Total, Delivery: Total | Each order is associated with one delivery |
| Restaurant — Receive — Order | 1 : N | Restaurant: Total, Order: Total | One restaurant can receive multiple orders |

### Assumptions

- Each customer is uniquely identified by a unique `C-ID`.
- Each restaurant is uniquely identified by a unique `ID`.
- Each reservation is uniquely identified by a unique `R-ID`.
- Each order is uniquely identified by a unique `O-ID`.
- Each menu item is uniquely identified by a unique `M-ID`.
- Each delivery is uniquely identified by a unique `D-ID`.
- One customer can make multiple reservations, while each reservation belongs to one customer.
- One restaurant can have multiple reservations, while each reservation is made for one restaurant.
- One customer can place multiple orders, while each order is placed by one customer.
- One restaurant can offer multiple menu items, while each menu item belongs to one restaurant.
- A restaurant can receive multiple orders, while each order is associated with one restaurant.
- Each order is associated with one delivery, and each delivery belongs to one order.
- The `Date` attribute in the `Reservation` entity stores the reservation date.
- The `Amount` and `Date` attributes in the `Order` entity store the total order amount and order date.
- The `Status` attribute in the `Delivery` entity represents the current delivery status.
---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**

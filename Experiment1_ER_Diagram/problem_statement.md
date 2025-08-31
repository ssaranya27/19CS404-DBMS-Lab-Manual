# ER Diagram Workshop – Submission Template

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

<img width="1423" height="670" alt="image" src="https://github.com/user-attachments/assets/914f1ed8-4a93-46af-8909-d0f55b70a534" />

### **Entities and Attributes**

| Entity                | Attributes (PK, FK)                                             | Notes                                     |
| --------------------- | --------------------------------------------------------------- | ----------------------------------------- |
| **Members**           | Member\_ID (PK), Name, MembershipType, Start\_Date              | Stores all member details.                |
| **Program**           | Program\_ID (PK), Program\_Name                                 | Fitness programs like Yoga, Zumba.        |
| **Trainers**          | Trainer\_ID (PK), Name, Speciality                              | Trainers assigned to programs.            |
| **Personal\_Session** | Session\_ID (PK), Date, Time, Member\_ID (FK), Trainer\_ID (FK) | Booked by members with trainers.          |
| **Attendance**        | Attendance\_ID (PK), Status, Session\_ID (FK), Member\_ID (FK)  | Tracks member attendance for sessions.    |
| **Payment**           | Payment\_ID (PK), Date, Amount, Type, Member\_ID (FK)           | Payments made for membership or sessions. |

---

### **Relationships and Constraints**

| Relationship                                     | Cardinality | Participation | Notes                                                                         |
| ------------------------------------------------ | ----------- | ------------- | ----------------------------------------------------------------------------- |
| **Members – Program (enrolls)**                  | M\:N        | Optional      | A member can join many programs, a program can have many members.             |
| **Trainers – Program (conducts)**                | M\:N        | Mandatory     | Programs may have multiple trainers, a trainer can conduct multiple programs. |
| **Members – Personal\_Session (books session)**  | M\:N        | Optional      | Members can book multiple personal sessions with trainers.                    |
| **Trainers – Personal\_Session**                 | 1\:M        | Mandatory     | A trainer can conduct many sessions, each session has one trainer.            |
| **Personal\_Session – Attendance (recorded as)** | 1\:M        | Mandatory     | Each session has many attendance records.                                     |
| **Members – Payment (makes)**                    | 1\:M        | Mandatory     | Each member can make multiple payments.                                       |

---

### **Assumptions**

* A member may or may not enroll in programs (optional participation).
* A program must have at least one trainer.
* Personal sessions are optional; not every member books one.
* Attendance is recorded only for scheduled sessions.
* Payments are mandatory for memberships and personal sessions.

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

<img width="1265" height="722" alt="image" src="https://github.com/user-attachments/assets/29cf7e74-0eb7-4190-8de5-b6d47cd97e31" />

### **Entities and Attributes**

| Entity                  | Attributes (PK, FK)                                                     | Notes                                     |
| ----------------------- | ----------------------------------------------------------------------- | ----------------------------------------- |
| **Member**              | Member\_ID (PK), Name, Contact, Join\_Date                              | Stores library member details.            |
| **Book**                | Book\_ID (PK), Title, Author, Category                                  | Information about books.                  |
| **Loan**                | Loan\_ID (PK), Loan\_Date, Return\_Date, Book\_ID (FK), Member\_ID (FK) | Tracks book borrowings.                   |
| **Event**               | Event\_ID (PK), Name, Date, Status                                      | Cultural/library events.                  |
| **Event\_Registration** | Registration\_ID (PK), Event\_ID (FK), Member\_ID (FK)                  | Tracks which members register for events. |
| **Speaker**             | Speaker\_ID (PK), Name, Expertise                                       | Speakers/authors for events.              |
| **Room**                | Room\_ID (PK), Room\_Name, Capacity                                     | Rooms for events or study.                |
| **Fine**                | Fine\_ID (PK), Amount, Status, Loan\_ID (FK), Member\_ID (FK)           | Fine for overdue returns.                 |

---

### **Relationships and Constraints**

| Relationship                                    | Cardinality     | Participation | Notes                                                                      |
| ----------------------------------------------- | --------------- | ------------- | -------------------------------------------------------------------------- |
| **Member – Loan (borrows)**                     | 1\:M            | Mandatory     | A member can borrow many books; each loan belongs to one member.           |
| **Book – Loan (can be loaned many times)**      | 1\:M            | Mandatory     | A book can be loaned multiple times; each loan relates to one book.        |
| **Member – Fine (pays)**                        | 1\:M            | Optional      | Only members with late returns pay fines.                                  |
| **Loan – Fine**                                 | 1:1 or 1\:M     | Optional      | A loan may result in zero or more fines.                                   |
| **Member – Event\_Registration (register via)** | 1\:M            | Optional      | Members can register for many events.                                      |
| **Event – Event\_Registration**                 | 1\:M            | Mandatory     | Each registration belongs to one event.                                    |
| **Event – Speaker (has)**                       | M\:N            | Mandatory     | An event can have multiple speakers; a speaker can attend multiple events. |
| **Event – Room (books)**                        | 1:1             | Mandatory     | Each event is held in one room.                                            |
| **Member – Book (borrows through Loan)**        | M\:N (via Loan) | Mandatory     | Covered through associative entity Loan.                                   |

---

### **Assumptions**

* A book can only be borrowed if it is available.
* A fine is only issued if a return date is missed.
* A member may attend events without borrowing books (two independent functions).
* Each event must be assigned a room and at least one speaker.
* One event cannot span multiple rooms (simplified).
* Each registration belongs to one event and one member only.

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

<img width="954" height="724" alt="image" src="https://github.com/user-attachments/assets/ef2584ee-4d05-4a34-b8cb-c4dd9ea93507" />

### **Entities and Attributes**

| Entity       | Attributes (PK, FK)                                                          | Notes                                                                  |
| ------------ | ---------------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| **Customer** | Customer\_ID (PK), Name, Phone\_No                                           | Stores customer details.                                               |
| **Waiter**   | Waiter\_ID (PK), Name                                                        | Waiters serving customers.                                             |
| **Order**    | Order\_ID / Bill\_ID (PK), Total\_Amount, Customer\_ID (FK), Waiter\_ID (FK) | Represents customer orders and billing.                                |
| **Dish**     | Dish\_ID (PK), Name, Category\_No (FK)                                       | Individual dishes served.                                              |
| **Category** | Category\_No (PK), Category\_Name                                            | Groups dishes into categories (e.g., Appetizer, Main Course, Dessert). |

---

### **Relationships and Constraints**

| Relationship                          | Cardinality | Participation | Notes                                                                      |
| ------------------------------------- | ----------- | ------------- | -------------------------------------------------------------------------- |
| **Customer – Order (places)**         | 1\:M        | Mandatory     | A customer can place many orders; each order belongs to one customer.      |
| **Waiter – Order (registers/serves)** | 1\:M        | Mandatory     | A waiter can serve many orders; each order is served by one waiter.        |
| **Order – Dish (contains)**           | M\:N        | Mandatory     | An order can contain multiple dishes; each dish can appear in many orders. |
| **Dish – Category (belongs to)**      | M:1         | Mandatory     | Each dish must belong to one category.                                     |
| **Order – Bill (generates)**          | 1:1         | Mandatory     | Each order generates one bill (Bill\_ID).                                  |

---

### **Assumptions**

* Each order is associated with **one customer and one waiter** only.
* A bill is generated for every order; no unpaid/temporary orders are stored.
* Dishes are predefined in the system and always belong to exactly one category.
* A customer can place multiple orders over time.
* A waiter can handle multiple customers/orders at the same time.
* The total amount is calculated based on the dishes included in the order.

---
### **Result**

Entities, their attributes, and the relationships between them are clearly represented with correct cardinalities.

# P01

|player name|team name|stadium|league|goals|assists|
|---|---|---|----|--:|--:|
|Lionel Messi|Barcelona| Camp Nou| La Liga| 8| 4|
|Luis Suarez| Barcelona| Camp Nou| La Liga| 6| 0|
|Cristiano Ronaldo| Juventus| Allianz| Serie A| 5| 1|
|...|...|...|...|...|...|

Say Barcelona builds a brand new stadium and we want to update the table to reflect this change.   
Let’s say there are 30 players in our table that have their team name as Barcelona.  
Describe what could be a potential problem or why this might be inefficient.  
Describe how you might go about fixing the problem you described above.

--- 
# P02  
File `StudentTakenCourseView.csv` *(it can be opened  with Excel, Google Spreadsheet)*.  
Show each step  
Detect possible functional dependencies, and draw ERD diagram after decomposition

---
** Copied from **it.uu.se**  
# P03

**P03.1**  
Specify all functional dependencies without redundancies for each table of the library database. Then state which normal form (1NF, 2NF, 3NF or BCNF) each of the existing tables is, and why.  
**P03.2**  
For each table that doesn’t fulfill the requirements for BCNF, explain the problems that this lack of normalization has and their potential consequences. Give some examples.  
**P03.3**  
Design a new database, with different tables, where all the tables fulfill BCNF without losing any information.  
Hints:
* consider dates as atomic (there is a type ‘date’ in SQL);
* assume that there is one telephone number per address;
* you can choose any of the approaches for relational database design: top-down (starting with ER modeling) or bottom-up (starting with specification of all functional
dependencies and applying a normalization algorithm).

There are three tables:  
* A table called BOOK, which contains data about the books. It has the attributes *TitleNr* (a number that this library assigns), *ISBN*, *CopyNr* (which is used to separate different copies of the same book), *Title*, *PublYear*, *Author*, and *AuthorNat*.   
The primary key consists of TitleNr, CopyNr and Author. An alternative key is formed by ISBN, CopyNr and Author.
* A table called CUSTOMER, which contains data about the persons who can borrow books.   
It has the attributes *CustomerNr* (a unique number identifying a person, assigned by the library), *PersonNr* (which is a unique number identifying a person, assigned by the Swedish state), *Name*, *Address*, *Tel*, and *NrBooks* (the number of books that this person has borrowed at the moment). *CustomerNr* is the primary key. *PersonNr* is an alternative key.  
* A table called *LOAN*, where the loans are stored. It has the attributes *TitleNr*, *CopyNr*, *CustomerNr*, *Date* (which is the date when the book was borrowed), and *BorrowerName* (which is the name of the customer who borrowed the book). The primary key consists of
TitleNr and CopyNr. 

Table data
---
## BOOK

| TitleNr | ISBN | CopyNr | Title | PublYear | Author | AuthorNat |
|---------|----------|--------|--------------|----------|--------------|-----------|
| 1 |0071148108| 1 | Database | 1997 | Silberschatz | USA |
| 1 |0071148108| 1 | Database | 1997 | Korth | USA |
| 1 |0071148108| 1 | Database | 1997 | Sudarshan | India |
| 2 |0805317538| 1 | Fundamentals | 1994 | Elmasri | USA |
| 2 |0805317538| 1 | Fundamentals | 1994 | Navathe | USA |
| 2 |0805317538| 2 | Fundamentals | 1994 | Elmasri | USA |
| 2 |0805317538| 2 | Fundamentals | 1994 | Navathe | USA |
| 3 |0198642253| 1 | Mord | 1995 | Guillou | Sweden |
| 3 |0198642253| 2 | Mord | 1995 | Guillou | Sweden |
| 4 |3411021764| 1 | Våld | 1998 | Guillou | Sweden |


## CUSTOMER

| CustomerNr | PersonNr | Name | Address | Tel | NrBooks |
|------------|----------|----------------|---------|------|---------|
| 1 |6312111658| Padron-McCarthy| Vägen 7 |282677| 1 |
| 2 |4403149901| Silberschatz | Gatan 6 |146000| 1 |
| 3 |4010229910| Elmasri | Gatan 8 |241000| 1 |
| 4 |4501129921| Schwarzenegger | Vägen 3 |174590| 0 |


## LOAN
| TitleNr | CopyNr | CustomerNr | Date | BorrowerName |
|---------|--------|------------|------|----------------|
| 1 | 1 | 3 |7/1 98| Elmasri |
| 3 | 2 | 1 |1/9 98| Padron-McCarthy|
| 2 | 1 | 2 |7/1 98| Silberschatz |
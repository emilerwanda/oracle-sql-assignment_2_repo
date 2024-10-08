# oracle-sql-assignment_2
this repo is for assignment 2, ISHIMWE EMILE 26160;

## LIBRARY MANAGEMENT SYSTEM

i designed database system that tracks the activity of the library action, between books, author, borrower and the loans, i used sqldeveloper in default connection of system. 

## TABLES

i created 4 tables named; Authors, Books, Borrowers and Loans respectively as shown in below screenshoots.
### table author
```sql
   CREATE TABLE AUTHORS 
   (	AUTHORID NUMBER(*,0), 
	AUTHORNAME VARCHAR2(20 BYTE), 
	BITHDATE DATE
   );

Insert into AUTHORS (AUTHORID,AUTHORNAME,BITHDATE) values (1,'ishimwe emile',to_date('29-AUG-03','DD-MON-RR'));
Insert into AUTHORS (AUTHORID,AUTHORNAME,BITHDATE) values (2,'umuhire leatitia',to_date('12-AUG-04','DD-MON-RR'));
Insert into AUTHORS (AUTHORID,AUTHORNAME,BITHDATE) values (3,'benitha elyse',to_date('12-SEP-05','DD-MON-RR'));
Insert into AUTHORS (AUTHORID,AUTHORNAME,BITHDATE) values (4,'sammy samuella',to_date('12-DEC-06','DD-MON-RR'));
```
![author](https://github.com/user-attachments/assets/c693201b-8d62-40bc-aa8e-c8ba3c30dd7a)
### table Books
```sql
      CREATE TABLE BOOKS 
   (	BOOKID NUMBER(*,0), 
	TITLE VARCHAR2(20 BYTE), 
	GENRE VARCHAR2(15 BYTE), 
	AUTHORID NUMBER(*,0)
   );

   
Insert into BOOKS (BOOKID,TITLE,GENRE,AUTHORID) values (201,'billioners','inspiration',1);
Insert into BOOKS (BOOKID,TITLE,GENRE,AUTHORID) values (202,'CookWithMe','teaching',2);
Insert into BOOKS (BOOKID,TITLE,GENRE,AUTHORID) values (203,'cleverness','teaching',3);
Insert into BOOKS (BOOKID,TITLE,GENRE,AUTHORID) values (204,'babying','kids',4);
Insert into BOOKS (BOOKID,TITLE,GENRE,AUTHORID) values (205,'become rich','inspiration',1);
Insert into BOOKS (BOOKID,TITLE,GENRE,AUTHORID) values (206,'butterfly','kids',4);
```
![books](https://github.com/user-attachments/assets/970d2201-8961-4075-a120-092d139113a3)
### table Borrower
```sql
CREATE TABLE BORROWERS 
   (	BORROWERID NUMBER(*,0), 
	BORROWERNAME VARCHAR2(20 BYTE), 
	CONTACTINFO VARCHAR2(20 BYTE)
   );

Insert into BORROWERS (BORROWERID,BORROWERNAME,CONTACTINFO) values (301,'kazungu','+250789990349');
Insert into BORROWERS (BORROWERID,BORROWERNAME,CONTACTINFO) values (302,'mahoro','+250789000038');
Insert into BORROWERS (BORROWERID,BORROWERNAME,CONTACTINFO) values (303,'philbert','+25078444038');
Insert into BORROWERS (BORROWERID,BORROWERNAME,CONTACTINFO) values (304,'sam','+250784743767');
Insert into BORROWERS (BORROWERID,BORROWERNAME,CONTACTINFO) values (305,'eddy','+250784746767');
Insert into BORROWERS (BORROWERID,BORROWERNAME,CONTACTINFO) values (306,'eric','+250784745555');
```
![borrower](https://github.com/user-attachments/assets/de2482c8-2834-4e6f-a9f5-f51f74455af0)
### table Loans
```sql
 CREATE TABLE LOANS 
   (	LOANID number(*,0), 
	BOOKID number(*,0), 
	BORROWERID number(*,0), 
	LOANDATE DATE, 
	RETURNDATE DATE, 
	AUTHORERID NUMBER(*,0)
   );

   Insert into LOANS  values (401,201,301,to_date('10-SEP-24','DD-MON-RR'),to_date('10-OCT-24','DD-MON-RR'),1);
Insert into LOANS values (402,202,306,to_date('15-SEP-24','DD-MON-RR'),to_date('15-OCT-24','DD-MON-RR'),2);
Insert into LOANS values (403,203,305,to_date('20-SEP-24','DD-MON-RR'),to_date('20-OCT-24','DD-MON-RR'),3);
Insert into LOANS  values (404,201,306,to_date('20-SEP-24','DD-MON-RR'),to_date('20-OCT-24','DD-MON-RR'),1);
Insert into LOANS  values (405,201,301,to_date('20-SEP-24','DD-MON-RR'),to_date('20-OCT-24','DD-MON-RR'),1);
```

![loans](https://github.com/user-attachments/assets/c12602cf-db52-406f-a97a-b6a7f093bac3)

### <u>RELATIONSHIP</u>

   they have different relationships each other(one-to-one, one-to-many and many-to-many) as shown below;
      ![relotionship](https://github.com/user-attachments/assets/7e4fb53b-f08a-44e0-b4eb-8ffffd2851d6)


## Querry Commands

   i also executed some query commands to table BOOKS (select, insert, delete, update, joins and subqueries);
 
   ### Select
   ```sql
         Select
            bookid, title, genre, authorid
            from books ;
```

   <img width="959" alt="Selecting" src="https://github.com/user-attachments/assets/aa720a23-091c-4069-b799-fbd5c4d73194">

 ### Insert
 
   ```sql
           
           INSERT INTO BOOKS VALUES ( 
         '207','WorldNowDays,'teaching','2') ;
```

<img width="959" alt="Inserting" src="https://github.com/user-attachments/assets/ea34b2ac-a939-433a-a0e1-f62e017529c4">

###   Update

 ```sql
    
    Update books
    set title='millioners'
    where title='billioners' ;
   ```
   <img width="959" alt="update" src="https://github.com/user-attachments/assets/b368e07c-12b7-4af6-93b6-86ab875bd63f">

   ### Delete
  
   ```sql
          Delete from books where
         bookid ='206'
         AND title='butterfly'
         AND genre='kids'
         AND authorid = '4';
```
   <img width="908" alt="delete" src="https://github.com/user-attachments/assets/7856c6e5-f312-415e-9a12-3baf251d4792">

### Join

   ```sql
         Select books.title, books.genre
         From books
         INNER JOIN loans ON books.bookid = loans.bookid;
```
   
   ![inner_join](https://github.com/user-attachments/assets/ab61601b-4c06-45d6-b481-7f18708f420c)
  
   ### Subquery
   ```sql
         Select Borrowerid, BorrowerName
         From borrowers
         where Borrowerid IN (Select borrowerid from loans where borrowerid = 306);
```
   ![subquery](https://github.com/user-attachments/assets/c8d66fec-9c89-4cf2-bb42-ca576a623d15)

   ## Problem statement
as i were doing all of this i faced challenge of limited knowledge and skills in database management but i tried as best as i can using different resources like in citation
  
   
   ## Citation
    . geeksforgeeks site; (https://www.geeksforgeeks.org/sql-ddl-dql-dml-dcl-tcl-commands/)
    . youtube channel; https://youtu.be/kbKty5ZVKMY


















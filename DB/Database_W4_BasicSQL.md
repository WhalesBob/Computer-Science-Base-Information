# Database_W4. Basic SQL

+ Structued Query Language(SQL)
  - Declarative(서술문처럼 쓴다)
  - DDL(Data Definition Language) 과 DML(Data Manipulation Language) 를 포함한다.
  - 거의 표준이다.

## Implementing the Design Process using DML, DDL, DCL, TCL

|Type|Commands|Description|
|-------|-----|----------|
|DML(Data Manipulation Language)|SELECT|정보검색|
||INSERT,UPDATE,DELETE|Data를 DB에서 수정한다|
|DDL(Data Definition Language)|CREATE,ALTER,DROP,RENAME,TRUNCATE|schama 나 제약조건을 만들거나 수정함.|
|DCL(Data Control Language)|GRANT, REVOKE|DB 접근권할을 유저에게서? 유저에게로? 바꾼다|
|TCL(Transaction Control Language|COMMIT,ROLLBACK,SAVEPOINT|데이터 수정의 logical flow를 컨트롤한다|

# MySQL | The CREATE Statement

+ Data 정의를 위해 사용하는 기본적인 SQL 명령어
  - Database, schema, table, view, assertion, trigger 등을 다 만들수 있다.

+ MySQL 에서는 DB 나 Schema(table) 를 CREATE 를 사용해서 만들 수 있다

+ 이럴 때 쓴다
  - 이름과, Attribute(속성) 과, 데이터 타입을 줄때
  - 제약조건 명시 : Attribute, 튜플, 키, 참조무결성(외래키)

+ Syntax 
```
CREATE TABLE [IF NOT EXISTS] table_name (
  (create_definition,....)
  [table_options]
  [partition_options]);
```

+ Example
```
CREATE TABLE EMPLOYESS(
    Fname VARCHAR(100) NOT NULL,
    Minit VARCHAR(100),
    Lname VARCHAR(100) NOT NULL,
    SSN CHAR(9) NOT NULL,
    Bdate DATE,
    Address VARCHAR(255),
    Sex CHAR,
    Salary DECIMAL(10,2),
    Super_ssn CHAR(9),
    Dno INT,
    PRIMARY KEY (SSN)
  );
```

+ CREATE TABLE Command
  - 기본적인 Table 만들때
    - Relation(테이블) 과 튜플이 실제적으로 만들어져서 DBMS 에 저장된다.
  - 가상 Relation(View)
    - CREATE VIEW 문을 통해서 만들어진다. 물리적으로 어떤 파일이 만들어지는게 아니다.

## Specifying Domains or UDTs(User Data Types)

+ 몇몇 DBMS 프로그램에서는, 유저가 자기만의 Domain 과 User Defined Types(UDT) 정의할 수도 있다.
+ 하지만, MySQL은 그런거없다

+ Domain
  -  이름을 Attribute 사항과 함께 쓴다
  -  여러 Attribute 에 사용되는 Domain 의 데이터 타입을 쉽게 바꿀 수 있다.
    - 그냥 그 Domain 을 (ex) VARCHAR 대신에 써놓고, 나중에 Domain 쪽 하나만 바꿔 놓으면 한방에 변경가능하다는 의미.
  
  - 그 Schema 의 가독성을 높여준다
  - EX) CREATE DOMAIN __SSN_TYPE__ AS CHAR(9)

+ TYPE
  - User Defined Types(UDTs) 는 객체지향 Application 에서 지원된다.
  ```
  CREATE TYPE PERSON AS OBJECT (
    Name  VARCHAR(30),
    Ssn   VARCHAR(9)
    );
  ```
  
### MySQL Built-in Data Types

<img src="images/DB4_1.png"/>

## Specifying Constraints in SQL

+ SQL 에서 제약조건 설정하기

+ Basic Constraints(기본 제약조건)
  - Key Constraint : primary key는 고유해야 한다 
  - Entity Integrity Constraint : Primary Key는 NULL 일수 없다
  - Referential Integrity Constraints : 외래 키는 반드시 기존에 있는 다른쪽의 Primary Key를 참조해야 한다.

+ Attribute 의 Default 값
  - DEFAULT <value>
  - 특정 Attribute 에는 NOT NULL 과 같이, NULL을 허용하지 않을 수도 있다.
  
+ CHECK 문
  - Table을 만들 때 제약조건을 더해서 넣을 수 있다.
  - ex ) Dnumber INT NOT NULL CHECK (Dnumber > 0 AND Dnumber < 21)
                                                              
## Specifying Keys

+ Key 설정하기

+ PRIMARY KEY 절
  - 하나 혹은 더 많은 Attribute 를, 해당 Relation 에서 Primary Key로 설정할 수 있다.
  - ex ) Dnumber INT PRIMARY KEY;

+ UNIQUE 절
  - 대체할 수 있는 secondary key를 설정한다.
    - Relational Model 에서 후보키인 것들을 설정한다 
                                                                  
  - ex ) Dname VARCHAR(15) UNIQUE;
                                                                                                                                   
+ FOREIGN KEY 절
  - 기본적으로 세팅된 Operation : 위반조건을 어겼을 때 업데이트를 막는 것
  - 참조 Triggered Action 절 붙이기
    - SET NULL, CASCADE, SET DEFAULT 중 하나 쓸수 있다
    - SET NULL 과 SET DEFAULT 는 DBMS 에서 DELETE와 ON UPDATE 할 때 처리된다.
    - CASCADE 옵션은 "Relationship" Relation 에 맞는 옵션이다.
    
## Table 만들고, 세팅하기


#### 선언하기
```
CREATE TABLE DEPARTMENT(
  Dname VARCHAR(15) NOT NULL,
  Dnumber INT NOT NULL,
  Mgr_ssn CHAR(9) DEFAULT '888665555',
  Mgr_start_date DATE,
  PRIMARY KEY (Dnumber),
  UNIQUE (Dname)
  );
```

#### Foreign Key 넣기

```
ALTER TABLE DEPARTMENT ADD FOREIGN KEY (Mgr_ssn) REFERENCES EMPLOYEE (Ssn) 
ON DELETE SET NULL ON UPDATE CASCADE
```


                                                                  
                                                                  
                                                                  

# Database_W5. SQL 2

+ 비교를 위한 NULL 값

<img src="images/DB5_1.png"/>

+ SQL 은 Attribute 값이 NULL 인지 아닌지 체크한다 
  - IS or IS NOT NULL
  - WHERE Super_Ssn = NULL 하면 안된다!
  
```
SELECT Fname,Lname FROM EMPLOYEE WHERE Super_Ssn IS NULL;
```

+ SQL 에서, NULL 은 어떤것과도 같지 않다. 심지어 다른 NULL 과도 equal 관계가 아니다.
+ True, False, unknown(NULL 을 support 하기 위함) 이렇게 3개가 있다.

<img src="images/DB5_2.png"/>

```
SELECT Fname, Lname FROM EMPLOYEE WHERE Super_Ssn = NULL;
```

+ 위 Query 문에 대한 설명
  - WHERE 문에 대한 결과가 항상 unknown 이다. 그래서 모든 row를 다 reject 하는 것이다.
  - 항상 WHERE 문이나 HAVING 문은 TRUE 일 때 그 결과를 띄워준다. unknown 이면 안된다.

+ Nested Query
  - 쿼리문 내부의 쿼리문
  - UNION 이랑은 다르다

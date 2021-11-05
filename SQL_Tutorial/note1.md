# 1. Select 
- 테이블에서 정보를 가져오기 위해 사용
## 기본 구조
    SELECT 칼럼명(열), 칼럼명, 
    FROM 테이블명 
    WHERE 조건식 ;
    
### 1)SELECT : 원하는 열(칼럼)을 선택해 데이터를 가져온다. 무엇을
### 2) FROM : SELECT에서 선택한 열을 어느 테이블에서 가져올지 결정. 어디에서
### 3) WHERE : 검색 조건을 통해 원하는 데이터만 가져올 수 있게 해준다. 어떤 조건  
* WHERE 부분은 생략 가능 (=조건이 없다, 전체 데이터를 가져 옴)
    


### * 전체 열을 보고싶다면 ?
    SELECT * FROM 을 통해 전체 열 확인 가능

# 2. Select Distinct
-  SQL중복제거 키워드 

## 기본 구조
    SELECT DISTINCT 칼럼명 FROM 테이블명 ;
- 해당 테이블의 특정 열의 내용들을 중복되지않고 고유한 자료들만으로 결과가 나온다.

### * 반환된 자료들의 수량을 확인하려면? 
     SELECT COUNT(DISTINCT 칼럼명) FROM 테이블명 ; 



# 3. Where

- 특정 조건에 부합하는 내용만 조회하고 싶을 때 사용하는 키워드 

## 기본 구조

    SELECT 칼럼명(열), 칼럼명, 
    FROM 테이블명 
    WHERE 조건, 조건, ... ;
## 예제1 
Customers테이블에서 Country 열의 내용이 'Mexico'인 것만 조회하고 싶을 때,

    SELECT * FROM Customers
    WHERE Country='Mexico'; 

## 조건연산자
- = 같다
- <>, != 같지 않다. 
- !< ~보다 작지 않다. 
- BETWEEN AND 두개의 특정한 값 사이
- IS NULL 값이 NULL 이다.
- LIKE ~ 특정 패턴과 일치하다. 

- IN 조건문의 값을 여러개로 설정

## 예제2 : LIKE 
- s로 시작하는 모든 문자열 데이터 

        WHERE Country LIKE 's%'
- s로 시작하는 3자리의 문자열 데이터

        WHERE Country LIKE 's__'
## 예제3 : IN 
- Country 열의 내용이 'Mexico'와 'Korea'인 것만을 조회하고 싶을 때,

        WHERE Country IN ('Mexico', 'Korea'); 

# 4. And, Or, Not 
- WHERE 절에서 사용되는 연산자 

 1. AND 
 - AND 연산자로 연결된 여러 조건들이 모두 참인 것들을 조회

 2. OR
 - OR 연산자로 연결된 여러 조건들 중 하나 이상의 조건이 참인 것들을 조회 

 3. NOT 
 - NOT 연산자 뒤의 조건이 참이 아닌 경우의 것들을 조회


# 5. Order by 
- 데이터들을 오름, 내림차순으로 정렬하는 키워드
- Order by는 기본적으로 오름차순으로 정렬을 한다

## 기본 구조

        SELECT column1, column2, ...
        FROM table_name
        ORDER BY column1, column2, ... ASC|DESC;
## 예제1 : 내림차순

        SELECT * FROM Customers
        ORDER BY Country DESC;

## 예제2 : 두개 이상의 열 정렬 

- Country열을 오름 차순으로 정렬하고, Country의 값이 같을 경우 CustomerName을 기준으로 정렬한다. 

        SELECT * FROM Customers
        ORDER BY Country, CustomerName;

## 예제 3 : 두개 이상의 열 정렬
- Country 열은 오름차순으로, CustomerName열을 내림차순으로 정렬한다. 

        SELECT * FROM Customers
        ORDER BY Country ASC, CustomerName DESC;

# 6. Insert into 
- 테이블에 새로운 자료를 추가하는 키워드

## 기본구조
-  특정 열에 데이터를 추가하고 싶을 때 

        INSERT INTO table_name (column1, column2, column3, ...)
        VALUES (value1, value2, value3, ...);
-  모든 열에 데이터를 추가하고 싶을 때 (한 행 전체 추가)

        INSERT INTO table_name
        VALUES (value1, value2, value3, ...);

## 예제

    INSERT INTO Customers (CustomerName, ContactName, Address, City, PostalCode, Country)
    VALUES ('Cardinal', 'Tom B. Erichsen', 'Skagen 21', 'Stavanger', '4006', 'Norway');


<img src="https://user-images.githubusercontent.com/63465350/139407500-099088c3-a9bb-48c6-9495-8bbe808c62dd.png" heght="300">



# 7. NULL Values
- 아무 값이 없는 것을 의미함 
- =, <, or <> 와 같은 비교 연산자로 NULL인지 확인할 수 없음
- IS NULL, IS NOT NULL 연산자 사용 

## 기본 구조

    SELECT column_names
    FROM table_name
    WHERE column_name IS NULL; 

# 8. Update 
- 기존 테이블에 있는 값을 수정하는 키워드

## 기본 구조
- 원하는 테이블의 특정 조건에 부합하는 열의 값을 수정 

        UPDATE table_name
        SET column1 = value1, column2 = value2, ...
        WHERE condition;

## 예제 

    UPDATE Customers
    SET ContactName = 'Alfred Schmidt', City= 'Frankfurt'
    WHERE CustomerID = 1;


# 9. Delete
- 기존 테이블에 있는 값을 삭제하는 키워드

## 기본 구조
- 원하는 테이블의 특정조건에 부합하는 부분을 삭제 

        DELETE FROM table_name WHERE condition;

## 예제1     
- 테이블에서 조건에 부합하는 행 전체를 삭제

        DELETE FROM Customers WHERE CustomerName='Alfreds Futterkiste';

## 예제 2 : 모든 데이터 삭제
- Customers 라는 테이블의 모든 데이터 삭제

        DELETE FROM Customers;


# 10. Select Top
- 많은 데이터들 중 특정 몇개의 데이터만 출력하고 싶을 때 사용하는 키워드
- for SQL server

## 기본구조

        SELECT TOP 개수 or 퍼센트

## 예제
        SELECT TOP 3 * FROM Customer

        SELECT TOP 50 PERCENT * FROM Customer

# 11. Limit 
- 많은 데이터들 중 특정 몇개의 데이터만 출력하고 싶을 때 사용하는 키워드
- Select top과 같은 기능
- for mySQL 

## 기본 구조

        SELECT * FROM Customers
        LIMIT 개수;

# 12. Min() Max()
- 선택된 행에서 최소, 최대 값을 반환해주는 함수 

## 기본 구조

        SELECT MIN(column_name)
        FROM table_name
        WHERE condition;

        SELECT MAX(column_name)
        FROM table_name
        WHERE condition;

## 예제 
- 가장 저렴한 물건의 가격을 "SmallestPrice"라는 이름으로 가져올 때
        
        SELECT MIN(Price) AS SmallestPrice
        FROM Products; 

<img src="https://user-images.githubusercontent.com/63465350/139871167-acbd3b8a-4c9c-46df-9a88-8bf41b00ff61.png" heght="300">


# 13. COUNT()
- row(열)의 갯수를 세서 반환해주는 함수 
## 기본 형식

        SELECT COUNT(column_name)
        FROM table_name
        WHERE condition;                

# 14. AVG()
- 숫자로 이루어진 행의 평균을 반환해주는 함수
## 기본 형식 
        SELECT AVG(column_name)
        FROM table_name
        WHERE condition;

# 15. SUM()
- 숫자로 이루어진 행의 합을 반환해주는 함수

## 기본 형식
        SELECT SUM(column_name)
        FROM table_name
        WHERE condition;
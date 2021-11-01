# SQL 2주차

1. JOIN 
- 두 개 이상의 테이블에서 컬럼을 합칠 때 사용(based on a related column between them)
~~~
SELECT table1.id, table2.column1, table1.column1
FROM table1
oo JOIN(Type of join) table 2 on table1.id = table2.id
~~~

  * INNER JOIN : 왼쪽과 오른쪽의 교집합만 반환 
    ``` 
    SELECT Orders.OrderID, Customers.CustomerName, Orders.OrderDate
    FROM Orders
    INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID
    ```
  * OUTER JOIN : 왼쪽과 오른쪽에 동일한 값이 없는 행도 반환
    
  * LEFT (OUTER) JOIN : 왼쪽의 모든 데이터 + 오른쪽의 교집합 데이터
    ~~~
    SELECT Customers.CustomerName, Orders.OrderID
    FROM Customers
    LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID
    ~~~
    
  * RIGHT (OUTER) JOIN : 오른쪽의 모든 데이터 + 왼쪽의 교집합 데이터
    ~~~
    SELECT Customers.CustomerName, Orders.OrderID
    FROM Customers
    RIGHT JOIN Orders ON Customers.CustomerID = Orders.CustomerID
    ~~~
   
  * FULL (OUTER) JOIN : 왼쪽과 오른쪽 데이터의 합집합 반환
    ~~~
    SELECT Customers.CustomerName, Orders.OrderID
    FROM Customers
    FULL OUTER JOIN Orders ON Customers.CustomerID=Orders.CustomerID
    ~~~
    
  * SELF JOIN : 자기 스스로를 결합시킴 -> 같은 테이블을 사용하기 때문에 반드시 별칭을 지어줘야 함
    ~~~
    SELECT A.CustomerName AS CustomerName1, B.CustomerName AS CustomerName2, A.City
    FROM Customers A, Customers B
    ~~~
    
  * CROSS JOIN : 특정 기준 없이 두 테이블 간의 모든 경우의 수에 대한 결합 변환 -> on 절 없음
    ~~~
    SELECT Customers.CustomerName, Orders.OrderDate
    FROM Customers
    CROSS JOIN Orders 
    ~~~
    
  * NATURAL JOIN : 두 테이블에 동일한 이름, 타입이 있으면 자동으로 결합한 결과 반환 -> 동일한 컬럼 select 되어야 하지만 
    ~~~
    SELECT deptno(부서 코드), empno(사원 번호), ename(사원 이름), dname(부서명)
    FROM t_emp
    NATURAL JOIN t_dept
    # 두 테이블에 모두 있는 deptno로 조인이 됨
    ~~~
    
 
2. Group by 
- 같은 값을 가진 컬럼을 그룹해서 요약해주는 쿼리
- 주로 aggreate 함수와 함께 쓰임(`COUNT(), MAX(), MIN(), SUM(), AVG()`)
~~~
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
ORDER BY column_name(s);
~~~
  - 예시
     ~~~
     SELECT COUNT(CustomerID), Country
     FROM Customers
     GROUP BY Country;
     ~~~

3. Having
- 조건절이지만 `where`와 달리 aggreated function과 함께 쓰임
- (그럼 항상 `group by`와 함께 쓰이나?)
~~~
SELECT column_name(s)
FROM table_name
WHERE condition
GROUP BY column_name(s)
HAVING condition
ORDER BY column_name(s);
~~~

  - 예시
    ~~~
    SELECT COUNT(CustomerID), Country
    FROM Customers
    GROUP BY Country
    HAVING COUNT(CustomerID) > 5;
    ~~~

집합연산자와 서브쿼리 = Union연산

집합연산자와 서브쿼리 = UnionAll연산

집합연산자와 서브쿼리 = intersect연산

집합연산자와 서브쿼리 = Except연산

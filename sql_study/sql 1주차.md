# sql 1주차

### 1. select \rightarrow 테이블 조회 시 사용
  
* 기본
  ```
    select 컬럼 from 테이블
    where 조건
  ```
* 전체 열 반환
  ```
    select * from 테이블
  ```



### 2. orderby -> 결과 정렬
  asc 오름차순 desc 내림차순

    select 컬럼 from 테이블
    orderby 컬럼 [asc/desc]

    

### 3. select distinct -> 중복 제거
* 지정된 컬럼에서 고유한 자료만 추출
  ```
    select distinct 컬럼
    from 테이블
   ```
* 응용
  * 테이블의 date에서 고유한 날짜만 추출
    ```
    select distinct date(날짜) 
    from 테이블
    ```
  * 고유한 자료의 개수 확인가능
    ```
    select count(distinct 컬럼) 
    from 테이블
    ```

    python에서 len(col.unique())느낌..


### 4. where -> 조회하고 싶은 조건

### 5. limit -> 지정된 갯수만큼의 자료만 보여줌
* 5개만 보여줌
  ```
  select * from 테이블 
  limit 5
  ```

* 3번째부터 5개 자료만 보여줌 
  ```
  limit 2,5(start, number to return)
  ```
  

### 6. fetch -> limit the number of rows returned by a query
* 0행부터 2개만 보여줌
  ```
  select * from 테이블
  fetch next 2 rows only;
  ```
* limit과 다른 점 : offset과 함께 써서 offset에서 지정한 행부터 fetch가 지정한 수의 행 반환
  * 10번째 행부터 10개 반환

    ```
    select * from 테이블 offset 10 rows
    fetch next 10 rows only;
    ```


### 7. in -> where 절 내에서 특정값 여러개를 선택하는 sql 연산자
  ```select * from 테이블
  where 컬럼명 in (값1, 값2, …)
  ```

### 8. between -> 범위 조건을 주는 연산자
  the values can be numbers, txt or dates
  시작과 끝도 포함됨

  ```select * from products
  where price between 10 and 20;
  ```

### 9. like -> 컬럼에서 특정 패턴을 검색, where 절 안에서 쓰임
* 와일드 카드 
  ```
  1. % : 0, 1, or 여러 문자 의미
  2. _ : 하나의 문자 의미
  ```
* 예시 : 이름이 a로 시작하는 고객을 반환
  ```
  select * from customers
  where  customers like ‘a%’;
  ```


### 10. isnull -> 결측치 확인
* 주소가 결측치인 데이터 
  ```
  select *
  from customers
  where Address Is NULL;
  ```



# 연습문제 1
---
### 1. rental date
```
select distinct date(rental_date) 
from rental r 
```
  - 처음에는 `select rental_date from rental`이라고 함
  - 대여가 있었던 날짜니까 distinct와 date를 사용

### 2. 영화길이 120분 이상 and 대여기간 4일 이상, 영화제목
```
select title from film f 
where length >= 120 and rental_duration >=4
```

### 3. staff_id=2, id and first name and last name
```
select staff_id, first_name, last_name from staff
where staff_id=2
```

### 4. payment_id = 17510, amount?
```
select amount from payment p 
where payment_id = 17510
```

### 5. scifi category_id?
```
select category_id from category c 
where name = 'Sci-Fi'
```

### 6. how many ratings in film table?
* how many?
  ```
  select count(distinct rating)  
  from film
  ```
* what kind of rating groups in film table?
  ```
  select distinct rating
  from film
  ```
  - 문제가 몇개의 등급이 있는지?를 물어봤기 때문에 첫번째가 답이라고 생각

### 7. all columns from rental where rental duration(return - rental) +1 >=10 
```
select * from rental r
where date(return_date) - date(rental_date) +1 >= 10
```
  - 정답이 좀 이해가 가지 않음
    1) from이 없어도 되는가?
    2) diff_date라고 정의했는데 where에서는 왜 사용하지 않았지?
    3) diff_date라고 정의하면 where에서 사용할 수 있는지?
    * 정답
    ```
    selec *, date(return_date)-date(rental_date) +1
            as diff_date
    where date(return_date)-date(rental_date) +1 >=10
    ```
### 8. id, full name, email where id = 50 multiples
```
select customer_id, first_name, last_name, email from customer
where customer_id%50 = 0
```
  - 정답에서는 `where mod(customer_id, 50) = 0` 이라고 사용
  - 연산자 함수?에 대해서 좀 더 공부해야겠음

### 9. title length = 8, title
```
select title from film
where length(title) = 8
order by title
```
  - 어떻게 나열하라는건지 문제가 더 정확하게 알려주면 좋겠어요
 
### 10. the number of cities in city table
```
select count(distinct city) 
from city c
```

### 11. actors full name, unique values, upper
```
select distinct upper(first_name||' '||last_name) as name from actor a
order by name
```
  - 변수 두 개 붙일 때는 `||''||` 이렇게 사용하면 됨
  - 문제에는 없었지만 보기 좋게 `order by name`을 사용하여 정렬

### 12. among customers, active=0, the numbers of customers
```
select count(distinct customer_id) 
from customer c 
where active=0
```

### 13. store_id=1, the number of customers
```
select count(customer_id)
from customer c 
where store_id = 1
```

### 14. how many returns when return date = 2005/06/20, 
```
select count(rental_id) 
from rental r
where date(return_date)='2005-06-20'
```
  - rental table의 return_date의 형태는 `datetime(format: YYYY-MM-DD HH:MI:SS)`임 -> 2005-06-20을 조건으로 하기 위해서는 `date(return_date)`로 해서 형식을 변환시켜줘야 함
  - 날짜는 `'yyyy-mm-dd'`로 표현하면 됨

### 15. all columns from film table where release at 2006, rating = 'G' rental_duration=3, 
```
select *
from film f 
where release_year = '2006' 
and rating='G' 
and rental_duration = 3
```

### 16. id, name in language table
```
select language_id, name
from "language" l 
```
  - language 컬럼은 자동으로 따옴표 처리가 된다. language라는 함수가 있어서 그런걸까?(검색은 해봤는데 뭐 딱히 잘 안 나옴..)

### 17. film_id, title, description in film table where rental_duration>=7
```
select film_id, title, description
from film f
where rental_duration >=7
```

### 18. film_id, title, description in film table where rental_duration=3 or 5
```
select film_id, title, description
from film f
where rental_duration =3
or rental_duration =5
```

### 19. id, name in actor table where fisrtname=Nick or lastname=Hunt
```
select actor_id, first_name, last_name 
from actor
where first_name = 'Nick' or last_name = 'Hunt'
```

### 20.first_name -> firstname, last_name ->lastname in actor table
```
select first_name as fisrtname, last_name as lastname
from actor
```
 - `as`를 쓰면 새롭게 이름을 부여할 수 있



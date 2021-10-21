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

### 11.
```
```

### 12.
```
```

### 13.
```
```

### 14.
```
```

### 15.
```
```

### 16.
```
```

### 17.
```
```

### 18.
```
```

### 19.
```
```

### 20.
```
```



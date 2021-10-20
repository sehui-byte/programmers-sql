

### 없어진 기록 찾기

- 문제 : 

- 답 :

  ```sql
  
  SELECT o.animal_id, o.name
  from ANIMAL_INS i
  right join ANIMAL_OUTS o on i.animal_id = o.animal_id
  where i.animal_id is null
  ;
  ```

  

### 있었는데요 없었습니다.

- 문제: https://programmers.co.kr/learn/courses/30/lessons/59043

- 답 : 

  ```sql
  SELECT i.animal_id, i.name
  FROM animal_ins i
  join animal_outs o on i.animal_id = o.animal_id
  where i.datetime > o.datetime
  order by i.datetime asc;
  ```

  

### 오랜 기간 보호한 동물(1)

- 문제 : https://programmers.co.kr/learn/courses/30/lessons/59044

- 답 : 

  ```sql
  SELECT i.name, i.datetime
  from animal_ins i
  left join animal_outs o on i.animal_id = o.animal_id
  where o.animal_id is null
  order by i.datetime
  limit 3
  ;
  ```



### 보호소에서 중성화한 동물

- 문제 : https://programmers.co.kr/learn/courses/30/lessons/59045#fn1

- 답 : 

  ```sql
  
  SELECT i.animal_id, i.animal_type, i.name
  from animal_ins i
  join animal_outs o on i.animal_id = o.animal_id
  where i.sex_upon_intake like '%Intact%'
  and (o.sex_upon_outcome like 'Neutered %' or o.sex_upon_outcome like 'Spayed%')
  order by i.animal_id
  ;
  ```

  
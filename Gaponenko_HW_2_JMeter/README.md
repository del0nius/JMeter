#### Jmeter_2 HW

#### 1) http://5.75.203.123:5005/user_info
```sql
req. (RAW JSON)
POST
age: int
salary: int
name: str
auth_token

resp.
{'start_qa_salary':salary,
 'qa_salary_after_6_months': salary * 2,
 'qa_salary_after_12_months': salary * 2.9,
 'person': {'u_name':[user_name, salary, age],
                                'u_age':age,
                                'u_salary_1.5_year': salary * 4}
                                }
```
Действия:
1) Достать из Respose значение из поля 'qa_salary_after_6_months' и передать в поле salary запроса http://5.75.203.123:5005/new_data

#### 2) http://5.75.203.123:5005/new_data
```sql
req.
POST
age: int
salary: int
name: str
auth_token

Resp.
{'name':name,
  'age': int(age),
  'salary': [salary, str(salary*2), str(salary*3)]}
```
Действия:
1) Достать из Respose значение из поля 'name' и передать в поле name запроса http://5.75.203.123:5005/new_data

#### 3) http://5.75.203.123:5005/test_pet_info
```sql
req.
POST
age: int
weight: int
name: str
auth_token

Resp.
{'name': name,
 'age': age,
 'daily_food':weight * 0.012,
 'daily_sleep': weight * 2.5}
```
Тесты:
1) Достать из Respose значение из поля age и передать в поле age запроса http://5.75.203.123:5005/get_test_user

Задание ***
0) Изучать как работают Response Assertion.
1) Сделать Assertion на провекрку статус код 200
2) Сделать Assertion на провекрку 'daily_food':weight * 0.012

#### 4) http://5.75.203.123:5005/get_test_user
```sql
req.
POST
age: int
salary: int
name: str
auth_token

Resp.
{'name': name,
 'age':age,
 'salary': salary,
 'family':{'children':[['Alex', 24],['Kate', 12]],
 'u_salary_1.5_year': salary * 4}
  }
```
Тесты:
Задание ***
0) Изучать как работают Response Assertion.
1) Сделать Assertion на провекрку статус код 200
2) Сделать Assertion на провекрку 'salary': salary
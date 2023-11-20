# Домашнее задание к занятию "`Базы данных`" - `Дубинин Денис`



### Задание 1

`Решение...`

Исходная таблица: Сотрудники '('
	ФИО_сотрудника  	varchar(50)
	Оклад 			numeric(8,2)
	Должность		varchar(30)
	Тип подразделения 	varchar(20)
	Структурное подразделение varchar(50)
	Дата найма 		date
	Адрес филиала 		varchar(50)
	Проэкт 			varchar(50)
')'

Для нормализации создаем дополнительные таблицы:

Должность (\
	job_title_id, первичный ключ, serial\
	должность, varchar(30)\
)

Структурное подразделение (/
	structural_subdvision_id первичный ключ serial/
	Тип подразделения varchar(20)/
)

Подразделение (
	unit_type_id, первичный ключ, serial
	Тип подразделения, varchar(20)
	structural_subdvision_id, внешний ключ, integer 
)

Субъект (
	subject_id первичный ключ serial
	Субъект (край, область), varchar(20)
)

Город (
	city_id первичный ключ serial
	Город, varchar(20)
)

Адрес филиала (
	branch_address_id, первичный ключ, serial
	subject_id, внешний ключ, integer
	city_id, внешний ключ, integer
	Улица и дом, varchar(20) 
)

Оклад (
	salary_id первичный ключ serial
	Оклад, numeric(8,2)
)

Таблица примет следующий вид:
Сотрудники (
	employee_id	первичный ключ serial
	ФИО_сотрудника  varchar(50)
	salary_id 	внешний ключ, integer
	job_title_id	внешний ключ, integer
	unit_type_id 	внешний ключ, integer
	Дата найма 	date
	branch_address_id внешний ключ, integer
	Проэкт 		varchar(50),
)



---



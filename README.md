# Домашнее задание к занятию "`Базы данных`" - `Дубинин Денис`



### Задание 1

`Решение...`

Исходная таблица: Сотрудники (\
	ФИО_сотрудника  	varchar(50)\
	Оклад 			numeric(8,2)\
	Должность		varchar(30)\
	Тип подразделения 	varchar(20)\
	Структурное подразделение varchar(50)\
	Дата найма 		date\
	Адрес филиала 		varchar(50)\
	Проэкт 			varchar(50)\
)

Для нормализации создаем дополнительные таблицы:

Должность (\
	должность_id, первичный ключ, serial\
	должность, varchar(30)\
)

Структурное подразделение (\
	структурное_подразделение_id первичный ключ serial\
	Тип подразделения varchar(20)\
)

Подразделение (\
	подразделение_id, первичный ключ, serial\
	Тип подразделения, varchar(20)\
	структурное_подразделение_id, внешний ключ, integer\
)

Субъект (\
	субъект_id первичный ключ serial\
	Субъект (край, область), varchar(20)\
)

Город (\
	город_id первичный ключ serial\
	Город, varchar(20)\
)

Адрес филиала (\
	адрес_филиала_id, первичный ключ, serial\
	субъект_id, внешний ключ, integer\
	город_id, внешний ключ, integer\
	Улица и дом, varchar(20) \
)

Оклад (\
	оклад_id первичный ключ serial\
	Оклад, numeric(8,2)\
)

Имя (\
	имя_id первичный ключ serial\
	Имя, varchar(10)\
)

Отчество (\
	отчество_id первичный ключ serial\
	Отчество, varchar(10)\
)

ФИО сотрудника (\
	ФИО_сотрудника_id, первичный ключ, serial\
	Фамилия, varchar(10) \
	имя_id, внешний ключ, integer\
	отчество_id, внешний ключ, integer\
)

Таблица примет следующий вид:
Сотрудники (\
	сотрудник_id		первичный ключ serial\
	ФИО_сотрудника_id  	внешний ключ, integer\
	оклад_id 		внешний ключ, integer\
	должность_id		внешний ключ, integer\
	подразделение_id 	внешний ключ, integer\
	Дата найма 		date\
	адрес_филиала_id 	внешний ключ, integer\
	Проэкт 			varchar(50)\
)

По замечаниям:\
1. ФИО вынес в отдельную таблицу с дочерними таблицами Имя и Отчество.\
2. Тип подразделения размещен в таблице Подразделение с внешним ключем Структурное подразделение.\
Исходя из данных в исходной таблице, считаю это более логичным чем то, на что обратили Вы внимание.\
3. Улицу и дом я на части не разбивал, они в одном столбце.\
А вот адрес в целом вынесен в таблицу Адрес филиала и разбит на Субъект, Город, улица с домом. \


---



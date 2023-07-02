# Домашнее задание Базы данных-Неклюдов Михаил


Задание 1.

Таблица 1. Сотрудники.
name_id, идентификатор сотрудника, PRIMARY KEY, SERIAL
ФИО, VARCHAR
оклад, MEDIUMINT
должность_id, идентификатор должности, FOREIGN KEY, INTEGER
структурное подразделение_id, идентификатор структурного подразделения, FOREIGN KEY,TINYINT
дата, DATE
регион_id, идентификатор региона, FOREIGN KEY,TINYINT
город_id, идентификатор города, FOREIGN KEY,TINYINT
адрес, VARCHAR
проект_id, иеднтификатор проекта, FOREIGN KEY,SMALLINT

Таблица 2. Должность.
должность_id, идентификатор должности, PRIMARY KEY,SERIAL
должность, VARCHAR

Таблица 3. Структурное подразделение.
структурное подразделение_id, идентификатор структурного подразделения, PRIMARY KEY,SERIAL
тип подразделения_id, идентификатор типа подразделения, FOREIGN KEY,TINYINT
структурное подразделение, VARCHAR

Таблица 4. Тип подразделения.
тип подразделения_Id, идентификатор типа подразделения, PRIMARY KEY,SERIAL
тип подразделения, VARCHAR

Таблица 5. Регион.
регион_id, идентификаатор региона, PRIMARY KEY,SERIAL
регион, VARCHAR

Таблица 6. Город.
город_id, идентификатор города, PRIMARY KEY,SERIAL
город, VARCHAR

Таблица 7. Проект.
проект_id, идентификатор проекта, PRIMARY KEY,SERIAL
структурное подразделение_id, идентификатор структурного подразделения, PRIMARY KEY,SERIAL
проект, VARCHAR


Задание 2.

На мой взгдял нужно выделить в отдельные таблицы: должность, тип подразделения, структурное подразделение, регион, город, проект.
Таблица Сотрудники будет зависить от таблиц Должность, Структурное подразделение, Регион, Город, Проект. Таблица Структрное подраазделение будет зависеть от таблицы тип подразделения. Таблица проект будет зависеть от таблицы Структурное подразделение и таблицы Сотрудники.
Для того, чтобы нормализовать данные нужно убрать списки в колонке адрес; удалить дубликаты в колонках: должность, тип подразделения, структурное подразделение, адрес, проект; удалить значение, неявляющееся частью ключа - колонка тип подразделения. 



28-11-2022
10:27
Authors: 
***
Tags: #programming #liquibase
***
# Tutorial

Добавление liquibase в проект.

В `alplication.properties` указываем где будут находиться чейнжлоги (миграции)
```
spring.liquibase.change-log=classpath:db.changelog/db.changelog-master.xml
```
Это стока указывает, что они будут находиться в папке `resources/dv` 
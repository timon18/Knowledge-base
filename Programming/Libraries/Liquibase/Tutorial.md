28-11-2022
10:27
Authors: Khutuev Tamerlan.
***
Tags: #programming #liquibase
***
# Tutorial

Добавление liquibase в проект.

В `alplication.properties` указываем где будут находиться чейнжлоги (миграции).
```
spring.liquibase.change-log=classpath:db.changelog/db.changelog-master.xml
```

Строка выше указывает, что в папке `resources/db/changelog` будет находиться главный changelog. 

```xml
<databaseChangeLog xmlns="http://www.liquibase.org/xml/ns/dbchangelog"  
                   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
                   xsi:schemaLocation="http://www.liquibase.org/xml/ns/dbchangelog  
                        http://www.liquibase.org/xml/ns/dbchangelog/dbchangelog-3.4.xsd">  
<!--    <include file="classpath:db/changelog/db.changelog-1.0.xml"/>-->  
</databaseChangeLog>
```

Остальные чейндлоги добавляются тегом `include`.

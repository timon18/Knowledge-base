 08-10-2021
14:04
Authors: Khutuev Tamerlan.
***
Tags: #programming #django #frameworks 
***
# Архитектура Django 
https://djangobook.com/mdj2-django-structure/

![[Pasted image 20211008142514.png]]

Клиент > Запрос > web server > wsgi > формирование request > middleware > корневой urls > app.urls > app.views > context processors > template > response > wsgi > web server > Клиент



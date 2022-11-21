06-10-2021
11:30
***
Tags: #programming #django 
***
# Запуск проекта Django


Для начала надо изолировать проект. Для этого настраиваем Virtualenv [[Virtualenv]].

>(Если не устонавили Django)Далее создаём в папке файл зависимостей requirements.txt. Впишем туда строку:
>Django
Далее с помощью pip устанавливаем зависимости:
>pip install -U -r requirements.txt

Создаём проект:

>django-admin.py startproject project\_name

Создаём приложение:

>python3 manage.py startapp app\_name

Далее приложение надо зарегистрировать. В фале settings.py дописываем имя приложения

>INSTALLED\_APPS = \[
'.....',
'.....',
'app\_name',
\]

В файле settings.py можно заменить язык сайта на русский.

>LANGUAGE\_CODE = 'ru'
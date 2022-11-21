06-10-2021
11:31
Authors: Khutuev Tamerlan.
***
Tags: #programming #python 
***
# Virtualenv 


Virtualenv — это инструмент, позволяющий создавать виртуальные окружения с пакетами.

Установить pip

>sudo apt-get install python-pip

Устанавливаем virtualenv


```python
sudo pip install virtualenvwrapper
```

В ~/.bashrc дописываем:

>export VIRTUALENVWRAPPER\_PYTHON=/usr/bin/python3
source /usr/bin/virtualenvwrapper.sh

Для того, что бы открыть **~/.bashrc** просто введи:

>nano ~/.bashrc

Но у меня это не сработало. По этому в ~/.bashrc я ввёл:

>export WORKON\_HOME=$HOME/.virtualenvs
export PROJECT\_HOME=$HOME/Devel
export VIRTUALENVWRAPPER\_PYTHON=/usr/bin/python3
source /usr/local/bin/virtualenvwrapper.sh

Вводим для типо перезагрузки файла

>source ~/.bashrc

Нужно ли это я не знаю,  но по моему я сделал:

>mkdir ~/.virtualenvs

Создаем новое окружение:

>mkvirtualenv env-name

  

Смотрим список окружений:

>workon

  

Заходим в окружение:

>workon env-name

  

Выходим из окружения:

>deactivate

  

Удаляем окружение:

>rmvirtualenv env-name
03-01-2021
19:06
Authors: Khutuev Tamerlan.
***
Tags: #learning #wsl #jupyter #programming 
***
# Jupyter и WSL
Просто так открыть его с браузера компьютера не получится. Надо настроить конфиг файл. Для того, что бы разрешить внешние подключения.

Файл конфигурации лежит (должен лежать) тут:
```
/home/user/.jupyter/jupyter_notebook_config.py
```

Но у меня его не было, по этому придётся его создать командой:
```
jupyter notebook --generate-config
```

Добавляем эти строчки (куда угодно, так как значения по умолчанию закоментированы)
`c.NotebookApp.allow_origin = '*'` 
`c.NotebookApp.ip = '0.0.0.0'` \# прослушиваем все IP

Если порт 8888 заблокировани то:
```
sudo ufw allow 8888
```

И дальше устанавливаем пароль:
```
jupyter notebook password
```

Теперь, что бы зайти с компьютера надо узать ip wsl. 
Для этого воодим команду:
```
ip addr | grep eth0
```

Запускаем сам Юпитер:
```
jupyter notebook
```

И вводим ip в браузер. С портом 8888.


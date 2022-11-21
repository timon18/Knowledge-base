06-10-2021
11:33
Authors: Khutuev Tamerlan.
***
Tags: #programming #git 
***
# Подключение и установка Git к GitHub Установка

[Хорошая ссылка](https://umedman.gitbooks.io/-git-keys-/content/index.html)

Ubuntu:

>sudo apt install git

Далее надо подключить его к  GitHub. Подключать будем по ssh. Нужны ключи. Для начала проверим есть они у нас или нет.

Про ключи -> [[OpenSSH]]

Теперь нам нужно добавить сгенерированные ключи к ssh-агенту.

Про ssh агента-> [[SSH Agent]]

Запустим его вручную.

`eval "$(ssh-agent -s)"`

Теперь нам нужно добавить созданные ключи к ssh-агенту. 

`ssh-add ~/.ssh/id_rsa`
  

Далее надо добавить ключ к учётной записи на GitHub.

Копируем открытый ключ командой.

`cat ~/.ssh/id_rsa.pub`

  
Далее заходим на сайт [GitHub.com](http://GitHub.com) под своей учетной записью и, щелкнув на своем аватаре, выбираем **Settings**. В меню, расположенном в левой части, выбираем **SSH and GPG keys** и нажимаем **New SSH key**. Заполняем поле **Title**, для того, чтобы нам самим было понятнее, что это за ключ, вставляем содержимое файла открытого ключа из буфера в поле **Key** и нажимаем **Add SSH key**.

Можно всё проверить соединение.

`ssh -T git@github.com`

  

Будет выведен такой (или похожий текст):

>The authenticity of host 'github.com (192.30.252.1)' can't be established.
RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
Are you sure you want to continue connecting (yes/no)?

Нажимаем enter.

>Hi username! You've successfully authenticated, but GitHub does not
provide shell access.

Для того, чтобы ssh-агент каждый раз запускался автоматически при старте Git Bash, добавим в файл **~/.bashrc** следующий код:

```
env=~/.ssh/agent.env
agent_load_env () { test -f "$env" && . "$env" >| /dev/null ; }
agent_start () {
(umask 077; ssh-agent >| "$env")
. "$env" >| /dev/null ; }
agent_load_env
# agent_run_state: 0=agent running w/ key; 1=agent w/o key; 2= agent not running
agent_run_state=$(ssh-add -l >| /dev/null 2>&1; echo $?)
if [ ! "$SSH_AUTH_SOCK" ] || [ $agent_run_state = 2 ]; then
agent_start
ssh-add
elif [ "$SSH_AUTH_SOCK" ] && [ $agent_run_state = 1 ]; then
	ssh-add
fi
unset env
```

Для того, что бы открыть **~/.bashrc** просто введи:

`nano ~/.bashrc`

  

Теперь всё подключено. Кстати. Про то как сделать первый комит будет написано на странице с репозиторием:

`echo "# test" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:timon18/test.git
git push -u origin main`

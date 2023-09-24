<div align="center">
  <h1> 30 Дней Python: День 23 - Виртуальное окружение </h1>
  <a href="https://github.com/obulygin/30-Days-Of-Python/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=obulygin/30-Days-Of-Python" />
</div>

[<< День 22](../22_Day_Web_scraping/22_web_scraping.md) | [День 24 >>](../24_Day_Statistics/24_statistics.md)

![30DaysOfPython](../images/30daysofpython.png)

- [📘 День 23](#-день-23)
  - [Установка виртуального окружения](#установка-виртуального-окружения)
  - [💻 Упражнения: День 23](#-упражнения-день-23)

# 📘 День 23

## Установка виртуального окружения

Перед началом работы над проектом лучше настроить виртуальное окружение. Виртуальное окружение позволяет создать изолированное или обособленное окружение. Это поможет избежать конфликтов в зависимостях у разных проектов. Если вы наберете pip freeze в вашем терминале, вы увидите все установленные на ваш компьютер пакеты. Если мы используем виртуальное окружение, мы получим доступ только к пакетам, установленным для данного проекта. Откройте ваш терминал и установите virtualenv

```sh
asabeneh@Asabeneh:~$ pip install virtualenv
```

Внутри папки 30DaysOfPython создайте папку flask_project.

После установки пакета virtualenv перейдите в созданную папку проекта и создайте виртуальное окружение командой:

Для Mac/Linux:
```sh
asabeneh@Asabeneh:~/Desktop/30DaysOfPython/flask_project\$ virtualenv venv

```

Для Windows:
```sh
C:\Users\User\Documents\30DaysOfPython\flask_project>python -m venv venv
```

Я предпочитаю называть папку для виртуального окружения venv, но вы можете использовать другое название. Давайте убедимся, что папка venv была создана с помощью команды ls (или dir для командной строки windows).

```sh
asabeneh@Asabeneh:~/Desktop/30DaysOfPython/flask_project$ ls
venv/
```

Давайте активируем виртуальное окружение, написав следующую команду в папке нашего проекта.

Для Mac/Linux:
```sh
asabeneh@Asabeneh:~/Desktop/30DaysOfPython/flask_project$ source venv/bin/activate
```
Активация виртуального окружения в Windows может отличаться в командной оболочке Windows Power shell и в git bash. 

В Windows Power Shell:
```sh
C:\Users\User\Documents\30DaysOfPython\flask_project> venv\Scripts\activate
```

В Windows Git bash:
```sh
C:\Users\User\Documents\30DaysOfPython\flask_project> venv\Scripts\. activate
```

Примечание переводчика: если при использовании команды venv\Scripts\activate в Windows 10 возникает ошибка, что отключено выполнение сценариев, то в Windows Power Shell от имени администратора нужно ввести команду:
```sh
PS C:\Users\User>Set-ExecutionPolicy Unrestricted
```

После того как вы ввели команду активации, директория вашего проекта будет начинаться с (venv). Взгляните на пример ниже.

```sh
(venv) asabeneh@Asabeneh:~/Desktop/30DaysOfPython/flask_project$
```

Теперь давайте проверим доступные в этом проекте пакеты с помощью команды pip freeze. Ни одного пакета на данный момент нет.

Мы собираемся создать небольшой проект на flask, поэтому давайте установим пакет flask для этого проекта.

```sh
(venv) asabeneh@Asabeneh:~/Desktop/30DaysOfPython/flask_project$ pip install Flask
```

Теперь давайте снова запустим pip freeze, чтобы увидеть список установленных для проекта пакетов:

```sh
(venv) asabeneh@Asabeneh:~/Desktop/30DaysOfPython/flask_project$ pip freeze
blinker==1.6.2
click==8.1.3
colorama==0.4.6
Flask==2.3.2
itsdangerous==2.1.2
Jinja2==3.1.2
MarkupSafe==2.1.2
Werkzeug==2.3.4
```

Когда закончите, следует деактивировать активированный проект с помощью команды _deactivate_.

```sh
(venv) asabeneh@Asabeneh:~/Desktop/30DaysOfPython$ deactivate
```

Необходимые для работы с flask модули установлены. Теперь директория вашего проекта готова для разработки проекта на flask. Вам следует добавить папку venv в ваш файл .gitignore, чтобы не отправлять ее на гитхаб.

## 💻 Упражнения: День 23

1. Создайте директорию проекта с виртуальным окружением как в примере выше.

🎉 ПОЗДРАВЛЯЮ ! 🎉

[<< День 22](../22_Day_Web_scraping/22_web_scraping.md) | [День 24 >>](../24_Day_Statistics/24_statistics.md)

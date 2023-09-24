<div align="center">
  <h1> 30 дней Python: День 26 - Python для веб-разработки </h1>
  <a href="https://github.com/obulygin/30-Days-Of-Python/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=obulygin/30-Days-Of-Python" />
</div>

[<< День 25 ](../25_Day_Pandas/25_pandas.md) | [День 27 >>](../27_Day_Python_with_mongodb/27_python_with_mongodb.md)

![30DaysOfPython](../images/30daysofpython.png)

- [📘 День 26](#день-26)
  - [Python для веб-разработки ](#python-для-веб-разработки)
    - [Flask](#flask)
      - [Структура папок](#структура-папок)
    - [Настройка структуры каталога вашего проекта](#настройка-структуры-каталога-вашего-проекта)
    - [Создание маршрутов](#создание-маршрутов)
    - [Создание шаблонов](#создание-шаблонов)
    - [Python-скрипт](#python-скрипт)
    - [Навигация](#навигация)
    - [Создание макета](#создание-макета)
      - [Обслуживающий статический файл](#обслуживающий-статический-файл)
    - [Развертывание](#развертывание)
      - [Создание аккаунта на Heroku](#создание-аккаунта-на-heroku)
      - [Вход в аккаунт Heroku](#вход-в-аккаунт-heroku)
      - [Создание файлов requirements и Procfile](#создание-файлов-requirements-и-procfile)
      - [Отправка проекта на Heroku](#отправка-проекта-на-heroku)
  - [Упражнения: День 26](#упражнения-день-26)

# 📘 День 26

## Python для веб-разработки 

Python - это универсальный язык программирования, который может использоваться во многих областях. В этом разделе мы рассмотрим, как использовать Python для веб-разработки. Существует много веб-фреймворков на Python. Django и Flask являются наиболее популярными. Сегодня мы рассмотрим, как использовать Flask для разработки веб-приложений.

### Flask

Flask - это фреймворк для веб-разработки, написанный на языке Python. Flask использует шаблонизатор Jinja2. Flask также может использоваться с другими современными библиотеками фронтенда, такими как React.

Если вы еще не установили пакет virtualenv, сначала установите его. Виртуальное окружение позволяет изолировать зависимости проекта от зависимостей на локальной машине.

#### Структура папок

После завершения всех шагов, структура файлов вашего проекта должна выглядеть следующим образом:

```sh

├── Procfile
├── app.py
├── env
│   ├── bin
├── requirements.txt
├── static
│   └── css
│       └── main.css
└── templates
    ├── about.html
    ├── home.html
    ├── layout.html
    ├── post.html
    └── result.html
```

### Настройка структуры каталога вашего проекта

Выполните следующие действия, чтобы начать работу с Flask.

Шаг 1: установите virtualenv, используя следующую команду.

```sh
pip install virtualenv
```

Step 2:

```sh
user@user:~/Desktop$ mkdir python_for_web
user@user:~/Desktop$ cd python_for_web/
user@user:~/Desktop/python_for_web$ virtualenv venv
user@user:~/Desktop/python_for_web$ source venv/bin/activate
(env) user@user:~/Desktop/python_for_web$ pip freeze
(env) user@user:~/Desktop/python_for_web$ pip install Flask
(env) user@user:~/Desktop/python_for_web$ pip freeze
Click==7.0
Flask==1.1.1
itsdangerous==1.1.0
Jinja2==2.10.3
MarkupSafe==1.1.1
Werkzeug==0.16.0
(env) user@user:~/Desktop/python_for_web$
```

Мы создали директорию проекта с названием "python_for_web". Внутри проекта мы создали виртуальное окружение с именем *venv* (это имя может быть любым). Затем мы активировали виртуальное окружение. После этого использовали команду "pip freeze", чтобы проверить установленные пакеты в каталоге проекта. Результат команды "pip freeze" был пустым, поскольку пакеты еще не были установлены.

Теперь давайте создадим файл app.py в директории проекта и напишем следующий код. Файл app.py будет основным файлом в проекте. В следующем коде используются модули Flask и os.

### Создание маршрутов

Маршруты для главной страницы и страницы "about"

```py
# импортируем flask
from flask import Flask
import os # импорт модуля операционной системы

app = Flask(__name__)

@app.route('/') # этот декоратор создает маршрут для главной страницы
def home ():
    return '<h1>Добро пожаловать</h1>'

@app.route('/about') # этот декоратор создает маршрут для страницы "about"
def about():
    return '<h1>О нас</h1>'


if __name__ == '__main__':
    # для развертывания мы используем environ
    # чтобы сделать его работающим как для продакшн-среды, так и для разработки
    port = int(os.environ.get("PORT", 5000))
    app.run(debug=True, host='0.0.0.0', port=port)
```

Для запуска Flask-приложения выполните команду _python app.py_ в основной директории приложения Flask.

После выполнения команды _python app.py_ проверьте локальный хост (local host) на порту 5000.

Мы добавили маршруты для главной страницы и страницы "about" в приведенном выше коде. Что, если мы хотим отобразить HTML-файл вместо строки? Это возможно с помощью функции *render_template*. Давайте создадим папку с именем "templates" и создадим файлы "home.html" и "about.html" в корневой папке проекта. Также давайте импортируем функцию *render_template* из модуля flask.

### Создание шаблонов

Создайте HTML-файлы внутри папки "templates".

home.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Домашняя страница</title>
  </head>

  <body>
    <h1>Добро пожаловать!</h1>
  </body>
</html>
```

about.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>О нас</title>
  </head>

  <body>
    <h1>Кое-что о нас</h1>
  </body>
</html>
```

### Python-скрипт

app.py

```py
# импортируем flask
from flask import Flask, render_template
import os # импорт модуля операционной системы

app = Flask(__name__)

@app.route('/') # этот декоратор создает маршрут для главной страницы
def home ():
    return render_template('home.html')

@app.route('/about') # этот декоратор создает маршрут для страницы "about"
def about():
    return render_template('about.html')

if __name__ == '__main__':
    # для развертывания мы используем environ
    # чтобы сделать его работающим как для продакшн-среды, так и для разработки
    port = int(os.environ.get("PORT", 5000))
    app.run(debug=True, host='0.0.0.0', port=port)
```

Как вы видите, для перехода на html страницы нам необходимо иметь панель навигации. Давайте добавим ссылку на каждую страницу или создадим макет, который будем использовать для каждой страницы.

### Навигация

```html
<ul>
  <li><a href="/">Домашняя страница</a></li>
  <li><a href="/about">О нас</a></li>
</ul>
```

Теперь мы можем перемещаться между страницами, используя вышеуказанную ссылку. Давайте создадим дополнительную страницу, которая будет обрабатывать данные формы. Вы можете назвать ее как угодно (например, post.html)

Мы можем вставлять данные в HTML-файлы с помощью шаблонного движка Jinja2.

```py
# импортируем flask
from flask import Flask, render_template, request, redirect, url_for
import os # импорт модуля операционной системы

app = Flask(__name__)

@app.route('/') # этот декоратор создает маршрут для главной страницы
def home ():
    techs = ['HTML', 'CSS', 'Flask', 'Python']
    name = '30 дней программирования на языке Python'
    return render_template('home.html', techs=techs, name = name, title = 'Домашняя страница')

@app.route('/about') # этот декоратор создает маршрут для страницы "about"
def about():
    name = '30 дней программирования на языке Python'
    return render_template('about.html', name = name, title = 'О нас')

@app.route('/post') # этот декоратор создает маршрут для страницы "post"
def post():
    name = 'Анализатор текста
    return render_template('post.html', name = name, title = name)

if __name__ == '__main__':
    # для развертывания мы используем environ
    # чтобы сделать его работающим как для продакшн-среды, так и для разработки
    port = int(os.environ.get("PORT", 5000))
    app.run(debug=True, host='0.0.0.0', port=port)
```

Давайте также рассмотрим шаблоны (templates):

home.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Домашняя страница</title>
  </head>

  <body>
    <ul>
      <li><a href="/">Домашняя страница</a></li>
      <li><a href="/about">О нас</a></li>
    </ul>
    <h1>Добро пожаловать в раздел {{name}}</h1>
     <ul>
    {% for tech in techs %}
      <li>{{tech}}</li>
    {% endfor %}
    </ul>
  </body>
</html>
```

about.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>О нас</title>
  </head>

  <body>
    <ul>
      <li><a href="/">Домашняя страница</a></li>
      <li><a href="/about">О нас</a></li>
    </ul>
    <h1>Кое что о нас</h1>
    <h2>{{name}}</h2>
  </body>
</html>
```

### Создание макета

В файлах шаблонов присутствует много повторяющегося кода, который можно устранить, создав макет (layout). Давайте создадим файл layout.html внутри папки templates. 
После создания макета мы будем импортировать его в каждый файл.

#### Обслуживающий статический файл

Создайте папку "static" в корневой директории вашего проекта. Внутри папки "static" создайте папку "CSS" или "styles" и создайте файл CSS стилей. Мы будем использовать модуль *url_for* для обслуживания статического файла. 

layout.html

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <link
      href="https://fonts.googleapis.com/css?family=Lato:300,400|Nunito:300,400|Raleway:300,400,500&display=swap"
      rel="stylesheet"
    />
    <link
      rel="stylesheet"
      href="{{ url_for('static', filename='css/main.css') }}"
    />
    {% if title %}
    <title>30 дней Python - {{ title}}</title>
    {% else %}
    <title>30 дней Python</title>
    {% endif %}
  </head>

  <body>
    <header>
      <div class="menu-container">
        <div>
          <a class="brand-name nav-link" href="/">30-дней-Python</a>
        </div>
        <ul class="nav-lists">
          <li class="nav-list">
            <a class="nav-link active" href="{{ url_for('home') }}">Домашняя страница</a>
          </li>
          <li class="nav-list">
            <a class="nav-link active" href="{{ url_for('about') }}">О нас</a>
          </li>
          <li class="nav-list">
            <a class="nav-link active" href="{{ url_for('post') }}"
              >Анализатор текста</a
            >
          </li>
        </ul>
      </div>
    </header>
    <main>
      {% block content %} {% endblock %}
    </main>
  </body>
</html>
```

Теперь давайте удалим повторяющийся код из других файлов шаблонов и импортируем layout.html. В атрибуте href мы будем использовать функцию _url_for_ с именем функции маршрута для связи с каждым маршрутом навигации.

home.html

```html
{% extends 'layout.html' %} {% block content %}
<div class="container">
  <h1>Добро пожаловать в раздел {{name}}</h1>
  <p>
    Это приложение очищает тексты и анализирует количество слов, символов и наиболее часто встречающиеся слова в тексте. Проверьте это, перейдя по ссылке "Анализатор текста" в меню. Для создания этого веб-приложения вам понадобятся следующие технологии:
  </p>
  <ul class="tech-lists">
    {% for tech in techs %}
    <li class="tech">{{tech}}</li>

    {% endfor %}
  </ul>
</div>

{% endblock %}
```

about.html

```html
{% extends 'layout.html' %} {% block content %}
<div class="container">
  <h1>О {{name}}</h1>
  <p>
    Это 30-дневный челлендж по программированию на языке Python. Если вы дошли до этой точки и продолжаете программировать, то вы большой молодец! Поздравляю вас с отличной работой!
  </p>
</div>
{% endblock %}
```

post.html

```html
{% extends 'layout.html' %} {% block content %}
<div class="container">
  <h1>Анализатор текста</h1>
  <form action="https://thirtydaysofpython-v1.herokuapp.com/post" method="POST">
    <div>
      <textarea rows="25" name="content" autofocus></textarea>
    </div>
    <div>
      <input type="submit" class="btn" value="Process Text" />
    </div>
  </form>
</div>

{% endblock %}
```

Методы запросов, такие как GET, POST, PUT и DELETE, являются общими методами запросов, которые позволяют выполнять операции CRUD - Create, Read, Update, Delete (Создание, Чтение, Обновление, Удаление).

В маршруте "post" мы будем использовать методы GET и POST в зависимости от типа запроса. Проверьте, как это выглядит в коде ниже. Метод request используется для обработки методов запросов и доступа к данным формы _app.py_

```py
# импортируем flask
from flask import Flask, render_template, request, redirect, url_for
import os # импорт модуля операционной системы

app = Flask(__name__)
# для предотвращения кэширования статических файлов
app.config['SEND_FILE_MAX_AGE_DEFAULT'] = 0



@app.route('/') # этот декоратор создает маршрут для главной страницы
def home ():
    techs = ['HTML', 'CSS', 'Flask', 'Python']
    name = '30 дней программирования на языке Python'
    return render_template('home.html', techs=techs, name = name, title = 'Домашняя страница')

@app.route('/about')
def about():
    name = '30 дней программирования на языке Python'
    return render_template('about.html', name = name, title = 'О нас')

@app.route('/result')
def result():
    return render_template('result.html')

@app.route('/post', methods= ['GET','POST'])
def post():
    name = 'Анализатор текста'
    if request.method == 'GET':
         return render_template('post.html', name = name, title = name)
    if request.method =='POST':
        content = request.form['content']
        print(content)
        return redirect(url_for('result'))

if __name__ == '__main__':
    # для развертывания мы используем environ
    # чтобы сделать его работающим как для продакшн-среды, так и для разработки
    port = int(os.environ.get("PORT", 5000))
    app.run(debug=True, host='0.0.0.0', port=port)
```

До сих пор мы рассмотрели, как использовать шаблоны и вставлять данные в шаблон, а также как создавать общий макет. Теперь давайте займемся статическими файлами. Создайте папку с названием "static" в корневой директории проекта, а внутри нее создайте папку с названием "css". В папке "css" создайте файл "main.css". Ваш файл "main.css" будет подключен к "layout.html".

Вам не нужно писать код файла CSS, просто скопируйте и используйте его. Перейдем к развертыванию приложения.

### Развертывание

#### Создание аккаунта на Heroku

Heroku предоставляет бесплатный сервис развертывания как для фронтенд-приложений, так и для полноценных приложений. Создайте аккаунт на [heroku](https://www.heroku.com/) и установите heroku [CLI](https://devcenter.heroku.com/articles/heroku-cli) на свой компьютер.
После установки Heroku напишите следующую команду

#### Вход в аккаунт Heroku

```sh
user@user:~$ heroku login
heroku: Нажмите любую клавишу, чтобы открыть браузер для входа или нажмите "q", чтобы выйти:
```

Давайте посмотрим результат, нажав любую клавишу на клавиатуре. Когда вы нажмете любую клавишу на клавиатуре, откроется страница входа в Heroku. После входа в систему ваше локальное устройство будет подключено к удаленному серверу Heroku. Если вы успешно подключены к удаленному серверу, вы увидите следующее.

```sh
user@user:~$ heroku login
heroku: Нажмите любую клавишу, чтобы открыть браузер для входа или нажмите "q", чтобы выйти:
Opening browser to https://cli-auth.heroku.com/auth/browser/be12987c-583a-4458-a2c2-ba2ce7f41610
Logging in ... done
Logged in as user@mail.com
user@user:~$
```

#### Создание файлов requirements и Procfile

Перед тем, как мы отправим наш код на удаленный сервер, нам понадобятся следующие файлы:

- requirements.txt
- Procfile

```sh
(env) user@user:~/Desktop/python_for_web$ pip freeze
Click==7.0
Flask==1.1.1
itsdangerous==1.1.0
Jinja2==2.10.3
MarkupSafe==1.1.1
Werkzeug==0.16.0
(env) user@user:~/Desktop/python_for_web$ touch requirements.txt
(env) user@user:~/Desktop/python_for_web$ pip freeze > requirements.txt
(env) user@user:~/Desktop/python_for_web$ cat requirements.txt
Click==7.0
Flask==1.1.1
itsdangerous==1.1.0
Jinja2==2.10.3
MarkupSafe==1.1.1
Werkzeug==0.16.0
(env) user@user:~/Desktop/python_for_web$ touch Procfile
(env) user@user:~/Desktop/python_for_web$ ls
Procfile          env/              static/
app.py            requirements.txt  templates/
(env) user@user:~/Desktop/python_for_web$
```

В файле Procfile будет указана команда, которая запускает приложение на веб-сервере, в нашем случае на Heroku.

```sh
web: python app.py
```

#### Отправка проекта на Heroku

Теперь приложение готово к развертыванию. Вот шаги для развертывания приложения на Heroku:

1. git init
2. git add .
3. git commit -m "commit message"
4. heroku create 'name of the app as one word'
5. git push heroku master
6. heroku open(to launch the deployed application)

После выполнения этих шагов вы получите приложение, подобное следующему:[этому](http://thirdaysofpython-practice.herokuapp.com/)

## Упражнения: День 26

1. Вы будете создавать [это приложение](https://thirtydaysofpython-v1-final.herokuapp.com/). Осталась только часть с анализом текста.


🎉 ПОЗДРАВЛЯЕМ ! 🎉

[<< День 25 ](../25_Day_Pandas/25_pandas.md) | [День 27 >>](../27_Day_Python_with_mongodb/27_python_with_mongodb.md)
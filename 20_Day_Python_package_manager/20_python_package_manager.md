<div align="center">
  <h1> 30 Дней Python: День 20 - PIP </h1>
  <a href="https://github.com/obulygin/30-Days-Of-Python/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=obulygin/30-Days-Of-Python" />
</div>

[<< День 19](../19_Day_File_handling/19_file_handling.md) | [День 21 >>](../21_Day_Classes_and_objects/21_classes_and_objects.md)

![30DaysOfPython](../images/30daysofpython.png)

- [📘 День 20](#-день-20)
  - [Python PIP - Пакетный меджер Python](#python-pip---пакетный-меджер-python)
    - [Что такое PIP](#что-такое-pip)
    - [Установка PIP](#установка-pip)
    - [Установка пакетов с помощью pip](#установка-пакетов-с-помощью-pip)
    - [Удаление пакетов](#удаление-пакетов)
    - [Установленные пакеты](#установленные-пакеты)
    - [Информация о пакетах](#информация-о-пакетах)
    - [PIP Freeze](#pip-freeze)
    - [Чтение URL](#чтение-url)
    - [Cоздание пакетов](#cоздание-пакетов)
    - [Дополнительная информация о пакетах](#дополнительная-информация-о-пакетах)
  - [Упражнения: День 20](#упражнения-день-20)

# 📘 День 20

## Python PIP - Пакетный меджер Python 

### Что такое PIP

PIP расшифровывается как "Preferred installer program". Мы используем _pip_ для установки различных пакетов, не входящих в стандартную библиотеку Python. Пакет - это модуль Python, который может содержать один или несколько модулей или других пакетов. В программировании нам не обязательно писать каждый раз писать вспомогательную программу, вместо этого мы устанавливаем пакеты и импортируем их в наши приложения.

### Установка PIP

Если у вас нет установленного pip, давайте установим его сейчас. Перейдите в терминал или командную строку и скопируйте следующую команду:

```sh
asabeneh@Asabeneh:~$ pip install pip
```

Проверьте, установлен ли pip, написав

```sh
pip --version
```

```py
asabeneh@Asabeneh:~$ pip --version
pip 21.1.3 from /usr/local/lib/python3.7/site-packages/pip (python 3.9.6)
```

Как видите, я использую версию pip 21.1.3, если вы видите число немного ниже или выше этого, не пугайтесь,  pip установлен.

Давайте посмотрим на популярные пакеты, используемые в сообществе Python для различных целей. Просто, чтобы вы знали, какие из пакетов доступны в Python.

### Установка пакетов с помощью pip

Давайте попробуем установить _numpy_, также известный как "numeric python" - один из самых популярных пакетов в сообществе машинного обучения и data science.

- NumPy - это фундаментальный пакет для научных вычислений с использованием Python. Он содержит:
  - мощный объект многомерного массива
  - сложные функции (например, broadcasting) 
  - инструменты для интеграции кода на C/C++ и Fortran
  - полезные возможности линейной алгебры, преобразования Фурье и генерации случайных чисел

```sh
asabeneh@Asabeneh:~$ pip install numpy
```

Давайте рассмотри numpy поближе. Откройте ваш IDE, выполните импорт numpy следующим образом:

```py
>>> import numpy
>>> numpy.version.version
'1.20.1'
>>> lst = [1, 2, 3,4, 5]
>>> np_arr = numpy.array(lst)
>>> np_arr
array([1, 2, 3, 4, 5])
>>> len(np_arr)
5
>>> np_arr * 2
array([ 2,  4,  6,  8, 10])
>>> np_arr  + 2
array([3, 4, 5, 6, 7])
>>>
```

Pandas - это библиотека с открытым исходным кодом и лицензией BSD, предоставляющая высокопроизводительные и простые в использовании структуры данных и инструменты для анализа данных. Давайте установим старшего брата _numpy_, __pandas__:

```sh
asabeneh@Asabeneh:~$ pip install pandas
```

```py
asabeneh@Asabeneh:~$ python
Python 3.9.6 (default, Jun 28 2021, 15:26:21)
[Clang 11.0.0 (clang-1100.0.33.8)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import pandas
```

Этот раздел не о numpy или pandas, здесь мы пытаемся научиться устанавливать пакеты и импортировать их.  Давайте импортируем модуль веб-браузера, который поможет нам открывать веб-сайты. Нам не нужно устанавливать этот модуль, он уже установлен по умолчанию вместе с Python 3. Это означает, что нам не нужно его устанавливать, мы можем можем его просто импортировать.

```py
import webbrowser # модуль веб-браузера для открытия веб-сайтов

# список URL-адресов: python
url_lists = [
    'http://www.python.org',
    'https://www.linkedin.com/in/asabeneh/',
    'https://github.com/Asabeneh',
    'https://twitter.com/Asabeneh',
]

#  открывает вышеуказанный список веб-сайтов в разных вкладках
for url in url_lists:
    webbrowser.open_new_tab(url)
```

### Удаление пакетов

Для удаления пакета вы можете использовать следующую команду:

```sh
pip uninstall название_пакета
```

### Установленные пакеты

Чтобы увидеть список установленных пакетов на вашем компьютере, вы можете использовать команду pip list.

```sh
pip list
```

### Информация о пакетах

Чтобы получить информацию о пакете, можно использовать команду pip show название_пакета.

```sh
pip show название_пакета
```

```sh
asabeneh@Asabeneh:~$ pip show pandas
Name: pandas
Version: 1.2.3
Summary: Powerful data structures for data analysis, time series, and statistics
Home-page: http://pandas.pydata.org
Author: None
Author-email: None
License: BSD
Location: /usr/local/lib/python3.7/site-packages
Requires: python-dateutil, pytz, numpy
Required-by:
```

Если вы хотите получить более подробную информацию, добавьте --verbose.

```sh
asabeneh@Asabeneh:~$ pip show --verbose pandas
Name: pandas
Version: 1.2.3
Summary: Powerful data structures for data analysis, time series, and statistics
Home-page: http://pandas.pydata.org
Author: None
Author-email: None
License: BSD
Location: /usr/local/lib/python3.7/site-packages
Requires: numpy, pytz, python-dateutil
Required-by:
Metadata-Version: 2.1
Installer: pip
Classifiers:
  Development Status :: 5 - Production/Stable
  Environment :: Console
  Operating System :: OS Independent
  Intended Audience :: Science/Research
  Programming Language :: Python
  Programming Language :: Python :: 3
  Programming Language :: Python :: 3.5
  Programming Language :: Python :: 3.6
  Programming Language :: Python :: 3.7
  Programming Language :: Python :: 3.8
  Programming Language :: Cython
  Topic :: Scientific/Engineering
Entry-points:
  [pandas_plotting_backends]
  matplotlib = pandas:plotting._matplotlib
```

### PIP Freeze

Для создания списка установленных пакетов с версиями, который можно использовать в файле requirements.txt, вы можете использовать команду pip freeze:

```sh
asabeneh@Asabeneh:~$ pip freeze
docutils==0.11
Jinja2==2.7.2
MarkupSafe==0.19
Pygments==1.6
Sphinx==1.2.2
```


### Чтение URL

На данный момент вы знакомы с тем, как читать или записывать файлы на вашем компьютере. Иногда нам хочется прочитать данные с веб-страницы, используя URL, или получить данные из API.
API расшифровывается как Application Program Interface. Это средство обмена структурированными данными между серверами, в основном в формате JSON. Чтобы открыть сетевое соединение, нам понадобится пакет с названием _requests_, который позволяет открывать сетевое соединение и выполнять операции CRUD (create, read, update and delete). В этом разделе мы рассмотрим только операцию чтения или получения данных.

Давайте установим пакет requests:

```py
asabeneh@Asabeneh:~$ pip install requests
```

В модуле requests мы увидим методы get, status_code, headers, text и json:
  - **get()**: для получения данных с URL, он возвращает response object.
  - **status_code**: после получения данных, мы можем проверить статус операции (успех, ошибка и т.д.).
  - **headers**: для проверки типов заголовков.
  - **text**: для извлечения текста из response object.
  - **json**: для извлечения данных в формате JSON.
Давайте прочитаем текстовый файл с веб-сайта https://www.w3.org/TR/PNG/iso_8859-1.txt.

```py
import requests # импортируем модуль requests
url = 'https://www.w3.org/TR/PNG/iso_8859-1.txt' #  текст с веб-сайта

response = requests.get(url) # открываем сетевое соединение и получаем данные
print(response)
print(response.status_code) # status code,, успешно: 200
print(response.headers)     # информация о заголовках
print(response.text) # выводим весь текст с веб-страницы
```

```sh
<Response [200]>
200
{'date': 'Sun, 08 Dec 2019 18:00:31 GMT', 'last-modified': 'Fri, 07 Nov 2003 05:51:11 GMT', 'etag': '"17e9-3cb82080711c0;50c0b26855880-gzip"', 'accept-ranges': 'bytes', 'cache-control': 'max-age=31536000', 'expires': 'Mon, 07 Dec 2020 18:00:31 GMT', 'vary': 'Accept-Encoding', 'content-encoding': 'gzip', 'access-control-allow-origin': '*', 'content-length': '1616', 'content-type': 'text/plain', 'strict-transport-security': 'max-age=15552000; includeSubdomains; preload', 'content-security-policy': 'upgrade-insecure-requests'}
```

- Давайте прочитаем данные из API. Примером API является https://restcountries.eu/rest/v2/all. Посмотрим как это обычно делается с помощью модуля requests.

```py
import requests
url = 'https://restcountries.eu/rest/v2/all'   # API стран
response = requests.get(url)   # открываем сетевое соединение и получаем данные
print(response) # response object
print(response.status_code)  # status code, успешно: 200
countries = response.json()
print(countries[:1])  # выводим только первую страну, удалите срез, чтобы увидеть все страны
```

```sh
<Response [200]>
200
[{'alpha2Code': 'AF',
  'alpha3Code': 'AFG',
  'altSpellings': ['AF', 'Afġānistān'],
  'area': 652230.0,
  'borders': ['IRN', 'PAK', 'TKM', 'UZB', 'TJK', 'CHN'],
  'callingCodes': ['93'],
  'capital': 'Kabul',
  'cioc': 'AFG',
  'currencies': [{'code': 'AFN', 'name': 'Afghan afghani', 'symbol': '؋'}],
  'demonym': 'Afghan',
  'flag': 'https://restcountries.eu/data/afg.svg',
  'gini': 27.8,
  'languages': [{'iso639_1': 'ps',
                 'iso639_2': 'pus',
                 'name': 'Pashto',
                 'nativeName': 'پښتو'},
                {'iso639_1': 'uz',
                 'iso639_2': 'uzb',
                 'name': 'Uzbek',
                 'nativeName': 'Oʻzbek'},
                {'iso639_1': 'tk',
                 'iso639_2': 'tuk',
                 'name': 'Turkmen',
                 'nativeName': 'Türkmen'}],
  'latlng': [33.0, 65.0],
  'name': 'Afghanistan',
  'nativeName': 'افغانستان',
  'numericCode': '004',
  'population': 27657145,
  'region': 'Asia',
  'regionalBlocs': [{'acronym': 'SAARC',
                     'name': 'South Asian Association for Regional Cooperation',
                     'otherAcronyms': [],
                     'otherNames': []}],
  'subregion': 'Southern Asia',
  'timezones': ['UTC+04:30'],
  'topLevelDomain': ['.af'],
  'translations': {'br': 'Afeganistão',
                   'de': 'Afghanistan',
                   'es': 'Afganistán',
                   'fa': 'افغانستان',
                   'fr': 'Afghanistan',
                   'hr': 'Afganistan',
                   'it': 'Afghanistan',
                   'ja': 'アフガニスタン',
                   'nl': 'Afghanistan',
                   'pt': 'Afeganistão'}}]
```

Мы используем метод json() объекта response, если мы получаем данные в формате JSON. Для файлов в форматах txt, html, xml и других мы можем использовать метод text.

### Cоздание пакетов

Мы создаем большое количество файлов в разных папках и подпапках на основе каких-либо критериев, чтобы мы могли легко находить и управлять ими. Как вы знаете, модуль может содержать несколько объектов, таких как классы, функции и т. д. Пакет может содержать один или несколько соответствующих модулей. Фактически пакет представляет собой папку, содержащую один или несколько файлов модулей. Давайте создадим пакет с названием mypackage:

Создайте новую папку с именем **mypackage** внутри папки 30DaysOfPython.
Создайте пустой файл **init.py** в папке mypackage.
Создайте модули **arithmetic.py** и **greet.py** с следующим кодом:

```py
# mypackage/arithmetics.py
# arithmetics.py
def add_numbers(*args):
    total = 0
    for num in args:
        total += num
    return total


def subtract(a, b):
    return (a - b)


def multiple(a, b):
    return a * b


def division(a, b):
    return a / b


def remainder(a, b):
    return a % b


def power(a, b):
    return a ** b
```

```py
# mypackage/greet.py
# greet.py
def greet_person(firstname, lastname):
    return f'{firstname} {lastname}, добро пожаловать на 30DaysOfPython челендж!'
```

Структура папок вашего пакета должна выглядеть следующим образом:

```sh
─ mypackage
    ├── __init__.py
    ├── arithmetic.py
    └── greet.py
```

А сейчас давайте откроем нашу IDE и попробуем использовать созданный нами пакет:

```sh
asabeneh@Asabeneh:~/Desktop/30DaysOfPython$ python
Python 3.9.6 (default, Jun 28 2021, 15:26:21)
[Clang 11.0.0 (clang-1100.0.33.8)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> from mypackage import arithmetics
>>> arithmetics.add_numbers(1, 2, 3, 5)
11
>>> arithmetics.subtract(5, 3)
2
>>> arithmetics.multiple(5, 3)
15
>>> arithmetics.division(5, 3)
1.6666666666666667
>>> arithmetics.remainder(5, 3)
2
>>> arithmetics.power(5, 3)
125
>>> from mypackage import greet
>>> greet.greet_person('Asabeneh', 'Yetayeh')
'Asabeneh Yetayeh, welcome to 30DaysOfPython Challenge!'
>>>
```

Как вы можете видеть, пакет работает великолепно. Папка пакета содержит специальный файл под названием **__init__.py**, который хранит содержимое пакета. Нам нужно поместим файл **__init__.py** в папку, чтобы Python начал распознавать эту папку как пакет. Файл **__init__.py** предоставляет доступ к определенным модулям для импорта. Пустой файл **__init__.py** делает все функции доступными при импорте пакета. Без файла **__init__.py** Python не поймет, что папка является пакетом, а не простой папкой.

### Дополнительная информация о пакетах

- Базы данных
  - SQLAlchemy или SQLObject - доступ к нескольким системам управления базами данных
    - _pip install SQLAlchemy_
- Веб-разработка
  - Django - высокоуровневый веб-фреймворк.
    - _pip install django_
  - Flask - микро-фреймворк для Python, основанный на Werkzeug и Jinja 2.
    - _pip install flask_
- Парсер HTML
  - [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) - парсер HTML/XML, разработанный для быстрого извлечения данных, можно использовать даже для файлов с неправильной разметкой.
    - _pip install beautifulsoup4_
  - PyQuery - реализует jQuery в Python; быстрее BeautifulSoup.

- Обработка XML
  - ElementTree - модуль в стандартной библиотеке Python, который предоставляет простой и удобный способ для обработки XML-документов. Он представляет собой легковесный и эффективный API для работы с XML, который позволяет создавать, изменять и извлекать данные из XML-структур.
- GUI
  - PyQt - привязки к кросс-платформенному фреймворку Qt.
  - TkInter - традиционный набор инструментов пользовательского интерфейса Python.
- Анализ данных, Data Science and машинное обучение
  - NumPy: одна из самых популярных библиотек машинного обучения в Python.
  - Pandas: библиотека для анализа данных, Data Science и машинного обучения в Python, которая предоставляет высокоуровневые структуры данных и широкий набор инструментов для анализа.
  - SciPy: SciPy  библиотека машинного обучения для разработчиков приложений и инженеров. Библиотека SciPy содержит модули для оптимизации, линейной алгебры, интеграции, обработки изображений и статистики.
  - Scikit-Learn: комбинация NumPy и SciPy. Она считается одной из лучших библиотек для работы со комплексными данными.
  - TensorFlow: библиотека машинного обучения, созданная Google.
  - Keras: одна из самых популярных библиотек машинного обучения в Python. Она предоставляет удобный и интуитивно понятный интерфейс для создания и обучения нейронных сетей. Keras облегчает процесс описания архитектуры нейронной сети и предлагает мощные инструменты для компиляции моделей, обработки наборов данных, визуализации графов и многого другого. Keras также является высокоуровневым интерфейсом к другой популярной библиотеке машинного обучения - TensorFlow, что позволяет использовать преимущества обеих библиотек вместе.
- Network:
  - requests: пакет, который мы можем использовать для отправки запросов на сервер с использованием различных методов, таких как GET, POST, DELETE, PUT.
    - _pip install requests_

🌕 Как всегда, ты молодец! Только что ты сделал 20 шаг к своей мечте. А теперь давай снова потренируем свои мозги!

## Упражнения: День 20

1. Прочитайте этот URL и найдите 10 наиболее часто встречающихся слов. romeo_and_juliet = 'http://www.gutenberg.org/files/1112/1112.txt'
2. Прочитайте API cats_api = 'https://api.thecatapi.com/v1/breeds' и найдите:
   1. минимальный, максимальный, средний, медианный вес кошек.
   2. минимальную, максимальную, среднюю, медианную продолжительность жизни кошек в годах.
   3. Создайте таблицу частоты стран и породы кошек.
3. Прочитайте [API стран](https://restcountries.eu/rest/v2/all) и найдите:
   1. 10 самых больших стран
   2. 10 наиболее распространенных языков
   3. бщее количество языков в API стран
4. UCI одно из самых распространенных мест для получения наборов данных для data science и машинного обучения. Прочтите содержимое UCL(https://archive.ics.uci.edu/ml/datasets.php). Без дополнительных библиотек это будет сложно, поэтому вы можете попробовать использовать BeautifulSoup4.

🎉 ПОЗДРАВЛЯЕМ! 🎉

[<< День 19](../19_Day_File_handling/19_file_handling.md) | [День 21 >>](../21_Day_Classes_and_objects/21_classes_and_objects.md)

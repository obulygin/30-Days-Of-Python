<div align="center">
  <h1> 30 Дней Python: День 19 - Работа с файлами </h1>
  <a href="https://github.com/obulygin/30-Days-Of-Python/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=obulygin/30-Days-Of-Python" />
</div>

[<< День 18](../18_Day_Regular_expressions/18_regular_expressions.md) | [День 20 >>](../20_Day_Python_package_manager/20_python_package_manager.md)

![30DaysOfPython](../images/30daysofpython.png)

- [📘 День 19](#-день-19)
  - [Работа с файлами](#работа-с-файлами)
    - [Открытие файлов для чтения](#открытие-файлов-для-чтения)
    - [Открытие файлов для записи и обновления](#открытие-файлов-для-записи-и-обновления)
    - [Удаление файла](#удаление-файла)
  - [Типы файлов](#типы-файлов)
    - [Файл с форматом txt](#файл-с-форматом-txt)
    - [Файл с форматом json](#файл-с-форматом-json)
    - [Преобразование JSON в словарь](#преобразование-json-в-словарь)
    - [Преобразование словаря в JSON](#преобразование-словаря-в-json)
    - [Сохранение в файле JSON](#сохранение-в-файле-json)
    - [Файл с форматом csv](#файл-с-форматом-csv)
    - [Файл с форматом xlsx](#файл-с-форматом-xlsx)
    - [Файл с форматом xml](#файл-с-форматом-xml)
  - [💻 Упражнения: День 19](#-упражнения-день-19)
    - [Упражнения: Уровень 1](#упражнения-уровень-1)
    - [Упражнения: Уровень 2](#упражнения-уровень-2)

# 📘 День 19

## Работа с файлами

До сегодняшнего дня мы рассмотрели большое количество типов данных в Python.  В этом разделе мы рассмотрим форматы файлов(.txt, .json, .xml, .csv, .tsv, .excel), в которых мы можем хранить данные. 

Давайте рассмотрим работу с форматом файла .txt

Работа с файлами - важная часть программирования, которая позволяет нам создавать, читать, обновлять и удалять файлы. В Python для работы с данными мы используем встроенную функцию open().

```py
# Синтаксис
open('filename', mode) # mode(r, a, w, x, t,b). Благодаря моду мы можем прочитать, записать или обновить файл. 
```

- "r" - Read - Значение по умолчанию. Открывает файл для чтения, возвращает ошибку, если файл не существует.
- "a" - Append - Открывает файл для добавления данных, создает файл, если он не существует.
- "w" - Write - Открывает файл для записи, создает файл, если он не существует.
- "x" - Create - Создает файл, возвращает ошибку, если файл уже существует.
- "t" - Text -Значение по умолчанию. Режим текста.
- "b" - Binary - Режим бинарных данных (например, изображения).

### Открытие файлов для чтения

Для открытия файла мы используем функцию open(), режимом по умолчанию является чтение, поэтому нам не нужно указывать 'r' или 'rt'. Я создал и сохранил файл с именем reading_file_example.txt в директории files. Давайте посмотрим, как его открыть:

```py
f = open('./files/reading_file_example.txt')
print(f) # <_io.TextIOWrapper name='./files/reading_file_example.txt' mode='r' encoding='UTF-8'>
```

Как вы можете видеть в приведенном выше примере, я вывел открытый файл, и он дал некоторую информацию о нем. Открытый файл имеет методы для взаимодействия с ним: read(), readline(), readlines(). После всех необходимых действий открытый файл должен быть закрыт с помощью метода close().

- _read()_: читает весь текст в виде строки. Если мы хотим ограничить количество считываемых символов, мы можем передать число методу read().

```py
f = open('./files/reading_file_example.txt')
txt = f.read()
print(type(txt))
print(txt)
f.close()
```

```sh
# выведет
<class 'str'>
Пример, который показывает открытие и чтение файла.
Это вторая строка файла.
```

Вместо вывода всего текста, давайте выведем первые 10 символов из текстового файла.

```py
f = open('./files/reading_file_example.txt')
txt = f.read(10)
print(type(txt))
print(txt)
f.close()
```

```sh
# выводит
<class 'str'>
Пример, вт
```

- *readline()*: читает только первую строку.

```py
f = open('./files/reading_file_example.txt')
line = f.readline()
print(type(line))
print(line)
f.close()
```

```sh
# выводит
<class 'str'>
Пример, который показывает открытие и чтение файла.
```

- _readlines()_: : читает весь текст построчно и возвращает список строк.

```py
f = open('./files/reading_file_example.txt')
lines = f.readlines()
print(type(lines))
print(lines)
f.close()
```

```sh
# вывод
<class 'list'>
['Пример, который показывает открытие и чтение файла.\n', 'Это вторая строка файла.']
```

Еще один способ получить все строки в виде списка - использовать метод  _splitlines()_:

```py
f = open('./files/reading_file_example.txt')
lines = f.read().splitlines()
print(type(lines))
print(lines)
f.close()
```

```sh
# выводит
<class 'list'>
['Пример, который показывает открытие и чтение файла.\n', 'Это вторая строка файла.']
```

После открытия файла мы должны его закрыть. Часто бывает, что мы забываем закрыть файлы. Существует дургой способ открытия файлов с помощью конструкции with, которая автоматически закрывает файлы. Давайте перепишем предыдущий пример с использованием метода with:

```py
with open('./files/reading_file_example.txt') as f:
    lines = f.read().splitlines()
    print(type(lines))
    print(lines)
```

```sh
# выводит
<class 'list'>
['Пример, который показывает открытие и чтение файла.\n', 'Это вторая строка файла.']
```

### Открытие файлов для записи и обновления

Для записи в файл мы должны добавить режим в качестве параметра функции open():

- "a" - append - добавит данные в конец файла, если файл не существует, он будет создан.
- "w" - write - перезапишет существующее содержимое файла, если файл не существует, он будет создан.

Давайте рассмотрим примеры:

```py
with open('./files/reading_file_example.txt','a') as f:
    f.write('Этот текст добавлен в конец')
```

Следующий метод создает новый файл, если файл не существует:

```py
with open('./files/writing_file_example.txt','w') as f:
    f.write('Этот текс будет добавлен в созданный файл')
```

### Удаление файла

В предыдущих разделах мы уже видели как создавать и удалять каталоги с помощью модуля os. Сейчас нам придется снова обратиться к этому модулю. 

```py
import os
os.remove('./files/example.txt')
```

Если файл не существует, метод remove вернет ошибку, чтобы этого избежать мы можем использовать условные конструкции, например, такое:

```py
import os
if os.path.exists('./files/example.txt'):
    os.remove('./files/example.txt')
else:
    print('Файл не существует')
```

## Типы файлов

### Файл с форматом txt

Файл с форматом txt является очень распространенной формой данных, и мы уже рассмотрели его в предыдущем разделе. Давайте перейдем к формату JSON.

### Файл с форматом json

JSON означает JavaScript Object Notation (Формат объектов JavaScript). Фактически, это строка, представляющая собой сериализованный объект JavaScript или словарь Python.

_Пример:_

```py
# словарь
person_dct= {
    "name":"Asabeneh",
    "country":"Finland",
    "city":"Helsinki",
    "skills":["JavaScrip", "React","Python"]
}
# JSON: строка из словаря
person_json = "{'name': 'Asabeneh', 'country': 'Finland', 'city': 'Helsinki', 'skills': ['JavaScrip', 'React', 'Python']}"

# Мы используем три кавычки и улучшаем его читаемость
person_json = '''{
    "name":"Asabeneh",
    "country":"Finland",
    "city":"Helsinki",
    "skills":["JavaScrip", "React","Python"]
}'''
```

### Преобразование JSON в словарь

Для преобразования JSON в словарь мы сначала импортируем модуль json, а затем используем метод *loads()*.

```py
import json
# JSON
person_json = '''{
    "name": "Asabeneh",
    "country": "Finland",
    "city": "Helsinki",
    "skills": ["JavaScrip", "React", "Python"]
}'''
# давайте преобразуем JSON в словарь
person_dct = json.loads(person_json)
print(type(person_dct))
print(person_dct)
print(person_dct['name'])
```

```sh
# вывод
<class 'dict'>
{'name': 'Asabeneh', 'country': 'Finland', 'city': 'Helsinki', 'skills': ['JavaScrip', 'React', 'Python']}
Asabeneh
```

### Преобразование словаря в JSON

To change a dictionary to a JSON we use _dumps_ method from the json module.

```py
import json
# словарь
person = {
    "name": "Asabeneh",
    "country": "Finland",
    "city": "Helsinki",
    "skills": ["JavaScrip", "React", "Python"]
}
# давайте преобразуем его в JSON
person_json = json.dumps(person, indent=4) # indent может быть равен 2, 4, 8. Он означает отступы и делает JSON более читаемым
print(type(person_json))
print(person_json)
```

```sh
# выводит
# когда вы выводите эту переменную, у неё нет кавычек, но на самом деле это строка
# JSON не имеет типа, он является строковым типом.
<class 'str'>
{
    "name": "Asabeneh",
    "country": "Finland",
    "city": "Helsinki",
    "skills": [
        "JavaScrip",
        "React",
        "Python"
    ]
}
```

### Сохранение в файле JSON

Мы также можем сохранить наши данные в файле JSON. Давайте попробуем это сделать! Для записи файла JSON мы используем метод json.dump(), он может принимать словарь, выходной файл, ensure_ascii и indent.

```py
import json
# словарь
person = {
    "name": "Asabeneh",
    "country": "Finland",
    "city": "Helsinki",
    "skills": ["JavaScrip", "React", "Python"]
}
with open('./files/json_example.json', 'w', encoding='utf-8') as f:
    json.dump(person, f, ensure_ascii=False, indent=4)
```

В приведенном выше коде мы используем кодировку (encoding) и отступ (indent). Отступ облегчает читаемость файла JSON.

### Файл с форматом csv

CSV означает "comma separated values" (значения, разделенные запятыми). CSV - это простой формат файла, используемый для хранения табличных данных, таких как таблица или база данных. CSV является очень распространенным форматом данных в data science.

**Пример:**

```csv
"name","country","city","skills"
"Asabeneh","Finland","Helsinki","JavaScript"
```

**Example:**

```py
import csv
with open('./files/csv_example.csv') as f:
    csv_reader = csv.reader(f, delimiter=',') # мы используем метод reader для чтения csv
    line_count = 0
    for row in csv_reader:
        if line_count == 0:
            print(f'Названия столбцов: {", ".join(row)}')
            line_count += 1
        else:
            print(
                f'\t{row[0]} - учитель. Он живет в  {row[1]}, {row[2]}.')
            line_count += 1
    print(f'Количество строк:  {line_count}')
```

```sh
# output:
Названия столбцов: name, country, city, skills
        Asabeneh - учитель. Он живет в Finland, Helsinki.
Количество строк:   2
```

### Файл с форматом xlsx

Для чтения файлов Excel нам необходимо установить пакет *xlrd*. Мы рассмотрим это после того, как рассмотрим установку пакетов с помощью pip.

```py
import xlrd
excel_book = xlrd.open_workbook('sample.xls)
print(excel_book.nsheets)
print(excel_book.sheet_names)
```

### Файл с форматом xml

XML - это еще один структурированный формат данных, который похож на HTML. В XML теги не предопределены. Первая строка - это объявление XML. Тег "person" является корневым элементом XML. У "person" есть атрибут "gender".

**Пример: XML**

```xml
<?xml version="1.0"?>
<person gender="female">
  <name>Asabeneh</name>
  <country>Finland</country>
  <city>Helsinki</city>
  <skills>
    <skill>JavaScrip</skill>
    <skill>React</skill>
    <skill>Python</skill>
  </skills>
</person>
```

Для получения дополнительной информации о том, как читать файл XML, ознакомьтесь с [документацией](https://docs.python.org/2/library/xml.etree.elementtree.html)

```py
import xml.etree.ElementTree as ET
tree = ET.parse('./files/xml_example.xml')
root = tree.getroot()
print('Root tag:', root.tag)
print('Attribute:', root.attrib)
for child in root:
    print('field: ', child.tag)
```

```sh
# выводит
Root tag: person
Attribute: {'gender': 'male'}
field: name
field: country
field: city
field: skills
```

🌕 Вы добились больших результатов. Не останавливайтесь на достигнутом, впереди Вас ждут ещё большие успехи! А теперь давайте немного поупражняемся.

## 💻 Упражнения: День 19

### Упражнения: Уровень 1

1. Напишите функцию, которая подсчитывает количество строк и количество слов в тексте. Все файлы находятся в папке "data":
   a) Прочитайте файл "obama_speech.txt" и подсчитайте количество строк и слов.
   b) Прочитайте файл "michelle_obama_speech.txt" и подсчитайте количество строк и слов.
   c) Прочитайте файл "donald_speech.txt" и подсчитайте количество строк и слов.
   d) Прочитайте файл "melina_trump_speech.txt" и подсчитайте количество строк и слов.
2. Прочитайте файл "countries_data.json" в папке "data" и создайте функцию, которая найдет десять самых распространенных языков.

   ```py
   # Ваш результат должен выглядеть следующим образом
   print(most_spoken_languages(filename='./data/countries_data.json', 10))
   [(91, 'English'),
   (45, 'French'),
   (25, 'Arabic'),
   (24, 'Spanish'),
   (9, 'Russian'),
   (9, 'Portuguese'),
   (8, 'Dutch'),
   (7, 'German'),
   (5, 'Chinese'),
   (4, 'Swahili'),
   (4, 'Serbian')]

   # Ваш результат должен выглядеть следующим образом
   print(most_spoken_languages(filename='./data/countries_data.json', 3))
   [(91, 'English'),
   (45, 'French'),
   (25, 'Arabic')]
   ```

3. Прочитайте файл "countries_data.json" в папке "data" и создайте функцию, которая создает список десяти наиболее населенных стран.

   ```py
   # Ваш результат должен выглядеть следующим образом
   print(most_populated_countries(filename='./data/countries_data.json', 10))

   [
   {'country': 'China', 'population': 1377422166},
   {'country': 'India', 'population': 1295210000},
   {'country': 'United States of America', 'population': 323947000},
   {'country': 'Indonesia', 'population': 258705000},
   {'country': 'Brazil', 'population': 206135893},
   {'country': 'Pakistan', 'population': 194125062},
   {'country': 'Nigeria', 'population': 186988000},
   {'country': 'Bangladesh', 'population': 161006790},
   {'country': 'Russian Federation', 'population': 146599183},
   {'country': 'Japan', 'population': 126960000}
   ]

   # Ваш результат должен выглядеть следующим образом

   print(most_populated_countries(filename='./data/countries_data.json', 3))
   [
   {'country': 'China', 'population': 1377422166},
   {'country': 'India', 'population': 1295210000},
   {'country': 'United States of America', 'population': 323947000}
   ]
   ```

### Упражнения: Уровень 2

4. Извлеките все входящие адреса электронной почты в виде списка из файла "email_exchange_big.txt".
5. Найдите наиболее часто встречающиеся слова в английском языке. Назовите свою функцию find_most_common_words. Она должна принимать два параметра: строку или файл и положительное целое число, указывающее количество слов. Ваша функция будет возвращать массив кортежей в порядке убывания. Проверьте вывод.

```py
    # Ваш результат должен выглядеть следующим образом
    print(find_most_common_words('sample.txt', 10))
    [(10, 'the'),
    (8, 'be'),
    (6, 'to'),
    (6, 'of'),
    (5, 'and'),
    (4, 'a'),
    (4, 'in'),
    (3, 'that'),
    (2, 'have'),
    (2, 'I')]

    # Ваш результат должен выглядеть следующим образом
    print(find_most_common_words('sample.txt', 5))

    [(10, 'the'),
    (8, 'be'),
    (6, 'to'),
    (6, 'of'),
    (5, 'and')]
```

6. Используйте функцию find_most_frequent_words для поиска:
   a) Десяти наиболее часто встречающихся слов в [Obama's speech](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/obama_speech.txt)
   b) Десяти наиболее часто встречающихся слов в [Michelle's speech](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/michelle_obama_speech.txt)
   c) Десяти наиболее часто встречающихся слов в [Trump's speech](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/donald_speech.txt)
   d) Десяти наиболее часто встречающихся слов в [Melina's speech](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/melina_trump_speech.txt)
7. Напишите приложение на Python, которое проверяет сходство между двумя текстами. Оно принимает файл или строку в качестве параметра и оценивает сходство двух текстов. Например, проверьте сходство между текстами [Michelle's](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/michelle_obama_speech.txt) и [Melina's](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/melina_trump_speech.txt). Вам может понадобиться несколько функций: функция для очистки текста (clean_text), функция для удаления служебных слов (remove_support_words) и, наконец, функция для проверки сходства (check_text_similarity). Список [stop words](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/stop_words.py) находится в директории data.
8. Найти 10 наиболее часто повторяющихся слов в файле "romeo_and_juliet.txt".
9. Прочитайте файл [hacker news csv](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/hacker_news.csv) и определите:
   a) Количество строк, содержащих "python" или "Python".
   b) Количество строк, содержащих "JavaScript", "javascript" или "Javascript".
   c) Количество строк, содержащих "Java", но не "JavaScript".


🎉 ПОЗДРАВЛЯЕМ ! 🎉

[<< День 18](../18_Day_Regular_expressions/18_regular_expressions.md) | [День 20 >>](../20_Day_Python_package_manager/20_python_package_manager.md)

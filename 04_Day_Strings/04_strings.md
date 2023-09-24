<div align="center">
  <h1> 30 Дней Python: День 4 - Строки</h1>
  <a href="https://github.com/obulygin/30-Days-Of-Python/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=obulygin/30-Days-Of-Python" />
</div>

[<< День 3](../03_Day_Operators/03_operators.md) | [День 5 >>](../05_Day_Lists/05_lists.md)

![30DaysOfPython](../images/30daysofpython.png)

- [День 4](#день-4)
  - [Строки](#строки)
    - [Создание строк](#создание-строк)
    - [Конкатенация строк](#конкатенация-строк)
    - [Экранирование последовательностей](#экранирование-последовательностей)
    - [Форматирование строк](#форматирование-строк)
      - [Старый стиль форматирования строк (% Оператор)](#старый-стиль-форматирования-строк--оператор)
      - [Новый стиль форматирования строк (str.format)](#новый-стиль-форматирования-строк-strformat)
      - [Интерполяция строк / f-строки (Python 3.6+)](#интерполяция-строк--f-строки-python-36)
    - [Строки в Python как последовательности символов](#строки-в-python-как-последовательности-символов)
      - [Распаковка строк](#распаковка-строк)
      - [Доступ к символам в строках по индексу](#доступ-к-символам-в-строках-по-индексу)
      - [Срезы строк в Python](#срезы-строк-в-python)
      - [Разворот строки](#разворот-строки)
      - [Пропуск символов в срезах](#пропуск-символов-в-срезах)
    - [Методы строк](#методы-строк)
  - [💻 Exercises - Day 4](#-exercises---day-4)

# День 4

## Строки

Текс является типом данных "строка"(string). Любой тип данных, записанный в виде текста, является строкой. Любые данные, заключенные в одинарные, двойные или тройные кавычки, являются строками. В Python существуют различные методы строк и встроенные функции для работы с данными типа "строка". Чтобы проверить длину строки, используйте метод len().

### Создание строк

```py
letter = 'P'                # Строка может быть как одним символом, так и набором из символов (текстом)
print(letter)               # P
print(len(letter))          # 1
greeting = 'Hello, World!'  # Строку можно создать используя одинарные или двойные кавычки,"Hello, World!"
print(greeting)             # Hello, World!
print(len(greeting))        # 13
sentence = "Надеюсь, Вам нравится 30 дней испытаний Python."
print(sentence)
```

Многострочную строку можно создать используя тройные одинарные(''') или тройные двойные кавычки("""). 

Пример:

```py
multiline_string = '''Я - учитель и наслаждаюсь преподаванием.
Я не нашел ничего такого, что было бы столь же благотворным, как наделение людей знаниями.
Вот почему я создал 30 дней Python.'''
print(multiline_string)

# Another way of doing the same thing
multiline_string = """Я - учитель и наслаждаюсь преподаванием.
Я не нашел ничего такого, что было бы столь же благотворным, как наделение людей знаниями.
Вот почему я создал 30 дней Python."""
print(multiline_string)
```

### Конкатенация строк

Мы можем объединять строки. Объединение или соединение строк называется конкатенацией.

Пример:

```py
first_name = 'Питер'
last_name = 'Паркер'
space = ' '
full_name = first_name  +  space + last_name
print(full_name) # Питер Паркер
# Проверка длинны строки с помощью встроенной функции len()
print(len(first_name))  # 5
print(len(last_name))   # 6
print(len(last_name) > len(first_name)) # True
print(len(full_name)) # 12
```

### Экранирование последовательностей

В Python и других языках программирования обратная косая черта \ за которой следует символ, является экранированной последовательностью. 

Давайте взглянем на наиболее распространенные экранированные символы:

- \n: Переход на новую строку
- \t: Горизонтальная табуляция (2-4 пробела)
- \\\\: Обратная косая черта
- \\': Одинарные кавычки (')
- \\": Двойные кавычки (")

А теперь взглянем на пример:

```py
print('Я надеюсь, что каждый получает удовольствие от Python Challenge.\nА вы получаете?') # Перенос строки
print('Дни\tТемы\tУпражнения') # Добавление табуляции или 4-х пробелов 
print('День 1\t3\t5')
print('День 2\t3\t5')
print('День 3\t3\t5')
print('День 4\t3\t5')
print('Это символ обратной косой черты (\\)') # Запись обратной косой черты
print('Изучения языков программирования принято начинать с фразы \"Hello, World!\"') # Запись двойных кавычек внутри одинарных
# такой код выведет:
Я надеюсь, что каждый получает удовольствие от Python Challenge.
А вы получаете?
Дни	 Темы	 Упражнения
День 1	5	    5
День 2	6	    20
День 3	5	    23
День 4	1	    35
Это символ обратной косой черты (\)
Изучения языков программирования принято начинать с фразы "Hello, World!"
```

### Форматирование строк

#### Старый стиль форматирования строк (% Оператор)

В Python существует множество способов форматирования строк. Сейчас мы рассмотрим некоторые из них. Оператор "%" используется для форматирования набора переменных объединенных в кортеж (tuple), вместе с форматирующей строкой, которая содержит обычный текст со "спецификаторами аргументов" - специальными символами, такими как "%s", "%d", "%f", "<small>number of digits</small>".

- %s - Строка (или любой объект со строковым представлением, например, числа)
- %d - Целые числа
- %f - Числа с плавающей точкой
- "%.<small>number of digits</small>f" - Числа с плавающей точкой с фиксированной точностью

```py
# Только строки
first_name = 'Питер'
last_name = 'Паркер'
language = 'Python'
formated_string = 'Меня зовут %s %s. Я учитель языка программирования %s.' %(first_name, last_name, language)
print(formated_string) # Меня зовут Питер Паркер. Я учитель языка программирования Python.

# Строки и числа
radius = 10
pi = 3.14
area = pi * radius ** 2
formated_string = 'Площадь круга с радиусом %d равна %.2f.' %(radius, area) # 2 указывает на 2 значащие цифры после точки

python_libraries = ['Django', 'Flask', 'NumPy', 'Matplotlib','Pandas']
formated_string = 'Есть разные библиотеки pythonю Вот некоторые из них:%s' % (python_libraries)
print(formated_string) # "Есть разные библиотеки pythonю Вот некоторые из них:['Django', 'Flask', 'NumPy', 'Matplotlib','Pandas']"
```

#### Новый стиль форматирования строк (str.format)

Этот способ форматирования строк с использованием метода format() был введен в Python версии 3. Он предоставляет более гибкий и универсальный подход к форматированию строк по сравнению с предыдущим методом оператора %.

```py

first_name = 'Питер'
last_name = 'Паркер'
language = 'Python'
formated_string = 'Меня зовут {} {}. Я учитель языка программирования {}.'.format(first_name, last_name, language)
print(formated_string) # Меня зовут Питер Паркер. Я учитель языка программирования Python.

a = 4
b = 3

print('{} + {} = {}'.format(a, b, a + b))
print('{} - {} = {}'.format(a, b, a - b))
print('{} * {} = {}'.format(a, b, a * b))
print('{} / {} = {:.2f}'.format(a, b, a / b)) # ограничивает количество цифр после запятой до двух.
print('{} % {} = {}'.format(a, b, a % b))
print('{} // {} = {}'.format(a, b, a // b))
print('{} ** {} = {}'.format(a, b, a ** b))

# Выводит
4 + 3 = 7
4 - 3 = 1
4 * 3 = 12
4 / 3 = 1.33
4 % 3 = 1
4 // 3 = 1
4 ** 3 = 64

# Строки и числа
radius = 10
pi = 3.14
area = pi * radius ** 2
formated_string = 'Площадь круга радиусом {} составляет {:.2f}.'.format(radius, area) # 2 числа после запятой
print(formated_string)

```

#### Интерполяция строк / f-строки (Python 3.6+)

Еще один способ форматирования строк - это интерполяция строк с помощью f-строк. Строки начинаются с буквы "f" и дают возможность вставлять данные в соответствующие позиции внутри строк. 

```py
a = 4
b = 3
print(f'{a} + {b} = {a +b}')
print(f'{a} - {b} = {a - b}')
print(f'{a} * {b} = {a * b}')
print(f'{a} / {b} = {a / b:.2f}')
print(f'{a} % {b} = {a % b}')
print(f'{a} // {b} = {a // b}')
print(f'{a} ** {b} = {a ** b}')
```

### Строки в Python как последовательности символов

Строки в Python являются последовательностями символов и обладают базовыми методами, схожими с другими упорядоченными последовательностями объектов в Python, такими как списки и кортежи. Самый простой способ извлечения отдельных символов из строк (а также отдельных элементов из любой последовательности) - это распаковка их в соответствующие переменные.

#### Распаковка строк

```py
language = 'Python'
a,b,c,d,e,f = language # распаковка строки в последовательность переменные
print(a) # P
print(b) # y
print(c) # t
print(d) # h
print(e) # o
print(f) # n
```


#### Доступ к символам в строках по индексу

В программировании нумерация начинается с нуля. Поэтому первая буква строки находится по индексу 0, а последняя буква - по индексу длины строки минус один.

![String index](../images/string_index.png)

```py
language = 'Python'
first_letter = language[0]
print(first_letter) # P
second_letter = language[1]
print(second_letter) # y
last_index = len(language) - 1
last_letter = language[last_index]
print(last_letter) # n
```

Если мы хотим начать с конца строки, мы можем использовать отрицательный индекс. -1 обозначает индекс последнего символа, -2 индекс второго символа с конца и т.д.

```py
language = 'Python'
last_letter = language[-1]
print(last_letter) # n
second_last = language[-2]
print(second_last) # o
```

#### Срезы строк в Python

В Python мы можем брать срезы от строк путем обращения к индексам этой строки.

```py
language = 'Python'
first_three = language[0:3] # начинаем с нулевого индекса включительно и идем до 3 невключительно. 
print(first_three) #Pyt
last_three = language[3:6]
print(last_three) # hon
# Другой способ
last_three = language[-3:]
print(last_three)   # hon
last_three = language[3:]
print(last_three)   # hon
```

#### Разворот строки

В Python мы можем с легкостью развернуть строку!

```py
greeting = 'Hello, World!'
print(greeting[::-1]) # !dlroW ,olleH
```

#### Пропуск символов в срезах

Мы  можем пропускать некоторые символы в срезах благодаря шагу среза.

```py
language = 'Python'
pto = language[0:6:2] # берем 0, 2 и 4 индексы
print(pto) # Pto
```

### Методы строк

В Python существует множество методок строк, которые позволяют нам форматировать строки. Давайте рассмотрим некоторые из них:

- capitalize(): Преобразует первый символ строки в заглавную букву.

```py
challenge = 'тридцать дней Python'
print(challenge.capitalize()) # 'Тридцать дней Python'
```

- count(): Возвращает количество вхождений подстроки в строку. Метод имеет следующий синтаксис: count(substring, start=..., end=...). Аргумент start принимает начальный индекс, а аргумент end принимает последний индекс, где будет вестись поиск подстроки.

```py
challenge = 'тридцать дней python'
print(challenge.count('т')) # 2
print(challenge.count('д', 7, 14)) # 1, 
print(challenge.count('th')) # 1
```

- endswith(): Проверяет, заканчивается ли строка указанным набором символов

```py
challenge = 'тридцать дней python'
print(challenge.endswith('on'))   # True
print(challenge.endswith('tion')) # False
```

- expandtabs(): Заменяет символ табуляции пробелами. Размер табуляции по умолчанию равен 8, а данный метод принимает аргумент и изменяет размер табуляции.

```py
challenge = 'тридцать\tдней\tpython'
print(challenge.expandtabs())   # 'тридцать  дней      python'
print(challenge.expandtabs(10)) # 'тридцать    дней        python'
```

- find(): Возвращает индекс первого вхождения подстроки, если подстрока не найдена, возвращает -1.

```py
challenge = 'традцать дней python'
print(challenge.find('y'))  # 15
print(challenge.find('th')) # 16
```

- rfind(): Возвращает индекс последнего вхождения подстроки, если подстрока не найдена, возвращает -1.

```py
challenge = 'тридцать дней python вместе'
print(challenge.rfind('т'))  # 6
print(challenge.rfind('е')) # 26
```

- format(): форматирует строку для более красивого вывода. 
   Подробнее о форматировании строк можно узнать по [ссылке](https://www.programiz.com/python-programming/methods/string/format).

```py
first_name = 'Питер'
last_name = 'Паркер'
age = 250
job = 'учитель'
country = 'Италия'
sentence = 'Меня зовут {} {}. Мне {} лет. Я {}. Моя любимая страна {}.'.format(first_name, last_name, age, job, country)
print(sentence) # Меня зовут Питер Паркер. Мне 250 лет. Я учитель. Моя любимая страна Италия.

radius = 10
pi = 3.14
area = pi * radius ** 2
result = 'Окружность круга с радиусом {} равна {}'.format(str(radius), str(area))
print(result) # Окружность круга с радиусом 10 равна 314
```

- index(): Возвращает наименьший индекс подстроки. В качестве дополнительных аргументов могут выступать начальный и конечный индексы. Если подстрока не найдена, возвращает ошибку valueError. 

```py
challenge = 'тридцать дней python'
sub_string = 'ца'
print(challenge.index(sub_string))  # 4
print(challenge.index(sub_string, 5)) # error
```

- rindex(): Возвращает наибольший индекс подстроки. В качестве дополнительных аргументов также могут выступать начальный и конечный индексы.

```py
challenge = 'thirty days of python'
sub_string = 'da'
print(challenge.rindex(sub_string))  # 8
print(challenge.rindex(sub_string, 9)) # error
```

- isalnum(): Проверяет, содержит ли строка только буквенно-цифровые символы.

```py
challenge = 'ТридцатьДнейPython'
print(challenge.isalnum()) # True

challenge = '30ДнейPython'
print(challenge.isalnum()) # True

challenge = 'тридцать дней python'
print(challenge.isalnum()) # False, пробел не является буквенно-цифровым символом

challenge = 'тридцать дней python 2019'
print(challenge.isalnum()) # False
```

- isalpha(): Проверяет, состоит ли строка только из буквенных символов.

```py
challenge = 'тридцать дней python'
print(challenge.isalpha()) # False, пробел снова не включается
challenge = 'ТридцатьДнейPython'
print(challenge.isalpha()) # True
num = '123'
print(num.isalpha())      # False
```

- isdecimal(): Проверяет, являются ли все символы в строке из десятичных цифр (от 0 до 9).

```py
challenge = 'тридцать дней python'
print(challenge.isdecimal())  # False
challenge = '123'
print(challenge.isdecimal())  # True
challenge = '\u00B2'
print(challenge.isdigit())   # False
challenge = '12 3'
print(challenge.isdecimal())  # False, пробел не допускается
```

- isdigit(): Проверяет, являются ли все символы в строке числами (от 0 до 9 и некоторми другми символами Юникода, представляющими числа).

```py
challenge = 'Тридцать'
print(challenge.isdigit()) # False
challenge = '30'
print(challenge.isdigit())   # True
challenge = '\u00B2'
print(challenge.isdigit())   # True
```

- isnumeric(): Проверяет, являются ли все символы в строке числами или связаными с числами символами(аналогично isdigit(), но принимает больше символов, например, ½).

```py
num = '10'
print(num.isnumeric()) # True
num = '\u00BD' # ½
print(num.isnumeric()) # True
num = '10.5'
print(num.isnumeric()) # False
```

- isidentifier(): Проверяет, является ли строка допустимым именем переменной.

```py
challenge = '30DaysOfPython'
print(challenge.isidentifier()) # False, потому что начинается с числа
challenge = 'thirty_days_of_python'
print(challenge.isidentifier()) # True
```

- islower(): Проверяет, являются ли все буквы в строке __строчными__.

```py
challenge = 'тридцать дней python'
print(challenge.islower()) # True
challenge = 'Тридцать дней python'
print(challenge.islower()) # False
```

- isupper(): Проверяет, являются ли все буквы в строке __заглавными__.

```py
challenge = 'тридцать дней python'
print(challenge.isupper()) #  False
challenge = 'ТРИДЦАТЬ ДНЕЙ PYTHON'
print(challenge.isupper()) # True
```

- join(): Возвращает объединенную строку.

```py
web_tech = ['HTML', 'CSS', 'JavaScript', 'React']
result = ' '.join(web_tech)
print(result) # 'HTML CSS JavaScript React'
```

```py
web_tech = ['HTML', 'CSS', 'JavaScript', 'React']
result = '# '.join(web_tech)
print(result) # 'HTML# CSS# JavaScript# React'
```

- strip(): Удаляет все указанные символы в начале и конце строки.

```py
challenge = 'тридцать дней pythoonnn'
print(challenge.strip('noth')) # 'тридцать дней py'
```

- replace(): Заменяет подстроку на заданную строку.

```py
challenge = 'тридцать дней python'
print(challenge.replace('python', 'удовольствия')) # 'стридцать дней удовольствия'
```

- split(): Разделяет строку, используя заданную строку или пробел в качестве разделителя.

```py
challenge = 'тридцать дней python'
print(challenge.split()) # ['тридцать', 'дней', 'python']
challenge = 'тридцать, дней, python'
print(challenge.split(', ')) # ['тридцать', 'дней', 'python']
```

- title(): Возвращает строку с заглавными буквами в каждом слове.

```py
challenge = 'тридцать дней python'
print(challenge.title()) # Тридцать Дней Python
```

- swapcase(): Преобразует все заглавные буквы в строчные и все строчные буквы в заглавные.

```py
challenge = 'тридцать дней python'
print(challenge.swapcase())   # ТРИДЦАТЬ ДНЕЙ PYTHON
challenge = 'Тридцать Дней Python'
print(challenge.swapcase())  # тРИДЦАТЬ дНЕЙ pYTHON
```

- startswith(): Проверяет, начинается ли строка с указанной строки.

```py
challenge = 'тридцать python'
print(challenge.startswith('три')) # True

challenge = '30 дней python'
print(challenge.startswith('thirty')) # False
```

🌕 Вы - необыкновенный человек, у вас огромный потенциал. Вы только что завершили 4-й день и стали  на четыре шага ближе к великим достижениям. Теперь пора заняться упражнениями для вашего ума и мышц.

## 💻 Exercises - Day 4

1. Соедените строки: 'Thirty', 'Days', 'Of', 'Python' в одну строку: 'Thirty Days Of Python'.
2. Соедените строки: 'Coding', 'For' , 'All' в одну строку: 'Coding For All'.
3. Объявите переменную с именем company и присвойте ей начальное значение "Coding For All".
4. Выведите значение переменной company с помощью функции print().
5. Выведите длину строки company с помощью метода len() и функции print().
6. Преобразуйте все символы строки в заглавные буквы с помощью метода upper().
7. Преобразуйте все символы строки в строчные буквы с помощью метода lower().
8. Используйте методы capitalize(), title(), swapcase() для форматирования значения строки "Coding For All".
9. Возьмите срезом первое слово из строки "Coding For All".
10. Проверьте, содержит ли строка "Coding For All" слово "Coding" с помощью метода index(), find() или других методов. 
11. Замените слово "coding" в строке "Coding For All" на "Python".
12. Измените "Python for Everyone" на "Python for All" с помощью метода replace() или других методов.
13. Разделите строку "Coding For All" с использованием пробела в качестве разделителя (метод split()).
14. Разделите строку "Facebook, Google, Microsoft, Apple, IBM, Oracle, Amazon" по запятой.
15. Какой символ находится на позиции 0 в строке "Coding For All"?
16. Какой последний индекс строки "Coding For All"?
17. Какой символ имеет индекс 10 в строке "Coding For All"?
18. Создайте акроним или сокращение для имени "Python For Everyone".
19. Создайте акроним или сокращение для имени "Coding For All".
20. Используйте индекс, чтобы определить индекс первого вхождения символа 'C' в строке "Coding For All".
21. Используя индексы, определите индекс первого вхождения символа 'F' в строке "Coding For All".
22. Используйте метод rfind(), чтобы определить индекс последнего вхождения символа 'l' в строке "Coding For All People".
23. Используйте метод index() или find(), чтобы найти индекс первого вхождения слова 'because' в следующем предложении: "You cannot end a sentence with because because because is a conjunction".
24. Используйте метод rindex(), чтобы найти индекс последнего вхождения слова 'because' в следующем предложении: "You cannot end a sentence with because because because is a conjunction".
25. Вырежьте фразу 'because because because' из следующего предложения: 'You cannot end a sentence with because because because is a conjunction'.
26. Найдите индекс первого вхождения слова 'because' в следующем предложении: 'You cannot end a sentence with because because because is a conjunction'.
27. Вырежьте фразу 'because because because' из следующего предложения: 'You cannot end a sentence with because because because is a conjunction'.
28. Выясните, начинается ли строка 'Coding For All' с подстроки 'Coding'?
29. Выясните, заканчивается ли строка 'Coding For All' подстрокой 'coding'?
30. '&nbsp;&nbsp; Coding For All &nbsp;&nbsp;&nbsp; &nbsp;' &nbsp;,  удалите пробелы слева и справа в данной строке.
31. Какая из следующих переменных вернет True при использовании метода isidentifier():
    - 30DaysOfPython
    - thirty_days_of_python
32. В следующем списке содержатся названия некоторых библиотек Python: ['Django', 'Flask', 'Bottle', 'Pyramid', 'Falcon']. Соедините список с ипользуя символ решетки и пробела в качестве разделителя.
33. Используйте последовательность символов новой строки для разделения следующих предложений:
    ```py
    I am enjoying this challenge.
    I just wonder what is next.
    ```
34. Используйте последовательность символов табуляции для записи следующих строк:
    ```py
    Name      Age     Country   City
    Asabeneh  250     Finland   Helsinki
    ```
35. Используйте метод форматирования строк для отображения следующего:
    ```sh
    radius = 10
    area = 3.14 * radius ** 2
    The area of a circle with radius 10 is 314 meters square.
    ```

36. Выведите следующие строки с использованием методов форматирования строк:

    ```sh
    8 + 6 = 14
    8 - 6 = 2
    8 * 6 = 48
    8 / 6 = 1.33
    8 % 6 = 2
    8 // 6 = 1
    8 ** 6 = 262144
    ```

🎉 ПОЗДРАВЛЯЕМ ! 🎉

[<< День 3](../03_Day_Operators/03_operators.md) | [День 5 >>](../05_Day_Lists/05_lists.md)






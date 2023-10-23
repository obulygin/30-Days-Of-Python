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
    - [Экранированные последовательности](#экранированные-последовательности)
    - [Форматирование строк](#форматирование-строк)
      - [Старый стиль форматирования строк (оператор %)](#старый-стиль-форматирования-строк--оператор)
      - [Более новый стиль форматирования строк (str.format)](#более-новый-стиль-форматирования-строк-strformat)
      - [Самый новый способ форматирования строк - f-строки (Python 3.6+)](#самый-новый-способ-форматирования-строк-строк--f-строки-python-36)
    - [Строки в Python как последовательности символов](#строки-в-python-как-последовательности-символов)
      - [Распаковка строк](#распаковка-строк)
      - [Доступ к символам в строках по индексу](#доступ-к-символам-в-строках-по-индексу)
      - [Срезы строк в Python](#срезы-строк-в-python)
      - [Разворот строки](#разворот-строки)
      - [Пропуск символов в срезах](#пропуск-символов-в-срезах)
    - [Методы строк](#методы-строк)
  - [💻 Упражнения - Day 4](#-exercises---day-4)

# День 4

## Строки

Текст в Python является типом данных "строка"(string). Любой тип данных, записанный в виде текста, является строкой. Любые данные, заключенные в одинарные, двойные или тройные кавычки, являются строками. В Python существуют различные методы строк и встроенные функции для работы с данными типа "строка". Чтобы проверить длину строки, используйте функцию len().

### Создание строк

```py
letter = 'P'                # Строка может быть как одним символом, так и набором из символов (текстом)
print(letter)               # P
print(len(letter))          # 1
greeting = 'Hello, World!'  # Строку можно создать используя одинарные или двойные кавычки - "Hello, World!"
print(greeting)             # Hello, World!
print(len(greeting))        # 13
sentence = 'Надеюсь, Вам нравится "Python за 30 дней"'
print(sentence)
```

Многострочную строку можно создать используя тройные одинарные(''') или тройные двойные кавычки("""). 

Пример:

```py
multiline_string = '''Python — высокоуровневый язык программирования общего назначения с динамической строгой типизацией и автоматическим управлением памятью, ориентированный на повышение производительности разработчика, читаемости кода и его качества, а также на обеспечение переносимости написанных на нём программ.'''
print(multiline_string)

# Можно использовать и двойные кавычки
multiline_string = """Python — высокоуровневый язык программирования общего назначения с динамической строгой типизацией и автоматическим управлением памятью, ориентированный на повышение производительности разработчика, читаемости кода и его качества, а также на обеспечение переносимости написанных на нём программ."""
print(multiline_string)
```

### Конкатенация строк

Мы можем объединять строки. Объединение строк называется конкатенацией.

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

### Экранированные последовательности

В Python и других языках программирования обратная косая черта \ за которой следует символ, является экранированной последовательностью. 

Давайте взглянем на наиболее распространенные экранированные символы:

- \n: Переход на новую строку
- \t: Горизонтальная табуляция (2-4 пробела)
- \\\\: Обратная косая черта
- \\': Одинарные кавычки (')
- \\": Двойные кавычки (")

А теперь взглянем на пример:

```py
print('Я надеюсь, вам нравится "Python за 30 дней".\nНравится ведь?') # Перенос строки
print('Дни\tТемы\tУпражнения') # Добавление табуляции 
print('День 1\t3\t5')
print('День 2\t3\t5')
print('День 3\t3\t5')
print('День 4\t3\t5')
print('Это символ обратной косой черты (\\)') # Запись обратной косой черты
print("Изучения языков программирования принято начинать с фразы \"Hello, World!\"") # Запись двойных кавычек внутри двойных
# такой код выведет:
Я надеюсь, вам нравится "Python за 30 дней"
Нравится ведь?
Дни	 Темы	 Упражнения
День 1	5	    5
День 2	6	    20
День 3	5	    23
День 4	1	    35
Это символ обратной косой черты (\)
Изучения языков программирования принято начинать с фразы "Hello, World!"
```

### Форматирование строк

#### Старый стиль форматирования строк (оператор %)

В Python существует множество способов форматирования строк. Сейчас мы рассмотрим некоторые из них. Оператор "%" используется для форматирования набора переменных объединенных в кортеж (tuple), вместе с форматирующей строкой, которая содержит обычный текст со "спецификаторами аргументов" - специальными символами, такими как "%s", "%d", "%f", "%.2f".

- %s - Строка (или любой объект со строковым представлением, например, числа)
- %d - Целые числа
- %f - Числа с плавающей точкой
- ""%.2f" - Числа с плавающей точкой с точностью до указанного количества знаков

```py
# Только строки
first_name = 'Питер'
last_name = 'Паркер'
language = 'Python'
formated_string = 'Меня зовут %s %s. Я учу %s.' %(first_name, last_name, language)
print(formated_string) # Меня зовут Питер Паркер. Я учу Python.

# Строки и числа
radius = 10
pi = 3.14
area = pi * radius ** 2
formated_string = 'Площадь круга с радиусом %d равна %.2f.' %(radius, area) # 2 указывает на 2 значащие цифры после точки

python_libraries = ['Django', 'Flask', 'NumPy', 'Matplotlib','Pandas']
formated_string = 'Есть разные библиотеки для Python. Вот некоторые из них: %s' % (python_libraries)
print(formated_string) # "Есть разные библиотеки python. Вот некоторые из них: ['Django', 'Flask', 'NumPy', 'Matplotlib','Pandas']"
```

#### Новый стиль форматирования строк (str.format)

Этот способ форматирования строк с использованием метода format() был введен в Python версии 3. Он предоставляет более гибкий и универсальный подход к форматированию строк по сравнению с предыдущим (оператор %).

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

#### Самый новый способ форматирования строк - f-строки (Python 3.6+)

Еще один способ форматирования строк - это f-строк. Если перед строкой поставить символ "f", то это даст возможность вставлять значения (и даже однострочные операции) на нужные позиции внутри строк. 

```py
a = 4
b = 3
print(f'{a} + {b} = {a + b}')
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
a, b, c, d, e, f = language # распаковка строки в последовательность переменные
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
print(first_letter)  # P
second_letter = language[1]
print(second_letter)  # y
last_index = len(language) - 1
last_letter = language[last_index]
print(last_letter)  # n
```

Если мы хотим начать с конца строки, мы можем использовать отрицательный индекс. -1 обозначает индекс последнего символа, -2 индекс второго символа с конца и т.д.

```py
language = 'Python'
last_letter = language[-1]
print(last_letter)  # n
second_last = language[-2]
print(second_last)  # o
```

#### Срезы строк в Python

В Python мы можем брать срезы от строк путем обращения к индексам этой строки.

```py
language = 'Python'
first_three = language[0:3]  # начинаем с нулевого индекса включительно и идем до 3 невключительно. 
print(first_three) # Pyt
last_three = language[3:6]
print(last_three)  # hon
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
print(pto)  # Pto
```

### Методы строк

В Python существует множество методок строк, давайте рассмотрим некоторые из них:

- capitalize(): Преобразует первый символ строки в заглавную букву.

```py
challenge = 'python за 30 дней'
print(challenge.capitalize()) # 'Python за 30 дней'
```

- count(): Возвращает количество вхождений подстроки в строку. Метод имеет следующий синтаксис: `count(substring, start=..., end=...)`. Параметр `start`` принимает начальный индекс для поиска, а параметр `end` принимает последний индекс, где будет вестись поиск подстроки.

```py
challenge = 'Python за 30 дней'
print(challenge.count('P')) # 1
print(challenge.count('а', 7, 14)) # 1
print(challenge.count('ё')) # 0
```

- endswith(): Проверяет, заканчивается ли строка указанным набором символов

```py
challenge = 'Python за 30 дней'
print(challenge.endswith('ей'))   # True
print(challenge.endswith('!')) # False
```

- expandtabs(): Заменяет символ табуляции на указанное количество пробелов

```py
challenge = 'Python\tза\t30\tдней'
print(challenge)   # Python	за	30	дней
print(challenge.expandtabs(1))  # Python за 30 дней
```

- find(): Возвращает индекс первого вхождения подстроки, если подстрока не найдена, возвращает -1.

```py
challenge = 'Python за 30 дней'
print(challenge.find('y'))  # 1
print(challenge.find('th')) # 2
```

- rfind(): Возвращает индекс последнего вхождения подстроки, если подстрока не найдена, возвращает -1.

```py
challenge = 'Python за 30 дней'
print(challenge.rfind('т'))  # -1
print(challenge.rfind('е'))  # 15

```

- format(): форматирует строку. Подробнее о форматировании строк можно узнать по [ссылке](https://teletype.in/@pythontalk/f_strings).

```py
first_name = 'Питер'
last_name = 'Паркер'
age = 250
job = 'Человек-паук'
country = 'Россия'
sentence = 'Меня зовут {} {}. Мне {} лет. Я {}. Моя любимая страна {}.'.format(first_name, last_name, age, job, country)
print(sentence) # Меня зовут Питер Паркер. Мне 250 лет. Я Человек-паук. Моя любимая страна Россия.

radius = 10
pi = 3.14
area = pi * radius ** 2
result = 'Окружность круга с радиусом {} равна {}'.format(str(radius), str(area))
print(result) # Окружность круга с радиусом 10 равна 314
```

- index(): Возвращает наименьший индекс подстроки. В качестве дополнительных аргументов могут выступать начальный и конечный индексы для поиска. Если подстрока не найдена, возвращает ошибку valueError. 

```py
challenge = 'Python за 30 дней'
sub_string = 'за'
print(challenge.index(sub_string))  # 7
print(challenge.index(sub_string, 10)) # error
```

- rindex(): Возвращает наибольший индекс подстроки. В качестве дополнительных аргументов также могут выступать начальный и конечный индексы для поиска.

```py
challenge = 'Python за 30 дней'
sub_string = ' '
print(challenge.rindex(sub_string))  # 12
print(challenge.rindex(sub_string, 13)) # error
```

- isalnum(): Проверяет, содержит ли строка только буквенно-цифровые символы.

```py
challenge = 'Python за 30 дней'
print(challenge.isalnum()) # # False, пробел не является буквенно-цифровым символом

challenge = 'Pythonза30дней'
print(challenge.isalnum()) # True
```

- isalpha(): Проверяет, состоит ли строка только из буквенных символов.

```py
challenge = 'Pythonза30дней'
print(challenge.isalpha()) # False, тут не только буквы
challenge = 'Pythonзатридцатьдней'
print(challenge.isalpha()) # True
```

- isdecimal(): Проверяет, являются ли все символы в строке цифрами.

```py
challenge = 'Python за 30 дней'
print(challenge.isdecimal())  # False
challenge = '123'
print(challenge.isdecimal())  # True
challenge = '\u00B2'
print(challenge.isdigit())   # False
challenge = '12 3'
print(challenge.isdecimal())  # False, пробел не допускается
```

- isdigit(): Проверяет, являются ли все символы в строке цифрами (от 0 до 9 и некоторми другми символами Юникода, представляющими числа).

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
challenge = 'python за 30 дней'
print(challenge.islower()) # True
challenge = 'Python за 30 дней'
print(challenge.islower()) # False
```

- isupper(): Проверяет, являются ли все буквы в строке __заглавными__.

```py
challenge = 'Python за 30 дней'
print(challenge.isupper()) #  False
challenge = 'PYTHON ЗА 30 ДНЕЙ'
print(challenge.isupper()) # True
```

- join(): возвращает строку, соединяя элементы переданной последовательности с разделителем.

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
challenge = 'Python за 30 дней!'
print(challenge.strip('!')) # Python за 30 дней
```

- replace(): Заменяет подстроку на заданную строку.

```py
challenge = 'Python за 30 дней'
print(challenge.replace('30', '10')) # Python за 10 дней
```

- split(): Разделяет строку, используя указанный разделитель (по умолчанию пробел)

```py
challenge = 'Python за 30 дней'
print(challenge.split()) # ['Python', 'за', '30', 'дней']
challenge = 'Python, за, 30, дней'
print(challenge.split(', ')) # ['Python', 'за', '30', 'дней']
```

- title(): Возвращает строку, где первые буквы каждого слова заглавные.

```py
challenge = 'python за 30 дней'
print(challenge.title()) # Python За 30 Дней
```

- swapcase(): Преобразует все заглавные буквы в строчные и все строчные буквы в заглавные.

```py
challenge = 'python за 30 дней'
print(challenge.swapcase())   # PYTHON ЗА 30 ДНЕЙ
challenge = 'Python За 30 Дней'
print(challenge.swapcase())  # pYTHON зА 30 дНЕЙ
```

- startswith(): Проверяет, начинается ли строка с указанной строки.

```py
challenge = 'Python за 30 дней'
print(challenge.startswith('Python')) # True

challenge = 'Python за 30 дней'
print(challenge.startswith('js')) # False
```

🌕 Супер! Вы только что стали на четыре шага ближе к великим достижениям. Теперь пора заняться упражнениям для закрепления.

## 💻 Exercises - Day 4

1. Соедините строки: 'Python', 'за', '30', 'дней' в одну строку: 'Python за 30 дней'.
2. Объявите переменную с именем company и присвойте ей начальное значение "Python за 30 дней".
3. Выведите значение переменной company с помощью функции print().
4. Выведите длину строки company с помощью функции len() и функции print().
5. Преобразуйте все символы строки в заглавные буквы с помощью метода upper().
6. Преобразуйте все символы строки в строчные буквы с помощью метода lower().
7. Используйте методы capitalize(), title(), swapcase() для форматирования значения строки "Python за 30 дней".
8. Возьмите срезом первое слово из строки "Python за 30 дней".
9. Проверьте, содержит ли строка "Python за 30 дней" слово "Python" с помощью метода index(), find() или других методов. 
10. Замените слово "Python" в строке "Python за 30 дней" на "Успех".
11. Измените "Python за 30 дней" на "Python навсегда" с помощью метода replace() или других методов.
12. Какой символ находится на позиции -7 в строке "Python за 30 дней"?
13. Какой последний индекс строки "Python за 30 дней"?
14. Используйте метод index() или find(), чтобы найти индекс первого вхождения слова 'because' в следующем предложении: "You cannot end a sentence with because because because is a conjunction".
15. Используйте метод rindex(), чтобы найти индекс последнего вхождения слова 'because' в следующем предложении: "You cannot end a sentence with because because because is a conjunction".
16. Вырежьте фразу 'because because because' из следующего предложения: 'You cannot end a sentence with because because because is a conjunction'.
17. При помощи срезов получите фразу 'because because because' из следующего предложения: 'You cannot end a sentence with because because because is a conjunction'.
18. '&nbsp;&nbsp; Python за 30 дней &nbsp;&nbsp;&nbsp; &nbsp;' &nbsp;,  удалите пробелы слева и справа в данной строке.
19. В следующем списке содержатся названия некоторых библиотек Python: ['Django', 'Flask', 'Bottle', 'Pyramid', 'Falcon']. Соедините список с ипользуя символ решетки и пробела в качестве разделителя.
20. Используйте табуляцию, чтобы вывести ровно аналогичную строку:
    ```py
    Name      Age     Country   City
    Oleg      999     Russia    Ekaterinburg
    ```
21. Используйте форматирование строк для выода следующего текста, ипсользуя переменные:
    ```sh
    radius = 10
    area = 3.14 * radius ** 2
    The area of a circle with radius 10 is 314 meters square.
    ```

22. Выведите следующие строки с использованием методов форматирования строк:

    ```sh
    8 + 6 = 14
    8 - 6 = 2
    8 * 6 = 48
    8 / 6 = 1.33
    8 % 6 = 2
    8 // 6 = 1
    8 ** 6 = 262144
    ```

🎉Поздравляем!🎉

[<< День 3](../03_Day_Operators/03_operators.md) | [День 5 >>](../05_Day_Lists/05_lists.md)






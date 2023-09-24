<div align="center">
  <h1> 30 Дней Python: День 18 - Регулярные Выражения </h1>
  <a href="https://github.com/obulygin/30-Days-Of-Python/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=obulygin/30-Days-Of-Python" />
</div>

[<< День 17](../17_Day_Exception_handling/17_exception_handling.md) | [День 19>>](../19_Day_File_handling/19_file_handling.md)

![30DaysOfPython](../images/30daysofpython.png)

- [📘 День 18](#-день-18)
  - [Регулярные выражения](#регулярные-выражения)
    - [Модуль *re*](#модуль-re)
    - [Методы модуля *re*](#методы-модуля-re)
      - [*re.match()*](#rematch)
      - [*re.search*](#research)
      - [Поиск всех совпадений с помощью метода **findall**](#поиск-всех-совпадений-с-помощью-метода-findall)
      - [Замена подстроки](#замена-подстроки)
  - [Разделение текста с использованием метода RegEx Split](#разделение-текста-с-использованием-метода-regex-split)
  - [Написание шаблонов RegEx](#написание-шаблонов-regex)
    - [Квадратные скобки](#квадратные-скобки)
    - [Экранирование специального символа \\ RegEx](#экранирование-специального-символа--regex)
    - [Одно или больше совпадений (+)](#одно-или-больше-совпадений-)
    - [Точка(.)](#точка)
    - [Ноль или больше совпадений(\*)](#ноль-или-больше-совпадений)
    - [Ноль или одно совпадение(?)](#ноль-или-одно-совпадение)
    - [Квантификатор в  RegEx](#квантификатор-в--regex)
    - [Символ ^](#символ-)
  - [💻 Упражнения: День 18](#-упражнения-день-18)
    - [Упраженения: Уровень 1](#упраженения-уровень-1)
    - [Упраженения: Уровень 2](#упраженения-уровень-2)
    - [Упраженения: Уровень 3](#упраженения-уровень-3)

# 📘 День 18

## Регулярные выражения

Регулярные выражения в Python - это мощный инструмент для работы с текстом. Они позволяют выполнять различные операции по поиску, сопоставлению и обработке текстовых данных на основе заданных шаблонов. Для использования регулярных выражений в Python необходимо импортировать модуль **re**. В этом модуле предоставляются различные функции и методы для работы с регулярными выражениями.

### Модуль *re*


После импорта модуля мы можем использовать его для поиска шаблонов.

```py
import re
```

### Методы модуля *re*

Для поиска шаблона мы используем различные методы модуля re, которые позволяют искать совпадение в строке.

* **re.match(pattern, string)**: Этот метод ищет совпадение шаблона pattern только в начале первой строки string. Если совпадение найдено, он возвращает объект совпадения, иначе возвращает None.
* *re.search(pattern, string)*: Этот метод ищет совпадение шаблона pattern в строке string. Он вернет первое найденное совпадение в любой части строки. Если совпадение найдено, он возвращает объект совпадения, иначе возвращает None. 
* **re.findall(pattern, string)**: Этот метод ищет все неперекрывающиеся совпадения шаблона pattern в строке string. Он возвращает список всех найденных.
* **re.split(pattern, string)**: Этот метод разделяет строку string по местам совпадения шаблона pattern и возвращает список разделенных элементов. 
* **re.sub(pattern, repl, string)**: Этот метод заменяет все совпадения шаблона pattern в строке string на строку repl. Он возвращает новую строку с выполненными заменами. 

#### *re.match()*

```py
# синтаксис
re.match(substring, string, re.I)
# substring - это строка или шаблон, string - текст, в котором мы ищем совпадение, re.I - параметр, указывающий игнорирование регистра
```

```py
import re

txt = 'Я люблю преподавать Python и JavaScript'
# Возвращает объект с информацией о расположении совпадения
match = re.match('Я люблю преподавать', txt, re.I)
print(match)  # <re.Match object; span=(0, 19), match='Я люблю преподавать'>
# Мы можем получить начальную и конечную позицию совпадения в виде кортежа, используя метод span()
span = match.span()
print(span)     # (0, 19)
# Давайте получим начальную и конечную позицию из кортежа
start, end = span
print(start, end)  # 0, 19
подстрока = txt[start:end]
print(подстрока)       # Я люблю преподавать
```

Как видно из приведенного выше примера, мы ищем шаблон (или подстроку) Я люблю преподавать. Метод match возвращает объект **только в том случае**, если текст начинается с заданного шаблона.

```py
import re

txt = 'Я люблю преподавать Python и JavaScript'
match = re.match('Мне нравится преподавать', txt, re.I)
print(match)  # None
```

Текст не начинается с *Мне нравится преподавать*, поэтому совпадение не найдено, и метод match возвращает None.

#### *re.search*

```py
# синтаксис
re.match(substring, string, re.I)
# substring - это строка или шаблон, string - текст, в котором мы ищем совпадение, re.I - параметр, указывающий игнорирование регистра
```

```py
import re

txt = '''Python - самый прекрасный язык, который когда-либо создал человек.
Я рекомендую Python в качестве первого языка программирования'''

# Возвращает объект с информацией о расположении совпадения
match = re.search('первого', txt, re.I)
print(match)  # <re.Match object; span=(98, 105), match='первого'>
# Мы можем получить начальную и конечную позицию совпадения в виде кортежа, используя метод span()
span = match.span()
print(span)     # (98, 105)
# Давайте получим начальную и конечную позицию из кортежа
start, end = span
print(start, end)  # 98, 105
подстрока = txt[start:end]
print(подстрока)       # первого
```

Как видно из примера выше, метод **search** практичнее метода match, потому что она ищет шаблон во всем тексте. Search возвращает объект с первым найденным совпадением, в противном случае возвращает None. Более удобный метод re - это **findall**. Он проверяет весь текст на наличие совпадений с шаблоном и возвращает все найденные совпадения в виде списка.

#### Поиск всех совпадений с помощью метода **findall**

*findall()* возвращает все совпадения в виде списка.

```py
txt = '''Python - самый прекрасный язык, который когда-либо создал человек.
Я рекомендую Python в качестве первого языка программирования'''

# Возвращает список
matches = re.findall('язык', txt, re.I)
print(matches)  # ['язык', 'язык']
```

Как видно, слово "язык" найдено дважды в строке. Попробуем еще несколько примеров.
Теперь мы будем искать слова "Python" и "python" в строке:

```py
txt = '''Python - самый прекрасный язык, который когда-либо создал человек.
Я рекомендую Python в качестве первого языка программирования'''

# Возвращает список
matches = re.findall('Python|python', txt, re.I)
print(matches)  # ['Python', 'python']

```

Так как мы используем флаг re.I, регистр букв не учитывается. Если флаг re.I отсутствует, то нам придется написать шаблон по-другому. Давайте проверим:

```py
txt = '''Python - самый прекрасный язык, который когда-либо создал человек.
Я рекомендую Python в качестве первого языка программирования'''

matches = re.findall('Python|python', txt)
print(matches)  # ['Python', 'python']

#
matches = re.findall('[Pp]ython', txt)
print(matches)  # ['Python', 'python']

```

#### Замена подстроки

```py
txt = '''Python - самый прекрасный язык, который когда-либо создал человек.
Я рекомендую Python в качестве первого языка программирования'''

match_replaced  = re.sub('Python|python', 'JavaScript', txt, re.I)
print(match_replaced )  # JavaScript - самый прекрасный язык, который когда-либо создал человек.
# ИЛИ
match_replaced  = re.sub('[Pp]ython', 'JavaScript', txt, re.I)
print(match_replaced )  # JavaScript - самый прекрасный язык, который когда-либо создал человек.

```

Рассмотрим еще один пример. Следующую строку прочитать сложно, пока мы не удалим символ %. Замена символа % на пустую строку очистит текст.

```py

txt = '''%I a%m te%%a%%che%r% a%n%d %% I l%o%ve te%ach%ing. 
T%he%re i%s n%o%th%ing as r%ewarding a%s e%duc%at%i%ng a%n%d e%m%p%ow%er%ing p%e%o%ple.
I fo%und te%a%ching m%ore i%n%t%er%%es%ting t%h%an any other %jobs. 
D%o%es thi%s m%ot%iv%a%te %y%o%u to b%e a t%e%a%cher?'''

matches = re.sub('%', '', txt)
print(matches)
```

```sh
I am teacher and I love teaching.
There is nothing as rewarding as educating and empowering people. 
I found teaching more interesting than any other jobs. Does this motivate you to be a teacher?
```

## Разделение текста с использованием метода RegEx Split

```py
txt = '''Я преподаватель и люблю преподавать.
Нет ничего более вдохновляющего, чем образование и развитие людей.
Я нашел преподавание более интересным, чем любую другую работу.
Вдохновляет ли это вас стать учителем?'''
print(re.split('\n', txt))  # разделение по символу \n - символ конца строки
```

```sh
['Я преподаватель и люблю преподавать.', 'Нет ничего более вдохновляющего, чем образование и развитие людей.', 'Я нашел преподавание более интересным, чем любую другую работу.', 'Вдохновляет ли это вас стать учителем?']

```

## Написание шаблонов RegEx 

Для объявления переменной типа строки мы используем одинарные или двойные кавычки.  Для объявления переменной типа регулярного выражения используем **r''**.
Следующий шаблон идентифицирует только слово "apple" в нижнем регистре. Чтобы сделать его регистронезависимым, мы можем либо переписать шаблон, либо добавить флаг.  

```py
import re

regex_pattern = r'apple'
txt = 'Apple and banana are fruits. An old cliche says an apple a day a doctor way has been replaced by a banana a day keeps the doctor far far away. '
matches = re.findall(regex_pattern, txt)
print(matches)  # ['apple']

# Чтобы сделать поиск независимым от регистра, добавим флаг re.I
matches = re.findall(regex_pattern, txt, re.I)
print(matches)  # ['Apple', 'apple']
# Мы также можем использовать набор символов (set of characters)
regex_pattern = r'[Aa]pple'   # это означает, что первая буква может быть "Apple" или "apple"
matches = re.findall(regex_pattern, txt)
print(matches)  # ['Apple', 'apple']

```
* []: Набор символов
  * [a-c] означает "a" или "b" или "c"
  * [a-z] означает любую букву от "a" до "z"
  * [A-Z] означает любой символ от "A" до "Z"
  * [0-3] означает 0 или 1 или 2 или 3
  * [0-9] означает любую цифру от 0 до 9
  * [A-Za-z0-9] означает любой отдельный символ, будь то буква от "a" до "z", от "A" до "Z" или цифра от 0 до 9
* \\: используется для иззбегания специальных символов
  * ∗\d означает: совпадение с цифрами(числами от 0 до 9)
  * \D означает: совпадение со символами,не являющимися цифрами
* . : любой символ, кроме символа новой строки (\n)
* ^: начинающиеся
  * r'^substring' например, r'^love' - предложения, начинающееся со слова "love"
  * r'[^abc] означает не "a", не "b", не "c".
* $: заканчивающиеся
  * r'substring$' например, r'love$' - предложения, заканчивающееся словом "love"
* *: ноль или более раз
  * r'[a]*' означает ноль или более вхождений символа "a"
* +: один или более раз
  * r'[a]+' означает одно или более вхождений символа "a"
* ?: ноль или один раз
  *  r'[a]?' означает ноль или одно вхождение символа "a"
* {3}: ровно 3 символа
* {3,}: не менее 3 символов
* {3,8}: от 3 до 8 символов
* |: либо
  * r'apple|banana' означает либо "apple", либо "banana"
* (): захват и группировка

![Regular Expression cheat sheet](../images/regex.png)

Давайте рассмотрим несколько примеров, чтобы прояснить данные метасимволы.

### Квадратные скобки

Давайте воспользуемся квадратными скобками для включения символов в нижнем и верхнем регистрах.

```py
regex_pattern = r'[Aa]pple' # эти квадратные скобки означают A или a
txt = 'Apple and banana are fruits. An old cliche says an apple a day a doctor way has been replaced by a banana a day keeps the doctor far far away.'
matches = re.findall(regex_pattern, txt)
print(matches)  # ['Apple', 'apple']

```

Если мы хотим найти слово "banana", мы можем написать шаблон следующим образом:



```py
regex_pattern = r'[Aa]pple|[Bb]anana' # эти квадратные скобки означают A или a
txt = 'Apple and banana are fruits. An old cliche says an apple a day a doctor way has been replaced by a banana a day keeps the doctor far far away.'
matches = re.findall(regex_pattern, txt)
print(matches)  # ['Apple', 'banana', 'apple', 'banana']

```

Используя квадратные скобки и оператор "или", мы получили соответствия для слов Apple, apple, Banana и banana.

### Экранирование специального символа \\ RegEx

```py
regex_pattern = r'\d'  # d - это специальный символ, который означает цифры
txt = 'This regular expression example was made on December 6,  2019 and revised on July 8, 2021'
matches = re.findall(regex_pattern, txt)
print(matches)  # ['6', '2', '0', '1', '9', '8', '2', '0', '2', '1'], это не то, что мы хотим

```

### Одно или больше совпадений (+)

```py
regex_pattern = r'\d+'  # d - это специальный символ, который означает цифры, + означает один или более раз
txt = 'This regular expression example was made on December 6,  2019 and revised on July 8, 2021'
matches = re.findall(regex_pattern, txt)
print(matches)  # ['6', '2019', '8', '2021'] - теперь это лучше!
```

### Точка(.)

```py
regex_pattern = r'[a].'  # квадратные скобки означают символ a, а точка означает любой символ, кроме перевода строки
txt = '''Apple and banana are fruits'''
matches = re.findall(regex_pattern, txt)
print(matches)  # ['an', 'an', 'an', 'a ', 'ar']

regex_pattern = r'[a].+'  # . означает любой символ, + означает один или более раз
matches = re.findall(regex_pattern, txt)
print(matches)  # ['and banana are fruits']

```

### Ноль или больше совпадений(\*)

Шаблон может не встречаться или может встречаться много раз..

```py
regex_pattern = r'[a].*'  # . любой символ, * любой символ ноль или более раз 
txt = '''Apple and banana are fruits'''
matches = re.findall(regex_pattern, txt)
print(matches)  # ['and banana are fruits']
```

### Ноль или одно совпадение(?)

Шаблон может не встречаться или встретиться один раз.

```py
txt = '''I am not sure if there is a convention how to write the word e-mail.
Some people write it as email others may write it as Email or E-mail.'''
regex_pattern = r'[Ee]-?mail'  # ? здесь означает, что '-' является необязательным
matches = re.findall(regex_pattern, txt)
print(matches)  # ['e-mail', 'email', 'Email', 'E-mail']
```

### Квантификатор в  RegEx

Мы можем указать длину подстроки, которую мы ищем в тексте, используя фигурные скобки. Представим, что нас интересует подстрока длиной 4 символа:

```py
txt = 'This regular expression example was made on December 6,  2019 and revised on July 8, 2021'
regex_pattern = r'\d{4}'  # ровно четыре символа
matches = re.findall(regex_pattern, txt)
print(matches)  # ['2019', '2021']

txt = 'This regular expression example was made on December 6,  2019 and revised on July 8, 2021'
regex_pattern = r'\d{1, 4}'   # от 1 до 4
matches = re.findall(regex_pattern, txt)
print(matches)  # ['6', '2019', '8', '2021']
```

### Символ ^

* Начинается с ... 
  
```py
txt = 'This regular expression example was made on December 6,  2019 and revised on July 8, 2021'
regex_pattern = r'^This'   # ^ означает начало строки
matches = re.findall(regex_pattern, txt)
print(matches)  # ['This']
```

* Отрицание

```py
txt = 'This regular expression example was made on December 6,  2019 and revised on July 8, 2021'
regex_pattern = r'[^A-Za-z ]+'   # ^ внутри набора символов означает отрицание: не A-Z, не a-z, нет пробела
matches = re.findall(regex_pattern, txt)
print(matches)  # ['6,', '2019', '8', '2021']
```

## 💻 Упражнения: День 18

### Упраженения: Уровень 1
 1. Какое самое частое слово в следующей строке paragraph:
```py
    paragraph = 'I love teaching. If you do not love teaching what else can you love. I love Python if you do not love something which can give you all the capabilities to develop an application what else can you love.
```

```sh
    [
    (6, 'love'),
    (5, 'you'),
    (3, 'can'),
    (2, 'what'),
    (2, 'teaching'),
    (2, 'not'),
    (2, 'else'),
    (2, 'do'),
    (2, 'I'),
    (1, 'which'),
    (1, 'to'),
    (1, 'the'),
    (1, 'something'),
    (1, 'if'),
    (1, 'give'),
    (1, 'develop'),
    (1, 'capabilities'),
    (1, 'application'),
    (1, 'an'),
    (1, 'all'),
    (1, 'Python'),
    (1, 'If')
    ]
```

2. Положение некоторых точек на оси x: -12, -4, -3 и -1 в отрицательном направлении, 0 - начало координат, 4 и 8 в положительном направлении. Извлеките эти числа из текста и найдите расстояние между двумя наиболее удаленными частицами.

```py
points = ['-1', '2', '-4', '-3', '-1', '0', '4', '8']
sorted_points =  [-4, -3, -1, -1, 0, 2, 4, 8]
distance = 8 -(-4) # 12
```

### Упраженения: Уровень 2

1. Напишите шаблон, который определяет, является ли строка допустимой переменной в Python.

    ```sh
    is_valid_variable('first_name') # True
    is_valid_variable('first-name') # False
    is_valid_variable('1first_name') # False
    is_valid_variable('firstname') # True
    ```

### Упраженения: Уровень 3

1. Удалите символ %. После удаления подсчитайте три наиболее часто встречающихся слова в строке.

    ```py
    sentence = '''%I $am@% a %tea@cher%, &and& I lo%#ve %tea@ching%;. There $is nothing; &as& mo@re rewarding as educa@ting &and& @emp%o@wering peo@ple. ;I found tea@ching m%o@re interesting tha@n any other %jo@bs. %Do@es thi%s mo@tivate yo@u to be a tea@cher!?'''

    print(clean_text(sentence)) # I am a teacher and I love teaching There is nothing as more rewarding as educating and empowering people I found teaching more interesting than any other jobs Does this motivate you to be a teacher
    print(most_frequent_words(cleaned_text)) # [(3, 'I'), (2, 'teaching'), (2, 'teacher')]
    ```

🎉 ПОЗДРАВЛЯЕМ ! 🎉

[<< День 17](../17_Day_Exception_handling/17_exception_handling.md) | [День 19>>](../19_Day_File_handling/19_file_handling.md)

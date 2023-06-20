<div align="center">
  <h1> 30 Дней Python: День 14 - Функции высшего порядка</h1>
  <a class="header-badge" target="_blank" href="https://www.linkedin.com/in/asabeneh/">
  <img src="https://img.shields.io/badge/style--5eba00.svg?label=LinkedIn&logo=linkedin&style=social">
  </a>
  <a class="header-badge" target="_blank" href="https://twitter.com/Asabeneh">
  <img alt="Twitter Follow" src="https://img.shields.io/twitter/follow/asabeneh?style=social">
  </a>

  <sub>Автор:
  <a href="https://www.linkedin.com/in/asabeneh/" target="_blank">Asabeneh Yetayeh</a><br>
  <small>Второе издание: Июль, 2021</small>
  </sub>
</div>
</div>

[<< День 13](../13_Day_List_comprehension/13_list_comprehension.md) | [День 15>>](../15_Day_Python_type_errors/15_python_type_errors.md)

![30DaysOfPython](../images/30DaysOfPython_banner3@2x.png)
- [📘 День 14](#-день-14)
  - [Функции высшего порядка](#функции-высшего-порядка)
    - [Функция как параметр](#функция-как-параметр)
    - [Функция как возвращаемое значение](#функция-как-возвращаемое-значение)
  - [Замыкание (Closures) в Python](#замыкание-closures-в-python)
  - [Декораторы в Python](#декораторы-в-python)
    - [Создание декораторов](#создание-декораторов)
    - [Применение нескольких декораторов к одной функции](#применение-нескольких-декораторов-к-одной-функции)
    - [Параметры в функциях декораторах](#параметры-в-функциях-декораторах)
  - [Встроенные функции высшего порядка](#встроенные-функции-высшего-порядка)
    - [Python - функция map()](#python---функция-map)
    - [Python - функция filter()](#python---функция-filter)
    - [Python - функция reduce](#python---функция-reduce)
  - [💻 Упражнения: День 14](#-упражнения-день-14)
    - [Упражнения: Уровень 1](#упражнения-уровень-1)
    - [Упражнения: Уровень 2](#упражнения-уровень-2)
    - [Упражнения: Уровень 3](#упражнения-уровень-3)

# 📘 День 14

## Функции высшего порядка

В Python функции рассматриваются как объекты первого класса, что позволяет выполнять следующие операции с функциями:

- Функция может принимать одну или несколько функций в качестве параметров
- Функция может быть возвращаемым значением другой функции
- Функцию можно изменять
- Функцию можно присвоить переменной

В данном разделе мы рассмотрим:

1. Работу с функциями в качестве параметров.
2. Возвращение функций в качестве результата из других функций.
3. Использование замыканий и декораторов в Python.

### Функция как параметр

```py
def sum_numbers(nums):  # обычная функция 
    return sum(nums)    # функция, использующая встроенную функцию sum :<

def higher_order_function(f, lst):  # функция, принимающая функцию в качестве параметра
    summation = f(lst)
    return summation
result = higher_order_function(sum_numbers, [1, 2, 3, 4, 5])
print(result)       # 15
```

### Функция как возвращаемое значение

```py
def square(x):          # функция возведения в квадрат
    return x ** 2

def cube(x):            # функция возведения в куб
    return x ** 3

def absolute(x):        # функция нахождения абсолютного значения
    if x >= 0:
        return x
    else:
        return -(x)

def higher_order_function(type):  # функция высшего порядка, возвращающая функцию
    if type == 'square':
        return square
    elif type == 'cube':
        return cube
    elif type == 'absolute':
        return absolute

result = higher_order_function('square')
print(result(3))       # 9
result = higher_order_function('cube')
print(result(3))       # 27
result = higher_order_function('absolute')
print(result(-3))      # 3
```

В приведенном выше примере вы видите, что функция высшего порядка возвращает разные функции в зависимости от переданного параметра.

## Замыкание (Closures) в Python

В Python имеется возможность создания вложенной функции, которая будет ссылаться на параметры объявленные в теле внешней функции. Замкнутая функция, будет возвращать значение вложенной функции. Давайте рассмотрим пример:

**Пример:**

```py
def add_ten():
    ten = 10
    def add(num):
        return num + ten
    return add

closure_result = add_ten()
print(closure_result(5))  # 15
print(closure_result(10))  # 20
```

## Декораторы в Python

Декоратор - это шаблон проектирования в Python, который позволяет пользователю добавлять новую функциональность к существующему объекту без изменения его структуры. Декораторы обычно вызываются перед определением функции, которую вы хотите декорировать.

### Создание декораторов

Для создания функции-декоратора нам нужна внешняя функция с вложенной функцией **wrapper()**.

**Пример:**

```py
# Обычная функция
def greeting():
    return 'Welcome to Python'
def uppercase_decorator(function):
    def wrapper():
        func = function()
        make_uppercase = func.upper()
        return make_uppercase
    return wrapper
g = uppercase_decorator(greeting)
print(g())          # WELCOME TO PYTHON

## Давайте реализуем приведенный выше пример с помощью декоратора

'''Эта функция-декоратор является функцией высшего порядка,
которая принимает функцию в качестве параметра'''
def uppercase_decorator(function):
    def wrapper():
        func = function()
        make_uppercase = func.upper()
        return make_uppercase
    return wrapper
@uppercase_decorator
def greeting():
    return 'Welcome to Python'
print(greeting())   # WELCOME TO PYTHON

```

### Применение нескольких декораторов к одной функции

```py

'''Эти функции-декораторы являются функциями высшего порядка,
которые принимают функции в качестве параметров'''

# Первый декоратор
def uppercase_decorator(function):
    def wrapper():
        func = function()
        make_uppercase = func.upper()
        return make_uppercase
    return wrapper

# Второй декоратор
def split_string_decorator(function):
    def wrapper():
        func = function()
        splitted_string = func.split()
        return splitted_string

    return wrapper

@split_string_decorator
@uppercase_decorator     # обратите внимание, что порядок применения декораторов важен, так как .upper() функция не работает с типом данных списка.
def greeting():
    return 'Welcome to Python'
print(greeting())   # WELCOME TO PYTHON
```

### Параметры в функциях декораторах

В большинстве случаев нам нужно, чтобы наши функции принимали параметры. Мы можем определить декоратор, который принимает параметры.

```py
def decorator_with_parameters(function):
    def wrapper_accepting_parameters(para1, para2, para3):
        function(para1, para2, para3)
        print("I live in {}".format(para3))
    return wrapper_accepting_parameters

@decorator_with_parameters
def print_full_name(first_name, last_name, country):
    print("I am {} {}. I love to teach.".format(
        first_name, last_name, country))

print_full_name("Asabeneh", "Yetayeh",'Finland')
```

## Встроенные функции высшего порядка

Сегодня мы рассмотрим такие функции высшего порядка как:  _map()_, _filter_, and _reduce_.
Также Python поддерживает lambda() функции, которые могут быть использованы в качестве параметров, и наиболее подходящим использованием эмих функций являются все те же функции **map**, **filter** и **reduce**.

### Python - функция map()

Функция map() - это встроенная функция высшего порядка, которая принимает функцию и итерируемый объект в качестве параметров.

```py
    # синтаксис
    map(function, итерируемый объект)
```

**Пример:1**

```py
numbers = [1, 2, 3, 4, 5] # итерируемый объект
def square(x):
    return x ** 2
numbers_squared = map(square, numbers)
print(list(numbers_squared))    # [1, 4, 9, 16, 25]
# Давайте воспользуемся lambda-функцией
numbers_squared = map(lambda x : x ** 2, numbers)
print(list(numbers_squared))    # [1, 4, 9, 16, 25]
```

**Пример:2**

```py
numbers_str = ['1', '2', '3', '4', '5']  # итерируемый объект
numbers_int = map(int, numbers_str)
print(list(numbers_int))    # [1, 2, 3, 4, 5]
```

**Пример:3**

```py
names = ['Asabeneh', 'Lidiya', 'Ermias', 'Abraham']  # с

def change_to_upper(name):
    return name.upper()

names_upper_cased = map(change_to_upper, names)
print(list(names_upper_cased))    # ['ASABENEH', 'LIDIYA', 'ERMIAS', 'ABRAHAM']

# Давайте снова воспользуемся lambda-функцией
names_upper_cased = map(lambda name: name.upper(), names)
print(list(names_upper_cased))    # ['ASABENEH', 'LIDIYA', 'ERMIAS', 'ABRAHAM']
```

Фактически, функция **map()** выполняет итерацию по списку и применяет функцию к каждому элементу. Например, она преобразует имена в верхний регистр и возвращает новый список.

### Python - функция filter() 

Функция **filter()** применяет указанную функцию к каждому элементу итерируемого объекта и возвращает только те элементы, для которых функция возвращает значение True.

```py
    # синтаксис
    filter(function, итерируемый объект)
```

**Пример:1**

```py
# Отфильтруем только четные числа
numbers = [1, 2, 3, 4, 5]  # итерируемый объект

def is_even(num):
    if num % 2 == 0:
        return True
    return False

even_numbers = filter(is_even, numbers)
print(list(even_numbers))       # [2, 4]
```

**Пример:2**

```py
numbers = [1, 2, 3, 4, 5]  # итерируемый объект

def is_odd(num):
    if num % 2 != 0:
        return True
    return False

odd_numbers = filter(is_odd, numbers)
print(list(odd_numbers))       # [1, 3, 5]
```

```py
# Оставляем только длинные имена
names = ['Asabeneh', 'Lidiya', 'Ermias', 'Abraham']  # итерируемый объект
def is_name_long(name):
    if len(name) > 7:
        return True
    return False

long_names = filter(is_name_long, names)
print(list(long_names))         # ['Asabeneh']
```



### Python - функция reduce

Функция **reduce()** содержится в модуле **functools**. Вначале мы должны импортировать модуль, чтобя она работала. Как функции map и filter, она принимает два параметра: функцию и итерируемый объект. Однако она не возвращает другой итерируемый объект, а вместо этого возвращает единственное значение.

**Example:1**

```py
numbers_str = ['1', '2', '3', '4', '5']  # итерируемый объект
def add_two_nums(x, y):
    return int(x) + int(y)

total = reduce(add_two_nums, numbers_str)
print(total)    # 15
```

## 💻 Упражнения: День 14

```py
countries = ['Estonia', 'Finland', 'Sweden', 'Denmark', 'Norway', 'Iceland']
names = ['Asabeneh', 'Lidiya', 'Ermias', 'Abraham']
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

### Упражнения: Уровень 1

1. Объясните разницу между map, filter и reduce.
2. Объясните разницу между функцией высшего порядка, замыканием и декоратором.
3. Задайте функцию call, параметрами которой будут map, filter или reduce. (Задайте 3 разные функции)
4. Используйте цикл **for** для вывода каждой страны в списке countries.
5. Используйте цикл **for** для вывода каждого имени в списке names.
6. Используйте цикл **for** для вывода каждого числа в списке numbers.

### Упражнения: Уровень 2

1. Используйте функцию высшего порядка map, чтобы создать новый список, заменив каждую страну на верхний регистр в списке countries.
2. Используйте функцию высшего порядка map, чтобы создать новый список, заменив каждое число на его квадрат в списке numbers.
3. Используйте функцию высшего порядка map, чтобы изменить каждое имя на верхний регистр в списке names.
4. Используйте функцию высшего порядка filter, чтобы отфильтровать страны, содержащие 'land'.
5. Используйте функцию высшего порядка filter, чтобы отфильтровать страны, имеющие ровно шесть символов.
6. Используйте функцию высшего порядка filter, чтобы отфильтровать страны, содержащие шесть букв и более.
7. Используйте функцию высшего порядка filter, чтобы отфильтровать страны, начинающиеся с буквы 'E'.
8. Cоздайте цепь из двух или более итераторов (например: arr.map(callback).filter(callback).reduce(callback))
9. Объявите функцию с именем get_string_lists, которая принимает список в качестве параметра, а затем возвращает список, содержащий только строки.
10. Используйте функцию высшего порядка reduce, чтобы суммировать все числа в списке numbers.
11. Используйте функцию высшего порядка reduce, чтобы объединить все страны и сформировать предложение: " Estonia, Finland, Sweden, Denmark, Norway, and Iceland are north European countries".
12. Объявите функцию с именем categorize_countries, которая возвращает список стран с общим шаблоном (вы можете найти список стран по [ссылке](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/countries.py)). Шаблоном может быть, 'land', 'ia', 'island' или 'stan'.
13. Создайте функцию, возвращающую словарь, где ключи - это начальные буквы стран, а значения - количество названий стран, начинающихся с этой буквы.
14. Объявите функцию get_first_ten_countries, которая возвращает список первых десяти стран из списка стран.
15. Объявите функцию get_last_ten_countries, которая возвращает список последних десяти стран из списка стран.

### Упражнения: Уровень 3

1. Используйте [countries_data.py](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/countries-data.py) для решения следующих заданий:
   - Отсортируйте страны по названию, столице и населению.
   - Отсортируйте десять наиболее распространенных языков по местоположению:.
   - Отсортеруйте страны по населению и выведите 10 наиболее населенных стран.

🎉 ПОЗДРАВЛЯЕМ ! 🎉

[<< День 13](../13_Day_List_comprehension/13_list_comprehension.md) | [День 15>>](../15_Day_Python_type_errors/15_python_type_errors.md)

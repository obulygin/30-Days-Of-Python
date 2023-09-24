<div align="center">
  <h1> 30 Дней Python: День 10 - Циклы</h1>
  <a href="https://github.com/obulygin/30-Days-Of-Python/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=obulygin/30-Days-Of-Python" />
</div>

[<< День 9](../09_Day_Conditionals/09_conditionals.md) | [День 11 >>](../11_Day_Functions/11_functions.md)

![30DaysOfPython](../images/30daysofpython.png)

- [📘 День 10](#-день-10)
  - [Циклы](#циклы)
    - [Цикл while](#цикл-while)
    - [Break and Continue - Часть 1](#break-and-continue---часть-1)
    - [Цикл for](#цикл-for)
    - [Break and Continue - Часть 2](#break-and-continue---часть-2)
    - [Функция range](#функция-range)
    - [Вложенные циклы](#вложенные-циклы)
    - [For Else](#for-else)
    - [Pass](#pass)
  - [💻 Упражнения: День 10](#-упражнения-день-10)
    - [Упражнения: Уровень 1](#упражнения-уровень-1)
    - [Упражнения: Уровень 2](#упражнения-уровень-2)
    - [Упражнения: Уровень 3](#упражнения-уровень-3)

# 📘 День 10

## Циклы


Жизнь полна рутины. В программировании мы также выполняем множество повторяющихся задач. Для обработки повторяющихся задач программные языки используют циклы. В Python не исключение, в нем имеются следующие виды циклов:


1. Цикл while 
2. Цикл for

### Цикл while

Для создания цикла while используется зарезирвированное слово **while**. Этот цикл используется для повторного выполнения блока инструкций, пока заданное условие имеет значение True. Когда условие становится ложным, то цикл прекращает свое действие. 

```py
  # синтаксис
while condition:
    code goes here
```

**Примеры:**

```py
count = 0
while count < 5:
    print(count)
    count = count + 1
#возвращает числа от 0 до 4
```
В приведенном выше цикле условие становится ложным, когда count становится равно 5. То есть, цикл останавливается после 4 прохода.

Если нам нужно выполнить блок кода, когда условие больше не является истинным, мы можем использовать else.

```py
  # синтаксис
while condition:
    code goes here
else:
    code goes here
```

**Пример:**

```py
count = 0
while count < 5:
    print(count)
    count = count + 1
else:
    print(count)
```

В этом случае, после 4 проходов, цикл выведет число 5 т.к. мы используем оператор else, а count будет равен 5. 


### Break and Continue - Часть 1

- Break: Мы можем использовать оператор break, когда хотим завершить цикл по определенным правилам.

```py
# синтаксис
while condition:
    code goes here
    if another_condition:
        break
```

**Пример:**

```py
count = 0
while count < 5:
    print(count)
    count = count + 1
    if count == 3:
        break
```

В данном примере цикл while проходит числа 0, 1, 2 и когда достагает 3, цикл прерывается.

- Continue:  С помощью оператора continue мы можем пропустить текущую итерацию и продолжить со следующей.

```py
  # синтаксис
while condition:
    code goes here
    if another_condition:
        continue
```

**Примеры:**

```py
count = 0
while count < 5:
    if count == 3:
        continue
    print(count)
    count = count + 1
```

В этом примере цикл вернет нам числа 0, 1, 2 и 4, т.к. в условии выполнения цикла мы пропускаем цифру 3.

### Цикл for

Для создания цикла for в Python используется ключевое слово **for**. Цикл **for** используется для итерации по последовательности (списку, кортежу, словарю, множеству или строке).

- Цикл for со списками

```py
# синтаксис
for iterator in lst:
    код будет здесь
```

**Пример:**

```py
numbers = [0, 1, 2, 3, 4, 5]
for number in numbers: # number - временное имя для обращения к элементам списка, действует только внутри этого цикла
    print(number)       # числа будут выводиться построчно от 0 до 5
```

- Цикл for со строками

```py
# синтаксис
for iterator in string:
    код будет здесь
```

**Пример:**

```py
language = 'Python'
for letter in language:
    print(letter)


for i in range(len(language)):
    print(language[i])
```

- Цикл for с кортежами

```py
# синтаксис
for iterator in tpl:
    код будет здесь
```

**Пример:**

```py
numbers = (0, 1, 2, 3, 4, 5)
for number in numbers:
    print(number)
```

- Цико for со словарями
  При итерации по словарю с помощью цикла for в Python мы получаем ключи этого словаря.

```py
  # синтаксис
for iterator in dct:
    код будет здесь
```

**Пример:**

```py
person = {
    'first_name':'Asabeneh',
    'last_name':'Yetayeh',
    'age':250,
    'country':'Finland',
    'is_marred':True,
    'skills':['JavaScript', 'React', 'Node', 'MongoDB', 'Python'],
    'address':{
        'street':'Space street',
        'zipcode':'02210'
    }
}
for key in person:
    print(key)

for key, value in person.items():
    print(key, value) # так мы получаем как ключи, так и значения
```

- Цикл for во множествах

```py
# синтаксис
for iterator in st:
    код будет здесь
```

**Пример:**

```py
it_companies = {'Facebook', 'Google', 'Microsoft', 'Apple', 'IBM', 'Oracle', 'Amazon'}
for company in it_companies:
    print(company)
```

### Break and Continue - Часть 2

Небольшое напоминание: __Break__: Мы используем break, когда хотим прервать выполнение цикла до его завершения.

```py
# синтаксис
for iterator in sequence:
    код будет здесь
    if condition:
        break
```

**Пример:**

```py
numbers = (0,1,2,3,4,5)
for number in numbers:
    print(number)
    if number == 3:
        break
```

В приведенном выше примере цикл останавливается, когда достигнуто значение 3.

Continue: Мы используем continue, когда хотим пропустить итерации цикла.

```py
  # синтаксис
for iterator in sequence:
    код будет здесь
    if condition:
        continue
```

**Пример:**

```py
numbers = (0,1,2,3,4,5)
for number in numbers:
    print(number)
    if number == 3:
        continue
    print('Next number should be ', number + 1) if number != 5 else print("loop's end") # для коротких условий нужны оба оператора if и else
print('outside the loop')
```

В приведенном выше примере, если число равно 3, шаг после условия (но внутри цикла) пропускается, и выполнение цикла продолжается, если остались еще итерации.


Функция **range()** используется для создания списка чисел. range(start, end, step) принимает три аргумента: начальное значение(start), конечное значение(end) и шаг(step). По умолчанию начальное значение равно 0, а шаг равен 1. Для работы функции нам необходимо указать конечный параметр, тогда остальные значения возьмутся по умолчанию, либо указать 2 или 3 аргумента.

Создание последовательностей с использованием range

```py
lst = list(range(11)) 
print(lst) # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
st = set(range(1, 11))  # 2 аргумента указывают начало и конец последовательности, шаг установлен по умолчанию равным 1
print(st) # {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

lst = list(range(0,11,2))
print(lst) # [0, 2, 4, 6, 8, 10]
st = set(range(0,11,2))
print(st) #  {0, 2, 4, 6, 8, 10}
```

```py
# синтаксис
for iterator in range(start, end, step):
    код будет здесь
```

**Пример:**

```py
for number in range(11):
    print(number)   # возвращает числа с 0 до 10, число 11 не включено
```

### Вложенные циклы

We can write loops inside a loop.

```py
# синтаксис
for x in y:
    for t in x:
        print(t)
```

**Пример:**

```py
person = {
    'first_name': 'Asabeneh',
    'last_name': 'Yetayeh',
    'age': 250,
    'country': 'Finland',
    'is_marred': True,
    'skills': ['JavaScript', 'React', 'Node', 'MongoDB', 'Python'],
    'address': {
        'street': 'Space street',
        'zipcode': '02210'
    }
}
for key in person:
    if key == 'skills':
        for skill in person['skills']:
            print(skill)
```

### For Else

Если мы хотим выполнить какое-то действие после окончания цикла, мы используем конструкцию else.

```py
# синтаксис
for iterator in range(start, end, step):
    do something
else:
    print('The loop ended')
```

**Пример:**

```py
for number in range(11):
    print(number)   # выводит числа от 0 до 10, число 11 не входит
else:
    print('The loop stops at', number)
```

### Pass

В Python, если мы не хотим пить код после двоеточего, мы можем написать ключевое слово pass, чтобы избежать ошибок. Также мы можем использовать его в качестве заполнителя для будущих операторов.

**Пример:**

```py
for number in range(6):
    pass
```

🌕 Ты достиг важного этапа, ты неудержим. Продолжай в том же духе! Ты только что завершил 10-й день испытаний и стал ещё на шаг ближе к свой цели. Теперь давай займемся тренировкой нашего мозга и закреплением материала. 

## 💻 Упражнения: День 10

### Упражнения: Уровень 1

1. Переберите числа от 0 до 10 с помощью цикла for, а после с помощью цикла while. 
2. Переберите числа от 10 до 0 с помощью цикла for, а после с помощью цикла while. 
3. Напишите цикл, который сделает семь вызовов функции **print()**, чтобы получить следующий треугольник:

   ```py
     #
     ##
     ###
     ####
     #####
     ######
     #######
   ```

4. Используйте вложенные циклы для создания следующей структуры:

   ```sh
   # # # # # # # #
   # # # # # # # #
   # # # # # # # #
   # # # # # # # #
   # # # # # # # #
   # # # # # # # #
   # # # # # # # #
   # # # # # # # #
   ```

5. Выведите данный пример при помощи цикла for

   ```sh
   0 x 0 = 0
   1 x 1 = 1
   2 x 2 = 4
   3 x 3 = 9
   4 x 4 = 16
   5 x 5 = 25
   6 x 6 = 36
   7 x 7 = 49
   8 x 8 = 64
   9 x 9 = 81
   10 x 10 = 100
   ```

6. Переберите список ['Python', 'Numpy', 'Pandas', 'Django', 'Flask'] и выведите каждый элемент списка на отдельной строке. 
7. Используйте цикл for для вывода **четных** чисел в диапазоне от 0 до 100.
8. Используйте цикл for для вывода **нечетных** чисел в диапазоне от 0 до 100.
   
### Упражнения: Уровень 2
    
1.  Используйте цикл for для итерации от 0 до 100 и выведите сумму всех чисел:

   ```sh
   Сумма всех чисел равна 5050.
   ```

2. Используйте цикл for для итерации от 0 до 100 и выведите  сумму всех четных чисел и сумму всех нечетных чисел:

    ```sh
    Сумма всех четных чисел = 2550. Сумма всех нечетных чисел = 2500.
    ```

### Упражнения: Уровень 3


1. Перейдите по [ссылке](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/countries.py). Пройдитесь по списку стран и выведите все страны, содержащие слово land в своем названии.
2. Есть список фруктов, ['banana', 'orange', 'mango', 'lemon']. Разверните его с помощью цикла.
3. Перейдите по  [ссылке](https://github.com/Asabeneh/30-Days-Of-Python/blob/master/data/countries-data.py):
   1. Сколько всего языков данно в файле?
   2. Найдите десять наиболее распространенных языков в файле.
   3. Найдите десять наиболее населенных стран мира.

🎉 ПОЗДРАВЛЯЕМ!  🎉

[<< День 9](../09_Day_Conditionals/09_conditionals.md) | [День 11 >>](../11_Day_Functions/11_functions.md)


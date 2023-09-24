<div align="center">
  <h1> 30 дней Python: День 5 - Списки</h1>
  <a href="https://github.com/obulygin/30-Days-Of-Python/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=obulygin/30-Days-Of-Python" />
</div>

[<< День 4](../04_Day_Strings/04_strings.md) | [День 6 >>](../06_Day_Tuples/06_tuples.md)

![30DaysOfPython](../images/30daysofpython.png)

- [День 5](#день-5)
  - [Списки](#списки)
    - [Как создавать списки.](#как-создавать-списки)
    - [Доступ к элементам списка с использованием положительного индексирования](#доступ-к-элементам-списка-с-использованием-положительного-индексирования)
    - [Доступ к элементам списка с использованием отрицательного индексирования](#доступ-к-элементам-списка-с-использованием-отрицательного-индексирования)
    - [Распаковка элементов списка](#распаковка-элементов-списка)
    - [Срезы элементов спика](#срезы-элементов-спика)
    - [Изменение списков](#изменение-списков)
    - [Проверка элементов списка](#проверка-элементов-списка)
    - [Добавление элементов в список](#добавление-элементов-в-список)
    - [Вставка элементов в список](#вставка-элементов-в-список)
    - [Удаление элементов из списка](#удаление-элементов-из-списка)
    - [Удаление элементов с использованием метода pop()](#удаление-элементов-с-использованием-метода-pop)
    - [Удаление элементов с использованием метода del](#удаление-элементов-с-использованием-метода-del)
    - [Очистка списка](#очистка-списка)
    - [Копирование списка](#копирование-списка)
    - [Объединение списков](#объединение-списков)
    - [Подсчет элементов списка](#подсчет-элементов-списка)
    - [Поиск индекса элемента](#поиск-индекса-элемента)
    - [Разворот списка](#разворот-списка)
    - [Сортировка списка](#сортировка-списка)
  - [💻 Упражнения: День 5](#-упражнения-день-5)
    - [Упражнения: Уровень 1](#упражнения-уровень-1)
    - [Упражнения: Уровень 2](#упражнения-уровень-2)

# День 5

## Списки

В Python существует четыре типа коллекций данных:

- Список (List): это упорядоченная и изменяемая коллекция. Допускается наличие повторяющихся элементов.
- Кортеж (Tuple): это упорядоченная и неизменяемая коллекция. Также допускается наличие повторяющихся элементов.
- Множество (Set): это неупорядоченная, неиндексированная и неизменяемая коллекция, можем добавлять новые элементы. Повторяющиеся элементы не допускаются (удаляются из множества).
- Словарь (Dictionary): это неупорядоченная, изменяемая и индексированная коллекция. Не допускается наличие повторяющихся элементов.

Список может быть пустым или содержать элементы различных типов данных.

### Как создавать списки.

В Python мы можем создавать списки двумя способами:

- Используя встроенную функцию list():

```py
# синтаксис
lst = list()
```

```py
empty_list = list() # Это пустой список, без элементов
print(len(empty_list)) # 0
```

- Using square brackets, []

```py
# синтаксис
lst = []
```

```py
empty_list = [] # также пустой список, без элементов
print(len(empty_list)) # 0
```

Оба способа создают пустые списки, не содержащие никаких элементов. Функция len() используется для определения длины списка, и в данном случае она возвращает 0, так как список пустой.

```py
fruits = ['banana', 'orange', 'mango', 'lemon']                     # список фруктов
vegetables = ['Tomato', 'Potato', 'Cabbage','Onion', 'Carrot']      # список овощей
animal_products = ['milk', 'meat', 'butter', 'yoghurt']              # список продуктов животного происхождения
web_techs = ['HTML', 'CSS', 'JS', 'React','Redux', 'Node', 'MongDB'] # список веб-технологий
countries = ['Finland', 'Estonia', 'Denmark', 'Sweden', 'Norway']   # cпиок стран

# Вывод списков и их длины
print('Fruits:', fruits)
print('Number of fruits:', len(fruits))
print('Vegetables:', vegetables)
print('Number of vegetables:', len(vegetables))
print('Animal products:',animal_products)
print('Number of animal products:', len(animal_products))
print('Web technologies:', web_techs)
print('Number of web technologies:', len(web_techs))
print('Countries:', countries)
print('Number of countries:', len(countries))
```

```sh
output
Fruits: ['banana', 'orange', 'mango', 'lemon']
Number of fruits: 4
Vegetables: ['Tomato', 'Potato', 'Cabbage', 'Onion', 'Carrot']
Number of vegetables: 5
Animal products: ['milk', 'meat', 'butter', 'yoghurt']
Number of animal products: 4
Web technologies: ['HTML', 'CSS', 'JS', 'React', 'Redux', 'Node', 'MongDB']
Number of web technologies: 7
Countries: ['Finland', 'Estonia', 'Denmark', 'Sweden', 'Norway']
Number of countries: 5
```

- В списки могут быть включены элементы различных типов данных:

```py
 lst = ['Asabeneh', 250, True, {'country':'Finland', 'city':'Helsinki'}] # список, содержащий элементы различных типов данных
```

### Доступ к элементам списка с использованием положительного индексирования

Для доступа к каждому элементу списка мы используем его индекс. Индексация в списках начинается с 0. Ниже приведена иллюстрация, которая показывает, где начинается индексация:

![List index](../images/list_index.png)

```py
fruits = ['banana', 'orange', 'mango', 'lemon']
first_fruit = fruits[0] # мы обращаемся к первому элементу с использованием его индекса
print(first_fruit)      # banana
second_fruit = fruits[1]
print(second_fruit)     # orange
last_fruit = fruits[3]
print(last_fruit) # lemon
# Last index
last_index = len(fruits) - 1
last_fruit = fruits[last_index]
```

### Доступ к элементам списка с использованием отрицательного индексирования

Отрицательная индексация начинается с конца, -1 относится к последнему элементу, -2 относится к предпоследнему элементу и т.д.

![List negative indexing](../images/list_negative_indexing.png)

```py
fruits = ['banana', 'orange', 'mango', 'lemon']
first_fruit = fruits[-4]
last_fruit = fruits[-1]
second_last = fruits[-2]
print(first_fruit)      # banana
print(last_fruit)       # lemon
print(second_last)      # mango
```

### Распаковка элементов списка

```py
lst = ['item','item2','item3', 'item4', 'item5']
first_item, second_item, third_item, *rest = lst
print(first_item)     # item1
print(second_item)    # item2
print(third_item)     # item3
print(rest)           # ['item4', 'item5']

```

```py
# Первый пример
fruits = ['banana', 'orange', 'mango', 'lemon','lime','apple']
first_fruit, second_fruit, third_fruit, *rest = lst
print(first_fruit)     # banana
print(second_fruit)    # orange
print(third_fruit)     # mango
print(rest)           # ['lemon','lime','apple']
# Второй прмер
first, second, third,*rest, tenth = [1,2,3,4,5,6,7,8,9,10]
print(first)          # 1
print(second)         # 2
print(third)          # 3
print(rest)           # [4,5,6,7,8,9]
print(tenth)          # 10
# Третий пример
countries = ['Germany', 'France','Belgium','Sweden','Denmark','Finland','Norway','Iceland','Estonia']
gr, fr, bg, sw, *scandic, es = countries
print(gr)
print(fr)
print(bg)
print(sw)
print(scandic)
print(es)
```

### Срезы элементов спика

- Положительная индексация: Мы можем указать диапазон положительных индексов, указав начало, конец и шаг. В результате нам вернется новый список, состоящий из элементов, выделенных нами срезом. (Срезы имеюи значения по умолчани: начало - 0 индекс, конец len(list), шаг - 1)

```py
fruits = ['banana', 'orange', 'mango', 'lemon']
all_fruits = fruits[0:4] # возвращает все фрукты
all_fruits = fruits[0:] # если мы не указываем, конечный индекс, то берутся все оставшиеся элементы
orange_and_mango = fruits[1:3] # не включает первый индекс
orange_mango_lemon = fruits[1:] # возвращает элементы, начиная с 1 индекса и до конца
orange_and_lemon = fruits[::2] # здесь мы использовали третий аргумент, шаг. Будет взят каждый второй элемент - ['banana', 'mango']
```

- Отрицательная индексация: Мы можем указать диапазон отрицательных индексов, указав начало, конец и шаг. В результате нам вернется новый список.

```py
fruits = ['banana', 'orange', 'mango', 'lemon']
all_fruits = fruits[-4:] # возвращает все фрукты
orange_and_mango = fruits[-3:-1] # не включает последний индекс, ['orange', 'mango']
orange_mango_lemon = fruits[-3:] # возвращает элементы, начиная с индекса -3 и до конца списка, ['orange', 'mango', 'lemon']
reverse_fruits = fruits[::-1] # отрицательный шаг возвращает элементы списка в обратном порядке, ['lemon', 'mango', 'orange', 'banana']
```

### Изменение списков

Список является изменяемой упорядоченной коллекцией элементов. 

Давайте посмотрим как мы можем изменить список фруктов:

```py
fruits = ['banana', 'orange', 'mango', 'lemon']
fruits[0] = 'avocado'
print(fruits)       #  ['avocado', 'orange', 'mango', 'lemon']
fruits[1] = 'apple'
print(fruits)       #  ['avocado', 'apple', 'mango', 'lemon']
last_index = len(fruits) - 1
fruits[last_index] = 'lime'
print(fruits)        #  ['avocado', 'apple', 'mango', 'lime']
```

### Проверка элементов списка

Можно проверить, содержит ли список какую-либо переменную, используя оператор __in__. 

Давайте взглянем на пример:

```py
fruits = ['banana', 'orange', 'mango', 'lemon']
does_exist = 'banana' in fruits
print(does_exist)  # True
does_exist = 'lime' in fruits
print(does_exist)  # False
```

### Добавление элементов в список

Чтобы добавить элемент в конец существующего списка, мы используем метод __append()__.

```py
# синтаксис
lst = list()
lst.append(item)
```

```py
fruits = ['banana', 'orange', 'mango', 'lemon']
fruits.append('apple')
print(fruits)           # ['banana', 'orange', 'mango', 'lemon', 'apple']
fruits.append('lime')   # ['banana', 'orange', 'mango', 'lemon', 'apple', 'lime']
print(fruits)
```

### Вставка элементов в список

Мы можем использовать метод __insert()__ для вставки одного элемента по указанному индексу в списке. Обратите внимание, что остальные элементы сдвигаются вправо. Метод insert() принимает два аргумента: индекс и элемент для вставки.

```py
# синтаксис
lst = ['item1', 'item2']
lst.insert(index, item)
```

```py
fruits = ['banana', 'orange', 'mango', 'lemon']
fruits.insert(2, 'apple') # вставляем apple между orange и mango
print(fruits)           # ['banana', 'orange', 'apple', 'mango', 'lemon']
fruits.insert(3, 'lime')   # ['banana', 'orange', 'apple', 'lime', 'mango', 'lemon']
print(fruits)
```

### Удаление элементов из списка

Метод __remove()__ удаляет указанный элемент из списка.

```py
# синтаксис
lst = ['item1', 'item2']
lst.remove(item)
```

```py
fruits = ['banana', 'orange', 'mango', 'lemon', 'banana']
fruits.remove('banana')
print(fruits)  # ['orange', 'mango', 'lemon', 'banana'] - этот метод удаляет первое вхождение элемента в списке
fruits.remove('lemon')
print(fruits)  # ['orange', 'mango', 'banana']
```
Метод __remove()__ удаляет первое вхождение указанного элемента из списка. Если в списке есть несколько экземпляров элемента, remove() удалит только первое вхождение.

### Удаление элементов с использованием метода pop()

Метод __pop()__ удаляет элемент с указанным индексом (или последний элемент, если индекс не указан):

```py
# синтаксис
lst = ['item1', 'item2']
lst.pop()       # последний элемент
lst.pop(index)
```

```py
fruits = ['banana', 'orange', 'mango', 'lemon']
fruits.pop()
print(fruits)       # ['banana', 'orange', 'mango']

fruits.pop(0)
print(fruits)       # ['orange', 'mango']
```

### Удаление элементов с использованием метода del

__del__ удаляет элемент с указанным индексом, а также может использоваться для удаления элементов в указанном диапазоне индексов. Оно также может полностью удалить список.

```py
# синтаксис
lst = ['item1', 'item2']
del lst[index] # удалит только один элемент
del lst        # для полного удаления списка
```

```py
fruits = ['banana', 'orange', 'mango', 'lemon', 'kiwi', 'lime']
del fruits[0]
print(fruits)       # ['orange', 'mango', 'lemon', 'kiwi', 'lime']
del fruits[1]
print(fruits)       # ['orange', 'lemon', 'kiwi', 'lime']
del fruits[1:3]     # удалит элементы между указанными индексами
print(fruits)       # ['orange', 'lime']
del fruits
print(fruits)       # Такое применение должно вызвать ошибку: NameError: name 'fruits' is not defined
```

### Очистка списка

Метод __clear()__ позволяет очистить список:

```py
# синтаксис
lst = ['item1', 'item2']
lst.clear()
```

```py
fruits = ['banana', 'orange', 'mango', 'lemon']
fruits.clear()
print(fruits)       # []
```

### Копирование списка

Для создания копии списка можно просто присвоить его новой переменной: **list2** = **list1**. В этом случае **list2** будет ссылаться на тот же самый список, что и **list1**. Если мы внесем изменения в **list2**, они также отразятся на оригинальном списке **list1**. Однако иногда требуется создать полностью независимую копию списка. Для этого можно использовать метод **copy()**.

```py
# синтаксис
lst = ['item1', 'item2']
lst_copy = lst.copy()
```

```py
fruits = ['banana', 'orange', 'mango', 'lemon']
fruits_copy = fruits.copy()
print(fruits_copy)       # ['banana', 'orange', 'mango', 'lemon']
```

### Объединение списков

В Python существует несколько способов объединить (конкатенировать) два или более списков.

- Оператор плюс (+)

```py
# синтаксис
list3 = list1 + list2
```

```py
positive_numbers = [1, 2, 3, 4, 5]
zero = [0]
negative_numbers = [-5,-4,-3,-2,-1]
integers = negative_numbers + zero + positive_numbers
print(integers) # [-5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5]
fruits = ['banana', 'orange', 'mango', 'lemon']
vegetables = ['Tomato', 'Potato', 'Cabbage', 'Onion', 'Carrot']
fruits_and_vegetables = fruits + vegetables
print(fruits_and_vegetables ) # ['banana', 'orange', 'mango', 'lemon', 'Tomato', 'Potato', 'Cabbage', 'Onion', 'Carrot']
```

- Соединение с использованием метода extend().
- Метод **extend()** позволяет добавить список в конец другого списка.

```py
# синтаксис
list1 = ['item1', 'item2']
list2 = ['item3', 'item4', 'item5']
list1.extend(list2)
```

```py
num1 = [0, 1, 2, 3]
num2= [4, 5, 6]
num1.extend(num2)
print('Numbers:', num1) # Numbers: [0, 1, 2, 3, 4, 5, 6]
negative_numbers = [-5,-4,-3,-2,-1]
positive_numbers = [1, 2, 3,4,5]
zero = [0]

negative_numbers.extend(zero)
negative_numbers.extend(positive_numbers)
print('Integers:', negative_numbers) # Integers: [-5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5]
fruits = ['banana', 'orange', 'mango', 'lemon']
vegetables = ['Tomato', 'Potato', 'Cabbage', 'Onion', 'Carrot']
fruits.extend(vegetables)
print('Fruits and vegetables:', fruits ) # Fruits and vegetables: ['banana', 'orange', 'mango', 'lemon', 'Tomato', 'Potato', 'Cabbage', 'Onion', 'Carrot']
```

### Подсчет элементов списка

Метод **count()** используется для подсчета количества появления элемента в списке. Возвращает целое число.

```py
# синтаксис
lst = ['item1', 'item2']
lst.count(item)
```

```py
fruits = ['banana', 'orange', 'mango', 'lemon']
print(fruits.count('orange'))   # в этом примере элемент 'orange' появляется один раз, поэтому количество равно 1
ages = [22, 19, 24, 25, 26, 24, 25, 24]
print(ages.count(24))           # 3
```

### Поиск индекса элемента

Метод **index()** возвращает индекс элемента в списке:

```py
# синтаксис
lst = ['item1', 'item2']
lst.index(item)
```

```py
fruits = ['banana', 'orange', 'mango', 'lemon']
print(fruits.index('orange'))   # 1
ages = [22, 19, 24, 25, 26, 24, 25, 24]
print(ages.index(24))           # 2, первое вхождение
```

### Разворот списка

Метод **reverse()** изменяет порядок элементов списка на обратный.

```py
# синтаксис
lst = ['item1', 'item2']
lst.reverse()

```

```py
fruits = ['banana', 'orange', 'mango', 'lemon']
fruits.reverse()
print(fruits) # ['lemon', 'mango', 'orange', 'banana']
ages = [22, 19, 24, 25, 26, 24, 25, 24]
ages.reverse()
print(ages) # [24, 25, 24, 26, 25, 24, 19, 22]
```

### Сортировка списка

Для сортировки списков мы можем использовать метод **sort()** или встроенную функцию **sorted()**. Метод **sort()** переупорядочивает элементы списка в порядке возрастания и изменяет исходный список. Если в методе **sort()** задать необязательны аргумент **reverse** и установить его в значении **True**, список будет упорядочен в порядке убывания.

- sort(): метод изменяет исходный список

  ```py
  # синтаксис
  lst = ['item1', 'item2']
  lst.sort()                # по возрастанию
  lst.sort(reverse=True)    # по убыванию
  ```

  **Примеры:**

  ```py
  fruits = ['banana', 'orange', 'mango', 'lemon']
  fruits.sort()
  print(fruits)             # отсортировано в алфавитном порядке, ['banana', 'lemon', 'mango', 'orange']
  fruits.sort(reverse=True)
  print(fruits) # ['orange', 'mango', 'lemon', 'banana']
  ages = [22, 19, 24, 25, 26, 24, 25, 24]
  ages.sort()
  print(ages) #  [19, 22, 24, 24, 24, 25, 25, 26]
 
  ages.sort(reverse=True)
  print(ages) #  [26, 25, 25, 24, 24, 24, 22, 19]
  ```

  sorted(): возвращает упорядоченный список без изменения исходного списка
  
  **Пример:**

  ```py
  fruits = ['banana', 'orange', 'mango', 'lemon']
  print(sorted(fruits))   # ['banana', 'lemon', 'mango', 'orange']
  # Reverse order
  fruits = ['banana', 'orange', 'mango', 'lemon']
  fruits = sorted(fruits,reverse=True)
  print(fruits)     # ['orange', 'mango', 'lemon', 'banana']
  ```

🌕 Вы упорны и уже достигли немалого. Вы только что завершили 5-й день и стали на пять шагов ближе к великим достижениям. Теперь пора заняться упражнениями для вашего ума.

## 💻 Упражнения: День 5

### Упражнения: Уровень 1 

1. Объявите пустой список.
2. Объявите список с более чем 5 элементами.
3. Найдите длину вашего списка.
4. Получите первый элемент, средний элемент и последний элемент списка.
5. Объявите список с именем mixed_data_types и поместите в него ваши данные (имя, возраст, рост, семейное положение, адрес).
6. Объявите список с именем it_companies и присвойте ему начальные значения: Facebook, Google, Microsoft, Apple, IBM, Oracle и Amazon.
7. Выведите список на экран с помощью print().
8. Выведите количество компаний в списке.
9. Выведите первую, среднюю и последнюю компанию.
10. Выведите список после изменения одной из компаний.
11. Добавьте в список IT-компанию.
12. Вставьте IT-компанию в середину списка компаний.
13. Преобразуйте одно из названий компаний в списке it_companies в верхний регистр (кроме IBM!).
14. Объедините элементы списка it_companies с помощью строки "#; ".
15. Проверьте, существует ли какая-либо компания в списке it_companies.
16. Отсортируйте список с помощью метода sort().
17. Отсортируйте список в обратном порядке с помощью метода reverse().
18. Возьмите срез из **первых** трех компаний списка.
19. Возьмите срез из **последних** трех компаний списка.
20. Возьмите срез из центральной компании.
21. Удалите первую IT-компанию из списка.
22. Удалите среднюю IT-компанию или компании из списка.
23. Удалите последнюю IT-компанию из списка
24. Удалите все IT-компании из списка.
25. Удалите список **it_companies**.
26. Объедините следующие списки:

    ```py
    front_end = ['HTML', 'CSS', 'JS', 'React', 'Redux']
    back_end = ['Node','Express', 'MongoDB']
    ```

27. После объединения списков в вопросе 26 скопируйте объединенный список и присвойте его переменной full_stack. Затем вставьте Python и SQL после Redux.

### Упражнения: Уровень 2

1. Следующий список содержит возраста 10 студентов:

```sh
ages = [19, 22, 19, 24, 20, 25, 26, 24, 25, 24]
```

- Отсортируйте список и найдите минимальный и максимальный возраст.
- Добавьте минимальный и максимальный возраст еще раз в список.
- Найдите медианный возраст (один средний элемент или два средних элемента, разделенных пополам).
- Найдите средний возраст (сумма всех элементов, разделенная на их количество).
- Найдите диапазон возрастов (максимальный возраст минус минимальный возраст).
- Сравните значения (min - среднее) и (max - среднее), используя метод abs().
  

2. Найдите среднюю страну (или страны) в [списке стран](https://github.com/Asabeneh/30-Days-Of-Python/tree/master/data/countries.py)
3. Разделите список стран на два равных списка, если количество стран четное, а если нет, добавьте одну дополнительную страну в впервый список.
4. ['China', 'Russia', 'USA', 'Finland', 'Sweden', 'Norway', 'Denmark'].  Распакуйте первые три страны, а остальные - объедините как страны Скандинавии.

🎉 ПОЗДРАВЛЯЕМ! 🎉

[<< День 4](../04_Day_Strings/04_strings.md) | [День 6 >>](../06_Day_Tuples/06_tuples.md)


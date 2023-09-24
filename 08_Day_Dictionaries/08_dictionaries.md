<div align="center">
  <h1> 30 дней Python: День 8 - Словари </h1>
  <a href="https://github.com/obulygin/30-Days-Of-Python/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=obulygin/30-Days-Of-Python" />
</div>

[<< День 7 ](../07_Day_Sets/07_sets.md) | [День 9 >>](../09_Day_Conditionals/09_conditionals.md)

![30DaysOfPython](../images/30daysofpython.png)

- [День 8](#день-8)
  - [Словари](#словари)
    - [Создание словаря](#создание-словаря)
    - [Длина словаря](#длина-словаря)
    - [Доступ к элементам словаря](#доступ-к-элементам-словаря)
    - [Добавление элементов в словарь](#добавление-элементов-в-словарь)
    - [Изменение элементов в словаре](#изменение-элементов-в-словаре)
    - [Проверка ключей в словаре](#проверка-ключей-в-словаре)
    - [Удаление пары ключ-значение из словаря](#удаление-пары-ключ-значение-из-словаря)
    - [Преобразование словаря в список элементов](#преобразование-словаря-в-список-элементов)
    - [Очистка словаря](#очистка-словаря)
    - [Удаление словаря](#удаление-словаря)
    - [Копирование словаря](#копирование-словаря)
    - [Получение ключей словаря в виде списка](#получение-ключей-словаря-в-виде-списка)
    - [Получение значений словаря в виде списка](#получение-значений-словаря-в-виде-списка)
  - [Упражнения: День 8](#упражнения-день-8)

# День 8

## Словари

Словарь - это коллекция неупорядоченных, изменяемых (mutable) пар (ключ: значение) типов данных.

### Создание словаря

Для создания словаря в Python мы используем фигурные скобки {} или встроенную функцию *dict()*.

```py
# синтаксис
empty_dict = {}
# создание словаря со значениями
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
```

**Например:**

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
```

Вышеуказанный словарь показывает, что значение в словаре может быть любым типом данных: строкой, булевым значением, списком, кортежем, множеством или другим словарем.

### Длина словаря

Функция *len()* возвращает количество пар "ключ: значение" в словаре.

```py
# синтаксис
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
print(len(dct)) # 4
```

**Например:**

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
print(len(person)) # 7

```

### Доступ к элементам словаря

Мы можем получить доступ к элементам словаря, обратившись к ним по имени ключа.

```py
# синтаксис
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
print(dct['key1']) # value1
print(dct['key4']) # value4
```

**Например:**

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
print(person['first_name']) # Asabeneh
print(person['country'])    # Finland
print(person['skills'])     # ['JavaScript', 'React', 'Node', 'MongoDB', 'Python']
print(person['skills'][0])  # JavaScript
print(person['address']['street']) # Space street
print(person['city'])       # Error
```

Доступ к элементу по имени ключа вызовет ошибку, если ключа не существует. Чтобы избежать этой ошибки, мы должны сначала проверить, существует ли ключ, или мы можем использовать метод _get()_. Метод _get()_ возвращает *None* (является объектом типа NoneType), если ключа не существует.

**Например:**

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
print(person.get('first_name')) # Asabeneh
print(person.get('country'))    # Finland
print(person.get('skills')) #['HTML','CSS','JavaScript', 'React', 'Node', 'MongoDB', 'Python']
print(person.get('city'))   # None
```

### Добавление элементов в словарь

Мы можем добавлять новые пары "ключ: значение" в словарь.

```py
# sсинтаксис
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
dct['key5'] = 'value5'
```

**Например:**

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
person['job_title'] = 'Instructor'
person['skills'].append('HTML')
print(person)
```

### Изменение элементов в словаре

Мы можем изменять элементы в словаре.

```py
# syntax
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
dct['key1'] = 'value-one'
```

**Например:**

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
person['first_name'] = 'Eyob'
person['age'] = 252
```

### Проверка ключей в словаре

Используем оператор _in_ для проверки существования ключа в словаре. 

```py
# синтаксис
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
print('key2' in dct) # True
print('key5' in dct) # False
```

### Удаление пары ключ-значение из словаря

- _pop(key)_: удаляет элемент с указанным именем ключа:
- _popitem()_: удаляет последний элемент
- _del_: удаляет элемент с указанным именем ключа

```py
# синтаксис
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
dct.pop('key1') # удаляет элемент с ключом 'key1'
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
dct.popitem() # удаляет последний элемент
del dct['key2'] # удаляет элемент с ключом 'key2'
```

**Например:**

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
person.pop('first_name')        # Удаляет элемент с именем "firstname"
person.popitem()                # Удаляет элемент с именем "address"
del person['is_married']        # Удаляет элемент с именем "is_married"
```

### Преобразование словаря в список элементов

Метод _items()_ преобразует словарь в список кортежей.

```py
# синтаксис
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
print(dct.items()) # dict_items([('key1', 'value1'), ('key2', 'value2'), ('key3', 'value3'), ('key4', 'value4')])
```

### Очистка словаря

Если мы не хотим оставлять элементы в словаре, мы можем очистить его, используя метод _clear()_.

```py
# синтаксис
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
print(dct.clear()) # None
```

### Удаление словаря

Если мы больше не используем словарь, мы можем полностью удалить его с помощью оператора del.

```py
# синтаксис
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
del dct
```

### Копирование словаря

Мы можем скопировать словарь с помощью метода _copy()_. Используя копию, мы можем избежать изменения исходного словаря.

```py
# синтаксис
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
dct_copy = dct.copy() # {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
```

### Получение ключей словаря в виде списка

Метод _keys()_ позволяет получить все ключи словаря в виде списка.

```py
# синтаксис
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
keys = dct.keys()
print(keys)     # dict_keys(['key1', 'key2', 'key3', 'key4'])
```

### Получение значений словаря в виде списка

Метод _values()_ позволяет получить все значения словаря в виде списка

```py
# синтаксис
dct = {'key1':'value1', 'key2':'value2', 'key3':'value3', 'key4':'value4'}
values = dct.values()
print(values)     # dict_values(['value1', 'value2', 'value3', 'value4'])
```

🌕 Вы просто великолепны! Теперь вы обладаете непревзойденной мощью словарей. Вы только что успешно выполнили задания восьмого дня и находитесь на 8 шагов впереди, двигаясь по пути к великолепию. Теперь давайте сделаем несколько упражнений для вашего ума и мышц.

## Упражнения: День 8

1. Создайте пустой словарь с именем "dog".
2. Добавьте в словарь "dog" ключи "name", "color", "breed", "legs" и "age".
3. Создайте словарь "student" и добавьте ключи "first_name", "last_name", "gender", "age", "marital status", "skills", "country", "city" и "address".
4. Получите длину словаря "student".
5. Получите значение ключа "skills" и проверьте его тип данных, он должен быть списком.
6. Измените значения ключа "skills", добавив одну или две навыка.
7. Получите ключи словаря в виде списка.
8. Получите значения словаря в виде списка.
9. Преобразуйте словарь в список кортежей с помощью метода _items()_.
10. Удалите один из элементов из словаря.
11. Удалите один из словарей полностью.

🎉 ПОЗДРАВЛЯЕМ ! 🎉

[<< День 7 ](../07_Day_Sets/07_sets.md) | [День 9 >>](../09_Day_Conditionals/09_conditionals.md)

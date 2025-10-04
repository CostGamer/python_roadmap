# Правила
- Все что не отмечено звездочкой надо точно и уверено знать  
- `*` - must have for interview  
- `**` - for flex in the interview

----

# `1` Python
## `1.1` Что такое компилируемых и интерпретируемых языки? В чем их отличие?  
## `1.2` Плюсы и минусы `Python`  
## `1.3` Какие задачи решает `Python`?

----

# `2` Ввод - вывод
## `2.1` print()
### `2.1.1` Как работает `print()`?  
### `2.1.2` Что такон аргумент?

## `2.2` input()
### `2.2.1` Как работает `input()`? Что принимает `input()`?  
### `2.2.2` Что такое переменная? Как можно и принято называть переменную?  
### `2.2.3` Что такое комментарий и как его делать?  
### `2.2.4` Несколько переменных в `print()`  
### `2.2.5` Переменные в `input()`  
### `2.2.6` Параметры `sep` & `end` в `print()`  

## `2.3` PEP8
### `2.3.1` Что такое `PEP8`?  
### `2.3.2` Обшие рекомендации  

## `2.4` Целочисленные операции
### `2.4.1` `int()`, `int(input())`  
### `2.4.2` Математические операции  
### `2.4.2` Операторы: (), **, //, %  

----

# `3` Условный оператор
## `3.1` `if-else`  
## `3.2` Что такое табуляция?  
## `3.3` Какие есть операторы сравнения? Цепочки сравнения и транзитивность  
## `3.4` Логические операции: `and`, `or`, `not`
Логические операции используются для комбинирования условий и работы с булевыми значениями (`True` и `False`).

### **Оператор `and` (логическое И)**
Возвращает `True`, только если **оба** операнда истинны.

```python
print(True and True)    # True
print(True and False)   # False
print(False and True)   # False
print(False and False)  # False

# Практический пример
age = 25
has_license = True

if age >= 18 and has_license:
    print("Можешь водить машину")  # Выведет: Можешь водить машину

# С числами (непустые значения считаются True)
x = 5
if x > 0 and x < 10:
    print("x находится между 0 и 10")  # Выведет: x находится между 0 и 10
```

### **Оператор `or` (логическое ИЛИ)**
Возвращает `True`, если **хотя бы один** операнд истинен.

```python
print(True or True)     # True
print(True or False)    # True
print(False or True)    # True
print(False or False)   # False

# Практический пример
is_weekend = False
is_holiday = True

if is_weekend or is_holiday:
    print("Можно отдыхать!")  # Выведет: Можно отдыхать!

# Проверка нескольких условий
role = "admin"
if role == "admin" or role == "moderator":
    print("Доступ разрешён")  # Выведет: Доступ разрешён
```

### **Оператор `not` (логическое НЕ)**
Инвертирует булево значение: `True` становится `False` и наоборот.

```python
print(not True)   # False
print(not False)  # True

# Практический пример
is_logged_in = False

if not is_logged_in:
    print("Пожалуйста, войдите в систему")  # Выведет: Пожалуйста, войдите в систему

# Проверка на пустоту
items = []
if not items:
    print("Список пуст")  # Выведет: Список пуст
```

### **Возвращаемые значения (не только True/False)**

В Python логические операторы возвращают **сам операнд**, а не обязательно `True` или `False`.

```python
# and возвращает первый False или последний операнд
print(5 and 10)      # 10 (оба истинны, вернули последний)
print(0 and 10)      # 0 (первый ложный)
print(5 and 0)       # 0 (второй ложный)
print("" and "hi")   # "" (пустая строка ложная)

# or возвращает первый True или последний операнд
print(5 or 10)       # 5 (первый истинный)
print(0 or 10)       # 10 (второй истинный)
print(0 or "")       # "" (оба ложные, вернули последний)
print(None or "default")  # "default" (часто для значений по умолчанию)

# Практическое применение
username = input("Имя: ") or "Гость"  # Если пустой ввод, то "Гость"
print(f"Привет, {username}!")
```


## `3.5` (`*`) Комбинирование и приоритизация логических операций  
При комбинировании нескольких логических операторов важно понимать порядок их выполнения.

### **Приоритет логических операторов:**
1. **`not`** — выполняется первым (наивысший приоритет)
2. **`and`** — выполняется вторым
3. **`or`** — выполняется последним (наименьший приоритет)

```python
# Пример без скобок
result = True or False and False
# Сначала: False and False = False
# Затем: True or False = True
print(result)  # True

# То же самое с явными скобками
result = True or (False and False)
print(result)  # True

# С оператором not
result = not True or False
# Сначала: not True = False
# Затем: False or False = False
print(result)  # False

# Более сложный пример
result = not False and True or False
# 1. not False = True
# 2. True and True = True
# 3. True or False = True
print(result)  # True
```

### **Использование скобок для ясности**

Даже зная приоритет, **всегда используйте скобки** для сложных выражений — это улучшает читаемость.

```python
age = 25
has_license = True
has_car = False

# Без скобок (может быть неочевидно)
can_drive = age >= 18 and has_license or has_car
print(can_drive)  # True

# Со скобками (понятнее)
can_drive = (age >= 18 and has_license) or has_car
print(can_drive)  # True

# Другая группировка даёт другой результат
can_drive = age >= 18 and (has_license or has_car)
print(can_drive)  # True
```

### **Практические примеры комбинирования**

```python
# Проверка диапазона
x = 15
if x > 10 and x < 20:
    print("x между 10 и 20")  # Выведет: x между 10 и 20

# Альтернативная запись (более питоническая)
if 10 < x < 20:
    print("x между 10 и 20")  # Выведет: x между 10 и 20

# Сложное условие с несколькими операторами
role = "user"
is_verified = True
age = 20

if (role == "admin" or role == "moderator") and is_verified and age >= 18:
    print("Полный доступ")
else:
    print("Ограниченный доступ")  # Выведет: Ограниченный доступ

# Проверка с not
password = "12345"
if not (len(password) >= 8 and password.isalnum()):
    print("Слабый пароль")  # Выведет: Слабый пароль

# Множественные условия
score = 85
attendance = 90

# Сначала and, потом or
if score >= 90 or score >= 80 and attendance >= 85:
    print("Отлично!")  # Выведет: Отлично!
    # Выполнится: score >= 80 and attendance >= 85 = True
    # Затем: False or True = True

# С явными скобками для другой логики
if (score >= 90 or score >= 80) and attendance >= 85:
    print("Хорошо!")  # Выведет: Хорошо!
```

### **Таблица истинности для комбинаций**

```python
# Все возможные комбинации для двух переменных
A = True
B = False

print(f"A and B = {A and B}")        # False
print(f"A or B = {A or B}")          # True
print(f"not A = {not A}")            # False
print(f"not A and B = {not A and B}")  # False
print(f"not A or B = {not A or B}")    # False
print(f"A and not B = {A and not B}")  # True
print(f"not (A and B) = {not (A and B)}")  # True (закон Де Моргана)
print(f"not A or not B = {not A or not B}")  # True (эквивалентно предыдущему)
```

**Важные правила:**
- Всегда используйте скобки для сложных выражений
- `not` имеет наивысший приоритет
- `and` выполняется раньше `or`
- Python использует короткое замыкание — вычисления останавливаются, как только результат становится очевидным

## `3.6` Вложенные условия  
## `3.7` Каскадные условия. Что такое `elif`

----

# `4` Типы данных 1
## `4.1` Что такое тип данных и зачем он нужен?  
## `4.2` Числовые типы данных. Целые числа и числа с плавающей точкой  
## `4.3` Функции `min()`, `max()`, `abs()`  
## `4.4` Функция `round`  
## `4.5` Строковый тип данных  
## `4.6` Функции `len()`, `in` для строк!  
## `4.7` (`*`) `bool` & `None`
### **Тип `bool` (булев тип)**

`bool` — это логический тип данных с двумя значениями: `True` и `False`.

```python
is_active = True
is_deleted = False

print(type(is_active))  # <class 'bool'>

# bool() преобразует значения
print(bool(1))       # True
print(bool(0))       # False
print(bool("text"))  # True
print(bool(""))      # False
print(bool([1, 2]))  # True
print(bool([]))      # False
```

**Ложные значения (Falsy):** `False`, `None`, `0`, `""`, `[]`, `()`, `{}`. Всё остальное — истина.

```python
items = []
if not items:
    print("Список пуст")  # Выведет: Список пуст
```

### **Тип `None` (отсутствие значения)**

`None` — специальный объект, обозначающий отсутствие значения.

```python
result = None
print(type(result))  # <class 'NoneType'>

# Функции без return возвращают None
def greet():
    print("Привет")

print(greet())  # None

# Проверка на None — используй is/is not
value = None
if value is None:  # Правильно
    print("Значение не задано")  # Выведет: Значение не задано
```

**Отличия `None` от `False`:**

```python
print(None == False)   # False — разные объекты
print(bool(None))      # False — но приводится к False
print(None is False)   # False — разные типы

# Оба ложные в условиях, но проверяются по-разному
if not None:
    print("None — ложь")  # Выведет

value = None
if value is None:  # Для None используй is
    print("Это None")  # Выведет: Это None
```

----

# `5` Строки
## `5.1` (`*`) Индексы

`Индекс` — это числовое значение, обозначающее позицию символа в строке. В Python индексы начинаются с `0` для первого символа.

### **Положительные индексы**

Отсчитываются с начала строки, начиная с `0`.

```python
s = "Python"
print(s[0])  # 'P' (первый символ)
print(s[1])  # 'y' (второй символ)
print(s[5])  # 'n' (шестой символ)

# Обращение к несуществующему индексу вызовет ошибку
# print(s[10])  # IndexError: string index out of range

# Длина строки
print(len(s))  # 6
print(s[len(s) - 1])  # 'n' (последний символ через длину)
```

### **Отрицательные индексы**

Отсчитываются с конца строки: `-1` — последний символ, `-2` — предпоследний и так далее.

```python
s = "Python"
print(s[-1])  # 'n' (последний символ)
print(s[-2])  # 'o' (предпоследний)
print(s[-6])  # 'P' (первый символ через отрицательный индекс)

# Соответствие положительных и отрицательных индексов
# s = "Python"
#     P  y  t  h  o  n
#     0  1  2  3  4  5   (положительные)
#    -6 -5 -4 -3 -2 -1   (отрицательные)
```

### **Практические примеры**

```python
text = "Hello, World!"

# Получение первого и последнего символа
first = text[0]
last = text[-1]
print(f"Первый: {first}, Последний: {last}")  # Первый: H, Последний: !

# Проверка символа на позиции
email = "user@example.com"
if email[0] == '@':
    print("Email не может начинаться с @")
else:
    print("Email корректен")  # Выведет: Email корректен

# Получение расширения файла
filename = "document.pdf"
extension = filename[-3:]  # Последние 3 символа (используя срез)
print(extension)  # 'pdf'
```

## `5.2` (`*`) Срезы. Срезы с одним/двумя/тремя параметрами `[x:y:z]` 
`Срез` (slice) позволяет извлечь подстроку, указав диапазон индексов. Синтаксис: `[start:stop:step]`.

- `start` — начальный индекс (включительно), по умолчанию `0`
- `stop` — конечный индекс (не включается!), по умолчанию конец строки
- `step` — шаг, по умолчанию `1`

### **Срезы с двумя параметрами `[start:stop]`**

```python
s = "Python Programming"

# От индекса 0 до 6 (не включая 6)
print(s[0:6])   # 'Python'
print(s[:6])    # 'Python' (start=0 по умолчанию)

# От индекса 7 до конца
print(s[7:])    # 'Programming'

# От 7 до 18
print(s[7:18])  # 'Programming'

# Средняя часть
print(s[3:9])   # 'hon Pr'

# Пустая строка (start >= stop)
print(s[5:5])   # ''
print(s[5:3])   # ''
```

### **Срезы с одним параметром `[:stop]` или `[start:]`**

```python
s = "Python"

# От начала до индекса 3
print(s[:3])    # 'Pyt'

# От индекса 2 до конца
print(s[2:])    # 'thon'

# Вся строка
print(s[:])     # 'Python'
```

### **Срезы с тремя параметрами `[start:stop:step]`**

Параметр `step` определяет шаг выбора символов.

```python
s = "Python Programming"

# Каждый второй символ
print(s[::2])   # 'Pto rgamn'

# Каждый третий символ
print(s[::3])   # 'Ph ormn'

# От 0 до 12 с шагом 2
print(s[0:12:2])  # 'Pto rg'

# От 7 до конца с шагом 2
print(s[7::2])    # 'Pormig'

# Пропуск первых и последних символов, шаг 2
print(s[1:-1:2])  # 'yhno rgmin'
```

### **Практические примеры**

```python
# Извлечение доменного имени из email
email = "user@example.com"
at_index = email.index('@')
domain = email[at_index + 1:]
print(domain)  # 'example.com'

# Получение первых N символов
text = "Hello, World!"
preview = text[:5]
print(preview)  # 'Hello'

# Удаление первого и последнего символа
s = '"quoted text"'
unquoted = s[1:-1]
print(unquoted)  # 'quoted text'

# Каждое второе слово (через split и срез)
sentence = "one two three four five six"
words = sentence.split()
every_second = words[::2]
print(every_second)  # ['one', 'three', 'five']

# Копирование строки
original = "Python"
copy = original[:]
print(copy)  # 'Python'
```

## `5.3` Методы строк (можно посмотреть все, но укажу, которые точно надо знать):  
- `capitalize()`  
- `title()`  
- `lower()`  
- `upper()`  
- `startswith()`  
- `strip()`  
- `isalpha()`  
- `isdigit()`  
- `islower()`  
- `isupper()`

## `5.4` (`*`) Отрицательные срезы  
Отрицательные индексы в срезах позволяют работать с концом строки без вычисления длины. Особенно полезны для реверса строки и извлечения данных с конца.

### **Отрицательные границы среза**

```python
s = "Hello, Python!"

# Последние 6 символов
print(s[-6:])      # 'Python!'

# С 4-го символа с конца до предпоследнего
print(s[-4:-1])    # 'tho'

# Все символы кроме последних 3
print(s[:-3])      # 'Hello, Pyth'

# Все символы кроме первых 7
print(s[7:])       # 'Python!'

# С -10 по -3
print(s[-10:-3])   # ', Pytho'

# Комбинирование положительных и отрицательных
print(s[2:-2])     # 'llo, Python'
```

### **Отрицательный шаг (реверс)**

При отрицательном `step` строка читается справа налево.

```python
s = "Python"

# Реверс строки
print(s[::-1])     # 'nohtyP'

# Каждый второй символ с конца
print(s[::-2])     # 'nhy'

# От конца до начала с шагом 3
print(s[::-3])     # 'nt'

# Реверс подстроки
text = "Hello, World!"
print(text[7:12][::-1])  # 'dlroW'
# Или в одном срезе (сложнее читается):
print(text[11:6:-1])     # 'dlroW'
```

### **Сложные срезы с отрицательными значениями**

При отрицательном шаге `start` должен быть **больше** `stop` (справа от него).

```python
s = "Python Programming"

# От индекса 10 до 5 (справа налево)
print(s[10:5:-1])   # 'mmargor' (неправильное направление)

# От -5 до -10 (справа налево)
print(s[-5:-10:-1]) # 'mim'

# От конца до индекса 7 (справа налево)
print(s[:7:-1])     # 'gnimmargorP'

# От индекса 10 до начала (справа налево)
print(s[10::-1])    # 'rP nohtyP'

# Весь текст в обратном порядке
print(s[::-1])      # 'gnimmargorP nohtyP'
```

### **Практические примеры с отрицательными срезами**

```python
# Проверка палиндрома
word = "radar"
if word == word[::-1]:
    print(f"{word} — палиндром")  # Выведет: radar — палиндром

# Удаление расширения файла
filename = "document.pdf"
name_without_ext = filename[:-4]  # Убираем последние 4 символа
print(name_without_ext)  # 'document'

# Получение последних N символов
text = "1234567890"
last_three = text[-3:]
print(last_three)  # '890'

# Извлечение кода страны из телефона
phone = "+1-555-1234"
country_code = phone[1:phone.index('-')]  # С индекса 1 до первого '-'
print(country_code)  # '1'

# Реверс каждого слова в предложении
sentence = "Hello World Python"
words = sentence.split()
reversed_words = [word[::-1] for word in words]
result = ' '.join(reversed_words)
print(result)  # 'olleH dlroW nohtyP'

# Получение домена верхнего уровня
url = "https://www.example.com"
tld = url[url.rfind('.') + 1:]  # После последней точки
print(tld)  # 'com'

# Удаление первого и последнего символа
quoted = "'Hello'"
unquoted = quoted[1:-1]
print(unquoted)  # 'Hello'

# Проверка, заканчивается ли строка на определённую подстроку
text = "example.txt"
if text[-4:] == ".txt":
    print("Это текстовый файл")  # Выведет: Это текстовый файл
```

### **Визуализация индексов для сложных срезов**

```python
s = "Python"
# Индексы:
#     P   y   t   h   o   n
#     0   1   2   3   4   5   (положительные)
#    -6  -5  -4  -3  -2  -1   (отрицательные)

# Примеры:
print(s[1:4])     # 'yth' (от 1 до 4, не включая 4)
print(s[-5:-2])   # 'yth' (то же самое через отрицательные)
print(s[::2])     # 'Pto' (каждый второй, шаг 2)
print(s[::-1])    # 'nohtyP' (реверс, шаг -1)
print(s[-1::-1])  # 'nohtyP' (от конца к началу)
print(s[:-4:-1])  # 'noh' (от конца до -4, не включая -4, справа налево)
```

**Ключевые моменты:**

- Отрицательные индексы удобны для работы с концом строки
- `[::-1]` — стандартный способ реверса строки
- При отрицательном шаге `start` должен быть правее `stop`
- Срезы никогда не вызывают `IndexError` — выходящие за границы индексы игнорируются
- Срезы создают **новую строку**, не изменяя оригинал (строки неизменяемы)

## `5.5` Конкатенация и другие математические операции  
## `5.6` (`*`) Форматирование:  
### `format()`  
Метод `format()` вставляет значения в строку по местам-заполнителям, указанным в фигурных скобках `{}`. Можно использовать позиционные или именованные аргументы, указывая внутри скобок номера или имена: 
```python
"Hello, {}!".format("Alice")  # Hello, Alice!
"{1}, {0}".format('first', 'second')  # second, first
"{name} is {age}".format(name="Bob", age=25)  # Bob is 25
```
Форматирование внутри фигурных скобок позволяет задавать выравнивание, ширину, точность и другие параметры:
```python
"{:>10}".format("cat")    # "       cat" (выравнивание по правому краю, ширина 10)
"{:.3}".format("caterpillar")  # "cat" (обрезка до 3 символов)
"{:0^9}".format(123)      # "000123000" (выравнивание с заполнением нулями)
```

### `f-строки` 
`F-строки` появились в Python 3.6 и позволяют вставлять выражения прямо в строку с префиксом f:
```python
name = "Alice"
age = 30
print(f"Hello, {name}! You are {age} years old.")  # Hello, Alice! You are 30 years old.
```
Также внутри фигурных скобок можно использовать форматирование:
```python
print(f"{123:0>9}")  # '000000123' (выравнивание по правому краю с заполнением нулями)
print(f"{123:.2f}")   # '123.00' (формат с двумя десятичными знаками)
```

## `5.7` (`**`) Как строки хранятся в памяти компьютера. Команды `ord()`, `chr()`  
## `5.8` (`**`) Кодировки

----

# `6` Циклы
## `6.1` For loop
### `6.1.1` Как написать for loop в `Python`?  
### `6.1.2` Функция `range`. `Range` с несколькими параметрами и отрицательным шагом генерации  
### `6.1.3` `_` в цикле for  
### `6.1.4` Концепция `флага` (сигнала)  

## `6.2` While loop
### `6.2.1` Как написать while loop в `Python`?  
### `6.2.2` Бесконечные циклы
### `6.2.3` (`*`) Операторы: `break`, `continue`, `else`. Кейсы применения
### **Оператор `break` — досрочный выход из цикла**

`break` прерывает цикл и переходит к коду после него. Полезен, когда нужно остановить цикл при выполнении условия.

```python
# Базовый пример
for i in range(10):
    if i == 5:
        break
    print(i)
# Выведет: 0 1 2 3 4

# Поиск элемента в списке
users = ["Alice", "Bob", "Charlie", "David"]
search = "Charlie"

for user in users:
    if user == search:
        print(f"Найден: {user}")
        break
# Выведет: Найден: Charlie

# Бесконечный цикл с break
while True:
    command = input("Введите команду (exit для выхода): ")
    if command == "exit":
        break
    print(f"Выполняю: {command}")
```

### **Оператор `continue` — пропуск текущей итерации**

`continue` пропускает оставшийся код в текущей итерации и переходит к следующей. Удобно для игнорирования определённых условий.

```python
# Базовый пример
for i in range(5):
    if i == 3:
        continue
    print(i)
# Выведет: 0 1 2 4

# Пропуск чётных чисел
for num in range(10):
    if num % 2 == 0:
        continue
    print(num)
# Выведет: 1 3 5 7 9

# Фильтрация данных
prices = [100, -50, 200, 0, 150]
for price in prices:
    if price <= 0:
        continue
    discount = price * 0.1
    print(f"Цена: {price}, скидка: {discount}")
# Выведет только положительные цены со скидками
```

### **Блок `else` с циклами — выполнение при нормальном завершении**

`else` после цикла выполняется, только если цикл завершился **без `break`**.

```python
# Базовый пример
for i in range(3):
    if i == 5:
        break
else:
    print("Цикл выполнен до конца")
# Выведет: Цикл выполнен до конца (break не сработал)

# Поиск с проверкой результата
numbers = [1, 3, 5, 7, 9]
target = 4

for num in numbers:
    if num == target:
        print(f"Число {target} найдено")
        break
else:
    print(f"Число {target} не найдено")
# Выведет: Число 4 не найдено

# Проверка простого числа
n = 17
for i in range(2, n):
    if n % i == 0:
        print(f"{n} не является простым числом")
        break
else:
    print(f"{n} — простое число")
# Выведет: 17 — простое число
```

**Кейсы применения:**

- **`break`:** поиск элемента (выход при первом совпадении), досрочный выход при ошибке, выход из бесконечных циклов
- **`continue`:** фильтрация данных (пропуск невалидных значений), уменьшение вложенности кода, пропуск ненужных итераций
- **`else` с циклом:** проверка результата поиска (найден/не найден), валидация данных, выполнение действий при полном прохождении цикла


## `6.3` Вложенные циклы
### `6.3.1` Что такое вложенные циклы?
### `6.3.2` (`*`) Как работают операторы `break`, `continue`, `else` во вложенных циклах
### **Оператор `break` во вложенных циклах**

`break` прерывает **только тот цикл, в котором он вызван**. Внешний цикл продолжает работать.

```python
# break прерывает только внутренний цикл
for i in range(3):
    print(f"Внешний цикл: i={i}")
    for j in range(3):
        if j == 1:
            break  # Выходит только из внутреннего цикла
        print(f"  Внутренний цикл: j={j}")
# Выведет:
# Внешний цикл: i=0
#   Внутренний цикл: j=0
# Внешний цикл: i=1
#   Внутренний цикл: j=0
# Внешний цикл: i=2
#   Внутренний цикл: j=0
```

**Выход из всех циклов сразу — использование флага:**

```python
# Флаг для выхода из всех циклов
found = False
for i in range(3):
    for j in range(3):
        if i == 1 and j == 1:
            found = True
            break  # Выход из внутреннего
    if found:
        break  # Выход из внешнего
    print(f"i={i} завершён")
# Выведет только: i=0 завершён
```

**Альтернатива — использование функции и return:**

```python
def find_in_matrix(matrix, target):
    for i, row in enumerate(matrix):
        for j, value in enumerate(row):
            if value == target:
                return (i, j)  # Выход из всех циклов сразу
    return None

matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
result = find_in_matrix(matrix, 5)
print(result)  # (1, 1)
```

### **Оператор `continue` во вложенных циклах**

`continue` действует **только на текущий цикл** — пропускает остаток текущей итерации и переходит к следующей.

```python
# continue во внутреннем цикле
for i in range(3):
    for j in range(3):
        if j == 1:
            continue  # Пропускает только j=1 во внутреннем цикле
        print(f"i={i}, j={j}")
# Выведет:
# i=0, j=0
# i=0, j=2
# i=1, j=0
# i=1, j=2
# i=2, j=0
# i=2, j=2

# continue во внешнем цикле
for i in range(3):
    if i == 1:
        continue  # Пропускает всю итерацию при i=1
    for j in range(2):
        print(f"i={i}, j={j}")
# Выведет:
# i=0, j=0
# i=0, j=1
# i=2, j=0
# i=2, j=1
```

### **Блок `else` во вложенных циклах**

`else` выполняется, только если цикл завершился **без `break`**. Каждый цикл имеет свой собственный `else`.

```python
# else для внутреннего цикла
for i in range(2):
    for j in range(3):
        if j == 5:  # Условие не выполнится
            break
    else:
        print(f"Внутренний цикл i={i} завершён без break")
# Выведет:
# Внутренний цикл i=0 завершён без break
# Внутренний цикл i=1 завершён без break

# break во внутреннем цикле отменяет его else
for i in range(2):
    for j in range(3):
        if j == 1:
            break  # else внутреннего цикла не выполнится
    else:
        print(f"Внутренний цикл i={i} завершён")
# Ничего не выведет (break сработал в обеих итерациях)

# Комбинация else для обоих циклов
for i in range(2):
    for j in range(2):
        print(f"i={i}, j={j}")
    else:
        print(f"  Внутренний цикл для i={i} завершён")
else:
    print("Внешний цикл завершён")
# Выведет:
# i=0, j=0
# i=0, j=1
#   Внутренний цикл для i=0 завершён
# i=1, j=0
# i=1, j=1
#   Внутренний цикл для i=1 завершён
# Внешний цикл завершён
```

**Практический пример — поиск в двумерном массиве:**

```python
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
target = 5
found = False

for i, row in enumerate(matrix):
    for j, value in enumerate(row):
        if value == target:
            print(f"Найдено {target} на позиции ({i}, {j})")
            found = True
            break
    if found:
        break
else:
    print(f"Значение {target} не найдено")
# Выведет: Найдено 5 на позиции (1, 1)
```

**Ключевые моменты:**

- `break` и `continue` влияют только на тот цикл, где они вызваны
- Для выхода из всех циклов используйте флаг или функцию с `return`
- `else` у каждого цикла работает независимо
- `else` не выполняется, если сработал `break` в соответствующем цикле

----

# `7` Типы данных 2 (Списки)
## `7.1` Что такое список? На что он похож в других языках (доп знание). Функция `list()`. Изменяемость списков.  
## `7.2` Функции `len()`, `in` для списков  
## `7.3` Индексы  
## `7.4` Slices. Посмотреть различные вариации  
## `7.5` Функции `sum()`, `min()`, `max()`  
## `7.6` Конкатенация и другие математические операции  
## `7.7` Методы списков (можно посмотреть все, но укажу, которые точно надо знать):  
- `append()`  
- `extend()`  
- оператор `del`  
- `remove()`  
- `pop()`  
- `reverse()`  
- `copy()`  
- `clear()`  
- `sort()`

## `7.8` Уметь перебирать списки через for  
## `7.9` (`*`) Распаковка списков

Распаковка списков позволяет одновременно присвоить элементы списка нескольким переменным. Это упрощает работу с данными и делает код более читаемым.

### **Базовая распаковка**

Количество переменных должно совпадать с количеством элементов.

```python
colors = ["red", "green", "blue"]
first, second, third = colors
print(first, second, third)  # red green blue

# С кортежами работает так же
point = (10, 20)
x, y = point
print(x, y)  # 10 20

# Ошибка при несовпадении количества
numbers = [1, 2, 3]
a, b = numbers  # ValueError: too many values to unpack
```

### **Распаковка с оператором `*` (звёздочка)**

Оператор `*` собирает несколько элементов в список.

```python
# Первый, последний и всё между ними
numbers = [1, 2, 3, 4, 5]
first, *middle, last = numbers
print(first)   # 1
print(middle)  # [2, 3, 4]
print(last)    # 5

# Только первый и остальные
head, *tail = numbers
print(head)  # 1
print(tail)  # [2, 3, 4, 5]

# Только последний и остальные
*init, last = numbers
print(init)  # [1, 2, 3, 4]
print(last)  # 5

# Игнорирование средних элементов
first, *_, last = numbers
print(first)  # 1
print(last)   # 5
# _ показывает, что средние элементы нас не интересуют
```

### **Распаковка при объединении списков**

```python
list1 = [1, 2]
list2 = [3, 4]
list3 = [5, 6]

# Объединение списков
merged = [*list1, *list2]
print(merged)  # [1, 2, 3, 4]

# Добавление элементов в начало и конец
extended = [0, *list1, *list2, 7]
print(extended)  # [0, 1, 2, 3, 4, 7]

# Объединение нескольких списков
all_lists = [*list1, *list2, *list3]
print(all_lists)  # [1, 2, 3, 4, 5, 6]
```

### **Распаковка в функциях**

```python
# Передача элементов списка как аргументов
def calculate(a, b, c):
    return a + b + c

values = [10, 20, 30]
result = calculate(*values)  # Эквивалентно calculate(10, 20, 30)
print(result)  # 60

# Создание копии списка
original = [1, 2, 3]
copy = [*original]
print(copy)  # [1, 2, 3]
print(copy is original)  # False (это другой объект)
```

### **Практические примеры**

```python
# Обмен значений без временной переменной
a, b = 10, 20
a, b = b, a
print(a, b)  # 20 10

# Работа с файлами CSV
data = "Иван,Петров,30"
first_name, last_name, age = data.split(',')
print(first_name)  # Иван
print(age)         # 30

# Распаковка вложенных структур
users = [("Alice", 25), ("Bob", 30), ("Charlie", 35)]
for name, age in users:
    print(f"{name} — {age} лет")
# Выведет:
# Alice — 25 лет
# Bob — 30 лет
# Charlie — 35 лет

# Пропуск ненужных значений
coordinates = (10, 20, 30, 40)
x, y, *_ = coordinates
print(x, y)  # 10 20
```


## `7.10` (*) Методы `split()`, `join()`
Эти методы используются для преобразования строк в списки и обратно.

### **Метод `split()` — разбиение строки на список**
Разбивает строку на подстроки по разделителю. Без аргумента разбивает по пробелам.

```python
# Разбиение по запятой
text = "яблоко,банан,апельсин"
fruits = text.split(',')
print(fruits)  # ['яблоко', 'банан', 'апельсин']

# Разбиение по точке с запятой
text = "раз,два;три.четыре"
parts = text.split(';')
print(parts)  # ['раз,два', 'три.четыре']

# Разбиение по пробелам (по умолчанию)
text = "один два три"
words = text.split()
print(words)  # ['один', 'два', 'три']

# Несколько пробелов обрабатываются как один
text = "один    два     три"
words = text.split()
print(words)  # ['один', 'два', 'три']

# Ограничение количества разбиений
text = "a,b,c,d,e"
result = text.split(',', 2)  # Разбить максимум 2 раза
print(result)  # ['a', 'b', 'c,d,e']
```

### **Метод `join()` — объединение списка в строку**

Объединяет элементы списка в строку, вставляя между ними разделитель.

```python
# Объединение через запятую и пробел
words = ['яблоко', 'банан', 'апельсин']
result = ", ".join(words)
print(result)  # "яблоко, банан, апельсин"

# Объединение через дефис
chars = list("Python")
result = "-".join(chars)
print(result)  # "P-y-t-h-o-n"

# Объединение с переносом строки
lines = ['строка 1', 'строка 2', 'строка 3']
text = "\n".join(lines)
print(text)
# Выведет:
# строка 1
# строка 2
# строка 3

# Объединение без разделителя
letters = ['H', 'e', 'l', 'l', 'o']
word = "".join(letters)
print(word)  # "Hello"
```

### **Практические комбинации `split()` и `join()`**

```python
# Очистка строки от лишних пробелов
text = "  много    пробелов   здесь  "
cleaned = " ".join(text.split())
print(cleaned)  # "много пробелов здесь"

# Замена разделителя
csv_data = "яблоко,банан,апельсин"
tsv_data = "\t".join(csv_data.split(','))
print(tsv_data)  # "яблоко	банан	апельсин"

# Работа с путями файлов
path_parts = ['home', 'user', 'documents', 'file.txt']
path = "/".join(path_parts)
print(path)  # "home/user/documents/file.txt"

# Парсинг CSV-подобных данных
data = "Иван,Петров,30,Москва"
fields = data.split(',')
name, surname, age, city = fields
print(f"{name} {surname}, {age} лет, {city}")
# Выведет: Иван Петров, 30 лет, Москва

# Создание строки из чисел
numbers = [1, 2, 3, 4, 5]
# join работает только со строками!
result = ", ".join(str(n) for n in numbers)
print(result)  # "1, 2, 3, 4, 5"

# Разбиение по нескольким разделителям (через replace)
text = "один,два;три.четыре"
normalized = text.replace(',', ' ').replace(';', ' ').replace('.', ' ')
words = normalized.split()
print(words)  # ['один', 'два', 'три', 'четыре']
```

### **Важные моменты**

```python
# split() возвращает список строк
text = "1,2,3"
numbers = text.split(',')
print(type(numbers[0]))  # <class 'str'> (не int!)

# join() работает только со строками
numbers = [1, 2, 3]
# result = ",".join(numbers)  # TypeError!
result = ",".join(map(str, numbers))  # Правильно
print(result)  # "1,2,3"

# Пустая строка между разделителями
text = "a,,b"
parts = text.split(',')
print(parts)  # ['a', '', 'b'] (пустая строка сохраняется)

# Разделитель не удаляется полностью
text = "a,b,c,"
parts = text.split(',')
print(parts)  # ['a', 'b', 'c', ''] (последний элемент пустой)
```

**Кейсы применения:**

- **`split()`:** парсинг CSV/TSV, разбиение строк по словам, обработка пользовательского ввода, работа с путями
- **`join()`:** формирование строк из списков, создание CSV, объединение строк с разделителем, форматирование вывода


## `7.11` (*) Списочные выражения (list comprehensions)
`List comprehension` — это компактный и читаемый способ создания списков на основе существующих итерируемых объектов. Позволяет заменить циклы `for` одной строкой кода.

### **Базовый синтаксис**

```python
# Общая структура: [выражение for элемент in итерируемый_объект]

# Простое создание списка
nums = [n for n in range(1, 6)]
print(nums)  # [1, 2, 3, 4, 5]

# Эквивалент через обычный цикл:
nums = []
for n in range(1, 6):
    nums.append(n)
```

### **Преобразование элементов**

```python
# Возведение в квадрат
nums = [1, 2, 3, 4, 5]
squares = [n * n for n in nums]
print(squares)  # [1, 4, 9, 16, 25]

# Преобразование в строки
numbers = [1, 2, 3]
strings = [str(n) for n in numbers]
print(strings)  # ['1', '2', '3']

# Применение методов
words = ["hello", "world", "python"]
uppercase = [word.upper() for word in words]
print(uppercase)  # ['HELLO', 'WORLD', 'PYTHON']

# Вычисления с несколькими операциями
prices = [100, 200, 300]
with_tax = [price * 1.2 for price in prices]
print(with_tax)  # [120.0, 240.0, 360.0]
```

### **Фильтрация с условием `if`**

```python
# Только нечётные числа
nums = [1, 2, 3, 4, 5, 6, 7, 8, 9]
odd = [n for n in nums if n % 2 == 1]
print(odd)  # [1, 3, 5, 7, 9]

# Квадраты только нечётных чисел
odd_squares = [n * n for n in nums if n % 2 == 1]
print(odd_squares)  # [1, 9, 25, 49, 81]

# Фильтрация строк
words = ["apple", "banana", "kiwi", "strawberry"]
short_words = [w for w in words if len(w) <= 5]
print(short_words)  # ['apple', 'kiwi']

# Несколько условий
numbers = range(1, 21)
result = [n for n in numbers if n % 2 == 0 if n > 10]
print(result)  # [12, 14, 16, 18, 20]
```

### **Условное выражение `if-else`**

```python
# Разная логика для чётных и нечётных
result = ["чётное" if x % 2 == 0 else "нечётное" for x in range(5)]
print(result)  # ['чётное', 'нечётное', 'чётное', 'нечётное', 'чётное']

# Преобразование значений
numbers = [1, -2, 3, -4, 5]
absolute = [n if n >= 0 else -n for n in numbers]
print(absolute)  # [1, 2, 3, 4, 5]

# Замена None
values = [10, None, 20, None, 30]
cleaned = [v if v is not None else 0 for v in values]
print(cleaned)  # [10, 0, 20, 0, 30]
```

### **Вложенные циклы**

```python
# Создание всех пар
pairs = [(x, y) for x in [1, 2, 3] for y in ['a', 'b']]
print(pairs)  # [(1, 'a'), (1, 'b'), (2, 'a'), (2, 'b'), (3, 'a'), (3, 'b')]

# Матрица (список списков)
matrix = [[x for x in range(1, 4)] for y in range(3)]
print(matrix)  # [[1, 2, 3], [1, 2, 3], [1, 2, 3]]

# Таблица умножения
table = [[i * j for j in range(1, 4)] for i in range(1, 4)]
print(table)  # [[1, 2, 3], [2, 4, 6], [3, 6, 9]]

# Развёртывание вложенного списка (flatten)
nested = [[1, 2], [3, 4], [5, 6]]
flat = [item for sublist in nested for item in sublist]
print(flat)  # [1, 2, 3, 4, 5, 6]

# С условием во вложенном цикле
result = [(x, y) for x in range(3) for y in range(3) if x != y]
print(result)  # [(0, 1), (0, 2), (1, 0), (1, 2), (2, 0), (2, 1)]
```

### **Практические примеры**

```python
# Извлечение значений из словарей
users = [
    {"name": "Alice", "age": 25},
    {"name": "Bob", "age": 30},
    {"name": "Charlie", "age": 35}
]
names = [user["name"] for user in users]
print(names)  # ['Alice', 'Bob', 'Charlie']

# Фильтрация и преобразование
adults = [user["name"] for user in users if user["age"] >= 30]
print(adults)  # ['Bob', 'Charlie']

# Обработка файла (построчно)
lines = ["  line 1  ", "line 2", "  line 3  "]
cleaned = [line.strip() for line in lines if line.strip()]
print(cleaned)  # ['line 1', 'line 2', 'line 3']

# Создание множества уникальных значений
numbers = [1, 2, 2, 3, 3, 3, 4]
unique = list({n for n in numbers})  # Set comprehension
print(unique)  # [1, 2, 3, 4]
```

### **Сравнение с обычным циклом**

```python
# List comprehension (одна строка)
squares = [x**2 for x in range(10) if x % 2 == 0]

# Эквивалент через цикл (4 строки)
squares = []
for x in range(10):
    if x % 2 == 0:
        squares.append(x**2)

print(squares)  # [0, 4, 16, 36, 64]
```

**Когда использовать:**
- Простые преобразования и фильтрация данных
- Создание новых списков на основе существующих
- Когда логика помещается в одну строку и остаётся читаемой

**Когда НЕ использовать:**
- Сложная логика, которую трудно читать в одну строку
- Когда нужны побочные эффекты (лучше использовать обычный цикл)
- Глубоко вложенные comprehensions (более 2 уровней)

## `7.12` Вложенные списки. Матрицы  
## `7.13` (*) Сортировка: `sorted()` и параметр `key`

Функция `sorted()` создаёт **новый** отсортированный список из любого итерируемого объекта, не изменяя оригинал. Параметр `key` позволяет задать критерий сортировки.

### **Базовая сортировка**

```python
# Числа по возрастанию (по умолчанию)
numbers = [5, 2, 8, 1, 9]
result = sorted(numbers)
print(result)  # [1, 2, 5, 8, 9]
print(numbers)  # [5, 2, 8, 1, 9] (оригинал не изменился)

# Строки по алфавиту
words = ["banana", "apple", "cherry"]
result = sorted(words)
print(result)  # ['apple', 'banana', 'cherry']

# В обратном порядке
result = sorted(numbers, reverse=True)
print(result)  # [9, 8, 5, 2, 1]

# Сортировка строки (возвращает список символов)
text = "python"
result = sorted(text)
print(result)  # ['h', 'n', 'o', 'p', 't', 'y']
print(''.join(sorted(text)))  # 'hnopty'
```

### **Параметр `key` — функция для вычисления критерия**

`key` принимает функцию, которая применяется к каждому элементу для определения значения сортировки.

```python
# Сортировка строк по длине
words = ["apple", "pie", "banana", "kiwi"]
result = sorted(words, key=len)
print(result)  # ['pie', 'kiwi', 'apple', 'banana']

# Сортировка без учёта регистра
words = ["Banana", "apple", "Cherry", "date"]
result = sorted(words, key=str.lower)
print(result)  # ['apple', 'Banana', 'Cherry', 'date']

# Сортировка чисел по абсолютному значению
numbers = [-5, 2, -8, 1, 9, -3]
result = sorted(numbers, key=abs)
print(result)  # [1, 2, -3, -5, -8, 9]

# Сортировка по последнему символу
words = ["hello", "world", "python", "code"]
result = sorted(words, key=lambda x: x[-1])
print(result)  # ['code', 'hello', 'python', 'world']
```

### **Сортировка кортежей и списков**

```python
# По умолчанию — по первому элементу
pairs = [(3, 'three'), (1, 'one'), (2, 'two')]
result = sorted(pairs)
print(result)  # [(1, 'one'), (2, 'two'), (3, 'three')]

# По второму элементу
result = sorted(pairs, key=lambda x: x[1])
print(result)  # [(1, 'one'), (3, 'three'), (2, 'two')]

# Сортировка по нескольким критериям (кортеж в key)
students = [
    ('Alice', 85, 20),
    ('Bob', 92, 19),
    ('Charlie', 85, 21),
    ('David', 92, 18)
]
# Сначала по оценке (убывание), потом по возрасту (возрастание)
result = sorted(students, key=lambda x: (-x[1], x[2]))
print(result)
# [('David', 92, 18), ('Bob', 92, 19), ('Alice', 85, 20), ('Charlie', 85, 21)]
```

### **Сортировка объектов**

```python
class Student:
    def __init__(self, name, grade, age):
        self.name = name
        self.grade = grade
        self.age = age
    
    def __repr__(self):
        return f"Student({self.name}, {self.grade}, {self.age})"

students = [
    Student('Alice', 85, 20),
    Student('Bob', 92, 19),
    Student('Charlie', 78, 21)
]

# По оценке
by_grade = sorted(students, key=lambda s: s.grade)
print(by_grade)
# [Student(Charlie, 78, 21), Student(Alice, 85, 20), Student(Bob, 92, 19)]

# По имени
by_name = sorted(students, key=lambda s: s.name)
print(by_name)
# [Student(Alice, 85, 20), Student(Bob, 92, 19), Student(Charlie, 78, 21)]

# По оценке (убывание), затем по имени (возрастание)
result = sorted(students, key=lambda s: (-s.grade, s.name))
print(result)
# [Student(Bob, 92, 19), Student(Alice, 85, 20), Student(Charlie, 78, 21)]
```

### **Сложные случаи сортировки**

```python
# Сортировка словаря по значениям
scores = {'Alice': 85, 'Bob': 92, 'Charlie': 78}
sorted_items = sorted(scores.items(), key=lambda x: x[1], reverse=True)
print(sorted_items)  # [('Bob', 92), ('Alice', 85), ('Charlie', 78)]

# Преобразование обратно в словарь (с Python 3.7+ порядок сохраняется)
sorted_dict = dict(sorted_items)
print(sorted_dict)  # {'Bob': 92, 'Alice': 85, 'Charlie': 78}

# Сортировка строк по количеству гласных
def count_vowels(word):
    return sum(1 for char in word.lower() if char in 'aeiou')

words = ["hello", "world", "python", "code"]
result = sorted(words, key=count_vowels)
print(result)  # ['world', 'python', 'code', 'hello']

# Естественная сортировка (числа в строках)
import re

def natural_key(text):
    return [int(c) if c.isdigit() else c.lower() for c in re.split('(\d+)', text)]

files = ['file1.txt', 'file10.txt', 'file2.txt', 'file20.txt']
result = sorted(files, key=natural_key)
print(result)  # ['file1.txt', 'file2.txt', 'file10.txt', 'file20.txt']
```

### **`sorted()` vs `list.sort()`**

```python
# sorted() — создаёт новый список
numbers = [3, 1, 2]
new_list = sorted(numbers)
print(numbers)   # [3, 1, 2] (не изменился)
print(new_list)  # [1, 2, 3]

# list.sort() — изменяет на месте, возвращает None
numbers = [3, 1, 2]
result = numbers.sort()
print(numbers)  # [1, 2, 3] (изменился)
print(result)   # None

# sort() также поддерживает key и reverse
numbers = [3, 1, 2]
numbers.sort(reverse=True)
print(numbers)  # [3, 2, 1]
```

### **Стабильная сортировка**

Python использует **стабильную** сортировку — элементы с одинаковыми ключами сохраняют исходный порядок.

```python
students = [
    ('Alice', 85),
    ('Bob', 85),
    ('Charlie', 85)
]
# Все имеют одинаковую оценку
result = sorted(students, key=lambda x: x[1])
print(result)
# [('Alice', 85), ('Bob', 85), ('Charlie', 85)]
# Порядок сохранился, как в исходном списке
```

**Когда использовать:**
- `sorted()` — когда нужен новый список или сортировка любого итерируемого объекта
- `list.sort()` — когда нужно отсортировать существующий список и сэкономить память
- `key` — для любой нестандартной сортировки (по атрибутам, длине, сложным критериям)
- `reverse=True` — для обратного порядка

----

# `8` Функции 1
## `8.1` Что такое функциональное программирование?  
## `8.2` Что такое функция? Как объявить функцию в Python?  
## `8.3` Функции с и без параметров  
## `8.4` Разница аргумента и параметра  
## `8.5` Разные виды `return`  

----

# `9` Типы данных 3
## `9.1` Кортежи
### `9.1.1` Что такое кортежи?  
### `9.1.2` В чем их плюсы и минусы? Их свойства. Отличие от списков  
### `9.1.3` Функции `len()`, `in` для кортежей и другие по типу `sum()`  
### `9.1.4` Методы кортежей:  
- `index()`  
- `count()`  
- `join()`
### `9.1.5` Распаковка кортежей  

## `9.2` Множества
### `9.2.1` Что такое множества? Свойства множеств  
### `9.2.2` Функции `len()`, `in` для множеств и другие по типу `sum()`  
### `9.2.3` Методы множеств (можно посмотреть все, но укажу, который точно надо знать):  
- `add()`  
- `remove()`  
- `discard()`  
- `pop()`  
- `clear()`  
- методы и операторы для операций между множествами  
- `issubset()`  
- `issuperset()`

### `9.2.3` (`*`) Генераторы множеств (`set comprehensions`)

`Set comprehension` — это компактный способ создания множества на основе итерируемого объекта с фильтрацией и преобразованием элементов. Синтаксис похож на list comprehension, но используются **фигурные скобки** `{}`.

### **Синтаксис**

```python
{expression for item in iterable if condition}
```

### **Базовые примеры**

```python
# Создание множества из квадратов чисел
numbers = [1, 2, 3, 4, 5]
squares = {x**2 for x in numbers}
print(squares)  # {1, 4, 9, 16, 25}

# Автоматическое удаление дубликатов
numbers = [1, 2, 2, 3, 3, 3, 4]
unique = {x for x in numbers}
print(unique)  # {1, 2, 3, 4}

# Преобразование в верхний регистр
words = ["hello", "world", "python", "hello"]
uppercase = {word.upper() for word in words}
print(uppercase)  # {'HELLO', 'WORLD', 'PYTHON'}
```

### **Фильтрация с условием**

```python
# Только чётные числа
numbers = [13, 21, 14, 24, 53, 62]
even_numbers = {num for num in numbers if num % 2 == 0}
print(even_numbers)  # {24, 62, 14} (порядок может отличаться)

# Только длинные слова
words = ["cat", "elephant", "dog", "giraffe", "ant"]
long_words = {word for word in words if len(word) > 3}
print(long_words)  # {'elephant', 'giraffe'}

# Положительные числа из смешанного списка
numbers = [-5, 3, -2, 8, 0, -1, 7]
positive = {n for n in numbers if n > 0}
print(positive)  # {8, 3, 7}
```

### **Преобразование элементов**

```python
# Длины уникальных слов
words = ["hello", "world", "hi", "python"]
lengths = {len(word) for word in words}
print(lengths)  # {2, 5, 6}

# Первые буквы слов
sentence = "the quick brown fox jumps over the lazy dog"
first_letters = {word[0] for word in sentence.split()}
print(first_letters)  # {'b', 'd', 'f', 'j', 'l', 'o', 'q', 't'}

# Абсолютные значения
numbers = [-5, 3, -3, 5, -7, 7]
absolutes = {abs(n) for n in numbers}
print(absolutes)  # {3, 5, 7}
```

### **Извлечение уникальных значений из сложных структур**

```python
# Уникальные возрасты из списка словарей
users = [
    {"name": "Alice", "age": 25},
    {"name": "Bob", "age": 30},
    {"name": "Charlie", "age": 25},
    {"name": "David", "age": 35}
]
ages = {user["age"] for user in users}
print(ages)  # {25, 30, 35}

# Уникальные расширения файлов
files = ["doc.txt", "image.png", "script.py", "data.txt", "photo.png"]
extensions = {file.split('.')[-1] for file in files}
print(extensions)  # {'txt', 'png', 'py'}

# Уникальные символы в строке
text = "hello world"
chars = {char for char in text if char != ' '}
print(chars)  # {'h', 'e', 'l', 'o', 'w', 'r', 'd'}
```

### **Вложенные циклы в set comprehension**

```python
# Уникальные произведения пар чисел
numbers1 = [2, 3]
numbers2 = [4, 5]
products = {x * y for x in numbers1 for y in numbers2}
print(products)  # {8, 10, 12, 15}

# Уникальные координаты сетки (без дубликатов)
grid = {(x, y) for x in range(3) for y in range(3) if x != y}
print(grid)  # {(0, 1), (0, 2), (1, 0), (1, 2), (2, 0), (2, 1)}
```

### **Практические примеры**

```python
# Поиск уникальных слов в тексте (без учёта регистра)
text = "Hello world hello Python python World"
unique_words = {word.lower() for word in text.split()}
print(unique_words)  # {'hello', 'world', 'python'}

# Извлечение доменов из списка email'ов
emails = ["user1@gmail.com", "user2@yahoo.com", "user3@gmail.com"]
domains = {email.split('@')[1] for email in emails}
print(domains)  # {'gmail.com', 'yahoo.com'}

# Уникальные цифры в числе
number = 1122334455
digits = {int(d) for d in str(number)}
print(digits)  # {1, 2, 3, 4, 5}

# Фильтрация валидных email (простая проверка)
emails = ["user@example.com", "invalid", "test@test.org", "bad@"]
valid = {email for email in emails if '@' in email and '.' in email.split('@')[-1]}
print(valid)  # {'user@example.com', 'test@test.org'}
```

### **Сравнение с list comprehension**

```python
numbers = [1, 2, 2, 3, 3, 3]

# List comprehension — сохраняет дубликаты
list_result = [x for x in numbers]
print(list_result)  # [1, 2, 2, 3, 3, 3]

# Set comprehension — удаляет дубликаты
set_result = {x for x in numbers}
print(set_result)  # {1, 2, 3}

# Преобразование set обратно в list
unique_list = list(set_result)
print(unique_list)  # [1, 2, 3] (или другой порядок)
```

**Когда использовать:**
- Нужны только уникальные элементы
- Порядок элементов не важен
- Требуется быстрая проверка принадлежности элемента
- Извлечение уникальных значений из данных

**Особенности:**
- Автоматически удаляет дубликаты
- Элементы неупорядочены (порядок не гарантируется)
- Элементы должны быть хешируемыми (нельзя добавить списки или словари)
- Быстрее list comprehension для проверки наличия элемента

### `9.2.4` (`**`) `frozenset`
`frozenset` — это неизменяемый (immutable) аналог множества (`set`). Как и множество, он хранит уникальные элементы, но после создания его нельзя изменить (добавлять или удалять элементы).

Основные особенности:
- Можно использовать как ключи в словарях или элементы других множеств (т.к. хешируем).
- Создаётся из итерируемого объекта: `frozenset(iterable)`.

```python
s = frozenset([1, 2, 2, 3])
print(s)  # frozenset({1, 2, 3})

# Попытка изменить вызовет ошибку:
# s.add(4)  # AttributeError: 'frozenset' object has no attribute 'add'
```


### **frozenset как элемент множества**

```python
# Множество множеств (только с frozenset)
set_of_sets = {
    frozenset([1, 2]),
    frozenset([3, 4]),
    frozenset([1, 2])  # Дубликат, будет удалён
}
print(set_of_sets)  # {frozenset({1, 2}), frozenset({3, 4})}

# Нельзя добавить обычный set
# set_of_sets.add({5, 6})  # TypeError: unhashable type: 'set'
```

### **Практические примеры**

```python
# Хранение неизменяемых групп пользователей
user_groups = {
    'alice': frozenset(['admin', 'editor']),
    'bob': frozenset(['viewer']),
    'charlie': frozenset(['admin', 'viewer', 'editor'])
}

# Проверка прав доступа
if 'admin' in user_groups['alice']:
    print("Alice имеет права администратора")  # Выведет

# Поиск пользователей с определёнными правами
admin_users = [user for user, groups in user_groups.items() if 'admin' in groups]
print(admin_users)  # ['alice', 'charlie']

# Граф связей (неизменяемые рёбра)
graph = {
    frozenset(['A', 'B']): 5,  # Ребро A-B с весом 5
    frozenset(['B', 'C']): 3,
    frozenset(['A', 'C']): 7
}

# Поиск веса ребра
edge = frozenset(['A', 'B'])
print(graph[edge])  # 5

# Кеширование результатов для наборов параметров
cache = {}

def calculate(params):
    frozen_params = frozenset(params.items())
    if frozen_params not in cache:
        # Сложные вычисления
        result = sum(params.values()) * 2
        cache[frozen_params] = result
    return cache[frozen_params]

print(calculate({'a': 1, 'b': 2}))  # 6
print(calculate({'a': 1, 'b': 2}))  # 6 (из кеша)
```

### **Преобразование между set и frozenset**

```python
# set → frozenset
s = {1, 2, 3}
fs = frozenset(s)
print(fs)  # frozenset({1, 2, 3})

# frozenset → set
fs = frozenset([4, 5, 6])
s = set(fs)
s.add(7)
print(s)  # {4, 5, 6, 7}

# frozenset остался неизменным
print(fs)  # frozenset({4, 5, 6})
```

**Когда использовать frozenset:**
- Нужно неизменяемое множество (для гарантии целостности данных)
- Множество должно быть ключом словаря
- Множество должно быть элементом другого множества
- Требуется хешируемая коллекция уникальных элементов
- Передача данных, которые нельзя случайно изменить

**Ключевые особенности:**
- Неизменяемый (immutable) — нельзя добавлять/удалять элементы
- Хешируемый (hashable) — можно использовать как ключ или в множестве
- Поддерживает все операции чтения множеств
- Создаётся один раз и не меняется
- Немного быстрее обычного `set` в некоторых операциях из-за неизменяемости

[Видео про frozenset](https://www.youtube.com/watch?v=YatGF3voZH8)


## `9.3` Словари
### `9.3.1` (`*`) Что такое словари? Свойства словарей 
[Видео про dict](https://youtu.be/MZZSMaEAC2g?si=YvGzIOcgZDZGICoG)

Словарь (`dict`) — это изменяемая коллекция, которая хранит данные в виде пар **ключ-значение**. Каждому уникальному ключу соответствует одно значение.

```python
# Создание словаря
person = {
    'name': 'Alice',
    'age': 30,
    'city': 'Moscow'
}

# Доступ к значению по ключу
print(person['name'])  # 'Alice'

# Добавление/изменение элемента
person['email'] = 'alice@example.com'  # Добавление
person['age'] = 31                      # Изменение

print(person)
# {'name': 'Alice', 'age': 31, 'city': 'Moscow', 'email': 'alice@example.com'}
```

**Основные свойства словарей:**

1. **Неупорядоченность** (до Python 3.7) / **Сохранение порядка вставки** (с Python 3.7+)
2. **Ключи уникальны** — дублирующиеся ключи перезаписываются
3. **Ключи должны быть неизменяемыми** (hashable) — строки, числа, кортежи
4. **Значения могут быть любыми** — включая другие словари, списки, объекты
5. **Быстрый доступ по ключу — O(1)** — не нужно перебирать элементы!

```python
# Ключи уникальны — дубликат перезаписывается
data = {'a': 1, 'b': 2, 'a': 3}
print(data)  # {'a': 3, 'b': 2}

# Значения могут повторяться
scores = {'Alice': 100, 'Bob': 85, 'Charlie': 100}
print(scores)  # {'Alice': 100, 'Bob': 85, 'Charlie': 100}

# Значения могут быть любого типа
mixed = {
    'name': 'Alice',
    'scores': [85, 90, 95],
    'active': True,
    'address': {'city': 'Moscow', 'street': 'Main St'}
}
```

**Главное преимущество — мгновенный поиск по ключу:**

```python
# Список — нужно перебирать все элементы (медленно для больших данных)
users_list = [
    ('alice', 'Alice'),
    ('bob', 'Bob'),
    ('charlie', 'Charlie')
    # ... 10000 элементов
]
# Чтобы найти пользователя, нужно перебрать весь список
for username, name in users_list:
    if username == 'charlie':
        print(name)  # Долго!

# Словарь — мгновенный доступ по ключу (быстро!)
users_dict = {
    'alice': 'Alice',
    'bob': 'Bob',
    'charlie': 'Charlie'
    # ... 10000 элементов
}
# Прямой доступ без перебора
print(users_dict['charlie'])  # Мгновенно!
```

### `9.3.2` Что может быть ключом словаря, а что нет?  
### `9.3.3` Функции `len()`, `in` для словарей и другие по типу `sum()`  
### `9.3.4` Методы словарей (можно посмотреть все, но укажу, который точно надо знать):  
- получение элемента из словаря  
- удаление элемента из словаря
- `keys()`  
- `values()`  
- `items()`  
- `get()`  
- `update()`  
- `setdefault()`  
- `pop()`  
- `clear()`  
- `copy()`

### `9.3.5` Уметь перебирать словари через for  
### `9.3.6` Вложенные словари  
### `9.3.7` (`*`) Генераторы словарей или `dict comprehensions`
Dict comprehension — это компактный способ создания словаря на основе итерируемого объекта с возможностью преобразования и фильтрации.

**Синтаксис:**
```python
{ключ: значение for элемент in итерируемый_объект if условие}
```

**Пример 1: Создание словаря из списка**

```python
# Создать словарь: число → квадрат числа
numbers = [1, 2, 3, 4, 5]
squares = {num: num**2 for num in numbers}
print(squares)  # {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

# С фильтрацией — только чётные числа
even_squares = {num: num**2 for num in numbers if num % 2 == 0}
print(even_squares)  # {2: 4, 4: 16}
```

**Пример 2: Преобразование данных**

```python
# Список имён → словарь: имя → длина имени
names = ['Alice', 'Bob', 'Charlie']
name_lengths = {name: len(name) for name in names}
print(name_lengths)  # {'Alice': 5, 'Bob': 3, 'Charlie': 7}

# Инвертирование словаря (ключи ↔ значения)
original = {'a': 1, 'b': 2, 'c': 3}
inverted = {value: key for key, value in original.items()}
print(inverted)  # {1: 'a', 2: 'b', 3: 'c'}
```

Dict comprehension создаёт словарь за одну строку, избегая циклов и временных переменных.

### `9.3.8` (`*`) Что такое коллекции и последовательности?
### **Коллекции (Collections)**

Коллекции — это структуры данных для хранения групп объектов. В Python основные типы коллекций: списки (`list`), кортежи (`tuple`), множества (`set`), словари (`dict`).

```python
# Основные коллекции
fruits_list = ['apple', 'banana', 'cherry']      # Список
coordinates = (10, 20, 30)                       # Кортеж
unique_numbers = {1, 2, 3, 4, 5}                # Множество
person = {'name': 'Alice', 'age': 30}           # Словарь

# Общие операции для всех коллекций
print(len(fruits_list))          # 3 (длина)
print('apple' in fruits_list)    # True (проверка вхождения)
for item in fruits_list:         # Итерация
    print(item)
```

### **Последовательности (Sequences)**

Последовательности — это **упорядоченные** коллекции, где элементы имеют позицию (индекс) и доступны по этой позиции. К ним относятся: списки, кортежи, строки, range.

```python
# Последовательности поддерживают индексацию и срезы
numbers = [10, 20, 30, 40, 50]   # Список — последовательность
text = "Python"                   # Строка — последовательность

# Индексация
print(numbers[0])      # 10 (первый элемент)
print(text[-1])        # 'n' (последний элемент)

# Срезы
print(numbers[1:4])    # [20, 30, 40]
print(text[:3])        # 'Pyt'

# НЕ последовательности — нет индексов
unique_set = {10, 20, 30}        # Множество
# print(unique_set[0])           # TypeError! У множества нет индексов

person_dict = {'name': 'Bob'}    # Словарь
# print(person_dict[0])          # KeyError! У словаря доступ по ключу, не по индексу
```

**Главное отличие:**

- **Последовательности** = коллекции с **порядком** и **индексами** (список, кортеж, строка)
- **Остальные коллекции** = нет гарантированного порядка или доступа по индексу (множество, словарь)

```python
# Порядок важен в последовательностях
list1 = [1, 2, 3]
list2 = [3, 2, 1]
print(list1 == list2)  # False (разный порядок)

# Порядок не важен в множествах
set1 = {1, 2, 3}
set2 = {3, 2, 1}
print(set1 == set2)    # True (важны только элементы)
```

**Все коллекции в Python итерируемы** (их можно перебрать в цикле), но только последовательности поддерживают индексацию и срезы.

----

# `10` Управление памятью
## `10.1` Устройство памяти в общем  
## `10.2` Устройства памяти в Python  
## `10.3` Переменные в Python. Как работают ссылки в Python  
## `10.4` Изменяемые и неизменяемые типы данных  
## `10.5` `copy()` & `deepcopy()`  
## `10.6` Garbage collector. Слабые и сильные ссылки  

----

# `11` Функции 2
## `11.1` Встроенные функции `type()`, `sorted()`, `reversed()`, `isinstance()`, `callable()`, `hasattr()`, `hash()` и другие  
## `11.2` Позиционные и именованные аргументы  
## `11.3` Аргументы по умолчанию  
## `11.4` Функции высшего порядка  
## `11.5` `lambda` функции  
## `11.6` `map()`, `filter()`, `reduce()`. Кейсы их применения  
## `11.7` `any()`, `all()`, `zip()`, `enumerate()`  

----

# `12` Работа с файлами
### `12.0.1` Потоковый ввод и вывод данных  

## `12.1` TXT
### `12.1.1` Что такое контекстный менеджер?  
### `12.1.2` Как читать и записывать в файл?  
### `12.1.3` Какие есть функции и методы для работы с TXT в Python?  

## `12.2` JSON
### `12.2.1` Что такое JSON? Для чего он нужен?  
### `12.2.2` Какие есть функции и методы для работы с JSON в Python?  
### `12.2.3` Как происходит конвертация типов данных при сериализации?  

## `12.3` CSV
### `12.3.1` Что такое CSV? Для чего он нужен?  
### `12.3.2` Какие есть функции и методы для работы с CSV в Python?  

----

# `13` Работа с датой и временем
## `13.1` Посмотреть модуль `datetime` и различные типы данных в нем: `date`, `time`, etc.  
## `13.2` На дате можно изучить `repr()` и посмотреть разницу с `str()`  
## `13.3` `strftime()`, `strptime()`, `isoformat()`, `fromisoformat()`, `combine()`, `now()`  
## `13.4` Что такое начало эпохи?  
## `13.5` Что такое `timedelta` и зачем оно нужно?  
## `13.6` Посмотреть, что такое временные зоны и как с ними работать  

----

# `14` Обработка исключений
## `14.1` Типы ошибок. Основные исключения в Python и их иерархия  
## `14.2` `try-except`  
## `14.3` `else` & `finally` в `try-except`  
## `14.4` Оператор `raise`  
## `14.5` Кастомные ошибки  

----

# `15` Рекурсия
## `15.1` Что такое рекурсия?  
## `15.2` Какие задачи решает рекурсия?  

----

# `16` Функции 3
## `16.1` Вложенные функции
## `16.2` (`*`) Замыкание. Зачем оно нужно?
**Замыкание** (closure) — это функция, которая определена внутри другой функции и хранит «замкнутые» значения переменных из внешней области видимости, даже после завершения работы внешней функции. То есть она "запоминает" своё окружение и может использовать переменные внешней функции, когда уже вне её контекста.

**Зачем нужны замыкания:**
- Для создания _фабричных функций_ с сохранением внутренних параметров (вместо глобальных переменных).
- Для инкапсуляции данных, когда не хочется использовать классы и нужно скрыть внутреннюю логику или состояние.
- Для генерации функций с "запомненным" состоянием или параметром.

```python
def make_multiplier(n):
    def multiplier(x):
        return x * n
    return multiplier

double = make_multiplier(2)
triple = make_multiplier(3)

print(double(4))  # 8
print(triple(4))  # 12
```
Здесь `multiplier` — замыкание: оно "помнит" значение `n` из внешней функции.

```python
def counter():
    count = 0
    def inc():
        nonlocal count
        count += 1
        return count
    return inc

count1 = counter()
print(count1())  # 1
print(count1())  # 2
```


## `16.3` (`*`) Паттерн Фабрика
`Паттерн Фабрика` — это способ централизованного создания объектов или значений, когда точный тип или параметры неизвестны заранее. В Python, без использования классов, он часто реализуется как функция, которая принимает параметры и возвращает нужное значение (например, другую функцию или структуру).

### Зачем нужен
- Чтобы упростить создание разных вариантов объектов или функций.
- Чтобы скрыть логику создания внутри одной функции.
- Чтобы избежать повторения кода.

### Пример простой фабрики без классов
```python
def animal_factory(animal_type):
    if animal_type == "dog":
        return "Гав-гав"
    elif animal_type == "cat":
        return "Мяу"
    else:
        return "Неизвестный звук"

print(animal_factory("dog"))  # Гав-гав
print(animal_factory("cat"))  # Мяу
```


## `16.4` (`*`) Локальные и глобальные переменные. Область видимости. Правило `LEGB`
В Python **локальные переменные** объявляются внутри функций и доступны только в этих функциях. **Глобальные переменные** находятся вне всех функций и доступны во всей программе. Если объявить переменную внутри функции с тем же именем, что и глобальная — внутри функции будет использоваться локальная версия, а глобальная вне функции.

**Область видимости** — определяет, где переменная "видна" и доступна для использования. Локальные переменные исчезают после завершения функции, глобальные — сохраняются на протяжении исполнения всей программы.

### LEGB правило поиска переменных
Python ищет переменные по цепочке областей видимости:
- **L**ocal (Локальная): внутри текущей функции или метода
- **E**nclosing (Вложенная): в родительских (внешних) функциях, если используется вложенность
- **G**lobal (Глобальная): на уровне всего модуля (файла)
- **B**uilt-in (Встроенная): специальные переменные и функции Python (например, `print`, `len`)

**Глобальная переменная:**
```python
x = "глобальная переменная"

def show():
    print(x)  # доступ к глобальной переменной
show()
print(x)      # доступ вне функции
```

**Локальная переменная:**
```python
def foo():
    y = "локальная переменная"
    print(y)
foo()
# print(y)  # Ошибка, вне функции переменная недоступна
```

**LEGB - вложенные функции:**
```python
def outer():
    a = "enclosing"
    def inner():
        print(a)  # ищет переменную во внешней функции (Enclosing)
    inner()
outer()
```

**Изменение глобальной переменной внутри функции:**
```python
global_var = 10

def update():
    global global_var
    global_var = 20  # изменится глобальная переменная
update()
print(global_var)    # 20
```

----

# `17` Декораторы
## `17.1` Что такое декоратор? Как написать свой декоратор?  
## `17.2` Есть ли что-то похожее в других языках?  
## `17.3` Атрибуты `__name__` & `__doc__`  
## `17.4` `@functools.wraps` - что такое и зачем?  
## `17.5` Параметризованный декоратор  

----

# `18` Итераторы
## `18.1` Что такое итераторы? Зачем они нужны? В чем их профит?  
## `18.2` Генераторы  
## `18.3` В чем разница генераторов от итераторов?  
## `18.4` Когда использовать и кейсы  
## `18.5` Повторить, что такое `range`  

----

# `19` Type hints
## `19.1` Что такое и зачем нужны?  
## `19.2` Что такое динамическая типизация?  
## `19.3` Модуль `typing`  
## `19.4` Если есть желание, посмотреть, как было на более старых версиях  

----

# `20` Extra Python  
_P.S: only for flexing on the job interview_  

## `20.1` Модуль `itertools`  
## `20.2` Модуль `functools`  
## `20.3` Регулярные выражения. Модуль `re`  

----

# `21` Cache
## `21.1` Что такое кэш?  
## `21.2` `lru_cache` и мемоизация  
## `21.3` Методы кэширования  
## `21.4` Что такое хэш?  
## `21.5` Разница кэша и хэша  

----

# `22` Типы данных 4  
_P.S: only for flexing on the job interview_  

## `22.1` `Decimal` что такое и для чего нужен?  
## `22.2` `namedtuple` что такое и для чего нужен?  
## `22.3` `defaultdict` что такое и для чего нужен?  
## `22.4` `OrderedDict` что такое и для чего нужен?  
## `22.5` `ChainMap` что такое и для чего нужен?  
## `22.6` `deque` что такое и для чего нужен?  
## `22.7` Можно ещё поизучать модуль `collections`  

----

# `23` Принципы ООП
## `23.1` Парадигмы программирования. Что такое объект в Python?  
## `23.2` Преимущества ООП и недостатки  
## `23.3` Что такое класс и объект?  
## `23.4` 4 принципа ООП  
- абстракция  
- инкапсуляция  
- наследование  
- полиморфизм  

----

# `24` Атрибуты и методы
## `24.1` Какие кейсы есть вообще, и какие соглашения на использовании в Python (camelCase, snake_case, etc)  
## `24.2` Функция `dir()` — для получения списка атрибутов и методов объекта  
## `24.3` Создание классов и объектов в Python  
## `24.4` Атрибуты класса и объекта (без `__init__`)  
## `24.5` Атрибут `__dict__` — словарь атрибутов объекта  
## `24.6` Встроенные функции для работы с атрибутами:  
- `getattr()` — получить атрибут  
- `setattr()` — установить атрибут  
- `delattr()` — удалить атрибут  
- `hasattr()` — проверить наличие атрибута  
## `24.7` Что такое метод и как его создавать?  

----

# `25` Методы экземпляра класса
## `25.1` Метод `__init__` — конструктор класса  
## `25.2` Параметр `self` — что это и зачем нужен  

----

# `26` Доступ к атрибутам
## `26.1` Сокрытие данных (инкапсуляция) в Python  
## `26.2` Соглашения между разработчиками по именованию и доступу  
## `26.3` Геттеры, сеттеры, делитеры — что это и зачем нужны  
## `26.4` Свойство (`property`) — атрибут с управляемым доступом  
## `26.5` Декоратор `@property` — как работает и зачем  
## `26.6` Декораторы `@classmethod` и `@staticmethod` — что такое `cls` и различия  
## `26.7` Продвинутое: `@singledispatchmethod` — перегрузка методов по типу аргумента  

----

# `27` (`*`) Магические методы
Что такое магические методы и зачем нужны?
## `27.1` `__init__`, `__new__`, `super()`, `__del__`
## `27.2` `__str__`, `__repr__`
## `27.3` Сравнение объектов
- `__eq__`
- `__ne__`
- `__lt__`
- `__gt__`
- `__le__`
- `__ge__`
## `27.4` Вызываемые объекты
- `__call__`
## `27.5` Работа с атрибутами
- `__getattribute__`
- `__getattr__`
- `__setattr__`
- `__delattr__`
## `27.6` Хэширование
## `27.7` (`**`) Ultra flex
1) Унарные операторы
2) Арифметические операции
3) Преобразование типов

----

# `28` (`*`) Протоколы
## `28.1` Итерируемые объекты и итераторы
## `28.2` Протокол контекстных менеджеров
## `28.3` Дескрипторы
## `28.4` (`**`) Ultra flex
1) Протокол последовательностей
2) Протокол дескрипторов

----

# `29` (`*`) Наследование и Полиморфизм
## `29.1` Наследование
## `29.2` Полиморфизм
## `29.3` Абстрактные классы и протоколы
## `29.4` Generics
## `29.5` Композиция

----

# `30` (`*`) Extra OOP
## `30.1` `__slots__`, `__dict__`
## `30.2` Enum
## `30.3` Миксины
## `30.4` dataclasses

----

# `31` (`*`) Виртуальное окружение
## `31.1` Что такое виртуальное окружение и зачем?
## `31.1` venv
## `31.1` poetry

----

# `32` (`*`) Многопоточность
## `32.1` Что такое многопоточность и зачем она нужна
## `32.2` Потоки vs Процессы — основные различия
## `32.3` GIL (Global Interpreter Lock) — что это и как влияет на многопоточность в Python
## `32.4` Модуль threading — основной инструмент для работы с потоками
## `32.5` Создание и запуск потоков:
- Класс `Thread`
- Параметры `target`, `args`, `kwargs`
- Метод `start()` — запуск потока
- Метод `join()` — ожидание завершения потока
## `32.6` Наследование от класса Thread — создание собственных потоков
## `32.7` Daemon потоки — что это и когда использовать
## `32.8` Синхронизация потоков:
`Lock` — блокировка для предотвращения гонки данных
`RLock` — рекурсивная блокировка
`Semaphore` — ограничение количества одновременных доступов
`Event` — сигнализация между потоками
`Condition` — условная синхронизация
## `32.9` Проблема гонки данных (race condition) и как её избежать
## `32.10` Deadlock (взаимная блокировка) — что это и как предотвратить
## `32.11` Модуль queue для безопасного обмена данными между потоками:
`Queue` — FIFO очередь
`LifoQueue` — LIFO очередь (стек)
`PriorityQueue` — очередь с приоритетами
## `32.12` threading.local() — thread-local данные
## `32.13` concurrent.futures.ThreadPoolExecutor — пул потоков для упрощённой работы
## `32.14` Контекстный менеджер для работы с блокировками
## `32.15` Когда использовать многопоточность: I/O-bound задачи

----

# `33` (`*`) Асинхронность
## `33.1` Что такое асинхронность и чем отличается от многопоточности
## `33.2` Синхронный vs асинхронный код — основные различия
## `33.3` Event Loop (цикл событий) — что это и как работает
## `33.4` Ключевые слова `async` и `await` — основы async/await синтаксиса
## `33.5` Корутины (coroutines) — что это и как их создавать
## `33.6` Модуль `asyncio` — основной инструмент для асинхронного программирования
## `33.7` Запуск асинхронного кода:
- `asyncio.run()` — запуск корутины
- `asyncio.create_task()` — создание задачи
- `asyncio.gather()` — параллельное выполнение корутин
## `33.8` Awaitable объекты — что можно await'ить
## `33.9` Task (задачи) — управление асинхронными операциями
## `33.10` `asyncio.sleep()` — асинхронная пауза
## `33.11` Async context managers — `async with`
## `33.12` Async iterators и async generators — `async for`
## `33.13` Работа с асинхронными очередями — `asyncio.Queue`
## `33.14` Синхронизация в asyncio:
- `asyncio.Lock`
- `asyncio.Semaphore`
- `asyncio.Event`
- `asyncio.Condition`
## `33.15` `asyncio.wait()` и `asyncio.wait_for()` — управление временем выполнения
## `33.16` Обработка исключений в асинхронном коде
## `33.17` `asyncio.shield()` — защита задач от отмены
## `33.18` Отмена задач — `task.cancel()` и обработка `CancelledError`
## `33.19` Работа с subprocess асинхронно — `asyncio.create_subprocess_exec()`
## `33.20` Интеграция синхронного кода в асинхронный:
- `asyncio.to_thread()` — выполнение блокирующего кода
- `loop.run_in_executor()` — использование executor'ов
## `33.21` `concurrent.futures` и asyncio — совместное использование
## `33.22` Async библиотеки для HTTP-запросов:
- `aiohttp` — основы (упоминание без деталей)
- `httpx` — основы (упоминание без деталей)
## `33.23` Когда использовать асинхронность: I/O-bound задачи с высоким concurrency
## `33.24` Продвинутое: создание собственного event loop
## `33.25` Продвинутое: `asyncio.Future` — низкоуровневая работа с результатами

----

# `33` (`*`) Логирование
## `33.1` Что такое логирование и зачем оно нужно
## `33.2` Логирование vs `print()` — основные различия
## `33.3` Модуль `logging` — стандартный инструмент
## `33.4` Уровни логирования — `DEBUG`, `INFO`, `WARNING`, `ERROR`, `CRITICAL`
## `33.5` Базовое логирование — `logging.basicConfig()` и простые функции
## `33.6` Logger — создание именованных логгеров через `logging.getLogger()`
## `33.7` Handler — куда отправляются логи:
- `StreamHandler` — консоль
- `FileHandler` — файл
- `RotatingFileHandler` — ротация файлов
## `33.8` Formatter — форматирование сообщений и основные переменные
## `33.9` Настройка уровней логирования для logger и handler
## `33.10` Логирование исключений — `logger.exception()` и `exc_info=True`
## `33.11` Конфигурация через словарь — `logging.config.dictConfig()`

----

# `34` (`*`) Паттерны проектирования*
## `34.1` Что такое паттерны проектирования и зачем они нужны
`Паттерны проектирования` — это проверенные временем решения типовых проблем, которые возникают при разработке программного обеспечения. Это не готовый код, который можно скопировать, а концептуальные шаблоны для решения конкретных задач.

**Зачем нужны паттерны**:
- **Переиспользование решений** — не нужно изобретать велосипед для типовых задач
- **Общий язык** — разработчики понимают друг друга, когда говорят "здесь нужен Singleton" или "давай используем Factory"
- **Улучшение архитектуры** — код становится более гибким, расширяемым и поддерживаемым
- **Избежание ошибок** — паттерны учитывают подводные камни, с которыми уже столкнулись другие разработчики

## `34.2` Категории паттернов — порождающие, структурные, поведенческие
`Паттерны проектирования` делятся на три основные категории по типу решаемых задач:

### **Порождающие паттерны (Creational Patterns)**
Отвечают за создание объектов. Помогают сделать систему независимой от способа создания, композиции и представления объектов.

**Основные паттерны:**
- **Singleton** — гарантирует единственный экземпляр класса
- **Factory Method** — делегирует создание объектов подклассам
- **Builder** — пошаговое создание сложных объектов
- **Prototype** — создание объектов через клонирование

**Когда использовать:** когда нужно контролировать процесс создания объектов, скрыть сложную логику инициализации или обеспечить гибкость при создании.

### **Структурные паттерны (Structural Patterns)**
Описывают способы композиции классов и объектов. Помогают организовать связи между объектами так, чтобы система оставалась гибкой и эффективной.

**Основные паттерны:**
- **Decorator** — позволяет динамически добавлять объектам новую функциональность, оборачивая их в специальные объекты-обёртки
- **Adapter** — приводит интерфейс класса к ожидаемому виду
- **Facade** — предоставляет простой интерфейс к сложной системе
- **Proxy** — контролирует доступ к объекту
- **Composite** — организует объекты в древовидную структуру

**Когда использовать:** когда нужно упростить сложные связи между объектами, сделать систему модульной или обеспечить совместимость несовместимых интерфейсов.

### **Поведенческие паттерны (Behavioral Patterns)**
Определяют взаимодействие между объектами и распределение обязанностей. Помогают организовать эффективную коммуникацию и управление алгоритмами.

**Основные паттерны:**
- **Strategy** — позволяет менять алгоритмы независимо от клиента
- **Observer** — механизм подписки на события
- **Iterator** — последовательный доступ к элементам коллекции
- **Command** — инкапсулирует запрос как объект
- **State** — изменяет поведение объекта при изменении состояния

**Когда использовать:** когда нужно гибко управлять поведением объектов, организовать взаимодействие между компонентами или инкапсулировать изменяющееся поведение.

## `34.3` Singleton — единственный экземпляр класса
`Singleton` гарантирует, что у класса существует только один экземпляр, и предоставляет глобальную точку доступа к нему.

**Зачем нужен:**
- Управление общими ресурсами — подключение к БД, логгер, конфигурация приложения
- Координация действий в системе через единую точку доступа
- Экономия ресурсов — создаём объект только один раз

**Реализация через `__new__`:**
```python
class Database:
    _instance = None
    
    def __new__(cls, *args, **kwargs):
        if cls._instance is None:
            cls._instance = super().__new__(cls)
        return cls._instance
    
    def __init__(self, host='localhost'):
        self.host = host

# Использование
db1 = Database('localhost')
db2 = Database('remote')
print(db1 is db2)  # True — один и тот же объект
```

Еще можно реализовать через: `декоратор` и `создания единственный экземпляр в коде, а затем его переиспользование (более Питонячий подход)`

**Когда использовать:**
- Конфигурация приложения
- Пул соединений к БД
- Система логирования
- Кеш или реестр объектов

**Осторожно:**
- Усложняет тестирование (глобальное состояние)
- Может нарушать принцип единственной ответственности
- В многопоточности требует синхронизации

[Больше про Singleton](https://habr.com/ru/companies/otus/articles/779914/)


## `34.4` Factory Method — фабричный метод для создания объектов
`Factory Method` делегирует создание объектов подклассам или отдельным методам, позволяя выбирать тип создаваемого объекта во время выполнения программы.

**Зачем нужен:**
- Скрывает сложную логику создания объектов
- Позволяет создавать разные типы объектов через единый интерфейс
- Упрощает добавление новых типов объектов без изменения существующего кода

**Простой пример — создание транспорта:**
```python
from abc import ABC, abstractmethod

class Transport(ABC):
    @abstractmethod
    def deliver(self):
        pass

class Truck(Transport):
    def deliver(self):
        return "Доставка по земле на грузовике"

class Ship(Transport):
    def deliver(self):
        return "Доставка по морю на корабле"

# Простой фабричный метод
class Logistics:
    @staticmethod
    def create_transport(transport_type: str) -> Transport:
        if transport_type == "ground":
            return Truck()
        elif transport_type == "sea":
            return Ship()
        else:
            raise ValueError(f"Неизвестный тип транспорта: {transport_type}")

# Использование
transport = Logistics.create_transport("ground")
print(transport.deliver())  # Доставка по земле на грузовике

transport = Logistics.create_transport("sea")
print(transport.deliver())  # Доставка по морю на корабле
```

**Pythonic подход — функция-фабрика:**
```python
def create_payment_processor(payment_type: str):
    processors = {
        'credit_card': CreditCardProcessor,
        'paypal': PayPalProcessor,
        'crypto': CryptoProcessor
    }
    
    processor_class = processors.get(payment_type)
    if processor_class is None:
        raise ValueError(f"Неизвестный тип платежа: {payment_type}")
    
    return processor_class()

# Использование
processor = create_payment_processor('paypal')
processor.process_payment(100)
```

**Когда использовать:**
- Когда заранее неизвестно, объекты каких типов нужно создавать
- Когда логика создания объектов сложная и её нужно инкапсулировать
- Когда нужно легко добавлять новые типы объектов
- Для парсеров, обработчиков файлов разных форматов, драйверов БД

**Преимущества:**
- Слабая связанность — клиент не зависит от конкретных классов
- Легко расширяется новыми типами
- Централизованная логика создания

[Больше про Factory Method](https://habr.com/ru/articles/725340/)

## `34.5` Builder — пошаговое создание сложных объектов
`Builder` позволяет создавать сложные объекты пошагово, разделяя процесс конструирования и представления. Особенно полезен, когда объект имеет много параметров или сложную структуру.

**Зачем нужен:**
- Упрощает создание объектов с множеством параметров
- Делает код читаемым и понятным
- Позволяет создавать разные представления объекта через один интерфейс
- Избегает "телескопических конструкторов" с десятками параметров

**Классический пример — построение дома:**
```python
class House:
    def __init__(self):
        self.walls = None
        self.roof = None
        self.windows = None
        self.doors = None
        self.garage = None
    
    def __str__(self):
        parts = []
        if self.walls:
            parts.append(f"Стены: {self.walls}")
        if self.roof:
            parts.append(f"Крыша: {self.roof}")
        if self.windows:
            parts.append(f"Окна: {self.windows}")
        if self.doors:
            parts.append(f"Двери: {self.doors}")
        if self.garage:
            parts.append(f"Гараж: {self.garage}")
        return "Дом с:\n" + "\n".join(parts)

class HouseBuilder:
    def __init__(self):
        self.house = House()
    
    def build_walls(self, material):
        self.house.walls = material
        return self  # Возвращаем self для цепочки вызовов
    
    def build_roof(self, roof_type):
        self.house.roof = roof_type
        return self
    
    def build_windows(self, count):
        self.house.windows = count
        return self
    
    def build_doors(self, count):
        self.house.doors = count
        return self
    
    def build_garage(self, has_garage):
        self.house.garage = has_garage
        return self
    
    def get_house(self):
        return self.house

# Использование — метод цепочки (fluent interface)
builder = HouseBuilder()
house = (builder
         .build_walls("кирпич")
         .build_roof("черепица")
         .build_windows(4)
         .build_doors(2)
         .build_garage(True)
         .get_house())

print(house)
# Дом с:
# Стены: кирпич
# Крыша: черепица
# Окна: 4
# Двери: 2
# Гараж: True
```

**Пример с HTTP-запросом:**
```python
class HttpRequest:
    def __init__(self):
        self.method = "GET"
        self.url = None
        self.headers = {}
        self.body = None
        self.timeout = 30
    
    def __str__(self):
        return f"{self.method} {self.url}\nHeaders: {self.headers}\nBody: {self.body}"

class RequestBuilder:
    def __init__(self, url):
        self.request = HttpRequest()
        self.request.url = url
    
    def method(self, method):
        self.request.method = method
        return self
    
    def header(self, key, value):
        self.request.headers[key] = value
        return self
    
    def body(self, data):
        self.request.body = data
        return self
    
    def timeout(self, seconds):
        self.request.timeout = seconds
        return self
    
    def build(self):
        return self.request

# Использование
request = (RequestBuilder("https://api.example.com/users")
           .method("POST")
           .header("Content-Type", "application/json")
           .header("Authorization", "Bearer token123")
           .body({"name": "John", "age": 30})
           .timeout(60)
           .build())

print(request)
# POST https://api.example.com/users
# Headers: {'Content-Type': 'application/json', 'Authorization': 'Bearer token123'}
# Body: {'name': 'John', 'age': 30}
```

**Pythonic подход — dataclass с Builder:**
```python
from dataclasses import dataclass, field
from typing import Optional, List

@dataclass
class Pizza:
    size: str
    cheese: bool = False
    pepperoni: bool = False
    mushrooms: bool = False
    olives: bool = False
    toppings: List[str] = field(default_factory=list)
    
    def __str__(self):
        base = f"Пицца {self.size}"
        ingredients = []
        if self.cheese:
            ingredients.append("сыр")
        if self.pepperoni:
            ingredients.append("пепперони")
        if self.mushrooms:
            ingredients.append("грибы")
        if self.olives:
            ingredients.append("оливки")
        ingredients.extend(self.toppings)
        
        if ingredients:
            return f"{base} с: {', '.join(ingredients)}"
        return base

class PizzaBuilder:
    def __init__(self, size: str):
        self.size = size
        self._cheese = False
        self._pepperoni = False
        self._mushrooms = False
        self._olives = False
        self._toppings = []
    
    def add_cheese(self):
        self._cheese = True
        return self
    
    def add_pepperoni(self):
        self._pepperoni = True
        return self
    
    def add_mushrooms(self):
        self._mushrooms = True
        return self
    
    def add_olives(self):
        self._olives = True
        return self
    
    def add_topping(self, topping: str):
        self._toppings.append(topping)
        return self
    
    def build(self) -> Pizza:
        return Pizza(
            size=self.size,
            cheese=self._cheese,
            pepperoni=self._pepperoni,
            mushrooms=self._mushrooms,
            olives=self._olives,
            toppings=self._toppings
        )

# Использование
pizza = (PizzaBuilder("большая")
         .add_cheese()
         .add_pepperoni()
         .add_mushrooms()
         .add_topping("бекон")
         .build())

print(pizza)  # Пицца большая с: сыр, пепперони, грибы, бекон
```

**Когда использовать:**
- Объект имеет много необязательных параметров
- Создание объекта требует множества шагов
- Нужно создавать разные представления одного объекта
- Хочется избежать конструктора с десятками параметров

**Преимущества:**
- Читаемый и понятный код
- Пошаговое конструирование
- Возможность повторного использования builder'а
- Изоляция сложной логики создания

[Еще реализация Builder](https://ru.hexlet.io/courses/python-object-oriented-design/lessons/builder/theory_unit)

## `34.6` Strategy — инкапсуляция алгоритмов
## `34.7` Observer — подписка на события и уведомления
## `34.8` Iterator — последовательный доступ к элементам (протокол итератора)
## `34.9` Context Manager — паттерн `with` и протокол `__enter__`/`__exit__`
## `34.10` Async Context Manager — `async with` и `__aenter__`/`__aexit__`
## `34.11` Async Decorator — декораторы для асинхронных функций
## `34.12` Dependency Injection — внедрение зависимостей

----

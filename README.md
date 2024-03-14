                                              Лабораторная работа №1
                                       Выполнил студент гр.БCТ 2201 Сиау.Э

Задание №1

Вызвать функцию print() и передать туда строку Hello, World!

Задание №2

Написать генератор случайных матриц(многомерных), который принимает опциональные параметры m, n, min_limit, max_limit, где m и n указывают размер матрицы, а min_lim и max_lim - минимальное и максимальное значение для генерируемого числа.

Задание №3

Реализовать методы сортировки строк (выбором, вставкой, пузырьком, Шелла, быстрая, турнирная) числовой матрицы в соответствии с заданием. Оценить время работы каждого алгоритма сортировки и сравнить его со временем стандартной функции сортировки. Испытания проводить на сгенерированных матрицах.

Выполнение:

                                                  В задании 1 нужно вызвать функцию print() и передать строку Hello World!

                                                                            Задание 1 представлено в 1.py




print("Hello, World!")
Hello, World!



                           В задании 2 нужно написать генератор случайных многомерных матриц (возможность ввода значений предоставляется пользователю)
                                                                      Задание 2 представлено в 2.py

import random


def random_matrix(m=3, n=3, min_limit=1,

max_limit=10):

    return [[random.randint(min_limit,
    
max_limit) for _ in range(n)] for _ i

range(m)]


#Пример использования
matrix = random_matrix(4, 4, 0, 200)
for row in matrix:
    print(row)
[167, 94, 29, 157]
[92, 102, 0, 136]
[69, 90, 200, 95]
[197, 40, 74, 34]


                                                                 В задании 3 нужно реализовать методы сортировки строк матриц
                                                                               Задание 3 представлено в 3.py


                                                                               

Сортировка вставкой :
Алгоритм сортировки вставками в Python делит список на две части и вставляет элементы на 
их правильные места во вторую часть списка, убирая их из первой.
Если второй элемент больше первого, то он остаётся на своём месте. 
Если он меньше, то вставляется на второе место, оставив первый элемент на первом месте.



#Сортировка вставкой 

def insertion_sort(arr):

     for i in range(1, len(arr)):
         key = arr[i]
         j = i - 1
         while j >= 0 and key < arr[j]:
             arr[j + 1] = arr[j]
             j -= 1
         arr[j + 1] = key
            
#Пример исползования

arr = [12, 11, 13, 5, 6]

insertion_sort(arr)

print("Отсортированный массив:", arr)

Отсортированный массив: [5, 6, 11, 12, 13]


Сортировка пузырьком (обменом):это метод сортировки массивов и списков путем последовательного 
сравнения и обмена соседних элементов, 
если предшествующий оказывается больше последующего.

#Сортивровка пузырком
def bubble_sort(arr):
    n = len(arr)

    for i in range(n):
         for j in range(0, n-i-1):
             if arr[j] > arr[j+1]:
                 arr[j], arr[j+1]= arr[j+1], arr[j]

    return arr
    

#Пример использования
arr = [64, 34, 25, 12, 22, 11, 90]
sorted_arr = bubble_sort(arr)
print("Отсортированный массив:", sorted_arr)

Отсортированный массив: [11, 12, 22, 25, 34, 64, 90]



Сортировка выбором:
Сортировка матрицы выбором в Python - это алгоритм сортировки, который применяется к матрице (двумерному массиву). 
Он работает путем поочередного нахождения наименьшего элемента в каждой строке и перемещения его на первое место в строке. 
После этого процесс повторяется для оставшихся элементов в строке.



#Сортировка выбором
def selection_sort(arr):
    n = len(arr)
    for i in range(n):
        min_index = i
        for j in range(i+1, n):
            if arr[j] < arr[min_index]:
                min_index = j 
        arr[i], arr[min_index] = arr[min_index], arr[i]

        

# Пример использования
arr = [64, 25, 12, 22, 11]
selection_sort(arr)
print("Отсортированный массив:", arr)

Отсортированный массив: [11, 12, 22, 25, 64]



Сортировка Шелла:
Метод Шелла заключается в том, чтобы сначала сортировать элементы с определенным шагом между ними, а затем постепенно уменьшать шаг. 
Сортировка выполняется с помощью сортировки вставками на каждом шаге. 
Когда шаг становится равным 1, массив полностью отсортирован.



#Сортировка Шелла
def shell_sort(arr):
    n = len(arr)
    gap = n // 2
    while gap > 0:
        for i in range(gap, n):
            temp = arr[i]
            j = i
            while j >= gap and arr[j - 
gap] > temp:
                 arr[j] = arr[j - gap]
                 j -= gap
            arr[j] = temp
        gap //=2

#Пример исползования
arr = [12, 34, 54, 2, 3]
shell_sort(arr)
print("Отсортированный массив:", arr)


Отсортированный массив: [2, 3, 12, 34, 54]




Быстрая сортировка: это эффективный алгоритм сортировки, который использует стратегию "разделяй и властвуй". 
Он работает путем выбора опорного элемента из массива и разделения массива на две подгруппы: одна содержит элементы, меньшие опорного, а другая - элементы, большие опорного. 
Затем алгоритм рекурсивно применяется к каждой из подгрупп.



#Быстрая сортировка
def quick_sort(arr):
    if len(arr) <=1:
        return arr
    else:
        pivot = arr[0]
        less = [x for x in arr[1:]
if x <= pivot]
        greater = [x for x in arr[1:
] if x > pivot]
        return quick_sort(less) + [
pivot] + quick_sort(greater)


        
#Пример использования
arr = [3, 6, 8, 10, 1, 2, 1]
sorted_arr = quick_sort(arr)
print(sorted_arr)



Турнирная сортировка:
Турнирная сортировка матрицы в Python - это алгоритм сортировки, который использует структуру данных
"турнирное дерево" для эффективной сортировки элементов матрицы. 



#Турнирная сортировка
def tournament_sort(arr):
    tree = [None] * 2 * (len(arr) + len(arr) % 2)
    index = len(tree) - len(arr)
    
    
    tree[index:index + len(arr)] = arr
    for i in range(index + len(arr) - 1, 0, -1):
        tree[i >> 1] = min(tree[i], tree[i ^ 1]) if tree[i] is not None and tree[i ^ 1] is not None else (tree[i ^ 1] if tree[i] is None else tree[i])
    return [tree[1]] + [tree.pop(tree.index(min(filter(None, tree[1:])))) for _ in arr]


arr = [54, 43, 3, 11, 0]
sorted_arr = tournament_sort(arr)
print(sorted_arr)


[0, 3, 3, 11, 43, 54]



Замеры времени работы алгоритмов сортировки:

Hello, World!
Execution time: 0.000993967056274414


#Турнирная сортировка
Execution time: 0.000993967056274414.


#Сортировка вставкой
Execution time: 0.0009963512420654297


#Сортивровка пузырком
Execution time: 0.0009963512420654297


#Сортировка выбором
Execution time: 0.0029976367950439453


#Сортировка Шелла
Execution time: 0.0019989013671875


#Быстрая сортировкa  
Execution time: 0.001998424530029297


Стандарт:
Execution time: 0.003990888595581055


#Турнирная сортировка
Execution time: 0.001993894577026367



                                                    Лабораторная работа №2
                                           Выполнил студент группы БСТ2201 Сиау.Э

                                           
Реализовать следующие структуры данных:


● Стек (stack):
Операции для стека: инициализация, проверка на пустоту, добавление нового элемента в начало, извлечение элемента из начала;


● Дек (двусторонняя очередь, deque):
Операции для дека: инициализация, проверка на пустоту, добавление нового элемента в начало, добавление нового элемента в конец, извлечение элемента из начала, извлечение элемента из конца.


Разработать программу обработки данных, содержащихся в заранее подготовленном txt-файле, в соответствии с заданиями, применив указанную в задании структуру данных. Результат работы программы вывести на экран и сохранить в отдельном txt-файле.


Создадим два класса для работы:



# класс для работы со Stack
class Stack:
    # инициализация
    def __init__(self):
        self.items = []
    # проверка на пустоту
    def isEmpty(self):
        return self.items == []
    # добавить элемент
    def push(self, item):
        self.items.append(item)
    # удалить элемент
    def pop(self):
        return self.items.pop()
    # развернуть 
    def reverse(self):
        self.items.reverse()

        
# класс для работы с Deque
class Deque:
    # инициализация
    def __init__(self):
        self.items = []
    # проверка на пустоту
    def isEmpty(self):
        return self.items == []
    # добавить вправо
    def append(self, item):
        self.items.append(item)
    # добавить влево
    def appendleft(self, item): 
        self.items.insert(0, item)
    # удалить справа
    def pop(self):
        return self.items.pop()
     # удалить слева
    def popleft(self):
        return self.items.pop(0)
    # вернуть элемент без удаления
    def peek(self):
        return self.items[-1]
     # развернуть 
    def reverse(self):
        self.items.reverse()
    # получить длину
    def __len__(self):
        return len(self.items)



# Функция для чтения текста из файла
def read_file(filename):
    with open(filename, 'r', encoding = "utf-8") as file:
        return [row.strip() for row in file]



# Функция для загрузки в файла
def save_to_file(filename, result):
    with open(filename, 'w', encoding = "utf-8") as f:
        if isinstance(result, str):
            f.write(result + "\n")
        else:
            for item in result:
                f.write(str(item) + "\n")



                                            Задание №1
    Отсортировать строки файла, содержащие названия книг, в алфавитном порядке с использованием двух деков.



# функция для сортировки названий книг
def sort_books(input_file_path):
  deq, sort_deq = [Deque() for _ in range(2)]
  [deq.append(book.strip()) for book in books]
  while not deq.isEmpty():
    element = deq.pop()
    # пока sort_deq не пустой и element меньше чем последний в sort_deq
    while not sort_deq.isEmpty() and element < sort_deq.peek():
      # добавляем в deq последний элемент sort_deq
      deq.append(sort_deq.pop())
    sort_deq.append(element)
  # вызов функции сохранения в файл
  save_to_file("test1.txt", sort_deq.items)
  while not sort_deq.isEmpty():
    print(sort_deq.popleft())
# вызов функции чтения из файл
books = read_file("task1.txt")
sort_books(books)


Джон Александер
Петер Блэксон
Сиау.Эрнест



                                                Задание №2                                       
                     Дек содержит последовательность символов для шифровки сообщений. 
                          Дан текстовый файл, содержащий зашифрованное сообщение. 
                                   Пользуясь деком, расшифровать текст. 
        Известно, что при шифровке каждый символ сообщения заменялся следующим за ним в деке по часовой стрелке через один.

        

# функция для расшифровки текста
def decode_text(input_file_path):
  deq = Deque()
  [deq.append(letter) for letter in 'абвгдеёжзийклмнопрстуфхцчшщъыьэюя']
  decrypted_text = ""
  # функция для расшифровки каждого символа
  def decryptText(variable):
    for letter in range(len(deq)):
      symbol = deq.popleft()
      # если наш извлеченный символ из дека == сравниваемому из текста
      if symbol == variable:
        # добавляем наш извлеченный символ из дека в конец дека
        deq.append(symbol)
        # извлечем след. символ после symbol
        next_symbol = deq.popleft()
        # посместим его в конец списка
        deq.append(next_symbol)
        # вернем последний извлченный символ для добавления в decrypted_text
        return next_symbol
      deq.append(symbol)


  for string in decode:
    for symbol in string.lower():
      decode_symbol = decryptText(symbol)
      # проверяет, произошло ли шифрование
      if decode_symbol:
          decrypted_text += decode_symbol
      else:
      
          decrypted_text += symbol
  # вызов функции сохранения в файл
  save_to_file("test2.txt", decrypted_text)
  return decrypted_text
# вызов функции чтения из файл
decode = read_file("task2.txt")
decode_text(decode)


'код от домофона - 47392!'





                                          Задание №3
                      Даны три стержня и n дисков различного размера. 
                  Диски можно надевать на стержни, образуя из них башни.
         Перенести n дисков со стержня А на стержень С, сохранив их первоначальный порядок. 
                    При переносе дисков необходимо соблюдать следующие правила:
                 на каждом шаге со стержня на стержень переносить только один диск;
                         диск нельзя помещать на диск меньшего размера;
                    для промежуточного хранения можно использовать стержень В. 
                 Реализовать алгоритм, используя три стека вместо стержней А, В, С. 
                       Информация о дисках хранится в исходном файле.

                       
                       
  def hanoi_tower(input_file_path):
  A, C, B = [Stack() for _ in range(3)]
  # положим диски в A начиная с n (большего)
  [A.push(disk) for disk in range(n, 0, -1)]
  # динамическое добавление атрибута
  A.name,C.name,B.name = "A", "C", "B"
  print(f'Состояние стержня A: {A.items}')
  # функция для движения дисков (решение рекурсией)
  def move_disks(n, start, end, middle):
    if n == 1:
      end.push(start.pop())
      print(f'Move disk 1 from rod {start.name} to rod {end.name}')
      return
    else:
      move_disks(n-1, start, middle, end)
      print(f'Move disk {n} from rod {start.name} to rod {end.name}')
      end.push(start.pop())
      move_disks(n-1, middle, end, start)
  # вызов функции и результата
  move_disks(n, A, C, B)
  C.reverse()
  save_to_file("test3.txt", C.items)
  C.reverse()
  return print(f'Состояние стержня C: {C.items}')
n = int(read_file("task3.txt")[0])
hanoi_tower(n)



Состояние стержня A: [4, 3, 2, 1]
Move disk 1 from rod A to rod B
Move disk 2 from rod A to rod C
Move disk 1 from rod B to rod C
Move disk 3 from rod A to rod B
Move disk 1 from rod C to rod A
Move disk 2 from rod C to rod B
Move disk 1 from rod A to rod B
Move disk 4 from rod A to rod C
Move disk 1 from rod B to rod C
Move disk 2 from rod B to rod A
Move disk 1 from rod C to rod A
Move disk 3 from rod B to rod C
Move disk 1 from rod A to rod B
Move disk 2 from rod A to rod C
Move disk 1 from rod B to rod C
Состояние стержня C: [4, 3, 2, 1]

                                                          Задание №4
                             Дан текстовый файл с программой на алгоритмическом языке.
                    За один просмотр файла проверить баланс круглых скобок в тексте, используя стек.


                    

                    
  def balance_round_brackets(input_file_path):
  balance = Stack()
  test = [symbol for row in text for symbol in row]
  for symbol in test:
    if symbol == "(":
      balance.push(symbol)
    elif symbol == ")":
      if balance.isEmpty():
        return False
      balance.pop()
  # вызов функции сохранения в файл
  save_to_file("test4.txt", str(balance.isEmpty()))
  # вернем True/False
  return balance.isEmpty()
# вызов функции чтения из файл
text = read_file("task4.txt")
balance_round_brackets(text)



True



                                          Задание №5
                     Дан текстовый файл с программой на алгоритмическом языке. 
          За один просмотр файла проверить баланс квадратных скобок в тексте, используя дек.



          
  def balance_square_brackets(input_file_path):
  balance = Deque()
  test = [symbol for row in text for symbol in row]
  for symbol in test:
    if symbol == "[":
      balance.append(symbol)
    elif symbol == "]":
      if balance.isEmpty():
        return False
      balance.pop()
  # вызов функции сохранения в файл
  save_to_file("test5.txt", str(balance.isEmpty()))
  # вернем True/False
  return balance.isEmpty()
# вызов функции чтения из файл
text = read_file("task5.txt")
balance_square_brackets(text)


False

                                            Задание №6
                                      Дан файл из символов. 
               Используя стек, за один просмотр файла напечатать сначала все цифры.
    затем все буквы, и, наконец, все остальные символы, сохраняя исходный порядок в каждой группе символов.



   def sort_text(input_file_path):
  stack = Stack()
  new_doc = ""
  for word in text:
    for symbol in word:
      # добавление в строку чисел иначе в стек
      if symbol.isdigit():
        new_doc += symbol
      else:
        stack.push(symbol)
    # добавление в строку букв
    for item in stack.items:
      if item.isalpha():
        new_doc += item
    # добавление в строку остальных символов
    for item in stack.items:
      if not item.isalpha():
        new_doc += item



  # вызов функции сохранения в файл
  save_to_file("test6.txt", new_doc)
  return new_doc
# вызов функции чтения из файл
text = read_file("task6.txt")
sort_text(text)


"4738GooddayCиауЭрнестHowareyoudoing'-,.    !_@'"



                                         Задание №7
                                   Дан файл из целых чисел. 
              Используя дек, за один просмотр файла напечатать сначала все отрицательные числа, 
                  затем все положительные числа, сохраняя исходный порядок в каждой группе.



   
  def balance_square_brackets(input_file_path):
  balance = Deque()
  test = [symbol for row in text for symbol in row]
  for symbol in test:
    if symbol == "[":
      balance.append(symbol)
    elif symbol == "]":
      if balance.isEmpty():
        return False
      balance.pop()
  # вызов функции сохранения в файл
  save_to_file("test5.txt", str(balance.isEmpty()))
  # вернем True/False
  return balance.isEmpty()
# вызов функции чтения из файл
text = read_file("task5.txt")
balance_square_brackets(text)


False



def sort_digits(input_file_path):
  deq = Deque()
  digits = [int(number.strip()) for number in numbers]
  [deq.append(num) for num in digits if num >= 0]
  digits.reverse()
  [deq.appendleft(num) for num in digits if num < 0]
  # вызов функции сохранения в файл
  save_to_file("test7.txt", deq.items)
  while not deq.isEmpty():
    print(deq.popleft())
# вызов функции чтения из файл
numbers = read_file("task7.txt")
sort_digits(numbers)


-6
-3
-4
19
0
12
7
10
1
79

                                     Задание №8
          Дан текстовый файл. Используя стек, сформировать новый текстовый файл, 
            содержащий строки исходного файла, записанные в обратном порядке: 
           первая строка становится последней, вторая – предпоследней и т.д.




   def reverse_strings(input_file_path):
    phrases = Stack()
    [phrases.push(string) for string in strings]
    phrases.reverse()
    # вызов функции сохранения в файл
    save_to_file("test8.txt", phrases.items)
    phrases.reverse()
    # вывод на экран
    while not phrases.isEmpty():
        print(phrases.pop())
# вызов функции чтения из файл
strings = read_file("task8.txt")
reverse_strings(strings)



Четвертая(4-й) фраза
Третья(3-й) фраза
Вторая(2-й) фраза
Первая(1-й) фраза




                                                      Вывод
               Разработал программы обработки данных, содержащихся в заранее подготовленном txt-файле, 
                    в соответствии с заданиями, применив указанную в задании структуру данных. 
                     Результат работы программ вывел на экран и сохранил в отдельном txt-файле.



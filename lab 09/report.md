---
# Front matter
lang: ru-RU
title: "Отчет по лабораторной работе 9"
subtitle: "Текстовой редактор vi"
author: "Шалыгин Георгий Эдуардович, НФИбд-02-20"

# Formatting
toc-title: "Содержание"
toc: true # Table of contents
toc_depth: 2
lof-title: "Список изображений"
lof: true # Список изображений
fontsize: 12pt
linestretch: 1.5
papersize: a4paper
documentclass: scrreprt
polyglossia-lang: russian
polyglossia-otherlangs: english
mainfont: Cambria
romanfont: Cambria
sansfont: Cambria
monofont: Cambria
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase
indent: true
pdf-engine: lualatex
header-includes:
  - \linepenalty=10 # the penalty added to the badness of each line within a paragraph (no associated penalty node) Increasing the value makes tex try to have fewer lines in the paragraph.
  - \interlinepenalty=0 # value of the penalty (node) added after each line of a paragraph.
  - \hyphenpenalty=50 # the penalty for line breaking at an automatically inserted hyphen
  - \exhyphenpenalty=50 # the penalty for line breaking at an explicit hyphen
  - \binoppenalty=700 # the penalty for breaking a line at a binary operator
  - \relpenalty=500 # the penalty for breaking a line at a relation
  - \clubpenalty=150 # extra penalty for breaking after first line of a paragraph
  - \widowpenalty=150 # extra penalty for breaking before last line of a paragraph
  - \displaywidowpenalty=50 # extra penalty for breaking before last line before a display math
  - \brokenpenalty=100 # extra penalty for page breaking after a hyphenated line
  - \predisplaypenalty=10000 # penalty for breaking before a display
  - \postdisplaypenalty=0 # penalty for breaking after a display
  - \floatingpenalty = 20000 # penalty for splitting an insertion (can only be split footnote in standard LaTeX)
  - \raggedbottom # or \flushbottom
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Познакомиться с операционной системой Linux. Получить практические навыки работы с редактором vi, установленным по умолчанию практически во всех дистрибутивах.

Объект исследования: редактор vi.

Предмет исследования: возможность для редактирования файлов в vi.

# Техническое обеспечение:

- Характеристики техники: AMD Ryzen 5 3500U 2.1 GHz, 8 GB оперативной памяти, 50 GB свободного места на жёстком диске;
- ОС Windows 10 Home
- Git  2.31.1
- Google Chrome 91.0.4472.19
- VirtualBox 2.0
- CentOS 7

# Условные обозначения и термины:

**Текстовым редактором**(text editor) называют программу, которая предназначена для редактирования (составления и изменения) файлов, содержащих только текст

**Виртуальная файловая система** (VFS) – компонент ядра Linux, обеспечивающий пользователю доступ к различным файловым системам. Собственно, VFS определяет интерфейс между ядром и файловой системой но, вместе с тем не ориентирована на какую-либо конкретную файловую систему.

**Владелец файла или каталога** – пользователь создавший файл или каталог, является его владельцем. Сменить владельца может только он сам или суперпользователь (root).

**Рут** (**root**) или **Суперпользователь** – администратор в UNIX-системах. Имеет все права пользователя и может выполнять любые без исключения операции.

**Файловая система ОС типа Linux** — иерархическая система каталогов, подкаталогов и файлов, которые обычно организованы и сгруппированы по функциональному признаку.[1]

# Теоретическое введение:

##### Запуск редактора vi.

Синтаксис редактора vi таков:

```bash
vi filename
```

где filename — имя файла, который надо редактировать.[1]

При этом в случае отсутствия файла с указанным именем будет создан такой файл. Переход в командный режим осуществляется нажатием клавиши Esc . Для выхода из редактора vi необходимо перейти в режим последней строки: находясь в командном режиме, нажать Shift-; (по сути символ : — двоеточие), затем: – набрать символы wq, если перед выходом из редактора требуется записать изменения в файл; – набрать символ q (или q!), если требуется выйти из редактора без сохранения.

##### Команды позиционирования

- 0 (ноль) — переход в начало строки; 
- $ — переход в конец строки; 
- G — переход в конец файла; 
- n G — переход на строку с номером n.

##### Команды перемещения по файлу

- Ctrl-d — перейти на пол-экрана вперёд; 
- Ctrl-u — перейти на пол-экрана назад; 
- Ctrl-f — перейти на страницу вперёд; 
- Ctrl-b — перейти на страницу назад

##### Команды перемещения по словам

- W или w — перейти на слово вперёд; 
- n W или n w — перейти на n слов вперёд; 
- b или B — перейти на слово назад; 
- n b или n B — перейти на n слов назад.

##### Вставка текста 

- а — вставить текст после курсора; 
-  А — вставить текст в конец строки; 
-  i — вставить текст перед курсором; 
- n i — вставить текст n раз; 
-  I — вставить текст в начало строки. 

##### Вставка строки 

- о — вставить строку под курсором; 
- О — вставить строку над курсором.

##### Удаление текста 

- x — удалить один символ в буфер; 
- d w — удалить одно слово в буфер; 
-  d $ — удалить в буфер текст от курсора до конца строки; 
- d 0 — удалить в буфер текст от начала строки до позиции курсора. При использовании прописных W и B под разделителями понимаются только пробел, табуляция и возврат каретки. При использовании строчных w и b под разделителями понимаются также любые знаки пунктуации.[2]




# Выполнение лабораторной работы

1. Выполним примеры, приведённые в первой части описания лабораторной работы

   1. Создайте каталог с именем ~/work/2020-2021/os/lab06. В нем вызовем vi и создадим файл hello.sh: vi hello.sh. (рис. -@fig:001)

      ![Создание файла](screens\1.jpg){ #fig:001 width=70% }

   2. Нажмите клавишу i и вводите следующий текст (рис. -@fig:002). Нажмем клавишу Esc для перехода в командный режим после завершения ввода текста. Нажмем :qw для выхода и сохранения файла.

      ```bash
      #!/bin/bash
      HELL=Hello
      function hello {
      	LOCAL HELLO=World
      	echo $HELLO
      }
      echo $HELLO
      hello
      ```

      ![Файл в vi](screens\2.jpg){ #fig:002 width=70% }

   3. Сделайте файл исполняемым (рис. -@fig:003).

      ```bash
      chmod +x hello.sh
      ```

      ![Изменение прав доступа](screens\3.jpg){ #fig:003 width=70% }

   4. Установим курсор в конец слова HELL второй строки, перейдем в режим вставки и заменим на HELLO. (рис.  -@fig:004)

      ![Редактирование HELLO](screens\4.jpg){ #fig:004 width=70% }

   5. Установим курсор на четвертую строку и сотрите слово LOCAL. Перейдем в режим вставки и наберите следующий текст: local, нажмем Esc для возврата в командный режим. (рис.  -@fig:005)

      ![Редактирование local](screens\5.jpg){ #fig:005 width=70% }

   6. Установим курсор на последней строке файла. Вставим после неё строку, содержащую следующий текст: echo $HELLO. (рис.  -@fig:006)

      ![Вставка и копирование строк](screens\6.jpg){ #fig:006 width=70% }

   7. Нажмите Esc для перехода в командный режим и удалим последнюю строку. (рис.  -@fig:007)

      ![Удаление строки](screens\7.jpg){ #fig:007 width=70% }

   8. Введите команду отмены изменений u для отмены последней команды. (рис.  -@fig:008)

      ![Отмена команды](screens\8.jpg){ #fig:008 width=70% }

   9. Введите :wq для сохранения изменений и выхода. (рис.  -@fig:009)

      ![Сохранение и выход](screens\9.jpg){ #fig:009 width=70% }

   


# Выводы

В процессе работы над лабораторной работы были получены навыки работы с редактором vi и освоены команды для редактирования файлов и навигации по ним.

# Библиография

1. https://docs.altlinux.org/ru-RU/archive/2.3/html-single/junior/alt-docs-extras-linuxnovice/ch02s10.html
2. Д.С. Кулябов, А.В. Королькова / Администрирование локальных систем. Лабораторные работы. — М.: Российский университет дружбы народов, 2017. — 119 с.
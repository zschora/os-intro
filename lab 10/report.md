---
# Front matter
lang: ru-RU
title: "Отчет по лабораторной работе 10"
subtitle: "Текстовой редактор emacs"
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

Познакомиться с операционной системой Linux. Получить практические навыки работы с редактором Emacs.

Объект исследования: редактор Emacs.

Предмет исследования: возможность для редактирования файлов в Emacs.

# Техническое обеспечение:

- Характеристики техники: AMD Ryzen 5 3500U 2.1 GHz, 8 GB оперативной памяти, 50 GB свободного места на жёстком диске;
- ОС Windows 10 Home
- Git  2.31.1
- Google Chrome 91.0.4472.19
- VirtualBox 2.0
- CentOS 7

# Условные обозначения и термины:

**Текстовым редактором**(text editor) называют программу, которая предназначена для редактирования (составления и изменения) файлов, содержащих только текст. [1]

**Буфер** — объект, представляющий какой-либо текст.

**Фрейм** соответствует окну в обычном понимании этого слова. Каждый фрейм содержит область вывода и одно или несколько окон Emacs.

**Окно** — прямоугольная область фрейма, отображающая один из буферов.

**Область вывода** — одна или несколько строк внизу фрейма, в которой Emacs выводит различные сообщения, а также запрашивает подтверждения и дополнительную информацию от пользователя.

**Минибуфер** используется для ввода дополнительной информации и всегда отображается в области вывода.

**Точка вставки** — место вставки (удаления) данных в буфере. [3]

# Теоретическое введение:

##### Запуск редактора Emacs .

Для запуска Emacs необходимо в командной строке набрать emacs.

Многие рутинные операции в Emacs удобнее производить с помощью клавиатуры, а не графического меню. Наиболее часто в командах Emacs используются сочетания c клавишами Ctrl и Meta (в обозначениях Emacs: C- и M-; клавиша Shift в Emasc обозначается как S-). Так как на клавиатуре для IBM PC совместимых ПК клавиши Meta нет, то вместо неё можно использовать Alt или Esc . Для доступа к системе меню используйте клавишу F10 .

##### Команды  перемещения курсора в буфере Emacs

- C-p переместиться вверх на одну строку
- C-n переместиться вниз на одну строку
- C-f переместиться вперёд на один символ
- C-b переместиться назад на один символ
- C-a переместиться в начало строки
- C-e переместиться в конец строки
- C-v переместиться вниз на одну страницу
- M-v переместиться вверх на одну страницу
- M-f переместиться вперёд на одно слово
- M-b переместиться назад на одно слово
- M-< переместиться в начало буфера
- M-> переместиться в конец буфера
- C-g закончить текущую операцию

##### Команды для работы с текстом

- C-d Удалить символ перед текущим положением курсора 
- M-d Удалить следующее за текущим положением курсора слово 
- C-k Удалить текст от текущего положения курсора до конца строки 
- M-k Удалить текст от текущего положения курсора до конца предложения 
- M-\ Удалить все пробелы и знаки табуляции вокруг текущего положения курсора 
- C-q Вставить символ, соответствующий нажатой клавише или сочетанию 
- M-q Выровнять текст в текущем параграфе буфера

##### Команды для поиска и замены в Emacs

- C-s текст поиска Поиск текста в прямом направлении 
- C-r текст поиска Поиск текста в обратном направлении
-  M-% Поиск текста и его замена с запросом (что на что заменить)

##### Прочие комбинации клавиш, используемые в Emacs

- C-\ Переключить язык 
- M-x command Выполнить команду Emacs с именем command 
- C-x u Отменить последнюю операцию[2, 3]




# Выполнение лабораторной работы

1. Выполним примеры, приведённые в первой части описания лабораторной работы

   1. Откроем emacs. (рис. -@fig:001)

      ![emacs](screens\1.jpg){ #fig:001 width=70% }

   2. Создадим файл lab07.sh с помощью комбинации Ctrl-x Ctrl-f (C-x C-f) (рис. -@fig:002).  Наберем текст ниже. Сохраним файл с помощью комбинации Ctrl-x Ctrl-s (C-x C-s).

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

      ![Файл в emacs](screens\2.jpg){ #fig:002 width=70% }

   3. Вырежем одной командой целую строку (С-k). (рис. -@fig:003).

      ![Вырезание строки](screens\3.jpg){ #fig:003 width=70% }
      
   4. Вставить эту строку в конец файла (C-y). (рис.  -@fig:004)

      ![Вставка в конец](screens\4.jpg){ #fig:004 width=70% }

   5. Выделить область текста (C-space). (рис.  -@fig:005)

      ![Выделение текста](screens\5.jpg){ #fig:005 width=70% }

   6. Скопируем область в буфер обмена (M-w). Вставим область в конец файла. (рис.  -@fig:006)

      ![Вставка и копирование строк](screens\6.jpg){ #fig:006 width=70% }

   7. Вновь выделить эту область и на этот раз вырезать её (C-w). (рис.  -@fig:007)

      ![Удаление строки](screens\7.jpg){ #fig:007 width=70% }

   8. Отмените последнее действие (C-/). (рис.  -@fig:008)

      ![Отмена команды](screens\8.jpg){ #fig:008 width=70% }

   9. Научимся использовать команды по перемещению курсора: 6.1 Переместите курсор в начало строки (C-a). 6.2. Переместите курсор в конец строки (C-e). 6.3. Переместите курсор в начало буфера (M-<). 6.4. Переместите курсор в конец буфера (M->).

      Выведем список активных буферов на экран (C-x C-b). (рис.  -@fig:009)

      ![Список буферов](screens\9.jpg){ #fig:009 width=70% }

   10. Переместимся во вновь открытое окно (C-x) o со списком открытых буферов и переключимся на другой буфер. (рис.  -@fig:010)

       ![Изменение буфера](screens\10.jpg){ #fig:010 width=70% }

   11. Теперь вновь переключайтесь между буферами, но уже без вывода их списка на экран (C-x b). (рис.  -@fig:011)

       ![Переключение буфера с помощью клавиш](screens\11.jpg){ #fig:011 width=70% }

   12. Поделите фрейм на 4 части: разделите фрейм на два окна по вертикали (C-x 3), а затем каждое из этих окон на две части по горизонтали (C-x 2). (рис.  -@fig:012)

       ![Разделение фреймов](screens\12.jpg){ #fig:012 width=70% }

   13. Переключимся в режим поиска (C-s) и найдем несколько слов, присутствующих в тексте.

       Переключение между результатами поиска: C-s.

       Выход из режима поиска: C-g (рис.  -@fig:013)

       ![Разделение фреймов](screens\13.jpg){ #fig:013 width=70% }

   14. Перейдем в другой режим поиска, нажав M-s o. В обычном режиме поиск выделяет цветом слова в тексте, здесь - список совпадений в окне ниже. рис.  -@fig:014)

   ![Разделение фреймов](screens\14.jpg){ #fig:014 width=70% }

   


# Выводы

В процессе работы над лабораторной работы были получены навыки работы с редактором emacs и освоены команды для редактирования файлов и навигации по ним.

# Библиография

1. https://docs.altlinux.org/ru-RU/archive/2.3/html-single/junior/alt-docs-extras-linuxnovice/ch02s10.html
2. https://habr.com/ru/post/190790/
3. Д.С. Кулябов, А.В. Королькова / Администрирование локальных систем. Лабораторные работы. — М.: Российский университет дружбы народов, 2017. — 119 с.
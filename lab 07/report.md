---
# Front matter
lang: ru-RU
title: "Отчет по лабораторной работе 7"
subtitle: "Поиск файлов. Перенаправление ввода-вывода. Просмотр запущенных процессов"
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

Ознакомление с инструментами поиска файлов и фильтрации текстовых данных. Приобретение практических навыков: по управлению процессами (и заданиями), по проверке использования диска и обслуживанию файловых систем.

Объект исследования: система Linux.

Предмет исследования: работа с инструментами поиска и фильтрации текстовых данных.

# Техническое обеспечение:

- Характеристики техники: AMD Ryzen 5 3500U 2.1 GHz, 8 GB оперативной памяти, 50 GB свободного места на жёстком диске;
- ОС Windows 10 Home
- Git  2.31.1
- Google Chrome 91.0.4472.19
- VirtualBox 2.0
- CentOS 7

# Условные обозначения и термины:

**Процесс **в Linux (как и в UNIX) - это программа, которая выполняется в отдельном виртуальном адресном пространстве. Когда пользователь регистрируется в системе, автоматически создается процесс, в котором выполняется оболочка (shell), например, /bin/bash.

**Поток** — это последовательность или цикл управления в процессе. 

**Файловая система ОС типа Linux** — иерархическая система каталогов, подкаталогов и файлов, которые обычно организованы и сгруппированы по функциональному признаку.[1]

# Теоретическое введение:

Ввод и вывод распределяется между тремя стандартными потоками:

- stdin - стандартный ввод (клавиатура)

- stdout - стандартный вывод (экран)

- stderr - стандартная ошибка (вывод ошибок на экран)

  Потоки вывода и ввода можно перенаправлять на другие файлы или устройства. Проще всего это делается с помощью символов >, >>, <, <<.

  Конвейер (pipe) служит для объединения простых команд или утилит в цепочки, в которых результат работы предыдущей команды передаётся последующей. Синтаксис следующий:

  команда 1 | команда 2 

  _#означает, что вывод команды 1 передастся на ввод команде 2_

  Команда find используется для поиска и отображения имён файлов, соответствующих заданной строке символов.

  Найти в текстовом файле указанную строку символов позволяет команда grep. Формат команды: grep строка имя_файла

  Команда df показывает размер каждого смонтированного раздела диска.

  Команда du показывает число килобайт, используемое каждым файлом или каталогом.

  Любую выполняющуюся в консоли команду или внешнюю программу можно запустить в фоновом режиме. Для этого следует в конце имени команды указать знак амперсанда &. 

  Для завершения задачи необходимо выполнить команду kill %номер задачи


# Выполнение лабораторной работы

1. Запишите в файл file.txt названия файлов, содержащихся в каталоге /etc. Допишем в этот же файл названия файлов, содержащихся в вашем домашнем каталоге.(рис. -@fig:001)

   ![Запись в файл](screens\1.jpg){ #fig:001 width=70% }

2. Выведем имена всех файлов из file.txt, имеющих расширение .conf, и запишем их в новый текстовой файл conf.txt.(рис. -@fig:002,  -@fig:003)

   ![Вывод файлов с расширение .conf](screens\2.jpg){ #fig:002 width=70% }

   ![Запись в файл conf.txt](screens\3.jpg){ #fig:003 width=70% }

3. Определим, какие файлы в домашнем каталоге имеют имена, начинающиеся с символа c. Несколько вариантов, как это сделать (рис. -@fig:004)

   ![Запись в файл conf.txt](screens\4.jpg){ #fig:004 width=70% }
   
4. Выведем на экран (постранично) имена файлов из каталога /etc, начинающиеся с символа h. (рис. -@fig:005)

   ![Имена файлов из каталога /etc, начинающиеся с h](screens\4.1.jpg){ #fig:005 width=70% }

   

5. Запустим в фоновом режиме процесс, который будет записывать в файл ~/logfile файлы, имена которых начинаются с log. (рис. -@fig:006)

6. Удалим файл ~/logfile. (рис. -@fig:006)

   ![Фоновый процесс](screens\5.jpg){ #fig:006 width=70% }

   

7. Запустим в фоновом режиме редактор gedit. (рис. -@fig:007)

8. Определим идентификатор процесса gedit, используя команду ps, конвейер и фильтр grep.  (рис. -@fig:007)

9. Прочтем справку (man) команды kill, после чего используем её для завершения процесса gedit.(рис. -@fig:007)

   ![Результаты команд df, du](screens\6.jpg){ #fig:007 width=70% }

10. Выполним команды df и du (рис. -@fig:008)

   ![Результаты команд df, du](screens\8.jpg){ #fig:008 width=70% }

11. Воспользовавшись справкой команды find, выведем имена всех директорий, имеющихся в домашнем каталоге.(рис. -@fig:011,  -@fig:012)

    ![Запись в файл conf.txt](screens\11.jpg){ #fig:011 width=70% }

    ![Поиск директорий](screens\12.jpg){ #fig:012 width=70% }

    

# Выводы

В процессе работы над лабораторной работы были получены навыки работы с инструментами поиска файлов и фильтрацией текстовых данных, приобретены практические навыки: по управлению процессами (и заданиями), по проверке использования диска и обслуживанию файловых систем.

# Библиография

1. https://ru.wikipedia.org/wiki/Bash
2. Д.С. Кулябов, А.В. Королькова / Администрирование локальных систем. Лабораторные работы. — М.: Российский университет дружбы народов, 2017. — 119 с.
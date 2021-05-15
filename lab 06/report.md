---
# Front matter
lang: ru-RU
title: "Отчет по лабораторной работе 6"
subtitle: "Анализ файловой системы Linux. Команды для работы с файлами и каталогами"
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

Ознакомление с файловой системой Linux, её структурой, именами и содержанием каталогов. Приобретение практических навыков по применению команд для работы с файлами и каталогами, по управлению процессами (и работами), по проверке использования диска и обслуживанию файловой системы.

Объект исследования: система Linux.

Предмет исследования: работа с файлами и каталогами из терминала.

# Техническое обеспечение:

- Характеристики техники: AMD Ryzen 5 3500U 2.1 GHz, 8 GB оперативной памяти, 50 GB свободного места на жёстком диске;
- ОС Windows 10 Home
- Git  2.31.1
- Google Chrome 91.0.4472.19
- VirtualBox 2.0
- CentOS 7

# Условные обозначения и термины:

**bash** - командный интерпретатор GNU Bourne-Again SHell

**Виртуальная файловая система** (VFS) – компонент ядра Linux, обеспечивающий пользователю доступ к различным файловым системам. Собственно, VFS определяет интерфейс между ядром и файловой системой но, вместе с тем не ориентирована на какую-либо конкретную файловую систему.

**Владелец файла или каталога** – пользователь создавший файл или каталог, является его владельцем. Сменить владельца может только он сам или суперпользователь (root).

**Рут** (**root**) или **Суперпользователь** – администратор в UNIX-системах. Имеет все права пользователя и может выполнять любые без исключения операции.

**Файловая система ОС типа Linux** — иерархическая система каталогов, подкаталогов и файлов, которые обычно организованы и сгруппированы по функциональному признаку.[1]

# Теоретическое введение:

Команда для создания текстовых файлов. Для создания текстового файла удобно воспользоваться командой touch. Формат команды: touch имя-файла

Команды просмотра текстовых файлов. Для просмотра небольших файлов удобно пользоваться командой cat. Формат команды: cat имя-файла. Для просмотра больших файлов используйте команду less.

Для просмотра начала файла можно воспользоваться командой head.

Команда tail выводит несколько (по умолчанию 10) последних строк .

**Копирование файлов и каталогов**

Копирование файлов и каталогов осуществляется при помощи команды cp. Формат команды: cp [-опции] исходный\_файл целевой\_файл

Команды mv и mvdir предназначены для перемещения и переименования файлов и каталогов. Формат команды mv: mv [-опции] старый\_файл новый\_файл

**Права доступа.** Каждый файл или каталог имеет права доступа: чтение r, запись w, выполнение x.

Права доступа к файлу или каталогу можно изменить, воспользовавшись командой chmod.[2]


# Выполнение лабораторной работы

1. Выполним примеры, приведённые в первой части описания лабораторной работы

   1. Скопировал файл ~/abc1 в файл april и в файл may. Скопировал файлы april и may в каталог monthly. Скопировал файл monthly/may в файл с именем june. Скопировал каталог monthly в каталог monthly.00. Скопировал каталог monthly.00 в каталог /tmp. (рис. -@fig:001)

      ![Создание, переименование и перемещение файлов](screens\1.jpg){ #fig:001 width=70% }

   2. Изменил название файла april на july в домашнем каталоге. Переместил файл july в каталог monthly.00. Переименовал каталог monthly.00 в monthly.01. Переместил каталог monthly.01в каталог reports. Переименовал каталог reports/monthly.01 в reports/monthly. (рис. -@fig:002)

      ![Создание, переименование и перемещение директорий](screens\2.jpg){ #fig:002 width=70% }

   3. Создал файл ~/may с правом выполнения для владельца. Лишил владельца файла ~/may права на выполнение. Создал каталог monthly с запретом на чтение для членов группы и всех остальных пользователей. Создал файл ~/abc1 с правом записи для членов группы. (рис. -@fig:003, -@fig:004 )

      ![Изменение прав доступа](screens\3.jpg){ #fig:003 width=70% }

   4. Воспользовался командой df, которая выведет на экран список всех файловых систем в соответствии с именами устройств, с указанием размера и точки монтирования, для определения объёма свободного пространства на файловой системе. (рис.  -@fig:004)

      ![Список файловых систем](screens\4.jpg){ #fig:004 width=70% }

   5. С помощью команды fsck проверил целостность файловой системы.(рис.  -@fig:005)

      ![Проверка целостности файловых систем](screens\5.jpg){ #fig:005 width=70% }

      

2. Выполняю следующие действия: (рис.  -@fig:006)

   1. Копирую файл /usr/include/sys/io.h в домашний каталог и называю его equipment.

   2. В домашнем каталоге создаю директорию ~/ski.plases.

   3. Перемещаю файл equipment в каталог ~/ski.plases.

   4. Переименовываю файл ~/ski.plases/equipment в ~/ski.plases/equiplist.

   5. Создаю в домашнем каталоге файл abc1 и копирую его в каталог ~/ski.plases, называю его equiplist2.

   6. Создаю каталог с именем equipment в каталоге ~/ski.plases.

   7. Перемещаю файлы ~/ski.plases/equiplist и equiplist2 в каталог ~/ski.plases/equipment.

   8. Создаю и перемещаю каталог ~/newdir в каталог ~/ski.plases и называю его plans.

      ![Создание, переименование и перемещение файлов](screens\6.jpg){ #fig:006 width=70% }

4. Определяю опции команды chmod, необходимые для того, чтобы присвоить файлам australia, play, my_os и feathers следующие права доступа соответственно, считая, что в начале таких прав нет: drwxr--r--, drwx--x—x, -r-xr--r--, -rw-rw-r-- (рис. -@fig:007, -@fig:008).

   ![Создание файлов](screens\7.jpg){ #fig:007 width=70% }

   ![Установка прав доступа](screens\8.jpg){ #fig:008 width=70% }

5. Проделываю следующие упражнения:

   1. Просматриваю содержимое файла /etc/password (рис. -@fig:009).

      ![Просмотр passwd](screens\9.jpg){ #fig:009 width=70% }

   2. Копирую файл ~/feathers в файл ~/file.old (рис. -@fig:010).

   3. Перемещаю файл ~/file.old в каталог ~/play (рис. -@fig:010).

   4. Копирую каталог ~/play в каталог ~/fun (рис. -@fig:010).

   5. Перемещаю каталог ~/fun в каталог ~/play и называю его games (рис. -@fig:010).

   6. Лишаю владельца файла ~/feathers права на чтение. (рис. -@fig:010).

   7. Пытаюсь просмотреть файл ~/feathers командой cat. Из-за лишения права на чтение, сделать этого не получается. (рис. -@fig:010).

   8. Пытаюсь скопировать файл ~/feathers. Из-за лишения права на чтение, сделать этого не получилось. (рис. -@fig:010).

   9. Даю владельцу файла ~/feathers право на чтение. (рис. -@fig:010).

      ![Манипуляции с правами доступа](screens\10.jpg){ #fig:010 width=70% }

      10. Лишаю владельца каталога ~/play права на выполнение.(рис. -@fig:011).

      11. Перехожу в каталог ~/play. Странно, но доступа к каталогу нет, с правами на выполнение - есть.(рис. -@fig:011).

      12. Даем владельцу каталога ~/play право на выполнение.(рис. -@fig:011).

          ![Права доступа для каталогов](screens\11.jpg){ #fig:011 width=70% }

6. Прочитаем man по командам mount, fsck, mkfs, kill.

   - mount - нужна для просмотра смонтированных файловых систем, а также для монтирования любых локальных или удаленных файловых систем.
   - fsck - проверяет и устраняет ошибки в файловой системе.
   - mkfs - действие заключается в создании указанной файловой системы на выбранном диске или разделе.
   -  kill - завершает некорректно работающее приложение. 

   

# Выводы

В процессе работы над лабораторной работы были получены навыки применения команд для работы с файлами и каталогами, по управлению процессами, по проверке использования диска и обслуживанию файловой системы.

# Библиография

1. https://ru.wikipedia.org/wiki/Bash
2. Д.С. Кулябов, А.В. Королькова / Администрирование локальных систем. Лабораторные работы. — М.: Российский университет дружбы народов, 2017. — 119 с.
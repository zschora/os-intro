---
# Front matter
lang: ru-RU
title: "Отчет по лабораторной работе 5"
subtitle: "Основы интерфейса взаимодействия пользователя с системой Unix на уровне командной строки"
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

Приобретение практических навыков взаимодействия пользователя с системой посредством командной строки.

Объект исследования: терминал системы CentOS.

Предмет исследования: использование терминала для взаимодействия с системой.

# Техническое обеспечение:

- Характеристики техники: AMD Ryzen 5 3500U 2.1 GHz, 8 GB оперативной памяти, 50 GB свободного места на жёстком диске;
- ОС Windows 10 Home
- Git  2.31.1
- Google Chrome 91.0.4472.19
- VirtualBox 2.0
- CentOS 7

# Условные обозначения и термины:

**bash** - командный интерпретатор GNU Bourne-Again SHell

**Сценарный язык** - высокоуровневый язык сценариев — кратких описаний действий, выполняемых системой. 

**Сценарий** — это программа, имеющая дело с готовыми программными компонентами.

**Файловая система ОС типа Linux** — иерархическая система каталогов, подкаталогов и файлов, которые обычно организованы и сгруппированы по функциональному признаку.[1]

# Теоретическое введение:

В операционной системе типа Linux взаимодействие пользователя с системой обычно осуществляется с помощью командной строки посредством построчного ввода команд. При этом обычно используется командные интерпретаторы языка shell: /bin/sh; /bin/csh; /bin/ksh.

**Формат команды.**

Общий формат команд можно представить следующим образом:

имя_команды разделитель аргументы

Команда `man` используется для просмотра (оперативная помощь) в диалоговом режиме руководства (manual) по основным командам операционной системы типа Linux. Формат команды: man <команда>

Команда `cd` используется для перемещения по файловой системе операционной системы типа Linux.

Для определения абсолютного пути к текущему каталогу используется команда `pwd`

Команда `ls` используется для просмотра содержимого каталога.

Команда `mkdir` используется для создания каталоговm, `rmdir` - для удаления, `rm` - удаление файлов.

Для вывода на экран списка ранее выполненных команд используется команда `history`.

К любой команде из выведенного на экран списка можно обратиться по её номеру в списке, воспользовавшись конструкцией ! номер_команды.[2]


# Выполнение лабораторной работы

1. Описываются проведённые действия, в качестве иллюстрации даётся ссылка на иллюстрацию (рис. -@fig:001)

   ![Имя домашнего каталога](screens\1.PNG){ #fig:001 width=70% }

2. Перейдем в каталог /tmp, просмотрим его содержимое командой ls (рис. -@fig:002).

   ![Каталог /tmp](screens\2.PNG){ #fig:002 width=70% }

3. Опция -а выводит также и скрытые файлы/каталоги (рис. -@fig:003).

   ![ls с флагом -a](screens\3.PNG){ #fig:003 width=70% }

4. Опция -l показывает информацию о файле: дату создания, владельца, и т. д. (рис. -@fig:004)

   ![ls с флагом -l](screens\4.PNG){ #fig:004 width=70% }

5. Найдём в каталоге /var/spool/ каталог cron (рис. -@fig:005)

   ![Каталог /var/spool](screens\5.PNG){ #fig:005 width=70% }

6. Выведем информацию о файлах в домашнем каталоге. Как видно, имя владельца gashalygin.

   ![Файлы домашнего каталога](screens\6.PNG){ #fig:006 width=70% }

7. Создадим в домашнем каталоге каталог newdir. В нем создадим каталог morefun. (рис. -@fig:007)

   ![Создание и удаление директорий](screens\7.PNG){ #fig:007 width=70% }

8. Создадим в домашнем каталоге letters, memos, misk. Затем удалим их одной командой rmdir.

   Команда rm и даже rmdir не удаляет каталог newdir, т.к. он не пуст. Удалим newdir/morefun и проверим, что он удалился.(рис. -@fig:008)

   ![Создание и удаление нескольких каталогов](screens\8.PNG){ #fig:008 width=70% }

9. Определим командой man опцию команды ls для отображения всех подкаталогов: man ls(рис. -@fig:009)

   ![Опция для отображения подкаталогов](screens\9.PNG){ #fig:009 width=70% }

10. Опции команды ls для отображения полной информации о каталогах в порядке времени создания/изменения.(рис. -@fig:010, -@fig:011)

    ![Опция для отображения полной информации](screens\10.PNG){ #fig:010 width=70% }

    ![Опция для отображения полной информации](screens\11.PNG){ #fig:011 width=70% }

11. Отобразим основные опции команды mkdir(рис. -@fig:012)

    - m - режим создания фалйов
    - р - нет ошибки если каталог уже существует
    - v - печатает сообщения при каждом создании каталога
    - z - устанавливает SELinux secuity контекст для всех создаваемых каталогов.

    ![Опции команды mkdir](screens\12.PNG){ #fig:012 width=70% }

12. Опции команды rmdir(рис. -@fig:013)

     - -р - удаление подкаталогов

     - -v - печать информации об удалении

     - -help - отобразить помощь по испольщованию

     - -version - версия

       ![Опции команды rmdir](screens\13.PNG){ #fig:013 width=70% }

13. Опции команды rm(рис. -@fig:014, -@fig:015)

    - f - игнор несуществующих файлов

    - i - спрашивать о каждом удалении

    - r - рекурсивно удалить подкаталоги

    - d - удалить пустые каталоги

      ![Опции команды rm](screens\14.PNG){ #fig:014 width=70% }

      ![Опции команды rm](screens\15.PNG){ #fig:015 width=70% }

14. С помощью команды history отобразим историю команд. Затем выполним команды из истории.(рис. -@fig:016, -@fig:017)

    ![История команд](screens\16.PNG){ #fig:016 width=70% }

    ![Выполнение команд из истории](screens\17.PNG){ #fig:017 width=70% }



# Выводы

В процессе работы над лабораторной работы были получены навыки работы с терминалом и взаимодействия с системой посредством командной строки. Усвоены некоторые простые команды: ls, cd, pwd, mkdir, etc.

# Библиография

1. https://ru.wikipedia.org/wiki/Bash
2. Д.С. Кулябов, А.В. Королькова / Администрирование локальных систем. Лабораторные работы. — М.: Российский университет дружбы народов, 2017. — 119 с.
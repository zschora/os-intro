---
# Front matter
lang: ru-RU
title: "Отчет по лабораторной работе 4"
subtitle: "Знакомство с операционной системой Linux"
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

Познакомиться с операционной системой Linux, получить практические навыки работы с консолью и некоторыми графическими менеджерами рабочих столов операционной системы.

Объект исследования: система UNIX.

Предмет исследования: начало работы в UNIX.

# Техническое обеспечение:

- Характеристики техники: AMD Ryzen 5 3500U 2.1 GHz, 8 GB оперативной памяти, 50 GB свободного места на жёстком диске;
- ОС Windows 10 Home
- Git  2.31.1
- Google Chrome 91.0.4472.19
- VirtualBox 2.0
- CentOS 7

# Условные обозначения и термины:

**Компьютерный терминал** — устройство ввода–вывода, основные функции которого заключаются в вводе и отображении данных.

**Текстовый терминал** (терминал, текстовая консоль) — интерфейс компьютера для последовательной передачи данных.

**Учётная запись пользователя** (user account) — идентификатор пользователя, на основе которого ему назначаются права на действия в операционной системе.

**Входное имя пользователя **(Login) — название учётной записи пользователя.

**Виртуальные консоли** — реализация концепции многотерминальной работы в рамках одного устройства.

Подробнее в [2] и [3].

# Теоретическое введение:

Загрузка системы завершается выводом на экран приглашения пользователя к регистрации «login:». После этого система запросит пароль (password), соответствующий введенному имени, выдав специальное приглашение — обычно «Password:».[1]

hostname login: username

Password:

В многопользовательской модели пользователи делятся на пользователей с обычными правами и администраторов.

Для каждого пользователя организуется домашний каталог, где хранятся его данные и настройки рабочей среды. Доступ других пользователей с обычными правами к этому каталогу ограничивается.

Учётная запись пользователя с UID=0 называется root и присутствует в любой системе типа Linux. Пользователь root имеет права администратора и может выполнять любые действия в системе.[2]

Учётные записи пользователей хранятся в файле /etc/passwd, который имеет следующую структуру [3]:

login:password:UID:GID:GECOS:home:shell

### Виртуальные консоли

В операционных системах типа Linux доступно обычно 6 виртуальных консолей, работающих в текстовом режиме. Переключение между консолями осуществляется при помощи сочетания клавиши Alt с одной из функциональных клавиш ( F1 – F6 ).

Виртуальные консоли при обращении к ним из командной строки обозначаются ttyN, где N — номер виртуальной консоли. Для перехода из текстового режима в графический необходимо нажать комбинацию клавиш Ctrl + Alt + F7 . Для переключения из графического режима в одну из текстовых виртуальных консолей достаточно нажать комбинацию клавиш Ctrl + Alt + Fn , где 𝑛 — номер необходимой виртуальной консоли.

Процедура регистрации в графическом режиме аналогична регистрации в текстовом режиме. Если пользователь входит в систему несколько раз под одним и тем же именем (на разных виртуальных консолях), то ему будут доступны несколько разных сеансов работы, не связанных между собой.

Для корректного завершения своей работы в системе пользователь должен выйти из системы. Чтобы завершить работу в виртуальной консоли, пользователю необходимо в соответствующей командной строке набрать команду logout или воспользоваться комбинацией клавиш Ctrl + D . При этом работа самой операционной системы не прекращается.[3]

### Выбор графической среды при логине

На компьютерах с операционной системой типа Linux может быть установлено несколько графических сред. После загрузки компьютера появится менеджер дисплея.[2, 3]

Графические среды:

- Среда Xfce
- Среда GNOME
- Среда KDE


# Выполнение лабораторной работы

1. Загрузим компьютер и перейдем на текстовую консоль. Всего доступно 5 текстовых консолей F2-F5.  Зарегистрируемся в таксовой консоли. В поле пароля не отображаются символы. (рис. -@fig:001)

   ![Регистрация в консоли](screens\1.jpg){ #fig:001 width=70% }

2. Для перемещения между консолями нужно набрать Alt+Fn (рис. -@fig:002). 

   ![Перемещение в другую консоль](screens\2.jpg){ #fig:002 width=70% }

3. Для возврата в графический режим Alt+F1. Здесь это упрощённый GNOME (рис. -@fig:003).

   ![Графический режим](screens\3.jpg){ #fig:003 width=70% }

4. Команда logout завершает консольные сеанс. (рис.  -@fig:004)

   ![Завершение сеанса](screens\4.jpg){ #fig:004 width=70% }

5. Зарегистрируемся в разных менеджерах. Установленные на рис.  -@fig:005.

   ![Графические менеджеры](screens\5.jpg){ #fig:005 width=70% }

6. Менеджер GNOME. (рис.  -@fig:006)

   Некоторые элементы GNOME: – файловый менеджер Nautilus; – эмулятор терминала GNOME Terminal; – текстовый редактор gedit; – приложение для просмотра документации Yelp; – стандартный веб-браузер Web (ранее — Epiphany); – приложение для управления электронной почтой Evolution; – комплект графических средств для администрирования GNOME System Tools.

   ![GNOME](screens\6.jpg){ #fig:006 width=70% }

7. KDE. (рис.  -@fig:007)

   Некоторые элементы KDE: – базовые библиотеки KDELibs; – компонент для просмотра HTML документов KHTML; – компонент, обеспечивающий доступ к файлам KIO; – оконный менеджер KWin; – рабочий стол и основные приложения kdebase; – инструменты графического администрирования kdeadmin; – утилиты kdeutils.

   ![KDE](screens\7.jpg){ #fig:007 width=70% }

8. XFCE. (рис.  -@fig:008)

   Элементы Xfce: – файловый менеджер Thunar; – менеджер окон Xfwm; – панель задач xfce4-panel; – менеджер рабочего стола xfdesktop; – менеджер сеансов xfce4-session; – диспетчер настроек xfce4-settings; – система хранения настроек xfconf; – поиск приложений xfce4-appfinder; – эмулятор терминала xfce4-terminal; – менеджер питания xfce4-power-manager.

   ![XFCE](screens\8.jpg){ #fig:008 width=70% }

9. Openbox. (рис.  -@fig:009)

   Меню вызывается кликом на правую клавишу мыши.

   ![Openbox](screens\9.jpg){ #fig:009 width=70% }

10. Откроем браузер Fireox. (рис.  -@fig:010)

    ![Браузер](screens\10.jpg){ #fig:010 width=70% }

    11. Текстовый редактор. (рис.  -@fig:011)

        ![Текстовый редактор](screens\11.jpg){ #fig:011 width=70% }

    12. Эмулятор консоли Konsole. (рис.  -@fig:012)

        ![Эмулятор консоли](screens\12.jpg){ #fig:012 width=70% }

# Выводы

В процессе работы над лабораторной работы были получены практические навыки работы с консолью и некоторыми графическими менеджерами рабочих столов операционной системы

# Библиография

1. https://www.comss.ru/page.php?id=2384
2. https://hamsterden.ru/desktop-environment/
3. Д.С. Кулябов, А.В. Королькова / Администрирование локальных систем. Лабораторные работы. — М.: Российский университет дружбы народов, 2017. — 119 с.
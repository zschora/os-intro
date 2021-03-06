---
## Front matter
lang: ru-RU
title: "Отчет по лабораторной работе 8"
subtitle: "Командная оболочка Midnight Commander"
author: |
	Шалыгин Г.Э, НФИбд-02-20\inst{1}
institute: |
	\inst{1}RUDN University, Moscow, Russian Federation
date: 2021, Москва

## Formatting
mainfont: Cambria
romanfont: Cambria
sansfont: Cambria
monofont: Cambria
toc: false
slide_level: 2
theme: metropolis
header-includes: 
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'
 - '\beamer@ignorenonframefalse'
 - '\makeatother'
aspectratio: 43
section-titles: true
---

# Цель работы

Освоение основных возможностей командной оболочки Midnight Commander. Приобретение навыков практической работы по просмотру каталогов и файлов; манипуляций с ними

Объект исследования: Midnight Commander.

Предмет исследования:  работа в Midnight Commander.

# Результаты

## Интерфейс

Запустим из командной строки mc (+Enter), его структура на  рис. -@fig:004

![Интерфейс](../screens\4.jpg){ #fig:004 width=70% }



---

## меню панелей

Выполним основные команды меню левой панели: быстрый просмотр  (рис. -@fig:010), дерево (рис. -@fig:011), информация (рис. -@fig:012).

![быстрый просмотр](..\screens\10.jpg){ #fig:010 width=40% }

![дерево](..\screens\11.jpg){ #fig:011 width=40% }



---

## меню файл

Из меню команда выполним следующие действия:

1. поиск в файловой системе файла с заданными условиями (например, файла с расширением .c или .cpp, содержащего строку main) (рис. -@fig:014);

2. вызов истории команд;

3. переход в домашний каталог (рис. -@fig:015);

4. анализ файла меню и файла расширений (рис. -@fig:016, рис. -@fig:017).

   ![поиск .cpp файлов](..\screens\14.jpg){ #fig:014 width=40% }

---

## меню настройки

Здесь собраны команды настройки интерфейса

![горизонтальное разделение панелей](screens\20.jpg){ #fig:020 width=50% }

---

## встроенный редактор

С его помощью можно:

- открыть файл, 
- удалить строку
- скопировать или переместить фрагмент текста
- отменить последнее действие
- перемещаться по файлу
- включить/отключить подсветку синтаксиса для файлов на языках программирования.

---

## Вывод

В процессе работы над лабораторной работы были изучены основные возможности командной оболочки Midnight Commander. Приобретены навыки практической работы по просмотру каталогов и файлов, манипуляций с ними.


## {.standout}

Спасибо за внимание


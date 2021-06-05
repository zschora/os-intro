---
## Front matter
lang: ru-RU
title: "Отчет по лабораторной работе 14"
subtitle: "Программирование в командном процессоре ОС UNIX"
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

Изучить основы программирования в оболочке ОС UNIX. Научиться писать более сложные командные файлы с использованием логических управляющих конструкций и циклов.

Объект исследования: система UNIX.

Предмет исследования: программирование в UNIX.

# Результаты

## calculate

Создадим файлы: calculate.h, calculate.c, main.c. Это будет примитивнейший калькулятор, способный складывать, вычитать, умножать и делить, возводить число в степень, брать квадратный корень, вычислять sin, cos, tan. При запуске он будет запрашивать первое число, операцию, второе число. После этого программа выведет результат и остановится. (рис. -@fig:001,   -@fig:002, -@fig:003  ). 

![Текст 1 скрипта](../screens\1.jpg){ #fig:001 width=30% }

![Результат работы 1 скрипта](../screens\2.jpg){ #fig:002 width=30% }

![Результат работы 1 скрипта](../screens\2.jpg){ #fig:002 width=30% }

---

## компиляция

Выполним компиляцию программы посредством gcc. (рис. -@fig:004).

![Текст 2 скрипта](../screens\4.jpg){ #fig:003 width=70% }

---

## Компиляция с makefile

Создадим Makefile. (рис.  -@fig:006). В нем прописаны те же команды для компиляции программы, вызываемые ранее вручную с флагами в виде переменных, которые можно менять при необходимости. Компиляция с его использованием на рис. -@fig:007

![Текст 3 скрипта](../screens\6.jpg){ #fig:007 width=40% }

![Текст 3 скрипта](../screens\7.jpg){ #fig:007 width=40% }

---

## gdb

С помощью gdb выполним отладку программы 

![Отладка с помощью gdb](../screens\8.jpg){ #fig:008 width=70% }

## splint

Затем установим утилиту splint и с ее помощью проанализируем коды файлов calculate.c и main.c. 

![Работа splint](../screens\10.jpg){ #fig:010 width=70% }


## {.standout}

Спасибо за внимание


---
## Front matter
lang: ru-RU
title: "Отчет по лабораторной работе 15"
subtitle: "Именованные каналы"
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

Приобретение практических навыков работы с именованными каналами

Объект исследования: система UNIX.

Предмет исследования:  работа с именованными каналами в UNIX.

# Результаты

## Результаты

Создадим файлы: common.h, server.c, client.c, client2.c для работы с именованными каналами со следующими критериями:

- Работает не 1 клиент, а несколько (например, два). 
- Клиенты передают текущее время с некоторой периодичностью (например, раз в пять секунд). Используйте функцию sleep() для приостановки работы клиента. 
- Сервер работает не бесконечно, а прекращает работу через некоторое время (например, 30 сек). Используйте функцию clock() для определения времени работы сервера.

![Текст 1 скрипта](../screens\1.jpg){ #fig:001 width=30% }



---

## компиляция

Выполним компиляцию программы посредством gcc. (рис. -@fig:003).

![Текст 2 скрипта](../screens\5.jpg){ #fig:003 width=70% }

---

## запуск

![Текст 3 скрипта](../screens\4.jpg){ #fig:007 width=40% }


## {.standout}

Спасибо за внимание

